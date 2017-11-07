---
title: "启用堆数据捕获"
description: "启用堆数据捕获"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 73d49914-7f60-426e-9833-cee7c5ec5d10
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: b07e44edbd1c4c12769be2e824451a4ef9637717
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="enabling-heap-data-capture"></a>启用堆数据捕获


流程堆分析叠收集捕获**HeapAlloc**和**HeapRealloc**事件时最有效。 要解码与符号的堆栈，您必须启用符号进行解码。 进程启动时或在现有进程，您可以捕获堆数据。

## <a name="to-enable-data-capture-when-a-process-is-started"></a>若要启用数据捕获时进程已启动


本示例启动正在从命令行启动数据捕获的序列分析的过程。 进程启动时启用数据捕获保证没有分配信息或历史记录不会丢失。 采用以下步骤来启用数据捕获进程启动︰

1.  从提升的命令提示符下，键入以下命令︰`xperf -on Base -BufferSize 1024 -MinBuffers 10 -MaxBuffers 16`

2.  下面是一个示例命令︰`xperf -start HeapSession -heap -PidNewProcess "C:\Program Files\Windows Sidebar\sidebar.exe" -BufferSize 1024 -MinBuffers 128 -MaxBuffers 128 -stackwalk HeapAlloc+HeapRealloc`

    在桌面上打开边栏。

    下表描述了这些命令。

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>命令</th>
    <th>说明</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>-启动 HeapSession</p></td>
    <td><p>初始化跟踪会话或记录器会话。 在这种情况下该会话被命名为&quot;HeapSession&quot;。</p></td>
    </tr>
    <tr class="even">
    <td><p>-堆</p></td>
    <td><p>标识&quot;HeapSession&quot;作为堆跟踪。</p></td>
    </tr>
    <tr class="odd">
    <td><p>-PidNewProcess</p></td>
    <td><p>初始化进程。 在这种情况下，初始化 Windows 边栏。</p></td>
    </tr>
    <tr class="even">
    <td><p>-BufferSize</p></td>
    <td><p>设置在其中存储事件数据的缓冲区的缓冲区大小。 最佳的缓冲区大小为 1024 KB。 默认值是 64 KB。</p></td>
    </tr>
    <tr class="odd">
    <td><p>-MinBuffers</p></td>
    <td><p>设置事件存储数据的缓冲区的最小数量。 <strong>MinBuffers</strong>应等于<strong>MaxBuffers</strong>以保证跟踪之间的一致性。</p></td>
    </tr>
    <tr class="even">
    <td><p>-MaxBuffers</p></td>
    <td><p>因为缓冲区分配的非分页内存中，这是一种有限的系统资源，分配<strong>MaxBuffers</strong> 。</p></td>
    </tr>
    <tr class="odd">
    <td><p>-stackwalk</p></td>
    <td><p>初始化 stackwalk 设施收集分配和解除分配信息并将该信息与特定的线程相关联。</p></td>
    </tr>
    <tr class="even">
    <td><p>HeapAlloc + HeapRealloc</p></td>
    <td><p>标识特定堆可以捕获并显示的 stackwalk 设施的事件。</p></td>
    </tr>
    </tbody>
    </table>

     

3.  键入以下命令︰`xperf -stop -stop HeapSession -d HeapTrace.etl`

    `-d HeapTrace.etl`命令合并跟踪会话中生成的 HeapTrace.etl 文件中。

## <a name="to-enable-data-capture-on-an-existing-process"></a>若要启用现有的进程数据捕获


此选项使数据捕获，而无需停止并重新启动该进程。 正在分析的情况没有发生之前以及之后在应用程序启动，和初始不需要堆分配 （它会生成非常大的跟踪文件） 时，这可能更加有利。

执行以下步骤︰

1.  从提升的命令提示符下启动 NT 内核记录器的基本标志，如下所示︰`xperf -on BASE`

2.  若要启用现有的进程的堆跟踪，替换为实际进程 ID *XXX*在下面的命令︰`xperf -start HeapSession -heap -Pid XXX -BufferSize 1024 -MinBuffers 128 -MaxBuffers 128 -stackwalk HeapAlloc+HeapRealloc`

3.  准备跟踪分析以相同的方式正如在已开始处理时数据捕获︰`xperf -stop -stop HeapSession -d heapTrace.etl`

## <a name="related-topics"></a>相关的主题


[堆](heap.md)

 

 







