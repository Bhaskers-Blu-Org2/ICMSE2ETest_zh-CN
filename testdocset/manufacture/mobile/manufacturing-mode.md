---
author: kpacquer
Description: "介绍 Windows 10 手机，制造模式是操作系统的一种完整，可以用于制造相关的任务，如组件并支持测试模式。"
ms.assetid: 9c5831f5-a200-436c-97cc-8bd92b30cb3e
MSHAttr: PreferredLib:/library/windows/hardware
title: "制造模式"
ms.openlocfilehash: ae3d9d861123199b3caad447bdaec0eda1ff743a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="manufacturing-mode"></a>制造模式


介绍 Windows 10 手机，制造模式是操作系统的一种完整，可以用于制造相关的任务，如组件并支持测试模式。

在 Windows Phone 8.1，不得不闪存 Microsoft 制造操作系统 (MMO) 进行制造测试和流程，测试硬件，如吹保险丝，并提供安全密钥。 一旦完成测试，您必须闪烁完整的操作系统。 这在制造车间上添加额外的时间。

此新功能允许您引导至一种制造模式的完整的操作系统 （和执行那些制造步骤） 而无需闪存映像 MMO。

## <a name="span-idmanufacturingprofilesspanspan-idmanufacturingprofilesspanspan-idmanufacturingprofilesspanmanufacturing-profiles"></a><span id="Manufacturing_profiles"></span><span id="manufacturing_profiles"></span><span id="MANUFACTURING_PROFILES"></span>生产配置文件


生产配置文件定义在制造模式下引导操作系统时应使用的设置。 该设备可以有多个制造配置文件。 名为默认的配置文件将包含在 Windows 10 移动。 默认配置文件包含引导设备至最小环境的制造模式的 Microsoft 组件的设置。

生产配置文件存储在注册表中的以下位置中的设备︰

**HKEY\_本地\_机\\系统\\开目前控制设置\\控件\\ManufacturingMode**您必须创建一个用于每个制造配置文件的子项。 该项下的配置文件，您可以更改系统在制造模式下的启动时的一些选择的操作系统组件的设置。 例如，您可以更改哪些服务需要启动时启用此制造配置文件。 如下所示，您可以在服务子项中，添加您自己的服务。 如果您想要设置为开始类型相同的所有服务，则可以使用\*的服务名称。 如果\*不使用通配符，制造配置文件中不包括的所有 Win32 服务将都使用其默认的启动类型。

**请注意** \*通配符仅适用于 Win32 服务，不包括内核模式的驱动程序。

 

下面的示例创建一个名为 CustomProfile 的生产配置文件，会导致 OEMFactoryTestService 自动启动的名为服务，并为按需启动的所有其他 Win32 服务︰

``` syntax
[HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\ManufacturingMode\CustomProfile]

[HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\ManufacturingMode\CustomProfile\Services]

[HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\ManufacturingMode\CustomProfile\Services\OEMFactoryTestService]
"Start"=dword:00000002

[HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\ManufacturingMode\CustomProfile\Services\*]
"Start"=dword:00000003
```

生产配置文件名称必须少于 64 个字符。

您不能使用**当前**制造模板的名称。 此名称已保留为制造当前活动配置文件。

 

 





