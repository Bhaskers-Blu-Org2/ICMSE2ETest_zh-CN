---
title: DeletePreMergedTraceFiles
description: DeletePreMergedTraceFiles
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 6c9424dd-6ec3-4835-af18-541cec28da76
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: d88b882e827bbed2808572376a8e85d96d3a3389
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="deletepremergedtracefiles"></a>DeletePreMergedTraceFiles


指示是否删除 premerged 的事件跟踪日志 (ETL) 文件。

## <a name="element-hierarchy"></a>元素层次结构


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[TraceMergeProperties](tracemergeproperties.md)&gt;

          &lt;[TraceMergeProperty](tracemergeproperty.md)&gt;

               &lt;**DeletePreMergedTraceFiles**&gt;

## <a name="syntax"></a>语法


``` syntax
<DeletePreMergedTraceFiles Value = boolean>
</DeletePreMergedTraceFiles>
```

## <a name="attributes-and-elements"></a>特性和元素


### <a name="attributes"></a>属性

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th>属性</th>
<th>说明</th>
<th>数据类型</th>
<th>是否必需</th>
<th>默认值</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>值</strong></p></td>
<td><p>指示是否删除 premerged 的 ETL 文件。</p></td>
<td><p>布尔</p></td>
<td><p>否</p></td>
<td><p>true</p></td>
</tr>
</tbody>
</table>

 

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>元素</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[TraceMergeProperty](tracemergeproperty.md)</p></td>
<td><p>包含多个配置文件中的记录进行合并时，将应用的配置。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[元素](elements.md)

 

 







