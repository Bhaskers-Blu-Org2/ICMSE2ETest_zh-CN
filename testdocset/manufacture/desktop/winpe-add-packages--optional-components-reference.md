---
author: Justinha
Description: "WinPE︰ 添加软件包 （可选的组件参考）"
ms.assetid: 67aa9c25-9fab-4970-8aa5-65f904969e8e
MSHAttr: PreferredLib:/library/windows/hardware
title: "WinPE︰ 添加软件包 （可选的组件参考）"
ms.openlocfilehash: ea77090f9d579bc951e1a3dda30ab7f540b7328e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="winpe-add-packages-optional-components-reference"></a>WinPE︰ 添加软件包 （可选的组件参考）


将功能包，也称为可选组件，添加到 Windows PE (WinPE)。

**语言**︰ 安装每个可选组件时，您必须首先安装非特定语言的可选组件，然后安装特定于语言的可选组件。 必需的语言资源必须是同一版本为非特定语言的资源。 语言资源都具有相同的名称作为可选组件的目录中安装的语言的文件夹中。

## <a name="span-idbkmk1spanspan-idbkmk1spanadding-optional-components"></a><span id="bkmk_1"></span><span id="BKMK_1"></span>添加可选组件


可选组件包括在 Windows 评估和部署工具包 (Windows ADK)，在 c:\\程序文件\\窗口工具包\\10\\评估和部署工具包\\Windows 预安装环境\\amd64\\WinPE\_OCs\\文件夹。

**使用 Windows PE 工具获取 Windows 评估和部署工具包**

-   安装[Windows 评估和部署工具包 (Windows ADK) 技术参考](http://go.microsoft.com/fwlink/p/?LinkId=526803)，其中包括 Windows PE 功能。

**创建一套 32 位或 64 位的 Windows PE 文件**

1.  单击**开始**，然后键入**部署**。 用鼠标右键单击**部署和图像处理工具环境**，然后选择**以管理员身份运行**。

2.  中的**部署工具和图像管理环境**，Windows PE 文件复制要用来启动的电脑。

    -   64 位版本可以引导 UEFI 64-位和 64 位 BIOS 电脑。

        ``` syntax
        copype amd64 C:\WinPE_amd64
        ```

    -   32 位 （uefi）、 32 位 BIOS 和 64 位 BIOS Pc，可以引导 32 位版本。

        ``` syntax
        copype x86 C:\WinPE_x86
        ```

**装载 Windows PE 启动映像**

-   Windows PE 映像装载。

    ``` syntax
    Dism /Mount-Image /ImageFile:"C:\WinPE_amd64\media\sources\boot.wim" /index:1 /MountDir:"C:\WinPE_amd64\mount"
    ```

**添加可选组件 （包或.cab 文件）**

1.  在 Windows PE 中添加的可选组件。 若要添加可选组件，您需要添加的可选组件和其相关的语言包。

    ``` syntax
    Dism /Add-Package /Image:"C:\WinPE_amd64\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-HTA.cab"  

    Dism /Add-Package /Image:"C:\WinPE_amd64\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-HTA_en-us.cab"
    ```

    **重要**  
    某些可选组件都必须按顺序安装的系统必备组件。 在此页上看到的可选组件的列表。

     

2.  验证的可选组件是图像的一部分︰

    ``` syntax
    Dism /Get-Packages /Image:"C:\WinPE_amd64\mount"
    ```

    检查生成的软件包列表并验证，该列表包含的可选组件和其相关的语言包。

**向包含可选组件的图像中添加更多的语言**

1.  列出 Windows PE 映像中的可选组件︰

    ``` syntax
    Dism /Get-Packages /Image:"C:\WinPE_amd64\mount"
    ```

2.  查看生成的软件包列表并在图像中，包括了基本的 Windows PE 的语言包中添加相应的语言包，每包。

    ``` syntax
    Dism /Add-Package /Image:"C:\WinPE_amd64\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\lp.cab"

    Dism /Add-Package /Image:"C:\WinPE_amd64\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-HTA_fr-fr.cab"
    ```

    在哪里... WinPE\_OCs\\fr fr\\lp.cab 表示基本的 Windows PE 的语言包。

3.  如果您要添加的日本、 韩国或中国的语言包，添加这些语言的字体软件包。 这里是日本的一个示例︰

    ``` syntax
    Dism /Add-Package /Image:"C:\WinPE_amd64\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-Font Support-JA-JP.cab"
    ```

4.  验证语言包是图像的一部分︰

    ``` syntax
    Dism /Get-Packages /Image:"C:\WinPE_amd64\mount"
    ```

    查看生成的软件包列表并验证每个可选的组件，其中包括基本的 Windows PE 映像中，是否存在相关的语言包。

5.  将区域设置更改为您想要使用的语言︰

    ``` syntax
    Dism /Set-AllIntl:en-US /Image:"C:\WinPE_amd64\mount"
    ```

    若要切换语言在 Windows PE 时，使用`wpeutil setmuilanguage`。

**卸载 Windows PE 映像并创建媒体**

1.  卸载 Windows PE 映像。

    ``` syntax
    Dism /Unmount-Image /MountDir:"C:\WinPE_amd64\mount" /commit
    ```

2.  创建可引导介质，如 USB 闪存驱动器。

    ``` syntax
    MakeWinPEMedia /UFD C:\WinPE_amd64 F:
    ```

3.  引导介质。 Windows PE 将自动启动。 Windows PE 窗口出现后，wpeinit 命令将自动运行。 这可能需要几分钟的时间。 请验证您的自定义。

## <a name="span-idbkmkbspanspan-idbkmkbspanlist-of-optional-components"></a><span id="bkmk_b"></span><span id="BKMK_B"></span>可选组件列表


<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">区域/可选组件名称</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>数据库/WinPE-MDAC</p></td>
<td align="left"><p>WinPE MDAC 支持 Microsoft® 开放式数据库连接(ODBC) (ODBC)、 OLE DB 和 Microsoft ActiveX® 数据对象 (ADO)。 这套技术提供了访问各种数据源，例如 Microsoft SQL Server®。 例如，这种访问使 Microsoft SQL Server 安装包含 ADO 对象的查询。 您可以构建一个动态的应答文件根据唯一的系统信息。 同样，您可以生成数据驱动客户端或服务器应用程序集成来自各种数据源，这两个关系 (SQL Server) 的信息和非关系。</p></td>
</tr>
<tr class="even">
<td align="left"><p>文件管理/WinPE-FMAPI</p></td>
<td align="left"><p>WinPE FMAPI 提供从加密卷访问到 Windows PE 文件管理 API (FMAPI) 发现和恢复已删除的文件。 FMAPI 还提供了用于发现和恢复已删除的文件从 Windows BitLocker 驱动器加密加密卷的密码或恢复密钥文件的能力。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>字体/WinPE 字体-旧式</p></td>
<td align="left"><p>WinPE 字体旧式包含各种语言/编写脚本的 32 字体文件。 这些字体的一些不再用作用户界面字体。 例如，如孟加拉语、 梵文、 古吉拉特语、 锡克教文、 卡纳达语、 马拉雅拉姆语、 Odia、 泰米尔语、 泰卢固语和僧伽罗语的脚本所覆盖 Mangal、 Latha、 Vrinda、 Gautami、 Kalinga、 artika、 Raavi、 Shruti 和 Tunga，但是 Windows 8 中他们所有统一下 Nirmala UI，单一、 平移印度洋的字体。 下面的列表显示的字体和语言包括在此可选组件︰</p>
<ul>
<li><p>estre.ttf 福音体文字 Edessa （叙利亚）</p></li>
<li><p>mvboli.ttf MV Boli （塔安那文）</p></li>
<li><p>高棉语 KhmerUI.ttf 用户界面 （UI 高棉语）</p></li>
<li><p>高棉语 KhmerUIB.ttf UI 加粗 (高棉文 UI)</p></li>
<li><p>Laoui.ttf 老挝语 UI （老挝语）</p></li>
<li><p>Laouib.ttf 老挝语 UI 加粗 （老挝语）</p></li>
<li><p>daunpenh.ttf DaunPenh （高棉语）</p></li>
<li><p>moolbor.ttf MoolBoran （高棉语）</p></li>
<li><p>dokchamp.ttf DokChampa （老挝语）</p></li>
<li><p>Himalaya.ttf Microsoft Himalaya （藏文）</p></li>
<li><p>蒙古语 monbaiti.ttf Baiti （蒙古文）</p></li>
<li><p>MSYI.ttf Microsoft Yi Baiti （彝文音节）</p></li>
<li><p>nyala.ttf Nyala （埃塞俄比亚语）</p></li>
<li><p>sylfaen.ttf Sylfaen (亚美尼亚语&amp;格鲁吉亚语)</p></li>
<li><p>euphemia.ttf Euphemia （统一加拿大土著语言符号）</p></li>
<li><p>plantc.ttf Plantagenet 切罗基文 （切罗基文）</p></li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><p>字体/WinPE 字体支持-JA-JP</p></td>
<td align="left"><p>WinPE 字体支持-JA-JP 包含打包为 TrueType 集合 (TTC) 文件的两个日语字体系列。 宋体是 Windows Vista 之前的 Windows 版本中的 Windows 日语用户界面字体。 宋体包含大字符集和嵌入的位图，以确保小的时候清晰呈现。 Meiryo，在 Windows Vista 中，引入了一种字体是专门设计用于在 Microsoft ClearType® 环境中呈现。 Meiryo 不包括嵌入的位图。 相反，Meiryo 依赖提示指令，以产生清晰的字符在较小的尺寸。 此外，该模块包含两个日本的位图字体，App932.fon 和 Vga932.fon。 该模块还包含仅用于位图的 TrueType 字体，Jpn_font.ttf。 该字体用于在启动屏幕上。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>字体/WinPE 字体支持-KO-KR</p></td>
<td align="left"><p>WinPE 字体支持-KO-KR 包含三个核心朝鲜语字体系列︰ Gulim、 Batang 和微软雅黑。 Gulim 是传统用户界面字体，并作为 TTC 文件，包含 Gulim、 GulimChe、 Dotum 和 DotumChe。 Batang 是旧版文本字体，还有 TTC 包含 Batang、 BatangChe、 GungSuh 和 GungSuhChe 的文件。 微软雅黑，在 Windows Vista 中，引入了一种字体是专门设计用于在一个清晰的呈现环境。 微软雅黑不包含嵌入的位图，而是依赖于提示指令，以产生清晰的字符在较小的尺寸。</p></td>
</tr>
<tr class="even">
<td align="left"><p>字体/WinPE 字体支持-ZH-CN</p></td>
<td align="left"><p>WinPE 字体支持中文 CN 包含作为 TTC 文件打包在一起的两个中文字体系列。 Simsun 是在 Windows Vista 之前的 Windows 版本的简化中文版用户界面字体。 Simsun 包含嵌入的位图，以确保小的时候清晰呈现。 其他 TTC 字体为 MingLiu。 MingLiu 有嵌入的位图，并提供支持的香港附属字符设置 (HKSCS)。 雅黑，在 Windows Vista 中，引入了一种字体是专门设计用于在一个清晰的呈现环境。 雅黑不包括嵌入的位图。 雅黑依赖提示指令，以产生清晰的字符在较小的尺寸。 此外，该模块包含一个位图 TrueType 字体，Chs_boot.ttf。 该字体用于在启动屏幕上。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>字体/WinPE 字体支持的 ZH-香港</p><p> 和 </p>
<p>WinPE 字体支持-ZH-TW</p></td>
<td align="left"><p>香港和台湾的可选组件包含作为 TTC 文件打包在一起的两个中文字体系列。 Simsun 是在 Windows Vista 之前的 Windows 版本的简化中文版用户界面字体。 Simsun 包含嵌入的位图，以确保小的时候清晰呈现。 MingLiu 有嵌入的位图，并提供了对 HKSCS 的支持。 JhengHei，在 Windows Vista 中，引入了一种字体是专门设计用于在一个清晰的呈现环境。 JhengHei 不包括嵌入的位图。 JhengHei 依赖提示指令，以产生清晰的字符在较小的尺寸。 此外，该模块包含一个位图 TrueType 字体，Cht_boot.ttf。 该字体用于在启动屏幕上。</p></td>
</tr>
<tr class="even">
<td align="left"><p>HTML/WinPE-HTA</p></td>
<td align="left"><p>WinPE HTA 提供 HTML 应用程序 (HTA) 支持创建的 Windows Internet Explorer® 脚本引擎和 HTML 服务通过 GUI 应用程序。 这些应用程序是受信任并显示菜单、 图标、 工具栏和您创建的标题信息。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Microsoft.NET/WinPE-NetFX</p></td>
<td align="left"><p>WinPE NetFX 包含用于客户端应用程序的.NET Framework 4.5 的一个子集。</p>
<p>不是所有 Windows 二进制文件都都在 Windows PE 中，并因此不是所有的 Windows Api 都是存在或无法使用。 由于有限的 API 集，以下.NET Framework 功能没有或较少的功能在 Windows PE 中︰</p>
<ul>
<li><p>Windows Presentation Foundation (WPF)</p></li>
<li><p>Windows 运行时</p></li>
<li><p>.NET Framework 合成 Api</p></li>
<li><p>Windows 控件库事件日志记录</p></li>
<li><p>.NET Framework COM 互操作性</p></li>
<li><p>.NET Framework 加密模型</p></li>
</ul>
<p><strong>依赖项</strong>︰ 安装<strong>WinPE WMI</strong> ，然后再安装<strong>WinPE NetFX</strong>。</p></td>
</tr>
<tr class="even">
<td align="left"><p>网络/WinPE-Dot3Svc</p></td>
<td align="left"><p>添加支持 IEEE 802.X 有线网络上的身份验证协议。 有关详细信息，请参阅[WinPE 网络驱动程序︰ 初始化和添加驱动程序](winpe-network-drivers-initializing-and-adding-drivers.md)。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>网络/WinPE-PPPoE</p></td>
<td align="left"><p>WinPE PPPoE 使您能够使用点对点协议 (PPPoE) 以太创建、 连接、 断开连接，并删除 Windows PE PPPoE 连接。 PPPoE 是封装内部以太网帧的点对点协议 (PPP) 帧的网络协议。 PPPoE 使 Windows 用户将其计算机远程连接到 web。 通过使用 PPPoE，用户可以几乎拨从一台计算机到另一通过以太网，以建立点对点的连接的计算机之间。 计算机可以使用此点到点连接来传输数据包。</p></td>
</tr>
<tr class="even">
<td align="left"><p>网络/WinPE-RNDIS</p></td>
<td align="left"><p>WinPE RNDIS 包含远程网络驱动程序接口规范 (NDIS 远程) 的支持。 WinPE RNDIS 使网络支持通过 USB 实现远程 NDIS 规范的设备。 远程 NDIS 定义独立于总线的消息集和描述该消息集各种 I/O 总线上的运行方式。 因此，硬件供应商不需要编写 NDIS 微型端口设备驱动程序。 此远程 NDIS 接口的标准化，因为一套主机驱动程序可以支持任意数量的总线连接网络的设备。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>网络/WinPE-WDS 的工具</p></td>
<td align="left"><p>WinPE WDS 工具包括启用映像捕获工具和多播的方案，其中涉及到自定义的 Windows 部署服务客户端的 Api。 如果要在自定义的 Windows PE 映像上运行的 Windows 部署服务客户端必须安装它。</p></td>
</tr>
<tr class="even">
<td align="left"><p>网络/WinPE-WiFi-包</p></td>
<td align="left"><p>Windows 恢复环境 (Windows RE) 使用 WinPE WiFi 包。 此软件包包含基本的 winre.wim 文件中。</p>
</tr>
<tr class="odd">
<td align="left"><p>Windows PowerShell / WinPE-PlatformID</p></td>
<td align="left"><p>WinPE PlatformID 包含 Windows PowerShell cmdlet 检索的物理计算机的平台标识符。 </p>
<p><strong>依赖项</strong>︰ 安装<strong>WinPE WMI</strong>和<strong>WinPE SecureStartup</strong> ，然后再安装<strong>WinPE PlatformID</strong>。</p>
<p>若要使用 Windows PowerShell cmdlet 检索平台标识符，您将需要安装<strong>WinPE PowerShell</strong>包。</p></td>
</tr>
<tr class="even">
<td align="left"><p>Windows PowerShell / WinPE-PowerShell</p></td>
<td align="left"><p>WinPE PowerShell 包含基于 Windows PowerShell 的诊断程序，可简化使用 Windows 管理工具 (WMI) 查询在制造硬件。 您可以创建基于 Windows PowerShell 的部署和管理基于 Windows PE 的工具。 除了部署，还可以恢复情况下使用 Windows PowerShell。 客户可以在 Windows 重新启动，然后使用 Windows PowerShell 脚本来解决问题。 客户并不局限于在 Windows PE 中运行的工具集。 同样，您可以生成脚本脱机解决方案，以恢复某些计算机无法引导方案。</p>
<p>WinPE PowerShell 包含以下已知的限制︰</p>
<ul>
<li><p>不支持 Windows PowerShell 远程处理。 任何的 cmdlet 所具有的远程处理功能将返回错误。</p></li>
<li><p>不支持 Windows PowerShell 集成脚本环境 (ISE)。</p></li>
<li><p>不支持 Windows PowerShell 2.0。</p></li>
</ul>
<p><strong>依赖项</strong>︰ 安装<strong>WinPE WMI</strong> &gt; <strong>WinPE NetFX</strong> &gt; <strong>WinPE 脚本</strong>安装<strong>WinPE PowerShell</strong>之前。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Windows PowerShell / WinPE-DismCmdlets</p></td>
<td align="left"><p>WinPE DismCmdlets 包含 DISM PowerShell 模块，其中包含用于管理和处理 Windows 映像的 cmdlet。</p>
<p>有关更多信息，请参阅[部署映像服务管理 (DISM) 在 Windows PowerShell 的 Cmdlet](http://go.microsoft.com/fwlink/p/?linkid=290822)。</p>
<p><strong>依赖项</strong>︰ 安装<strong>WinPE WMI</strong> &gt; <strong>WinPE NetFX</strong> &gt; <strong>WinPE 脚本</strong> &gt; <strong>WinPE PowerShell</strong>之前安装<strong>WinPE DismCmdlets</strong>。</p></td>
</tr>
<tr class="even">
<td align="left"><p>Windows PowerShell / WinPE-SecureBootCmdlets</p></td>
<td align="left"><p>WinPE SecureBootCmdlets 包含用于管理安全引导 UEFI （统一可扩展固件接口） 环境变量的 PowerShell cmdlet。</p>
<p><strong>依赖项</strong>︰ 安装<strong>WinPE WMI</strong> &gt; <strong>WinPE NetFX</strong> &gt; <strong>WinPE 脚本</strong> &gt; <strong>WinPE PowerShell</strong>之前安装<strong>WinPE SecureBootCmdlets</strong>。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Windows PowerShell / WinPE-StorageWMI</p></td>
<td align="left"><p>WinPE StorageWMI 包含 PowerShell cmdlet 的存储管理。 这些 cmdlet 使用 Windows 存储管理 API (SMAPI) 来管理本地存储，如磁盘、 分区和卷对象。 或者，这些 cmdlet 使用数组存储管理以及 Windows SMAPI 使用存储管理提供程序。 WinPE StorageWMI 还包含 Internet SCSI (iSCSI) 连接到以太网网络适配器或 iSCSI 主机总线适配器 (HBA) 通过外部基于 iSCSI 的存储阵列上的虚拟磁盘的主机或服务器启动器 cmdlet。</p>
<p><strong>依赖项</strong>︰ 安装<strong>WinPE WMI</strong> &gt; <strong>WinPE NetFX</strong> &gt; <strong>WinPE 脚本</strong> &gt; <strong>WinPE PowerShell</strong>之前安装<strong>WinPE StorageWMI</strong>。</p></td>
</tr>
<tr class="even">
<td align="left"><p>恢复/WinPE-Rejuv</p></td>
<td align="left"><p>Windows 恢复环境 (Windows RE) 使用 WinPE Rejuv。 此软件包包含基本的 winre.wim 文件中。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>恢复/WinPE-SRT</p></td>
<td align="left"><p>使用 Windows RE WinPE SRT。 此软件包包含基本的 winre.wim 文件中。</p></td>
</tr>
<tr class="even">
<td align="left"><p>恢复/WinPE-WinReCfg</p></td>
<td align="left"><p>WinPE WinReCfg 包含 Winrecfg.exe 工具，并使以下情况︰</p>
<ul>
<li><p>从基于 x86 的 Windows PE 在离线的基于 x64 的操作系统映像上配置 Windows RE 设置引导。</p></li>
<li><p>从基于 x64 的 Windows PE 在离线的基于 x86 的操作系统映像上配置 Windows RE 设置引导。</p></li>
</ul>
</tr>
<tr class="odd">
<td align="left"><p>脚本/WinPE-脚本</p></td>
<td align="left"><p>WinPE 脚本包含多语言脚本环境，非常适合于自动化系统管理任务，如批处理文件。 WSH 对象和其他支持自动化，例如 WMI 管理是许多系统管理任务的核心 Windows 子系统的基于 COM 技术，可以调用 Windows 脚本宿主 (WSH) 环境中运行的脚本。</p>
<p><strong>依赖项</strong>︰ 在使用 WinPE NetFX 和 WinPE HTA 时安装 WinPE-脚本以确保完整的脚本功能才可用。 安装顺序无关。</p></td>
</tr>
<tr class="even">
<td align="left"><p>脚本/WinPE WMI</p></td>
<td align="left"><p>WinPE WMI 包含启用最少的系统诊断程序的 Windows 管理规范 (WMI) 提供程序的一个子集。 WMI 是管理数据和操作上的基于 Windows 的操作系统的基础结构。 您可以编写 WMI 脚本或应用程序在远程计算机上的管理任务自动执行。 此外，WMI 提供管理数据系统和产品的其他部分。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>安装/Winpe-LegacySetup</p></td>
<td align="left"><p>Winpe LegacySetup 包含从 \Sources 文件夹在 Windows 媒体上的所有安装文件。 当服务安装程序或 Windows 媒体上的 \Sources 文件夹中添加此可选组件。 您必须添加此可选组件一起安装功能的可选组件。 若要将新的 Boot.wim 文件添加到媒体，添加父 WinPE-安装程序，或者儿童 （客户端安装 WinPE 或 WinPE 安装服务器），和媒体的可选组件。 支持 Windows Server 2008 R2 安装需要媒体安装程序。</p></td>
</tr>
<tr class="even">
<td align="left"><p>安装/WinPE-安装程序</p></td>
<td align="left"><p>WinPE-安装程序安装 WinPE 端和 WinPE 设置服务器的父级。 它包含 \Sources 文件夹中所有通用的客户端和服务器的安装文件。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>安装/WinPE 端安装客户端</p></td>
<td align="left"><p>客户端安装 WinPE 包含父 WinPE-安装可选组件的客户端署名文件。</p>
<p><strong>依赖项</strong>︰ 安装<strong>WinPE-安装程序</strong>，然后再安装<strong>WinPE 端安装客户端</strong>。</p></td>
</tr>
<tr class="even">
<td align="left"><p>安装/WinPE-安装服务器</p></td>
<td align="left"><p>WinPE 安装服务器包括父 WinPE-安装可选组件的服务器品牌文件。</p>
<p><strong>依赖项</strong>︰ 安装<strong>WinPE-安装程序</strong>，然后再安装<strong>WinPE 安装服务器</strong>。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>启动/WinPE-SecureStartup</p></td>
<td align="left"><p>WinPE SecureStartup 使资源调配和管理 BitLocker 和受信任的平台模块 (TPM)。 它包括 BitLocker 的命令行工具、 BitLocker WMI 管理库、 TPM 驱动程序、 TPM 基础服务 (TB)、 <strong>Win32_TPM</strong>类，BitLocker 解除锁定向导和 BitLocker UI 库。 TPM 驱动程序提供了更好的支持，BitLocker 和在此环境中预启动 TPM。</p>
<p><strong>依赖项</strong>︰ 安装<strong>WinPE WMI</strong> ，然后再安装<strong>WinPE SecureStartup</strong>。</p></td>
</tr>
<tr class="even">
<td align="left"><p>存储/WinPE-EnhancedStorage</p></td>
<td align="left"><p>WinPE EnhancedStorage 使 Windows 发现的存储设备，如加密的驱动器，并将受信任的计算组 (TCG) 和 IEEE 1667 结合的实现的附加功能 (&quot;标准主机附件的暂时性存储设备中的身份验证协议&quot;) 规范。 此可选组件，Windows 可以使用 BitLocker 本身管理这些存储设备。</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idwindowsreoptionalcomponentsspanspan-idwindowsreoptionalcomponentsspanspan-idwindowsreoptionalcomponentsspanwindows-re-optional-components"></a><span id="Windows_RE_optional_components"></span><span id="windows_re_optional_components"></span><span id="WINDOWS_RE_OPTIONAL_COMPONENTS"></span>Windows RE 可选组件


默认 Windows RE 映像包含以下内置可选组件︰

-   WinPE-EnhancedStorage

-   WinPE-Rejuv

-   WinPE 脚本

-   WinPE-SecureStartup

-   WinPE-安装程序

-   WinPE SRT

-   WinPE WDS 工具

-   WinPE WMI

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题

[WinPE︰ 优化并缩小图像](winpe-optimize.md)

[对于 Windows 10 WinPE](winpe-intro.md)

[WinPE︰ 安装和自定义](winpe-mount-and-customize.md)

 

 






