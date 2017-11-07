---
title: "时间和时间戳的格式"
description: "时间和时间戳的格式"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 4ef3a58b-da6e-46cb-9655-9c81abce7b71
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 8ae028772788d18c5ed78224743864efc581ad56
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="time-and-timestamp-formats"></a>时间和时间戳的格式


在命令行上显示的时间和时间跨度的格式。

``` syntax
xperf -help format
```

## <a name="remarks"></a>备注


Xperf 的各种操作支持采取时间和时间跨度参数的选项。

时间参数通常采取的`-range`选项。 在下表中描述的格式，可以读取时间。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>1234 [s | ms | 我们 | ns]</p></td>
<td><p>1234 [秒 | 毫秒 | 微秒 | 纳] 自跟踪文件的开头。</p>
<p>默认单位为微秒。</p></td>
</tr>
<tr class="even">
<td><p>2004/12/04:20:05:20.1234[+UTC] 物理时钟时间。</p></td>
<td><p>所有日期和时间组件都是必需的但时区的时间。 如果未不指定任何时区，则假定时间可本地时区中。 (这也是所使用的时间格式<code>-a tracestats</code>。)</p></td>
</tr>
</tbody>
</table>

 

**请注意**  
目前支持的唯一的本地时区和 UTC。

 

时间跨度参数通常所接受的解决方案的选项。 在下表中描述的格式之一，可以阅读 Timespans。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>1234 [s | ms | 我们 | ns]</p></td>
<td><p>1234 [秒 | 毫秒 | 微秒 | 纳]</p></td>
</tr>
<tr class="even">
<td><p>20:05:20.1234</p></td>
<td><p>20 时 5 分 20 秒 123.4 毫秒。 所有的时间组件是必需的。</p></td>
</tr>
</tbody>
</table>

 

**请注意**  
在 Xperf 跟踪转储的事件时间戳总是显示以毫秒为单位。

 

## <a name="related-topics"></a>相关的主题


[Xperf 命令行参考](xperf-command-line-reference.md)

 

 







