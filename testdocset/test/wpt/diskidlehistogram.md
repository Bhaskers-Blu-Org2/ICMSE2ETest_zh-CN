---
title: diskidlehistogram
description: diskidlehistogram
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 16552102-b666-4c50-b530-87b31c4838be
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 80cf7c897e4c0c98bb259b7f76b098ed1b626422
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="diskidlehistogram"></a>diskidlehistogram


此操作将生成直方图显示的所有磁盘活动和空闲时间。

``` syntax
-a diskidlehistogram [-disknum <n>] [-buckets B1 B2 ... Bn] [-idletimeout T1 T2 ... Tn] [-idletheshold <t>] [-spindownOverhead [t]] [-spinupOverhead [t]] [-exc_file File1 File2 ... FileN] [-exc_filestr String1 String2 ... StringN] [-exc_filere <regex>]
```

## <a name="options"></a>Options


<a href="" id="-disknum-n-"></a>**-disknum***&lt;n&gt;*  
*n*表示磁盘编号 （从 0 开始磁盘索引）。 默认值是输出直方图的所有磁盘。

<a href="" id="-bucketsb1-b2---bn"></a>**-桶***B1 B2...Bn*  
参数指示不同范围的空闲的长度，以秒为单位。 默认存储桶如下所示︰

-   \[0 s 1 s\]

-   \[1 s 5 s\]

-   \[5 s，60 s\]

-   \[60 s，180 s\]

-   \[180 s 600 s\]

-   \[600 s 900 s\]

-   \[900 s、 1200 s\]

-   \[1200 秒，1800年秒\]

-   \[1800 s + inf\]

磁盘空闲直方图显示磁盘空闲时间和空闲期数的分布不同的空闲期间长度范围的示例值，如下表中所示。

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>小于 1 秒</th>
<th>1-600 秒</th>
<th>多家 600 秒</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>空闲时间</p></td>
<td><p>1000</p></td>
<td><p>1000</p></td>
<td><p>2000</p></td>
</tr>
<tr class="even">
<td><p>总的空闲时间百分比</p></td>
<td><p>25</p></td>
<td><p>25</p></td>
<td><p>50</p></td>
</tr>
<tr class="odd">
<td><p>空闲计数</p></td>
<td><p>90</p></td>
<td><p>5</p></td>
<td><p>5</p></td>
</tr>
<tr class="even">
<td><p>总的空闲计数百分比</p></td>
<td><p>90</p></td>
<td><p>5</p></td>
<td><p>5</p></td>
</tr>
</tbody>
</table>

 

第一行显示直方图的存储桶︰ 空闲长度的不同范围。

第二行显示每个存储桶的累计空闲时间。 例如，所有空闲期短于 1 秒的累计空闲时间是 1000 秒。

第三行计算每个存储桶的空闲时间的百分比除以桶按总空闲时间的空闲时间。

第四行是空闲期间捕获的每个存储桶数。 在此示例中，有 90 空闲期持续少于一秒。

最后一行计算的每个存储桶的空闲期的百分比除以的空闲期总空闲期数的存储桶数。

以下命令将生成以下列表中的存储桶︰ **-桶为 1 5 条六十年代 180s年**:

-   \[0，1 s\]

-   \[1 s 5 s\]

-   \[5 s，60 s\]

-   \[60 s，180 s\]

-   \[180 s + inf\]

<a href="" id="-idletimeoutt1-t2---tn"></a>**-idletimeout***T1 T2...Tn*  
参数指示的空闲超时时间，以秒为单位。 默认值是 5、 60、 180、 600 和 1800年。

<a href="" id="-idletheshold-t-"></a>**-idletheshold***&lt;t&gt;*  
参数指示的空闲阈值，以秒为单位。 空闲时间短于此阈值将被忽略。

<a href="" id="-spindownoverhead-t-"></a>**-spindownOverhead***\[t\]*  
如果不指定参数，则默认值为 0。

使用磁盘 I/O 的时间戳和指定的空闲超时时间的序列，可以计算下和方式，将旋转磁盘时多长时间，它可以在旋转按下状态，如下表中所示。

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th>超时值，以秒为单位</th>
<th>5</th>
<th>60</th>
<th>180</th>
<th>600</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>预计驱动器降速功能机会时间 （秒）</p></td>
<td><p>3800</p></td>
<td><p>2000</p></td>
<td><p>1000</p></td>
<td><p>500</p></td>
</tr>
<tr class="even">
<td><p>估计的驱动器降速功能机会计数</p></td>
<td><p>500</p></td>
<td><p>100</p></td>
<td><p>50</p></td>
<td><p>10</p></td>
</tr>
</tbody>
</table>

 

第一行显示利息估计向下旋转时间空闲超时的值。 第二行显示了对应于每个超时的估计总旋转下时间。 在此示例中，5 秒的超时后所得 3800 秒旋转下的总时间。 第三行显示时间磁盘降速每超时值的估计的的数。

<a href="" id="-spinupoverheadt"></a>**-spinupOverhead***T*  
如果没有指定参数，则默认值为 0 秒。

<a href="" id="-exc-filefile1-file1---filen"></a>**-exc\_文件***File1 File1...FileN*  
排除的文件匹配提供完整的文件路径。 您必须指定您想要排除的每个文件的完整文件路径。

<a href="" id="-exc-filestrstring1-string2---stringn"></a>**-exc\_filestr***String1 String2...StringN*  
排除文件，其中包含一个或多个提供的字符串。

<a href="" id="-exc-filere-regx-"></a>**-执行\_filere***&lt;regx&gt; *  
提供的 ATL 正则表达式匹配的文件排除。 例如，您可以忽略所有通过指定表达式结尾带有.dll 的文件"。\*\\.dll".

**请注意**  在定义一个新行，您必须包括回车符。 而不是使用**\\n**，使用**\\r\\n**。 由包括两个字符 (回车 = r; 换行符 = n)，创建一个行结束符。 [感兴趣的区域](regions-of-interest.md)文件时，这是很有帮助。

 

## <a name="remarks"></a>备注


有几个系统文件的磁盘 I/o 是以对其他文件的磁盘 I/o 响应。 这些系统文件如下所示︰

-   $LogFiles

-   $Mft

-   $Bitmap

-   lastalive0.dat

-   lastalive1.dat

-   $UsnJrnl: $J

它可能很难区分哪些磁盘对其他文件的 I/o 会导致特定磁盘 I/O 到上面的系统文件。 因此，如果您想要查看已排除的文件的影响，还必须排除这些系统文件。 由于这些系统文件的磁盘 I/o 为响应或"非法携带"上其他的磁盘 I/o，忽略仅这些系统文件本身不应显著更改磁盘空闲直方图。

此操作的输出可以导入到电子表格中进行排序和分析。 为输出提供了两个额外的度量标准︰

<a href="" id="avgiointerval"></a>**AvgIOInterval**  
对于特定文件，这将是对该文件的两个后续 I/o 之间的平均间隔。 如果某个文件具有微小的 I/O 时间间隔，如小于 1 秒的时间间隔，此统计数据可能会产生误导。 即使该文件也有较大 I/O 时间间隔，如 30 分钟，平均的 IO 间隔看起来可能很多比另一个具有中等文件短 I/O 的时间间隔，例如 10 分钟。 在这种情况下，您可以使用`-idlethreshold T`从分析中删除空闲期不超过 1 秒。

<a href="" id="maxiointerval"></a>**MaxIOInterval**  
对于每个文件，这将是对该文件的两个后续 I/o 之间的最大间隔。 基于此统计数据输出排序按默认值。 具有一个较大的 I/O 时间间隔的文件仍然可以平均有频繁的 i/o 操作。

**请注意**  
使用这些指标和每个文件的直方图的两个磁盘活动全面描述。

 

避免使用不同的物理磁盘 （或设备，如 USB 闪存驱动器） 来收集跟踪 perturbing 研究下的磁盘。

## <a name="example"></a>示例


下面的示例演示此操作提供默认参数的典型用法

``` syntax
Xperf -i Trace.etl -a diskidlehistogram > output.csv
```

磁盘 I/o，以及相关的信息，例如注册表/cswitch/堆栈上收集信息，以防需要更深入的分析。 `Compact_cswitch`可以用来减小跟踪文件的大小。 下面的示例演示了一套建议 Xperf 标志。

``` syntax
xperf -on dispatcher+PROC_THREAD+LOADER+CSWITCH+COMPACT_CSWITCH +registry+DISK_IO+DISK_IO_INIT+FILEIO -stackwalk cswitch+readythread+DiskReadInit+DiskWriteInit+DiskFlushInit -buffersize 1024
sleep <desired trace time in seconds> or run scenario
xperf -d trace.etl
```

## <a name="related-topics"></a>相关的主题


[Xperf 操作](xperf-actions.md)

 

 







