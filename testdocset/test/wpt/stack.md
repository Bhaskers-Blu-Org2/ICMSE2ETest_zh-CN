---
title: "堆栈"
description: "堆栈"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 7f8b4905-4702-4bba-998e-baa533adcdb2
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 0c2046f70fa861254642f2325bec02ed8a06de5e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="stack"></a>堆栈


此操作生成一个文本文件，其中总结了堆栈相关的度量标准。

``` syntax
-a stack [-butterfly [n]] [-range T1 T2] [-export <format>] [-pid <pid> ...] [-tid <tid> ...] [-process RegEx1 RegEx2 ... RegExN] [-symbol RegEx1 RegEx2 ... RegExN] [-event RegEx1 RegEx2 ... RegExN]
```

## <a name="options"></a>Options


<a href="" id="-butterfly-n-"></a>**-蝴蝶***\[n\]*  
此跟踪，包括至少拥有的符号中显示堆栈的蝴蝶视图&lt; *min\_点击*&gt;点击、 是否会计算每一处或只有第一个匹配项。 默认值*min\_点击*为 10。

<a href="" id="-ranget1-t2"></a>**-范围***T1 T2*  
时间间隔将报告限于`[lo, hi]`。 *T1*的默认值为零。 *T2*的默认值是`_I64_MAX`。

<a href="" id="-pid-pid-"></a>**-pid***&lt;pid&gt;*  
包括只从匹配的进程标识符的进程的堆栈。

<a href="" id="-tid-tid-"></a>**-tid***&lt;tid&gt;*  
包括只从匹配的线程标识符的线程的堆栈。

<a href="" id="-processregex1-regex2---regexn"></a>**-过程***RegEx1 RegEx2...RegExN*  
包括只从与提供的 ATL 正则表达式相匹配的线程的堆栈。

<a href="" id="-symbolregex1-regex2---regexn"></a>**-符号***RegEx1 RegEx2...RegExN*  
包括只包含堆栈中与匹配提供的 ATL 正则表达式的符号。

<a href="" id="-eventregex1-regex2---regexn"></a>**-事件***RegEx1 RegEx2...RegExN*  
包括只堆栈提供的 ATL 正则表达式匹配的事件。

## <a name="related-topics"></a>相关的主题


[Xperf 操作](xperf-actions.md)

[时间和时间戳的格式](time-and-timestamp-formats.md)

 

 







