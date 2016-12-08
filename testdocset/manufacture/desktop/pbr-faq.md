---
author: Justinha
Description: "点击式重新设置的常见问题 (FAQ)"
ms.assetid: 80a313e3-6c2e-4768-9fec-78dd2876f024
MSHAttr: PreferredLib:/library/windows/hardware
title: "点击式重新设置的常见问题 (FAQ)"
ms.openlocfilehash: abfe8a173bf415aa1648048652767e0d3e96008b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="push-button-reset-frequently-asked-questions-faq"></a>点击式重新设置的常见问题 (FAQ)


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">问题</th>
<th align="left">解答</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">是个用户所需的窗口重新运行按钮重置功能？</td>
<td align="left">是。 要运行按钮重置功能，必须在本地硬盘上提供 Windows RE 启动映像 (Winre.wim) 并使用 Reagentc 工具来注册它的位置。 您可以使用默认的 Winre.wim （网址 C:\Windows\System32\Recovery） 或自定义的 Winre.wim 图像。 如果在本地硬盘上未启用 Windows RE，用户将不得不启动 Windows RE 从媒体访问按钮重置功能。</td>
</tr>
<tr class="even">
<td align="left">精简的操作系统是什么？</td>
<td align="left">精简的操作系统是允许 Windows 10 在 Pc 上存储容量为 16GB 低与要部署的功能的集合。 两个主要技术包括︰
<ul>
<li>运行时系统文件的压缩</li>
<li>单实例存储与按钮重置功能所用的自定义软件包的安装自定义项的</li>
</ul></td>
</tr>
<tr class="odd">
<td align="left">何时应使用精简的操作系统？</td>
<td align="left">同时，系统的压缩文件和单实例存储的自定义具有相同特征作为从 Windows 8.1 的 WIMBoot 技术。 而紧凑的操作系统都支持所有硬件配置，它只被推荐基于闪存的存储在 Pc 上使用。</td>
</tr>
<tr class="even">
<td align="left">如何知道是否操作系统将会压缩？</td>
<td align="left">可以使用 Compact.exe 来查询当前的压缩状态。</td>
</tr>
<tr class="odd">
<td align="left">如何判断是否.ppkg 是单一实例？</td>
<td align="left">运行 Fsutil.exe，并指定存储.ppkg 的驱动器。 例如︰ <code>fsutil.exe wim enumwims c:</code></td>
</tr>
<tr class="even">
<td align="left">是否有任何格式要求的 ResetConfig.xml 文件？</td>
<td align="left">是。 始终使用 utf-8 编码，并且不使用 Unicode 或 ANSI。 在 ResetConfig.xml 文件中，和其他.xml 文件中添加以下声明︰ <code>&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;</code>。</td>
</tr>
<tr class="odd">
<td align="left">哪些类型的可移动介质制造商创建恢复媒体的支持？</td>
<td align="left">Dvd 或 USB 闪存驱动器可以用作恢复媒体。 请注意，按钮重置功能要求所有恢复资源位于相同的介质。</td>
</tr>
<tr class="even">
<td align="left">Recimg.exe 是否支持在 Windows 10？</td>
<td align="left">Windows 10 中，没有 recimg.exe 已被否决。</td>
</tr>
<tr class="odd">
<td align="left">点击式重新设置是否支持在 Windows 服务器上？</td>
<td align="left">没有，Windows 服务器 2016年技术预览不支持此功能。</td>
</tr>
<tr class="even">
<td align="left">可以自定义恢复解决方案 （即不点击式重置） 恢复资源调配使用 Windows ICD 或者 USMT 的扫描状态工具创建的包。</td>
<td align="left">只能通过使用 Windows 图像处理和配置设计器 (ICD) 创建的按钮重置或部署媒体应用资源调配包。 不支持自定义恢复解决方案这些软件包的应用。</td>
</tr>
<tr class="odd">
<td align="left">如果配置软件包创建使用 USMT 的扫描状态工具是大于 4 GB，将"创建恢复驱动器"实用程序允许客户创建 USB 恢复媒体吗？</td>
<td align="left">是的<strong>恢复驱动器创建</strong>实用程序将拆分的供应包分成小块之前将其复制到 USB 闪存驱动器。 恢复过程中，部分将重组到原始配置包。</td>
</tr>
<tr class="even">
<td align="left">我已预先安装在计算机上的操作系统更新，如何确保它们正在恢复过程中恢复？</td>
<td align="left">DISM.exe 的与 /StartComponentCleanup 和 /ResetBase 选项的 /Cleanup-Image 命令将所有已安装的 OS 更新标记为永久。 在恢复期间始终还原永久更新。</td>
</tr>
<tr class="odd">
<td align="left">如何确定上次运行 /ResetBase 选项时？</td>
<td align="left"><p>检查注册表路径下的<strong>LastResetBase_UTC</strong>注册表项︰</p>
<p>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Component 基于服务</p></td>
</tr>
<tr class="even">
<td align="left">我有文件需要保留恢复时重置您的 PC 和刷新您的 PC 不会进行，但我不想它们捕获使用扫描状态。 应放置这些文件的位置</td>
<td align="left">在 C:\Recovery\OEM 下的所有内容将都保留在重置期间修改您的 PC 和刷新您的 PC。 但是，应该注意的是，这些内容将同时备份到 USB 恢复媒体使用创建的恢复驱动器的实用程序时。</td>
</tr>
<tr class="odd">
<td align="left">我找不到刷新 PC 选项设置或 Windows RE 中了。 该功能在哪里？</td>
<td align="left">同时刷新您的 PC 和您的 PC 都属于相同的用户体验，重置此 PC 选项和 Windows RE 中设置下现在的重置。 当您启动重置此 PC 体验时，您将看到其他选项︰
<ul>
<li><strong>将文件保存</strong>– 这将启动刷新您的 PC 功能。</li>
<li><strong>移除所有内容</strong>– 这将启动重置您的 PC 功能。</li>
<li><strong>恢复出厂设置</strong>– 在个人电脑升级的 Windows 8/8.1，这将启动工厂恢复使用现有的恢复映像。</li>
</ul></td>
</tr>
<tr class="even">
<td align="left">使用扫描状态捕获自定义项时是否应指定 /drivers 选项？</td>
<td align="left">/Drivers 选项不是必需的如果所创建的资源调配包是要用于按钮重置功能。 依靠以点击方式重置功能持续驱动程序已经安装，这样就无需重新应用工厂预安装驱动程序。 注意︰ 使用扫描状态的 /apps 选项捕获驱动程序安装的驱动程序 INF 包的小程序。</td>
</tr>
<tr class="odd">
<td align="left">可用磁盘空间是否需要刷新您的 PC 的功能才能成功运行？</td>
<td align="left">如果您已安装的自定义转换文件指针引用使用扫描状态创建的自定义软件包，则所需的磁盘空间︰ 4 GB + size_of_ppkg * 0.2
<p>否则，所需的磁盘空间为︰ 4 GB + size_of_ppkg * 2</p></td>
</tr>
<tr class="even">
<td align="left">我需要从 128 MB 的 MSR 分区的大小减少到 16 MB，根据更新的分区布局的建议是？</td>
<td align="left">No. Windows 将继续支持 128 MB MSR 分区。 但是，在 Pc 上存储容量有限，16 MB MSR 分区建议为最终用户提供多少可用存储器的性能越好。</td>
</tr>
<tr class="odd">
<td align="left">是否有任何已知的问题与使用重置后经过工厂地面测试还原至出厂状态恢复 Pc 个人计算机？</td>
<td align="left">尽管 PBR 功能并未打算在工厂地板上使用，没有任何技术限制，这将使它。 但是，记住以下时在工厂车间使用重置您的 PC:
<ul>
<li>如果工厂地面测试包括激活 Windows，请重新设置您的 PC 不还原回非激活状态的单位</li>
<li>预安装的 RDX 内容将被删除</li>
<li>如果单位不会重置多天工厂验证但仍接通后，将在维护期间删除除在 OOBE 期间选择预安装的语言</li>
<li>最终用户将能够告诉，单位已重置期间工厂通过寻找下 C:\Windows\Logs\PBR 的 PBR 日志</li>
</ul></td>
</tr>
</tbody>
</table>

 

 

 





