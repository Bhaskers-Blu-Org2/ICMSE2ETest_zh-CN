---
author: Justinha
Description: "硬盘上的位置的路径格式"
ms.assetid: 9f9d96ae-4fec-487d-95d2-ffd09b7d9fd1
MSHAttr: PreferredLib:/library/windows/hardware
title: "硬盘上的位置的路径格式"
ms.openlocfilehash: 1d4ffeb42480ecd7520ced5b9ec1c731e831033f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="hard-disk-location-path-format"></a>硬盘上的位置的路径格式


本主题介绍的硬盘位置路径格式。 此格式用于标识位置路径使用 DiskPart 工具中的每个磁盘。 位置路径格式取决于计算机的物理连接。

描述如何配置 Windows® 标识基于位置路径格式的驱动器的说明，请参阅[配置多个硬盘驱动器](configure-multiple-hard-drives.md)。

## <a name="span-idlocationpathformatspanspan-idlocationpathformatspanspan-idlocationpathformatspanlocation-path-format"></a><span id="LocationPathFormat"></span><span id="locationpathformat"></span><span id="LOCATIONPATHFORMAT"></span>位置路径格式


小型计算机系统接口 (SCSI)、 串行连接 SCSI (SAS)，或独立磁盘冗余阵列 (RAID) 总线类型的磁盘的位置路径的基本语法如下所示︰

&lt;*即插即用的位置路径适配器的*&gt;**\#**&lt;*总线类型*&gt;(**P**&lt;*路径 ID*&gt;**T**&lt;*目标 ID*&gt;**L**&lt;*LUN ID*&gt;)

对于具有高级技术附件 (ATA) 或串行 ATA (SATA) 总线类型的磁盘位置路径的基本语法如下所示︰

&lt;*即插即用的位置路径适配器的*&gt;**\#**&lt;*总线类型*&gt;(**C**&lt;*通道 ID*&gt;**T**&lt;*目标 ID*&gt;**L**&lt;*LUN ID*&gt;)

下表的位置路径中定义的元素。

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
<td align="left"><p>&lt;<em>适配器的即插即用的位置路径</em>&gt;</p></td>
<td align="left"><p>适配器的路径。 通过调用 SetupDiGetDeviceProperty 与 DEVPKEY_Device_LocationPaths 属性检索路径。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>#</strong>&lt;<em>总线类型</em>&gt;</p></td>
<td align="left"><p>以下类型之一︰ ATA、 SCSI、 SAS 或 RAID。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>P</strong>&lt;<em>Path ID</em>&gt;</p></td>
<td align="left"><p>SCSI_ADDRESS PathId 字段。 通过调用 IOCTL_SCSI_GET_ADDRESS 来检索 PathID。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>C</strong>&lt;<em>通道 ID</em>&gt;</p></td>
<td align="left"><p>SCSI_ADDRESS PathId 字段。 通过调用 IOCTL_SCSI_GET_ADDRESS 来检索 PathID。</p>
<div class="alert">
<strong>请注意</strong>  
<p>对于使用 ATA/SATA 总线类型的磁盘，通道 ID 引用同一 PathID 字段。 仍使用 C 的前缀。</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>T</strong>&lt;<em>目标 ID</em>&gt;</p></td>
<td align="left"><p>SCSI_ADDRESS TargetId 字段。 通过调用 IOCTL_SCSI_GET_ADDRESS 来检索 TargetId。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>L</strong>&lt;<em>LUN ID</em>&gt;</p></td>
<td align="left"><p>SCSI_ADDRESS 的逻辑单元号 (LUN) 字段。 通过调用 IOCTL_SCSI_GET_ADDRESS 来检索该 LUN。</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idexamplesspanspan-idexamplesspanspan-idexamplesspanexamples"></a><span id="Examples"></span><span id="examples"></span><span id="EXAMPLES"></span>示例


下表给出每种总线或磁盘位置路径的示例︰

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">总线或磁盘类型</th>
<th align="left">位置路径</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>集成开发环境 (IDE)，ATA、 并行 ATA (PATA) 或 SATA</p></td>
<td align="left"><p>PCIROOT(0)#PCI(0100)#ATA(C01T03L00)</p></td>
</tr>
<tr class="even">
<td align="left"><p>SCSI</p></td>
<td align="left"><p>PCIROOT(0)#PCI(1C00)#PCI(0000)#SCSI(P00T01L01)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>SAS</p></td>
<td align="left"><p>PCIROOT(1)#PCI(0300)#SAS(P00T03L00)</p></td>
</tr>
<tr class="even">
<td align="left"><p>外围组件互连 (PCI) RAID</p></td>
<td align="left"><p>PCIROOT(0)#PCI(0200)#PCI(0003)#PCI(0100)#RAID(P02T00L00)</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[配置多个硬盘驱动器](configure-multiple-hard-drives.md)

[DiskPart 命令行语法](http://go.microsoft.com/fwlink/?LinkId=128458)

 

 






