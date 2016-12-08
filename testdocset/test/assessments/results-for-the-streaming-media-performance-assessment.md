---
title: "流式媒体性能评估的结果"
description: "流式媒体性能评估的结果"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 238eba8e-fe97-4422-be7a-88e4e232de8a
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: f421fe7cece1fc2f86d13579cccaddd70b9dc3fb
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="results-for-the-streaming-media-performance-assessment"></a>流式媒体性能评估的结果


流式媒体性能评估服务可帮助您评估和提高流媒体性能的计算机。 此评估使用流式已部署的服务器应用程序在本地计算机或远程服务器上。 评估启动 Internet Explorer® 10 并播放媒体内容从开始到结束或在指定的时间。 然后，关闭 Internet Explorer 将生成结果。

本主题提供了对于理解流式媒体除了指导如何使用这些结果来识别和解决对流式媒体体验产生负面影响的公共问题的性能评估结果的指导。 虽然 Internet Explorer 用作流客户端在此分析中，可以应用在本主题中讨论的技术来提高 Windows 上一般的流媒体体验。

本主题︰

-   [目标文件](#bkmk-goals)

-   [指标](#bkmk-metrics)

-   [问题](#bkmk-streamingissues)

有关此评估、 系统要求和评估设置的详细信息，请参阅[流式媒体性能](streaming-media-performance.md)。

## <a name="a-href-idbkmk-goalsagoals-file"></a><a href="" id="bkmk-goals"></a>目标文件


您可以创建自定义的目标来衡量结果视图中的您改进。 目标文件是会审的工具，可帮助您了解 PC 的性能如何，比较 Pc 业务中。

例如，基本的便携式计算机目标可能不同于为高端桌面计算机设置的目标或者市场预期可能会更改所需的灵活性，可以定义不同类型的目标和时间的推移和技术的关键要求提高的方式中。

度量值是与该指标的目标相比，状态都用颜色编码在结果视图中，如下所示︰

-   浅紫色意味着系统具有出色的用户体验，有没有感觉到的问题。

-   紫色的中等意味着用户体验是容许，可以优化系统。 检查以查看可对系统进行何种改进的建议和分析。 这可能是软件更改，更改配置或硬件更改。

-   深紫色意味着系统有很差的用户体验，并且有重大改进的空间。 检查以查看可对系统进行改进的建议和分析。 这可能是软件更改，更改配置或硬件更改。 您可能需要考虑进行权衡，以便提供 Windows 遇到的高质量。

-   没有颜色的含义有没有定义为度量的目标。

**请注意**  
在 Windows 评估 Toolkit 针对 Windows 8，某些评估包括默认目标文件。 查看使用此版本的工具，结果在第一次使用该默认目标文件。 但是，您还可以定义自定义目标针对 Windows 8 相同的方式，可以为 Windows 8.1 和 Windows 10。

 

您可以设置文件位置的目标并将目标文件添加到该位置之前可用于用户界面应用的自定义目标。 选择目标文件后，它将继续是目标文件，用于打开的任何结果。

可每次只能有一个目标文件。 所有的评估的目标是单个目标文件中设置的。 评估工具将搜索顺序如下目标︰

1.  自定义的目标文件

2.  在结果文件中定义的目标

3.  评估清单中定义的目标

您可以在 %PROGRAMFILES%使用提供了该示例的目标文件\\窗口工具包\\10\\评估和部署工具包\\Windows 评估 Toolkit\\SDK\\样本\\目标来创建目标文件。

**请注意**  
不能包装作业的目标文件，但可以将其存储在供其他用户使用共享。

 

## <a name="a-href-idbkmk-metricsametrics"></a><a href="" id="bkmk-metrics"></a>指标


流式媒体性能评估报告标准音频和视频的故障。 而不是直接汇报的计数的视频时遇到的难题，根据人类认知分类失灵。 大多数人开始觉察视频和音频进行的 80ms年到 160ms年范围内同步输出。 在此时间范围内，计算之前可以察觉到，可以在每秒 30 帧视频中的小故障的连续帧的数量。 基于连续有失灵的帧数，视频失灵归类为主要媒介或次要失灵，如下所示︰

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>失灵的连续帧的计数</th>
<th>小故障分类</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1</p></td>
<td><p>小小故障</p></td>
</tr>
<tr class="even">
<td><p>2-4</p></td>
<td><p>中等的小故障</p></td>
</tr>
<tr class="odd">
<td><p>&gt;= 5</p></td>
<td><p>主要问题</p></td>
</tr>
</tbody>
</table>

 

评估工作负载的 60 秒播放持续时间可以分为 60 秒。 每个时间间隔基于间隔中发生的故障的类型，属于大、 中、 次要、 无故障间隔。 例如，一个中型的小故障间隔是一中至少一个中型的小故障发生，但没有重大故障已注意到。 同样一个小小故障间隔是一个在其中至少一个小小故障发生，但注意到没有中或主要失灵。

默认情况下，这一评估运行 3 迭代的工作负荷。 但是，视频播放 3 迭代过程 5 次。 第一次迭代是初始化 Internet Explorer，然后有 3 视频回放的计算度量值。 评估结果是最后一次迭代。

-   **迭代的培训**。 这是为了确保 Internet Explorer DLL 被加载的第一个迭代。

-   **定时迭代**。 这些迭代作为度量值的基础。 度量值是这些三个迭代的平均值。 默认情况下，60 秒的流三个完整的迭代生成用于计算度量值的 StreamingMediaAssessment.etl 跟踪文件。 这些迭代过程只浅启用了日志记录来减少生成的指标检测的系统开销。 因此，详细的诊断事件不会收集该跟踪文件中。

-   **分析迭代**。 此迭代收集信息，同时评估正在运行，并且用作基础生成的评估问题。 这是流的 60 秒内完全迭代。 在该迭代期间启用详细日志记录以收集详细的诊断信息。 在这次迭代 (StreamingMediaAssessmentDiagTrace.etl) 中生成的跟踪文件是由评估检测系统上常见的与媒体相关的问题分析。

在用户界面中的详细信息窗格中提供了跟踪文件的链接。 若要查看单个的迭代中，在结果视图中的值用鼠标右键单击结果列标题，然后选择**显示迭代**。

## <a name="a-href-idbkmk-streamingissuesaissues"></a><a href="" id="bkmk-streamingissues"></a>问题


此评估执行高级的问题分析，并提供到 Windows 性能分析器 (WPA) 标识问题进行故障排除的链接。 在大多数情况下，您可以选择 WPA 深入分析链接来解决出现的问题。 WPA 打开时，可能还会有其他详细信息的磁盘活动或 CPU 活动可用根据问题的类型。 深入分析的问题和建议有关的详细信息，请参阅[In-Depth 分析的常见问题](common-in-depth-analysis-issues.md)。

评估服务启动时，它执行某些初步的计算机上检查，以确保可以跨不同的评估使用生成一致的结果。 如果评估运行之前警告得不到解决，各种警告会出现在评估结果。 完成流式媒体评估，基于自动分析诊断跟踪文件的后评估生成公共媒体问题在系统中发现的问题。 在 WPA 可以分析这些问题。 除了处理的生成的问题，其他的手动分析可以执行诊断跟踪文件使用 WPA 和 GPUView，包含在 Windows 性能 Toolkit 的工具。

本部分包括︰

-   [常见的问题](#bkmk-streamingproblems)

-   [预检查警告](#bkmk-precheck)

-   [生成的问题分析](#bkmk-streaminganalyze)

-   [相关的难题](#bkmk-streamingglitches)

-   [软件与硬件解码](#bkmk-streamingsoftware)

-   [高 GPU 利用率](#bkmk-streaminggpu)

-   [评估报告的退出代码为 0x80050006](#exitcode)

### <a name="a-href-idbkmk-streamingproblemsacommon-problems"></a><a href="" id="bkmk-streamingproblems"></a>常见的问题

一些音频故障的主要原因包括︰

-   **长时间运行的中断服务例程 (ISR) 和延迟的过程调用 (DPC)**

    ISR 是一个设备驱动程序例程，内核中断调度程序将控制权移交给当设备发出中断。 在 Windows I/O 模型中，Isr 运行以高设备中断请求等级 (IRQL)，以便他们执行很少的工作，尽量避免不必要地阻止低等级中断。 ISR 通常排队 DPC，运行在较低的 IRQL，执行中断处理的其余部分。 Dpc 不应运行超过 100 微秒，Isr 不应运行时间超过 25 微秒。 除了其他系统的性能影响，长时间运行 Isr 和 Dpc 可能导致音频故障会导致音频引擎延迟。 ISR 或运行持续时间大于 1 毫秒到 3ms 的 DPC 可能会影响系统的介质性能。 类似于长时间运行 Isr 和 Dpc、 频繁 Isr 和 Dpc （ISR/DPC 风暴） 可以有类似对性能的影响。 通常在网络、 存储和图形驱动程序中找到此类 ISR 和 DPC 的问题。 评估时间大于 3ms 长时间运行的 ISR DPC，可 1 毫秒到 3ms 和错误之间生成一个警告。 有关详细信息，请参阅[分析生成的问题](#bkmk-streaminganalyze)。

-   **在派单级别下运行的内核工作线程**

    除了 Dpc 一些内核线程可能同时运行派遣级别 (IRQL = 2)。 同样这也可能导致音频故障所导致的延迟。 为了检测这种情况下，查找低优先级系统线程的运行不间断长时间而不被抢占。

-   **客户端一侧挨饿**

    这是当源无法读取从磁盘或网络速度不够快，才能跟上实时解码和呈现。 例如，磁盘可能限定由硬页错误，因此无法从磁盘中更快地读取样本比实时的方式。

顶部的视频失灵原因如下所示︰

1.  **下游的瓶颈**︰ 源不足 （限定磁盘）

2.  **中途瓶颈**︰ 解码器透支 （软件或硬件解码器限定）

3.  **上游的瓶颈**︰ GPU 是限定或遇到慢内存传输

### <a name="a-href-idbkmk-precheckapre-check-warnings"></a><a href="" id="bkmk-precheck"></a>预检查警告

在开始之前 （流式视频） 的评估，流媒体性能评估系统上运行一些预先检查。 当这些预先检查失败时，评估生成错误和警告。 虽然错误阻止运行评估，警告非阻塞并允许继续评估。 一些重要的前检查，对评估结果的影响如下所示︰

-   **交流电源是必需的 （警告）**

    我们建议运行流媒体性能评估上的计算机使用交流电源，因为某些设备在计算机上的运行在电池上时可以缩小影响评估结果。

-   **运行带有 VGA 驱动程序不建议 （警告）**

    缺少显示驱动程序，例如 Microsoft 基本显示驱动程序，可能会导致其他视频失灵。 要获得准确的结果，请确保正确的显示驱动程序的安装前运行评估。 有关驱动程序的其他详细信息，运行[驱动程序验证](driver-verification.md)评估。

-   **建议运行活动音频呈现设备不是没有 （警告）**

    如果系统上没有音频呈现设备，一些与音频相关评估结果可能不准确。 如果您有音频设备，为其安装驱动程序之前运行评估。 如果计算机没有内置扬声器，将耳机或扬声器连接到计算机以解决此警告的音频输出端口。

-   **远程会话不建议 （警告）**

-   若要获得更精确的结果，我们建议评估 （而不是使用远程桌面会话） 的计算机上本地运行。

-   **多显示器 （警告）**

    若要获得更精确的结果，我们建议只连接一个显示器的计算机上运行评估。 由于评估启动 Internet Explorer 在 kiosk 模式下 （全屏幕），在单个监视器系统上，Internet Explorer 是合成到桌面将顶级窗口。 在多显示器的计算机，可能会有其他的顶级窗口。 这会影响评估结果。

### <a name="a-href-idbkmk-streaminganalyzeaanalyzing-generated-issues"></a><a href="" id="bkmk-streaminganalyze"></a>生成的问题分析

在大多数情况下，您可以选择 WPA 深入分析链接生成问题进行故障排除。 此操作将打开 StreamingMediaAssessmentDiagTrace.etl 在 WPA 使用适当的配置文件，来分析问题。 在 WPA，您可以展开中**问题详细信息和区域的调查**以缩小问题范围的问题。 深入分析的问题和建议有关的详细信息，请参阅[In-Depth 分析的常见问题](common-in-depth-analysis-issues.md)。

### <a name="a-href-idbkmk-streamingglitchesacorrelating-glitches"></a><a href="" id="bkmk-streamingglitches"></a>相关的难题

分析完之后生成的评估的问题，可以通过在 WPA，打开诊断跟踪，然后使用**流媒体分析**链接执行其他分析。 这将启动 WPA 的适合于流媒体跟踪分析的视图。

第一个表感兴趣的是**活动**提供了评估的分析迭代过程中发生的活动 （或称区间） 的分层视图。 例如，可以检查以下时间间隔︰

-   流媒体评估 – 根间隔的评估中，跨越整个跟踪。

-   流式媒体评估迭代 – 在每个迭代跟踪文件; 在评估的时间间隔默认情况下只有一个迭代包含诊断跟踪。

-   工作负载 – 为每个视频在迭代中的工作负荷的时间间隔。 默认情况下，唯一的 1080p 工作负荷为存在。

-   媒体引擎寿命 – 工作负荷视频流式处理的时间间隔。

当发现跟踪感兴趣的间隔时，WPA，在选择的时间间隔和缩放到所选内容以缩小分析。

**一般事件**表中可查看记录的小故障事件 （底部最表在 WPA 的分析选项卡上）。 选择一般事件表中预设的**小故障事件**进行筛选所需的小故障。 在跟踪中有多个小故障事件表示系统上的相对不良流体验。 要分析这些失灵的原因，请尝试将它们关联起来的 WPA 中其他汇总表的图表。 通过与其他汇总表关联的小故障事件，可以发现系统中可能出现的问题。

### <a name="a-href-idbkmk-streamingsoftwareasoftware-vs-hardware-decoding"></a><a href="" id="bkmk-streamingsoftware"></a>软件与硬件解码

可解码 H.264 视频流在此评估中的软件或硬件解码。 如果在系统上的图形卡不支持 H.264 视频的解码，然后软件用于解码。 使用软件，而不是使用 GPU 的 CPU 中执行解码工作。 在这种情况下，可以限定 CPU。 这样，就无法跟上视频流，从而导致故障的实时解码的需要。

使用硬件解码的能力可以通过支持的图形卡的 DXVA2 模式来确定。 DXVA2 模式与 DXVA2\_ModeH264\_VLD 前缀 (如 DXVA2\_ModeH264\_VLD\_FGT) 指示图形卡可以支持硬件解码 H.264 视频。 可以从下面的 XML 元素中的 JobResults XML 文件获取支持的图形卡的 DXVA2 模式︰ /AxeJobResults/ MachineConfiguration/EcoSysInfo/图形/DXVA2Modes。 结果视图详细信息窗格中显示 JobResults XML 文件的位置。

### <a name="a-href-idbkmk-streaminggpuahigh-gpu-utilization"></a><a href="" id="bkmk-streaminggpu"></a>高 GPU 利用率

在限定 GPU 时也可以因上游瓶颈而导致视频失灵。 GPU 利用率可以通过 GPUView 工具中打开的流媒体诊断跟踪进行可视化处理。 GPUView 工具可以读取记录事件跟踪日志 (.etl) 文件中的视频和内核事件，并以图形方式显示数据。 GPUView 工具是 Windows 性能 Toolkit 的一部分，可在以下位置安装后:"%programfiles(x86)%\\窗口工具包\\10\\Windows 性能 Toolkit\\gpuview\\GPUView.exe"。 流式媒体诊断跟踪具有相似的路径:"&lt;作业结果目录&gt;\\000\_StreamingMedia\\StreamingMediaAssessmentDiagTrace.etl"。

可以使用 GPUView 来确定图形处理单元 (GPU) 和中央处理单元 (CPU) 与直接内存访问 (DMA) 缓冲区处理 （以及所有其他视频处理） 上视频硬件的性能。 开发人员和测试人员可以使用 GPUView 来显示不同种类的事件可能导致失灵、 准备延迟和较差的同步等异常情况。 有关如何使用 GPUView 的详细信息，请参阅文档帮助文件，GPUView.chm，安装工具。

### <a name="a-href-idexitcodeathe-assessment-reports-an-exit-code-of-0x80050006"></a><a href="" id="exitcode"></a>评估报告的退出代码为 0x80050006

维护任务已注册的电脑上，但尚未完成之前运行的评估时，将发生此错误。 为维护任务通常会影响评估指标，这样可以防止运行，这样的评估。

要解决此问题，请执行以下任一操作︰

1.  确保计算机已连接到网络和交流电源供电运行。 手动启动，请使用以下命令从提升提示符挂起的维护任务︰

    `rundll32.exe advapi32.dll,ProcessIdleTasks`

2.  禁用定期和空闲状态维护任务，并在运行评估之前停止所有的维护任务。

## <a name="related-topics"></a>相关的主题


[流式媒体性能](streaming-media-performance.md)

[Windows 评估 Toolkit 技术参考](windows-assessment-toolkit-technical-reference.md)

[评估服务](assessments.md)

[深入分析常见问题](common-in-depth-analysis-issues.md)

[连接备用能源效率](connected-standby-energy-efficiency.md)

 

 







