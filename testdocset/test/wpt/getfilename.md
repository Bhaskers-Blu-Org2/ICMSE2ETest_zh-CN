---
title: GetFileName
description: GetFileName
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 15f12bd8-a977-4c39-8da7-74b51bd7d54a
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: b6b72776e8c90355498b12bcf0bd22b87497ceea
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="getfilename"></a>GetFileName


获取从指定的文件的字符串。

## <a name="syntax"></a>语法


``` syntax
HRESULT GetFileName
  ([out] BSTR* pbstrFileName)
;
```

## <a name="parameters"></a>参数


<a href="" id="pbstrfilename"></a>*pbstrFileName*  
\[出\]一个指针，指向字符串文件的名称。

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

 

 







