---
title: WaitForText
description: WaitForText
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: d030b3b3-421e-4cc1-9752-d5f69a011fae
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: de6cbbffc028249c74a5490b1e577aa8331a56fb
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="waitfortext"></a>WaitForText


等待，直到用户添加适当的文本字符串，并调用 SetTextAvailable。

## <a name="syntax"></a>语法


``` syntax
HRESULT WaitForText
  ([in] ULONG Milliseconds)
;
```

## <a name="parameters"></a>参数


<a href="" id="milliseconds"></a>*毫秒*  
\[在\]指示等待延迟的毫秒数。

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

 

 







