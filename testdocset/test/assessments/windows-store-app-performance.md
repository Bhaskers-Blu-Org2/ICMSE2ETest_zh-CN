---
title: "Windows 应用商店应用程序性能"
description: "Windows 应用商店应用程序性能"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: dfd6d400-fd14-4fbb-b75f-657b4a213026
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 5cdd93b75be954b6d8d1e8e2f6f4d0ffadf8e989
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-store-app-performance"></a>Windows 应用商店应用程序性能


Windows 应用商店应用程序性能评估服务可帮助您优化您的应用程序更好的客户体验。 评估测量多快的速度应用程序打开并将暂停，并在 PC 上使用的资源量。 可以使用此评估服务可帮助您提高单个应用程序，或可帮助您优化的领料快速、 流畅的应用程序很好地在您的 PC 上运行的 Windows 映像。

本主题︰

-   [开始之前](#bkmk-begin)

-   [设置](#bkmk-settings)

有关结果和这一评估所产生的问题的详细信息，请参阅[Windows 商店应用程序性能评估服务的结果](results-for-the-windows-store-app-performance-assessment.md)。

## <a name="a-href-idbkmk-beginabefore-you-begin"></a><a href="" id="bkmk-begin"></a>开始之前


**警告**  
Windows 8.1 中的第一次运行帮助提示可以对评估结果产生负面影响。 若要禁用这些，从提升的命令提示符下，运行下面的命令并重新启动计算机︰`reg.exe add "HKLM\Software\Policies\Microsoft\Windows\EdgeUI" /v DisableHelpSticker /t REG_DWORD /d "1" /f`

 

**警告**  
仅在桌面处于全屏模式时，请运行此评估。 如果您有另一个 Windows 应用商店应用程序打开的并行与桌面，则不要运行此评估。

 

**请注意**  
Windows 应用商店应用程序性能评估只提供在计算机上的 Windows 应用商店应用程序的结果，它不会评估桌面应用程序。

 

为了获得最佳效果︰

-   退出所有打开的桌面应用。

-   完成应用程序想要评估的任何首次运行任务。 例如，某些应用程序要求用户登录，用户接受许可协议或 UI 设置的第一次运行该应用程序。

-   请确保所有的应用程序处于最新状态。 您可以打开 Windows 应用商店要检查有任何挂起的更新对您的 PC 上安装的应用程序。

-   不进行交互与 PC 运行评估时。

-   确保，Ngen.exe 已为运行之前评估的第一次运行每个应用程序通过执行以下任一项︰

    1.  通过提升的提示符下运行以下命令手动运行 Ngen.exe 替换*&lt;DotNetVersion&gt; * .NET 的计算机上安装的任何版本︰

        `%WinDir%\Microsoft.NET\Framework\<DotNetVersion>\Ngen.exe ExecuteQueuedItems`

    2.  大约 30 秒钟运行应用程序。 这会导致包括 Ngen.exe 运行的计划的任务。

### <a name="system-requirements"></a>系统要求

您可以在以下操作系统上运行此评估︰

-   Windows 8

-   Windows® RT

-   Windows 8.1

-   Windows RT 8.1

-   Windows 10

支持的体系结构包括基于 x86 和基于 x64 的基于 ARM 的系统。

您可以下列方式中的任一 Windows RT 8.1 系统上运行此评估︰

-   打包在 Windows® 评估控制台中，该评估作业并运行在 Windows RT 8.1。 有关此选项的详细信息，请参阅[包作业，并在另一台计算机上运行它](package-a-job-and-run-it-on-another-computer.md)。

-   使用 Windows 评估服务。 有关详细信息，请参阅[Windows 评估服务技术参考](http://go.microsoft.com/fwlink/?LinkId=215628)。

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
<td><p>可以使用此设置来指定评估运行的次数。 结果是迭代的平均。 默认情况下，运行三个小版本为您提供更准确的结果。</p>
<div class="alert">
<strong>请注意</strong>  
<p>在每次迭代期间评估打开每个 Windows 应用商店应用程序。 每个迭代的长度成正比所评估的应用程序的总次数。 在准备阶段的评估，应用程序还可能会打开。</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td><p>重新启动每个 Windows 应用商店应用程序</p></td>
<td><p>您可以使用此设置强制每个应用程序，而不是恢复可能已经在计算机上打开的应用程序重新启动。</p></td>
</tr>
<tr class="even">
<td><p>请输入 Windows 应用商店应用程序名称</p></td>
<td><p>您可以使用此设置来指定要用于评估而不是对所有应用程序运行评估应用程序名称。 评估将包括与您输入的名称匹配的所有应用程序。 可以使用部分应用程序名称以匹配多个应用程序。 例如，如果您输入<strong>Contoso</strong>在 PC 上使用<strong>Contoso 财务</strong>应用程序和安装<strong>Contoso 新闻</strong>应用程序，评估将包括这两个应用程序。</p></td>
</tr>
<tr class="odd">
<td><p>启用详细的 CPU 度量标准</p></td>
<td><p>此设置可用于获取有关 CPU 使用率详解应用程序的详细的信息。 您需要配置要使用此设置的符号。 有关详细信息，请参见[符号支持](../wpt/symbol-support.md)。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[Windows 应用商店应用程序性能评估的结果](results-for-the-windows-store-app-performance-assessment.md)

 

 







