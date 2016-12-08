---
title: GetLineNumber
description: GetLineNumber
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: d25dc5f0-386e-4dc1-aaaf-c59523a23c21
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: fda23c88689d8da992a0a6be66cd61139fb37292
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="getlinenumber"></a>GetLineNumber


获取 XML 验证错误发生处的行号。

## <a name="syntax"></a>语法


``` syntax
HRESULT GetLineNumber
  ([out, retval] ULONG* pLineNumber)
;
```

## <a name="parameters"></a>参数


<a href="" id="plinenumber"></a>*pLineNumber*  
\[出\]一个指针，指向 XML 验证错误发生处的行号。

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
<td><p>函数成功返回的行号。</p></td>
</tr>
<tr class="even">
<td><p>E_POINTER</p></td>
<td><p>指针无效。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[IParsingErrorInfo](iparsingerrorinfo.md)

 

 







