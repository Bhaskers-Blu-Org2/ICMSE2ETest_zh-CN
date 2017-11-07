---
author: Justinha
Description: "Sysprep 命令行选项"
ms.assetid: b20ee6ea-b1c4-4cd2-91ea-52f667a704bb
MSHAttr: PreferredLib:/library/windows/hardware
title: "Sysprep 命令行选项"
ms.openlocfilehash: 4c0c7316f8e48e79c26851b07726352d379a5c1c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="sysprep-command-line-options"></a>Sysprep 命令行选项


运行**Sysprep**准备 Windows 安装捕获。 本主题描述系统准备 (Sysprep) 工具的命令行语法。

如果您打算创建的安装程序部署到另一台计算机的映像，必须运行**Sysprep**命令和**一般化**选项，即使另一台计算机具有相同的硬件配置。 **Sysprep 一般化 /**命令将唯一信息删除从您的 Windows 安装，以便可以安全地重复使用另一台计算机上的图像。 下次您启动 Windows 映像，在[specialize](specialize.md)配置阶段运行。

## <a name="span-idsysprepcommand-lineoptionsspanspan-idsysprepcommand-lineoptionsspanspan-idsysprepcommand-lineoptionsspansysprep-command-line-options"></a><span id="Sysprep_Command-Line_Options"></span><span id="sysprep_command-line_options"></span><span id="SYSPREP_COMMAND-LINE_OPTIONS"></span>Sysprep 命令行选项


Sysprep 下面的命令行选项有︰

**Sysprep.exe** \[ **/oobe** | **/审核**\]

\[**一般化 /**\]

\[**/mode:vm**\]

\[**重新启动/** | **/shutdown** | **/ 退出**\]

\[**安静 /**\]

\[**无人参与 /:***&lt;应答文件&gt;*\]

下表列出了 Sysprep 命令行选项︰

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
<td align="left"><p><strong>模式</strong></p></td>
<td align="left"><p>将计算机重新启动到审核模式。 审核模式使您可以添加其他驱动程序或 Windows 的应用程序。 在发送给最终用户的安装之前，您也可以测试 Windows 安装。 例如︰</p>
<pre class="syntax" space="preserve"><code>Sysprep /audit</code></pre>
<p>如果您指定答案文件，Windows 安装程序审核模式下运行[auditSystem](auditsystem.md)和[auditUser](audituser.md)配置阶段。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>一般化 /</strong></p></td>
<td align="left"><p>准备要进行映像的 Windows 安装。 Sysprep 删除 Windows 安装的所有唯一的系统信息。 Sysprep 重置安全 ID (SID)、 清除任何的系统还原点和删除事件日志。 例如︰</p>
<pre class="syntax" space="preserve"><code>Sysprep /generalize /shutdown</code></pre>
<p>下次计算机启动时，将运行在[specialize](specialize.md)配置阶段。 配置阶段创建新的安全标识符 (SID)。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/oobe</strong></p></td>
<td align="left"><p>OOBE 模式重新启动计算机。 例如︰</p>
<pre class="syntax" space="preserve"><code>Sysprep /generalize /shutdown /oobe</code></pre>
<p>OOBE 使最终用户能够自定义 Windows 操作系统、 创建用户帐户、 命名计算机，并执行其他任务。 Sysprep 进程 OOBE 开始之前[oobeSystem](oobesystem.md)配置中的任何设置将传递答案文件中。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/mode:vm</strong></p></td>
<td align="left"><p>这样，您可以为同一虚拟机 (VM) 或虚拟机监控程序 VHD 部署 VHD，泛化虚拟硬盘 (VHD)。 虚拟机重新启动之后，虚拟机可以引导到 OOBE。 例如︰</p>
<pre class="syntax" space="preserve"><code>Sysprep /generalize /oobe /mode:vm</code></pre>
<p>应用于虚拟机模式下的唯一额外开关<strong>是/重引导</strong>、 <strong>/shutdown</strong>，和<strong>/ 退出</strong>。您必须部署 VHD 上虚拟机 (VM) 或虚拟机管理程序使用相同的硬件配置文件。 例如，如果创建 Microsoft Hyper-V VHD，您可以仅部署您的 VHD 到 Microsoft Hyper-V 虚拟机与相应的硬件配置文件。 将 VHD 部署到不同的虚拟机与不同的硬件配置文件可能会导致意外的问题。</p>
<div class="alert">
<strong>重要</strong>  
<p>您只能运行在虚拟机内部的虚拟机模式从。</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/reboot</strong></p></td>
<td align="left"><p>重新启动计算机。 若要审核计算机，并验证首次运行经验运行正常，您可以使用此选项。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/shutdown</strong></p></td>
<td align="left"><p><strong>Sysprep</strong>命令完成运行后关闭计算机。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>安静 /</strong></p></td>
<td align="left"><p>运行 Sysprep 工具而不是屏幕上显示确认消息。 如果您自动执行 Sysprep 工具，您可以使用此选项。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ 退出</strong></p></td>
<td align="left"><p>而无需重新启动或关闭计算机，Sysprep 运行指定的命令后关闭 Sysprep 工具。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>无人参与 /:</strong><em>&lt;应答文件&gt;</em></p></td>
<td align="left"><p>在无人参与安装过程中将答案文件中的设置应用于 Windows 在<em>&lt;应答文件&gt;</em>指定要使用的答案文件的路径和文件名称。 例如︰</p>
<pre class="syntax" space="preserve"><code>Sysprep /audit /reboot /unattend:F:\Unattend.xml</code></pre>
<p>其中<em>F</em>是便携式存储设备 (Unattend.xml) 的应答文件所在的驱动器号。</p></td>
</tr>
</tbody>
</table>

 

**重要**  
您必须使用**Sysprep 一般化 /**命令进行归纳完整的 Windows 安装，可用于部署到一台新计算机，在安装之前是否使用成像、 硬盘复制或另一种方法。 移动或复制到另一台计算机而不运行的 Windows 映像**Sysprep 一般化 /**命令不受支持。

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Sysprep （系统准备） 概述](sysprep--system-preparation--overview.md)

[Sysprep 过程概述](sysprep-process-overview.md)

[Sysprep （通用化） Windows 安装](sysprep--generalize--a-windows-installation.md)

[Sysprep 支持的服务器角色](sysprep-support-for-server-roles.md)

[使用答案文件与 Sysprep 一起](use-answer-files-with-sysprep.md)

 

 






