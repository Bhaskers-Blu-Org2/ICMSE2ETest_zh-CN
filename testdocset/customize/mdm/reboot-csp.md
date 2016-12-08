---
title: "重新启动 CSP"
description: "重新启动 CSP"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 4E3F1225-BBAD-40F5-A1AB-FF221B6BAF48
ms.openlocfilehash: d4750d4f47fee2e890885585bce43ff13d1da13d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="reboot-csp"></a>重新启动 CSP


重新启动配置服务提供程序用于配置重新启动设置。

下图显示重新配置服务提供程序管理对象以树格式由开放移动联盟设备管理 (OMA DM)，OMA 客户端资源调配和企业 DM。

![重新启动](images/reboot-csp.png)

<a href="" id="--vendor-msft-reboot"></a>**./Vendor/MSFT/Reboot**  
重新启动配置服务提供程序的根节点。

受支持的操作是获得。

<a href="" id="rebootnow"></a>**RebootNow**  
此节点执行的设备重新启动。

> **请注意** 如果此节点处于执行状态，设备将重新启动，在每个同步。 我们建议您清除的执行状态，一旦发生同步。

 

受支持的操作被执行。

<a href="" id="schedule"></a>**日程安排**  
受支持的操作是获得。

<a href="" id="schedule-single"></a>**计划/单**  
此节点将执行重新启动在预定的日期和时间。 设置为 null （空） 日期将会删除现有的计划。 日期和时间值是 ISO8601，和所需的日期和时间。 例如︰ 2015年-12-15T07:36:25Z

受支持的操作是获得和替换。

<a href="" id="schedule-dailyrecurrent"></a>**计划/DailyRecurrent**  
此节点将执行重新启动在预定的时间，在配置的起始时间和日期开始每一天。 设置为 null （空） 日期将会删除现有的计划。 日期和时间值是 ISO8601，和所需的日期和时间。 例如︰ 2015年-12-15T07:36:25Z

受支持的操作是获得和替换。

## <a name="related-topics"></a>相关的主题


[配置服务提供程序的引用](configuration-service-provider-reference.md)

 

 






