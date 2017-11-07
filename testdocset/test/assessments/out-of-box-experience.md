---
title: "全新安装体验"
description: "全新安装体验"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: D97B30B5-A604-483F-821C-9831218F2AA7
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: beaec02cb8475e66e1725326faad92a15bebd41b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="out-of-box-experience"></a>全新安装体验


适用于︰ Windows 8.1，Windows 10

此评估衡量关键方面首次启动体验 (OOBE) 通常图像自定义项和应用于 Windows 零售映像软件加载项受影响的持续的时间。 从性能跟踪收集 10 为 Windows 系统的第一次启动过程中使用事件跟踪 Windows (ETW) 获得测量结果。 评估措施第一次登录，以及如智能安装和配置应用程序安装的特定方面的持续的时间。

本主题︰

-   [开始之前](#beforebegin)

-   [手动执行的评估](#bkmk-streamingworkloads)

-   [设置](#settings)

## <a name="a-href-idbeforebeginabefore-you-begin"></a><a href="" id="beforebegin"></a>开始之前


**警告** 这一评估不会执行以自动方式。

 

**警告** 图像被测试需要是为了测量成功收集从未--引导状态。 尝试还原回前 OOBE 状态评估的图像将收益率比较结果并不是受支持的方案。

 

## <a name="a-href-idbkmk-streamingworkloadsamanual-execution-of-assessment"></a><a href="" id="bkmk-streamingworkloads"></a>手动执行的评估


这一评估以收集所需数据以便提供结果需要手动执行。 请按照下面的说明。

1.  创建新包作业只 OOBE 评估。
    1.  在 Windows 评估控制台中，选择制造和部署选项卡。 如果没有打开的选项卡上，单击主页页面，然后双击以打开该作业。
    2.  单击包。
    3.  在包到另一台计算机对话框上运行一个作业时，输入将帮助您识别此作业时选择要打开并查看，如包装生产和部署作业结果的说明。
    4.  在包路径框中，键入要用来存储作业包的位置。 对于本练习，位置应该是在可移动媒体中，如 USB 闪存驱动器。
    5.  在结果路径框中，键入要用来存储结果的位置。 默认情况下，这是相对路径。\\结果文件夹中运行作业时的相同位置。
    6.  单击确定。 包装作业时, 将打开该作业的存储的位置。
    7.  USB 闪存驱动器中弹出。

2.  通过安装的 Windows 映像的将评估准备机。
3.  将包复制到此计算机 （理想情况下在不同的磁盘和分区）。
4.  启动机。
5.  当第一个提示显示时，请按"shift + F10"打开管理员命令提示符窗口。
6.  导航到 ADK 包。 运行"cd Assessment1\\%处理器\_体系结构 %"，然后运行"添加\_autologger.reg"。 请确认注册表设置已成功导入。
7.  在命令提示符处，运行"关闭 /r /t 0"。 计算机将重新启动。
8.  一旦重新启动，请输入所需的数据，让计算机继续完成 OOBE。 使用本地或实时帐户在一定条件下的想要测试...
9.  到达桌面，时导航到 ADK 包。 运行"cd Assessment1\\%处理器\_体系结构 %"并运行"停止\_autologger.cmd"。 这将收集与 autologger 和其他相关的日志启动 ETW 跟踪。 文件夹名为"Assessment1\\%处理器\_体系结构 %\\&lt;日期-时间&gt;\_&lt;用户名&gt;\_&lt;名，&gt;"结果创建的位置。
10. 将这些内容复制到具有安装来分析结果在 ADK 的机。

## <a name="settings"></a>Settings


默认情况下，此评估使用推荐的设置。 这些设置定义 microsoft 以确保在不同的计算机配置或一段时间，在同一台计算机上，可以比较结果。 当您查看结果时，请运行的信息包括表示，以便您可以轻松地标识使用除不建议的设置的结果使用推荐的设置的元数据。

如果您想要收集其他数据要比所捕获，默认情况下，还可以自定义这些设置。 例如，可以确定特定的数据，将帮助您执行计算机的某个特定方面的更详细的分析。

下表描述评估建议的设置，设置值，并对每个设置的替代值。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>设置</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>手动收集的 OOBE 日志</p></td>
<td><p>这是包含的跟踪和日志手动执行 OOBE 的文件夹的完整路径。</p>
<p>这是分析所需的参数。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[体验评估出结果](results-for-the-out-of-box-experience-assessment.md)

[Windows 评估 Toolkit 技术参考](windows-assessment-toolkit-technical-reference.md)

[评估服务](assessments.md)

 

 







