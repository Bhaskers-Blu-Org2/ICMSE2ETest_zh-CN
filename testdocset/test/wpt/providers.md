---
title: "提供程序"
description: "提供程序"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 2da92ebb-055a-45ff-8da6-7a06f78a8d9e
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 0c4f17a2e7ae5e0ca3910b304f38ec8e23073d03
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="providers"></a>提供程序


提供程序是公开事件到 Windows 性能记录器 (WPR) 跟踪 Windows 事件 (ETW) 组件。 在一个配置文件，包括堆事件提供程序中，您可以使用单个系统提供程序和多个事件提供程序。

## <a name="system-providers"></a>系统提供商


系统提供程序提供内核事件。 系统提供程序通过使用下列定义︰

-   要收集的事件的关键词。

-   要从中收集事件的堆栈。

-   池标记以指示所做的分配或分配类型的组件。

有关受支持的系统的关键字的说明，请参阅[（在 SystemProvider) 的关键字](keyword--in-systemprovider-.md)。

## <a name="event-providers"></a>事件提供程序


您可以配置事件提供程序可以通过指定一个十六进制位屏蔽关键字提供特定类型的事件 （与提供程序支持的那些）。 因为提供程序都支持不同的事件，有这些关键字的任何字符串常量。 因此，它们必须是十六进制样式的字符串。

## <a name="related-topics"></a>相关的主题


[WPR 功能](wpr-features.md)

[2.系统和事件提供程序定义](2-system-and-event-provider-definitions.md)

 

 







