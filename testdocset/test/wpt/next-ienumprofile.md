---
title: Next
description: "下一步 "
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 488d7957-a6a6-4961-a7ff-aca254e72eb4
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 2a5ed2f511154554a005a5e163fdaeea4952d7de
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="next"></a>下一步 


返回一个数组，其中包含指定的数量的元素。

## <a name="syntax"></a>语法


``` syntax
HRESULT Next
  ([in] ULONG celt,
  [out, size_is(celt), length_is(*pCeltFetched)] IProfile** prgVar,
  [out] ULONG* pCeltFetched)
;
```

## <a name="parameters"></a>参数


<a href="" id="celt"></a>*celt*  
\[在\]返回的元素的数目。

<a href="" id="prgvar"></a>*prgVar*  
\[出\]数组至少*celt*，以包含元素的大小。

<a href="" id="pceltfetched"></a>*pCeltFetched*  
\[出\]指向的元素数的指针返回*rgVar*，则为 NULL。

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
<td><p>函数成功返回数组。</p></td>
</tr>
<tr class="even">
<td><p>S_FALSE</p></td>
<td><p>返回的元素数是少然后<em>celt</em>。</p></td>
</tr>
<tr class="odd">
<td><p>E_POINTER</p></td>
<td><p>指示指针无效。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[IEnumProfile](ienumprofile.md)

 

 







