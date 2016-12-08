---
title: GetElementId
description: GetElementId
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 43a95260-6098-47a9-b087-fd1b477af263
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: c49541f168fbff75272b4a695f6d901eaea4554c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="getelementid"></a>GetElementId


返回的 XML 验证错误发生处的元素的标识符。

## <a name="syntax"></a>语法


``` syntax
HRESULT GetElementId
  ([out, retval] BSTR* pbstrElementId)
;
```

## <a name="parameters"></a>参数


<a href="" id="pbstrelementid"></a>*pbstrElementId*  
\[出\]一个指针，指向 XML 验证错误发生处的元素的标识符。

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
<td><p>函数成功返回元素标识符。</p></td>
</tr>
<tr class="even">
<td><p>E_POINTER</p></td>
<td><p>指针无效。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[IParsingErrorInfo](iparsingerrorinfo.md)

 

 







