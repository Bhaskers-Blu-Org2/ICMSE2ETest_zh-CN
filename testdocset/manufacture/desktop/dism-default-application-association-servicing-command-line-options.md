---
author: Justinha
Description: "DISM 默认应用程序关联服务命令行选项"
ms.assetid: 78cad8f9-2048-48f7-8eb6-44011adbca24
MSHAttr: PreferredLib:/library/windows/hardware
title: "DISM 默认应用程序关联服务命令行选项"
ms.openlocfilehash: bdaa2162794c485ac22e5399a47632484d646c99
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="dism-default-application-association-servicing-command-line-options"></a>DISM 默认应用程序关联服务命令行选项


默认应用程序关联服务命令可用于导入、 导出列表，并删除指定的应用程序打开的文件，根据文件扩展名或协议的设置。

服务使用 DISM 的 Windows 映像的基本语法如下︰

**DISM.exe** {**/图像︰**&lt;*路径\_到\_图像\_目录*&gt; | **/Online**} \[ **dism\_全局\_选项**\] {**服务\_选项**} \[ &lt;*服务\_参数*&gt;\]

下列默认应用程序服务选项可用于脱机映像。

**DISM.exe /image:**&lt;*路径\_到\_图像\_目录*&gt; \[ **/Get-DefaultAppAssociations** | **/Import-DefaultAppAssociations** | **/Remove-DefaultAppAssociations**\]

下列默认应用程序关联服务选项可用于正在运行的操作系统。

**DISM.exe / 在线**\[ **/Export-DefaultAppAssociations** | **/Get-DefaultAppAssociations** | **导入 DefaultAppAssociations** | **删除 DefaultAppAssociations**\]

下表描述了可以如何使用每个默认应用程序关联的服务选项。 这些选项不是区分大小写的。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">选项</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>/ 获取帮助</strong></p>
<p><strong>/?</strong></p></td>
<td align="left"><p>关联的默认应用程序服务命令行选项后紧接着使用，显示的选项和参数的信息。 其他主题可能会在指定了映像之后变为可用。</p>
<p>示例︰</p>
<p><strong>Dism /image:C:\test\offline /Import-DefaultAppAssociations /？</strong></p>
<p><strong>Dism 在线 / /Get-DefaultAppAssociations /？</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ 导出-DefaultAppAssociations:</strong>&lt;<em>path_to_export_file</em>&gt;</p></td>
<td align="left"><p>从正在运行的操作系统的默认应用程序关联导出到一个.xml 文件中。</p>
<p>示例：</p>
<p><strong>Dism.exe / 在线 /Export-DefaultAppAssociations:C:\AppAssoc.xml</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ Get DefaultAppAssociations</strong></p></td>
<td align="left"><p>显示已指定的 Windows 映像中设置的默认应用程序关联的列表。 此选项可用于验证关联的图像已成功导入该默认应用程序。</p>
<p>示例︰</p>
<p><strong>Dism.exe /Image:C:\test\offline /Get-DefaultAppAssociations</strong></p>
<p><strong>Dism.exe / 在线 /Get-DefaultAppAssociations</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ 导入-DefaultAppAssociations:</strong>&lt;<em>path_to_xml_file</em>&gt;</p></td>
<td align="left"><p>默认应用程序关联的一组将导入.xml 文件中指定的 Windows 映像。 在他们第一次登录期间将为每个用户应用的默认应用程序关联。</p>
<p>示例︰</p>
<p><strong>Dism.exe /Image:C:\test\offline /Import-DefaultAppAssociations:C:\AppAssoc.xml</strong></p>
<p><strong>Dism.exe / 在线 /Import-DefaultAppAssociations:C:\AppAssoc.xml</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ 删除 DefaultAppAssociations</strong></p></td>
<td align="left"><p>从指定的 Windows 映像中删除默认的应用程序关联。</p>
<p>示例︰</p>
<p><strong>Dism.exe /Image:C:\test\offline /Remove-DefaultAppAssociations</strong></p>
<p><strong>Dism.exe / 在线 /Remove-DefaultAppAssociations</strong></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[DISM 是什么？](what-is-dism.md)

[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)

[部署映像服务和管理 (DISM) 命令行选项](deployment-image-servicing-and-management--dism--command-line-options.md)

 

 






