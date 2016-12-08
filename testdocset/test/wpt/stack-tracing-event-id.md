---
title: "堆栈\\_跟踪\\_事件\\_ID"
description: "堆栈\\_跟踪\\_事件\\_ID"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: f03d36fd-9f14-4212-9be6-717e42c18f6f
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: fca9723767f9aa4720b360c52c129c63eca37532
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="stacktracingeventid"></a>堆栈\_跟踪\_事件\_ID


这个结构告诉内核记录器，以包括对命名的事件的调用堆栈。

``` syntax
typedef struct _STACK_TRACING_EVENT_ID {
GUID EventGuid; 
UCHAR Type; 
UCHAR Reserved[7]; 
} STACK_TRACING_EVENT_ID, *PSTACK_TRACING_EVENT_ID
```

## <a name="members"></a>成员


<a href="" id="eventguid"></a>**EventGuid**  
GUID 用于标识特定的内核事件配置为生成的调用堆栈。 有关此成员的详细信息，请参阅[NT 内核记录器常量](http://go.microsoft.com/fwlink/p/?LinkID=212227&clcid=0x409)。 Evntrace.h 列出了**EventGuids** 。

<a href="" id="type"></a>**类型**  
事件之一\_跟踪\_类型\_\* evntrace.h 或[跟踪控件事件类型](https://msdn.microsoft.com/library/windows/hardware/dn640668.aspx)的一个类型。

<a href="" id="reserved"></a>**保留**  
保留供将来使用。

## <a name="remarks"></a>备注


此结构的成员都是相同的经典\_事件\_ID 结构的 Windows 7 版本和 Windows 服务器 2008 SDK 中可用︰

``` syntax
typedef struct _CLASSIC_EVENT_ID {
GUID EventGuid; 
UCHAR Type; 
UCHAR Reserved[7]; 
} CLASSIC_EVENT_ID, *PCLASSIC_EVENT_ID;
```

**要求︰**

**版本︰**可用于在 Windows Vista 中开始。 这种结构被随 Windows 性能分析器。

**标头︰**在 KernelTraceControl.h 中声明。 包括 KernelTraceControl.h。

**库︰**包含在 KernelTraceControl.dll 中。

## <a name="related-topics"></a>相关的主题


[结构](structures-wpa.md)

 

 







