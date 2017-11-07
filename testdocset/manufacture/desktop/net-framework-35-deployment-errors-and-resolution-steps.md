---
author: Justinha
Description: ".NET Framework 3.5 部署错误和解决步骤"
ms.assetid: 1320d926-3ff7-4deb-b7b8-17190028dd97
MSHAttr: PreferredLib:/library/windows/hardware
title: ".NET Framework 3.5 部署错误和解决步骤"
ms.openlocfilehash: 57c5bcaa7afbfc249000af5cc8db3df71363ae94
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="net-framework-35-deployment-errors-and-resolution-steps"></a>.NET Framework 3.5 部署错误和解决步骤


本主题介绍使用功能按需启用或部署.NET Framework 3.5 和建议采取的步骤来解决问题时可能遇到的常见错误。

**表 1 功能需求错误代码**

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">错误代码</th>
<th align="left">名称</th>
<th align="left">说明</th>
<th align="left">解决方法步骤</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>0x800F081F</p></td>
<td align="left"><p>CBS_E_SOURCE_MISSING</p></td>
<td align="left"><p>找不到源文件。 使用<strong>源</strong>选项指定的文件恢复功能所需的位置。 有关如何指定源位置的详细信息，请参阅[配置 Windows 修复源](http://go.microsoft.com/fwlink/?LinkId=243077)。</p></td>
<td align="left"><p>验证指定的源所需的文件。 源参数应指向安装介质上 （例如，映像装载到<strong>c:\mount</strong> <strong>c:\mount\windows</strong> ） 已装载的映像的 Windows 文件夹的<strong>\sources\sxs 文件夹</strong>中。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x800F0906</p></td>
<td align="left"><p>CBS_E_DOWNLOAD_FAILURE</p></td>
<td align="left"><p>无法下载源文件。 使用<strong>源</strong>选项指定的文件恢复功能所需的位置。 有关如何指定源位置的详细信息，请参阅[配置 Windows 修复源](http://go.microsoft.com/fwlink/?LinkId=243077)。</p>
<p>Windows 无法连接到互联网才能下载必需的文件。 确保系统已连接至互联网，然后单击<strong>重试</strong>。</p></td>
<td align="left"><p>确认计算机或服务器已连接到 Windows 更新，然后您就可以浏览到<strong>http://update.microsoft.com</strong>。 如果使用 WSUS 管理此计算机的更新时，请验证启用了组策略设置<strong>将 Windows 更新联系人直接来下载修复内容而不是 Windows 服务器更新设备驱动程序列表）</strong> 。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x800F0907</p></td>
<td align="left"><p>CBS_E_GROUPPOLICY_DISALLOWED</p></td>
<td align="left"><p>DISM 失败。 未不执行任何操作。 详细信息，请参阅在<strong>%WINDIR%\logs\DISM\dism.log</strong>日志文件。</p>
<p>由于网络策略设置，Windows 无法连接到互联网下载完成所请求的更改所需的文件。</p></td>
<td align="left"><p>有关<strong>指定可选组件的安装和维修组件的设置</strong>组策略设置的帮助与网络管理员联系。</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Microsoft.NET Framework 3.5 部署注意事项](microsoft-net-framework-35-deployment-considerations.md)

 

 






