---
title: "事件\\_跟踪\\_类型\\_虚拟\\_自由"
description: "事件\\_跟踪\\_类型\\_虚拟\\_自由"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 1c547a82-5e5e-4c0e-b3b5-5830f5a52bab
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 140c5a5bb2d1e789a359f5c3bf107dae29de9e0a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="eventtracetypevirtualfree"></a>事件\_跟踪\_类型\_虚拟\_自由


此标志使虚拟内存可用事件的堆栈跟踪。

``` syntax
#define EVENT_TRACE_TYPE_VIRTUAL_FREE 0x63
```

## <a name="remarks"></a>备注


此事件类型是类似于在**事件中使用的事件类型\_跟踪\_属性。EnableFlags**成员，但较特定的内核跟踪控件 api。

**要求︰**

**版本︰**可用于在 Windows Vista 中开始。 这种结构被随 Windows 性能分析器。

**标头︰**在 KernelTraceControl.h 中声明。 包括 KernelTraceControl.h。

**库︰**包含在 KernelTraceControl.dll 中。

## <a name="related-topics"></a>相关的主题


[跟踪控制事件类型](trace-control-event-types.md)

 

 







