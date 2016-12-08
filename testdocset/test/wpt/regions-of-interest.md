---
title: "感兴趣的区域"
description: "感兴趣的区域"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 46062275-1d15-4361-81c6-be4a2f15938d
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 907beeb68c849adeb8cae25b9c36ded4bcadbc0c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="regions-of-interest"></a>感兴趣的区域


感兴趣的区域是在启用跟踪的部分应用程序的用户友好的标签的 WPA 的新功能。 这些标签来查找事件定义开始和停止给定区域的应用。 区域和它们的事件包含在区域 XML 文件。 Microsoft 提供的应用程序分析，某些区域文件，您还可以定义自己的区域文件，您的应用程序或方案。 此功能使您可以快速轻松地识别复杂区域，极大地增加了速度和性能分析的效率。

举一个例子，假设包含几个加载序列，其中每个由一个事件，A，跟另一个事件，b。与区域感兴趣，可应用于这些 A B 时间范围内的每个用户友好的"加载"标签。 现在，而无需手动识别这些事件序列，WPA 自动应用"加载"的标签，从而可以快速直观地显示这些事件的发生。

作为另一个示例中，用户需要来分析特定的 Windows 应用商店应用程序的性能。 应用程序生命周期可以分为几个阶段，如启动、 暂停/恢复，以及关闭，其中的每个可能有相应的区域定义。 与这些区域定义，任何用户可以轻松地标识这些生命周期事件的发生。

若要使用 WPA 感兴趣的区域，您必须︰

-   感兴趣的方案过程中收集了 ETW 跟踪 (.etl) 文件

-   感兴趣区域的定义文件 (.xml)

## <a name="creating-a-regions-of-interest-file"></a>创建一个感兴趣的区域文件


有关创建区域感兴趣的文件的信息，请参阅[创建一个感兴趣的区域文件](creating-a-regions-of-interest-file.md)

## <a name="supporting-regex-in-a-regions-of-interest-file"></a>支持感兴趣的区域文件中的正则表达式


感兴趣的文件的区域支持正则表达式 (regex)。 有关正则表达式和感兴趣的区域文件中创建新行的信息，请参阅[创建一个感兴趣的区域文件](creating-a-regions-of-interest-file.md)

## <a name="applying-a-regions-of-interest-file-to-an-open-trace"></a>打开跟踪应用感兴趣的区域文件


感兴趣的区域文件可用于将附加的标记应用于在 WPA 打开跟踪︰

-   从菜单中选择**跟踪**，**跟踪属性**。

-   出现在**跟踪属性**窗格中选择**添加**。

-   导航到并选择所需的感兴趣区域清单文件 (.xml)，并选择**打开**。

-   现在，该文件将添加到**区域的兴趣定义**列表框。 通过选择窗口顶部附近的**分析**选项卡切换到**分析**窗格中。

-   在**图形浏览器**中展开**系统活动**节点。

-   如果您跟踪包含任何已定义的清单文件的区域，**感兴趣区域的**图表出现在**图形浏览器**作为最后一个下**系统活动**关系图 （之前的**计算**类别中）。 关系图拖放到**分析**窗格。

    跟踪不包含任何感兴趣的区域，如果您看不到**感兴趣的区域**图。

**请注意**  
特性化 CPU 使用量表依赖于区域内利息定义属性为不同的活动的 CPU 使用率。 使用多个区域文件时，不同地区感兴趣的可以重叠和冲突。 发生这些冲突时，WPA 是无法准确特性在给定的时间范围内给定线程的单个活动。

若要避免这些潜在的冲突，请使用一次只有一个地区定义文件。

 

## <a name="related-topics"></a>相关的主题


[创建文件感兴趣的区域](creating-a-regions-of-interest-file.md)

[WPA 功能](wpa-features.md)

 

 







