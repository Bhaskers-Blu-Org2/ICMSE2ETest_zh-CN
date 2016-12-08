---
author: Justinha
Description: "REAgentC 命令行选项"
ms.assetid: da498872-1c26-4cb8-a5da-80a0d45200f3
MSHAttr: PreferredLib:/library/windows/hardware
title: "REAgentC 命令行选项"
ms.openlocfilehash: 82b55bbe9b8b98380d2a5a563c25545322bf1e67
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="reagentc-command-line-options"></a>REAgentC 命令行选项


您可以使用 REAgentC.exe 工具来配置 Windows 恢复环境 (Windows RE) 引导图像和按钮重置的恢复图像，并管理恢复选项和自定义项。 在脱机 Windows 映像或运行的 Windows 操作系统上，您可以运行**REAgentC**命令。

**请注意**  
如果您使用 Windows PE 2.X，3.X 或 4.x 版脱机 Windows 10 安装上配置故障恢复，必须从恢复的 Windows 评估和部署工具包 (Windows ADK) 文件夹中使用的 Winrecfg.exe 文件。 Winrecfg.exe 支持仅 REAgentC.exe 支持离线操作。

 

## <a name="span-idreagentccommandsspanspan-idreagentccommandsspanspan-idreagentccommandsspanreagentc-commands"></a><span id="REAgentC_Commands"></span><span id="reagentc_commands"></span><span id="REAGENTC_COMMANDS"></span>REAgentC 命令


下面的命令行选项是可用的 Windows RE:

**reagentc.exe** &lt;命令&gt;&lt;参数&gt;

下表描述了这些命令行选项︰

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">选项</th>
<th align="left">在线/离线</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>/setreimage/路径</strong> <em>&lt;path_to_Windows_RE_image&gt; </em> [<strong>/target</strong> <em>&lt;path_to_offline_image&gt;</em>]</p>
<p></p></td>
<td align="left"><p> 全部影响</p></td>
<td align="left"><p>设置 Windows RE 引导映像的位置。 在 Windows 10、 Windows 8.1、 Windows 8、 Windows 服务器 2016年技术预览、 Windows Server 2012 R2 和 Windows Server 2012 <strong>，/路径</strong>支持的本地磁盘上位置的 UNC 路径。 例如︰</p>
<pre class="syntax" space="preserve"><code>Reagentc /setreimage /path S:\Recovery\WindowsRE</code></pre>
<p><strong>/Target</strong>选项用于指定 Windows 映像的位置，当您应用该设置脱机。 例如︰</p>
<pre class="syntax" space="preserve"><code>Reagentc /setreimage /path T:\Recovery\WindowsRE /target W:\Windows</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p><strong>启用/</strong> [<strong>/auditmode</strong>] [<strong>/osguid</strong> &lt;bcd_guid&gt;]</p></td>
<td align="left"><p>联机</p></td>
<td align="left"><p>使自定义的 Windows RE 引导映像。</p>
<p><strong>启用</strong>选项将自动运行在专业化配置阶段。 如果不指定 Windows RE 引导图像，计算机会尝试启用 Windows RE \Windows\System32\Recovery 文件夹中使用默认的 Winre.wim 文件。</p>
<ul>
<li><p><strong>/auditmode</strong>:</p>
<p>默认情况下，<strong>启用</strong>选项不执行任何操作，当 Windows 在审核模式下。 若要重写默认行为，并在审核模式下启用 Windows RE，指定<strong>/auditmode</strong>选项。 例如︰</p>
<pre class="syntax" space="preserve"><code>Reagentc /enable /auditmode</code></pre>
<p>如果您一般化映像，在审核模式下<strong>使用/启用</strong>选项后，您使用<strong>启用</strong>选项再次或直至专业化配置阶段运行后之前，将禁用 Windows RE。</p></li>
<li><p><strong>/osguid</strong> &lt;bcd_guid&gt;:</p>
<p>此选项允许您启用 Windows PE 的自定义 Windows RE 引导映像。 它只能在运行 bcdboot.exe 之后。 &lt;bcd_guid&gt;是通过运行目标 Windows 安装引导配置数据 (BCD) 标识符<code>bcdedit -enum -v</code>。</p>
<pre class="syntax" space="preserve"><code>Reagentc /enable /osguid {00000000-0000-0000-0000-000000000000}</code></pre></li>
</ul></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/disable</strong></p></td>
<td align="left"><p>联机</p></td>
<td align="left"><p>禁用任何活动的 Windows RE 图像映射到联机映像。 例如︰</p>
<pre class="syntax" space="preserve"><code>Reagentc /disable</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/boottore</strong></p></td>
<td align="left"><p>联机</p></td>
<td align="left"><p>指定 Windows RE 自动启动下一次系统启动。 例如︰</p>
<pre class="syntax" space="preserve"><code>Reagentc /boottore</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/setosimage/路径</strong> <em>&lt;path_to_recovery_image&gt;</em> <strong>/index</strong> <em>&lt;image_index&gt; </em> [<strong>/target</strong> <em>&lt;path_to_offline_image&gt;</em>]</p></td>
<td align="left"><p> 全部影响</p></td>
<td align="left"><p>在 Windows 10 中不使用此设置。</p>
<p>注册联机或脱机映像中的点击式重新设置图像的位置。 恢复映像必须是 Windows 映像 (.wim) 格式。</p>
<p><strong>/Index</strong>选项指定要从使用.wim 文件中的恢复图像的索引号。 例如︰</p>
<pre class="syntax" space="preserve"><code>Reagentc /setosimage /path R:\RecoveryImage /index 1</code></pre>
<p><strong>/Target</strong>选项用于指定脱机 Windows 映像的位置。 例如︰</p>
<pre class="syntax" space="preserve"><code>Reagentc /setosimage /path R:\RecoveryImage /index 1 /target W:\Windows</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/info</strong> [<strong>/target</strong> <em>&lt;path_to_offline_image&gt;</em>]</p></td>
<td align="left"><p> 全部影响</p></td>
<td align="left"><p>在线或离线图像上显示 Windows RE 和任何可用的恢复映像的当前状态。 例如，以下命令返回联机系统的状态︰</p>
<pre class="syntax" space="preserve"><code>Reagentc /info</code></pre>
<p><strong>/Target</strong>选项用于获取有关脱机映像配置信息。 例如︰</p>
<pre class="syntax" space="preserve"><code>Reagentc /info /target W:\Windows</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/setbootshelllink</strong> [<strong>/configfile</strong> <em>&lt;path_to_BootShellXML&gt;</em>] [<strong>/target</strong> <em>&lt;path_to_offline_image&gt;</em>]</p></td>
<td align="left"><p> 全部影响</p></td>
<td align="left"><p>注册 Windows 启动选项菜单中显示的自定义工具的链接。 例如︰</p>
<pre class="syntax" space="preserve"><code>Reagentc /setbootshelllink /configfile F:\BootMenu\AddDiagnosticsToolToBootMenu.xml</code></pre>
<p>BootShellXML 是 an.xml 文件，其中包含<em>&lt;BootShell&gt;</em>元素和<em>&lt;名称&gt;</em>和<em>&lt;说明&gt;</em>想要在链接中显示的属性。 有关详细信息，请参阅[自定义 Windows RE](customize-windows-re.md)。</p>
<p><strong>/Target</strong>选项用于指定脱机 Windows 映像的位置。 如果不使用此参数，则使用运行状态的操作系统。 例如︰</p>
<pre class="syntax" space="preserve"><code>Reagentc /setbootshelllink /target W:\Windows</code></pre></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Windows RE 疑难解答功能](windows-re-troubleshooting-features.md)

 

 






