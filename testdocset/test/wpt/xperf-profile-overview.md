---
title: "Xperf 配置文件概述"
description: "Xperf 配置文件概述"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 2de4bf4a-eb88-4dd9-a91d-2b049ce9cd49
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 9e25ef2c0445cfa51ea15a69ac95810c1070c143
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="xperf-profile-overview"></a>Xperf 配置文件概述


跟踪配置文件是跟踪的有关特定类型设置的集合。 这些配置文件不兼容 Windows 性能记录器 (WPR) 录制的。 您可以收集和控制这些设置与每个操作的单个命令。 大多数配置文件是这两种类型之一︰ 基于内存的或基于文件的。 选择配置文件相匹配的机制，用于跟踪︰ 写入到内存的缓冲区中，或写入文件。

下表描述类型的会话。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>会话类型</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>InSequentialFile 的会话</p></td>
<td><p>这些会话保存到一个文件中按顺序，将其扩展，直到达到预设的最大文件大小。 这种现象将映射到 ETW 顺序模式。</p></td>
</tr>
<tr class="even">
<td><p>InBuffer 的会话</p></td>
<td><p>这些会话将数据保存在内存中，当缓冲区已满时，用最新的数据覆盖最旧的数据。 这些会话必须保存为一个快照文件进行分析。 这种现象将映射到的 ETW 缓冲模式。</p></td>
</tr>
</tbody>
</table>

 

**请注意**  
不能组合的文件模式。

 

## <a name="related-topics"></a>相关的主题


[Xperf 配置文件](xperf-profiles.md)

[会话](sessions.md)

[提供程序](providers.md)

 

 







