---
title: "事件\\_跟踪\\_标志\\_调度程序"
description: "事件\\_跟踪\\_标志\\_调度程序"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 939bd14d-06f4-4109-9e7c-95e35815c2e3
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 2d62e9b6b16e378584f959f1ebb5cab35f198e8c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="eventtraceflagdispatcher"></a>事件\_跟踪\_标志\_调度程序


此标志允许捕获就绪的线程事件。

``` syntax
#define EVENT_TRACE_FLAG_DISPATCHER 0x00000800
```

## <a name="remarks"></a>备注


一个内核跟踪控制标志启用或禁用内核事件类型的日志记录。 有关内核的标志和相应的内核事件的详细信息，请参阅[事件\_跟踪\_属性结构](http://go.microsoft.com/fwlink/p/?linkid=212231&clcid=0x409)。

**要求︰**

**版本︰**可用于在 Windows Vista 中开始。 这种结构被随 Windows 性能分析器。

**标头︰**在 KernelTraceControl.h 中声明。 包括 KernelTraceControl.h。

**库︰**包含在 KernelTraceControl.dll 中。

## <a name="related-topics"></a>相关的主题


[跟踪控制标志](trace-control-flags.md)

 

 







