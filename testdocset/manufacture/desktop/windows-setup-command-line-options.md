---
author: Justinha
Description: "Windows 安装程序命令行选项"
ms.assetid: 16001d04-db9f-4953-abc7-37903ef47fd1
MSHAttr: PreferredLib:/library/windows/hardware
title: "Windows 安装程序命令行选项"
ms.openlocfilehash: 0b4528a27c96d51db770c0798488e27639269174
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-setup-command-line-options"></a>Windows 安装程序命令行选项


下面的命令行选项是可用的 Windows 安装程序。 开头第 10 Windows 版本 1607，可以作为参数传递给 Windows 安装程序命令行的替代方法使用 setupconfig 文件。 有关详细信息，请参阅[Windows 安装程序自动化概述](windows-setup-automation-overview.md)。

**setup.exe** \[ **/1394debug:***&lt;通道&gt;* \[**波特率︰***&lt;baudrate&gt; *\]\]

\[**/addbootmgrlast**\]

\[**/Auto**{**清洁** | **DataOnly** | **升级**}\]

\[**/busparams:***&lt;bus.device.function&gt;*\]

\[**/CompactOS**{**启用** | **禁用**}\]

\[**/Compat**{**IgnoreWarning** | **ScanOnly**}\]

\[**/ 拷贝***&lt;位置&gt;*\]

\[**调试︰***&lt;通道&gt;* \[**波特率︰***&lt;baudrate&gt; *\]\]

\[**/DynamicUpdate**{**启用** | **禁用**}\]

\[**/emsport:**{**COM1** | **COM2** | **usebiossettings** | **关闭**}\[ **/emsbaudrate:***&lt;baudrate&gt; *\]\]

\[**/ InstallDrivers***&lt;位置&gt;*\]

\[**/installfrom***&lt;路径&gt;*\]

\[**/ InstallLangPacks***&lt;位置&gt;*\]

\[**m:***&lt;文件夹\_名称&gt;*\] \[ **/noreboot**\] 

\[**/MigrateDrivers**{**all** | **none**}\]

\[**/netdebug:**hostip =&lt;*w.x.y.z*&gt;，端口 =&lt;*n*&gt;、 密钥 =&lt;*q.r.s.t*&gt;\[，nodhcp\]\[，busparams =*n.o.p*\]\]

\[**/ NoReboot**\]

\[**/PKey***&lt;产品密钥&gt;*\]

\[**/ PostOOBE***&lt;位置&gt;*\[**\\setupcomplete.exe**\]\]

\[**/ PostRollback***&lt;位置&gt;*\[**\\setuprollback.exe**\]\]

\[**安静 /**\]

\[**/ ReflectDrivers***&lt;位置&gt;*\]

\[**/ResizeRecoveryPartition**{**启用** | **禁用**}\]

\[**/ShowOOBE**{**完整** | **无**}\]

\[**/Telemetry**{**启用** | **禁用**}\]

\[**/ 安装程序的 TempDrive:***&lt;驱动器盘符&gt;*\]

\[**无人参与 /:***&lt;答案\_文件&gt;*\]

\[**/ 卸载**{**启用** | **禁用**}\]

\[**/usbdebug:***&lt;主机名&gt;*\]

\[**/wdsdiscover**\]

\[**/wdsserver:***&lt;服务器名&gt;*\]

## <a name="span-idsetupcommand-lineoptionsspanspan-idsetupcommand-lineoptionsspanspan-idsetupcommand-lineoptionsspansetup-command-line-options"></a><span id="Setup_Command-Line_Options"></span><span id="setup_command-line_options"></span><span id="SETUP_COMMAND-LINE_OPTIONS"></span>安装程序命令行选项


下表列出了安装程序命令行选项︰

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><strong>选项</strong></th>
<th align="left"><strong>说明</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>/1394Debug:</strong><em>&lt;通道&gt;</em> [<strong>波特率︰</strong><em>&lt;baudrate&gt;</em>]</p></td>
<td align="left"><p>启用内核调试通过 IEEE 1394 (FireWire) 端口在 Windows 运行时和在[windowsPE](windowspe.md)配置阶段的 Windows 安装程序。</p>
<p><em>&lt;通道&gt;</em>指定调试通道。 默认值为<em>&lt;通道&gt;</em>为<strong>1</strong>。</p>
<p>[<strong>波特率︰</strong><em>&lt;baudrate&gt;</em>] 指定 Windows 在调试过程中传输数据时要使用的波特率。 默认设置为<strong>19200</strong>。 您还可以设置<em>&lt;baudrate&gt;</em>设置为<strong>57600</strong>或<strong>115200</strong>。 例如︰</p>
<pre class="syntax" space="preserve"><code>Setup /1394debug:1 /baudrate:115200</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ AddBootMgrLast</strong></p></td>
<td align="left"><p>指示 Windows 安装程序将 Windows 启动管理器添加 UEFI 固件启动顺序中的最后一项。 此选项只是支持 UEFI pc 运行 Windows PE 4.0 或更高版本。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ 自动</strong>{<strong>清洁</strong> | <strong>DataOnly</strong> | <strong>升级</strong>}</p></td>
<td align="left"><p>执行自动的升级到 Windows 10 或 Windows 8.1 批量许可版本只。</p>
<p>使用 /auto 时，则不能使用无人参与文件。</p>
<p>使用 /auto 时，Windows 安装程序将使用 ei.cfg，在开始安装之前检查兼容性问题。 Ei.cfg 格式不正确，如果安装程序将自动退出，记录退出代码。</p>
<p><strong>全新</strong>︰ 执行 Windows 的全新安装。</p>
<p><strong>DataOnly</strong>︰ 执行升级的 Windows 中，只有 （将数据和保存不是应用程序。）如果只包含数据的安装选项不可用，因为兼容性检查，Windows 安装程序将自动退出，并记录退出代码。</p>
<p><strong>升级</strong>︰ 执行保存应用程序和数据的 Windows 升级。 如果升级安装选项不可用，或者用户需要解决应用程序兼容性问题，Windows 安装程序将自动退出和记录退出代码。</p>
<p><strong>Setup.exe 退出代码︰</strong></p>
<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">退出代码名称</th>
<th align="left">退出代码</th>
<th align="left">原因</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>CONX_SETUP_EXITCODE_CONTINUE_REBOOT</p></td>
<td align="left"><p>0x3</p></td>
<td align="left"><p>此升级已成功完成。</p></td>
</tr>
<tr class="even">
<td align="left"><p>CONX_SETUP_EXITCODE_RESUME_AT_COMPAT_REPORT</p></td>
<td align="left"><p>0x5</p></td>
<td align="left"><p>兼容性检查检测到在继续升级之前需要解决的问题。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>CONX_SETUP_EXITCODE_AUTO_INSTALL_FAIL</p></td>
<td align="left"><p>0x7</p></td>
<td align="left"><p>（升级或仅对数据） 的安装选项不可用。</p></td>
</tr>
</tbody>
</table>
<p> </p>
<strong>清除</strong>
<p><strong>/noautoexit</strong>︰ 未在 Windows 10 中使用。 在 Windows 8.1，如果发现错误，Windows 安装程序没有退出，但改为停止并保持在安装程序屏幕上，直到用户解决问题。 从那一刻开始安装被就读。</p>
<p><strong>/performDU</strong>︰ 未在 Windows 10 中使用。 在 Windows 8.1 Windows 安装程序将检查动态更新为 Windows 安装程序。</p>
<p><strong>示例︰</strong></p>
<pre class="syntax" space="preserve"><code>Setup /auto clean 
Setup /auto dataonly 
Setup /auto upgrade</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ BusParams:</strong><em>&lt;bus.device.function&gt;</em></p></td>
<td align="left"><p>指定 PCI 地址 1394年、 USB、 还是网络调试端口。 总线、 设备和函数的数字必须是十进制格式。 示例：</p>
<pre class="syntax" space="preserve"><code>Setup /busparams:0.29.7 </code></pre>
<p>有关更多信息，请参阅[设置内核调试使用 USB 2.0](http://go.microsoft.com/fwlink/?LinkId=317360)。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ CompactOS</strong> {<strong>启用</strong> | <strong>禁用</strong>}</p></td>
<td align="left"><p>指定是否使用精简的操作系统功能来节省硬盘空间。 默认情况下，Windows 安装程序确定是否自动使用此功能。</p>
<p><strong>启用</strong>︰ 安装程序将安装 Windows 使用压缩的系统文件。</p>
<p><strong>禁用</strong>︰ 安装程序将安装 Windows 使用未压缩的系统文件</p>
<p>若要了解有关精简的操作系统的详细信息，请参阅[袖珍 OS，单实例存储和图像优化](compact-os.md)。</p>
<pre class="syntax" space="preserve"><code>Setup /compactos enable</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ 兼容</strong>{<strong>IgnoreWarning</strong> | <strong>ScanOnly</strong>}</p></td>
<td align="left"><p><strong>IgnoreWarning</strong>︰ 安装程序将完成安装，忽略任何防碍兼容性消息</p>
<p><strong>ScanOnly</strong>: Windows 安装程序兼容性扫描，通过运行和退出代码指示是否存在任何兼容性问题与相似 （没有完成安装）。 安装程序将返回 0xC1900210，如果不发现任何问题。 如果发现兼容性问题，安装程序会返回 0xC1900208。</p>
<p>示例：</p>
<pre class="syntax" space="preserve"><code>Setup /compat /IgnoreWarning</code></pre>
<p>如果您启动安装程序<code>/Compat ScanOnly</code>:</p>
<ul>
<li>如果找不到任何兼容的问题，它将返回 MOSETUP_E_COMPAT_SCANONLY (0xC1900210)</li>
<li>如果它找到了可操作的兼容问题，如应用程序，它将返回 MOSETUP_E_COMPAT_INSTALLREQ_BLOCK (0xC1900208)</li>
<li>如果它找到 Mig-选择不可用，它将返回 MOSETUP_E_COMPAT_MIGCHOICE_BLOCK (0xC1900204)</li>
<li>如果找到该计算机没有资格享受 Windows 10，它将返回 MOSETUP_E_COMPAT_SYSREQ_BLOCK (0xC1900200)</li>
<li>如果找到该计算机没有足够的可用空间来安装，它将返回 MOSETUP_E_INSTALLDISKSPACE_BLOCK (0xC190020E)</li>
</ul>
<p>此命令使用其他开关工作正常。 例如，若要在没有任何 UI，后台运行安装程序︰</p>
<pre class="syntax" space="preserve"><code>Setup /Auto Upgrade /Quiet /Compat ScanOnly</code></pre>
<p>若要忽略用户界面中的常见免责声明，例如，语言更改︰</p>
<pre class="syntax" space="preserve"><code>Setup /Auto Upgrade /Quiet /Compat ScanOnly /Compat IgnoreWarning</code></pre>
<p>大多数情况下，管理员可能想看兼容 XML，如果安装程序找到兼容的问题。 该管理员甚至可以使用复制日志标志收集安装程序日志︰</p>
<pre class="syntax" space="preserve"><code>Setup /Auto Upgrade /Quiet /Compat ScanOnly /Compat IgnoreWarning /CopyLogs &lt;folder_path&gt; </code></pre>
<p>此设置是 Windows 10 的新增功能。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ 拷贝</strong><em>&lt;位置&gt;</em></p></td>
<td align="left"><p>安装程序将复制或上载到指定的位置 （假定计算机/用户到位置具有权限和网络的访问） 失败时的 logs(compressed)。</p>
<p>已接受的参数都是本地文件路径和 UNC 网络路径。</p>
<div class="alert">
<strong>请注意</strong> 将运行中的系统上下文中，因此它可能不具有权限复制到需要用户权限的位置。
</div>
<div>
 
</div>
<p>示例：</p>
<pre class="syntax" space="preserve"><code>Setup /copylogs \\server\share\ </code></pre>
<p>此设置是 Windows 10 的新增功能。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ 调试︰</strong><em>&lt;端口&gt;</em> [<strong>波特率︰</strong><em>&lt;baudrate&gt;</em>]</p></td>
<td align="left"><p>启用内核调试通过通讯 (COM) 端口，当 Windows 正在运行，并且在[windowsPE](windowspe.md)配置阶段的 Windows 安装程序。</p>
<p><em>&lt;端口&gt;</em>指定的调试端口。 默认值为<em>&lt;端口&gt;</em>为<strong>1</strong>。</p>
<p>[<strong>波特率︰</strong><em>&lt;baudrate&gt; </em>指定 Windows 在调试过程中传输数据时要使用的波特率。 默认设置为<strong>19200</strong>。 您还可以设置<em>&lt;baudrate&gt;</em>设置为<strong>57600</strong>或<strong>115200</strong>。 例如︰</p>
<pre class="syntax" space="preserve"><code>Setup /1394debug:1 /baudrate:115200</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ DynamicUpdate</strong> {<strong>启用</strong> | <strong>禁用</strong>}</p></td>
<td align="left"><p>指定是否安装程序将执行动态更新操作 （搜索、 下载和安装更新）。 示例：</p>
<pre class="syntax" space="preserve"><code>setup /auto upgrade /DynamicUpdate disable </code></pre>
<p>此设置是 Windows 10 的新增功能。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ EMSPort:</strong> {<strong>COM1</strong> | <strong>COM2</strong> | |<strong>关闭</strong>}[<strong>/emsbaudrate:</strong><em>&lt;baudrate&gt;</em>]</p></td>
<td align="left"><p>启用或禁用 Windows 安装过程中以及服务器操作系统已经安装后的紧急管理服务 (EMS)。 以下参数用于在 Windows 安装过程中指定的 EMS 的行为。</p>
<p><strong>COM1</strong> COM1 上实现 EMS。 支持 x86 系统只。</p>
<p><strong>COM2</strong>上的 COM2 实现 EMS。 支持 x86 系统只。</p>
<p><strong>usebiossettings</strong>使用 BIOS 指定的设置。 对于 x86 系统中，Windows 使用串行端口控制台重定向 (SPCR) 表中的值。 如果在 BIOS 中指定的任何 SPCR 表或 EFI 控制台设备路径，则 Windows 将禁用<strong>usebiossettings</strong>。<strong>usebiossettings</strong></p>
<p><strong>关闭</strong>禁用 EMS。 如果在 Windows 安装程序中禁用了 EMS，您稍后可以通过修改启动设置启用 EMS。</p>
<p></p>
<p>[<strong>/emsbaudrate:</strong><em>&lt;baudrate&gt;</em>] 指定 Windows 在调试过程中传输数据时要使用的波特率。 默认值为<strong>19200</strong>。 您还可以设置<em>&lt;波特率&gt;</em>设置还可以设置为<strong>57600</strong>或<strong>115200</strong>。 例如︰</p>
<pre class="syntax" space="preserve"><code>Setup /emsport:COM1 /emsbaudrate:115200</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ InstallDrivers</strong><em>&lt;位置&gt;</em></p></td>
<td align="left"><p>将驱动程序.inf 样式添加到新的 Windows 10 安装。 驱动程序.inf 可以在指定的位置中的文件夹中。 该命令将递归通过指定的位置。 示例：</p>
<p>已接受的参数都是本地文件路径或 UNC 网络包含.inf 文件的文件夹路径。</p>
<pre class="syntax" space="preserve"><code>setup.exe /auto upgrade /installdrivers C:\Fabrikam\drivers /noreboot </code></pre>
<p>此设置是 Windows 10 的新增功能。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ InstallFrom</strong> <em>&lt;路径&gt;</em></p></td>
<td align="left"><p>指定要 Windows 安装过程中使用不同的 Install.wim 文件。 这使您可以使用一个预安装环境来安装多个版本的 Windows 映像。 例如，可以使用 32 位版本的 Windows 安装程序来部署 64 位的 Windows 图像。 此外可以跨平台部署中使用答案文件。 有关详细信息，请参阅"创建 WIM 的多种体系结构类型" [Windows 安装程序支持的平台和跨平台部署](windows-setup-supported-platforms-and-cross-platform-deployments.md)中。</p>
<p><em>&lt;路径&gt;</em>指定要安装的.wim 文件的路径。 例如︰</p>
<pre class="syntax" space="preserve"><code>Setup /installfrom D:\custom.wim</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ InstallLangPacks</strong><em>&lt;位置&gt;</em></p></td>
<td align="left"><p>添加到新的 Windows 10 安装语言包 (lp.cab)。</p>
<p>语言包可在指定的位置中的文件夹中。 命令安装文件夹中的指定位置的子文件夹中所有的 lp.cab 文件和文本转换为语音的识别，例如语言能力。</p>
<p>已接受的参数都是本地文件路径或 UNC 网络包含.inf 文件的文件夹路径。</p>
<pre class="syntax" space="preserve"><code>setup /auto upgrade /installlangpacks C:\Fabrikam\Languages\French /noreboot</code></pre>
<p>此设置是 Windows 10 的新增功能。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>m:</strong><em>&lt;文件夹名&gt;</em></p></td>
<td align="left"><p>指示安装程序从备用位置复制替换文件。 此选项指示安装程序首先查找备用位置，并且如果文件存在，可使用这些文件而非默认位置的文件。</p>
<p><em>&lt;文件夹名&gt;</em>指定的名称和文件夹包含替换文件，并且可以是任何本地驱动器位置的位置。 不支持 UNC 路径。</p>
<p>您必须知道文件的 Windows 系统上的安装位置。 必须将所有附加的文件复制到安装源或在 $OEM$ 文件夹<em>&lt;文件夹名&gt;</em>。 $OEM$ 结构提供的目标安装磁盘的表示。 例如︰</p>
<pre class="syntax" space="preserve"><code>$OEM$\$1</code></pre>
<p>映射到 %系统驱动器 %，这可能是驱动器 c。</p>
<pre class="syntax" space="preserve"><code>$OEM$\$$</code></pre>
<p>映射到 %WINDIR%，可能是 C:\windows\。</p>
<pre class="syntax" space="preserve"><code>$OEM$\$progs</code></pre>
<p>映射到程序文件目录。</p>
<pre class="syntax" space="preserve"><code>$OEM$\$docs</code></pre>
<p>映射到用户的我的文档文件夹。</p>
<p>例如，将已更新的 C:\Program Files\Messenger\Msmsgs.exe 文件复制到 Windows 安装，创建以下文件夹结构上 Pro\Sources\$OEM$\$Progs\Messenger\Msmsgs.exe 安装源，通过使用<strong>安装程序</strong>命令︰</p>
<pre class="syntax" space="preserve"><code>Pro\sources\setup.exe /m</code></pre>
<p>如果您替换文件，Windows 文件保护保护，还必须将更新后的文件复制到本地源与 Windows 一起安装。 例如，可以将文件复制到 C:\Windows\i386 文件夹。 文件名必须是在 Windows 安装程序中使用的名称相同。 例如，将下面的文件和文件夹结构添加到 $OEM$ 目录︰</p>
<pre class="syntax" space="preserve"><code>Pro\sources\$OEM$\$$\i386\msmsgs.ex_</code></pre>
<p>如果使用未在安装共享文件，则必须指定文件夹名称。 在此示例中<em>&lt;文件夹名&gt;</em>是 C:\additional_files:</p>
<pre class="syntax" space="preserve"><code>Setup /m:C:\additional_files</code></pre>
<p>其中，C:\additional_files 是您自定义的 $OEM$ 目录。 例如︰</p>
<pre class="syntax" space="preserve"><code>C:\additional_files\$$\i386\msmsgs.ex_</code></pre>
<p>如果要更改在替换文件中的资源，您必须更新的多语言用户界面 (MUI) 文件添加到安装中。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ MigrateDrivers</strong> {<strong>所有</strong> | <strong>无</strong>}</p></td>
<td align="left"><p>指示安装程序是否从现有安装升级过程中迁移的驱动程序。 您可以指定<strong>全部</strong>或<strong>无</strong>。 默认情况下，安装程序将决定最好为每个单独的驱动程序，根据安装选择。</p>
<p>使用<strong>/installdrivers</strong>，可以使用此开关，尽管它并不是必需。</p>
<pre class="syntax" space="preserve"><code>Setup /auto upgrade /migratedrivers all 
Setup /auto upgrade /migratedrivers none /installdrivers N:\NewDrivers</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ NetDebug:</strong>hostip =&lt;<em>w.x.y.z</em>&gt;，端口 =&lt;<em>n</em>&gt;、 密钥 =&lt;<em>q.r.s.t</em>&gt;[，nodhcp] [，busparams =<em>n.o.p</em>]</p></td>
<td align="left"><p>启用内核调试通过网络。</p>
<p>使用 hostip 来识别主机的 IP 地址。</p>
<p>使用端口标识的端口。 默认的起始端口 49152，并且默认结束端口为 65535。 </p>
<p>使用键提供密码以建立安全连接。</p>
<p>要避免使用 DHCP 连接，请使用 nodhcp。 （可选）</p>
<p>使用 busparams 可以选择总线编号、 设备编号和特定的 PCI 总线设备的适配器的函数数目。 （可选）</p>
<p>示例︰</p>
<pre class="syntax" space="preserve"><code>setup /netdebug:hostip=10.125.4.86,port=50000,key=0.0.0.0 
setup /netdebug:hostip=10.125.4.86,port=50000,key=abcdefg.123.hijklmnop.456,nodhcp 
setup /netdebug:hostip=10.125.4.86,port=50000,key=dont.use.previous.keys,busparams=1.5.0</code></pre>
<p>有关详细信息，请参阅[设置内核模式调试通过网络电缆手动](http://go.microsoft.com/fwlink/p/?linkid=317384)。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ NoReboot</strong></p></td>
<td align="left"><p>指示 Windows 安装程序无法重新启动计算机，Windows 安装程序的低级阶段完成后。 <strong>/Noreboot</strong>选项使您能够在 Windows 重新启动之前执行其他命令。 此选项取消仅在第一个的重新启动。 该选项不会取消重新启动。 例如︰</p>
<pre class="syntax" space="preserve"><code>Setup /noreboot</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ 主键</strong> <em>&lt;产品密钥&gt;</em></p></td>
<td align="left"><p>提供特定的产品密钥与安装程序。 示例：</p>
<pre class="syntax" space="preserve"><code>setup.exe /auto upgrade /pkey xxxxx-xxxxx-xxxxx-xxxxx-xxxxx </code></pre>
<p>此设置是 Windows 10 的新增功能。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ PostOOBE</strong><em>&lt;位置&gt;</em>[<strong>\setupcomplete.exe</strong>]</p></td>
<td align="left"><p>完成安装后，运行的脚本。</p>
<p>已接受的参数都是本地文件路径或 UNC 网络路径到名为 setupcomplete.cmd 的文件或文件夹，其中包含 setupcomplete.cmd。</p>
<pre class="syntax" space="preserve"><code>setup.exe /auto upgrade /postoobe c:\Fabrikam\setupcomplete.cmd</code></pre>
<p>到包含名为的脚本的文件夹的路径︰ <strong>setupcomplete.cmd</strong>︰ 将整个文件夹的内容复制到 $Windows。 ~ BT OOBE 之后运行。</p>
<pre class="syntax" space="preserve"><code>setup.exe /auto upgrade /postoobe c:\Fabrikam\</code></pre>
<p>此设置是 Windows 10 的新增功能。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ PostRollback</strong><em>&lt;位置&gt;</em>[<strong>\setuprollback.exe</strong>]</p></td>
<td align="left"><p>如果用户回滚其版本的 Windows，请运行一个脚本。</p>
<p>已接受的参数都是本地文件路径或 UNC 网络路径到名为 setuprollback.cmd 的文件或文件夹，其中包含 setuprollback.cmd。</p>
<pre class="syntax" space="preserve"><code>setup.exe /auto upgrade /postrollback c:\Fabrikam\setuprollback.cmd</code></pre>
<p>到包含名为的脚本的文件夹的路径︰ <strong>setuprollback.cmd</strong>︰ 将整个文件夹的内容复制到 $Windows。 ~ BT OOBE 之后运行。</p>
<pre class="syntax" space="preserve"><code>setup.exe /auto upgrade /postrollback \\server\share</code></pre>
<p>此设置是 Windows 10 的新增功能。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ 安静</strong></p></td>
<td align="left"><p>这将取消显示任何安装程序的用户体验，包括回滚的用户体验。 示例：</p>
<pre class="syntax" space="preserve"><code>setup /auto upgrade /quiet</code></pre>
<p>此设置是 Windows 10 的新增功能。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ ReflectDrivers</strong><em>&lt;位置&gt;</em></p></td>
<td align="left"><p>指定包含加密的已启用的第三方加密的计算机的驱动程序的文件夹的路径。</p>
<pre class="syntax" space="preserve"><code>Setup /ReflectDrivers &lt;folder_path&gt; </code></pre>
<p>此设置是 Windows 10，1607年版本的新增功能。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ ResizeRecoveryPartition</strong> {<strong>启用</strong> | <strong>禁用</strong>}</p></td>
<td align="left"><p>指定是否调整现有的 Windows 恢复环境 (Windows RE) 分区的大小或在安装过程中创建一个新的确定。</p>
<p><strong>启用</strong>︰ 在安装期间，Windows 可以将现有的 Windows RE 工具分区大小调整或如果需要创建一个新。</p>
<p><strong>禁用</strong>: Windows 不会将现有的 Windows RE 工具分区大小调整或在安装过程中创建一个新。</p>
<p>若要了解有关 Windows RE 分区的详细信息，请参阅[基于 UEFI/GPT 的硬盘分区](configure-uefigpt-based-hard-drive-partitions.md)和[基于 BIOS/MBR 硬盘分区](configure-biosmbr-based-hard-drive-partitions.md)。</p>
<pre class="syntax" space="preserve"><code>Setup /resizerecoverypartition disable</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ ShowOOBE</strong> {<strong>完整</strong> | <strong>无</strong>}</p></td>
<td align="left"><p><strong>全</strong>︰ 要求用户以交互方式完成的体验 (OOBE)。</p>
<p><strong>无</strong>︰ 跳过 OOBE 并选择默认设置。</p>
<p>示例：</p>
<pre class="syntax" space="preserve"><code>setup.exe /auto upgrade /showoobe full</code></pre>
<p>此设置是 Windows 10 的新增功能。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ 遥测</strong>{<strong>启用</strong> | <strong>禁用</strong>}</p></td>
<td align="left"><p>指定 Windows 安装程序是否应捕获和报告安装数据。</p>
<p><strong>启用</strong>︰ 设置捕获和报告安装数据。</p>
<p><strong>禁用</strong>︰ 安装程序不会不捕获和报告安装数据。</p>
<pre class="syntax" space="preserve"><code>Setup /telemetry disable</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ 安装程序的 TempDrive</strong> {<strong>启用</strong> | <strong>禁用</strong>}</p></td>
<td align="left"><p>指示 Windows 安装程序将在指定的分区上临时安装文件。 升级<strong>/tempdrive:</strong>选项将影响只能临时文件的位置。 操作系统升级运行 Setup.exe 文件所在的分区中。</p><p>/Tempdrive 参数是 Windows 10，1607，版本中可用，但不可在早期版本的 Windows 10。</p>
<p><em>&lt;驱动器盘符&gt;</em>指定要在 Windows 安装过程中复制到安装文件的分区。 例如︰</p>
<pre class="syntax" space="preserve"><code>Setup /tempdrive:H</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ 无人参与︰</strong><em>&lt;应答</em>&gt;</p></td>
<td align="left"><p>使您可以使用 Windows 安装程序答案文件。 这被称为无人参与安装。 您必须指定一个值为<em>&lt;应答&gt;</em>。 Windows 安装程序在安装过程中应用答案文件中的值。</p>
<p><em>&lt;应答&gt;</em>指定的文件路径和文件名的无人参与的 Windows 安装程序答案文件。</p>
<pre class="syntax" space="preserve"><code>Setup /unattend:\\server\share\unattend.xml</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ 卸载</strong>{<strong>启用</strong> | <strong>禁用</strong>}</p></td>
<td align="left"><p>确定是否包括 Windows 控件，允许用户返回到以前的操作系统。</p>
<p>此设置是 Windows 10 的新增功能。</p>
<pre class="syntax" space="preserve"><code>Setup /uninstall disable</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ USBDebug:</strong><em>&lt;主机名&gt;</em></p></td>
<td align="left"><p>设置调试在 USB 端口上。 调试数据会在下次重新启动时生效。</p>
<p><em>&lt;主机名&gt;</em>指定要调试的计算机的名称。 例如︰</p>
<pre class="syntax" space="preserve"><code>Setup /usbdebug:testmachine01</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ WDSDiscover</strong></p></td>
<td align="left"><p>指定客户端应该在 Windows 部署服务 (WDS) 发现模式。</p>
<p>如果您不使用此选项指定<strong>/wdsserver</strong> ，WDS 搜索服务器。 例如，若要在启动 WDS 客户端这个动态发现模式下，运行以下命令︰</p>
<pre class="syntax" space="preserve"><code>Setup /wds /wdsdiscover</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ WDSServer:</strong><em>&lt;服务器名&gt;</em></p></td>
<td align="left"><p>指定客户端应该连接到 Windows 部署服务服务器的名称。</p>
<p>若要使用此设置，您必须使用<code>/wdsdiscover</code>选项。</p>
<p><em>&lt;服务器名称&gt;</em>可以是 IP 地址、 NetBIOS 名称或完全限定的域名 (FQDN)。 例如，启动 Windows 部署服务客户端在此静态发现模式下，运行以下命令︰</p>
<pre class="syntax" space="preserve"><code>Setup /wds /wdsdiscover /wdsserver:MyWDSServer</code></pre></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Windows 安装程序状态](windows-setup-states.md)

[Windows 安装程序版本配置和产品 ID 文件 （EI.cfg 和 PID.txt）](windows-setup-edition-configuration-and-product-id-files--eicfg-and-pidtxt.md)

[Windows 安装程序日志文件和事件日志](windows-setup-log-files-and-event-logs.md)

 

 
