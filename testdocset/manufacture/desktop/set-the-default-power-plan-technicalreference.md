---
author: Justinha
Description: "设置默认的电源计划"
ms.assetid: e6c722ae-29f4-4249-adbe-9121fdadcf4c
MSHAttr: PreferredLib:/library/windows/hardware
title: "设置默认的电源计划"
ms.openlocfilehash: bdd2a842782dba60ef64bcbc2eb17f4d20c872bd
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="set-the-default-power-plan"></a>设置默认的电源计划


按照以下说明来部署 Windows 8 或 Windows Server® 2012 Pc 时设置默认电源计划。 电源计划也称为是一种*电源使用方案*。

**请注意**  
此页提供了有关制造个人电脑的信息。

若要修改您自己的 PC 上电源计划，请参见[电源计划︰ 常见问题](http://go.microsoft.com/fwlink/p/?linkid=278892)。

 

**若要设置默认的电源计划**

1.  在技术人员计算机上，打开提升的命令提示符。

2.  如果您想要使用从另一台计算机的电源计划，导入的电源计划。

    例如，要导入的电源计划，被命名为 OutdoorPlan，请键入以下命令在命令提示符处︰

    ``` syntax
    powercfg -IMPORT C:\OutdoorPlan.pow
    ```

3.  键入以下内容以查找计算机上的所有电源计划的 GUID:

    ``` syntax
    powercfg -LIST
    ```

    计算机将返回列表中可用的电源计划。 下面的示例，请参阅这些计划为*guidPlan1*和*guidPlan2*。

    ``` syntax
    Existing Power Schemes (* Active)
    -----------------------------------
    Power Scheme GUID: {guidPlan1}  (Balanced) *
    Power Scheme GUID: {guidPlan2}  (Power saver)
    ```

4.  注意您想要更改电源计划旁边列出的 Guid。

5.  设置您想要设置为活动电源计划作为默认的电源计划。 例如，您可以使用下面的命令︰

    ``` syntax
    powercfg -SETACTIVE {guidPlan2}
    ```

    其中， *guidPlan2*是电源计划的名称。

    可以在答案文件中，使用一个自定义命令或通过在审核模式下打开提升的命令提示符运行此命令。

**确认默认的电源计划**

1.  单击**开始**，然后选择**控制面板**。

2.  单击**硬件和声音**，然后选择**电源选项**。

    **电源选项**控制面板将打开，并显示电源计划。

3.  查看每个电源计划。

4.  验证正确的计划设置为活动电源计划。 计算机显示一个星号 (\*) 旁边的当前电源计划。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[将自定义命令添加到答案文件](https://msdn.microsoft.com/library/windows/hardware/dn915058)

[引导到审核模式或 OOBE 的窗口](boot-windows-to-audit-mode-or-oobe.md)

[创建自定义电源计划](create-a-custom-power-plan-technicalreference.md)

[电源策略配置和部署 Windows 中](http://go.microsoft.com/fwlink/p/?linkid=129584)

 

 






