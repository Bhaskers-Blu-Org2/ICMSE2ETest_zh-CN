---
title: StartKernelTrace
description: StartKernelTrace
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: b8eab537-85ae-441e-aea9-486626ec0c16
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 49b8528d26dba62ea2732370a107f22570d70f01
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="startkerneltrace"></a>StartKernelTrace


此函数将注册并启动内核事件跟踪会话。 您还可以启用 stackwalking 对于某些内核事件使用此函数。

``` syntax
ULONG
WINAPI
StartKernelTrace(
__out PTRACEHANDLE TraceHandle,
__inout PEVENT_TRACE_PROPERTIES Properties,
__in ULONG cStackTracingEventIds
);
```

## <a name="parameters"></a>参数


<a href="" id="tracehandle--out-"></a>*TraceHandle*\[出\]  
存储事件跟踪会话的句柄。 此参数设置为零，如果句柄无效。 此参数不应与无效的\_处理\_值。 如果函数失败，则不使用此句柄。

<a href="" id="properties--in--out-"></a>*属性*\[传入、 传出\]  
存储指向的[事件\_跟踪\_属性结构](http://go.microsoft.com/fwlink/p/?linkid=212231&clcid=0x409)。 事件\_跟踪\_属性配置会话行为的某些方面。

该事件的第一个成员\_跟踪\_属性结构是[WNODE\_标头结构](http://go.microsoft.com/fwlink/p/?LinkID=212222&clcid=0x409)，到这里为**Wnode**。

以下事件\_跟踪\_属性。Wnode 成员必须设置以配置内核跟踪控制。

<a href="" id="buffersize"></a>**BufferSize**  
此成员包含的总大小，以字节为单位，为事件跟踪会话属性分配的内存。 内存的大小必须包含足够的空间来存储以下数据︰

-   该事件\_跟踪\_属性结构。

-   会话名称字符串。

-   日志文件的名称字符串。

<a href="" id="guid"></a>**Guid**  
每个跟踪会话必须定义引用会话的 GUID。

对于 NT 内核记录器会话，必须将此成员设为 SystemTraceControlGuid。 有关日志记录模式的常数的详细信息，请参阅[NT 内核记录器常量](http://go.microsoft.com/fwlink/p/?LinkID=212229&clcid=0x409)。

<a href="" id="clientcontext"></a>**ClientContext**  
此成员集计算每个事件日志记录的时间戳时使用的时钟分辨率。 有关此成员的默认值是查询性能计数器。

您可以指定下列值之一︰

-   **1:**查询性能计数器 (QPC)。 QPC 提供高分辨率 （100 纳秒） 的时间戳，但检索相对更高。 如果您具有事件率或使用者合并不同的缓冲区中的事件，请使用此分辨率。 在较旧的计算机上的时间戳可能不准确因为计数器有时会跳过向前因为硬件有错误。

-   **2:**系统时间。 系统时间提供了一个低分辨率 （10 毫秒） 的时间戳，但检索成本相对较低。 如果事件的数量很大，对于系统的时间分辨率可能不足够精细，以确定事件的顺序。 在这种情况下的一组事件将具有相同的时间戳，但在其中 ETW 提供这些事件的顺序可能不正确。

-   **3:**CPU 周期计数器。 CPU 计数器提供了高分辨率的时间戳，最便宜要检索。 但是，CPU 计数器是不现实的而且不应在生产环境中使用。 例如，在某些计算机上，计时器频率由于热量和电源更改时，除了在某些州停止更改。 如果您的硬件不支持这种时钟类型，ETW 将使用系统时间。 在 Windows Server 2003，Windows XP SP1 和 Windows XP 中，不支持此值。 在 Windows Server 2003 sp1 和 sp2 的 Windows XP 引入了它。

<a href="" id="flags"></a>**标志**  
此成员必须包含 WNODE\_标志\_跟踪\_GUID，以指示该结构包含事件跟踪信息并将信息发送到记录器。 WNODE\_标志\_跟踪\_在 Evntrace.h 中定义 GUID。

以下事件\_跟踪\_还必须设置属性成员︰

<a href="" id="logfilemode"></a>**LogFileMode**  
表示模式将被用于在内核事件跟踪会话日志记录。 此成员用于指定事件都写入到日志文件、 实时使用者，或两者。

该成员还可以用于指定会话是一个专用的记录器会话。 可以指定一个或多个模式。 有关可能的模式的列表，请参阅[日志记录模式的常数](https://msdn.microsoft.com/library/windows/desktop/aa364080.aspx)。

**请注意**  
不要指定实时记录，除非有实时消费者准备要使用的事件。 如果不有任何实时的消费者，事件写入播放文件。 播放文件的大小是有限的。 如果达到此限制时，任何新的事件不记录到日志文件或播放文件。 日志记录功能失败，此时状态\_日志\_文件\_完整。

 

<a href="" id="enableflags"></a>**EnableFlags**  
此成员只用于 NT 内核记录器会话。 它标识内核记录器的跟踪事件。 通过使用逻辑**OR**，此成员可以包含一个或多个值。 指定的事件，除了内核记录器也记录硬件配置事件。

以下跟踪控制标志所提供的事件除了有\_跟踪\_属性︰

-   [事件\_跟踪\_标志\_调度程序](https://msdn.microsoft.com/library/dn640677.aspx)

-   [事件\_跟踪\_标志\_虚拟\_分配](https://msdn.microsoft.com/library/dn631804.aspx)

<a href="" id="logfilenameoffset"></a>**LogFileNameOffset**  
此数字表示从内存的起始位置的偏移量分配到包含日志文件名称以空值终止的字符串的开头的结构。

以下注意事项︰

-   应为文件扩展名.etl。

-   路径中的所有文件夹必须都存在。

-   路径可以是相对的、 绝对的、 局部的或远程。

-   路径不得包含环境变量，因为这些变量都没有展开。

-   启动跟踪的用户必须具有写入权限的文件夹。

-   日志文件名被限制为 1024年个字符。

-   如果您将**LogFileMode**设置为事件\_跟踪\_专用\_记录器\_模式或事件\_跟踪\_文件\_模式\_NEWFILE，确保分配足够的内存来包括追加到专用记录器会话和添加到日志文件序列号的文件名称的进程标识符使用来创建新的文件日志模式。

-   如果您不希望将事件记录到日志文件 (例如，您可以指定事件\_跟踪\_真正\_时间\_仅模式)，将**LogFileNameOffset**设置为零。 如果您指定仅实时记录，还提供一个有效的日志文件的名称偏移量日志文件名称用于创建连续的日志文件到日志文件和日志事件。 如果**LogFileMode**为零，并且提供一个有效的日志文件的名称偏移量，还会创建连续的日志文件。

-   如果您想要将事件记录到日志文件，您必须分配足够的内存供该结构包含的日志文件名和后结构的会话名称。 该日志文件名称必须遵循在内存中的会话名称。

-   使用默认的安全描述符，即日志文件将作为父目录的 ACL 创建跟踪文件。 如果您想要限制对文件的访问权限，请使用适当的 Acl 创建父目录。

<a href="" id="loggernameoffset"></a>**LoggerNameOffset**  
此成员从一开始到 null 结尾的字符串，其中包含会话名称的开头的结构分配的内存中表示的偏移量。

以下注意事项︰

-   会话名称不能超过 1024年个字符。

-   会话名称不区分大小写，并且必须是唯一的。

-   时为此结构分配内存，则必须保留足够的内存包括会话名称和日志文件下面结构的名称。

-   会话名称必须放在内存中的日志文件名之前。 日志文件名称必须被复制到对方的区域。 此函数将写入由内核的会话名称\_记录器\_名。

根据选择的日志文件的类型，可能需要设置**MaximumFileSize**成员。

**请注意**  
不需要因为此函数总是使用内核设置记录器名称**LoggerNameOffset** \_记录器\_调用 StartKernelTrace 的名称值。 此函数将检查是否有**Wnode.Guid**与**SystemTraceControlGuid**;如果不是，它将返回错误\_无效\_参数。 如果**Wnode.Guid**与**KernelRundownGuid**相对应，应指定的记录器名称。 **KernelRundownGuid**是用来记录事件，如现有进程信息，线程信息，每个进程加载的图像的 GUID 的硬件配置，如 CPU、 视频、 磁盘、 网络卡、 服务、 电源，插和磁盘 IDE 通道。

 

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


如果**StackTracingEventIds**包含在**事件中未启用的事件\_跟踪\_属性。EnableFlags**字段或无法解码通过内核跟踪控制，这些标志将被忽略，并返回错误代码。

**要求︰**

**版本︰**可用于在 Windows Vista 中开始。 这种结构被随 Windows 性能分析器。

**标头︰**在 KernelTraceControl.h 中声明。 包括 KernelTraceControl.h。

**库︰**包含在 KernelTraceControl.dll 中。

## <a name="related-topics"></a>相关的主题


[函数](functions-wpa.md)

[自定义注入的系统信息](custom-injection-of-system-information.md)

 

 







