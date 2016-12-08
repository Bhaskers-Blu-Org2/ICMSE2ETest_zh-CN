---
author: Justinha
Description: Push-button reset features are included with Windows 10 for desktop editions (Home, Pro, Enterprise, and Education), though you'll need to perform additional steps to deploy PCs with the following customizations.
ms.assetid: f23d7e3f-0254-4fe8-9d61-5a58856c74be
MSHAttr: PreferredLib:/library/windows/hardware
title: "将按钮重置功能的部署"
ms.openlocfilehash: 3849dc9bd5eadc46f9474973799b12548fa00002
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="deploy-push-button-reset-features"></a>将按钮重置功能的部署


点击式重置功能都将包括使用 Windows 10 桌面版 （家庭、 Pro、 企业和教育），但可能需要执行额外步骤将使用下列自定义部署的 Pc。

-   Windows 桌面应用程序
-   Windows 设置，例如自定义 OOBE 屏幕或开始菜单。
-   自定义的分区布局。

这些步骤还演示了如何在重置捕获日志或执行其他清理任务过程中添加您自己的脚本。

## <a name="span-idprerequisitesspanspan-idprerequisitesspanspan-idprerequisitesspanprerequisites"></a><span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>系统必备组件


若要完成这些过程，您需要技术人员计算机的 Windows 10 组件安装有 Windows 10 以下 Windows 评估和部署工具包 (ADK):

-   部署工具
-   Windows 预安装环境 (Windows PE)
-   图像处理和配置设计器 (ICD)
-   用户状态迁移工具 (USMT)

您将需要︰

-   目标计算机的驱动器大小 100 GB 或更大
-   Windows 桌面版本图像 (install.wim) 10
-   Windows RE 启动映像 (Winre.wim) （将从 Windows 10 图像提取这）。

整个部署过程的概述，请参阅[桌面制造指南](http://go.microsoft.com/fwlink/p/?LinkId=526101)。

使用以下步骤准备扫描状态工具，安装完毕后捕获 Windows 桌面应用程序︰

**第 1 步︰ 准备扫描状态工具**

1.  在技术人员计算机上，将 Windows ADK 文件从 Windows 用户状态迁移工具 (USMT) 和 Windows 安装程序复制到工作文件夹。 您将需要与目标设备的体系结构相匹配。 您不需要复制子文件夹。

    ``` syntax
    md C:\ScanState_amd64
    xcopy /E "C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\User State Migration Tool\amd64" C:\ScanState_amd64
    xcopy /E /Y "C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Setup\amd64\Sources" C:\ScanState_amd64
    ```

2.  在某些情况下，Windows Defender 设置和检测历史记录可能捕获到的自定义软件包扫描状态工具。 这可能会导致冲突的文件，因为恢复过程失败，将导致计算机重新启动并重复输入"安装 Windows"阶段。 这些后续步骤将会阻止 Windows Defender 设置捕获。

    1.  在运行 Windows 10 台 PC 上使用扫描状态工具，生成配置文件︰

        ``` syntax
        ScanState.exe /apps /genconfig:C:\pbr_config.xml 
        ```

    2.  在记事本中打开配置文件
    3.  搜索配置文件中的以下行︰

        ``` syntax
        <component displayname="Windows-Defender-AM-Sigs" migrate="yes"… 
        <component displayname="Windows-Defender-AM-Engine" migrate="yes"… 
        <component displayname="Security-Malware-Windows-Defender" migrate="yes"… 
        ```

    4.  修改"移植"值从"是"与"否"的每一行。 例如︰

        ``` syntax
        <component displayname="Windows-Defender-AM-Sigs" migrate="no"… 
        <component displayname="Windows-Defender-AM-Engine" migrate="no"… 
        <component displayname="Security-Malware-Windows-Defender" migrate="no"… 
        ```

        在本主题后面部分中的步骤 10 中，您将指定配置文件，当您使用扫描状态捕获到.ppkg 文件的自定义项。

    5.  保存并关闭该配置文件。

3.  工作文件夹的内容复制到某个网络位置或 USB 闪存驱动器。

使用以下步骤自定义 Windows RE 引导映像，如果需要其他驱动程序和语言包。

**步骤 2︰ 提取和自定义 Windows RE 启动映像 （可选）**

1.  在技术人员计算机上，单击**开始**并键入部署。 用鼠标右键单击**部署和图像处理工具环境**，然后选择**以管理员身份运行**。
2.  在**部署和图像处理工具环境**，创建的文件夹结构来存储 Windows 映像，它的装载点。

    ``` syntax
    Mkdir C:\OS_image\mount
    ```

3.  创建的文件夹结构来存储 Windows RE 启动映像和其挂载点。

    ``` syntax
    Mkdir C:\winre_amd64\mount
    ```

4.  装载到该文件夹的 Windows 映像 (install.wim) \\OS\_图像\\使用 DISM 装载。

    ``` syntax
    Dism /mount-image /imagefile:C:\OS_image\install.wim /index:1 /mountdir:C:\OS_image\mount
    ```

    其中`Index:1`Install.wim 文件中的所选图像的索引。

5.  安装的 Windows 映像的 Windows RE 映像复制到新文件夹中。

    ``` syntax
    xcopy /H C:\OS_image\mount\windows\system32\recovery\winre.wim C:\winre_amd64 
    ```

6.  卸载 Windows 映像。 提示︰ 如果您没有 Windows 映像中进行任何其他更改，您可以卸载映像更快地使用`/discard`选项。

    ``` syntax
    Dism /unmount-image /mountdir:C:\OS_image\mount /discard
    ```

7.  装载 Windows RE 引导映像以进行编辑。

    ``` syntax
    Dism /mount-image /imagefile:C:\winre_amd64\winre.wim /index:1 /mountdir:C:\winre_amd64\mount
    ```

    其中`Index:1`是 Winre.wim 文件中的所选图像的数字。

    一旦从 Install.wim 文件中提取 Winre.wim 文件，您可以自定义 Windows RE 引导映像。

8.  将语言包、 引导所必需设备驱动程序和输入的设备驱动程序添加到 Windows RE 引导映像。 若要了解详细信息，请参阅[自定义 Windows RE](customize-windows-re.md)。
9.  提交您的自定义并卸载映像。

    ``` syntax
    Dism /unmount-image /mountdir:C:\winre_amd64\mount /commit 
    ```

如果您计划自定义通用的所有版本的 Windows 10 （包括 Windows 10 Mobile） 的设置，使用以下步骤创建的配置包的指定要在恢复过程中恢复设置︰

**步骤 3︰ 创建资源调配包与要恢复的设置 （可选）**

1.  在技术人员计算机上启动 Windows 映像以及配置设计器 (ICD)。
2.  单击**文件** &gt; **新的项目**。
3.  输入项目名称和说明，然后单击**下一步**
4.  在**选择项目工作流**步骤中，选择**资源调配包**选项，，然后单击**下一步**。
5.  在**选择的设置可查看和配置**步骤中，选择**共有的所有 Windows 版本**的选项，，然后单击**下一步**。
6.  在**导入资源调配包 （可选）**步骤中，请单击**完成**以创建新的项目。
7.  使用**可用的自定义**窗格中添加设置，并指定应在恢复过程中恢复默认值。 这些设置将显示在**所选自定义项**窗格中。
8.  单击**导出** &gt; **资源调配包**。
9.  在**描述资源调配的包**步骤中，单击**下一步**。
10. 在**选择设置包的安全详细信息**步骤中，单击**下一步**。
11. 在**选择资源调配将包保存到的位置**步骤中，输入要保存的软件包 （如网络共享），然后单击**下一步**的位置。
12. 单击**生成**以创建资源调配的包。
13. 设置包创建后，单击**完成**。

如果您的自定义设置包括设置特定于桌面版本的 Windows 10 版，使用以下步骤创建 unattend.xml 指定这些设置，以在恢复过程中恢复︰

**步骤 4︰ 创建无人参与文件还原设置 （可选）**

1.  在技术人员计算机上，启动**Windows 系统映像管理器**。
2.  单击**文件** &gt; **选择的 Windows 映像**。
3.  当系统提示您创建一个目录文件，请单击**是**。
4.  使用**Windows 映像**和**应答文件**窗格将设置添加到专业化或 oobeSystem 阶段 （或两者），并指定应在恢复过程中恢复默认值。
5.  单击**工具** &gt; **验证答案文件**以检查是否有错误。 更正标识的任何问题。
6.  单击**文件** &gt; **保存答案文件**。 输入要保存的应答文件 （如网络共享），然后单击**保存**的位置。

如果您计划使用点击式重新设置扩展点，可以使用以下步骤准备扩展脚本并将它们使用点击式重置配置文件注册。

**重要** 如果您具有创建无人参与文件，您还必须创建脚本以重新应用它使用 BasicReset\_AfterImageApply 和 FactoryReset\_AfterImageApply 扩展点。

 

**第 5 步︰ 准备按钮重置扩展性脚本 （可选）**

1.  创建刷新您的 PC 功能运行时，在可用的扩展点运行的脚本 (.cmd) 或可执行文件 (.exe):

    答︰ 在 BasicReset\_BeforeImageApply

    B︰ 在 BasicReset\_AfterImageApply

2.  创建重新设置您的 PC 功能在运行时在可扩展性点运行的脚本 (.cmd) 或可执行文件 (.exe):

    C︰ 在 FactoryReset\_AfterDiskFormat

    D︰ 在 FactoryReset\_AfterImageApply

3.  将脚本保存到网络位置或 USB 闪存驱动器。
4.  创建的 ResetConfig.xml 文件中指定的脚本，您创建了四个扩展性点的位置。 例如︰

    ``` syntax
    <?xml version="1.0" encoding="utf-8"?>
    <Reset>
        <Run Phase="BasicReset_BeforeImageApply">
            <Path>Fabrikam\SampleScript_A.cmd</Path>
            <Duration>2</Duration>
        </Run>
        <Run Phase="BasicReset_AfterImageApply">
            <Path>Fabrikam\SampleScript_B.cmd</Path>
            <Param></Param>
            <Duration>2</Duration>
        </Run>
        <Run Phase="FactoryReset_AfterDiskFormat">
            <Path>Fabrikam\SampleScript_C.cmd</Path>
            <Duration>2</Duration>
        </Run>
        <Run Phase="FactoryReset_AfterImageApply">
            <Path>Fabrikam\SampleScript_D.cmd</Path>
            <Param></Param>
            <Duration>2</Duration>
        </Run>
    </Reset>
    ```

    **重要** 如果您使用文本编辑器来创作的 ResetConfig.xml 文件，使用.xml 文件扩展名保存文档，并使用**utf-8 编码**。 不使用 Unicode 或 ANSI。

     

5.  保存 ResetConfig.xml 文件以及您创建的扩展脚本。

**第 6 步︰ 创建裸机恢复配置 （可选）**

-   要指定当用户执行裸机恢复使用通过他们的 Pc 上创建恢复媒体使用的分区布局，请修改 resetconfig.xml 包括以下元素︰

    ``` syntax
    <?xml version="1.0" encoding="utf-8"?>
    <Reset>
                <SystemDisk>
            <MinSize>160000</MinSize>
            <DiskpartScriptPath>ReCreatePartitions.txt</DiskpartScriptPath>
            <OSPartition>3</OSPartition>
            <WindowsREPartition>4</WindowsREPartition>
            <WindowsREPath>Recovery\WindowsRE</WindowsREPath>
            <Compact>False</Compact>
    </SystemDisk>
    </Reset>
    ```

    -   **MinSize** -指定系统磁盘的最小大小，以兆字节 (MB)。 如果系统磁盘不满足此最小大小，则不会继续恢复过程。
    -   **DiskpartScriptPath** -相对于 install.wim 位置的 Diskpart 脚本路径。 该脚本应假设所有现有分区已被删除，而系统磁盘在 Diskpart 中具有焦点。
    -   **OSPartition** -恢复映像将应用于的分区，则必须指定它。 ESP 或活动分区必须是同一磁盘操作系统上。
    -   **WindowsREPartition**;**– WindowsREPath**（可选）应在其中装载 WinRE 位置。 媒体上的 WinRE 启动映像将被复制并向操作系统注册。 （等同于运行"reagentc.exe /setreimage"）

    如果在 resetconfig.xml 中，未指定分区信息，用户仍然可以执行裸机恢复使用他们所创建的介质。 但是，将改为使用 Windows 10 / 建议默认的分区布局。

**第 7 步︰ 创建初始部署的 diskpart 脚本**

1.  创建磁盘分区的初始部署的脚本。

    **（uefi） 的示例**︰

    ``` syntax
    rem These commands are used with DiskPart tool.
    rem Erase the drive and create four partitions
    rem for a UEFI/GPT-based PC.
    select disk 0
    clean
    convert gpt
    rem == 1. System Partition =======================
    create partition efi size=100
    rem ***NOTE: For 4KB-per-sector drives, change 
    rem this value to size=260.***
    format quick fs=fat32 label="System"
    assign letter="S"
    rem == 2. Microsoft Reserved (MSR) Partition =====
    create partition msr size=16
    rem == 3. Windows Partition ======================
    rem ==    a. Create Windows Partition ============
    create partition primary
    rem ==    b. Create space for Windows RE tools partition
    shrink minimum=450
    rem ==    c. Prepare the Windows partition
    format quick fs=ntfs label="Windows"
    assign letter="W"
    rem == 4. Windows RE Tools Partition =============
    create partition primary
    format quick fs=ntfs label="Windows RE tools"
    set id=de94bba4-06d1-4d40-a16a-bfd50179d6ac
    assign letter="T"
    exit
    ```

    **BIOS 的示例**︰

    ``` syntax
    rem These commands are used with DiskPart to 
    rem erase the drive and create three partitions 
    rem for a BIOS/MBR-based PC. 
    rem Adjust the partition sizes to fill the drive.
    select disk 0
    clean
    rem === 1. System Partition =====================
    create partition primary size=100
    format quick fs=ntfs label="System"
    assign letter="S" 
    active 
    rem === 2. Windows Partition ====================
    rem ==    a. Create Windows partition ===========
    create partition primary 
    rem ==    b. Create space for Windows RE tools partition ====
    shrink minimum=450
    rem ==    c. Prepare the Windows partition ======
    format quick fs=ntfs label="Windows" 
    assign letter="W" 
    rem === 3. Windows RE Tools Partition =============
    create partition primary
    format quick fs=ntfs label="Windows RE tools"
    set id=27
    assign letter="R" 
    exit
    ```

2.  命名的脚本 CreatePartitions UEFI 或 CreatePartitions-BIOS.txt，并将其保存到网络位置或 USB 闪存驱动器。 注意︰ 在 Diskpart 这些示例中，分区指派的字母 s:\\，w:\\，和 t:\\简化分区标识。 计算机重新启动后，Windows PE 自动分配的盘符 c:\\到 Windows 分区。 其他分区不接收驱动器号。

**第 8 步︰ 创建用于裸机恢复的 diskpart 脚本 （可选）**

**第 8 步︰ 创建用于裸机恢复的 diskpart 脚本 （可选）**

1.  创建用于裸机恢复的 diskpart 脚本。

    **重要**不应包括用于裸机恢复的 diskpart 脚本`select disk`或`clean`命令。 Diskpart 脚本处理之前，将自动选择系统磁盘。

    **（uefi） 的示例**︰

    ``` syntax
    rem These commands are used with DiskPart tool.
    rem Erase the drive and create five partitions
    rem for a UEFI/GPT-based PC.
    convert gpt
    rem == 1. System Partition =======================
    create partition efi size=100
    rem ***NOTE: For 4KB-per-sector drives, change 
    rem this value to size=260.***
    format quick fs=fat32 label="System"
    assign letter="S"
    rem == 2. Microsoft Reserved (MSR) Partition =====
    create partition msr size=16
    rem == 3. Windows Partition ======================
    rem ==    a. Create Windows Partition ============
    create partition primary
    rem ==    b. Create space for Windows RE tools partition
    shrink minimum=450
    rem ==    c. Prepare the Windows partition
    format quick fs=ntfs label="Windows"
    assign letter="W"
    rem == 4. Windows RE Tools Partition =============
    create partition primary
    format quick fs=ntfs label="Windows RE tools"
    set id=de94bba4-06d1-4d40-a16a-bfd50179d6ac
    assign letter="T"
    exit
    ```
    
    **BIOS 的示例**︰

    ``` syntax
    rem These commands are used with DiskPart to 
    rem erase the drive and create three partitions 
    rem for a BIOS/MBR-based PC. 
    rem Adjust the partition sizes to fill the drive.
    rem === 1. System Partition =====================
    create partition primary size=100
    format quick fs=ntfs label="System"
    assign letter="S" 
    active 
    rem === 2. Windows Partition ====================
    rem ==    a. Create Windows partition ===========
    create partition primary 
    rem ==    b. Create space for Windows RE tools partition ====
    shrink minimum=450
    rem ==    c. Prepare the Windows partition ======
    format quick fs=ntfs label="Windows" 
    assign letter="W" 
    rem === 3. Windows RE Tools Partition =============
    create partition primary
    format quick fs=ntfs label="Windows RE tools"
    set id=27
    assign letter="R" 
    exit
    ```

2.  脚本 RecreatePartitions UEFI.txt 或 RecreatePartitions-BIOS.txt，命名并保存到相同的网络位置或 USB 闪存驱动器创建分区。

**步骤 9︰ 部署和自定义 Windows**

1.  在目标计算机上，启动 Windows PE。
2.  在 Windows PE 的命令提示符下运行该脚本来创建建议的硬盘分区。

    ``` syntax
    Diskpart /s N:\CreatePartitions.txt
    ```

    其中 n:\\CreatePartition 是该文件的位置。

3.  适用于 Windows 分区的 Windows 参考映像。

    ``` syntax
    Dism /Apply-Image /ImageFile:N:\Install.wim /Index:1 /ApplyDir:W:\
    ```

    可选︰ 您还可以指定 /compact 选项以便写入的文件压缩磁盘。 例如︰

    ``` syntax
    Dism /Apply-Image /ImageFile:N:\Install.wim /Index:1 /ApplyDir:W:\ /Compact:on
    ```

    如果您正在部署 Windows Pc 上的存储容量有限，但建议不要在电脑上旋转的存储设备，这很有用。

4.  通过使用 BCDboot 配置系统分区。

    ``` syntax
    W:\Windows\System32\Bcdboot W:\Windows
    ```

5.  创建一个文件夹，在 Windows RE 工具分区中，并将自定义 Windows RE 引导映像复制到其中。

    ``` syntax
    Mkdir T:\Recovery\WindowsRE
    xcopy /H N:\Winre.wim T:\Recovery\WindowsRE
    ```

    其中 t:\\是 Windows RE 工具分区。

    **重要** 必须将存储在 Winre.wim\\恢复\\WindowsRE。

     

6.  注册与 Windows 映像的 Windows RE 启动映像。

    ``` syntax
    W:\Windows\System32\Reagentc /setreimage /path T:\Recovery\WindowsRE /target W:\Windows
    ```

7.  使用 Diskpart，可以隐藏 Windows RE 工具 (t:\\) 从 Windows 资源管理器中的分区。

    **基于 UEFI 的计算机︰**

    ``` syntax
    select disk 0
    select partition 4
    remove
    set id=de94bba4-06d1-4d40-a16a-bfd50179d6ac
    gpt attributes=0x8000000000000001
    exit
    ```

    **基于 BIOS 的计算机︰**

    ``` syntax
    select disk 0
    select partition 3
    remove
    set id=27
    exit
    ```

8.  自定义目标计算机上的 Windows 映像︰
    1.  执行脱机 Windows 映像，如特定的基于 INF 驱动程序程序包安装到目标计算机，安装操作系统更新和语言包或其他 Windows 应用程序的资源调配的自定义设置。
    2.  启动目标 PC 进入审核模式。 这可以通过使用与在 Microsoft Windows 部署的应答文件 |重新封装 |模式 = 审核设置，或先启动 PC 至 OOBE，，然后按 CTRL + SHIFT + F3。
    3.  执行任何剩余的自定义，例如安装应用程序和特定于目标电脑的设备软件程序包。

9.  如果您已经安装了操作系统更新，清理被取代的组件和标记作为永久更新，以便他们将在恢复过程中恢复︰

    ``` syntax
    DISM.exe /Cleanup-Image /StartComponentCleanup /ResetBase
    ```

**第 10 步︰ 捕获和部署自定义的恢复**

1.  使用扫描状态工具来捕获到一个包中提供的已安装自定义项。 /Config 选项用于前面在本主题中，步骤 1 中指定您所修改的配置文件，并将.ppkg 文件保存在 c: 文件夹\\恢复\\的自定义设置。

    ``` syntax
    D:\ScanState_amd64\scanstate.exe /apps /config:<path_to_config_file> /ppkg C:\Recovery\Customizations\apps.ppkg /o /c /v:13 /l:C:\ScanState.log
    ```

    其中 n:\\是在步骤 1 中安装扫描状态工具的位置。

2.  如果 Windows ICD 具有用于创建额外的供应包应恢复在恢复过程中的自定义操作，请将包复制到目标计算机。 例如︰

    ``` syntax
    xcopy N:\RecoveryPPKG\*.ppkg C:\Recovery\Customizations
    ```

    其中 n:\\是其他资源调配程序包的位置。

3.  将任何按钮重置配置文件 (resetconfig.xml) 和可扩展性的脚本复制到目标计算机，然后配置写/修改它们的权限。 例如︰

    ``` syntax
    mkdir C:\Recovery\OEM
    xcopy /E N:\RecoveryScripts\* C:\Recovery\OEM
    ```

    其中 n:\\是配置文件和脚本所处的位置。

4.  限制的自定义项，写/更改权限和隐藏的根文件夹。 例如︰

    ``` syntax
    icacls C:\Recovery\Customizations /inheritance:r /T
    icacls C:\Recovery\Customizations /grant:r SYSTEM:(F) /T
    icacls C:\Recovery\Customizations / grant:r *S-1-5-32-544:(F) /T
    icacls C:\Recovery\OEM /inheritance:r /T
    icacls C:\Recovery\OEM /grant:r SYSTEM:(F) /T
    icacls C:\Recovery\OEM / grant:r *S-1-5-32-544:(F) /T
    attrib +H C:\Recovery
    ```

5.  使用 Sysprep 工具重新封装 Windows 映像，而无需使用 / 一般化选项。

    ``` syntax
    Sysprep /oobe /exit
    ```

    **请注意** 重要提示︰ 您必须配置的图像，被传送到客户引导到 OOBE。

     

6.  （可选）为了节省空间，您可以将转换文件指针引用的自定义软件包已安装的 Windows 桌面应用程序。 为此，请引导到 Windows PE 的目标 PC 并运行下面的命令︰

    ``` syntax
    DISM /Apply-CustomDataImage /CustomDataImage:C:\Recovery\Customizations\USMT.ppkg /ImagePath:C:\ /SingleInstance
    ```

7.  关闭目标电脑的包装和装运。 当用户首次启动 PC 时，系统将引导至 OOBE。

**第 11 步︰ 验证您的自定义**

1.  请验证您的自定义，还原恢复之后，他们继续通过您的 PC 运行刷新的功能将您从以下的入口点的 PC 功能重置︰

    **设置︰**从开始菜单上，单击**设置&gt;更新和安全&gt;恢复**。 单击**重置此电脑**下的**开始**按钮，然后按照屏幕上的说明。

    **Windows RE**︰ 从选择 Windows RE 选项屏幕单击**疑难解答&gt;重置此电脑**，然后按照屏幕说明

2.  **验证恢复介质可以创建，然后通过运行的裸机恢复功能来验证其功能︰**

    1.  启动创建控制面板中的恢复驱动器。
    2.  请按照屏幕上的说明创建 USB 恢复驱动器。
    3.  从 USB 恢复驱动器启动计算机
    4.  从选择选项屏幕中，单击**疑难解答**
    5.  单击**恢复从驱动器**中，然后按照屏幕上的说明

    **请注意** 依靠以点击方式重置用户界面重新设计了在 Windows 10。 **将文件保存**选项用户界面中的现在对应于**刷新您的 PC**功能，而**删除所有内容**的选项对应于**重置您的 PC**功能。

     

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[扫描状态语法](http://go.microsoft.com/fwlink/p/?linkid=615076)

[裸露金属的重置恢复︰ 在部署新设备的过程创建恢复媒体](create-media-to-run-push-button-reset-features-s14.md)

[部署使用扫描状态的按钮重置功能](http://go.microsoft.com/fwlink/?LinkId=615126)

 

 






