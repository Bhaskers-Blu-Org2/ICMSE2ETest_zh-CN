---
title: "关键字 （在 SystemProvider)"
description: "关键字 （在 SystemProvider)"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: afe8e6db-f5ad-4a94-9878-97840f91b8b2
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: cc635aaccce829e7cc184b0f0c32980c97d6e37f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="keyword-in-systemprovider"></a>关键字 （在 SystemProvider)


描述可用于内核模式会话的核心标志。

## <a name="element-hierarchy"></a>元素层次结构


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;[SystemProvider](systemprovider.md)&gt;

               &lt;[Keywords (in SystemProvider)](keywords--in-systemprovider-.md)&gt;

                    &lt;**Keyword (in SystemProvider)**&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;[SystemCollectorId](systemcollectorid.md)&gt;

                         &lt;[SystemProviderId](systemproviderid.md)&gt;

                                &lt;[Keywords (in SystemProvider)](keywords--in-systemprovider-.md)&gt;

                                     &lt;**Keyword (in SystemProvider)**

                         &lt;[SystemProvider](systemprovider.md)&gt;

                                &lt;[Keywords (in SystemProvider)](keywords--in-systemprovider-.md)&gt;

                                     &lt;**Keyword (in SystemProvider)**

## <a name="syntax"></a>语法


``` syntax
<Keyword Value = "AllFaults" | "CompactCSwitch" | "ContiguousMemorygeneration" | ... >
</Keyword>
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
<td><p>介绍了系统跟踪 Windows 事件 (ETW) 事件。</p></td>
<td><p>请参见备注部分中有关可能的值。</p></td>
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
<td><p>[关键字 （在 SystemProvider)](keywords--in-systemprovider-.md)</p></td>
<td><p>表示一个系统关键字集合。</p></td>
</tr>
</tbody>
</table>

 

## <a name="remarks"></a>备注


下表描述了**值**属性的可能值。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>值</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>AllFaults</p></td>
<td><p>记录所有错误。</p></td>
</tr>
<tr class="even">
<td><p>CompactCSwitch</p></td>
<td><p>使用门户的&quot;CSwitch&quot;，这减少了为每个 CSwitch，记录的信息，以及使用差分压缩和批处理。</p></td>
</tr>
<tr class="odd">
<td><p>ContiguousMemorygeneration</p></td>
<td><p>记录中的连续内存代。</p></td>
</tr>
<tr class="even">
<td><p>CpuConfig</p></td>
<td><p>在 CPU 配置更改都记录。</p></td>
</tr>
<tr class="odd">
<td><p>CSwitch</p></td>
<td><p>上下文开关活动被记录下来。</p></td>
</tr>
<tr class="even">
<td><p>DiskIO</p></td>
<td><p>磁盘 I/O 被记录下来。</p></td>
</tr>
<tr class="odd">
<td><p>DiskIOInitialization</p></td>
<td><p>初始化磁盘 I/O 被记录下来。</p></td>
</tr>
<tr class="even">
<td><p>DPC</p></td>
<td><p>记录了延迟的过程调用。</p></td>
</tr>
<tr class="odd">
<td><p>驱动程序</p></td>
<td><p>驱动程序活动被记录下来。</p></td>
</tr>
<tr class="even">
<td><p>FileIO</p></td>
<td><p>记录文件 I/O。</p></td>
</tr>
<tr class="odd">
<td><p>FileIOInit</p></td>
<td><p>记录文件 I/O 初始化。</p></td>
</tr>
<tr class="even">
<td><p>文件名</p></td>
<td><p>将记录中的文件的名称。</p></td>
</tr>
<tr class="odd">
<td><p>占地面积</p></td>
<td><p>用于进行内存分析，此选项指定要刷新工作集中在一个特殊的刷新标记。</p></td>
</tr>
<tr class="even">
<td><p>HardFaults</p></td>
<td><p>记录硬盘故障。</p></td>
</tr>
<tr class="odd">
<td><p>IdleStates</p></td>
<td><p>记录空闲状态。</p></td>
</tr>
<tr class="even">
<td><p>中断</p></td>
<td><p>记录的中断。</p></td>
</tr>
<tr class="odd">
<td><p>KernelQueue</p></td>
<td><p>核心队列的更改记录。</p></td>
</tr>
<tr class="even">
<td><p>加载程序</p></td>
<td><p>内核和用户模式下加载和卸载事件记录。</p></td>
</tr>
<tr class="odd">
<td><p>Memory</p></td>
<td><p>提供有关物理内存使用情况的事件。</p></td>
</tr>
<tr class="even">
<td><p>MemoryInfo</p></td>
<td><p>提供有关内存管理器，例如数免费、 使用基本信息和备用页，等等。</p></td>
</tr>
<tr class="odd">
<td><p>池</p></td>
<td><p>内存池的更改记录。</p></td>
</tr>
<tr class="even">
<td><p>Power</p></td>
<td><p>记录中的功率消耗。</p></td>
</tr>
<tr class="odd">
<td><p>ProcessCounter</p></td>
<td><p>表示配置文件中进程计数器。</p></td>
</tr>
<tr class="even">
<td><p>ProcessThread</p></td>
<td><p>进程和线程的创建和删除事件记录。</p></td>
</tr>
<tr class="odd">
<td><p>ReadyThread</p></td>
<td><p>就绪的线程事件记录。</p></td>
</tr>
<tr class="even">
<td><p>注册表</p></td>
<td><p>对注册表的更改记录。</p></td>
</tr>
<tr class="odd">
<td><p>SampledProfile</p></td>
<td><p>采样配置文件。</p></td>
</tr>
<tr class="even">
<td><p>自旋锁</p></td>
<td><p>自旋锁信息记录。</p></td>
</tr>
<tr class="odd">
<td><p>SplitIO</p></td>
<td><p>提供有关拆分 I/O 请求的事件。 可将单个 I/O 请求拆分为多个请求，因为磁盘碎片或其他原因。</p></td>
</tr>
<tr class="even">
<td><p>SystemCall</p></td>
<td><p>记录的系统调用。</p></td>
</tr>
<tr class="odd">
<td><p>ThreadPriority</p></td>
<td><p>线程优先级的更改记录。</p></td>
</tr>
<tr class="even">
<td><p>Timer</p></td>
<td><p>提供有关系统计时器事件。</p></td>
</tr>
<tr class="odd">
<td><p>VirtualAllocation</p></td>
<td><p>虚拟内存分配被记录下来。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[元素](elements.md)

[CustomKeyword](customkeyword.md)

 

 







