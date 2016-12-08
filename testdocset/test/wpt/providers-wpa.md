---
title: "提供程序"
description: "提供程序"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 19c60e7c-2673-4e7c-9b04-978ac94ce812
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: e93a58e7493fa0db5fdd7aa43dc43943f558c1be
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="providers"></a>提供程序


显示可用的提供程序和组。

``` syntax
xperf -providers [Installed|I] [Registered|R] [KernelFlags|KF] [KernelGroups|KG] [Kernel|K]
```

## <a name="remarks"></a>备注


此选项会查询所有安装已知且已注册提供程序，以及所有已知的内核标志和组。

支持下表中的选项。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>选项</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>我安装</strong></p></td>
<td><p>包括安装已知提供程序。</p></td>
</tr>
<tr class="even">
<td><p><strong>R 注册</strong></p></td>
<td><p>包括已注册的提供程序。</p></td>
</tr>
<tr class="odd">
<td><p><strong>KF KernelFlags</strong></p></td>
<td><p>包括内核的标志。</p></td>
</tr>
<tr class="even">
<td><p><strong>公斤 KernelGroups</strong></p></td>
<td><p>包括内核组。</p></td>
</tr>
<tr class="odd">
<td><p><strong>K 内核</strong></p></td>
<td><p>包括内核标志和组;快捷方式&quot;KF 公斤&quot;。</p></td>
</tr>
</tbody>
</table>

 

如果未不指定任何选项，输出中包含的所有提供程序。

## <a name="related-topics"></a>相关的主题


[Xperf 选项](xperf-options.md)

 

 







