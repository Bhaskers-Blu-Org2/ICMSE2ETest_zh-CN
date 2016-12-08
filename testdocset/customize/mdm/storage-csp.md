---
title: "存储 CSP"
description: "存储 CSP"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: b19bdb54-53ed-42ce-a5a1-269379013f57
ms.openlocfilehash: 064c287b271a4085b212b616e1df86add499d4f3
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="storage-csp"></a>存储 CSP


存储企业配置服务提供程序用于配置存储卡设置。 目前，唯一需要配置的设置是启用或禁用存储卡。

> **请注意** 存储 CSP 不再支持 Windows 10 中，它仅支持在 Windows 10 移动向后兼容性。 使用系统/AllowStorageCard 中[策略的 CSP](policy-configuration-service-provider.md) 。

 

下面的关系图以树格式显示存储配置服务提供程序。

![资源调配\-csp\-存储](images/provisioning-csp-storage.png)

<a href="" id="disable"></a>**禁用**  
必需。 一个布尔值，指定是否要启用或禁用存储卡。 如果值为**True**禁用存储卡。 如果值为**False**使存储卡。 默认值为**False**。 值是区分大小写。

支持的操作包括获取和替换。

> **请注意**  如果设备返回一个 404 错误代码时服务器将 Get 命令应用于./Vendor/MSFT/Storage/禁用，则意味着该设备没有 SD 卡。

 

## <a name="related-topics"></a>相关的主题


[配置服务提供程序的引用](configuration-service-provider-reference.md)

 

 






