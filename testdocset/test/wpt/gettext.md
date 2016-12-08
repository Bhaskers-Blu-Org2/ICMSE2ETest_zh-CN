---
title: GetText
description: GetText
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 6abaf7c8-ce52-48af-b4cd-a0039123140c
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 80cb27be746f0bf9783e3cb303e1b6190428f22d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="gettext"></a>GetText


获取指定的文本。

## <a name="syntax"></a>语法


``` syntax
HRESULT GetText
  ([in] ULONG iText,
  [out] BSTR* pbstrText)
;
```

## <a name="parameters"></a>参数


<a href="" id="itext"></a>*iText*  
\[在中\]

<a href="" id="pbstrtext"></a>*pbstrText*  
\[出\]为文本字符串的指针。

## <a name="return-value"></a>返回值


下表描述了可能的返回值。 失败返回值是特定于实现的。

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
<td><p>表示成功。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[ITraceMergeTextHandler](itracemergetexthandler.md)

 

 







