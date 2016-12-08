---
title: "Xperf 内置配置文件"
description: "Xperf 内置配置文件"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 5628e0c0-5882-4b83-b8c1-058e5a125c68
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 833421904f3db858bee5e925aea0660f6cf2f1eb
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="xperf-built-in-profiles"></a>Xperf 内置配置文件


若要显示所有的内置 Xperf 配置文件，请运行下面的命令。

``` syntax
xperf -profiles
```

下表描述了可用的配置文件。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>配置文件</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>性能 ！FileIOProfiles.InSequentialFile</p></td>
<td><p>顺序文件中的文件 I/O 跟踪配置文件。</p></td>
</tr>
<tr class="even">
<td><p>性能 ！FileIOProfiles.InBuffer</p></td>
<td><p>在缓冲区中的文件 I/O 跟踪配置文件。</p></td>
</tr>
<tr class="odd">
<td><p>性能 ！GeneralProfiles.InSequentialFile</p></td>
<td><p>公共系统指标跟踪配置文件的顺序文件中。</p></td>
</tr>
<tr class="even">
<td><p>性能 ！GeneralProfiles.InBuffer</p></td>
<td><p>通用系统指标跟踪配置文件的缓冲区中。</p></td>
</tr>
<tr class="odd">
<td><p>性能 ！PerfCoreProfiles.InSequentialFile</p></td>
<td><p>在顺序文件中跟踪配置文件 （包括所有内置的配置文件） 的基本系统指标。</p></td>
</tr>
<tr class="even">
<td><p>性能 ！PerfCoreProfiles.InBuffer</p></td>
<td><p>基本系统跟踪配置文件 （包括所有内置的配置文件） 的缓冲区中的度量标准。</p></td>
</tr>
<tr class="odd">
<td><p>性能 ！RegistryProfiles.InSequentialFile</p></td>
<td><p>在顺序文件中的注册表跟踪配置文件。</p></td>
</tr>
<tr class="even">
<td><p>性能 ！RegistryProfiles.InBuffer</p></td>
<td><p>注册表的缓冲区中跟踪配置文件。</p></td>
</tr>
<tr class="odd">
<td><p>性能 ！StdProfile</p></td>
<td><p>（无法启动） 的内置配置文件中使用的一般定义。</p></td>
</tr>
</tbody>
</table>

 

## <a name="examples"></a>示例


下面的示例打开几种 ETW 会话，并根据需要将它们合并到一个单一的跟踪文件。

**基于内存的跟踪配置文件**

内存中重复执行快照跟踪配置文件，运行下面的命令。

``` syntax
xperf -start perf!GeneralProfiles.InBuffer
```

运行某些方案，然后再运行下面的命令。

``` syntax
xperf -save perf!GeneralProfiles.InBuffer snapshot1.etl
```

可还可以继续保存其他快照，并随即停止跟踪捕获通过运行下面的命令。

``` syntax
xperf -cancel perf!GeneralProfiles.InBuffer
```

**基于文件的跟踪配置文件**

要启动一个基于文件的跟踪配置文件，请运行以下命令。

``` syntax
xperf -start perf!RegistryProfiles.InSequentialFile
```

运行某些方案，然后再运行以下命令来停止跟踪捕获。

``` syntax
xperf -stop perf!RegistryProfiles.InSequentialFile trace.etl
```

**扩展配置文件定义**

配置文件定义可以扩展和包括使用命令行。 例如，将**ReadyThread**堆栈添加到**性能 ！FileIOProfiles.InSequentialFile**配置文件，运行下面的命令。

``` syntax
xperf -start perf!FileIOProfiles.InSequentialFile -stackwalk ReadyThread
```

## <a name="related-topics"></a>相关的主题


[Xperf 配置文件](xperf-profiles.md)

 

 







