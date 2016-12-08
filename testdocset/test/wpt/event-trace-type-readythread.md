---
title: "事件\\_跟踪\\_类型\\_READYTHREAD"
description: "事件\\_跟踪\\_类型\\_READYTHREAD"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: a34bf78c-2d42-485e-a64c-e87256ba08c7
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: a0525d4812cd9e6d871499f78790302e8d21ae74
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="eventtracetypereadythread"></a>事件\_跟踪\_类型\_READYTHREAD


此标志使 ReadyThread 事件的堆栈跟踪。

``` syntax
#define EVENT_TRACE_TYPE_READYTHREAD 0x32
```

## <a name="remarks"></a>备注


此事件类型是类似于在**事件中使用的事件类型\_跟踪\_属性。EnableFlags**成员，但较特定的内核跟踪控件 api。

**要求︰**

**版本︰**可用于在 Windows Vista 中开始。 这种结构被随 Windows 性能分析器。

**标头︰**在 KernelTraceControl.h 中声明。 包括 KernelTraceControl.h。

**库︰**包含在 KernelTraceControl.dll 中。

## <a name="related-topics"></a>相关的主题


[跟踪控制事件类型](trace-control-event-types.md)

 

 







