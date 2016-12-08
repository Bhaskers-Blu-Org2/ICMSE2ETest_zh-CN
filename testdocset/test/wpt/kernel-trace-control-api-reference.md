---
title: "内核跟踪控件 API 参考"
description: "内核跟踪控件 API 参考"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 16ecacd5-25aa-43d7-b842-cb8f92db8eeb
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 9c65487f0aa1ea28bdee68ebe631b17f9b3424da
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="kernel-trace-control-api-reference"></a>内核跟踪控件 API 参考


利用此 API，捕获内核堆栈跟踪，合并多个跟踪文件进行分析，跟踪和合并文件中包括系统信息的堆。

内核跟踪控制 API 可供使用了 Windows Vista 中。

Windows 7 和 Windows Vista 中，系统需要将**DisablePagingExecutive**注册表值设置 x64 上的 stackwalking **HKLM\\系统\\开目前控制设置\\控件\\会话管理器\\内存管理**。 有关详细信息，请参阅[DisablePagingExecutive](http://go.microsoft.com/fwlink/p/?linkid=213095)。

**请注意** Windows 8 或更高的系统不需要此注册表更改。

 

下面的示例演示如何查询该注册表值。

``` syntax
@REG QUERY "HKLM\System\CurrentControlSet\Control\Session Manager\Memory Management" -v DisablePagingExecutive
```

下面的示例演示如何启用 stackwalking。

``` syntax
@REG ADD "HKLM\System\CurrentControlSet\Control\Session Manager\Memory Management" -v DisablePagingExecutive -d 0x1 -t REG_DWORD -f
@IF NOT %ERRORLEVEL% == 0 echo error: Could not configure system for 64-bit stackwalking. Please run this script from an elevated administrator console.
```

**请注意**  
要使这些更改生效，必须重新启动系统。

 

下面的示例演示如何禁用 stackwalking。

``` syntax
@REG ADD "HKLM\System\CurrentControlSet\Control\Session Manager\Memory Management" -v DisablePagingExecutive -d 0x0 -t REG_DWORD -f
@IF NOT %ERRORLEVEL% == 0 echo error: Could not remove 64-bit stackwalking configuration. Please run this script from an elevated administrator console.
```

**请注意**  
要使这些更改生效，必须重新启动系统。

 

## <a name="in-this-section"></a>在这一节


[函数](functions-wpa.md)

[结构](structures-wpa.md)

[跟踪控制标志](trace-control-flags.md)

[跟踪控制事件类型](trace-control-event-types.md)

[自定义注入的系统信息](custom-injection-of-system-information.md)

## <a name="related-topics"></a>相关的主题


[Windows 性能 Toolkit 技术参考](windows-performance-toolkit-technical-reference.md)

 

 







