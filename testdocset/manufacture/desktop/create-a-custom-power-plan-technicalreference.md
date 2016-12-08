---
author: Justinha
Description: "创建自定义电源计划"
ms.assetid: d1d0e1b0-f15f-482c-9e9b-1b75a05dfeb3
MSHAttr: PreferredLib:/library/windows/hardware
title: "创建自定义电源计划"
ms.openlocfilehash: 51b1b866add958982b8f0cd5b67f5ae16f3d972a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="create-a-custom-power-plan"></a>创建自定义电源计划


*电源计划*是管理计算机如何使用和节约用电的硬件和系统设置的集合。 电源计划也称为是一种*电源使用方案*。 您可以创建自定义电源计划，为特定的计算机优化。

默认情况下，Windows 8 和 Windows Server® 2012年包含三个电源计划︰**平衡**、**节能程序**和**高性能**。 可以为您的系统中自定义这些现有计划，创建新的计划，根据现有计划，或从头开始创建新的电源计划。

优化 Windows 电源计划有助于提高电池使用寿命。 但是，单个应用程序、 设备或系统功能的执行效果不佳可以大大缩短电池寿命。 有关影响电池寿命因素的信息，请参阅[管理电池寿命和电源消耗概述](managing-battery-life-and-power-consumption-overview-technicalreference.md)。

## <a name="span-idinthistopicspanspan-idinthistopicspanspan-idinthistopicspanin-this-topic"></a><span id="In_this_topic"></span><span id="in_this_topic"></span><span id="IN_THIS_TOPIC"></span>本主题中


[创建自定义的电源计划](#createcustomizedplan)

[列出可用的电源计划](#listpowerplans)

[部署电源计划](#deploypowerplan)

## <span id="CreateCustomizedPlan"></span><span id="createcustomizedplan"></span><span id="CREATECUSTOMIZEDPLAN"></span>


**创建自定义的电源计划**

1.  单击**开始**，然后选择**控制面板**。

2.  单击**硬件和声音**，然后选择**电源选项**。

3.  **电源选项**控制面板将打开，并显示电源计划。

4.  单击**创建电源计划**。

5.  请按照屏幕说明进行操作来创建和自定义电源计划基于现有计划的文件。 电源计划"OutdoorPlan"的名称。

    **请注意**  
    您可以管理通过控制面板最常见的电源计划设置。 要微调不会出现在控制面板中的设置，请参阅[自定义电源计划调整](fine-tune-a-custom-power-plan-technicalreference.md)。

## <span id="ListPowerPlans"></span><span id="listpowerplans"></span><span id="LISTPOWERPLANS"></span>


**列出可用的电源计划**

-   在技术人员计算机上，在提升的命令提示符下，键入以下命令︰

    ``` syntax
    powercfg -LIST
    ```

    计算机将返回列表中可用的电源计划。 在下面的示例中，这些计划是*已平衡*、*节能程序*和*OutdoorPlan*。

    ``` syntax
    Existing Power Schemes (* Active)
    -----------------------------------
    Power Scheme GUID: {guidPlan1}  (Balanced) *
    Power Scheme GUID: {guidPlan2}  (Power saver)
    Power Scheme GUID: {guidPlan3}  (OutdoorPlan)
    ```

    注意您想要捕获电源计划旁边列出的 Guid。

## <span id="DeployPowerPlan"></span><span id="deploypowerplan"></span><span id="DEPLOYPOWERPLAN"></span>


**部署电源计划**

为您的系统创建正常工作的电源计划后，可以部署到目标计算机的电源计划。

若要导出 OutdoorPlan 电源计划，在技术人员计算机上创建、 打开提升的命令提示符，并键入以下命令然后

``` syntax
powercfg -EXPORT C:\OutdoorPlan.pow {guidPlan-New}
```

这将创建新的电源计划文件。

若要了解详细信息，请参阅[设置默认电源计划](set-the-default-power-plan-technicalreference.md)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题

[管理的电池寿命和电源消耗概述](managing-battery-life-and-power-consumption-overview-technicalreference.md)

[测试电池寿命和电源消耗](test-battery-life-and-power-consumption-technicalreference.md)

[设置默认的电源计划](set-the-default-power-plan-technicalreference.md)