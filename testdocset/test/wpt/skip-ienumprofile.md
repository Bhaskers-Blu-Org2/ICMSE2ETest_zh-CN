---
title: "跳过"
description: "跳过"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 3cf0d9c8-d456-424a-8d33-1f900f78595e
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 264fe68623582c1145f5bf80a7074cb05d9ae6d9
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="skip"></a>跳过


指示要跳过元素的数。

## <a name="syntax"></a>语法


``` syntax
HRESULT Skip
  ([in] ULONG celt)
;
```

## <a name="parameters"></a>参数


<a href="" id="celt"></a>*celt*  
\[在\]要跳过的元素数。

## <a name="return-value"></a>返回值


下表描述了可能的返回值。

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
<td><p>函数成功返回要跳过元素的数。</p></td>
</tr>
<tr class="even">
<td><p>S_FALSE</p></td>
<td><p>返回的元素数是少然后<em>celt</em>。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[IEnumProfile](ienumprofile.md)

 

 







