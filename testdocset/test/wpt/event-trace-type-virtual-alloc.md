---
title: "事件\\_跟踪\\_类型\\_虚拟\\_分配"
description: "事件\\_跟踪\\_类型\\_虚拟\\_分配"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 91ba3533-f652-4073-9dce-6511730a801e
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: bcba130b65a8e84e9bee114ed947855536c8479b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="eventtracetypevirtualalloc"></a>事件\_跟踪\_类型\_虚拟\_分配


此标志使虚拟内存分配事件的堆栈跟踪。

``` syntax
#define EVENT_TRACE_TYPE_VIRTUAL_ALLOC 0x62
```

## <a name="remarks"></a>备注


此事件类型是类似于在**事件中使用的事件类型\_跟踪\_属性。EnableFlags**成员，但较特定的内核跟踪控件 api。

**要求︰**

**版本︰**可用于在 Windows Vista 中开始。 这种结构被随 Windows 性能分析器。

**标头︰**在 KernelTraceControl.h 中声明。 包括 KernelTraceControl.h。

**库︰**包含在 KernelTraceControl.dll 中。

## <a name="related-topics"></a>相关的主题


[跟踪控制事件类型](trace-control-event-types.md)

 

 







