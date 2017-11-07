---
title: GetInnerErrorInfo
description: GetInnerErrorInfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: f3cfd46e-bed5-47fd-a2bb-f7e34f7877c6
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: ad7c8f10f69fd45372fe6f00117511a7e551c9d1
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="getinnererrorinfo"></a>GetInnerErrorInfo


返回有关错误的其他信息。

## <a name="syntax"></a>语法


``` syntax
HRESULT GetInnerErrorInfo
  ([out, retval] IUnknown** ppVal)
;
```

## <a name="parameters"></a>参数


<a href="" id="ppval"></a>*ppVal*  
\[出\]指针，它指向[IUnknown](http://go.microsoft.com/fwlink/p/?linkid=217447)接口，它提供有关导致错误的其他信息。 如果没有内部信息，则此参数为 NULL。

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
<td><p>函数成功返回错误信息。</p></td>
</tr>
<tr class="even">
<td><p>S_FALSE</p></td>
<td><p>指示没有其他错误的信息是可用的并且<em>ppVal</em>为空。</p></td>
</tr>
<tr class="odd">
<td><p>E_POINTER</p></td>
<td><p>指示指针无效。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[IControlErrorInfo](icontrolerrorinfo.md)

 

 







