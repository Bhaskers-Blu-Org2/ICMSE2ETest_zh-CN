---
title: "启动"
description: "启动"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: c6bf946c-9da7-4147-a37e-c117e1ea1fff
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: eef76519936de09ada2829e8a0b58b2ba1bcf4e5
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="boot"></a>启动


此操作会产生一个 XML 报告，总结了在启动中的各种指标。

``` syntax
-a boot [-minCPUToShow <n>] [-maxFilesToShow <n>] [-expectedProcessesFile <file name>] [-minIntervalToShow <n>] [-userShellExecutable]
```

## <a name="options"></a>Options


<a href="" id="-mincputoshow-n-"></a>**-minCPUToShow***&lt;n&gt;*  
* &lt;n&gt;*表示 CPU 使用率在范围 0-100 中显示的最小百分比。

<a href="" id="-maxfilestoshow-n-"></a>**-maxFilesToShow***&lt;n&gt;*  
* &lt;n&gt;*指示要显示的文件最大数量。

<a href="" id="-expectedprocessesfile-file-name-"></a>**-expectedProcessesFile***&lt;文件的名称&gt;*  
*&lt;文件名&gt;*指定一个文本文件，其中包含预期的进程名称的列表。

<a href="" id="-minintervaltoshow-n-"></a>**-minIntervalToShow***&lt;n&gt;*  
* &lt;n&gt;*指示要显示，以微秒为单位的最小时间间隔时间。 默认值是 10。

<a href="" id="-usershellexecutable"></a>**-userShellExecutable**  
在跟踪中找到可执行文件的用户 shell。 默认值为 Explorer.exe。

## <a name="related-topics"></a>相关的主题


[Xperf 操作](xperf-actions.md)

 

 







