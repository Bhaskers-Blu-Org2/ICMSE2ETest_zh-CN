---
author: Justinha
Description: "获取映像或组件使用 DISM 的清单"
ms.assetid: cab41da0-3155-4170-8377-b6335de47a38
MSHAttr: PreferredLib:/library/windows/hardware
title: "获取映像或组件使用 DISM 的清单"
ms.openlocfilehash: aa3beecb7ca8089202e33b4ac2854d2784795b4f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="take-inventory-of-an-image-or-component-using-dism"></a>获取映像或组件使用 DISM 的清单


您可以采取哪些驱动程序、 程序包，库存和 Windows 映像中包含的其他文件和设置。 为此，请使用部署映像服务和管理 (DISM) 服务命令。

您可以采取的清单或服务的特定 Windows 映像之前，必须从 WIM 或 VHD 文件装载脱机映像。 有关详细信息，请参阅[安装和修改 Windows 映像使用 DISM](mount-and-modify-a-windows-image-using-dism.md)。

在此部分中︰

[获取 Windows 图像信息](#getwiminformatio)

[获取 Windows PE 的信息](#getwindowspeinformation)

[获取驱动程序的信息](#getdriverinformation)

[获取包和功能信息](#getpackageinformation)

[获取应用程序软件包 (.appx) 服务信息](#getapppackage)

[获得国际设置和语言](#getinternationalsettingslang)

[获取 Windows 版本信息](#getwindowseditioninformation)

[获取应用程序的修补程序信息](#getapplicationinformation)

## <a name="span-idgetwiminformatiospanspan-idgetwiminformatiospanspan-idgetwiminformatiospanget-windows-image-information"></a><span id="GetWIMInformatio"></span><span id="getwiminformatio"></span><span id="GETWIMINFORMATIO"></span>获取 Windows 图像信息


您可以使用图像命令列出有关特定 Windows 映像 (WIM) 文件或虚拟硬盘 (VHD) 文件，包含在 WIM 中特定图像的相关或 VHD 文件，以及已装载 WIM 或 VHD 文件的信息。 此信息可以帮助您确定装载位置、 映像名称，或验证您要装载的映像的体系结构。

您可以通过使用**/Get-ImageInfo**服务在 DISM 命令收集所有 WIM 或 VHD 文件中的图像信息。 您还可以通过指定名称或索引号的图像收集 WIM 或 VHD 文件，例如操作系统、 体系结构和设置，在特定的图像信息。 在 VHD 文件中指定的图像，必须使用**/Index:1** 。

您可以在您的计算机标识当前装载的映像，您可以通过使用**/Get-MountedImageInfo**服务命令列出有关已装载映像如读/写权限、 装载位置、 已安装的文件路径和装入的映像的索引信息。

有关 DISM 中可用的图像命令的详细信息，请参阅[DISM 的部署映像服务和管理技术参考的窗口](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md)。

**向列表包含在 WIM 或 VHD 文件的图像**

1.  单击**开始**，然后键入**部署**。 用鼠标右键单击**部署和图像处理工具环境**，然后选择**以管理员身份运行**。

2.  列出有关所有 WIM 或 VHD 文件，在提升的命令提示符下键入中的图像的信息︰

    ``` syntax
    Dism /Get-ImageInfo /imagefile:C:\test\images\install.wim
    ```

    有关使用替换的**/Index**或**/Name**选项，将更多详细的信息时显示指定的图像。 在 VHD 文件中指定的图像，必须使用`/Index:1`。

生成的报告包含以下信息。

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">字段</th>
<th align="left">说明</th>
<th align="left">示例</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>索引</p></td>
<td align="left"><p>WIM 或 VHD 文件中的图像的索引值。</p></td>
<td align="left"><p>1</p></td>
</tr>
<tr class="even">
<td align="left"><p>名称</p></td>
<td align="left"><p>Windows 版本 WIM 或 VHD 文件中的映像的名称。</p></td>
<td align="left"><p>Windows 8 专业版</p></td>
</tr>
<tr class="odd">
<td align="left"><p>说明</p></td>
<td align="left"><p>WIM 或 VHD 文件中图像的说明。</p></td>
<td align="left"><p>Windows 8 专业版</p></td>
</tr>
<tr class="even">
<td align="left"><p>大小</p></td>
<td align="left"><p>图像的大小。</p></td>
<td align="left"><p>8,045,951,502 字节</p></td>
</tr>
</tbody>
</table>

 

**若要列出装入的映像**

1.  单击**开始**，然后键入**部署**。 用鼠标右键单击**部署和图像处理工具环境**，然后选择**以管理员身份运行**。

2.  在提升的命令提示符下，键入︰

    ``` syntax
    Dism /Get-MountedImageInfo 
    ```

生成的报告包含以下信息︰

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">字段</th>
<th align="left">说明</th>
<th align="left">示例</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>装入目录</p></td>
<td align="left"><p>装载映像的位置。</p></td>
<td align="left"><p><strong>C:\Test\Mount</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>图像文件</p></td>
<td align="left"><p>到 WIM 或 VHD 文件的完整路径。</p></td>
<td align="left"><p><strong>C:\Test\Images\install.wim</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>图像索引</p></td>
<td align="left"><p>已装载的映像包含在 WIM 或 VHD 文件的索引号。</p></td>
<td align="left"><p>1</p></td>
</tr>
<tr class="even">
<td align="left"><p>已装入的读/写</p></td>
<td align="left"><p><strong>是</strong>如果允许只读访问已装载的映像装入的映像如果允许读和写访问权限或<strong>无</strong>。</p></td>
<td align="left"><p>是</p></td>
</tr>
<tr class="odd">
<td align="left"><p>。</p></td>
<td align="left"><p>装入映像的状态。 可能的值包括︰</p>
<p><strong>还行。</strong> 装入映像。 没有任何问题。</p>
<p><strong>需要重新装载。</strong> 必须重新加载该图像。 这可致时装载映像重新启动主机系统。</p>
<p><strong>无效。</strong>: 映像处于无效状态。 您可能必须使用<strong>/Cleanup-Mountpoints</strong>在图像上。</p></td>
<td align="left"><p>确定</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idgetwindowspeinformationspanspan-idgetwindowspeinformationspanspan-idgetwindowspeinformationspanget-windows-pe-information"></a><span id="GetWindowsPEInformation"></span><span id="getwindowspeinformation"></span><span id="GETWINDOWSPEINFORMATION"></span>获取 Windows PE 的信息


您可以装载 Windows 预安装环境 (Windows PE) 映像以便进行处理以相同的方式将任何 Windows 映像。 也有一些 Windows PE 服务特定于 Windows PE 映像的命令。 可以对列表如 scratchspace、 目标路径和分析信息的 Windows PE 设置使用这些命令。 有关 DISM 中可用的 Windows PE 服务命令的详细信息，请参阅[DISM Windows PE 服务命令行选项](dism-windows-pe-servicing-command-line-options.md)。

**列出已安装的 Windows PE 映像中的所有设置。**

1.  单击**开始**，然后键入**部署**。 用鼠标右键单击**部署和图像处理工具环境**，然后选择**以管理员身份运行**。

2.  列出有关所有已安装的 Windows PE 映像，在提升的命令提示符下键入中的 Windows PE 设置信息︰

    ``` syntax
    Dism /image:C:\test\offline /Get-PESettings
    ```

生成的报告包含以下信息︰

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">字段</th>
<th align="left">说明</th>
<th align="left">示例</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>分析</p></td>
<td align="left"><p>启用还是禁用 Windows PE 分析报告。</p></td>
<td align="left"><p>禁用</p></td>
</tr>
<tr class="even">
<td align="left"><p>临时空间</p></td>
<td align="left"><p>当在 ramdisk 模式下启动 Windows PE 系统卷上写的可用空间量。</p></td>
<td align="left"><p>32 MB</p></td>
</tr>
<tr class="odd">
<td align="left"><p>目标路径</p></td>
<td align="left"><p>在启动时 Windows PE 映像的根路径。</p></td>
<td align="left"><p>X:\</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idgetdriverinformationspanspan-idgetdriverinformationspanspan-idgetdriverinformationspanget-driver-information"></a><span id="GetDriverInformation"></span><span id="getdriverinformation"></span><span id="GETDRIVERINFORMATION"></span>获取驱动程序的信息


驱动程序服务命令可用于枚举驱动程序包的.inf 文件的基础的驱动程序存储区中。 您可以使用**/get**命令显示脱机映像中的第三方驱动程序包或所有驱动程序包的基本信息。 当您指向脱机映像或运行的操作系统时，您可以确定驱动程序包中的图像，并获取有关驱动程序的信息。

您可以显示有关特定安装的.inf 文件，或尚未安装的详细的信息。 在驱动程序存储区中安装的驱动程序将被命名为 Oem0.inf、 Oem1.inf，等等。

有关 DISM 中可用的驱动程序服务命令的详细信息，请参阅[DISM 驱动程序服务命令行选项](dism-driver-servicing-command-line-options-s14.md)。

**若要列出脱机映像中的驱动程序包**

1.  单击**开始**，然后键入**部署**。 用鼠标右键单击**部署和图像处理工具环境**，然后选择**以管理员身份运行**。

2.  已装载的脱机 Windows 映像中使用以下命令列出有关所有驱动程序包的信息之一︰

    ``` syntax
    Dism /image:C:\test\offline /Get-Drivers
    ```

    ``` syntax
    Dism /image:C:\test\offline /Get-Drivers /all
    ```

    对于正在运行的操作系统，请键入下列命令之一︰

    ``` syntax
    Dism /online /Get-Drivers
    ```

    ``` syntax
    Dism /online /Get-Drivers /all
    ```

生成的报告包含以下信息︰

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">字段</th>
<th align="left">说明</th>
<th align="left">示例</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>已发布的名称</p></td>
<td align="left"><p>驱动程序包之后添加到驱动程序存储区的名称。</p></td>
<td align="left"><p>Oem0.inf</p></td>
</tr>
<tr class="even">
<td align="left"><p>原始文件名</p></td>
<td align="left"><p>驱动程序包的原始.inf 文件名称。</p></td>
<td align="left"><p>Toaster.inf</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Inbox</p></td>
<td align="left"><p><strong>是</strong>的默认驱动程序 （驱动程序） 或<strong>无</strong>第三方驱动程序包。</p></td>
<td align="left"><p>否</p></td>
</tr>
<tr class="even">
<td align="left"><p>类名</p></td>
<td align="left"><p>设备类的驱动程序的友好名称是的成员。</p></td>
<td align="left"><p>Printer</p></td>
</tr>
<tr class="odd">
<td align="left"><p>提供程序名称</p></td>
<td align="left"><p>提供程序或驱动程序软件包的数字签名。</p></td>
<td align="left"><p>Microsoft</p></td>
</tr>
<tr class="even">
<td align="left"><p>日期</p></td>
<td align="left"><p>在.inf 文件中指定的驱动程序相关联的日期。 将为您的区域设置正确格式化日期。</p></td>
<td align="left"><p>2006 年 10 月 31 日</p></td>
</tr>
<tr class="odd">
<td align="left"><p>版本</p></td>
<td align="left"><p>在 INF driverVer 指令指定的版本号。</p></td>
<td align="left"><p>6.1.6801.0</p></td>
</tr>
</tbody>
</table>

 

**若要获取有关特定驱动程序的信息**

1.  单击**开始**，然后键入**部署**。 用鼠标右键单击**部署和图像处理工具环境**，然后选择**以管理员身份运行**。

2.  列出有关脱机 Windows 映像中特定驱动程序包的信息。 例如，键入︰

    ``` syntax
    Dism /image:C:\test\offline /Get-DriverInfo /driver:oem1.inf
    ```

    对于正在运行的操作系统，请键入︰

    ``` syntax
    Dism /online /Get-DriverInfo /driver:oem1.inf
    ```

生成的报告包含以下信息︰

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">字段</th>
<th align="left">说明</th>
<th align="left">示例</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>已发布的名称</p></td>
<td align="left"><p>驱动程序包之后添加到驱动程序存储区的名称。</p></td>
<td align="left"><p>Oem0.inf</p></td>
</tr>
<tr class="even">
<td align="left"><p>驱动程序存储路径</p></td>
<td align="left"><p>驱动程序位置的路径。 如果安装驱动程序，则列出驱动程序存储的路径。 如果尚未安装驱动程序，则列出服务主机上的驱动程序的路径。</p></td>
<td align="left"><p><strong>E:\Images\Mount_depset\Windows\System32\DriverStore\FileRepository\Fasttx2k.inf_x86_neutral_0328f62e\Fasttx2k.inf</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>类名</p></td>
<td align="left"><p>设备类的驱动程序的友好名称是的成员。</p></td>
<td align="left"><p>Printer</p></td>
</tr>
<tr class="even">
<td align="left"><p>类描述</p></td>
<td align="left"><p>设备类的驱动程序的说明会的成员。</p></td>
<td align="left"><p>打印机</p></td>
</tr>
<tr class="odd">
<td align="left"><p>类 GUID</p></td>
<td align="left"><p>设备类的驱动程序所在的 GUID。</p></td>
<td align="left"><p><strong>{4D36E97B-E325-11CE-BFC1-08002BE10318}</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>日期</p></td>
<td align="left"><p>在.inf 文件中指定的驱动程序相关联的日期。 将为您的区域设置正确格式化日期。</p></td>
<td align="left"><p>2003 年 8 月 6 日</p></td>
</tr>
<tr class="odd">
<td align="left"><p>版本</p></td>
<td align="left"><p>在 INF driverVer 指令指定驱动程序版本编号。</p></td>
<td align="left"><p>1.0.1.37</p></td>
</tr>
<tr class="even">
<td align="left"><p>引导关键</p></td>
<td align="left"><p><strong>是</strong>如果驱动程序是引导关键或<strong>否</strong>，如果它不是。</p></td>
<td align="left"><p><strong>否</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>体系结构的驱动程序</p></td>
<td align="left"><p>图像上安装驱动程序的体系结构。 如果尚未安装驱动程序，则该字段重复报告为每个受支持的操作系统体系结构。</p></td>
<td align="left"><p>x86</p></td>
</tr>
<tr class="even">
<td align="left"><p>制造商</p></td>
<td align="left"><p>受支持设备的制造商。</p></td>
<td align="left"><p>艾德</p></td>
</tr>
<tr class="odd">
<td align="left"><p>说明</p></td>
<td align="left"><p>受支持设备的说明。</p></td>
<td align="left"><p><strong>Windows XP 探险作品 376 控制器</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>体系结构</p></td>
<td align="left"><p>该体系结构的驱动程序。</p></td>
<td align="left"><p>x86</p></td>
</tr>
<tr class="odd">
<td align="left"><p>硬件 ID</p></td>
<td align="left"><p>受支持设备的硬件 ID。</p></td>
<td align="left"><p><strong>ABC_3376</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>服务名称</p></td>
<td align="left"><p>驱动程序的服务名。</p></td>
<td align="left"><p><strong>C1232k</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>兼容 Id</p></td>
<td align="left"><p>备用插即用 (PnP) Id 的设备，如果任意适用。</p></td>
<td align="left"><p><strong>* 12ABC</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>排除 Id</p></td>
<td align="left"><p>将不匹配任何应用设备的即插即用 Id。</p></td>
<td align="left"><p><strong>* A_123</strong></p></td>
</tr>
</tbody>
</table>

 

**请注意**  
如果您指向尚未安装的驱动程序，则报告将稍有不同。

 

## <a name="span-idgetpackageinformationspanspan-idgetpackageinformationspanspan-idgetpackageinformationspanget-package-and-feature-information"></a><span id="GetPackageInformation"></span><span id="getpackageinformation"></span><span id="GETPACKAGEINFORMATION"></span>获取包和功能信息


操作系统程序包服务命令可用于获取有关 Windows 程序包的信息。 此外可以使用 DISM 和程序包服务命令来获取有关脱机或在运行 Windows 安装的 Windows 功能的信息。

可以使用**/PackagePath**选项指定.cab 文件或从中提取.cab 文件的文件夹。 不能使用此命令来获取.msu 文件的包信息。 或者，可以使用**/Get-Packages**查找程序包的名称，并将**/PackageName**指定包的名称。

可以显示有关某个功能的详细的信息。 您必须使用**/get**命令**/FeatureName**选项。 使用**/Get-Features**选项可以查找图像中的功能的名称。 功能的名称是区分大小写如果处理非 Windows 8 的 Windows 映像。

有关 DISM 中可用的操作系统程序包服务命令的详细信息，请参阅[DISM 操作系统程序包服务命令行选项](dism-operating-system-package-servicing-command-line-options.md)。

**若要列出映像中的所有程序包**

1.  单击**开始**，然后键入**部署**。 用鼠标右键单击**部署和图像处理工具环境**，然后选择**以管理员身份运行**。

2.  若要列出有关脱机 Windows 映像中的程序包的所有信息，请键入下面的命令︰

    ``` syntax
    Dism /image:C:\test\offline /Get-Packages
    ```

    对于正在运行的操作系统，请键入以下命令︰

    ``` syntax
    Dism /online /Get-Packages
    ```

生成的报告包含以下信息︰

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">字段</th>
<th align="left">说明</th>
<th align="left">示例</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>程序包标识</p></td>
<td align="left"><p>在图像中出现的程序包的名称。</p></td>
<td align="left"><p><strong>Microsoft-Windows-NetFx3-OC-Package~31bf3856ad364e35~x86~en-US~6.1.6772.0</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>省/市/自治区</p></td>
<td align="left"><p>程序包的当前状态。 如︰</p>
<p><strong>安装。</strong> 安装包。</p>
<p><strong>安装挂起。</strong> 该软件包已安装，但需要重新启动才能完成挂起的联机操作。</p>
<p><strong>转移。</strong> 程序包已准备好可以安装。</p></td>
<td align="left"><p><strong>安装</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>版本类型</p></td>
<td align="left"><p>它的包类型。 如︰</p>
<p><strong>功能包。</strong> Windows 操作系统功能。</p>
<p><strong>语言包。</strong> Windows 操作系统语言包或语言界面包 (LIP)。</p>
<p><strong>基础。</strong> 核心操作系统组件包括可选功能。</p></td>
<td align="left"><p>功能包</p></td>
</tr>
<tr class="even">
<td align="left"><p>安装时间</p></td>
<td align="left"><p>UTC 日期和安装所发生的时间。 如果尚未安装该程序包，则安装时间字段为空。</p></td>
<td align="left"><p>2008 年 8 月 18 日 7:58: 00PM</p></td>
</tr>
</tbody>
</table>

 

**列出有关特定程序包的信息**

1.  单击**开始**，然后键入**部署**。 用鼠标右键单击**部署和图像处理工具环境**，然后选择**以管理员身份运行**。

2.  列出有关脱机 Windows 映像，键入以下命令之一中特定程序包的信息︰

    ``` syntax
    Dism /image:C:\test\offline /Get-PackageInfo /PackagePath:C:\packages\package.cab
    ```

    ``` syntax
    Dism /image:C:\test\offline /Get-PackageInfo /PackageName:Microsoft.Windows.Calc.Demo~6595b6144ccf1df~x86~en~1.0.0.0
    ```

    对于正在运行的操作系统，请键入下列命令之一︰

    ``` syntax
    Dism /online /Get-PackageInfo /PackagePath:C:\packages\package.cab
    ```

    ``` syntax
    Dism /online /Get-PackageInfo /PackageName:Microsoft.Windows.Calc.Demo~6595b6144ccf1df~x86~en~1.0.0.0
    ```

生成的报告包含以下信息︰

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">字段</th>
<th align="left">说明</th>
<th align="left">示例</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>程序包标识</p></td>
<td align="left"><p>在图像中出现的程序包的名称。</p></td>
<td align="left"><p><strong>Microsoft-Windows-NetFx3-OC-Package~31bf3856ad364e35~x86~en-US~6.1.6772.0</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>适用</p></td>
<td align="left"><p>指示是否该软件包可应用于图像。</p></td>
<td align="left"><p><strong>否</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>版权</p></td>
<td align="left"><p>程序包的版权信息。</p></td>
<td align="left"><p>版权所有 © Microsoft 公司。 保留所有权利。</p></td>
</tr>
<tr class="even">
<td align="left"><p>单位</p></td>
<td align="left"><p>提供该程序包，如果可用的公司。</p></td>
<td align="left"><p>微软公司</p></td>
</tr>
<tr class="odd">
<td align="left"><p>创建时间</p></td>
<td align="left"><p>日期和时间创建包时，如果可用。</p></td>
<td align="left"><p>2008 年 8 月 18 日 7:58: 00PM</p></td>
</tr>
<tr class="even">
<td align="left"><p>说明</p></td>
<td align="left"><p>包的简短说明。</p></td>
<td align="left"><p>KB300106 的</p></td>
</tr>
<tr class="odd">
<td align="left"><p>安装客户端</p></td>
<td align="left"><p>客户端工具的安装程序包。</p></td>
<td align="left"><p>DISM 程序包管理器提供程序</p></td>
</tr>
<tr class="even">
<td align="left"><p>安装程序包名称</p></td>
<td align="left"><p>已安装的 package.mum 文件的名称。</p></td>
<td align="left"><p><strong>Microsoft-Windows-NetFx3-OC-Package~31bf3856ad364e35~x86~en-US~6.1.6772.0.mum</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>安装时间</p></td>
<td align="left"><p>日期和时间安装程序包。 如果尚未安装该程序包，则<strong>安装时间</strong>字段为空。</p></td>
<td align="left"><p>2008 年 8 月 18 日 7:58: 00PM</p></td>
</tr>
<tr class="even">
<td align="left"><p>上次更新时间</p></td>
<td align="left"><p>上次更新包，如果可用日期。</p></td>
<td align="left"><p>2008 年 8 月 18 日 7:58: 00PM</p></td>
</tr>
<tr class="odd">
<td align="left"><p>名称</p></td>
<td align="left"><p>如果已本地化的包，显示名称。</p>
<p>通常情况下，&quot;默认&quot;将显示所有服务程序包。</p></td>
<td align="left"><p>ActiveX® 安装程序服务</p></td>
</tr>
<tr class="even">
<td align="left"><p>产品名称</p></td>
<td align="left"><p>程序包所属，如果有的产品名称。</p></td>
<td align="left"><p><strong>Microsoft 的 Windows-NetFx3-OC-包</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>产品版本</p></td>
<td align="left"><p>程序包所属，如果可用的产品版本。</p></td>
<td align="left"><p>123.01.0000</p></td>
</tr>
<tr class="even">
<td align="left"><p>版本类型</p></td>
<td align="left"><p>它的包类型。 如︰</p>
<p><strong>功能包。</strong> Windows 操作系统功能。</p>
<p><strong>语言包。</strong> Windows 操作系统语言包或语言界面包 (LIP)。</p>
<p><strong>基础。</strong> 核心操作系统组件包括可选功能。</p></td>
<td align="left"><p>功能包</p></td>
</tr>
<tr class="odd">
<td align="left"><p>需要重新启动</p></td>
<td align="left"><p>指示在安装或卸载程序包联机时是否需要重新启动。</p></td>
<td align="left"><p>可能</p></td>
</tr>
<tr class="even">
<td align="left"><p>支持信息</p></td>
<td align="left"><p>在何处查找支持信息，如果有的话。</p></td>
<td align="left"><p>http://support.microsoft.com/?kbid=300106</p></td>
</tr>
<tr class="odd">
<td align="left"><p>省/市/自治区</p></td>
<td align="left"><p>指示是否在操作系统中安装软件包。 可能的值如下所示︰</p>
<p><strong>不存在。</strong> 未安装软件包。</p>
<p><strong>安装。</strong> 安装包。</p>
<p><strong>安装挂起。</strong> 该程序包将安装，但需要重新启动才能完成挂起的联机操作。</p>
<p><strong>转移。</strong> 程序包已准备好可以安装。</p></td>
<td align="left"><p>安装</p></td>
</tr>
<tr class="even">
<td align="left"><p>完全脱机功能</p></td>
<td align="left"><p><strong>是的。</strong> 而不启动图像，可以脱机安装包。</p>
<p><strong>否。</strong> 若要完成此程序包的安装，您必须启动到图像。</p>
<p><strong>未确定。</strong> 您可能需要引导才能完成图像到此程序包的安装。 许多软件包可脱机安装完全。 如果您尝试安装的程序包脱机，则需要重新启动，它将报告在日志文件中。 您可以检查包使用 Get PackageInfo 命令的状态。</p>
<p>此字段仅适用于 Windows 8，Windows Server® 2012 和 Windows 预安装环境 (Windows PE) 4.0 版的目标图像。</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>自定义属性</p></td>
<td align="left"><p>程序包清单文件中定义的自定义属性的列表。 如果没有自定义属性，则将显示 （未找到自定义属性）。</p></td>
<td align="left"><p>依赖项︰ 语言包</p></td>
</tr>
<tr class="even">
<td align="left"><p>功能包列表</p></td>
<td align="left"><p>在包中找到的功能列表。</p>
<p>如果在包中没有功能，则将显示程序包标识跟 （没有找到此程序包的功能）。</p></td>
<td align="left"><p><strong>Microsoft-Windows-NetFx3-OC-Package~31bf3856ad364e35~x86~en-US~6.1.6772.0 （没有找到此程序包的功能）</strong></p></td>
</tr>
</tbody>
</table>

 

**若要列出映像中的所有功能**

1.  单击**开始**，然后键入**部署**。 用鼠标右键单击**部署和图像处理工具环境**，然后选择**以管理员身份运行**。

2.  列出有关脱机 Windows 映像，键入以下命令之一中的功能的信息︰

    ``` syntax
    Dism /image:C:\test\offline /Get-Features
    ```

    ``` syntax
    Dism /image:C:\test\offline /Get-Features /PackageName:Microsoft.Windows.Calc.Demo~6595b6144ccf1df~x86~en~1.0.0.0
    ```

    ``` syntax
    Dism /image:C:\test\offline /Get-Features /PackagePath:C:\packages\package.cab
    ```

    对于正在运行的操作系统，请键入下列命令之一︰

    ``` syntax
    Dism /online /Get-Features
    ```

    ``` syntax
    Dism /online /Get-Features /PackageName:Microsoft.Windows.Calc.Demo~6595b6144ccf1df~x86~en~1.0.0.0
    ```

    ``` syntax
    Dism /online /Get-Features /PackagePath:C:\packages\package.cab
    ```

生成的报告包含以下信息︰

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">字段</th>
<th align="left">说明</th>
<th align="left">示例</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>功能名称</p></td>
<td align="left"><p>作为其功能的名称将显示在图像中。</p></td>
<td align="left"><p><strong>InboxGames</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>省/市/自治区</p></td>
<td align="left"><p>该功能的当前状态。 可能的值如下所示︰</p>
<ul>
<li><p><strong>已启用。</strong> 已启用该功能。</p></li>
<li><p><strong>禁用。</strong> 此功能已禁用。</p></li>
<li><p><strong>启用挂起。</strong> 将启用该功能，但需要重新启动才能完成挂起的联机操作。</p></li>
<li><p><strong>禁用挂起。</strong> 该功能将被禁用，但需要重新启动才能完成挂起的联机操作。</p></li>
<li><p><strong>禁用删除负载。</strong> 此功能已禁用，其负载已被删除。 只有包元数据是在图像中存在。 可以还原负载并部署映像后，可以根据需要启用该功能。 即需即装功能的详细信息，请参阅[配置 Windows 修复源](configure-a-windows-repair-source.md)。</p></li>
</ul></td>
<td align="left"><p><strong>禁用</strong></p></td>
</tr>
</tbody>
</table>

 

**列出有关特定功能的信息**

1.  单击**开始**，然后键入**部署**。 用鼠标右键单击**部署和图像处理工具环境**，然后选择**以管理员身份运行**。

2.  列出有关脱机 Windows 映像，键入以下命令之一中的某个特定功能的信息︰

    ``` syntax
    Dism /image:C:\test\offline /Get-FeatureInfo /FeatureName:Hearts
    ```

    ``` syntax
    Dism /image:C:\test\offline /Get-FeatureInfo /FeatureName:LocalPack-GB /PackageName:Microsoft-Windows-LocalPack-GB-Package~6595b6144ccf1df~x86~~1.0.0.0
    ```

    对于正在运行的操作系统，请键入以下命令︰

    ``` syntax
    Dism /online /Get-FeatureInfo /FeatureName:Hearts 
    ```

生成的报告包含以下信息︰

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">字段</th>
<th align="left">说明</th>
<th align="left">示例</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>功能名称</p></td>
<td align="left"><p>功能的名称。</p></td>
<td align="left"><p><strong>InboxGames</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>显示名称</p></td>
<td align="left"><p>作为其功能的名称将显示在用户界面中。</p></td>
<td align="left"><p><strong>游戏</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>说明</p></td>
<td align="left"><p>功能的简短说明。</p></td>
<td align="left"><p>标准的内置游戏。</p></td>
</tr>
<tr class="even">
<td align="left"><p>需要重新启动</p></td>
<td align="left"><p>指示当启用或禁用此功能时是否需要重新启动计算机。</p></td>
<td align="left"><p><strong>是</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>省/市/自治区</p></td>
<td align="left"><p>该功能的当前状态。 可能的值如下所示︰</p>
<p><strong>已启用。</strong> 已启用该功能。</p>
<p><strong>禁用。</strong> 此功能已禁用。</p>
<p><strong>启用挂起。</strong> 将启用该功能，但需要重新启动才能完成挂起的联机操作。</p>
<p><strong>禁用挂起。</strong> 该功能将被禁用，但需要重新启动才能完成挂起的联机操作。</p>
<p><strong>禁用删除负载。</strong> 此功能已禁用，其负载已被删除。 只有包元数据是在图像中存在。 可以还原负载并部署映像后，可以根据需要启用该功能。 即需即装功能的详细信息，请参阅[配置 Windows 修复源](configure-a-windows-repair-source.md)。</p></td>
<td align="left"><p><strong>禁用</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>自定义属性</p></td>
<td align="left"><p>程序包清单文件中定义的自定义属性的列表。 如果没有自定义属性，则将显示 （未找到自定义属性）。</p></td>
<td align="left"><p>依赖项︰ 语言包</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idgetapppackagespanspan-idgetapppackagespanspan-idgetapppackagespanget-app-package-appx-servicing-information"></a><span id="GetAppPackage"></span><span id="getapppackage"></span><span id="GETAPPPACKAGE"></span>获取应用程序软件包 (.appx) 服务信息


可以使用应用程序软件包 (.appx) 服务命令列出 Windows 映像中提供的应用程序。 提供应用程序将注册为 Windows 映像创建每个用户配置文件。

有关应用程序程序包服务命令 DISM 中可用的详细信息，请参阅[DISM 应用程序包 （.appx 或.appxbundle） 服务命令行选项](dism-app-package--appx-or-appxbundle--servicing-command-line-options.md)。

**若要列出 Windows 映像中的提供应用程序**

1.  单击**开始**，然后键入**部署**。 用鼠标右键单击**部署和图像处理工具环境**，然后选择**以管理员身份运行**。

2.  要列出已装载的脱机 Windows 映像中提供应用程序，请键入︰

    ``` syntax
    Dism /image:c:\test\offline /Get-ProvisionedAppxPackages
    ```

    对于正在运行的操作系统，请键入︰

    ``` syntax
    Dism /online /Get-ProvisionedAppxPackages
    ```

生成的报告包含以下信息︰

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">字段</th>
<th align="left">说明</th>
<th align="left">示例</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>DisplayName</p></td>
<td align="left"><p>应用程序的名称。</p></td>
<td align="left"><p>Fabrikam.Sample.CS</p></td>
</tr>
<tr class="even">
<td align="left"><p>版本</p></td>
<td align="left"><p>应用程序软件包的版本号。</p></td>
<td align="left"><p>1.0.0.0</p></td>
</tr>
<tr class="odd">
<td align="left"><p>体系结构</p></td>
<td align="left"><p>应用程序体系结构。</p></td>
<td align="left"><p>neutral</p></td>
</tr>
<tr class="even">
<td align="left"><p>资源 Id</p></td>
<td align="left"><p>有关详细信息，请参阅[应用程序打包词汇表](http://go.microsoft.com/fwlink/p/?linkid=252145)。</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>软件包名称</p></td>
<td align="left"><p>应用程序文件包的全名。</p></td>
<td align="left"><p>Fabrikam.Sample.CS_1.0.0.0_neutral_s9y1p3hwd5qda</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idgetinternationalsettingslangspanspan-idgetinternationalsettingslangspanspan-idgetinternationalsettingslangspanget-international-settings-and-languages"></a><span id="GetInternationalSettingsLang"></span><span id="getinternationalsettingslang"></span><span id="GETINTERNATIONALSETTINGSLANG"></span>获得国际设置和语言


国际服务命令可用于查询现有 Windows 和 Windows PE 映像中的国际设置。 有关 DISM 中可用的操作系统程序包服务命令的详细信息，请参阅[DISM 语言和国际服务命令行选项](dism-languages-and-international-servicing-command-line-options.md)。

**重要**  
国际服务命令不能使用 Windows Vista 或 Windows Server 2008 的图像上。

 

**联机**选项用于显示正在运行的操作系统中的国际设置和语言有关的信息。 使用**/图像︰** &lt;*路径\_到\_脱机\_图像\_目录*&gt;显示脱机映像中的国际设置和语言有关的信息。 当与**/image**和**/distribution**选项一起使用，将显示有关国际设置和语言分布中的信息。

**若要列出所有国际设置和语言**

1.  单击**开始**，然后键入**部署**。 用鼠标右键单击**部署和图像处理工具环境**，然后选择**以管理员身份运行**。

2.  列出有关脱机 Windows 映像，键入以下命令之一中的国际设置的所有信息︰

    ``` syntax
    Dism /image:C:\test\offline /Get-Intl
    ```

    ``` syntax
    Dism /image:C:\test\offline /distribution:C:\windows_distribution\langpacks /Get-Intl
    ```

    对于正在运行的操作系统，请键入以下命令︰

    ``` syntax
    Dism /online /Get-Intl
    ```

生成的报告包含以下信息︰

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">字段</th>
<th align="left">说明</th>
<th align="left">示例</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>默认系统用户界面语言</p></td>
<td align="left"><p>当前设置为默认系统用户界面语言使用的语言。</p></td>
<td align="left"><p><strong>EN-US</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>系统区域设置</p></td>
<td align="left"><p>（也称为系统区域设置） 的非 Unicode 程序和字体设置的语言。</p></td>
<td align="left"><p><strong>EN-US</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>默认时区</p></td>
<td align="left"><p>当前设置为默认的时区。</p></td>
<td align="left"><p>太平洋标准时间</p></td>
</tr>
<tr class="even">
<td align="left"><p>默认用户的用户区域设置</p></td>
<td align="left"><p>&quot;标准和格式&quot;为默认用户设置的语言 （也称为用户区域设置）。</p></td>
<td align="left"><p><strong>EN-US</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>位置</p></td>
<td align="left"><p>当前的操作系统设置地理位置。 有关地理位置的详细信息，请参阅[表的地理位置](http://go.microsoft.com/fwlink/?LinkId=131360)。</p></td>
<td align="left"><p>美国</p></td>
</tr>
<tr class="even">
<td align="left"><p>活动键盘</p></td>
<td align="left"><p>活动键盘值对。 在提供的示例，0409年语言标识符，并且 00000409 键盘标识符。</p></td>
<td align="left"><p><strong>0409: 00000409</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>默认键盘</p></td>
<td align="left"><p>默认键盘值对。 在提供的示例，0409年语言标识符，并且 00000409 键盘标识符。</p></td>
<td align="left"><p><strong>0409: 00000409</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>已安装的语言</p></td>
<td align="left"><p>所有已安装的语言包的列表。</p></td>
<td align="left"><p><strong>EN-US</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>类型</p></td>
<td align="left"><p>每种安装的语言包。 有关详细信息，请参阅[将语言包添加到 Windows](add-language-packs-to-windows.md)。</p></td>
<td align="left"><p><strong>EN-US</strong></p>
<p>类型︰ 完全本地化的语言</p>
<p><strong></strong>ar SA</p>
<p>类型︰ 部分本地化的语言，MUI 类型</p>
<p>备用语言<strong>EN-US</strong>， <strong>FR-FR</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>分发的语言</p></td>
<td align="left"><p>分布共享中可用语言的列表。</p>
<div class="alert">
<strong>请注意</strong>  
<p>此列表包含分布共享中的文件夹的名称。 不验证实际 LP.cab 文件文件夹中的语言。 例如，如果通讯组的路径...\Langpacks\bg-BG\Lp.cab，bg-BG 的值将被视为分布共享中的语言即使 LP.cab 文件不是 bg-BG 的正确.cab 文件。</p>
</div>
<div>
 
</div></td>
<td align="left"><p>在通讯组中的默认语言是︰ <strong>JA-JP</strong></p>
<p>其他可用语言的分布情况是︰ <strong>bg-BG</strong>， <strong>nl NL</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>键盘的分层驱动程序</p></td>
<td align="left"><p>日语或朝鲜语键盘，如果已安装的键盘驱动程序的列表。</p></td>
<td align="left"><p>日语键盘 （106/109 键）</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idgetwindowseditioninformationspanspan-idgetwindowseditioninformationspanspan-idgetwindowseditioninformationspanget-windows-edition-information"></a><span id="GetWindowsEditionInformation"></span><span id="getwindowseditioninformation"></span><span id="GETWINDOWSEDITIONINFORMATION"></span>获取 Windows 版本信息


可以使用版本服务命令可获得有关的信息的 Windows 版本可用于升级。

目标版本的 Windows，您可以升级到的版本。 您可以显示有关当前版本或脱机 Windows 映像或运行的操作系统的目标版本的信息。

有关 Windows 版服务 DISM 中可用的命令的详细信息，请参阅[Windows 版 DISM 服务命令行选项](dism-windows-edition-servicing-command-line-options.md)。

**若要获取有关当前的 Windows 版本的信息**

1.  单击**开始**，然后键入**部署**。 用鼠标右键单击**部署和图像处理工具环境**，然后选择**以管理员身份运行**。

2.  若要列出有关脱机 Windows 映像的当前版本的信息，请键入以下命令︰

    ``` syntax
    Dism /image:C:\test\offline /Get-CurrentEdition
    ```

    对于正在运行的操作系统，请键入以下命令︰

    ``` syntax
    Dism /online /Get-CurrentEdition
    ```

**若要获取有关 Windows 的目标版本的信息**

1.  单击**开始**，然后键入**部署**。 用鼠标右键单击**部署和图像处理工具环境**，然后选择**以管理员身份运行**。

2.  若要列出有关脱机 Windows 映像的目标版本的信息，请键入以下命令︰

    ``` syntax
    Dism /image:C:\test\offline /Get-TargetEditions
    ```

    对于正在运行的操作系统，请键入以下命令︰

    ``` syntax
    Dism /online /Get-TargetEditions
    ```

## <a name="span-idgetapplicationinformationspanspan-idgetapplicationinformationspanspan-idgetapplicationinformationspanget-application-patch-information"></a><span id="GetApplicationInformation"></span><span id="getapplicationinformation"></span><span id="GETAPPLICATIONINFORMATION"></span>获取应用程序的修补程序信息


可以在脱机映像上使用应用程序服务命令行选项，检查 Microsoft® Windows® 安装应用程序修补程序 （.msp 文件） 的适用性，并查询您脱机映像安装 Windows 安装程序的应用程序 （.msi 文件） 有关的信息和应用程序修补程序 （.msp 文件）。

可以显示有关已安装的修补程序和应用程序筛选的 MSP 修补程序的详细的信息。 如果指定**/PatchCode**选项，Windows 安装程序的所有应用程序修补程序应用于为都显示详细的信息。 如果指定**/ProductCode**选项，则将显示在指定的应用程序中的所有 MSP 修补程序的信息。

该特定的修补程序应用于指定的 Windows 安装应用程序时，才显示如果**/PatchCode**和**/ProductCode**选项指定的信息。 如果未指定**/PatchCode**和**/ProductCode**选项，所有安装 Windows 安装程序程序包和 MSP 修补程序的显示。

应用程序服务命令 DISM 中可用的详细信息，请参阅[DISM 应用程序服务命令行选项](dism-application-servicing-command-line-options.md)。

**列出有关已安装的 MSP 修补程序的信息**

1.  单击**开始**，然后键入**部署**。 用鼠标右键单击**部署和图像处理工具环境**，然后选择**以管理员身份运行**。

2.  列表中的信息有关 MSP 修补程序，键入下列命令之一︰

    ``` syntax
    Dism /image:C:\test\offline /Get-AppPatchInfo
    ```

    ``` syntax
    Dism /image:C:\test\offline /Get-AppPatchInfo /PatchCode:{B0B9997C-GUID-GUID-GUID-74D866BBDFFF}
    ```

    ``` syntax
    Dism /image:C:\test\offline /Get-AppPatchInfo /ProductCode:{B0F9497C-GUID-GUID-GUID-74D866BBDF59}
    ```

    ``` syntax
    Dism /image:C:\test\offline /Get-AppPatchInfo /PatchCode:{B0B9997C-GUID-GUID-GUID-74D866BBDFFF} /ProductCode:{B0F9497C-GUID-GUID-GUID-74D866BBDF59}
    ```

生成的报告包含以下信息︰

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">字段</th>
<th align="left">说明</th>
<th align="left">示例</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>修补程序代码</p></td>
<td align="left"><p>GUID 用于标识特定的 Windows 安装程序程序包。 程序包代码将.msi 文件与应用程序或产品，并且还可以用于验证源。</p></td>
<td align="left"><p><strong>{8ACD2816-595D-48AA-A43B-3523CAA4F692}</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>产品代码</p></td>
<td align="left"><p>主要应用程序或产品的标识的 GUID。</p></td>
<td align="left"><p>{7764DEFC-C5D1-413C-8428-2AA903BF6DAA}</p></td>
</tr>
<tr class="odd">
<td align="left"><p>修补程序名称</p></td>
<td align="left"><p>修补程序的注册的显示名称。 修补程序不包括在 MsiPatchMetadata 表中的<strong>显示名称</strong>属性，用于返回的显示名称为空字符串。</p></td>
<td align="left"><p>QFE9-非可移动</p></td>
</tr>
<tr class="even">
<td align="left"><p>修补程序的状态</p></td>
<td align="left"><p>如果此修补程序当前应用到产品中，1。</p>
<p>2 如果已由另一个修补程序取代此修补程序。</p>
<p>4 如果此修补程序已过时的另一个修补程序。</p></td>
<td align="left"><p>1 （应用）</p></td>
</tr>
<tr class="odd">
<td align="left"><p>修补程序卸载</p></td>
<td align="left"><p>1 如果修补程序被标记为可以从产品中卸载。 在这种情况下，安装程序仍可以阻止卸载，如果需要另一个修补程序无法卸载此修补程序。 否则，报告 0。</p></td>
<td align="left"><p>0</p></td>
</tr>
<tr class="even">
<td align="left"><p>帮助链接</p></td>
<td align="left"><p>在何处查找支持信息，如果有的话。</p></td>
<td align="left"><p>http://www.microsoft.com</p></td>
</tr>
<tr class="odd">
<td align="left"><p>转换</p></td>
<td align="left"><p>通过上次安装的修补程序应用到产品中的修补程序转换的集合。 此值可能不能为每个用户的非托管应用程序如果用户没有登录到计算机。</p></td>
<td align="left"><p><strong>: App1RTMToApp1QFE9;: #App1RTMToApp1QFE9</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>本地包</p></td>
<td align="left"><p>产品使用的本地缓存的修补程序文件的位置。</p></td>
<td align="left"><p><strong>C:\Windows\Installer\132f5c.msp</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>安装日期</p></td>
<td align="left"><p>当修补程序已应用到产品中的日期。</p></td>
<td align="left"><p>20080912</p></td>
</tr>
</tbody>
</table>

 

**列出有关 MSP 修补程序应用于应用程序的信息**

1.  单击**开始**，然后键入**部署**。 用鼠标右键单击**部署和图像处理工具环境**，然后选择**以管理员身份运行**。

2.  列表中的信息有关 MSP 修补程序，键入下列命令之一︰

    ``` syntax
    Dism /image:C:\test\offline /Get-AppPatches
    ```

    ``` syntax
    Dism /image:C:\test\offline /Get-AppPatches /ProductCode:{B0F9497C-GUID-GUID-GUID-74D866BBDF59}
    ```

生成的报告包含以下信息︰

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">字段</th>
<th align="left">说明</th>
<th align="left">示例</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>修补程序代码</p></td>
<td align="left"><p>GUID 用于标识特定的 Windows 安装程序包。 程序包代码将.msi 文件与应用程序或产品，并且还可以用于验证源。</p></td>
<td align="left"><p><strong>{8ACD2816-595D-48AA-A43B-3523CAA4F692}</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>产品代码</p></td>
<td align="left"><p>主要应用程序或产品的标识的 GUID。</p></td>
<td align="left"><p><strong>{7764DEFC-C5D1-413C-8428-2AA903BF6DAA}</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>修补程序名称</p></td>
<td align="left"><p>修补程序的注册的显示名称。 修补程序不包括在 MsiPatchMetadata 表中的<strong>显示名称</strong>属性，用于返回的显示名称为空字符串。</p></td>
<td align="left"><p>QFE9-非可移动</p></td>
</tr>
</tbody>
</table>

 

**列出有关所有 Windows 安装程序应用程序信息**

1.  单击**开始**，然后键入**部署**。 用鼠标右键单击**部署和图像处理工具环境**，然后选择**以管理员身份运行**。

2.  若要列出有关 MSP 修补程序的信息，请键入以下命令︰

    ``` syntax
    Dism /image:C:\test\offline /Get-Apps
    ```

生成的报告列出的产品代码和脱机映像中安装的应用程序的产品名称。 例如︰

产品代码︰ **{DB935363-5A68-47AF-A55A-CFC90F2E83BC}**

产品名称︰ MsiTestApplication2

**列出有关特定的 Windows 安装程序应用程序信息**

1.  单击**开始**，然后键入**部署**。 用鼠标右键单击**部署和图像处理工具环境**，然后选择**以管理员身份运行**。

2.  若要列出有关 MSP 修补程序的信息，请键入以下命令︰

    ``` syntax
    Dism /image:C:\test\offline /Get-AppInfo /ProductCode:{B0F9497C-GUID-GUID-GUID-74D866BBDF59}
    ```

生成的报告包含以下信息︰

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">字段</th>
<th align="left">说明</th>
<th align="left">示例</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>产品代码</p></td>
<td align="left"><p>主要应用程序或产品的标识的 GUID。</p></td>
<td align="left"><p><strong>{DB935363-5A68-47AF-A55A-CFC90F2E83BC}</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>产品名称</p></td>
<td align="left"><p>应用程序的名称。</p></td>
<td align="left"><p>MsiTestApplication2</p></td>
</tr>
<tr class="odd">
<td align="left"><p>产品状态</p></td>
<td align="left"><p>在初始化该产品的安装状态。</p>
<p>如果该产品不公布也不安装-1。</p>
<p>如果该产品已公布但未安装，1。</p>
<p>2 如果为不同的用户安装该产品。</p>
<p>5 如果为当前用户安装该产品。</p></td>
<td align="left"><p>5 （已安装）</p></td>
</tr>
<tr class="even">
<td align="left"><p>程序包代码</p></td>
<td align="left"><p>GUID 用于标识特定的 Windows 安装程序包。 程序包代码将.msi 文件与应用程序或产品，并且还可以用于验证源。</p></td>
<td align="left"><p><strong>{C67CA1AE-6074-4810-BD74-F6BBB609744A}</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>产品版本</p></td>
<td align="left"><p>以字符串格式的产品版本。</p></td>
<td align="left"><p>1.0.0</p></td>
</tr>
<tr class="even">
<td align="left"><p>工作分配类型</p></td>
<td align="left"><p>如果产品已公布或安装每个用户，0。</p>
<p>如果产品安装每台计算机的所有用户或将公布的 1。</p></td>
<td align="left"><p>1 （按计算机）</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Publisher</p></td>
<td align="left"><p>该产品制造商的名称。</p></td>
<td align="left"><p>Microsoft MSI 测试</p></td>
</tr>
<tr class="even">
<td align="left"><p>语言</p></td>
<td align="left"><p>产品语言十进制标识符。</p></td>
<td align="left"><p>1033</p></td>
</tr>
<tr class="odd">
<td align="left"><p>安装源</p></td>
<td align="left"><p>目录，它包含源.cab 文件或源文件树的安装程序包。</p></td>
<td align="left"><p><strong>E:\Testpkg\App2_RTM\</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>包名称</p></td>
<td align="left"><p>原始的安装程序包的名称。</p></td>
<td align="left"><p>MsiTestApplication2.msi</p></td>
</tr>
<tr class="odd">
<td align="left"><p>帮助链接</p></td>
<td align="left"><p>在何处查找支持信息，如果有的话。</p></td>
<td align="left"><p>http://www.microsoft.com/management</p></td>
</tr>
<tr class="even">
<td align="left"><p>转换</p></td>
<td align="left"><p>通过上次安装的修补程序应用到产品中的修补程序转换的集合。 此值可能不能为每个用户的非托管应用程序如果用户没有登录到计算机。</p></td>
<td align="left"><p><strong>C:\Windows\Installer\{BDB20E90-3ACD-450B-BBDE-61E39687C6B1} \ACBlueT02.mst</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>本地包</p></td>
<td align="left"><p>本地缓存程序包的位置。</p></td>
<td align="left"><p><strong>C:\Windows\Installer\132f3b.msi</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>安装日期</p></td>
<td align="left"><p>该应用程序的安装日期。</p></td>
<td align="left"><p><strong>20080912</strong></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[使用 DISM Windows 映像提供服务](service-a-windows-image-using-dism.md)

[使用 DISM Windows PE 映像提供服务](service-a-windows-pe-image-with-dism.md)

[部署映像服务和管理 (DISM) 最佳做法](deployment-image-servicing-and-management--dism--best-practices.md)

 

 






