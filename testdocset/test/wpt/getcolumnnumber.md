---
title: GetColumnNumber
description: GetColumnNumber
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: abe730ac-4c04-48f0-b37c-6e096dca07c5
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 1d9e3ff79047a45f7df055661a00d64224ffef2b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="getcolumnnumber"></a>GetColumnNumber


获取 XML 验证错误发生处的列的编号。

## <a name="syntax"></a>语法


``` syntax
HRESULT GetColumnNumber
  ([out, retval] ULONG* pColumnNumber)
;
```

## <a name="parameters"></a>参数


<a href="" id="pcolumnnumber"></a>*pColumnNumber*  
\[出\]一个指针，指向 XML 验证错误发生处的列的编号。

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
<td><p>函数成功返回的列数。</p></td>
</tr>
<tr class="even">
<td><p>E_POINTER</p></td>
<td><p>指示指针无效。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[IParsingErrorInfo](iparsingerrorinfo.md)

 

 







