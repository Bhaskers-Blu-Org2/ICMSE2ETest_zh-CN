---
title: "函数"
description: "函数"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: d449cc0e-82fd-484f-8ca6-56a430489e08
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 33c31abc1b40bf84a4d6cc590739440301e9ec95
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="functions"></a>函数


本节介绍内核跟踪控制 API 中可用的函数。

## <a name="in-this-section"></a>在这一节


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>[CreateMergedTraceFile](createmergedtracefile.md)</p></td>
<td><p>将多个 WPT/ETW 跟踪文件合并到单一的输出文件。</p></td>
</tr>
<tr class="even">
<td><p>[StartHeapTrace](startheaptrace.md)</p></td>
<td><p>注册并启动一套指定 Pid 的堆跟踪会话。 启用堆栈遍历某些堆事件如分配或删除使用此函数。</p></td>
</tr>
<tr class="odd">
<td><p>[StartKernelTrace](startkerneltrace.md)</p></td>
<td><p>注册并启动内核事件跟踪会话。</p></td>
</tr>
<tr class="even">
<td><p>[UpdateHeapTrace](updateheaptrace.md)</p></td>
<td><p>更新现有的堆跟踪与一组新的 Pid、 stackwalking 事件或其他 ETW 会话更改会话。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[内核跟踪控件 API 参考](kernel-trace-control-api-reference.md)

 

 







