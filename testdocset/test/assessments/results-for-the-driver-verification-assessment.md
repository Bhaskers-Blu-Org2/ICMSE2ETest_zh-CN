---
title: "驱动程序验证评估结果"
description: "驱动程序验证评估结果"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 16514264-4581-408b-bd7a-778ca245f0bc
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 61d238f3eb74a6f8ee21e7caa7d1df642ca8352c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="results-for-the-driver-verification-assessment"></a>驱动程序验证评估结果


驱动程序验证评估可以帮助您验证脱机 Windows 映像或运行的 Windows 操作系统中包含正确的驱动程序集。 结果可帮助您识别问题，如丢失、 不必要的和过时的驱动程序。

本主题︰

-   [目标文件](#bkmk-goals)

-   [指标](#bkmk-driverresults)

-   [问题](#bkmk-driverissues)

有关系统要求和评估设置的详细信息，请参阅[驱动程序验证](driver-verification.md)。

## <a name="a-href-idbkmk-goalsagoals-file"></a><a href="" id="bkmk-goals"></a>目标文件


您可以创建自定义的目标来衡量结果视图中的您改进。 目标文件是会审的工具，可帮助您了解 PC 的性能如何，比较 Pc 业务中。

例如，基本的便携式计算机目标可能不同于为高端桌面计算机设置的目标或者市场预期可能会更改所需的灵活性，可以定义不同类型的目标和时间的推移和技术的关键要求提高的方式中。

度量值是与该指标的目标相比，状态都用颜色编码在结果视图中，如下所示︰

-   浅紫色意味着系统具有出色的用户体验，有没有感觉到的问题。

-   紫色的中等意味着用户体验是容许，可以优化系统。 检查以查看可对系统进行何种改进的建议和分析。 这可能是软件更改，更改配置或硬件更改。

-   深紫色意味着系统有很差的用户体验，并且有重大改进的空间。 检查以查看可对系统进行改进的建议和分析。 这可能是软件更改，更改配置或硬件更改。 您可能需要考虑进行权衡，以便提供 Windows 遇到的高质量。

-   没有颜色的含义有没有定义为度量的目标。

在 Windows 评估 Toolkit 针对 Windows 8，某些评估包括默认目标文件。 查看使用此版本的工具，结果在第一次使用该默认目标文件。 但是，您还可以定义自定义目标针对 Windows 8 相同的方式，可以为 Windows 8.1 和 Windows 10。

您可以设置文件位置的目标并将目标文件添加到该位置之前可用于用户界面应用的自定义目标。 选择目标文件后，它将继续是目标文件，用于打开的任何结果。

可每次只能有一个目标文件。 所有的评估的目标是单个目标文件中设置的。 评估工具将搜索顺序如下目标︰

1.  自定义的目标文件

2.  在结果文件中定义的目标

3.  评估清单中定义的目标

您可以在 %PROGRAMFILES%使用提供了该示例的目标文件\\窗口工具包\\10\\评估和部署工具包\\Windows 评估 Toolkit\\SDK\\样本\\目标来创建目标文件。

**请注意**  
不能包装作业的目标文件，但可以将其存储在供其他用户使用共享。

 

## <a name="a-href-idbkmk-driverresultsametrics"></a><a href="" id="bkmk-driverresults"></a>指标


驱动程序验证评估评估您的计算机上的驱动程序并产生结果，可帮助您管理已安装的驱动程序。 下表描述了运行驱动程序验证评估后所提供的度量标准。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>公制</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>所有设备</p></td>
<td><p>列出所有评估发现的设备。 您可以展开的设备的列表，请参阅和标识的设备名称和设备类的指标。</p></td>
</tr>
<tr class="even">
<td><p>与其他问题的设备</p></td>
<td><p>此表中有其他问题比那些专门列出的设备数。</p></td>
</tr>
<tr class="odd">
<td><p>缺少驱动程序的设备</p></td>
<td><p>缺少驱动程序的设备数。 您可以展开该指标缺少驱动程序的设备的列表，请参阅和标识的设备名称和设备类。</p></td>
</tr>
<tr class="even">
<td><p>驱动程序更新可用的设备</p></td>
<td><p>有可用的驱动程序更新的设备数。 您可以展开该指标要查看的设备的列表，并确定设备名称、 更好的驱动程序、 驱动程序文件、 驱动程序供应商和驱动程序的版本。</p></td>
</tr>
<tr class="odd">
<td><p>多个驱动程序的设备</p></td>
<td><p>具有多个驱动程序的设备数。 您可以展开该指标与多个相关联的驱动程序的设备的列表，请参阅和标识的设备名称和设备类。</p></td>
</tr>
<tr class="even">
<td><p>旧设备</p></td>
<td><p>被视为旧设备的设备数。 您可以展开该指标的旧式设备列表，请参阅并确定设备名称、 设备类型、 设备说明、 实例 ID 和设备制造商。</p></td>
</tr>
<tr class="odd">
<td><p>不必要的驱动程序</p></td>
<td><p>有不必要的软件与任何硬件设备没有关联的驱动程序的设备数。 您可以展开此统计数据进行不必要的驱动程序列表，请参阅并确定驱动程序文件、 驱动程序说明驱动程序供应商和驱动程序版本。</p></td>
</tr>
</tbody>
</table>

 

## <a name="a-href-idbkmk-driverissuesaissues"></a><a href="" id="bkmk-driverissues"></a>问题


驱动程序验证评估介绍驱动程序的问题，提供了有关这些问题会影响系统，并提出可能的解决办法的方法的信息。 运行驱动程序验证评估后，可以显示下面的问题和建议。 问题说明、 建议和其他信息的链接，还提供在用户界面中。

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>问题</th>
<th>说明</th>
<th>建议</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>缺少的驱动程序</p></td>
<td><p>没有为此设备找到任何驱动程序。 该设备不会没有适当的驱动程序。</p></td>
<td><p>当连接到互联网，搜索 Windows 更新此设备的驱动程序。 若要自动搜索 Windows 更新缺少驱动程序，请运行评估再次连接到 Internet 时，使用默认设置。 在某些情况下您可能必须联系 OEM 或设备制造商联系以获取该驱动程序。</p></td>
</tr>
<tr class="even">
<td><p>多个驱动程序</p></td>
<td><p>列出多个可用的驱动程序的设备。</p></td>
<td><p>额外的驱动程序会浪费空间，并且可以包含危及计算机的安全漏洞。 我们建议您包括只有必需的驱动程序。 通过使用 DISM，从脱机映像中删除额外的驱动程序或从正在运行的计算机中卸载的驱动程序，使用设备管理器。 有关如何使用 DISM 删除驱动程序的详细信息，请参阅[驱动程序服务命令行选项](http://go.microsoft.com/fwlink/?LinkId=225962)。</p></td>
</tr>
<tr class="odd">
<td><p>不必要的驱动程序</p></td>
<td><p>列出未与任何可用的硬件设备关联的驱动程序。 不必要的驱动程序可能是软件或服务的驱动程序。</p></td>
<td><p>如果不使用此软件或服务，可以考虑将其删除。 额外的驱动程序可以删除脱机使用 DISM，或通过使用设备管理器。 [驱动程序服务命令行选项](http://go.microsoft.com/fwlink/?LinkId=225962)，请参阅。</p></td>
</tr>
<tr class="even">
<td><p>更新更好的驱动程序</p></td>
<td><p>更新的驱动程序是可用的。</p></td>
<td><p>我们建议您更新最佳设备功能的驱动程序。 还有更多最新的驱动程序提供在 Windows 更新。 使用提供的链接来下载驱动程序，或与设备制造商联系，了解进一步的更新。 有关如何使用 Windows 更新的信息，请参阅[Windows 更新的驱动程序发布](http://go.microsoft.com/fwlink/?LinkId=242240)。</p></td>
</tr>
<tr class="odd">
<td><p>旧设备</p></td>
<td><p>列出的设备，并没有插 id。</p></td>
<td><p>Microsoft 设备关联的根枚举设备没有插 id。 按此评估中无法计算此类设备。 使用其他方法来验证该设备的功能。</p></td>
</tr>
</tbody>
</table>

 

### <a name="the-assessment-reports-an-exit-code-of-0x80050006"></a>评估报告的退出代码为 0x80050006

维护任务已注册的电脑上，但尚未完成之前运行的评估时，将发生此错误。 为维护任务通常会影响评估指标，这样可以防止运行，这样的评估。

要解决此问题，请执行以下任一操作︰

1.  确保计算机已连接到网络和交流电源供电运行。 手动启动，请使用以下命令从提升提示符挂起的维护任务︰

    `rundll32.exe advapi32.dll,ProcessIdleTasks`

2.  禁用定期和空闲状态维护任务，并在运行评估之前停止所有的维护任务。

## <a name="related-topics"></a>相关的主题


[驱动程序验证](driver-verification.md)

[Windows 评估 Toolkit](windows-assessment-toolkit-technical-reference.md)

[评估服务](assessments.md)

 

 







