---
title: "边缘安全软件影响"
description: "边缘安全软件影响"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 216cee5b-9665-4324-a25c-a0d3b2d429fd
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 0cf89dae951b10c99e3cddbee8b86153c5f2c94d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="edge-security-software-impact"></a>边缘安全软件影响


适用于︰ Windows 10

边缘安全软件影响评估度量方面的 Microsoft 边缘通常受到反恶意软件。 评估测量启动的影响，并浏览 Microsoft 边缘的时间。

本主题︰

-   [开始之前](#beforebegin)

-   [设置](#settings)

关于这一评估所产生的结果的详细信息，请参阅[边安全软件影响评估的结果](results-for-the-edge-security-software-impact-assessment.md)。

## <a name="a-href-idbeforebeginabefore-you-begin"></a><a href="" id="beforebegin"></a>开始之前


**警告** 请确保 Microsoft 边缘默认 HTTP 协议处理程序。 若要验证这一点，启动设置应用程序，然后定位到"系统-&gt;默认应用程序-&gt;协议来选择默认的应用程序"。 选中的 Microsoft 边缘是 http。

 

为了获得最佳效果︰

-   退出所有打开的桌面应用程序或 Windows 应用程序。
-   完成首次运行任务所需评估、 特定相关的安全应用程序的安装和准备。
-   不进行交互与 PC 运行评估时。

## <a name="settings"></a>Settings


默认情况下，此评估使用推荐的设置。

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
<td><p>使用建议的设置</p></td>
<td><p>默认情况下，选中此复选框，则使用推荐的设置。 若要更改此评估服务的设置，必须首先清除此复选框。</p></td>
</tr>
<tr class="even">
<td><p>URL</p></td>
<td><p>可以使用此设置指定网站中的评估，而不是使用本地测试页包括评估与测试过程中使用。 如果不指定此参数，将使用本地测试页。 可以实时或本地 Url 进行测试。</p></td>
</tr>
<tr class="odd">
<td><p>迭代</p></td>
<td><p>可以使用此设置来指定评估运行的次数。 结果是迭代的平均。</p></td>
</tr>
<tr class="even">
<td><p>最大限度地边缘</p></td>
<td><p>此设置不起作用。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[边缘的安全软件影响评估的结果](results-for-the-edge-security-software-impact-assessment.md)

[Windows 评估 Toolkit 技术参考](windows-assessment-toolkit-technical-reference.md)

[评估服务](assessments.md)

 

 







