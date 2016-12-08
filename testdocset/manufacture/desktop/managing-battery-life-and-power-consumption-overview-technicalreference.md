---
author: Justinha
Description: "管理的电池寿命和电源消耗概述"
ms.assetid: 9e5f962a-7647-431f-b10e-98c7589ec388
MSHAttr: PreferredLib:/library/windows/hardware
title: "管理的电池寿命和电源消耗概述"
ms.openlocfilehash: 37da9176af68f0ba958343959b7c9c090e05d631
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="managing-battery-life-and-power-consumption-overview"></a>管理的电池寿命和电源消耗概述


基于 Windows® 的笔记本电脑必须符合能源效益的管理法规要求，如美国环境保护署 (EPA) 能源之星程序。 此外，调查表明，更长的电池寿命的笔记本电脑仍然是使用者的主要要求。

例如，低容量电池、 大量占用处理器的驱动程序或配置不当的电源设置的硬件和软件因素可能会导致电池寿命显著减少。 当您设计您的系统时，您应该试验的多个配置每个因素找到电池寿命和性能的最佳平衡点。

## <a name="span-idhardwarespanspan-idhardwarespanspan-idhardwarespanhardware"></a><span id="Hardware"></span><span id="hardware"></span><span id="HARDWARE"></span>硬件


本节列出了几种可影响电池寿命的常见硬件设计考虑事项。

-   **电池容量。** 请与您的电池制造商联系，以确定电池容量。

-   **其他硬件组件。** 硬件组件制造商寻求每个硬件组件的电源消耗测试结果。

有关每个电池寿命因素的信息，请参阅[移动电池寿命解决方案︰ 移动平台专业人士指南](http://go.microsoft.com/fwlink/?LinkId=209929)。

## <a name="span-idsoftwarespanspan-idsoftwarespanspan-idsoftwarespansoftware"></a><span id="Software"></span><span id="software"></span><span id="SOFTWARE"></span>软件


本节列出了几种可影响电池寿命的常见软件设计考虑事项。

-   **驱动程序。** 随着向系统中添加每个新的驱动程序，观察对功率消耗的驱动程序的影响。 一个执行效果不佳的驱动程序可能会严重影响系统性能。

-   **应用程序、 服务和其他软件。** 随着您添加到系统的每个新软件应用程序，观察对功耗的应用程序的影响。 一个执行效果不佳的应用程序可能会严重影响系统性能。

-   **Windows 电源策略设置。** 优化 Windows 电源策略设置应用于平衡性能需求和电池寿命。 有关详细信息，请参阅部分︰ [Windows 电源策略设置](#configurablesettingsimpactingbatterylife)。

有关每个电池寿命因素的详细信息，请参阅[移动电池寿命解决方案︰ 移动平台专业人士指南](http://go.microsoft.com/fwlink/?LinkId=209929)。

## <a name="span-idconfigurablesettingsimpactingbatterylifespanspan-idconfigurablesettingsimpactingbatterylifespanspan-idconfigurablesettingsimpactingbatterylifespanwindows-power-policy-settings"></a><span id="ConfigurableSettingsImpactingBatteryLife"></span><span id="configurablesettingsimpactingbatterylife"></span><span id="CONFIGURABLESETTINGSIMPACTINGBATTERYLIFE"></span>Windows 电源策略设置


本节列出了几种可影响电池寿命的常见可配置设置。 测试这些设置和其他设置来创建最佳电源计划为您的系统。

设置特定于计算机是否接通电源 (ac) 或使用电池电源 (DC)。 您可以配置以下设置︰

-   **显示亮度**

    显示在使用时减少移动计算机上的电源消耗的最有效方法是降低显示器亮度。 连接的显示器是最大的电源使用者。 显示使用的整体系统电源消耗的 40%。

    默认情况下，Windows 会大大降低显示器亮度当移动计算机依靠电池电源。 根据硬件和用户的需要，您可以调整默认显示器亮度设置低延长电池寿命，或者调高使显示屏容易阅读。

-   **显示超时**

    移动 PC 的电池寿命可大大延长使用短显示空闲超时。

    **请注意**  
    **显示变暗**︰ 移动的计算机运行 Windows 8.1 和 Windows Server 2012 R2 将调低显示屏**显示超时**之前的 15 秒。 此值不能是可配置的。

     

-   **硬盘超时**

    尽管硬盘驱动器上不是典型的移动计算机中的主电源使用者，您可以以节省电能，通过增加硬盘超时。

    当硬盘已经空闲了一段时间内时，该硬驱的马达停止。 下次计算机需要访问硬盘，硬盘开始再次旋转时系统响应可能较慢。

    根据硬件和用户的需要，您可以调整默认硬盘超时低延长电池寿命，或者调高提高硬盘的可用性。

-   **休眠模式**

    默认情况下，如果处理器处于空闲状态，并且最终用户在不使用计算机，Windows 会进入低功耗休眠模式或休眠模式。 下一次当计算机需要处理器电源，处理器恢复时系统响应可能较慢。

    根据硬件和用户的需要，您可以调整默认睡眠计时器低延长电池寿命，或者调高提高处理器的可用性。

-   **无线适配器节能模式**

    默认情况下，Windows 配置到**最高性能**交流电源和电池电源的 802.11 节能模式。 此配置使无线适配器处于活动状态，即使不传输数据。 这缓解了一些无线适配器与接入点不兼容 802.11 节能模式的之间的兼容性问题。

    如果您创建自定义电源策略，以节省更多电能，并帮助延长电池寿命，请咨询有关电源策略值更改为**最大节电**模式或**中等节电**效果无线适配器的制造商。

您可以手动修改每个内置电源配置的电源设置。 若要了解有关这些设置和其他常见的可配置电源设置的详细信息，请参阅[移动电池寿命解决方案︰ 移动平台专业人士指南](http://go.microsoft.com/fwlink/?LinkId=209929)和[电源策略配置和部署 Windows 中的](http://go.microsoft.com/fwlink/p/?linkid=129584)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[移动电池寿命解决方案︰ 移动平台专业人士指南](http://go.microsoft.com/fwlink/?LinkId=209929)

[设置默认的电源计划](set-the-default-power-plan-technicalreference.md)

[创建自定义电源计划](create-a-custom-power-plan-technicalreference.md)

[Windows 性能 Toolkit](http://go.microsoft.com/fwlink/p/?linkid=210214)

[电源策略配置和部署 Windows 中](http://go.microsoft.com/fwlink/p/?linkid=129584)

 

 






