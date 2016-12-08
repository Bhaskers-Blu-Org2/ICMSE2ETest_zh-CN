---
title: UpdateHeapTrace
description: UpdateHeapTrace
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 5cbff080-bdaa-412d-8412-22013f2717fb
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 9f319e5fec486aefffe45f162ae5cea6b01f23b1
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="updateheaptrace"></a>UpdateHeapTrace


\[某些信息与预发行产品在商业上发布之前可能大幅度修改。 Microsoft 不做任何担保，明示或暗示的担保，此处提供的信息。\]

此函数更新跟踪会话的一组新的 Pid、 stackwalking 事件或其他 ETW 会话更改现有堆。

``` syntax
ULONG
WINAPI
UpdateHeapTrace(
    _Inout_ PEVENT_TRACE_PROPERTIES Properties,
    _In_z_ LPCWSTR wszSessionName,
    _In_reads_opt_(cPids) const ULONG Pids[],
    _In_  ULONG cPids,
    _In_reads_opt_(cStackTracingEventIds) const STACK_TRACING_EVENT_ID StackTracingEventIds[],
    _In_  ULONG cStackTracingEventIds
    );
```

## <a name="parameters"></a>参数


<a href="" id="tracehandle--out-"></a>*TraceHandle*\[出\]  
存储事件跟踪会话的句柄。 此参数设置为零，如果句柄无效。 此参数不应与无效的\_处理\_值。 如果函数失败，则不使用此句柄。

<a href="" id="properties--in--out-"></a>*属性*\[传入、 传出\]  
一个指针，指向[事件\_跟踪\_属性](https://msdn.microsoft.com/library/windows/desktop/aa363784.aspx)更新会话的属性与结构。 请参阅 ControlCode 事件的[ControlTrace](https://msdn.microsoft.com/library/windows/desktop/aa363696.aspx)函数\_跟踪\_控件\_更新此结构的成员可以指定哪些详细信息。

<a href="" id="wszsessionname-in-"></a>*wszSessionName*\[中\]  
要更新的堆跟踪会话名称。 这应该是被传递给 StartHeapTrace 的名称相同。

<a href="" id="pids--in-"></a>*Pid*\[in\]  
进程 Id，以启用上的堆跟踪的数组。

<a href="" id="cpids--in--out-"></a>*cPids*\[传入、 传出\]  
Pid 的数组的大小。

<a href="" id="stacktracingeventids--in-"></a>*StackTracingEventIds*\[in\]  
数组的[堆栈\_跟踪\_事件\_ID](https://msdn.microsoft.com/library/windows/hardware/dn631805.aspx)结构指定应为启用哪堆事件堆栈审核。 可以为 NULL。

<a href="" id="cstacktracingeventids--in-"></a>*cStackTracingEventIds*\[in\]  
StackTracingEventIds 数组的大小。

## <a name="return-value"></a>返回值


错误\_成功表示成功。

可能的错误值如下表所述。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>错误值</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ERROR_ALREADY_EXISTS</p></td>
<td><p>只能运行一个内核记录器实例在系统上运行。 如果该函数尝试启动另一个组件启动内核日志记录后，可能将返回此错误。</p></td>
</tr>
<tr class="even">
<td><p>ERROR_INVALID_FLAGS</p></td>
<td><p>可能表示<strong>Properties.EnableFlags</strong>中有无效的跟踪标记。</p></td>
</tr>
<tr class="odd">
<td><p>ERROR_OUT_OF_MEMORY</p></td>
<td><p>可能是表示为 EVENT_TRACE_PROPERTIES 分配内存失败。</p></td>
</tr>
</tbody>
</table>

 

如果函数而不是列出的那些原因失败，则返回的系统错误代码。

## <a name="remarks"></a>备注


无

## <a name="related-topics"></a>相关的主题


[函数](functions-wpa.md)

[StartHeapTrace](startheaptrace.md)

 

 







