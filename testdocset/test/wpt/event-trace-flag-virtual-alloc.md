---
title: "事件\\_跟踪\\_标志\\_虚拟\\_分配"
description: "事件\\_跟踪\\_标志\\_虚拟\\_分配"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 01bbdf2d-20e2-4588-a90b-4c962e69cbc1
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 1870a8563d20cefe4aa5def802319af3d5ce23e6
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="eventtraceflagvirtualalloc"></a>事件\_跟踪\_标志\_虚拟\_分配


此标志允许捕获虚拟分配和释放事件。

``` syntax
#define EVENT_TRACE_FLAG_VIRTUAL_ALLOC 0x00004000
```

## <a name="remarks"></a>备注


一个内核跟踪控制标志启用或禁用内核事件类型的日志记录。 有关内核的标志和相应的内核事件的详细信息，请参阅[事件\_跟踪\_属性结构](http://go.microsoft.com/fwlink/p/?linkid=212231&clcid=0x409)。

**要求︰**

**版本︰**可用于在 Windows Vista 中开始。 这种结构被随 Windows 性能分析器。

**标头︰**在 KernelTraceControl.h 中声明。 包括 KernelTraceControl.h。

**库︰**包含在 KernelTraceControl.dll 中。

## <a name="related-topics"></a>相关的主题


[跟踪控制标志](trace-control-flags.md)

 

 







