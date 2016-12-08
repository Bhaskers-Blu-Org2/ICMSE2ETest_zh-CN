---
author: Justinha
Description: "Windows 安装程序自动化概述"
ms.assetid: 240b02ae-1f06-4b92-9b46-b4dbd1089c65
MSHAttr: PreferredLib:/library/windows/hardware
title: "Windows 安装程序自动化概述"
ms.openlocfilehash: fd0fe5ec99d084ba0a624e9c7f992b7c2740eb18
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-setup-automation-overview"></a>Windows 安装程序自动化概述

## <a name="use-setupconfigini-to-install-windows"></a>使用 Setupconfig.ini 可以将 Windows 安装

### <a name="what-is-a-setupconfig-file"></a>Setupconfig 文件是什么？

Setupconfig 是一个配置文件，用于将一组标志或参数传递给 Windows setup.exe。 作为一种替代方法将参数传递到 Windows 安装程序命令行上使用此文件。 此功能是 Windows 10 1511年及更高版本中可用。

IT 专业人员可以使用 setupconfig 文件来将参数添加到 Windows 安装程序，从 Windows Update 和 Windows 服务器更新服务。

本主题介绍可与 Windows 10 Setup.exe 的不同参数。

Setupconfig.ini 文件可以包含单个参数或参数和值对。 不包括"/"字符，以及参数和值对，包含"="之间的两个。 

例如，您创建使用以下 Setupconfig.ini。 请注意，标题`[SetupConfig]`是必需的。

```syntax
[SetupConfig]
NoReboot
ShowOobe=None
Telemetry=Enable
ReflectDrivers = <path of folder containing INF and SYS files for the encryption drivers>
```

这等效于下面的命令行︰

```syntax
Setup /NoReboot /ShowOobe None /Telemetry Enable
```

### <a name="how-does-windows-setup-use-setupconfigini"></a>Windows 安装程序如何使用 Setupconfig.ini？

#### <a name="using-mediaiso-file"></a>使用媒体/ISO 文件

如果从媒体或 ISO 文件运行 Windows 安装程序，则必须包含在命令行上的 setupconfig 文件的位置 ("/ ConfigFile `<path>`") 运行 setup.exe 时。 例如︰

```syntax
Setup.exe /ConfigFile <path to Setupconfig.ini>
```

在 setupconfig 文件中包含在命令行上的用作参数和相同的参数，如果 setupconfig 文件参数和值将具有优先权。 

#### <a name="using-windows-update"></a>使用 Windows 更新

如果此更新通过 Windows 更新，Windows 安装程序搜索中的 setupconfig 文件的默认位置。 您可以包含 setupconfig 文件︰

"%systemdrive%\users\default\appdata\local\microsoft\windows\wsus\setupconfig.ini"


## <a name="use-an-answer-file-while-installing-windows"></a>在安装 Windows 时使用的应答文件

可以使用答案文件自动完成 Windows 安装︰

**使用 USB 闪存驱动器**

1.  使用示例答案文件或创建您自己与 Windows 系统映像管理器 （Windows sim 卡）。

2.  将文件保存为**Autounattend.xml** USB 闪存驱动器的根目录。

3.  在新 PC 上，放在 Windows 产品 DVD 和 USB 闪存驱动器，然后启动计算机。 选择任何其他答案文件时，Windows 安装程序搜索此文件。

**选择答案文件**

-   您可以在安装过程中选择特定的应答文件通过引导至 Windows 预安装环境中，并使用**setup.exe**命令及**/unattend:***文件名*选项。 有关详细信息，请参阅[WinPE︰ 创建 USB 可启动驱动器](winpe-create-usb-bootable-drive.md)。

对于示例答案文件和用于自动化安装设置的列表，请参阅[自动执行 Windows 安装程序](automate-windows-setup.md)。

## <a name="modify-an-existing-installation"></a>修改现有安装

在安装过程中重新启动是必需的因为一份答案文件会缓存到 %WINDIR%\\黑豹的 Windows 安装目录。 您可以修改此文件以执行下列任一操作︰

-   更新系统和控制面板设置，而将映像启动。

-   准备计算机启动到审核模式下更新镜像 (请参见 Microsoft Windows 部署\\重新封装\\[模式](http://go.microsoft.com/fwlink/?LinkId=275830))。

-   更新驱动程序或程序包的安装的顺序。 （有依赖关系的包可能需要按特定的顺序安装）。

**替换在脱机映像中的答案文件**

1.  在 Windows 系统映像管理器 (Windows SIM) 创建一个自定义的回答文件。

2.  打开提升的命令提示符。

3.  将 Windows 映像进行安装。

    ``` syntax
    Dism /Mount-Image /ImageFile:"C:\images\CustomImage.wim" /Index:1 /MountDir:C:\mount
    ```

4.  修改或替换文件︰ \\Windows\\黑豹\\unattend.xml 中已装载的映像。

    ``` syntax
    Copy CustomAnswerFile.xml C:\mount\Windows\Panther\unattend.xml
    ```

    **请注意**  
    映像中的答案文件可能包含未处理的设置。 如果您想获得处理这些设置，请编辑现有的文件，而不是取代它。

     

5.  卸载该映像。

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\mount /Commit
    ```

6.  未指定答案文件将其部署到新的 PC，测试图像。 Windows 安装程序运行时，它将查找并使用此答案文件。

## <a name="implicit-answer-file-search-order"></a>模糊答案文件搜索顺序


Windows 安装程序搜索的开头的每个配置阶段中，包括初始安装前后的应用和引导映像的答案文件。 如果找到答案文件，并且它包含给定的配置阶段的设置，它处理这些设置。

Windows 安装程序标识，并记录所有可用的答案文件，具体取决于搜索顺序。 使用具有最高优先级的应答文件。 应答文件是验证，然后将其缓存到计算机。 有效的答案文件缓存到 $Windows。 ~ BT\\源\\在[windowsPE](windowspe.md)和[offlineServicing](offlineservicing.md)配置期间黑豹目录传递。 Windows 安装到硬盘中提取后，将答案文件缓存到 %WINDIR%\\黑豹。

下表显示模糊答案文件搜索顺序。

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">搜索顺序</th>
<th align="left">位置</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>1</p></td>
<td align="left"><p>注册表</p>
<p>HKEY_LOCAL_MACHINE\System\Setup\UnattendFile</p></td>
<td align="left"><p>在注册表中为答案文件中指定的指针。 不需要被命名为 Unattend.xml 应答文件。</p></td>
</tr>
<tr class="even">
<td align="left"><p>2</p></td>
<td align="left"><p>%WINDIR%\Panther\Unattend</p></td>
<td align="left"><p>应答文件的名称必须是 Unattend.xml 或 Autounattend.xml。</p>
<div class="alert">
<strong>请注意</strong>  
<p>Windows 安装程序将只在下层安装此目录中搜索。 如果从 Windows PE 启动 Windows 安装程序，则不搜索 %WINDIR%\Panther\Unattend 目录。</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td align="left"><p>3</p></td>
<td align="left"><p>%WINDIR%\Panther</p></td>
<td align="left"><p>Windows 安装程序将缓存的答案文件复制到此位置在安装的后续阶段中使用。 例如，当计算机重新启动时，安装程序会继续应用答案文件中的设置。 如果您显式指定答案文件，通过使用 Windows 安装程序或 Sysprep，答案文件缓存到此目录将覆盖与显式指定的应答文件。</p>
<div class="alert">
<strong>重要</strong>  
<p>不要使用、 修改或覆盖此目录中的答案文件。 在安装过程中，Windows 安装程序进行注释此目录中的答案文件。 此应答文件不能重复使用 Windows sim 卡或任何其他 Windows 安装中。</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td align="left"><p>4</p></td>
<td align="left"><p>可移动的读/写介质驱动器，该驱动器的根目录处的顺序。</p></td>
<td align="left"><p>可移动的读/写介质驱动器，该驱动器的根目录处的顺序。</p>
<p>应答文件的名称必须是 Unattend.xml 或 Autounattend.xml，并且必须在驱动器的根目录中的答案文件。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>5</p></td>
<td align="left"><p>按顺序排列驱动器，该驱动器的根目录处的可移动只读介质。</p></td>
<td align="left"><p>按顺序排列驱动器，该驱动器的根目录处的可移动只读介质。</p>
<p>应答文件的名称必须是 Unattend.xml 或 Autounattend.xml，并且必须在驱动器的根目录中。</p></td>
</tr>
<tr class="even">
<td align="left"><p>6</p></td>
<td align="left"><p>[offlineServicing](offlineservicing.md) ，并[windowsPE](windowspe.md)配置阶段︰</p>
<ul>
<li><p>在 Windows 分发的 \Sources 目录</p></li>
</ul>
<p>所有其他阶段︰</p>
<ul>
<li><p>%WINDIR%\System32\Sysprep</p></li>
</ul></td>
<td align="left"><p>在[windowsPE](windowspe.md)和[offlineServicing](offlineservicing.md)配置阶段，应答文件的名称必须是 Autounattend.xml。</p>
<p>对于所有其他配置阶段中，文件名必须 Unattend.xml。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>7</p></td>
<td align="left"><p>系统驱动器 %%</p></td>
<td align="left"><p>应答文件的名称必须是 Unattend.xml 或 Autounattend.xml</p></td>
</tr>
<tr class="even">
<td align="left"><p>8</p></td>
<td align="left"><p>Windows 安装程序 (setup.exe) 正在运行，在驱动器的根目录中的驱动器。</p></td>
<td align="left"><p>应答文件的名称必须是 Unattend.xml 或 Autounattend.xml，并且必须在根目录中的 Windows 安装程序文件夹路径。</p></td>
</tr>
</tbody>
</table>

 

## <a name="sensitive-data-in-answer-files"></a>在答案文件中的敏感数据


安装程序将删除缓存的答案文件结尾的每个配置阶段中的敏感数据。

**重要**  
答案文件缓存到计算机在 Windows 安装过程中，因为答案文件将坚持之间重新启动计算机。 将计算机交付给客户之前，您必须删除缓存的答案文件在 %WINDIR%\\黑豹目录。 如果答案文件中包括域密码、 产品密钥或其他敏感数据，则可能存在潜在的安全问题。 但是，如果您有未处理的设置在[oobeSystem](oobesystem.md)配置传递要在最终用户启动计算机时运行，请考虑删除答案文件已处理的部分。 当您运行**sysprep /oobe**命令的一种选择可能是使用单独的应答文件只包含在 oobeSystem 配置阶段的设置。

 

但是，如果应答文件嵌入位置的优先级高于缓存的答案文件，然后缓存的答案可能被覆盖开头的每个后续配置阶段，如果嵌入的答案文件与隐式的搜索条件相匹配。 例如，如果应答文件嵌入在 %WINDIR%\\黑豹\\人参与\\Unattend.xml，嵌入的答案文件将替换缓存的答案文件开头的每个配置阶段。 例如，嵌入的应答文件指定的[专门](specialize.md)和[oobeSystem](oobesystem.md)配置阶段，那么嵌入式的应答文件发现**specialize**配置阶段中，缓存，处理，并清除敏感数据。 再次在 oobeSystem 配置阶段发现和再次缓存嵌入的答案文件。 因此，专业化配置传递的敏感数据不再被清除。 以前处理的配置阶段的敏感数据不会再次清除。 必须重写缓存的答案文件，除非我们建议答案文件嵌入在优先级较低的位置。

**重要**  
答案文件缓存到计算机在 Windows 安装过程中，因为答案文件将坚持之间重新启动计算机。 将计算机交付给客户之前，您必须删除缓存的答案文件在 %WINDIR%\\黑豹目录。 如果答案文件中包括域密码、 产品密钥或其他敏感数据，则可能存在潜在的安全问题。 但是，如果您有未处理的设置在[oobeSystem](oobesystem.md)配置传递要在最终用户启动计算机时运行，请考虑删除答案文件已处理的部分。 当您运行**sysprep /oobe**命令的一种选择可能是使用单独的应答文件只包含在 oobeSystem 配置阶段的设置。

 

可以删除计算机上的缓存或嵌入应答文件的 Setupcomplete.cmd 命令脚本中添加命令。 有关详细信息，请参阅[添加到 Windows 安装程序的自定义脚本](add-a-custom-script-to-windows-setup.md)。

##<a name="windows-setup-annotates-configuration-passes-in-an-answer-file"></a>Windows 安装程序标注在答案文件中配置阶段


在处理某个配置阶段后，Windows 安装程序批注以指示传递已处理缓存的答案文件。 如果再次运行配置阶段且尚未更换或在中期计划中更新缓存的答案文件，该答案文件设置将不会再次处理。 相反，Windows 安装程序将搜索位于较低位置的优先级高于缓存 Unattend.xml 文件的隐式 Unattend.xml 文件。

例如，可以将 Windows 安装的应答文件中包含 Microsoft Windows 部署 /**RunSynchronous**命令在[specialize](specialize.md)配置传递。 在安装期间，专业化配置阶段运行，执行**RunSynchronous**命令。 安装完成后，与**一般化 /**选项运行**sysprep**命令。 如果没有较高的优先级比缓存的答案文件或应答文件未显式传递到 Sysprep 工具没有应答文件，安装程序运行的专业化配置传递的下一次计算机启动时。 由于缓存的答案文件包含已应用该配置阶段的设置批注，不执行**RunSynchronous**命令。

## <a name="implicit-answer-file-search-examples"></a>模糊答案文件搜索示例


下面的示例帮助描述模糊答案文件搜索的行为。

### <a name="span-idanswerfilesnamedautounattendxmlareautomaticallydiscoveredbywindowssetupspanspan-idanswerfilesnamedautounattendxmlareautomaticallydiscoveredbywindowssetupspanspan-idanswerfilesnamedautounattendxmlareautomaticallydiscoveredbywindowssetupspananswer-files-named-autounattendxml-are-automatically-discovered-by-windows-setup"></a><span id="Answer_Files_Named_Autounattend.xml_are_Automatically_Discovered_by_Windows_Setup"></span><span id="answer_files_named_autounattend.xml_are_automatically_discovered_by_windows_setup"></span><span id="ANSWER_FILES_NAMED_AUTOUNATTEND.XML_ARE_AUTOMATICALLY_DISCOVERED_BY_WINDOWS_SETUP"></span>答案文件命名为 Autounattend.xml 是由 Windows 安装程序可自动发现

1.  创建名为 Autounattend.xml，其中包括在[windowsPE](windowspe.md)配置阶段的设置的答案文件。

2.  将 Autounattend.xml 复制到可移动媒体设备。

3.  配置为从 CD 或 DVD 启动您计算机的 BIOS。

4.  启动 Windows 产品 DVD。

5.  在启动 Windows 时，请插入可移动媒体设备。 此示例假定可移动介质所分配的驱动器号 d:\\。

    Windows 安装程序启动，并会自动标识 Autounattend.xml 作为一个有效的应答文件。 因为应答文件使用有效文件名 (Autounattend.xml) 位于其中一个有效的搜索路径 （D 的根），包括当前配置阶段 ([windowsPE](windowspe.md)) 的有效设置，将使用此答案文件。

    将答案文件缓存到计算机中。 如果在以后的阶段中发现没有其他答案文件，在 Windows 安装程序使用缓存的答案文件。

### <a name="span-idanswerfilesarediscoveredinorderofprecedenceinpredefinedsearchpathsspanspan-idanswerfilesarediscoveredinorderofprecedenceinpredefinedsearchpathsspanspan-idanswerfilesarediscoveredinorderofprecedenceinpredefinedsearchpathsspananswer-files-are-discovered-in-order-of-precedence-in-predefined-search-paths"></a><span id="Answer_Files_are_Discovered_in_Order_of_Precedence_in_Predefined_Search_Paths"></span><span id="answer_files_are_discovered_in_order_of_precedence_in_predefined_search_paths"></span><span id="ANSWER_FILES_ARE_DISCOVERED_IN_ORDER_OF_PRECEDENCE_IN_PREDEFINED_SEARCH_PATHS"></span>在预定义的搜索路径中的优先次序中发现答案文件

1.  在前面的方案中使用的步骤，使用答案文件安装 Windows。 用于将 Windows 安装的答案文件会缓存到系统在 %WINDIR%\\黑豹目录。

2.  将 Unattend.xml 文件复制到 %WINDIR%\\System32\\Sysprep 目录。

    此答案文件中的[一般化](generalize.md)配置阶段已设置。

3.  创建参考映像的**一般化 /**选项运行**sysprep**命令。

    因为 %WINDIR%\\System32\\Sysprep 目录隐式的搜索路径中，找到答案文件复制到此目录。 但是，安装 Windows 所使用的答案文件仍处于缓存在计算机上，并且包含的[一般化](generalize.md)配置阶段的设置。 此缓存的答案文件的优先级高于到 Sysprep 目录复制。 使用缓存的答案文件。

    **请注意**  
    作为一个命令行工具或 GUI 工具，可以运行 Sysprep 工具。 如果在运行 Sysprep 工具作为 GUI 工具，您可以选择**通用化**复选框。

     

    若要使用新的应答文件，可以将它复制到一个目录的优先级高于缓存的答案文件，或者您可以通过使用**无人参与**选项指定答案文件。 例如︰

    ``` syntax
    sysprep /generalize /unattend:C:\MyAnswerFile.xml
    ```

### <a name="answer-files-must-include-a-valid-configuration-pass"></a>答案文件必须包含有效的配置阶段

1.  Unattend.xml 文件复制到可移动媒体设备。

    Unattend.xml 文件具有仅为[auditSystem](auditsystem.md)和[auditUser](audituser.md)配置阶段的设置。

2.  在已安装的 Windows 操作系统，运行**sysprep 一般化 /oobe /**命令。

    即使答案文件可用于隐式搜索路径之一，Unattend.xml 文件被忽略，因为它不包含有效的[一般化](generalize.md)配置阶段的刀。

## <a name="span-idbkmkdspanspan-idbkmkdspanadditional-resources"></a><span id="bkmk_d"></span><span id="BKMK_D"></span>其他资源


下面的主题有关的答案文件和配置阶段的详细信息，请参阅︰

-   [有关创建答案文件的最佳做法](https://msdn.microsoft.com/library/windows/hardware/dn915073)

-   [创建或打开答案文件](https://msdn.microsoft.com/library/windows/hardware/dn915085)

-   [配置答案文件中的组件和设置](https://msdn.microsoft.com/library/windows/hardware/dn915078)

-   [验证答案文件](https://msdn.microsoft.com/library/windows/hardware/dn915106)

-   [隐藏在应答文件中的敏感数据](https://msdn.microsoft.com/library/windows/hardware/dn915098)

-   [配置阶段的工作](how-configuration-passes-work.md)

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Windows 安装程序方案和最佳做法](windows-setup-scenarios-and-best-practices.md)

[Windows 安装程序安装过程](windows-setup-installation-process.md)

[自动执行 Windows 安装程序](automate-windows-setup.md)

[审核模式概述](audit-mode-overview.md)

[Windows 安装程序配置阶段](windows-setup-configuration-passes.md)

[Windows 安装程序支持的平台和跨平台部署](windows-setup-supported-platforms-and-cross-platform-deployments.md)

 

 






