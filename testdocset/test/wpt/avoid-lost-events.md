---
title: "避免丢失的事件"
description: "避免丢失的事件"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 7512de7a-de82-43e5-b100-d82faf59a7cb
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: a0b3911d9d880cfc3d76ee21c4ab18651e8e29ee
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="avoid-lost-events"></a>避免丢失的事件


在 Windows 性能记录器 (WPR)，某些应用程序中生成这样多个事件的事件跟踪 Windows (ETW) 不能赶上日志频率。 这个问题表现为录制中丢失的事件。 该问题可能会导致分析困难或错误结论由于不完整的数据。

**请注意**  
默认情况下，WPR 用于分页的内存缓冲区。 若要设置 WPR 用于非分页内存缓冲区，请提供*NonPagedMemory*属性设置为*true* 。 有关如何创建自定义配置文件的详细信息，请参阅[创作录制配置文件](authoring-recording-profiles.md)和[2。系统和事件提供程序定义](2-system-and-event-provider-definitions.md)。

 

您可以帮助防止 WPR 丢失 ETW 缓冲区或事件在以下方面︰

-   使用更大的缓冲区可以更高效的磁盘 I/O WPR 将缓冲区写入磁盘时。

-   您的计算机上使用特定的缓冲区配置请求第一次的数据集合计数。

-   使用**recordTempTo**的命令行选项来记录到另一个位置而不是默认。

-   增加缓冲区的数目。

-   简化您正在测试的方案，或选择较少的配置文件。

-   系统驱动器上的可用磁盘空间。

-   使用高级硬件，以收集数据;例如，使用具有较大吞吐量的磁盘子系统。 这是需要考虑的最后一个选项。 您通常可以避免丢失事件通过仔细选择的提供程序来启用和使用的缓冲区。

## <a name="related-topics"></a>相关的主题


[WPR 常见方案](windows-performance-recorder-common-scenarios.md)

[配置文件记录](recording-profiles.md)

[记录模式](logging-mode.md)

[更改的日志记录模式](change-the-logging-mode.md)

[详细信息级别](detail-level.md)

[更改明细数据级别](change-the-detail-level.md)

[会话](sessions.md)

[会话 （Windows 驱动程序）](http://go.microsoft.com/fwlink/p/?linkid=246706)

 

 







