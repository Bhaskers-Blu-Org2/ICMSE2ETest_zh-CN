---
title: Stack
description: Stack
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 21653c0c-ed2b-45d2-aecb-872eac23d3dd
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: cbddd13ceaf1b8494e89b9c09af0c807eac62984
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="stack"></a>Stack


介绍了叠被启用内核事件。

## <a name="element-hierarchy"></a>元素层次结构


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;[SystemProvider](systemprovider.md)&gt;

               &lt;[Stacks](stacks.md)&gt;

                    &lt;**Stack**&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;[SystemCollectorId](systemcollectorid.md)&gt;

                         &lt;[SystemProviderId](systemproviderid.md)&gt;

                                &lt;[Stacks](stacks.md)&gt;

                                     &lt;**Stack**&gt;

                          &lt;[SystemProvider](systemprovider.md)&gt;

                                &lt;[Stacks](stacks.md)&gt;

                                     &lt;**Stack**&gt;

## <a name="syntax"></a>语法


``` syntax
<Stack Value = "AlpcClosePort" | "AlpcConnectFail" | "AlpcConnectRequest" ...>
</Stack>
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
<td><p>指示系统堆栈。</p></td>
<td><p>有关可能值，请参阅备注部分。</p></td>
<td><p>是</p></td>
<td><p></p></td>
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
<td><p>[堆栈](stacks.md)</p></td>
<td><p>表示堆栈的集合。</p></td>
</tr>
</tbody>
</table>

 

## <a name="remarks"></a>备注


下表描述了**值**属性的可能值。

**AlpcClosePort**

高级的本地过程调用 (ALPC) 关闭端口信息。

**AlpcConnectFail**

ALPC 连接失败的消息。

**AlpcConnectRequest**

ALPC 连接请求。

**AlpcConnectSuccess**

ALPC 连接请求成功。

**AlpcReceiveMessage**

ALPC 消息被接收。

**AlpcSendMessage**

ALPC 消息已发送。

**AlpcUnwait**

ALPC 等待请求已取消。

**AlpcWaitForNewMessage**

ALPC 等待新消息请求。

**AlpcWaitForReply**

ALPC 等待答复的请求。

**CcCanIWriteFail**

**CcFlushCache**

**CcFlushSection**

**CcLazyWriteScan**

**CcReadAhead**

**CcWorkitemComplete**

**CcWorkitemDequeue**

**CcWorkitemEnqueue**

**CcWriteBehind**

**ContiguousMemoryGeneration**

连续内存的生成的事件。

**CSwitch**

上下文切换。

**DiskFlushInit**

初始化磁盘刷新。

**DiskReadInit**

初始化的磁盘读取操作。

**DiskWriteInit**

初始化的磁盘写操作。

**ExecutiveResource**

行政资源的操作。

**FileCleanup**

文件清理。

**宏**

关闭的文件。

**文件**

创建一个文件。

**文件删除**

删除文件。

**FileDirEnum**

枚举的文件目录。

**FileDirNotify**

更改目录控制中断请求过程附带目录通知小代码时，会记录一个文件 I/O 事件。

**FileFlush**

刷新文件。

**FileFSCTL**

文件系统控制操作。

**FileOpEnd**

文件操作的结束。

**FileQueryInformation**

查询文件的信息。

**FileRead**

从文件读取。

**FileRename**

重命名的文件。

**FileSetInformation**

文件信息中的更改。

**FileWrite**

写入到一个文件。

**HardFault**

硬盘故障。

**HeapAllocation**

堆分配。

**HeapCreate**

堆集的创建。

**HeapDestroy**

销毁的堆。

**HeapFree**

释放的堆。

**HeapRangeCreate**

创建一堆系列。

**HeapRangeDestroy**

销毁的堆范围。

**HeapRangeRelease**

堆范围的发行。

**HeapRangeReserve**

已保留堆范围。

**HeapReallocation**

重新分配的堆。

**ImageLoad**

已加载图像。

**ImageUnload**

图像已被卸载。

**KernelQueueEnqueue**

事情已添加到内核队列。

**KernelQueueDequeue**

事情已从核心队列。

**KernelSignal**

**KernelSignalInit**

**KernelSync**

**KernelSyncAll**

**KernelWaitSync**

**KernelWaitSyncAll**

**映射文件**

映射文件。

**标记**

**MiniFilterPostOpInit**

**MiniFilterPreOpInit**

**PageAccess**

对页的访问。

**PagefaultAV**

访问冲突页面错误。

**PagefaultCopyOnWrite**

写入时拷贝的页面错误。

**PagefaultDemandZero**

要求零页面错误。

**PagefaultGuard**

故障时保护页。

**PagefaultHard**

硬页错误。

**PagefaultTransition**

切换页面错误。

**PagefileBackedImageMapping**

**PagefileMappedSectionCreate**

创建页面文件的映射区域。

**PagefileMappedSectionDelete**

删除的页面文件的映射区域。

**PageRangeAccess**

访问的页面范围。

**PageRangeRelease**

页面范围的发行。

**PageRelease**

版本的页面。

**PoolAllocation**

内存池分配。

**PoolAllocationSession**

会话池分配。

**PoolFree**

释放的内存池分配。

**PoolFreeSession**

释放的会话池。

**PowerDeviceNotify**

电源设备通知。

**PowerDeviceNotifyComplete**

电源设备通知的结束日期。

**PowerIdleStateChange**

空闲状态发生变化。

**PowerPerfStateChange**

电源状态变化，旧的和新的处理器的频率，其中包括它适用于处理器。

**PowerPostSleep**

该设备从休眠状态中已经出现了。

**PowerPreSleep**

该设备正在进入睡眠状态。

**PowerSessionCallout**

核心是要执行的电源转换。

**PowerSessionCalloutReturn**

**PowerSessionCallout**已完成，并将记录状态或错误。

**PowerSetDevicesState**

设置设备的电源状态。

**PowerSetDevicesStateReturn**

**PowerSetDevicesState**已完成，并将记录状态或错误。

**PowerSetPowerAction**

电源操作的设置。

**PowerSetPowerActionReturn**

指示电源操作后的状态。

**PowerThermalConstraint**

更改热量约束或首字下沉的设备事件。

**ProcessCreate**

已创建一个进程。

**ProcessDelete**

进程已被删除。

**SampledProfile**

表明样本配置文件。

**SampledProfileSetInterval**

采样间隔的配置文件的设置。

**ReadyThread**

就绪的线程的事件。

**RegistryCloseKey**

关闭注册表项。

**RegistryCreateKey**

创建注册表项。

**RegistryDeleteKey**

删除的注册表项。

**RegistryDeleteValue**

删除注册表值。

**RegistryEnumerateKey**

该注册表项的枚举。

**RegistryEnumerateValueKey**

注册表项的值的枚举。

**RegistryFlush**

注册表刷新。

**RegistryKcbCreate**

创建注册表键控制块。

**RegistryKcbDelete**

删除的注册表项控制块。

**RegistryOpenKey**

打开注册表项。

**RegistryQueryKey**

该注册表项的查询。

**RegistryQueryMultipleValue**

多个注册表值的查询。

**RegistryQuerySecurity**

一种查询注册表的安全设置。

**RegistryQueryValue**

注册表值的查询。

**RegistrySetInformation**

设置的注册表信息。

**RegistrySetSecurity**

正在设置注册表安全性。

**RegistrySetValue**

正在设置注册表值。

**RegistryVirtualize**

对注册表虚拟化。

**SplitIO**

指示已拆分为单独的数据包的 I/O。

**SystemCallEnter**

系统调用的开始处。

**SystemCallExit**

系统调用的结束。

**ThreadCreate**

线程的创建。

**ThreadDCEnd**

结束的线程的设备上下文。

**ThreadDCStart**

线程的设备上下文的开始日期。

**ThreadDelete**

删除的某个线程。

**ThreadPoolCallbackCancel**

正在取消线程池回调。

**ThreadPoolCallbackDequeue**

从队列中移除回调线程池。

**ThreadPoolCallbackEnqueue**

在队列中放置一个线程池的回调。

**ThreadPoolCallbackStart**

线程池回调的开头。

**ThreadPoolCallbackStop**

线程池回调结束。

**ThreadPoolClose**

线程池的关闭。

**ThreadPoolCreate**

创建的线程池。

**ThreadPoolSetMaxThreads**

设置线程池中的最大线程数。

**ThreadPoolSetMinThreads**

设置线程池中的线程的最小数目。

**ThreadSetBasePriority**

设置线程的基本优先级。

**ThreadSetPriority**

设置线程的优先级。

**TimerPeriodic**

定期计时器事件。

**TimerOnShot**

一劳永逸的计时器事件。

**UnMapFile**

取消映射的文件。

**VirtualAllocation**

分配虚拟内存。

**VirtualFree**

虚拟释放内存。

 

## <a name="related-topics"></a>相关的主题


[元素](elements.md)

 

 







