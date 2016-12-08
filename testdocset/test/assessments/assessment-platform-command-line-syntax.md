---
title: "评估平台命令行语法"
description: "评估平台命令行语法"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 34286b79-1867-4d0d-8b65-6a0c6a7e5df8
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 6c74f6ae01ced36cdb45c952ae784f8582a00478
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="assessment-platform-command-line-syntax"></a>评估平台命令行语法


**AXE.exe**是一个与 Windows 评估 Toolkit 安装的命令行工具。 这组命令行选项可用于自动执行脚本中的作业并最小化资源使用状况。 作业是一个或多个评估的计算机上运行一次。 命令行选项不能用于撰写作业。 您应该创建、 修改和通过使用 Windows 评估控制台保存作业。 默认情况下，作业保存到 %USERPROFILE%\\文档\\评估 Windows 控制台\\作业文件夹。

默认情况下，AXE.exe 安装到︰

%PROGRAMFILES%\\窗口工具包\\10\\评估和部署工具包\\Windows 评估 Toolkit\\*&lt;体系结构&gt;*

其中*&lt;体系结构&gt;*是 x86 或 amd64。

## <a name="command-line-options"></a>命令行选项


使用来自命令行的评估平台的基本语法是︰

``` syntax
AXE.exe jobfile [AXE_options]
```

下表提供了有关如何使用每个选项的说明。 这些选项不区分大小写。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>选项</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>帮助</strong>或<strong>/？</strong></p></td>
<td><p>显示可用的<strong>AXE.exe</strong>命令行选项的信息。</p></td>
</tr>
<tr class="even">
<td><p><strong>JobFile</strong></p></td>
<td><p>指定要运行的作业文件。</p>
<p>作业文件的路径可以是相对路径。 如果您运行的从<strong>AXE.exe</strong>目录中作业，没有路径是必需的。 默认情况下，当您在 Windows 评估控制台中，创建作业时保存在 %USERPROFILE%\Documents\Windows 评估 Console\Jobs 文件夹中。</p>
<div class="alert">
<strong>请注意</strong>  
<p>如果未不指定任何其他参数，执行某项操作，则需要此选项。</p>
</div>
<div>
 
</div>
<p>示例：</p>
<pre class="syntax" space="preserve"><code>AXE C:\Assessments\MyJobs\Job1.jobx</code></pre></td>
</tr>
<tr class="odd">
<td><p><strong>/ 超时</strong><em>&lt;秒&gt;</em></p></td>
<td><p>指定的时间，以秒为单位，该作业将等待另一个作业完成，然后退出并显示错误。 默认值为零，这意味着，当作业如果另一个作业已在运行，将立即退出。 这是一个可选参数。</p>
<p>示例：</p>
<pre class="syntax" space="preserve"><code>AXE C:\Assessments\myJobs\Job1.jobx /Timeout 30</code></pre></td>
</tr>
<tr class="even">
<td><p><strong>/ NoPublish</strong></p></td>
<td><p>指定不将结果文件发布到作业文件中指定的位置。 使用此选项时，结果保存到默认位置，%localappdata%\microsoft\axe\results。</p>
<p>示例：</p>
<pre class="syntax" space="preserve"><code>AXE C:\Assessments\myJobs\Job1.jobx /NoPublish</code></pre></td>
</tr>
<tr class="odd">
<td><p><strong>/ PublishPath</strong><em>&lt;目录&gt;</em></p></td>
<td><p>指定要发布到的结果文件的文件夹的路径。 这将覆盖该出版物路径， &lt;ResultsPublishPath&gt;，指定的作业中。 如果结合<strong>/NoPublish</strong>，则忽略此参数。</p>
<p>示例：</p>
<pre class="syntax" space="preserve"><code>AXE C:\Assessments\myJobs\Job1.jobx /PublishPath C:\Assessments\myResults</code></pre></td>
</tr>
<tr class="even">
<td><p><strong>/ RemoveRestart</strong></p></td>
<td><p>指定任何现有挂起作业重新启动任务应该删除的。</p>
<div class="alert">
<strong>请注意</strong>  
<p>使用此选项时，不需要<strong>/JobFile</strong>选项。</p>
</div>
<div>
 
</div>
<p>当您运行一个作业时，评估创建任务系统出现故障，如断电时重新启动作业。 使用此选项时，该任务会从任务计划程序。 如果没有作业重新启动任务被挂起，评估将返回错误信息，通知您该任务不存在。</p>
<p>示例：</p>
<pre class="syntax" space="preserve"><code>AXE /RemoveRestart</code></pre></td>
</tr>
<tr class="odd">
<td><p><strong>/ NoWarnings</strong></p></td>
<td><p>禁止显示警告消息。 这是一个可选参数。</p>
<p>示例：</p>
<pre class="syntax" space="preserve"><code>AXE C:\Assessments\myJobs\Job1.jobx /NoWarnings</code></pre></td>
</tr>
<tr class="even">
<td><p><strong>/ 暂停</strong></p></td>
<td><p>在作业完成后，要等待您按某个键，则暂停 AXE.exe。 然后，您可以看到的任何错误或关闭控制台 AXE.exe 退出之前，可在控制台中的其他信息。</p>
<p>示例：</p>
<pre class="syntax" space="preserve"><code>AXE C:\Assessments\myJobs\Job1.jobx /Pause</code></pre></td>
</tr>
<tr class="odd">
<td><p><strong>/ JobParameter 参数 =</strong><em>&lt;值&gt;</em></p></td>
<td><p>指定要重写的作业清单中可能存在的作业参数值。 这是一个可选参数。 您可以使用它达 100 次可以指定多个作业参数。 如果重复作业参数名称显示，评估使用的最后一个。 <strong>/PublishPath</strong>选项优先于设置&lt;ResultsPublishPath&gt;作业参数，使用此选项。</p>
<p>示例：</p>
<pre class="syntax" space="preserve"><code>AXE C:\Assessments\myJobs\Job1.jobx /JobParameter iterations=1</code></pre></td>
</tr>
<tr class="even">
<td><p><strong>/ DisplayLog</strong><em>&lt;path_to_AXE_ETL_log_file&gt;</em></p></td>
<td><p>显示<strong>AXE.exe</strong>用于日志记录的事件跟踪日志 (ETL) 文件的内容。 您必须指定<strong>AXE.exe</strong> ETL 文件的路径。 作业运行时，日志文件的位置将出现在控制台中。 文件名可能包含通配符字符。</p>
<p>日志文件的默认位置是 %LOCALAPPDATA%\Microsoft\Axe\Logs\<em>&lt;GUID&gt;</em>，其中<em>&lt;GUID&gt;</em>是为每个新作业将随机生成的 GUID。 作业结果文件以&lt;SessionLogFiles&gt;节点还包含完整的位置。 此节点指定的所有日志文件。</p>
<div class="alert">
<strong>请注意</strong>  
<p>所有的 ETL 文件自动转换成结果目录中保存一个 AxeLog.txt 文件。 您可以使用记事本中打开此文件。</p>
</div>
<div>
 
</div>
<p>示例：</p>
<pre class="syntax" space="preserve"><code>AXE /DisplayLog &lt;path_to_file&gt;</code></pre></td>
</tr>
</tbody>
</table>

 

**有以下好处︰**

-   在命令提示符下运行作业占用资源较少，对性能指标的影响较小。

-   命令行选项可用于自动执行一个作业。

-   命令行选项提供 Windows 评估控制台中未提供的附加参数。

**限制︰**

-   预配置的作业中的一个或一个 Windows 评估 Toolkit 提供一个评估不能运行该作业。

-   您不能创建或使用**AXE.exe**修改作业。 您必须使用 Windows 评估控制台。

## <a name="related-topics"></a>相关的主题


[Windows 评估控制台概述](windows-assessment-console-overview.md)

 

 







