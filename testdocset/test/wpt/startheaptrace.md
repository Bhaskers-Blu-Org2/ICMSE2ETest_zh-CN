---
title: StartHeapTrace
description: StartHeapTrace
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 2f3ecae0-532a-45ab-a5e3-a5ed4868decf
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 62cd9090390576c155140a761fe3285702904da4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="startheaptrace"></a>StartHeapTrace


\[某些信息与预发行产品在商业上发布之前可能大幅度修改。 Microsoft 不做任何担保，明示或暗示的担保，此处提供的信息。\]

此函数注册，并将启动一套指定 Pid 的堆跟踪会话。 您还可以启用堆栈审核某些堆事件如分配或删除使用此函数。

必须在调用此函数之前创建的堆跟踪被启用的进程。 来捕获堆事件从最开始的程序，则建议使用能启动进程[创建\_暂停](https://msdn.microsoft.com/library/windows/desktop/ms682425.aspx)标记，然后为其 PID，则过程启用的堆跟踪恢复。

堆跟踪是非常详细，可以快速生成一个很大的跟踪文件。 事件可能丢失轻松如果会话的缓冲区太小或太少。 建议的堆启用跟踪的进程的数量有限，为了不丢失事件。 启用堆跟踪可能会对所跟踪的过程对性能的影响。

``` syntax
ULONG
WINAPI
StartHeapTrace(
    _Out_ PTRACEHANDLE TraceHandle,
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
存储指向的[事件\_跟踪\_属性](https://msdn.microsoft.com/library/windows/desktop/aa363784.aspx)结构。 事件\_跟踪\_属性配置会话行为的某些方面。

不需要设置 Guid 成员，因为此函数始终使用其自己的值。 如果没有指定 GUID 将不能使用它。

<a href="" id="wszsessionname--in-"></a>*wszSessionName*\[in\]  
要传递给[StartTrace](https://msdn.microsoft.com/library/windows/desktop/aa364117.aspx)的 SThe 会话名称。

<a href="" id="pids--in-"></a>*Pid*\[in\]  
进程 Id，以启用上的堆跟踪的数组。

<a href="" id="cpids--in-"></a>*cPids*\[in\]  
Pid 的数组的大小。

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

[UpdateHeapTrace](updateheaptrace.md)

 

 







