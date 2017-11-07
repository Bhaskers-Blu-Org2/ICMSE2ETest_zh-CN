---
author: Justinha
Description: "在实验室中使用下面的脚本。 它可能有助于创建这些一次性或从网站上下载这些示例。"
ms.assetid: 621503da-e74f-4eef-8315-72c8be67747a
MSHAttr: PreferredLib:/library/windows/hardware
title: "示例脚本"
ms.openlocfilehash: 45d1f4104eeb781a5c5a83eef14233d191f1f9e0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="sample-scripts"></a>示例脚本

[下载在该实验中使用的示例脚本](http://go.microsoft.com/fwlink/p/?LinkId=800657) 

将这些脚本复制到您的存储 USB 驱动器的根。  请参阅此页后，可以了解什么是脚本中。

下一步︰[部署 Windows 使用脚本](deploy-windows-with-a-script-sxs.md)

## <a name="span-idimagedeploymentscriptsspanspan-idimagedeploymentscriptsspanspan-idimagedeploymentscriptsspanimage-deployment-scripts"></a><span id="Image_deployment_scripts"></span><span id="image_deployment_scripts"></span><span id="IMAGE_DEPLOYMENT_SCRIPTS"></span>映像部署脚本

下面的脚本使用一个图像文件，设置 Windows 设备和配置按钮重置功能。

### <a name="span-idcreatepartitions-firmwaretxtspanspan-idcreatepartitions-firmwaretxtspanspan-idcreatepartitions-firmwaretxtspancreatepartitions-firmwaretxt"></a><span id="CreatePartitions-_firmware_.txt"></span><span id="createpartitions-_firmware_.txt"></span><span id="CREATEPARTITIONS-_FIRMWARE_.TXT"></span>CreatePartitions-（固件）.txt

使用 DiskPart 与这些脚本格式并为窗口，包括恢复工具设置硬盘分区。 调整分区大小以填充所需的驱动器。

### <a name="applyimagebat"></a>ApplyImage.bat

使用此脚本将 Windows 映像应用到新设备。

``` syntax
@echo ApplyImage.bat
@echo     Applies a Windows image to a desktop PC.
@echo     To run this script, boot the device using WinPE first.
@echo     NOTE: This script erases the primary hard drive
@echo.
@echo UPDATE (JULY 2016):
@echo * This script stops just after applying the image.
@echo   This gives you an opportunity to add siloed provisioning packages (SPPs)
@echo   so that you can include them in your recovery tools.
@echo.
@echo   After the script is complete, use apply-recovery.bat to finish
@echo   setting up the recovery tools.
@echo.
@echo * Checks whether the PC is booted into BIOS or UEFI mode
@echo   and applies the appropriate disk configuration.
@echo.
@echo * Includes support for the /EA variables for quicker
@echo   image capture and recovery.
@echo.
@echo * Checks to see if you're booted into Windows PE.
@echo.
@if not exist X:\Windows\System32 echo ERROR: This script is built to run in Windows PE.
@if not exist X:\Windows\System32 goto END
@if %1.==. echo ERROR: To run this script, add a path to a Windows image file.
@if %1.==. echo Example: ApplyImage D:\WindowsWithFrench.wim
@if %1.==. goto END
@echo *********************************************************************
@echo Checking to see if the PC is booted in BIOS or UEFI mode.
wpeutil UpdateBootInfo
for /f "tokens=2* delims=    " %%A in ('reg query HKLM\System\CurrentControlSet\Control /v PEFirmwareType') DO SET Firmware=%%B
@echo            Note: delims is a TAB followed by a space.
@if x%Firmware%==x echo ERROR: Can't figure out which firmware we're on.
@if x%Firmware%==x echo        Common fix: In the command above:
@if x%Firmware%==x echo             for /f "tokens=2* delims=    "
@if x%Firmware%==x echo        ...replace the spaces with a TAB character followed by a space.
@if x%Firmware%==x goto END
@if %Firmware%==0x1 echo The PC is booted in BIOS mode. 
@if %Firmware%==0x2 echo The PC is booted in UEFI mode. 
@echo *********************************************************************
@echo Formatting the primary disk...
@if %Firmware%==0x1 echo    ...using BIOS (MBR) format and partitions.
@if %Firmware%==0x2 echo    ...using UEFI (GPT) format and partitions. 
@echo CAUTION: All the data on the disk will be DELETED.
@SET /P READY=Erase all data and continue? (Y or N):
@if %READY%.==y. set READY=Y
@if not %READY%.==Y. goto END
if %Firmware%==0x1 diskpart /s %~dp0CreatePartitions-BIOS.txt
if %Firmware%==0x2 diskpart /s %~dp0CreatePartitions-UEFI.txt
@echo *********************************************************************
@echo  == Set high-performance power scheme to speed deployment ==
call powercfg /s 8c5e7fda-e8bf-4a96-9a85-a6e23a8c635c
@echo *********************************************************************
@echo  == Apply the image to the Windows partition ==
@SET /P COMPACTOS=Deploy as Compact OS? (Y or N):
@if %COMPACTOS%.==y. set COMPACTOS=Y
@echo Does this image include Extended Attributes?
@echo    (If you're not sure, type N).
@SET /P EA=(Y or N):
@if %EA%.==y. set EA=Y
if %COMPACTOS%.==Y.     if %EA%.==Y.     dism /Apply-Image /ImageFile:%1 /Index:1 /ApplyDir:W:\ /Compact /EA
if not %COMPACTOS%.==Y. if %EA%.==Y.     dism /Apply-Image /ImageFile:%1 /Index:1 /ApplyDir:W:\ /EA
if %COMPACTOS%.==Y.     if not %EA%.==Y. dism /Apply-Image /ImageFile:%1 /Index:1 /ApplyDir:W:\ /Compact
if not %COMPACTOS%.==Y. if not %EA%.==Y. dism /Apply-Image /ImageFile:%1 /Index:1 /ApplyDir:W:\
@echo *********************************************************************
@echo == Copy boot files to the System partition ==
W:\Windows\System32\bcdboot W:\Windows /s S:
@echo *********************************************************************
@echo   Next steps:
@echo   * Add Windows desktop applications (optional):
@echo       DISM /Apply-SiloedPackage /ImagePath:W:\ 
@echo            /PackagePath:"D:\App1.spp" /PackagePath:"D:\App2.spp"  ...
@echo   * Add the recovery image:
@echo       ApplyRecovery.bat
@echo   * Reboot:
@echo       exit
:END
```

此脚本依赖于以下两个 DiskPart 脚本，CreatePartitions UEFI.txt，CreatePartitions-BIOS.txt，必须放置在同一个文件夹︰

### <a name="createpartitions-uefitxt"></a>CreatePartitions UEFI.txt

创建基于 UEFI 的计算机系统、 MSR、 窗口和恢复工具分区。

此脚本暂时将这些驱动器号︰ 系统 = S，Windows = W 和恢复 = R。 MSR 分区没有得到一封信。 字母 W 用于避免潜在的驱动器号冲突。 重新启动设备后，Windows 分区分配的字母 C，和其他分区不接收驱动器号。

下图显示了生成的分区配置︰

![缺省分区布局示意图︰ 系统、 msr、 窗口和恢复](images/dep-win10-partitions-uefi.png)

``` syntax
rem == CreatePartitions-UEFI.txt ==
rem == These commands are used with DiskPart to
rem    create four partitions
rem    for a UEFI/GPT-based PC.
rem    Adjust the partition sizes to fill the drive
rem    as necessary. ==
select disk 0
clean
convert gpt
rem == 1. System partition =========================
create partition efi size=100
rem    ** NOTE: For Advanced Format 4Kn drives,
rem               change this value to size = 260 ** 
format quick fs=fat32 label="System"
assign letter="S"
rem == 2. Microsoft Reserved (MSR) partition =======
create partition msr size=16
rem == 3. Windows partition ========================
rem ==    a. Create the Windows partition ==========
create partition primary 
rem ==    b. Create space for the recovery tools ===
shrink minimum=500
rem       ** NOTE: Update this size to match the
rem                size of the recovery tools 
rem                (winre.wim)                    **
rem ==    c. Prepare the Windows partition ========= 
format quick fs=ntfs label="Windows"
assign letter="W"
rem === 4. Recovery partition ======================
create partition primary
format quick fs=ntfs label="Recovery"
assign letter="R"
set id="de94bba4-06d1-4d40-a16a-bfd50179d6ac"
gpt attributes=0x8000000000000001
list volume
exit
```

### <a name="createpartitions-biostxt"></a>CreatePartitions BIOS.txt

创建基于 BIOS 的电脑系统、 窗口和恢复工具分区。

此脚本暂时将这些驱动器号︰ 系统 = S，Windows = W 和恢复 = R。 字母 W 用于避免潜在的驱动器号冲突。 重新启动设备后，Windows 分区分配的字母 C，和其他分区不接收驱动器号。

下图显示了生成的分区配置︰

![缺省分区布局示意图︰ 系统、 窗口和恢复](images/dep-win10-partitions-bios.png)

``` syntax
rem == CreatePartitions-BIOS.txt ==
rem == These commands are used with DiskPart to
rem    create three partitions
rem    for a BIOS/MBR-based computer.
rem    Adjust the partition sizes to fill the drive
rem    as necessary. ==
select disk 0
clean
rem == 1. System partition ======================
create partition primary size=100
format quick fs=ntfs label="System"
assign letter="S"
active
rem == 2. Windows partition =====================
rem ==    a. Create the Windows partition =======
create partition primary
rem ==    b. Create space for the recovery tools  
shrink minimum=500
rem       ** NOTE: Update this size to match the
rem                size of the recovery tools 
rem                (winre.wim)                 **
rem ==    c. Prepare the Windows partition ====== 
format quick fs=ntfs label="Windows"
assign letter="W"
rem == 3. Recovery partition ====================
create partition primary
format quick fs=ntfs label="Recovery image"
assign letter="R"
set id=27
list volume
exit
```

### <a name="applyrecoverybat"></a>ApplyRecovery.bat

使用此脚本来准备 Windows 恢复分区。

``` syntax
@echo == ApplyRecovery.bat ==
@echo  *********************************************************************
@echo  == Copy the Windows RE image to the Windows RE Tools partition ==
md R:\Recovery\WindowsRE
xcopy /h W:\Windows\System32\Recovery\Winre.wim R:\Recovery\WindowsRE\
@echo  *********************************************************************
@echo  == Register the location of the recovery tools ==
W:\Windows\System32\Reagentc /Setreimage /Path R:\Recovery\WindowsRE /Target W:\Windows
@echo  *********************************************************************
@echo  == If Compact OS, single-instance the recovery provisioning package ==
@echo     Options: N: No
@echo              Y: Yes
@echo              D: Yes, but defer cleanup steps to first boot.
@echo                 Use this if the cleanup steps take more than 30 minutes.
@echo                 defer the cleanup steps to the first boot.
@SET /P COMPACTOS=Deploy as Compact OS? (Y, N, or D):
@if %COMPACTOS%.==y. set COMPACTOS=Y
@if %COMPACTOS%.==d. set COMPACTOS=D
if %COMPACTOS%.==Y. dism /Apply-CustomDataImage /CustomDataImage:W:\Recovery\Customizations\USMT.ppkg /ImagePath:W:\ /SingleInstance
if %COMPACTOS%.==D. dism /Apply-CustomDataImage /CustomDataImage:W:\Recovery\Customizations\USMT.ppkg /ImagePath:W:\ /SingleInstance /Defer
@rem *********************************************************************
@echo Checking to see if the PC is booted in BIOS or UEFI mode.
wpeutil UpdateBootInfo
for /f "tokens=2* delims=    " %%A in ('reg query HKLM\System\CurrentControlSet\Control /v PEFirmwareType') DO SET Firmware=%%B
@echo            Note: delims is a TAB followed by a space.
@if x%Firmware%==x echo ERROR: Can't figure out which firmware we're on.
@if x%Firmware%==x echo        Common fix: In the command above:
@if x%Firmware%==x echo             for /f "tokens=2* delims=    "
@if x%Firmware%==x echo        ...replace the spaces with a TAB character followed by a space.
@if x%Firmware%==x goto END
@if %Firmware%==0x1 echo The PC is booted in BIOS mode. 
@if %Firmware%==0x2 echo The PC is booted in UEFI mode. 
@echo  *********************************************************************
@echo == Hiding the recovery tools partition
if %Firmware%==0x1 diskpart /s %~dp0HideRecoveryPartitions-BIOS.txt
if %Firmware%==0x2 diskpart /s %~dp0HideRecoveryPartitions-UEFI.txt
@echo *********************************************************************
@echo == Verify the configuration status of the images. ==
W:\Windows\System32\Reagentc /Info /Target W:\Windows
@echo    (Note: Windows RE status may appear as Disabled, this is OK.)
@echo *********************************************************************
@echo      All done!
@echo      Disconnect the USB drive from the reference device.
@echo      Type exit to reboot.
@echo.
:END
```

此脚本依赖于以下两个 DiskPart 脚本，HideRecoveryPartitions UEFI.txt，HideRecoveryPartitions-BIOS.txt，必须放置在同一个文件夹︰

### <a name="hiderecoverypartitions-uefitxt"></a>HideRecoveryPartitions UEFI.txt

``` syntax
rem === HideRecoveryPartitions-UEFI.txt ===
select disk 0
select partition 4
set id=de94bba4-06d1-4d40-a16a-bfd50179d6ac
gpt attributes=0x8000000000000001
remove
list volume
```

### <a name="hiderecoverypartitions-biostxt"></a>HideRecoveryPartitions BIOS.txt

``` syntax
rem === HideRecoveryPartitions-BIOS.txt ===
select disk 0
select partition 3
set id=27
remove
list volume
```


## <a name="span-idstartlayoutlayoutmodificationxmlspanspan-idstartlayoutlayoutmodificationxmlspanstart-layout-layoutmodificationxml"></a><span id="start_layout__layoutmodification.xml_"></span><span id="START_LAYOUT__LAYOUTMODIFICATION.XML_"></span>开始布局 (LayoutModification.xml)


在 Windows 10 开始麻将牌布局提供 Oem 要追加到包含 Web 链接、 辅助磁贴、 Windows 的应用程序和 Windows 桌面应用程序的默认开始布局的拼贴的能力。 Oem 可以使用此布局，使其适用于多个地区或市场而无需复制了大量的工作。 另外，Oem 可以添加最多三个默认的系统区域中，其中包括重要的或经常访问系统位置的用户提供系统驱动列表 o 中的常用应用程序部分应用程序和最近安装的应用程序。

要充分利用所有这些新功能并具有 Windows 10 的最可靠、 最完整的开始自定义体验，请考虑创建一个 LayoutModification.xml 文件。 此文件指定如何 OEM 图块布局应在开始。 有关如何自定义新的开始布局的详细信息，请参阅 Windows 10 合作伙伴文档中的[自定义 Windows 10 启动屏幕](https://msdn.microsoft.com/library/windows/hardware/mt170651)的主题。

示例**LayoutModification.xml**:

``` syntax
<LayoutModificationTemplate
    xmlns="http://schemas.microsoft.com/Start/2014/LayoutModification"
    xmlns:defaultlayout="http://schemas.microsoft.com/Start/2014/FullDefaultLayout"
    xmlns:start="http://schemas.microsoft.com/Start/2014/StartLayout"
    Version="1">
  <RequiredStartGroupsCollection>
    <RequiredStartGroups
      Region="DE|ES|FR|GB|IT|US">
      <AppendGroup
        Name="Fabrikam Group 1">
        <start:Tile
          AppUserModelID="Microsoft.Office.Word_8wekyb3d8bbwe!microsoft.word"
          Size="2x2"
          Row="0"
          Column="0"/>
        <start:DesktopApplicationTile
          DesktopApplicationID="Microsoft.Windows.Explorer"
          Size="2x2"
          Row="0"
          Column="2"/>
        <start:Tile
          AppUserModelID="Microsoft.Office.Excel_8wekyb3d8bbwe!microsoft.excel"
          Size="2x2"
          Row="0"
          Column="4"/>
      </AppendGroup>    
      <AppendGroup
        Name="Fabrikam Group 2">
        <start:Tile
          AppUserModelID="Microsoft.Reader_8wekyb3d8bbwe!Microsoft.Reader"
          Size="2x2"
          Row="0"
          Column="0"/>
        <start:DesktopApplicationTile
          DesktopApplicationID="http://www.bing.com/"
          Size="2x2"
          Row="0"
          Column="2"/>
        <start:DesktopApplicationTile
          DesktopApplicationLinkPath="%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs\Accessories\Paint.lnk"
          Size="2x2"
          Row="0"
          Column="4"/>
      </AppendGroup>
    </RequiredStartGroups>
    <RequiredStartGroups>
      <AppendGroup
        Name="Fabrikam Group 1">
        <start:Tile
          AppUserModelID="Microsoft.Office.Word_8wekyb3d8bbwe!microsoft.word"
          Size="2x2"
          Row="0"
          Column="0"/>
        <start:SecondaryTile
          AppUserModelID="Microsoft.Windows.Spartan_cw5n1h2txyewy!Microsoft.Spartan.Spartan"
          TileID="FabrikamWeblinkTile"
          Arguments="http://www.fabrikam.com"
          DisplayName="Fabrikam"
          Square150x150LogoUri="ms-appx:///Assets/SpartanMedium.png"
          ShowNameOnSquare150x150Logo="true"
          BackgroundColor="#FF112233"
          Size="2x2"
          Row="0"
          Column="2"/>
      </AppendGroup>    
    </RequiredStartGroups>
  </RequiredStartGroupsCollection> 
  <TopMFUApps>
    <Tile AppUserModelID="Microsoft.WindowsCalculator_8wekyb3d8bbwe!App" />
  </TopMFUApps>  
</LayoutModificationTemplate>
```

**在开始布局演练**

1.  如果您尚没有一个创建名为**LayoutModification.xml**的文件。
2.  如果您需要指定是否追加组必须仅应用于特定地区，，使用可选的**区域**属性中的**RequiredStartGroups**元素。 区域值必须等于两个字母的国家/地区代码。 使用管道"|"分隔符，如果需要指定多个国家/地区。

    ``` syntax
    <RequiredStartGroups
          Region="DE|ES|FR|GB|IT|US">
    ```

3.  指定您想要添加在**AppendGroup**中的拼贴。 Oem 可以添加最多的两个**AppendGroup**。 下面的示例演示两个组，称为"Fabrikam 组 1"和"Fabrikam 组 2"，其中包含国家/地区设备匹配所指定**区域**中应用的拼贴 （在这种情况下，区域是德国、 西班牙、 法国、 大不列颠及北爱尔兰联合王国、 意大利和美国）。 每个组包含三个拼贴，您需要根据您想要开始锁定该图块使用的各种元素。

    ``` syntax
    <RequiredStartGroups
          Region="DE|ES|FR|GB|IT|US">
          
          <!-- OEMs can add a maximum of two AppendGroup. Each AppendGroup specifies a group of
               tiles that will be appended to Start. -->
          <AppendGroup
            Name="Fabrikam Group 1">
            <!-- Add the News Universal Windows app to Start -->
            <start:Tile
              AppUserModelID="Microsoft.Office.Word_8wekyb3d8bbwe!microsoft.word"
              Size="2x2"
              Row="0"
              Column="0"/>
            <!-- Add a Windows desktop application with a known AppUserModelID  -->
            <start:DesktopApplicationTile
              DesktopApplicationID="Microsoft.Windows.Explorer"
              Size="2x2"
              Row="0"
              Column="2"/>
            <!-- Add the Excel Preview Universal Windows app -->
            <start:Tile
              AppUserModelID="Microsoft.Office.Excel_8wekyb3d8bbwe!microsoft.excel"
              Size="2x2"
              Row="0"
              Column="4"/>
          </AppendGroup>
          
          <AppendGroup
            Name="Fabrikam Group 2">
            <!-- Add a Windows 8.1 app -->
            <start:Tile
              AppUserModelID="Microsoft.Reader_8wekyb3d8bbwe!Microsoft.Reader"
              Size="2x2"
              Row="0"
              Column="0"/>
            <!-- Web link tile with associated .url file is in legacy Start Menu folder. This requires
                 a shortcut or .url file to be added in one of several legacy Start Menu directories, such as
                 "%APPDATA%\Microsoft\Windows\Start Menu\Programs\" 
                 or the all users profile "%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs\" -->
            <start:DesktopApplicationTile
              DesktopApplicationID="http://www.bing.com/"
              Size="2x2"
              Row="0"
              Column="2"/>
            <!-- Add a Windows desktop application link in a legacy Start Menu folder. You must add the .lnk file 
                 in the specified location when the device first boots. -->
            <start:DesktopApplicationTile
              DesktopApplicationLinkPath="%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs\Accessories\Paint.lnk"
              Size="2x2"
              Row="0"
              Column="4"/>
          </AppendGroup>
        </RequiredStartGroups>
    ```

    下面的示例显示名为 Fabrikam 组 1，如果设备国家/地区不匹配任何以前的 RequiredStartGroups 中指定的那些将应用的一个组。

    ``` syntax
        <!-- Non-region specific group -->
        <RequiredStartGroups>
          <AppendGroup
            Name="Fabrikam Group 1">
            <!-- Add the Word Preview Universal Windows app -->
            <start:Tile
              AppUserModelID="Microsoft.Office.Word_8wekyb3d8bbwe!microsoft.word"
              Size="2x2"
              Row="0"
              Column="0"/>
            <!-- Add the Excel Preview Universal Windows app -->
            <start:Tile
              AppUserModelID="Microsoft.Office.Excel_8wekyb3d8bbwe!microsoft.excel"
              Size="2x2"
              Row="0"
              Column="2"/>
          </AppendGroup>    
        </RequiredStartGroups>
    ```

    创建 LayoutModification.xml 文件时，请牢记以下︰

    -   如果您不知道应用程序的应用程序用户模型 ID 固定使用**开始︰ DesktopApplicationTile**标记的 Windows 桌面应用程序，您需要在第一次启动之前传统 「 开始 」 菜单目录下创建一个.lnk 文件。
    -   如果**开始︰ DesktopApplicationTile**标记用于固定传统.url 的快捷方式启动，必须创建.url 文件，并将此文件添加到 「 开始 」 菜单目录前第一次启动传统。

    对于上述的情况中，可以使用以下目录放置.url 或.lnk 文件︰

    -   应用程序数据 %%\\Microsoft\\Windows\\「 开始 」 菜单\\程序\\
    -   %ALLUSERSPROFILE%\\Microsoft\\Windows\\「 开始 」 菜单\\程序\\

4.  或者，您可以添加最多 3 系统区域的常用部分的应用程序。 下面的示例演示如何将计算器应用程序添加到区域中频繁使用的系统。

    ``` syntax
      <!-- Add the calculator app to the frequently used system area -->
      <TopMFUApps>
        <Tile AppUserModelID="Microsoft.WindowsCalculator_8wekyb3d8bbwe!App" />
      </TopMFUApps>
    ```

5.  将 LayoutModification.xml 文件保存。

    一旦您已经创建的 LayoutModification.xml 文件，您需要将此文件放在使用 Windows ICD 或经典样式部署正确的系统位置。 有关如何执行此操作的详细信息，请参阅︰

    -   Windows ICD-实验室 1，第 7 步︰ 自定义开始布局
    -   经典样式部署-实验室 2a 步骤 5︰ 添加修改开始布局所需的文件

    如果不创建 LayoutModification.xml 文件并继续使用启动无人参与的设置，操作系统将使用无人参与的答案文件，并采取前 12 SquareTiles 或 DesktoporSquareTiles 中指定的设置无人参与文件。 系统将自动在新创建的组的这些图块开始的结尾 — — 前六个图块都放在第一的 OEM 组和第二组 6 个拼贴都放在第二个的 OEM 组。 如果在无人参与文件中指定 OEMName，则此元素的值用于命名将要创建的 OEM 组。

## <a name="span-idmicrophonesettingsspeechsettingcmdspanspan-idmicrophonesettingsspeechsettingcmdspanmicrophone-settings-speechsettingcmd"></a><span id="microphone_settings__speechsetting.cmd_"></span><span id="MICROPHONE_SETTINGS__SPEECHSETTING.CMD_"></span>麦克风设置 (SpeechSetting.cmd)


使用此脚本来调整设备的麦克风，为帮助最大化语音的功能，如 Cortana 的准确性。 若要了解如何测试您的设备的合适取值，请参阅硬件 WEG 在[Cortana 设备测试安装](https://msdn.microsoft.com/library/windows/hardware/dn957009)。

### <a name="speechsettingcmd"></a>SpeechSetting.cmd

``` syntax
@echo off
@echo.
@echo This script will set the Device.SpeechRecognition.DefaultMicGain values.
@echo.
 
setlocal
setlocal ENABLEDELAYEDEXPANSION
 
if "%1"=="" goto :InputPrompt
 call :tohex %1
@echo %_DECVAL% == 0x%_HEXVAL%
set /a Percentage=%_DECVAL%/100
 
set RegPath=HKLM\Software\Microsoft\Speech_OneCore\AudioInput\MicWiz
set RegKey=DefaultDefaultMicGain
set RegValue=0x%_HEXVAL%
 
@echo reg add %RegPath% /v %RegKey% /t REG_DWORD /d %RegValue% /f
reg add %RegPath% /v %RegKey% /t REG_DWORD /d %RegValue% /f
if %errorlevel% NEQ 0 echo Reg Add function failed. && goto :Error
@echo.
@echo Successfully set the MicGain value to %Percentage% percent.
@echo.
goto :end
 
:ToHex
     set _DECVAL=%1
     set _HEXVAL=
     set _VAL=%1
     if %1 LSS 0 (
         REM break the number into two parts so that we can output the
         REM full value within the bounds of a 32 bit signed value
         set /A _offset="-(-2147483647 - !_VAL!) + 2"
         set /A _VAL="!_offset! / 16 + 0x7FFFFFF"
         set /A _P="!_offset! %% 16 + 0xF"
 
         if !_P! GEQ 16 (
         set /A _VAL="!_VAL! + 1"
         set /A _P="!_P! %% 16"
         )
         if !_P! LEQ 9 set _HEXVAL=!_P!!_HEXVAL!
         if "!_P!" == "10" set _HEXVAL=A!_HEXVAL!
         if "!_P!" == "11" set _HEXVAL=B!_HEXVAL!
         if "!_P!" == "12" set _HEXVAL=C!_HEXVAL!
         if "!_P!" == "13" set _HEXVAL=D!_HEXVAL!
         if "!_P!" == "14" set _HEXVAL=E!_HEXVAL!
         if "!_P!" == "15" set _HEXVAL=F!_HEXVAL!
     )
 
     :hexloop
     set /A _P="%_VAL% %% 16"
     if %_P% LEQ 9 set _HEXVAL=%_P%%_HEXVAL%
     if "%_P%" == "10" set _HEXVAL=A%_HEXVAL%
     if "%_P%" == "11" set _HEXVAL=B%_HEXVAL%
     if "%_P%" == "12" set _HEXVAL=C%_HEXVAL%
     if "%_P%" == "13" set _HEXVAL=D%_HEXVAL%
     if "%_P%" == "14" set _HEXVAL=E%_HEXVAL%
     if "%_P%" == "15" set _HEXVAL=F%_HEXVAL%
     set /A _VAL="%_VAL% / 16"
     if "%_VAL%" == "0" goto :endloop
     goto :hexloop
 
:InputPrompt
      @echo.
      @echo Incorrect Usage.
      @echo.
      @echo Please input a decimal value as a parameter.
      @echo.
      @echo Example:
      @echo SpeechSetting.cmd 4200
      @echo.
      @echo This example sets the MicGain as 42 percent which is 0x1068.
      @echo.
goto :end
 
:Error
@echo.
@echo Error occurred.
@echo.
goto :end
 
:endloop
     set _offset=
     set _P=
     set _VAL=
goto :eof
 
:end 
```

## <a name="span-idremovewindowsappsspanspan-idremovewindowsappsspanspan-idremovewindowsappsspanremove-windows-apps"></a><span id="Remove_Windows_apps"></span><span id="remove_windows_apps"></span><span id="REMOVE_WINDOWS_APPS"></span>Windows 应用程序中移除


将语言包添加到映像中，当您需要删除并重新安装每个 Windows 应用程序，以确保它们包括语言资源。

下面是两个脚本，一个可用于脱机映像，从中移除应用程序，另一种可用于在审核模式下运行的图像中删除应用程序︰

### <a name="removeappsinofflineimagecmd"></a>删除\_应用程序\_在\_脱机\_image.cmd

此脚本假定的文件的名称是 install.wim，install.wim，即被修改的索引相同的文件夹中运行脚本\#1，并在其他索引位置没有其他 Windows 映像 (\#2， \#3），需要保留。

``` syntax
@echo off
@rem Run this script from the same folder that includes install.wim 
cls
md mount
dism /mount-image /mountdir:mount /imagefile:install.wim /index:1
if exist appx.txt del appx.txt
if exist applist.txt del applist.txt
if exist appremove.cmd del appremove.cmd
dism /image:mount /get-provisionedappxpackages > appx.txt
findstr /c:"PackageName" appx.txt > applist.txt
setlocal enabledelayedexpansion
set INTEXTFILE=applist.txt
set OUTTEXTFILE=appremove.cmd
set SEARCHTEXT=PackageName : 
set REPLACETEXT=dism /image:mount /remove-provisionedappxpackage /packagename:
set OUTPUTLINE=

for /f "tokens=1,* delims=¶" %%A in ( '"type %INTEXTFILE%"') do (
SET string=%%A
SET modified=!string:%SEARCHTEXT%=%REPLACETEXT%!

echo !modified! >> %OUTTEXTFILE%
)
del appx.txt
del applist.txt
call appremove.cmd
dism /unmount-image /mountdir:mount /commit
echo "Check to make sure operations completed successfully. If not, press Ctrl+C."
pause
ren install.wim install-temp.wim
dism /export-image /sourceimagefile:install-temp.wim /sourceindex:1 /destinationimagefile:install.wim
del install-temp.wim
```

### <a name="removeappsinauditmodecmd"></a>删除\_应用程序\_在\_审核\_mode.cmd

此脚本假定您正在引用的 PC 上运行在审核模式下。

``` syntax
@echo off
@rem Use MOUNT folder in folder where script is run 
cls
dism /mount-image /mountdir:mount /imagefile:install.wim /index:1
if exist appx.txt del appx.txt
if exist applist.txt del applist.txt
if exist appremove.cmd del appremove.cmd
dism /image:mount /get-provisionedappxpackages > appx.txt
findstr /c:"PackageName" appx.txt > applist.txt
setlocal enabledelayedexpansion
set INTEXTFILE=applist.txt
set OUTTEXTFILE=appremove.cmd
set SEARCHTEXT=PackageName : 
set REPLACETEXT=dism /image:mount /remove-provisionedappxpackage /packagename:
set OUTPUTLINE=

for /f "tokens=1,* delims=¶" %%A in ( '"type %INTEXTFILE%"') do (
SET string=%%A
SET modified=!string:%SEARCHTEXT%=%REPLACETEXT%!

echo !modified! >> %OUTTEXTFILE%
)
del appx.txt
del applist.txt
call appremove.cmd
dism /unmount-image /mountdir:mount /commit
ren install.wim install-temp.wim
dism /export-image /sourceimagefile:install-temp.wim /sourceindex:1 /destinationimagefile:install.wim
del install-temp.wim
```

## <a name="span-idboottoauditspanspan-idboottoauditspanspan-idboottoauditspanboottoaudit"></a><span id="BootToAudit"></span><span id="boottoaudit"></span><span id="BOOTTOAUDIT"></span>BootToAudit


将答案文件添加到 Windows 映像中 c:\\装载\\windows\\Windows\\黑豹\\unattend.xml 以指示它启动到审核模式。 您可以在 Windows 系统映像管理器创建此答案文件。

### <a name="boottoaudit-x64"></a>BootToAudit x64

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<unattend xmlns="urn:schemas-microsoft-com:unattend">
<!-- BootToAudit-x64.xml -->
    <settings pass="oobeSystem">
        <component name="Microsoft-Windows-Deployment" processorArchitecture="amd64" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
            <Reseal>
                <Mode>Audit</Mode>
            </Reseal>
        </component>
    </settings>
</unattend>
```

### <a name="boottoaudit-x86"></a>BootToAudit x86

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<unattend xmlns="urn:schemas-microsoft-com:unattend">
<!-- BootToAudit-x86.xml -->
    <settings pass="oobeSystem">
        <component name="Microsoft-Windows-Deployment" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
            <Reseal>
                <Mode>Audit</Mode>
            </Reseal>
        </component>
    </settings>
</unattend>
```

## <a name="span-idkeepingwindowssettingsthrougharecoveryspanspan-idkeepingwindowssettingsthrougharecoveryspanspan-idkeepingwindowssettingsthrougharecoveryspankeeping-windows-settings-through-a-recovery"></a><span id="Keeping_Windows_settings_through_a_recovery"></span><span id="keeping_windows_settings_through_a_recovery"></span><span id="KEEPING_WINDOWS_SETTINGS_THROUGH_A_RECOVERY"></span>将通过恢复 Windows 设置


通过 unattend.xml 安装文件时，创建的设置也不 Windows 开始菜单的自定义项使用 LayoutModification.xml 创建全系统重置，也不能从 oobe.xml 第一个登录信息期间，Windows 不会自动保存。

若要确保在保存您的自定义内容包含步骤将 unattend.xml、 LayoutModification.xml 和 oobe.xml 文件重新到位。 下面是一些示例脚本，说明如何保留这些设置并将它们放回适当的点。 Unattend.xml、 LayoutModification.xml、 oobe.xml，加上这些两个文本文件的副本保存在 c:\\恢复\\OEM\\:

### <a name="resetconfigxml"></a>ResetConfig.xml

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<!-- ResetConfig.xml -->
<Reset>
  <Run Phase="BasicReset_AfterImageApply">
    <Path>EnableCustomizationsAfterRecovery.cmd</Path>
    <Duration>2</Duration>
  </Run>
  <Run Phase="FactoryReset_AfterImageApply">
    <Path>EnableCustomizationsAfterRecovery.cmd</Path>
    <Duration>2</Duration>
  </Run>
</Reset>
```

### <a name="enablecustomizationsafterrecoverycmd"></a>EnableCustomizationsAfterRecovery.cmd

``` syntax
rem EnableCustomizationsAfterRecovery.cmd

rem Set the variable %TARGETOS%      (Typically this is C:\Windows)
for /F "tokens=1,2,3 delims= " %%A in ('reg query "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\RecoveryEnvironment" /v TargetOS') DO SET TARGETOS=%%C

rem Set the variable %TARGETOSDRIVE% (Typically this is C:)
for /F "tokens=1 delims=\" %%A in ('Echo %TARGETOS%') DO SET TARGETOSDRIVE=%%A

rem Add back Windows settings, Start menu, and OOBE.xml customizations
copy "%TARGETOSDRIVE%\Recovery\OEM\Unattend.xml" "%TARGETOS%\Panther\Unattend.xml" /y
copy "%TARGETOSDRIVE%\Recovery\OEM\LayoutModification.xml" "%TARGETOSDRIVE%\Users\Default\AppData\Local\Microsoft\Windows\Shell\LayoutModification.xml" /y
xcopy "%TARGETOSDRIVE%\Recovery\OEM\OOBE\Info" "%TARGETOS%\System32\Info\" /s

rem Recommended: Create a pagefile for devices with 1GB or less of RAM.
wpeutil CreatePageFile /path=%TARGETOSDRIVE%\PageFile.sys /size=256


rem EnableCustomizationsAfterRecovery.cmd
set ScriptFolder=%~dp0

for /f "skip=2 tokens=2,*" %%a in ('reg.exe query "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\RecoveryEnvironment" /v "TargetOS"') do set "TargetOS=%%b"
echo TargetOS: %TargetOS% >> %LogFile%
for %%A in (%TargetOS%) do set "TargetOSDrive=%%~dpA"

copy "%ScriptFolder%\Unattend.xml" "%TargetOSDrive%\Windows\Panther\Unattend.xml" /y
copy "%ScriptFolder%\LayoutModification.xml" "%TargetOSDrive%\Users\Default\AppData\Local\Microsoft\Windows\Shell\LayoutModification.xml" /y
copy "%ScriptFolder%\oobe.xml" "%TargetOSDrive%\System32\Info\Oobe.xml" /y
```

对于多语言部署 OOBE.xml 使用更复杂的文件夹结构。 没关系，只需将整个文件夹结构复制到 c:\\恢复\\OEM，然后修改该脚本以将整个文件夹复制︰

``` syntax
xcopy "%ScriptFolder%\Info\" "%TargetOSDrive%\System32\Info\" /s
```

若要了解有关使用点击式重新设置扩展点的更多信息，请参阅[添加脚本的按钮重置功能](http://go.microsoft.com/fwlink/?LinkId=618946)。

## <a name="span-idreinstallwindowsinboxappsspanreinstall-windows-inbox-apps-windows-10-version-1607"></a><span id="Reinstall_Windows_inbox_apps"></span>重新安装 Windows 的收件箱的应用程序 (Windows 10，1607年版本)

添加新语言后，请重新安装 Windows 的应用程序。 而不首先删除它们，可以重新安装应用程序。 

### <a name="reinstallinboxapps-x64cmd"></a>ReinstallInboxApps x64.cmd

``` syntax
DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.3DBuilder_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.3DBuilder_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.WindowsAlarms_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.WindowsAlarms_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.BingWeather_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.BingWeather_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.WindowsCalculator_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.WindowsCalculator_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.WindowsCamera_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.WindowsCamera_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.WindowsFeedbackHub_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.WindowsFeedbackHub_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.Getstarted_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.Getstarted_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.WindowsMaps_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.WindowsMaps_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.Messaging_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.Messaging_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.MicrosoftOfficeHub_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.MicrosoftOfficeHub_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx
DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.Office.OneNote_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.Office.OneNote_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.WindowsCommunicationsApps_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.WindowsCommunicationsApps_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.People_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.People_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.Windows.Photos_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.Windows.Photos_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.StorePurchaseApp_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.StorePurchaseApp_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.MicrosoftSolitaireCollection_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.MicrosoftSolitaireCollection_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x86.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.Advertising.Xaml.x64.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.Advertising.Xaml.x86.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.WindowsSoundRecorder_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.WindowsSoundRecorder_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.MicrosoftStickyNotes_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.MicrosoftStickyNotes_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.WindowsStore_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.WindowsStore_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.XboxApp_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.XboxApp_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.XboxIdentityProvider_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.XboxIdentityProvider_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.ZuneMusic_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.ZuneMusic_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.ZuneVideo_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.ZuneVideo_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.SkypeApp_kzf8qxf38zg5c.appxbundle /LicensePath:e:\apps\amd64\Microsoft.SkypeApp_kzf8qxf38zg5c.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.OneConnect_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.OneConnect_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x64.1.3.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.DesktopAppInstaller_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.DesktopAppInstaller_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx
```

### <a name="reinstallinboxapps-x86cmd"></a>ReinstallInboxApps x86.cmd

``` syntax
DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.3DBuilder_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.3DBuilder_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.WindowsAlarms_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.WindowsAlarms_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.BingWeather_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.BingWeather_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.WindowsCalculator_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.WindowsCalculator_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.WindowsCamera_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.WindowsCamera_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.WindowsFeedbackHub_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.WindowsFeedbackHub_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.Getstarted_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.Getstarted_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.WindowsMaps_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.WindowsMaps_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.Messaging_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.Messaging_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.MicrosoftOfficeHub_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.MicrosoftOfficeHub_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.Office.OneNote_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.Office.OneNote_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.WindowsCommunicationsApps_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.WindowsCommunicationsApps_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.People_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.People_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.Windows.Photos_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.Windows.Photos_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.StorePurchaseApp_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.StorePurchaseApp_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.MicrosoftSolitaireCollection_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.MicrosoftSolitaireCollection_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Runtime.x86.1.3.appx /DependencyPackagePath:e:\apps\x86\Microsoft.Advertising.Xaml.x86.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.WindowsSoundRecorder_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.WindowsSoundRecorder_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.MicrosoftStickyNotes_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.MicrosoftStickyNotes_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.WindowsStore_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.WindowsStore_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.XboxApp_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.XboxApp_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.XboxIdentityProvider_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.XboxIdentityProvider_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.ZuneMusic_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.ZuneMusic_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.ZuneVideo_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.ZuneVideo_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.SkypeApp_kzf8qxf38zg5c.appxbundle /LicensePath:e:\apps\x86\Microsoft.SkypeApp_kzf8qxf38zg5c.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.OneConnect_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.OneConnect_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Framework.x86.1.3.appx /DependencyPackagePath:e:\apps\x86\Microsoft.NET.Native.Runtime.x86.1.3.appx

DISM /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\x86\Microsoft.DesktopAppInstaller_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\x86\Microsoft.DesktopAppInstaller_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\x86\Microsoft.VCLibs.x86.14.00.appx
```


 