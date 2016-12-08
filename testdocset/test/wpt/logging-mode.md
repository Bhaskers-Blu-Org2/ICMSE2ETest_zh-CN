---
title: "记录模式"
description: "记录模式"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 96dc60e4-0550-4cac-b405-9aab923b7435
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: ba4b34f9cecc69118e5c27884cd976db03dcc232
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="logging-mode"></a>记录模式


定义 Windows 性能记录器 (WPR) 配置文件时，必须从以下选项中选择日志记录模式︰

-   **文件**︰ 记录日志数据写入顺序文件

-   **内存**︰ 内存中的记录对循环缓冲区日志记录数据

默认情况下，日志记录模式设置为**内存**。 但是，*开/关*切换始终记录到文件中。

日志记录到文件通常用于短录制可以预料到将被记录的事件。 日志记录到内存通常用于记录可以在任何时间发生的事件。 WPR 登录到内存时，缓冲区大小和配置文件详细信息的级别确定覆盖旧事件之前，WPR 记录数据的时间长度。

**警告︰**  
要将限制文件大小，请选择**内存**。 日志记录到文件中，可用磁盘空间时，文件大小的唯一限制。 如果文件太大，您可能不能在 Windows 性能分析器 (WPA) 进行分析。

 

创作自定义录制配置文件，必须在同一个记录配置文件定义 (.wprp) 文件中定义文件和内存版本。 当您选择用于录制的配置文件时，您必须选择文件或内存中用于该记录事件的版本。 自定义配置文件的示例，请参见[3。配置文件定义](3-profile-definitions.md)。

.Wprp 文件可以有最多四个配置文件定义︰ 一个用于每个详细信息级别和日志记录模式组合。 强制执行以下约束︰

-   该配置文件标识符必须是以下面的格式︰ &lt; *ProfileName*&gt;。&lt; *DetailLevel*&gt;。&lt; *LoggingMode*&gt;

-   存在于单个文件中的所有配置文件都必须具有相同的名称。

-   .Wprp 文件必须包含配置文件的内存和文件日志记录模式。

在创作自定义的配置文件，您必须定义[BufferSize](buffersize.md)元素和[缓冲区](buffers.md)元素。 作为缓冲区使用的大小，以千字节 (KB)，定义固定数量或总内存的百分比，您可以定义缓冲区的总金额。 默认缓冲区数为 64，和默认缓冲区大小为 128 KB。

WPR 命令行界面可用于查看每个提供程序所使用的缓冲区的数目和大小。

``` syntax
wpr -profiledetails CPU

Microsoft Windows Performance Recorder Version 6.2.9200


Profile                 : CPU.Verbose.Memory


Collector Name          : NT Kernel Logger
Buffer Size (KB)        : 1024
Number of Buffers       : 613
```

**请注意**  
WPR 支持仅单值*NumberOfBuffers*。 它不支持最小值和最大缓冲区。

 

有关如何设置缓冲区的一般准则如下所示︰

-   事件堆栈需要更多的空间与事件，而堆栈。 因此，WPR 使用更多的缓冲区，将多个数据记录相同的一段时间。

-   请确保您缓冲区的尺寸正确。 如果缓冲区太大，太多内存的消耗和系统性能会受到影响。 如果缓冲区太小，事件可能会丢失，并跟踪变得毫无用处。

-   当记录到内存时，缓冲区大小将决定覆盖旧事件之前，WPR 记录数据的时间长度。 对于内存跟踪，我们建议将缓冲区设置为如 1%至 5%的物理内存，具体取决于配置文件的总内存的百分比。 除非记录配置文件非常详细，是应该足够的物理内存的 10%。

-   缓冲区在记录到比时记录到内存的文件时通常较小。 但是，如果缓冲区太小，缓冲区会刷新到磁盘过于频繁。 除非记录配置文件是非常详细的 10-50 MB 的物理内存就足够了。

有关缓冲区的详细指导，请参阅[会话 （Windows 驱动程序）](http://go.microsoft.com/fwlink/p/?linkid=246706)。

## <a name="related-topics"></a>相关的主题


[WPR 功能](wpr-features.md)

[详细信息级别](detail-level.md)

[3.配置文件定义](3-profile-definitions.md)

[更改的日志记录模式](change-the-logging-mode.md)

 

 







