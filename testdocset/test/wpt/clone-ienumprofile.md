---
title: "克隆"
description: "克隆"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 057b095c-c244-434e-bf0f-09fb54089390
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: cb7606ab61862e2e418e7867a6a97ef9fa9e3258
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="clone"></a>克隆


创建克隆枚举器。

## <a name="syntax"></a>语法


``` syntax
HRESULT Clone
  ([out] IEnumProfile** ppEnum)
;
```

## <a name="parameters"></a>参数


<a href="" id="ppenum"></a>*ppEnum*  
\[出\]指针返回到克隆枚举器的位置。

## <a name="return-value"></a>返回值


下表描述了可能的返回值。

## <a name="exceptions"></a>异常


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>返回值</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>S_OK</p></td>
<td><p>已成功创建克隆枚举器的函数。</p></td>
</tr>
<tr class="even">
<td><p>E_OUTOFMEMORY</p></td>
<td><p>指示内存不足，无法完成该操作。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[IEnumProfile](ienumprofile.md)

 

 







