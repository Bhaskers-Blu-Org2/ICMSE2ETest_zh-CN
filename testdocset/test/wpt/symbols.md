---
title: "符号"
description: "符号"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 7d34c86b-3b0c-40b1-a71d-b23978f97edf
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: b196f9f5790621af998ae6e7d36bab50345bef9a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="symbols"></a>符号


启用并配置符号解码支持。

``` syntax
xperf -i <trace file>… [-o output] -symbols [cacheonly] [verbose] [dbghelplog]
```

## <a name="parameters"></a>参数


<a href="" id="cacheonly"></a>*cacheonly*  
使用 SymCache，但不是 DbgHelp。 此选项可加快符号解码与缺少符号文件毕竟有趣的符号文件都已转换代码的二进制图像多跟踪。

<a href="" id="verbose"></a>*详细*  
详细模式。 打印符号路径和版本信息。 有关详细信息，请参见[加载符号](loading-symbols.md)。

<a href="" id="dbghelplog"></a>*dbghelplog*  
使有关**stderr**DbgHelp 调试日志。

符号解码支持进一步的 DbgHelp 和 SymCache 的配置下表中使用环境变量。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>_NT_SYMBOL_PATH</p></td>
<td><p>指定的 DbgHelp 路径搜索来查找符号文件 （用.pdb 文件扩展名） 对应于二进制图像文件中跟踪使用。 请参阅下面的关于此变量。</p></td>
</tr>
<tr class="even">
<td><p>_NT_SYMCACHE_PATH</p></td>
<td><p>指定本地 SymCache 目录的路径。 默认情况下，使用 \SymCache。</p></td>
</tr>
</tbody>
</table>

 

**请注意**  
符号解码，跟踪必须是内核跟踪 （或结合内核跟踪处理用户跟踪），其过程\_+ 加载程序线程的内核标志启用，并且，已停止和合并在一起`-d`或`-merge`拍摄它时的计算机上。 Xperf 使符号解码其自定义跟踪合并过程执行专门的图像识别过程。

 

## <a name="remarks"></a>备注


如果未在命令行上指定此行动，已禁用符号进行解码。

## <a name="related-topics"></a>相关的主题


[Xperf 选项](xperf-options.md)

[加载符号](loading-symbols.md)

[深入分析常见问题](../assessments/common-in-depth-analysis-issues.md)

 

 







