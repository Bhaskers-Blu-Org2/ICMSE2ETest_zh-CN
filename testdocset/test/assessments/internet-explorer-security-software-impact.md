---
title: "Internet Explorer 安全软件影响"
description: "Internet Explorer 安全软件影响"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: d71e8ac3-f160-4554-8a26-2d3a95ac059e
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 0feeea13688d55bfea948993a0c5f56ea3b36a8d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="internet-explorer-security-software-impact"></a>Internet Explorer 安全软件影响


Internet Explorer 安全软件影响评估测量方面的 Internet Explorer 通常受到反恶意软件和其他浏览器加载项。 评估措施在显示时间、 CPU 时间和资源利用率的 Internet Explorer 安全软件的影响。

有关结果和这一评估所产生的问题的详细信息，请参阅[Internet Explorer 安全软件影响评估的结果](results-for-internet-explorer-security-software-impact-assessment.md)。

## <a name="before-you-begin"></a>开始之前


Windows 8.1 中的第一次运行帮助提示可以对评估结果产生负面影响。 若要禁用这些，从提升的命令提示符下，运行下面的命令并重新启动计算机︰`reg.exe add "HKLM\Software\Policies\Microsoft\Windows\EdgeUI" /v DisableHelpSticker /t REG_DWORD /d "1" /f`

为了获得最佳效果︰

-   将此评估通过只运行 Windows Defender 使用干净的 Windows 映像与相同电脑上的相同评估结果的结果进行比较。 这将帮助您确定添加到图像反恶意软件的影响。

### <a name="system-requirements"></a>系统要求

您可以在以下操作系统上运行此评估︰

-   Windows 8

-   Windows RT

-   Windows 8.1

-   Windows RT 8.1

-   Windows 10

支持的体系结构包括基于 x86 和基于 x64 的基于 ARM 的系统。

您可以下列方式中的任一 Windows RT 8.1 系统上运行此评估︰

-   打包在 Windows 评估控制台中，该评估作业并运行在 Windows RT 8.1。 有关此选项的详细信息，请参阅[打包作业和运行它在另一台计算机上](package-a-job-and-run-it-on-another-computer.md)。

-   使用 Windows 评估服务。 有关详细信息，请参阅[Windows 评估服务](windows-assessment-services-technical-reference.md)。

## <a name="a-href-idbkmk-settingsasettings"></a><a href="" id="bkmk-settings"></a>设置


您可以使用默认设置或自定义的设置进行评估。 当您查看结果时，您可以看到是否使用评估服务的推荐的设置或自定义设置，以便跨多台计算机或一段时间，可以比较相同作业的结果。

下表描述评估建议的设置，值和每个设置的替代值。

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
<td><p>迭代</p></td>
<td><p>可以使用此设置来指定评估运行的次数。 结果是迭代的平均。 默认情况下，十个迭代运行以便为您提供更准确的结果。</p></td>
</tr>
<tr class="odd">
<td><p>URL</p></td>
<td><p>可以使用此设置指定网站中的评估，而不是使用本地测试页包括评估与测试过程中使用。</p>
<div class="alert">
<strong>请注意</strong>  
<p>我们建议您使用默认设置。 本地测试页面随评估，可以在不使用 internet 连接的情况下运行。 如果指定评估需要互联网连接的网站，可以引入新的变量可能会影响测试的结果。</p>
</div>
<div>
 
</div></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[Internet Explorer 安全软件影响评估的结果](results-for-internet-explorer-security-software-impact-assessment.md)

 

 







