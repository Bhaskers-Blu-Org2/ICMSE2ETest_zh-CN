---
title: "严格的供应商"
description: "严格的供应商"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: b75d08cc-eaa5-42b8-9bac-d9b6aa35f31a
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 11db583e7ee8197b57e940b38881fba49247b6b9
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="strict-providers"></a>严格的供应商


Windows 性能记录器 (WPR) 录制配置文件存储在 XML 文件具有.wprp 扩展名。 *配置文件定义*将组合在一起的收集器和提供程序定义在.wprp 文件中。 提供程序定义中的**严格**属性时开始记录时不会启动该提供程序用于控制录制配置文件的行为。

提供程序可能无法启动，原因有多种，例如提供程序实现或配置不正确的系统中的缺陷。 当提供程序不启动，其**严格**的特性设置为"true"，启动操作将失败并回滚。 取消所有收集器和提供程序已成功启动。 错误日志提供了错误的信息的提供程序没有启动。 如果**严格**属性设置为"false"，尽可能多的收集器和提供程序启动是可行的并且开始操作成功。 提供程序没有启动有关的信息将显示为警告而不是错误。

## <a name="related-topics"></a>相关的主题


[编写配置文件记录](authoring-recording-profiles.md)

[2.系统和事件提供程序定义](2-system-and-event-provider-definitions.md)

 

 







