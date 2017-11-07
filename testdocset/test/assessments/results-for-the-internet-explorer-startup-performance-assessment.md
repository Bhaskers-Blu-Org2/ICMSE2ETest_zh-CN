---
title: "Internet Explorer 启动性能评估的结果"
description: "Internet Explorer 启动性能评估的结果"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: c61f4af5-a8ac-4671-98ca-97aaf72bd4f0
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: ff3e22153ad96be8a2ad1185f2dcb996ef59ab94
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="results-for-the-internet-explorer-startup-performance-assessment"></a>Internet Explorer 启动性能评估的结果


Internet Explorer 启动性能评估服务可帮助您评估新的 Internet Explorer 窗口的创建过程中执行的活动。 评估测量完全呈现新的 Internet Explorer 窗口在桌面上，具有一个选项卡和简单内容所需的时间。 此测量包括 IExplore.exe 进程和框架创建和选项卡创建间隔的加载时间。

它还能测量扩展加载并初始化启动过程的性能。 有几种类型的扩展，包括菜单、 工具栏、 浏览器栏和浏览器帮助程序对象 (Bho)。 若要查看在计算机中，在 Internet Explorer 中的**管理加载项**对话框中，在安装的扩展的类型向右选择列标题，选择**列**，然后选择**类型**。

本主题有助于您理解 Internet Explorer 启动性能评估所产生的结果。 有关如何使用结果来识别并解决常见的对启动 Internet Explorer 时您体验产生负面影响的问题，它还提供指导。

本主题︰

-   [目标文件](#bkmk-goals)

-   [指标](#bkmk-iestartupmetrics)

-   [问题](#bkmk-iestartupissues)

有关系统要求和评估设置的详细信息，请参阅[Internet Explorer 启动性能](internet-explorer-startup-performance.md)。

## <a name="a-href-idbkmk-goalsagoals-file"></a><a href="" id="bkmk-goals"></a>目标文件


您可以创建自定义的目标来衡量结果视图中的您改进。 目标文件是会审的工具，可帮助您了解 PC 的性能如何，比较 Pc 业务中。

例如，基本的便携式计算机目标可能不同于为高端桌面计算机设置的目标或者市场预期可能会更改所需的灵活性，可以定义不同类型的目标和时间的推移和技术的关键要求提高的方式中。

度量值是与该指标的目标相比，状态都用颜色编码在结果视图中，如下所示︰

-   浅紫色意味着系统具有出色的用户体验，有没有感觉到的问题。

-   紫色的中等意味着用户体验是容许，可以优化系统。 检查以查看可对系统进行何种改进的建议和分析。 这可能是软件更改，更改配置或硬件更改。

-   深紫色意味着系统有很差的用户体验，并且有重大改进的空间。 检查以查看可对系统进行改进的建议和分析。 这可能是软件更改，更改配置或硬件更改。 您可能需要考虑进行权衡，以便提供 Windows 遇到的高质量。

-   没有颜色的含义有没有定义为度量的目标。

**请注意**  
在 Windows 评估 Toolkit 针对 Windows 8，某些评估包括默认目标文件。 查看使用此版本的工具，结果在第一次使用该默认目标文件。 但是，您还可以定义自定义目标针对 Windows 8 相同的方式，可以为 Windows 8.1 和 Windows 10。

 

您可以设置文件位置的目标并将目标文件添加到该位置之前可用于用户界面应用的自定义目标。 选择目标文件后，它将继续是目标文件，用于打开的任何结果。

可每次只能有一个目标文件。 所有的评估的目标是单个目标文件中设置的。 评估工具将搜索顺序如下目标︰

1.  自定义的目标文件

2.  在结果文件中定义的目标

3.  评估清单中定义的目标

您可以在 %PROGRAMFILES%使用提供了该示例的目标文件\\窗口工具包\\10\\评估和部署工具包\\Windows 评估 Toolkit\\SDK\\样本\\目标来创建目标文件。

**请注意**  
不能包装作业的目标文件，但可以将其存储在供其他用户使用共享。

 

## <a name="a-href-idbkmk-iestartupmetricsametrics"></a><a href="" id="bkmk-iestartupmetrics"></a>指标


本部分介绍报告评估，共同导致的不良结果这些问题每个度量标准和可能的补救措施在 Internet Explorer 启动的指标。 衡量标准的 Internet Explorer 启动阶段对齐。 有的 Internet Explorer 启动六个阶段︰ 处理创建、 框架创建，选项卡创建、 扩展创建 (CoCreateInstance)、 扩展初始化 （设置站点），以及停靠窗口 （对于某些扩展类型） 的显示。 此处介绍的相应指标。

**请注意**  
顶级的**IE 启动持续时间**指标全面，包括创建流程、 框架和选项卡后，运行的任务。

 

-   [创建 Internet Explorer 进程](#bkmkl-createieprocess)

-   [Internet Explorer 框架创建](#bkmk-ieframecreate)

-   [Internet Explorer 选项卡创建](#bkmk-ietabcreate)

-   [创建扩展加载项计数](#bkmk-createextension)

-   [将网站设置为扩展](#bkmk-setextension)

-   [扩展工具栏显示停靠窗口](#bkmk-extensiontoolbar)

**请注意**  
如果启用启用微筛选器诊断模式设置，评估结果将包括微筛选器规格。 有关微筛选器的指标和结果的详细信息，请参阅[微筛选器诊断程序](minifilter-diagnostics.md)。

 

### <a name="a-href-idbkmkl-createieprocessacreate-internet-explorer-process"></a><a href="" id="bkmkl-createieprocess"></a>创建 Internet Explorer 进程

**最适用于︰**设备制造商，反恶意软件供应商

此指标用于衡量创建 Internet Explorer 过程所需的时间。 这包括操作系统开始加载和执行 iexplorer.exe，到 Internet Explorer 开始初始化的帧创建阶段用信号通知的时间之间的时间间隔。 或者，当 iexplorer.exe 启动 （如 Windows 内核由报告） （所报告的 Internet Explorer） 启动创建框架阶段之前的时间间隔。

**典型的影响因素**

-   CPU 速度

-   反恶意软件

**分析和补救措施**

如果评估以一致的方式报告这一阶段时间太长，则建议在 WPA 找到根本原因的深入分析。

### <a name="a-href-idbkmk-ieframecreateainternet-explorer-frame-create"></a><a href="" id="bkmk-ieframecreate"></a>Internet Explorer 框架创建

**最适用于︰**设备制造商、 反恶意软件供应商、 视频驱动程序开发人员

此指标用于衡量完全呈现的窗口框架中 Internet Explorer，包括从启动的时间间隔，以及 Internet Explorer 创建第一个选项卡之前加载或初始化任何扩展，包括创建顶级窗口 （框架） 并初始化该窗口内的 Direct3D 呈现之前所花费的时间。 Internet Explorer 框架的父进程和 UI 容器在一个顶级 Internet Explorer 窗口的选项卡。 选项卡承载在单独的进程，但父进程负责发射用于评估分析的跟踪事件。

**典型的影响因素**

-   CPU 速度

-   反恶意软件

-   视频驱动程序

**分析和补救措施**

如果评估以一致的方式报告时间创建 Internet Explorer 帧的持续时间太长，请按照 WPA 进一步分析链接，请参阅高级详细信息并找到根源。

### <a name="a-href-idbkmk-ietabcreateainternet-explorer-tab-create"></a><a href="" id="bkmk-ietabcreate"></a>Internet Explorer 选项卡创建

**最适用于︰**设备制造商，反恶意软件软件供应商

此指标用于衡量在 Internet Explorer，包括创建和初始化框架中的选项卡，以及创建和初始化所有及其扩展的时间间隔创建新的选项卡所需的时间。 选项卡是流程和用户界面用于单个标签及其内容的容器。 没有始终至少一个选项卡上，尽管可能会在同一进程中承载多个选项卡。 创建并在选项卡的过程中初始化扩展。

**典型的影响因素**

-   CPU 速度

-   反恶意软件

-   Extensions

**分析和补救措施**

扩展的性能分析，建议关注各种扩展相关指标如创建和设置站点。 但是，如果这一阶段以一致的方式报告有时间太长，但不是带标记的单独的扩展的性能，按照 WPA 进一步分析链接，请参阅高级详细信息并找到根源。

### <a name="a-href-idbkmk-createextensionacreate-extensions-addon-count"></a><a href="" id="bkmk-createextension"></a>创建扩展加载项计数

**最适用于︰**设备制造商，反恶意软件供应商

此统计数据枚举 CreateExtension 操作中所涉及的 Internet Explorer 加载项。 您可以展开此统计数据以查看列表中的每个扩展和其相应的持续时间。 对于每个，被指实例化使用 CoCreateInstance() 扩展所需的时间。 这还包括加载的扩展 DLL 和任何其静态 DLL 依赖项的时间。 当 Internet Explorer 初始化加载项时，它首先调用添加的 CLSID，反过来调用该加载项的 CoCreateInstance() 函数模块的 DllGetClassObject() 函数在内存中创建一个对象。 加载项不通常会导致性能延迟在此函数调用过程。 不过，值得关注的同时优化启动性能，因为可以对加载项相关性能降低此函数调用。

**典型的影响因素**

-   CPU 速度

-   DLL 依赖项

-   同步或阻塞 I/O 操作 （磁盘或网络）

-   反恶意软件

**分析和补救措施**

大家在此阶段，不应做扩展，因此此处所用的时间的任何非普通数额可能是个问题。 设备制造商可能需要卸载该扩展。 为扩展作者在 WPA 的深入分析以及下列区域扩展的代码的代码评审建议︰

-   **DllMain**︰ 是 DllMain 方法花时间，在此阶段非普通现象。

-   **DllGetClassObject**︰ 经常花时间在此阶段不常用的 DllGetClassObject 方法。

-   **类构造函数 （c + +） （或同等）**︰ 扩展应不太大，在包括构造函数用于构造 （CLSID 由标识的类） 的类被创建期间。

-   **静态的 DLL 依赖项**︰ 这些都是有至少一个静态导入需求的扩展 DLL 中的 Dll。 他们必须加载并解析窗口将返回从 LoadLibrary() 调用由 Internet Explorer，无论是否实际使用它们之前。

    这不包括 Dll 的延迟加载，通过使用 /DELAYLOAD 或 LoadLibrary()。

    如果特定 DLL 只是偶尔使用，或在启动时或在初始化过程中不使用，请考虑使用 /DELAYLOAD。

-   **动态 DLL 依赖项**︰ 如果扩展名调用 LoadLibrary() API 中，或连接到一个 DLL，它是在 /DELAYLOAD 列表中，则该用法应进行审查，以确定是否它可以推迟到以后。 如果 DLL 是延迟加载，但总是在启动时或在初始化过程中使用，请考虑从 /DELAYLOAD 列表中删除。

    **请注意**  
    这不应为任何 Windows Api 调用取决于正在运行的 Windows 的版本;那些总是应该延迟加载。 例如，如果扩展文本呈现为使用 DirectWrite 和 GDI 用作回退，然后它应不静态链接到 dwrite.dll。 这样做可以完全使其无法在早期版本的 Windows 上装载。

     

**其他信息**

[MSDN: /DELAYLOAD （延迟加载导入）](http://msdn.microsoft.com/library/yx9zd12s.aspx)

### <a name="a-href-idbkmk-setextensionaset-site-for-extensions"></a><a href="" id="bkmk-setextension"></a>将网站设置为扩展

**最适用于︰**扩展的作者，设备制造商

此统计数据枚举 SetSite 操作中所涉及的 Internet Explorer 加载项。 您可以展开此统计数据以查看列表中的每个扩展和其相应的持续时间。 对于每个，被指 Internet Explorer 到扩展名为 IObjectWithSite::SetSite() 的方法调用所花费的时间。 此方法建立与 Internet Explorer 通信扩展的能力。 扩展通常执行此处启动/初始化批量。 这建立添加的初始通信与 Internet Explorer，所有 Internet Explorer 加载项必须都实现 IObjectWithSite 接口公开。 加载项通常在此函数中如显示工具栏用户界面或加载其他模块运行其初始化例程。

**典型的影响因素**

这通常会影响仅由 IObjectWithSite::SetSite() 扩展的实现。 请务必避免同步阻塞/磁盘或网络 I/O 尽可能在此方法的过程中。

**分析和补救措施**

设备制造商可能需要卸载该扩展。 为扩展作者除了 IObjectWithSite::SetSite() 实现的代码评审建议对于 WPA 的深入分析。 可能有的可以推迟到以后的某个时间，或者可能是异步执行的以便他们可以与其他插件的初始化并行运行此代码的某些部分。

**其他信息**

[MSDN: IObjectWithSite 接口](http://msdn.microsoft.com/library/aa768220.aspx)

### <a name="a-href-idbkmk-extensiontoolbaraextension-toolbar-show-docking-window"></a><a href="" id="bkmk-extensiontoolbar"></a>扩展工具栏显示停靠窗口

**最适用于︰**扩展的作者 （工具栏和浏览器栏只）、 设备制造商

此统计数据枚举 Internet Explorer 显示单独的工具栏的加载项。 您可以展开此统计数据以查看列表中的每个扩展和其相应的持续时间。 对于每个计量的 IDockingWindow::ShowDW() 实现中所用的时间间隔。 如果正在初始化该加载项的工具栏或浏览器栏，Internet Explorer 将调用 IDockingWindow::ShowDW() 函数来使附加在浏览器窗口上可见添加的。 某些加载项选择运行其 UI 的呈现代码在该函数内，因此它也会影响启动性能。

**典型的影响因素**

-   CPU 速度

-   复杂的用户界面进行显示或初始化

**分析和补救措施**

设备制造商可能需要卸载加载项。 为扩展作者除了 IDockingWindow::ShowDW() 实现的代码评审建议对于 WPA 的深入分析。

如果扩展运行 UI 的呈现代码，例如 WM\_画图，它可能会将它推迟到以后，根据扩展编写方式。 如果不可能或难避免呈现代码 (WM\_油漆) 在此阶段，您可以尝试延迟呈现以下战略或类似。

1.  创建和扩展的用户界面，而先向其中添加任何子窗口显示主 HWND 使用发送消息发送 WM 后\_SETREDRAW 消息的 wParam 等于 FALSE。

    **警告**  
    这将暂时禁用窗口的所有绘画。 这必须慎用;如果使用不当，它可能导致难以调试的问题。

     

2.  接下来，创建并添加子窗口或内容。

3.  发送窗口另一个 WM\_SETREDRAW 消息的 wParam 值为 TRUE。

4.  使用 InvalidateRect 或 RedrawWindow 进行重绘该窗口。

5.  从 IDockingWindow::ShowDW() 返回。

**其他信息**

[MSDN: IDockingWindow::ShowDW 方法](http://msdn.microsoft.com/library/windows/desktop/bb762050.aspx)

[MSDN: WM\_SETREDRAW 消息](http://msdn.microsoft.com/library/dd145219%28v=vs.85%29.aspx)

## <a name="a-href-idbkmk-iestartupissuesaissues"></a><a href="" id="bkmk-iestartupissues"></a>问题


Internet Explorer 启动性能评估执行高级的问题分析，并提供对 Windows® 性能分析器 (WPA) 标识问题进行故障排除的链接。 当 WPA 打开磁盘活动有关的更多详细信息或 CPU 活动可根据问题的类型。 详细信息深入分析有关问题和建议请参阅， [In-Depth 分析的常见问题](common-in-depth-analysis-issues.md)。

### <a name="the-assessment-reports-an-exit-code-of-0x80050006"></a>评估报告的退出代码为 0x80050006

维护任务已注册的电脑上，但尚未完成之前运行的评估时，将发生此错误。 为维护任务通常会影响评估指标，这样可以防止运行，这样的评估。

要解决此问题，请执行以下任一操作︰

1.  确保计算机已连接到网络和交流电源供电运行。 手动启动，请使用以下命令从提升提示符挂起的维护任务︰

    `rundll32.exe advapi32.dll,ProcessIdleTasks`

2.  禁用定期和空闲状态维护任务，并在运行评估之前停止所有的维护任务。

## <a name="related-topics"></a>相关的主题


[Internet Explorer 启动性能](internet-explorer-startup-performance.md)

[评估服务](assessments.md)

[开/关切换性能](onoff-transition-performance.md)

 

 







