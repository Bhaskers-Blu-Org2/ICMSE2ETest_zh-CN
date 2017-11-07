---
title: GetHResult
description: GetHResult
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 5c7606d5-3a6d-4dc5-b232-ed24974d662c
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 081288b791b6bf7fdc52df51569fca9418522a9e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="gethresult"></a>GetHResult


返回一个 HRESULT 值，该值指示的错误代码。

## <a name="syntax"></a>语法


``` syntax
HRESULT GetHResult
  ([out, retval] HRESULT* pHResult)
;
```

## <a name="parameters"></a>参数


<a href="" id="phresult"></a>*pHResult*  
\[出\]指针，它指向 HRESULT 值，它指示的错误代码。

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
<td><p>函数成功返回的错误代码。</p></td>
</tr>
<tr class="even">
<td><p>E_POINTER</p></td>
<td><p>无效的指针。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[IControlErrorInfo](icontrolerrorinfo.md)

 

 







