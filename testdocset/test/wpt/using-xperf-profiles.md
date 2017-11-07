---
title: "使用 Xperf 配置文件"
description: "使用 Xperf 配置文件"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 31673dde-fe06-4b54-afe2-f9bd9c5e60d2
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: d28b041175192220be1d3d5e782b87aca0e23288
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="using-xperf-profiles"></a>使用 Xperf 配置文件


本节演示如何通过使用配置文件捕获跟踪信息。 分析内存时，如果考虑您的跟踪写入文件，因为 ETW 将通过并不会干扰缓存。 分析磁盘 I/O 时，如果考虑到循环缓冲区内存中保存您的跟踪。 如您需要捕获进行长时间跟踪，将不适合在内存中的缓冲区，或者如果您只关心跟踪内容的最后的 5-10 秒，有一些还其他注意事项。

## <a name="procedure"></a>过程


1.  选择配置文件，例如，**性能 ！FileIOProfiles.InBuffer** ，使用与以下示例类似的命令来显示有关它的信息。

    ``` syntax
    xperf -profiles perf!FileIOProfiles.InBuffer
    ```

    此命令将列出所有配置文件，接着是会话中该配置文件提供程序︰

    配置文件︰ FileIOProfiles.InBuffer

    会话︰ FileIOProfiles.InBuffer.Sessions

    会话︰ FileIOProfiles.InBuffer.Sessions\[0\]。内核\[0\]

    会话︰ FileIOProfiles.InBuffer.Sessions\[0\]。用户\[0\]

    提供程序︰ FileIOProfiles.InBuffer.Providers

    提供程序︰ FileIOProfiles.InBuffer.Providers\[0\]。内核\[0\]

    提供程序︰ FileIOProfiles.InBuffer.Providers\[0\]。用户\[0\]

2.  假定您选择了使用基于文件的跟踪，使用下面的命令启动**InSequentialFile**跟踪配置文件。

    ``` syntax
    xperf -start perf!GeneralProfiles.InSequentialFile
    ```

    如果出现问题，则报告错误。 例如，两次启动相同的配置文件将导致错误的会话已在运行。

3.  显示哪个**InSequentialFile**记录器已经通过使用下面的命令启动特定的配置文件。

    ``` syntax
    xperf -profileloggers perf!GeneralProfiles.InSequentialFile
    ```

    对该命令的响应是类似于下面的示例。

    会话状态为"性能 ！ 的GeneralProfiles.InSequentialFile":

    "NT 内核记录器": 运行

    PerfCoreUserSession\_InSequentialFile︰ 运行

4.  停止的**InSequentialFile**跟踪配置文件和保存跟踪信息，然后将它们合并到一个跟踪文件，如 Merged.etl，通过使用下面的命令。

    ``` syntax
    xperf -stop perf!GeneralProfiles.InSequentialFile merged.etl
    ```

    如果出现问题，则报告错误。

5.  开始重写在开始时，所有的 ETW 会话，将启动到 256 记录器的*MaxBuffers*值的**InSequentialFile**跟踪配置文件。 若要执行此操作，请使用下面的命令。

    ``` syntax
    xperf -start perf!GeneralProfiles.InSequentialFile -MaxBuffers 256
    ```

    如果出现问题，则报告错误。

6.  对于活动的**InSequentialFile** ETW 记录器的跟踪配置文件中指定通过使用下面的命令更新*MaxBuffers*值。

    ``` syntax
    xperf -update perf!GeneralProfiles.InSequentialFile -MaxBuffers 256
    ```

    发出此命令后，将显示没有响应。

## <a name="related-topics"></a>相关的主题


[Xperf 配置文件](xperf-profiles.md)

 

 







