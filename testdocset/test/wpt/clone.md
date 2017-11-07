---
title: "克隆"
description: "克隆"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 0f8f2e42-f67c-4523-a81a-5a2e34dc4e8f
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: d1b57ff1ed18dd92acb398fc5a9afabdbda8e134
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="clone"></a>克隆


克隆的一整个套错误和警告。

## <a name="syntax"></a>语法


``` syntax
HRESULT Clone
  ([out] IEnumControlWarningInfo** ppEnum)
;
```

## <a name="parameters"></a>参数


<a href="" id="ppenum"></a>*ppEnum*  
\[出\]在返回到克隆枚举器的位置的指针。

## <a name="return-value"></a>返回值


下表描述了可能的值。

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


[IEnumControlWarningInfo](ienumcontrolwarninginfo.md)

 

 







