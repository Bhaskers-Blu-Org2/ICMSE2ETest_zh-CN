---
title: "会话"
description: "会话"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: cb2a15ea-3519-4efb-8031-93b19fac10d4
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: a5186b06819c8ea1db76558e7678a65ae2c417d7
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="sessions"></a>会话


Windows 性能记录器 (WPR) 扩展跟踪 Windows 事件 (ETW)。 ETW 日志记录会话是内存中的缓冲区的集合，这些接受通过 ETW 提供程序应用程序编程接口 (API) 的事件。 这些缓冲区通常非分页并由内核。 ETW 将缓冲区分配给每个处理器。 ETW 事件生成和缓冲是无锁以启用 ETW 日志所有种类的事件。

每次该 ETW 调用**EventWrite**方法时，ETW 预留 ETW 已分配给正在运行调用线程的处理器的当前缓冲区中的空间。 然后，ETW 事件头和用户数据复制到该空间。 当缓冲区已满时，ETW 日志记录会话的日志文件或实时流式处理使用者刷新缓冲区。 然后，ETW 将可用缓冲区分配给该处理器。

如果日志记录吞吐量超过刷新器能够释放缓冲区，日志记录会话中的所有可用的缓冲区空间可能会变得不可用。 例如，这可能是因为磁盘写入吞吐量低于传入事件吞吐量。 这将导致引发错误**EventWrite** \_不\_ENOUGH\_内存错误和事件数据丢失。 在这种情况下，ETW 增加日志记录会话的**EventsLost**属性，以便使用者能够看到丢失的数据。

有关如何避免丢失中记录的事件的详细信息，请参阅[避免丢失事件](avoid-lost-events.md)。

## <a name="logging-to-memory-or-to-a-file"></a>记录到内存或文件


您可以配置配置文件在内存或文件记录事件数据的缓冲区。 缓冲模式是循环内存中的会话。 作为对请求的事件跟踪日志 (ETL) 文件的快照，您可以保存此会话的内容。 当您保存内容时 WPR 不会刷新内存中的缓冲区空间的内容。

您可以保留上不断缓冲模式会话。 这是特别有用如果您不知道感兴趣的行为将发生时。 选择所需的循环缓冲区空间时足够小，能够保留在内存中缓冲模式。 连续的日志文件是最佳的控制方案。 例如，可以使用连续的日志文件进行回归测试，或中感兴趣的行为会更容易预测。

有关日志记录选项的详细信息，请参阅[日志记录模式](logging-mode.md)。

## <a name="recording-profiles"></a>配置文件记录


记录配置文件控制每个会话。 配置文件可以是内置的配置文件或用户定义的配置文件。 有关详细信息，请参阅[记录配置文件](recording-profiles.md)。

## <a name="buffer-size"></a>缓冲区大小


缓冲区大小是非常重要的控制 I/O 效率并确保 WPR 不跳过大的事件。 非常小的缓冲区，可以减少 I/O 写入效率。 我们建议最小缓冲区大小为 64 KB 或 128KB，以促进良好的写入性能并减少磁盘开销和丢失的事件。 缓冲区大小将决定录制的最大持续时间。 ETW 限制到大约 64 KB 事件的最大大小。

## <a name="collectors"></a>收集器


记录配置文件中的会话，您必须定义系统收集器和一个或多个事件收集器。 收集器名称必须是唯一的系统和系统到日志文件所必须具有的独占写权限。 日志文件的名称也必须是唯一的而所有收集器的文件的名称。 因此日志文件的路径必须指定环境变量而 WPR 不展开环境变量。 有关详细信息，请参阅[1。收集器定义](1-collector-definitions.md)。

## <a name="providers"></a>提供程序


从一组已定义的系统和事件提供程序收集日志记录会话。 这是在每会话基础上配置的重要项目。 大多数提供程序可以具有多对多关系与会话。 特殊的提供程序所必需的某些事件，例如内核或堆事件。 有关详细信息，请参阅[提供程序](providers.md)。

## <a name="related-topics"></a>相关的主题


[WPR 功能](wpr-features.md)

[WPR 常见方案](windows-performance-recorder-common-scenarios.md)

[配置文件记录](recording-profiles.md)

[缓冲区](buffers.md)

[BufferSize](buffersize.md)

 

 







