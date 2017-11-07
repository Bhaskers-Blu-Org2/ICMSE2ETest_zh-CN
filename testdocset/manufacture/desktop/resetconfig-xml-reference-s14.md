---
author: Justinha
Description: "ResetConfig XML 参考"
ms.assetid: dc9f16c9-d094-49d6-9aaf-3a02c381ccc0
MSHAttr: PreferredLib:/library/windows/hardware
title: "ResetConfig XML 参考"
ms.openlocfilehash: b79d244ebaf6a07bc078e3d87a713cfe228f6214
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="resetconfig-xml-reference"></a>ResetConfig XML 参考


此引用描述用于创作的 ResetConfig.xml 文件，用于配置 Windows 恢复环境按钮重置功能的所有 XML 元素。

## <a name="span-idresetspanspan-idresetspanspan-idresetspanreset"></a><span id="Reset"></span><span id="reset"></span><span id="RESET"></span>重置


`Reset` XML 元素可以包含的元素︰ `Run` ， `SystemDisk`。

## <a name="span-idresetconfigrunspanspan-idresetconfigrunspanspan-idresetconfigrunspanrun"></a><span id="ResetConfigRun"></span><span id="resetconfigrun"></span><span id="RESETCONFIGRUN"></span>运行


`Run` XML 元素用于添加自定义脚本添加到按钮重置功能。

您可以指定最多四个`Run`在一个 ResetConfig.xml 文件中的元素。 每个`Run`元素必须包含不同*\[ExtPoint\]*值`Phase`属性。

下表描述了可以添加到中的有效元素`Run`元素︰

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">元素</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><code>Run Phase=&quot;[ExtPoint]&quot;&quot;</code></p></td>
<td align="left"><p>每个<code>Run</code>元素定义要使用的扩展性点的脚本在该扩展性点，执行和预计的持续时间以分钟为单位。</p>
<p><code>Phase</code>属性是必需的。 它为<em>[ExtPoint]</em>接受下面的值︰</p>
<ul>
<li><p><code>BasicReset_BeforeImageApply</code>. 运行指定的程序扩展性点 a。</p></li>
<li><p><code>BasicReset_AfterImageApply</code>. 在扩展性点 B 上运行指定的程序</p></li>
<li><p><code>FactoryReset_AfterDiskFormat</code>. 在扩展性点 C 运行指定的程序</p></li>
<li><p><code>FactoryReset_AfterImageApply</code>. 在扩展性点 D 运行指定的程序</p></li>
</ul>
<p>您可以指定最多四个<code>Run</code>在一个 ResetConfig.xml 文件的各节。 但是，每个<code>Run</code>部分必须包含不同阶段属性值。</p></td>
</tr>
<tr class="even">
<td align="left"><p><code>Path</code></p></td>
<td align="left"><p>指定对于特定的脚本位置<code>Run</code>部分。</p>
<p>路径必须是脚本中包含 ResetConfig.xml （通常是 C:\Recovery\OEM） 的文件夹的相对路径。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><code>Duration</code></p></td>
<td align="left"><p>在几分钟内，列出了您想要运行的自定义脚本指定的估计的时间。 此估计值用于在 GUI 中显示进度信息。</p>
<p>持续时间必须为整数，并且必须是 1 到 5 之间。</p></td>
</tr>
<tr class="even">
<td align="left"><p><code>Param</code></p></td>
<td align="left"><p>指定要在运行自定义脚本或可执行文件时使用的命令行参数。 值将被视为一个字符串，并且可以包含多个参数。</p>
<p><code>Param</code> 不支持空元素。 如果您的脚本不需要参数，则不包括此元素。 有关示例，请参见本主题后面的[使用 ResetConfig.xml](#usingresetconfig-xml) 。</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idresetconfigxmlsysdiskoptionsspanspan-idresetconfigxmlsysdiskoptionsspansystemdisk"></a><span id="resetconfig.xml_sysdisk_options"></span><span id="RESETCONFIG.XML_SYSDISK_OPTIONS"></span>SystemDisk


`SystemDisk`元素进行自定义的裸机恢复功能。 有关详细信息，请参阅[创建的介质运行 Push-Button 重置功能](create-media-to-run-push-button-reset-features-s14.md)。

您可以指定一个`SystemDisk`部分。 以下是必需和可选元素︰

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">元素</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><code>MinSize</code>
<p></p></td>
<td align="left"><p>必需。 指定主硬盘，所需的最小大小 （兆字节）。</p>
<p>如果系统磁盘不满足此大小要求将不会继续执行裸机恢复。</p></td>
</tr>
<tr class="even">
<td align="left"><p><code>DiskpartScriptPath</code></p></td>
<td align="left"><p>必需。 相对于 C:\Recovery\OEM 的 Diskpart 脚本的路径。 该脚本应假设所有现有分区已被删除，而系统磁盘在 Diskpart 中具有焦点。</p>
<p>例如，如果恢复脚本位于<code>C:\Recovery\OEM\Scripts\RecreatePartitions.dps</code>，使用值<code>\Scripts\RecreatePartitions.dps</code>。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><code>OSPartition</code></p></td>
<td align="left"><p>必需。 应该向其还原操作系统的分区。 ESP 或活动分区必须是同一磁盘操作系统上。</p></td>
</tr>
<tr class="even">
<td align="left"><p><code>RestoreFromIndex</code></p></td>
<td align="left"><p>可选项。 裸机恢复期间要应用的 install.wim 中的图像的索引。 此元素是可选的仅需要上制造商创建恢复媒体</p></td>
</tr>
<tr class="odd">
<td align="left"><p><code>WindowsREPartition</code></p></td>
<td align="left"><p>可选项。 指定 Windows RE 启动映像所在的分区。</p>
<p><code>WindowsREPartition</code> ，<code>WindowsREPath</code>元素是可选的但必须同时使用。 如果只有其中一个元素，则您的用户将无法对硬盘进行重新分区。</p></td>
</tr>
<tr class="even">
<td align="left"><p><code>WindowsREPath</code></p></td>
<td align="left"><p>可选项。 其中 Winre.wim 启动映像是复制，转移，相对于中指定分区的根文件夹路径指定<code>WindowsREPartition</code>元素。</p>
<p><code>WindowsREPartition</code> ，<code>WindowsREPath</code>元素是可选的但必须同时使用。 如果只有其中一个元素，则您的用户将无法对硬盘进行重新分区。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><code>Compact</code></p></td>
<td align="left"><p>可选项。 指定是否应启用的每个文件压缩应用恢复映像。 此元素是可选的仅需要上制造商创建恢复媒体。</p>
<p><code>Compact</code> 接受以下值︰</p>
<ul>
<li><code>True</code>︰ 分别压缩图像中应用的文件。</li>
<li><code>False</code> （默认值）︰ 不使用压缩。</li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><p><code>RecoveryImagePartition</code></p></td>
<td align="left"><p>此设置是 Windows 10 中弃用。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><code>RecoveryImagePath</code></p></td>
<td align="left"><p>此设置是 Windows 10 中弃用。</p></td>
</tr>
<tr class="even">
<td align="left"><p><code>RecoveryImageIndex</code></p></td>
<td align="left"><p>此设置是 Windows 10 中弃用。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><code>WIMBoot</code></p></td>
<td align="left"><p>此设置是 Windows 10 中弃用。</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idusingresetconfigxmlspanspan-idusingresetconfigxmlspanusing-resetconfigxml"></a><span id="usingresetconfig.xml"></span><span id="USINGRESETCONFIG.XML"></span>使用 ResetConfig.xml


如果您使用文本编辑器来创作.xml 文件，您必须使用.xml 文件扩展名保存文档并使用 utf-8 编码。 不能使用 ANSI 编码。

这些文件应该放在 c: 文件夹\\恢复\\OEM 和按钮重置功能会自动检测。

## <a name="span-idexamplespanspan-idexamplespanspan-idexamplespanexample"></a><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>示例


这是 ResetConfig.xml 文件的代码示例。

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<Reset>
 <Run Phase="BasicReset_BeforeImageApply">
   <Path>Fabrikam\CopyFiles.cmd</Path>
   <Duration>2</Duration>
 </Run>
 <Run Phase="BasicReset_AfterImageApply">
   <Path>Fabrikam\InstallDrivers.cmd</Path>
   <Param>/allDrivers</Param>
   <Duration>2</Duration>
 </Run>
 <Run Phase="FactoryReset_AfterDiskFormat">
   <Path>Fabrikam\FixPartitions.exe</Path>
   <Duration>2</Duration>
 </Run>
 <Run Phase="FactoryReset_AfterImageApply">
   <Path>Fabrikam\InstallDrivers.cmd</Path>
   <Param>/allDrivers</Param>
   <Duration>2</Duration>
 </Run>
 <SystemDisk>
   <MinSize>75000</MinSize>
   <DiskpartScriptPath>Fabrikam\CreatePartition.txt </DiskpartScriptPath>
   <OSPartition>4</OSPartition>
   <RestoreFromIndex>2</RestoreFromIndex>
   <WindowsREPartition>1</WindowsREPartition>
   <WindowsREPath>Recovery\WindowsRE</WindowsREPath>
   <Compact>False</Compact>
 </SystemDisk>
</Reset>
```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[点击式重新设置概述](push-button-reset-overview.md)

[创建介质运行按钮重置功能](create-media-to-run-push-button-reset-features-s14.md)

 

 






