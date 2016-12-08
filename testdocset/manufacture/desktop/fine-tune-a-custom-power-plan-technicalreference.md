---
author: Justinha
Description: "调整自定义电源计划"
ms.assetid: 3f3b0d9d-d84a-4b87-a271-159d80ebbcc7
MSHAttr: PreferredLib:/library/windows/hardware
title: "调整自定义电源计划"
ms.openlocfilehash: 1baf2ed1045fb08c9dba3063640a858808fbc966
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="fine-tune-a-custom-power-plan"></a>调整自定义电源计划


电源计划是管理计算机如何使用和节约用电的硬件和系统设置的集合。 您可以创建自定义电源计划，为特定的计算机优化。

您可以管理通过控制面板最常见的电源计划设置。 有关详细信息，请参阅[创建自定义电源计划](create-a-custom-power-plan-technicalreference.md)。 要调整不是可以通过控制版面配置的特定于硬件的配置，使用 PowerCfg 工具。

## <a name="span-idmodifypowerplanspanspan-idmodifypowerplanspanspan-idmodifypowerplanspanmanually-modifying-a-power-plan"></a><span id="ModifyPowerPlan"></span><span id="modifypowerplan"></span><span id="MODIFYPOWERPLAN"></span>手动修改电源计划


您可以使用自定义所有可配置的 Windows 电源选项`powercfg`命令从提升的命令提示符。 这包括不可通过控制版面配置的特定于硬件的配置。

**列出可用的电源计划**

-   在技术人员计算机上，在提升的命令提示符下，键入以下命令︰

    ``` syntax
    powercfg -LIST
    ```

    计算机将返回列表中可用的电源计划。 在以下示例中，这些计划是*平衡*和*节能程序*。

    ``` syntax
    Existing Power Schemes (* Active)
    -----------------------------------
    Power Scheme GUID: {guidPlan1}  (Balanced) *
    Power Scheme GUID: {guidPlan2}  (Power saver)
    ```

    注意您想要更改电源计划旁边列出的 Guid。 您将需要手动更新设置并捕获电源计划这些 Guid。

**若要设置为活动电源计划要修改**

-   若要修改计划，使用的 GUID，您想要更改将该电源计划设置为活动电源计划的电源计划。 例如︰

    ``` syntax
    powercfg -SETACTIVE {guidPlan2}
    ```

**要调整设置**

1.  本部分介绍如何通过使用手动配置其他电源配置设置`powercfg`命令。 测试这些设置，以创建最佳电源计划为您的系统。

    **了解现有的电源设置。**

    1.  在提升的命令提示符下，键入以下命令︰

        ``` syntax
        powercfg -QUERY
        ```

        计算机将显示此计划的电源设置的所有信息。

    2.  找到您想要更改的设置的子组 GUID。 例如，如果要修改显示设置，请查找显示子组的 GUID:

        ``` syntax
        Subgroup GUID: {guidSubgroup-Display}  (Display)
        ```

    3.  找到您想要更改的设置 GUID。 例如，若要修改显示亮度设置，请查找 GUID （显示亮度） 设置︰

        ``` syntax
        Power Setting GUID: {guidPowerSetting-Brightness}  (Display brightness)
        ```

    4.  从查询命令查看信息，查看可能的设置，并确定适合您的计算机的值。

        **请注意**  
        您必须通过使用十进制整数输入这些值。 但是的值显示在屏幕上为特定于设置的十六进制值。

        例如，若要设置最大显示亮度为 50%的亮度，以输入值 50。 当您使用`powercfg -QUERY`命令来确认该设置，则值将显示为 0x00000032。

        ``` syntax
        Power Setting GUID: {guidPowerSetting-Brightness}  (Display brightness)
          Minimum Possible Setting: 0x00000000
          Maximum Possible Setting: 0x00000064
          Possible Settings increment: 0x00000001
          Possible Settings units: %
         Current AC Power Setting Index: 0x00000064
         Current DC Power Setting Index: 0x00000032
        ```

2.  调整的时间当计算机已接通电源的电源设置的值。 例如，若要显示亮度级别设置为 100%，在计算机已接通电源时，键入以下命令︰

    ``` syntax
    powercfg -SETACVALUEINDEX {guidPlan-New} {guidSubgroup-Display}  {guidPowerSetting-Brightness} 100
    ```

3.  调整计算机时电池供电的电源设置的值。 例如，若要在计算机使用电池电源时，显示器亮度级别设置为 75%，键入以下命令︰

    ``` syntax
    powercfg -SETDCVALUEINDEX {guidPlan-New} {guidSubgroup-Display}  {guidPowerSetting-Brightness} 75
    ```

4.  使用**查询**命令来验证设置。 例如︰

    ``` syntax
    powercfg -QUERY
    ```

    计算机将显示以十六进制表示法新电源设置索引。 例如︰

    ``` syntax
    Power Setting GUID: {guidPowerSetting-Brightness}  (Display brightness)
          Minimum Possible Setting: 0x00000000
          Maximum Possible Setting: 0x00000064
          Possible Settings increment: 0x00000001
          Possible Settings units: %
        Current AC Power Setting Index: 0x00000064
        Current DC Power Setting Index: 0x0000004b
    ```

    计算机已接通电源时的十六进制值 0x00000064 表示 100%显示亮度。 当计算机正在使用电池电源时的十六进制值 0x0000004b 表示 75%显示亮度。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[创建自定义电源计划](create-a-custom-power-plan-technicalreference.md)

[设置默认的电源计划](set-the-default-power-plan-technicalreference.md)

 

 






