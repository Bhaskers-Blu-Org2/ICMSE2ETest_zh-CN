---
title: "关系图"
description: "关系图"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 44ccfef7-aaee-4194-a26d-5285e41eb683
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: e6ceee999a29d0d663820e908a2bf7b32d5580d8
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="graphs"></a>关系图

Windows 性能分析器 (WPA) 提供了以下类型的关系图︰

-   [线图](#line_stacked_bar)
-   [堆积折线图](#line_stacked_bar)
-   [堆积条形图](#line_stacked_bar)
-   [火焰图](#flame_graphs)
-   [生存期关系图](#lifetime_graphs)
-   [活动类型的关系图](#activity_type_graphs)
-   连续的资源跟踪信息
-   [一般事件关系图](#generic_events_graphs)

<a name="line_stacked_bar"></a>
## <a name="line-stacked-line-and-stacked-bar-graphs"></a>线，堆积线和堆积条形图

当您行、 堆积线或堆积条形图从**图形资源管理器**窗口拖到**分析**选项卡时，它显示为折线图，如下图所示

![线图](images/wpaline.jpg)

要更改关系图的外观，请单击图表标题栏上的最右边的下拉箭头，然后选择**堆积线**或**堆积条形图**。

下面的插图显示为堆积折线图的同一个图形。

![堆积的折线图](images/wpastackedline.jpg)

下图显示为堆积条形图的同一个图形。

![堆积的条形图](images/wpastackedbar.jpg)

您可以指定 4 到 100 间隔的堆积条形图。

<a name="flame_graphs"></a>
## <a name="flame-graphs"></a>火焰图

*火焰图*是关系图的模式下，您可以快速比较表中的数据值。 每个*火焰组*的宽度取决于其在视图中的权重值。 例如，使用 CPU 堆栈每个帧的重量显示其宽度。 已筛选出一组特定的数据时，此模式是最佳。

要切换到火焰图，请确保表配置与金色栏左侧的列和单个数值列右侧的蓝色条块使用 SUM 聚合，然后**火焰**从菜单中选择图形顶部的图形。 或者，使用内置**的过程中，堆栈着火**预设**式 （采样） 的 CPU 使用率**图表中。

<img src="images\wpa-select-chart-type-menu.png" alt="Chart menu in WPA." height="170"><br/>

下图是一种 CPU 采样并筛选到 Notepad.exe 的堆栈。 在图中， **comctl32.dll ！TV_DrawTree**是当前的筛选视图中的大框架。 从这里，您可以检查堆栈来查找在其中执行最大工时量。

![CPU 采样并筛选到一个较小集的堆栈的示例。](images/wpa-graph-flame-example-CPU-sampled.jpg)

如果文本可读的最小高度，显示火焰组的名称。 若要显示带有数据的工具提示，请将鼠标指针悬停的火焰图形中的一项。 若要选择表中的对应数据，单击以展开它在表中，或要过滤表中，右击，然后单击数据视图中的**筛选器对火焰**的火焰组。 

火焰图可以用任何顺序分组列左侧的金条的配置。 下面的插图显示磁盘使用情况和磁盘服务时间的分组。 **普通**的工具提示显示的名称和值的鼠标指针下方的火焰组。

![着火的磁盘使用情况和工具提示中显示的名称与磁盘服务时间的图形示例和鼠标指针下方的火焰组的值。](images/wpa-graph-flame-example-disk-usage.jpg)

<a name="lifetime_graphs"></a>
## <a name="lifetime-graphs"></a>生存期关系图

生命周期图表显示各个类别，例如进程，为定义的类别的生存期的水平条。

下图显示的流程生命周期图。

![流程生命周期图](images/processlifetime.jpg)

<a name="activity_type_graphs"></a>
## <a name="activity-type-graphs"></a>活动类型的关系图

活动类型图用水平条形图来显示类型的活动。 在每一栏上，活动的时间是灰色的。 例如，如果您放大到足够的详细信息这种类型的关系图，您可以看到，每个磁盘读取或写入的时间也会用了。

下面的插图显示了输入和输出类型。

![wpa 进程的 i/o](images/wpaio.jpg)

<a name="generic_events_graphs"></a>
## <a name="generic-events-graphs"></a>一般事件关系图

一般事件关系图显示录制中深的所有事件。

下图是一个一般事件图的一个示例。

![wpa 一般事件关系图](images/wpagenericevents.jpg)


## <a name="related-topics"></a>相关的主题

[WPA 功能](wpa-features.md)

 

 







