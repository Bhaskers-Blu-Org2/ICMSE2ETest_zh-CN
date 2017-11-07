---
title: GetElementType
description: GetElementType
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 4546c402-5966-4f36-acad-51418a1698d1
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 4cfd8e0fbcf6b846130a5c3431a3483a473a96a9
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="getelementtype"></a>GetElementType


返回的 XML 验证错误发生处的元素的类型。

## <a name="syntax"></a>语法


``` syntax
HRESULT GetElementType
  ([out, retval] BSTR* pbstrElementType)
;
```

## <a name="parameters"></a>参数


<a href="" id="pbstrelementtype"></a>*pbstrElementType*  
\[出\]为 XML 验证错误发生处的元素的类型的指针。

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
<td><p>函数成功返回的元素类型。</p></td>
</tr>
<tr class="even">
<td><p>E_POINTER</p></td>
<td><p>指针无效。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[IParsingErrorInfo](iparsingerrorinfo.md)

 

 







