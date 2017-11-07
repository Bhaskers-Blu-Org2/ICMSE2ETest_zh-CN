---
author: Justinha
Description: "Sysprep 支持的服务器角色"
ms.assetid: ed484189-a2a7-423e-b191-202559efa81f
MSHAttr: PreferredLib:/library/windows/hardware
title: "Sysprep 支持的服务器角色"
ms.openlocfilehash: 046db4b422e7e0a39a086772294160d4cefe1fa1
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="sysprep-support-for-server-roles"></a>Sysprep 支持的服务器角色


许多常见服务器角色支持系统准备工具 (Sysprep)。 但是，如果您运行**Sysprep**命令和**一般化 /**选项安装服务器，并且您正在使用不支持的服务器角色，这些角色可能无法正常映像和部署过程完成之后。 因此，您必须启用并配置不支持 Sysprep 映像和部署过程执行后任何服务器角色。

下表列出了服务器角色和指定角色是否支持 Sysprep。

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">服务器角色</th>
<th align="left">Windows Server 2008 中的 Sysprep 支持</th>
<th align="left">Windows Server 2008 R2 中的 Sysprep 支持</th>
<th align="left">在 Windows Server® 2012 Sysprep 支持</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Active Directory 证书服务 (AD CS)</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>否</p></td>
</tr>
<tr class="even">
<td align="left"><p>活动目录域服务 (AD DS)</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>否</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Active Directory 联合身份验证服务 (AD FS）)</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>否</p></td>
</tr>
<tr class="even">
<td align="left"><p>活动目录轻量级目录服务 (AD LDS)</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>否</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Active Directory Rights Management Services (AD RMS)</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>否</p></td>
</tr>
<tr class="even">
<td align="left"><p>应用程序服务器</p></td>
<td align="left"><p>是</p></td>
<td align="left"><p>是</p></td>
<td align="left"><p>是</p></td>
</tr>
<tr class="odd">
<td align="left"><p>动态主机配置协议 (DHCP) 服务器</p></td>
<td align="left"><p>是</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>否</p></td>
</tr>
<tr class="even">
<td align="left"><p>域名系统 (DNS) 服务器</p></td>
<td align="left"><p>不适用</p></td>
<td align="left"><p>不适用</p></td>
<td align="left"><p>不适用</p></td>
</tr>
<tr class="odd">
<td align="left"><p>传真服务器</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>否</p></td>
</tr>
<tr class="even">
<td align="left"><p>文件和存储服务</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>是</p></td>
<td align="left"><p>是</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Hyper-V™</p></td>
<td align="left"><p>不适用</p></td>
<td align="left"><p>是</p>
<p>不支持 Hyper-V™ 上的虚拟网络。 任何虚拟网络在运行 Sysprep 工具之前，必须删除。</p></td>
<td align="left"><p>是</p>
<p>不支持 Hyper-V™ 上的虚拟网络。 任何虚拟网络在运行 Sysprep 工具之前，必须删除。</p></td>
</tr>
<tr class="even">
<td align="left"><p>网络策略和 Access Services (NPAS) ¹</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>否</p></td>
</tr>
<tr class="odd">
<td align="left"><p>网络策略路由和远程 Access Services</p></td>
<td align="left"><p>是</p></td>
<td align="left"><p>不适用</p></td>
<td align="left"><p>不适用</p></td>
</tr>
<tr class="even">
<td align="left"><p>打印和文档服务 （打印服务） ²</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>是</p></td>
<td align="left"><p>是</p></td>
</tr>
<tr class="odd">
<td align="left"><p>远程桌面服务 ³</p></td>
<td align="left"><p>是</p></td>
<td align="left"><p>是</p></td>
<td align="left"><p>是</p></td>
</tr>
<tr class="even">
<td align="left"><p>流式媒体服务 （可通过下载获得）</p></td>
<td align="left"><p>不适用</p></td>
<td align="left"><p>不适用</p></td>
<td align="left"><p>不适用</p></td>
</tr>
<tr class="odd">
<td align="left"><p>UDDI 服务 ⁴</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>不适用</p></td>
<td align="left"><p>不适用</p></td>
</tr>
<tr class="even">
<td align="left"><p>批量激活服务 ⁵</p></td>
<td align="left"><p>不适用</p></td>
<td align="left"><p>不适用</p></td>
<td align="left"><p>不适用</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Web 服务器 (Internet Information Services)</p></td>
<td align="left"><p>是</p>
<p>不支持使用 Applicationhost.config 文件中的加密凭据。</p></td>
<td align="left"><p>是</p>
<p>不支持使用 Applicationhost.config 文件中的加密凭据。</p></td>
<td align="left"><p>是</p>
<p>不支持使用 Applicationhost.config 文件中的加密凭据。</p></td>
</tr>
<tr class="even">
<td align="left"><p>Windows 部署服务</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>是</p>
<p>不支持如果初始化 Windows 部署服务。 ⁶</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Windows 服务器更新服务驱动程序列表</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>否</p></td>
</tr>
</tbody>
</table>

 

⁽¹⁾ NPAS 包括健康注册机构 (HRA)、 网络策略服务器 (NPS) 和主机凭据验证协议 (HCAP)。

⁽²⁾ 在 Windows Server 2008 R2，打印服务时更名为打印和文件服务。

⁽³⁾ 在 Windows Server 2008 R2，终端服务已重命名远程桌面服务，即所谓的远程桌面会话主机。

⁽⁴⁾ UDDI 服务未包括在 Windows Server 2008 R2。

⁽⁵⁾ 卷激活服务是 Windows Server 2012 的新功能。

⁽⁶⁾ 必须先取消在运行 Sysprep 之前安装了 Windows 部署服务角色的服务器。 可以通过使用**wdsutil /uninitialize-server**命令初始化服务器。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Sysprep （系统准备） 概述](sysprep--system-preparation--overview.md)

[Sysprep 过程概述](sysprep-process-overview.md)

[Sysprep 命令行选项](sysprep-command-line-options.md)

[Sysprep （通用化） Windows 安装](sysprep--generalize--a-windows-installation.md)

 

 






