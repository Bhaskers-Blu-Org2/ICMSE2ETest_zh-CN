---
title: IsEqual
description: IsEqual
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: ad2c2023-6748-4fc3-b2c4-02bf92637dc0
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: a9a5af2d07ccbbae535289ef80e5f3fbf2d1ab2c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="isequal"></a>IsEqual


比较两个[ITraceMergeProperties](itracemergeproperties.md)对象。

## <a name="syntax"></a>语法


``` syntax
HRESULT IsEqual
  ([in] ITraceMergeProperties* pTraceMergeProperties)
;
```

## <a name="parameters"></a>参数


<a href="" id="ptracemergeproperties"></a>*pTraceMergeProperties*  
\[在\]到**ITraceMergeProperties**对象进行比较的指针。

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
<td><p>这些对象具有相同合并属性的跟踪。</p></td>
</tr>
<tr class="even">
<td><p>S_FALSE</p></td>
<td><p>对象不具有相同的跟踪合并属性。</p></td>
</tr>
<tr class="odd">
<td><p>E_INVALIDARG</p></td>
<td><p>一个或多个参数是无效的。 使用[IParsingErrorInfo](iparsingerrorinfo.md)来获取详细的错误信息。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[ITraceMergeProperties](itracemergeproperties.md)

 

 







