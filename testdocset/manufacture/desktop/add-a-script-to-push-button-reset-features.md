---
author: Justinha
Description: "配置扩展点，可以自定义的按钮重置体验。 这使您可以运行自定义脚本、 安装其他应用程序，或保留其他用户或应用程序数据。"
ms.assetid: 147358d0-bae5-4f48-b02d-1ccc48bdcc2e
MSHAttr: PreferredLib:/library/windows/hardware
title: "将脚本添加到按钮重置功能"
ms.openlocfilehash: 33e585a4e4c115b340c84a3c8c32f4a676fc5894
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add-a-script-to-push-button-reset-features"></a>将脚本添加到按钮重置功能


配置扩展点，可以自定义的按钮重置体验。 这使您可以运行自定义脚本、 安装其他应用程序，或保留其他用户或应用程序数据。

## <a name="span-idprerequisitesspanspan-idprerequisitesspanspan-idprerequisitesspanprerequisites"></a><span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>系统必备组件


要配置扩展点和自定义按钮重置体验，您需要以下各项。

-   一个名为 ResetConfig.xml 的配置文件
-   执行自定义操作的脚本选择扩展点。
-   这些脚本所需的任何其他文件

每个脚本必须满足以下要求︰

-   是一个可执行文件 (.exe) 或命令脚本 (.cmd)
-   运行时不显示图形用户界面 (GUI)
-   返回 0 以表示操作成功，或是一个非零值，以指示不成功的操作

这些文件应该放在 c: 文件夹\\恢复\\OEM 和按钮重置功能会自动检测。 它是确定要使用的子文件夹。

## <a name="span-idstep1creatingconfigurationfilestoprepareforrecoveryspanspan-idstep1creatingconfigurationfilestoprepareforrecoveryspanspan-idstep1creatingconfigurationfilestoprepareforrecoveryspanstep-1-creating-configuration-files-to-prepare-for-recovery"></a><span id="Step_1__Creating_Configuration_Files_to_Prepare_for_Recovery"></span><span id="step_1__creating_configuration_files_to_prepare_for_recovery"></span><span id="STEP_1__CREATING_CONFIGURATION_FILES_TO_PREPARE_FOR_RECOVERY"></span>步骤 1︰ 创建配置文件，来为恢复做准备


**若要创建扩展脚本**

-   在记事本中，您可以创建自定义脚本来保存或检索日志文件，请检查分区，并安装应用程序。

    **重要**  
    您的脚本必须满足以下要求︰

    -   脚本的格式设置为.cmd 或.exe 文件。
    -   这些脚本不依赖默认 Windows RE 映像 (winre.wim) 中不存在的 Windows PE 可选组件。
    -   这些脚本不依赖于二进制文件 （如.exe 或.dll 文件），在默认的 Windows RE 图像 (winre.wim) 中不存在。
    -   不显示图形用户界面 (GUI) 而运行的脚本。
    -   这些脚本在每个扩展性点的 5 分钟内完成所有预定的功能。
    -   该脚本不能修改的驱动器号。 这可能会导致恢复失败。

    如果成功，您的脚本必须返回 0 （零）。 如果按钮重置会收到一个非 0 值，将发生以下步骤︰

    -   **如果运行刷新您的 PC 的功能**︰ 系统的所有更改都将都回滚。 如果从 Windows **PC 设置**菜单启动脚本或可执行文件，在 Windows 中重新启动系统。 如果从 Windows RE 或**启动选项**菜单启动该脚本或可执行文件，系统将仍保留在 Windows RE，并显示一条错误消息。

    -   **如果运行重置您的 PC 的功能**︰ 该故障将被忽略。 脚本或可执行文件在重置过程中下一步将继续和日志失败。

    如果需要可用于存储在以下位置。

    -   **Windows PE RAM 驱动器 （x:）**。 这个虚拟的驱动器创建的 Windows PE 并**刷新您的 PC**的过程中将保持活动状态。 可用于它**刷新您的 PC**功能分区被刷新，并要在该分区后恢复数据刷新已完成之前保存数据。 可用内存量仅限于在系统上，Windows RE 工具完全展开时所需的 RAM 的量减去 RAM 量。 有关安装 Windows RE 和确定完全展开的文件大小的说明，请参阅[自定义 Windows RE](customize-windows-re.md)。

    -   **指定 OEM 分区**。 可以在分区上保留额外空间。 例如，可以恢复图像分区、 上留出空间，并使用脚本来临时指派一个驱动器号，然后将文件保存到该分区。 但是，如果您的用户使用恢复介质对磁盘重新分区，这些分区上的数据可能会丢失在恢复过程中。

     

    **示例 1︰ 保存日志文件**

    此示例脚本保留将否则被删除，通过将它们放在内存中，可以通过另一个示例脚本，可检索到一个临时位置中的文件**RetrieveLogFiles.cmd**。

    ``` syntax
    :rem == SaveLogFiles.cmd

    :rem == This sample script preserves files that would 
    :rem    otherwise be removed by placing them in a 
    :rem    temporary location in memory, to be retrieved by
    :rem    RetrieveLogFiles.cmd.

    :rem == 1. Use the registry to identify the location of
    :rem       the new operating system and the primary hard
    :rem       drive. For example, 
    :rem       %TARGETOS% may be defined as C:\Windows
    :rem       %TARGETOSDRIVE% may be defined as C:
    for /F "tokens=1,2,3 delims= " %%A in ('reg query "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\RecoveryEnvironment" /v TargetOS') DO SET TARGETOS=%%C

    for /F "tokens=1 delims=\" %%A in ('Echo %TARGETOS%') DO SET TARGETOSDRIVE=%%A

    :rem == 2. Copy old logs to a temporary folder in memory
    mkdir X:\Temp
    xcopy %TARGETOS%\Logs\*.* X:\temp /cherkyi

    EXIT 0
    ```

    **示例 2︰ 检索日志文件**

    此示例脚本将检索已保存在内存中的文件`SaveLogFiles.cmd`编写脚本，并将其添加回系统。 它也运行系统诊断程序，，然后将输出发送到 c:\\Fabrikam 文件夹。

    ``` syntax
    :rem == RetrieveLogFiles.cmd

    :rem == This sample script retrieves the files that 
    :rem    were saved in memory by 
    :rem    SaveLogFiles.cmd,
    :rem    and adds them back to the system.
    :rem
    :rem    It also runs a system diagnostic, and sends the output
    :rem    to the C:\Fabrikam folder.


    :rem == 1. Use the registry to identify the location of
    :rem       the new operating system and the primary drive.
    :rem        
    :rem       %TARGETOS% is the Windows folder 
    :rem          (This later becomes C:\Windows)
    :rem       %TARGETOSDRIVE% is the Windows partition 
    :rem          (This later becomes C:)
    for /F "tokens=1,2,3 delims= " %%A in ('reg query "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\RecoveryEnvironment" /v TargetOS') DO SET TARGETOS=%%C
    for /F "tokens=1 delims=\" %%A in ('Echo %TARGETOS%') DO SET TARGETOSDRIVE=%%A

    :rem == 2. Copy the old logs to the new OS 
    :rem       at C:\Windows\OldLogs
    mkdir %TARGETOS%\OldLogs
    xcopy X:\Temp\*.* %TARGETOS%\OldLogs /cherkyi

    :rem == 3. Run system diagnostics using the
    :rem       DirectX Diagnostic tool, and save the 
    :rem       results to the C:\Fabrikam folders. ==

    mkdir %TARGETOSDRIVE%\Fabrikam
    %TARGETOS%\system32\dxdiag.exe /whql:off /t %TARGETOSDRIVE%\Fabrikam\DxDiag-TestLogFiles.txt

    EXIT 0
    ```

**若要创建按钮重置配置文件**

1.  在记事本中，创建一个指向按钮重置扩展性脚本的配置文件 (ResetConfig.xml)。 有关此文件的详细信息，请参阅[ResetConfig XML 参考](resetconfig-xml-reference-s14.md)。

    ``` syntax
    <?xml version="1.0" encoding="utf-8"?>
    <!-- ResetConfig.xml -->
       <Reset>
          <Run Phase="BasicReset_BeforeImageApply">
             <Path>SaveLogFiles.cmd</Path>
             <Duration>4</Duration>
          </Run>      
          <Run Phase="BasicReset_AfterImageApply">
             <Path>RetrieveLogFiles.cmd</Path>
             <Duration>2</Duration>
          </Run>
          <Run Phase="FactoryReset_AfterDiskFormat">
             <Path>CheckPartitions.exe</Path>
             <Duration>2</Duration>
          </Run>
          <Run Phase="FactoryReset_AfterImageApply">
             <Path>InstallApps.cmd</Path>
             <Param>/allApps</Param>
             <Duration>2</Duration>
          </Run>
          <!-- May be combined with Recovery Media Creator
               configurations – insert SystemDisk element here -->
       </Reset>
    ```

    其中 SaveLogFiles.cmd、 RetrieveLogFiles.cmd、 CheckPartitions.exe 和 InstallApps.cmd 是所有虚构的脚本。

2.  单击**文件**，然后单击**另存为**。 在**编码**框中，选择**utf-8**，，然后将此文件另存为 e:\\恢复\\RecoveryImage\\ResetConfig.xml。

    其中*E*是 USB 闪存驱动器或其他可移动媒体的驱动器号。 不要使用 ANSI 编码。

    **请注意**  
    同一个 ResetConfig.xml 文件可用于将 Windows 配置为创建恢复媒体。 有关详细信息，请参阅[部署 Push-Button 重置功能](deploy-push-button-reset-features.md)。

     

## <a name="span-idbkmk4spanspan-idbkmk4spanstep-2-adding-configuration-files-and-scripts-to-the-destination-computer"></a><span id="bkmk_4"></span><span id="BKMK_4"></span>步骤 2︰ 将配置文件和脚本添加到目标计算机


**若要添加您的配置文件和脚本**

1.  在目标计算机上，使用配置文件中插入 USB 闪存驱动器。

2.  将配置文件复制到目标计算机

    ``` syntax
    Copy E:\Recovery\RecoveryImage\* R:\RecoveryImage\*
    ```

    其中*E*是 USB 闪存驱动器的驱动器号。

## <a name="span-idsamplescriptmakingsureunattendxmllayoutmodificationxmlandoobexmlarekeptduringaresetspanspan-idsamplescriptmakingsureunattendxmllayoutmodificationxmlandoobexmlarekeptduringaresetspanspan-idsamplescriptmakingsureunattendxmllayoutmodificationxmlandoobexmlarekeptduringaresetspansample-script-making-sure-unattendxml-layoutmodificationxml-and-oobexml-are-kept-during-a-reset"></a><span id="Sample_script__making_sure_unattend.xml__LayoutModification.xml__and_OOBE.xml_are_kept_during_a_reset"></span><span id="sample_script__making_sure_unattend.xml__layoutmodification.xml__and_oobe.xml_are_kept_during_a_reset"></span><span id="SAMPLE_SCRIPT__MAKING_SURE_UNATTEND.XML__LAYOUTMODIFICATION.XML__AND_OOBE.XML_ARE_KEPT_DURING_A_RESET"></span>示例脚本︰ 确保 unattend.xml、 LayoutModification.xml 和 OOBE.xml 保留在重置期间


通过 unattend.xml 安装文件时，创建的设置也不 Windows 开始菜单的自定义项使用 LayoutModification.xml 创建全系统重置，也不能从 oobe.xml 第一个登录信息期间，Windows 不会自动保存。 若要确保在保存您的自定义内容包含步骤将 unattend.xml、 LayoutModification.xml 和 oobe.xml 文件重新到位。

下面是一些示例脚本，说明如何保留这些设置并将它们放回适当的点。

Unattend.xml、 LayoutModification.xml、 oobe.xml，加上这些两个文本文件的副本保存在 c:\\恢复\\OEM\\。

**ResetConfig.xml:**

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

**EnableCustomizationsAfterRecovery.cmd:**

``` syntax
rem EnableCustomizationsAfterRecovery.cmd

rem Define %TARGETOS% as the Windows folder (This later becomes C:\Windows) 
for /F "tokens=1,2,3 delims= " %%A in ('reg query "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\RecoveryEnvironment" /v TargetOS') DO SET TARGETOS=%%C

rem Define %TARGETOSDRIVE% as the Windows partition (This later becomes C:)
for /F "tokens=1 delims=\" %%A in ('Echo %TARGETOS%') DO SET TARGETOSDRIVE=%%A

rem Add back Windows settings, Start menu, and OOBE.xml customizations
copy "%TARGETOSDRIVE%\Recovery\OEM\Unattend.xml" "%TARGETOS%\Panther\Unattend.xml" /y
copy "%TARGETOSDRIVE%\Recovery\OEM\LayoutModification.xml" "%TARGETOSDRIVE%\Users\Default\AppData\Local\Microsoft\Windows\Shell\LayoutModification.xml" /y
xcopy "%TARGETOSDRIVE%\Recovery\OEM\OOBE\Info" "%TARGETOS%\System32\Info\" /s

rem Recommended: Create a pagefile for devices with 1GB or less of RAM.
wpeutil CreatePageFile /path=%TARGETOSDRIVE%\PageFile.sys /size=256
```

对于多语言部署 OOBE.xml 使用更复杂的文件夹结构。 没关系，只需将整个文件夹复制到 c:\\恢复\\OEM，然后修改该脚本以将整个文件夹复制︰

``` syntax
xcopy "%ScriptFolder%\Info\" "%TargetOSDrive%\System32\Info\" /s
```

## <a name="span-idnextstepsspanspan-idnextstepsspanspan-idnextstepsspannext-steps"></a><span id="Next_Steps"></span><span id="next_steps"></span><span id="NEXT_STEPS"></span>下一步行动


现在，您已自定义按钮重置经验，您可以部署恢复图像分区的恢复图像的按钮重置 (Install.wim)。

若要将 Diskpart 脚本，ResetConfig.xml 文件中，并点击式重新设置恢复映像 (install.wim) 复制到目标计算机的恢复映像分区，请按照[部署 Push-Button 重置功能](deploy-push-button-reset-features.md)主题中的说明进行操作。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[点击式重新设置概述](push-button-reset-overview.md)

[创建介质运行按钮重置功能](create-media-to-run-push-button-reset-features-s14.md)

[将按钮重置功能的部署](deploy-push-button-reset-features.md)

[REAgentC 命令行选项](reagentc-command-line-options.md)

[ResetConfig XML 参考](resetconfig-xml-reference-s14.md)

 

 






