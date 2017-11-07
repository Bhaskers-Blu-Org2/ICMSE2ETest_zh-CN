---
title: "WPA 查询语法"
description: "WPA 查询语法"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: b62dfcb3-1900-438f-84ac-9e6113de67bb
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: ac56b3c766489016e37bb0aa6336f212609b60a7
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wpa-query-syntax"></a>WPA 查询语法


语法搜索和过滤组件的 Windows 性能分析器 (WPA) 是 Windows 查询语法的扩展。 有关详细信息，请参阅[高级查询语法](http://go.microsoft.com/fwlink/p/?linkid=229849)。

## <a name="available-extensions"></a>可用的扩展


下表描述了可用的扩展。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>说明</th>
<th>示例</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>如果空格或字符括在方括号中，属性名称可以包含空格和其他非字母数字字符。</p></td>
<td><p><code>[All Count]:&gt;0</code></p>
<p><code>[% Weight]:= 5.6</code></p></td>
</tr>
<tr class="even">
<td><p>字符串类型允许<strong>正则表达式</strong>运算符 （*） 星号。</p></td>
<td><p>下面的查询匹配<em>iexplore</em>和<em>资源管理器中</em>，但不是<em>myexplorer</em>:</p>
<p><code>ProcessName:* '.?explore.*'</code></p></td>
</tr>
<tr class="odd">
<td><p>内存大小后缀 （KB、 MB、 GB） 和时间单位 (s，ms，我们 ns) 上双和整数支持文本。 这些后缀是不区分大小写。</p></td>
<td><p><code>Size :&gt; 20MB AND Size :&lt; 0.5GB</code></p>
<p><code>Duration :&gt; 5ms OR Duration :&lt; 1us</code></p></td>
</tr>
<tr class="even">
<td><p>支持灵活精度相等运算的浮动文本。 精度取决于查询中包含的十进制数字的数量。</p></td>
<td><p><code>Duration := 4.5ms</code> 有可能产生较大的结果集比<code>Duration :=4.50ms</code>。</p></td>
</tr>
</tbody>
</table>

 

您可以限制搜索范围的行的子集︰ 系列名称。 系列名称是左侧的金色栏最右边的非空列的名称。 在下面的表中，行 1-6 系列名称是*过程*。 对于所有其他行中，系列名称是*模块*。

![wpa 搜索](images/wpasearch.jpg)

如果查询的`Process:~='iexplore'`，选择行 6-13。

如果查询的`Process:~='iexplore' AND [Series Name] := 'Process'`，选择仅行 6。

如果查询的`Process:~'iexplore' AND [Series Name] := 'Module'`，选择 7-13 行。

## <a name="related-topics"></a>相关的主题


[WPA 功能](wpa-features.md)

 

 







