---
title: IsEqual
description: IsEqual
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 358b6599-0360-47ee-bac7-8ae0f119c01f
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: d7330fa7884dfecb104dabd316d83881efb60366
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="isequal"></a>IsEqual


比较两个[IProfileCollection](iprofilecollection.md)对象以查看它们是否具有匹配的配置文件属性。 不考虑到配置文件的顺序。

## <a name="syntax"></a>语法


``` syntax
HRESULT IsEqual
  ([in] IProfileCollection* pProfileCollection)
;
```

## <a name="parameters"></a>参数


<a href="" id="pprofilecollection"></a>*pProfileCollection*  
\[在\]到**IProfileCollection**对象进行比较的指针。

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
<td><p>配置文件的集合相等。</p></td>
</tr>
<tr class="even">
<td><p>S_FALSE</p></td>
<td><p>对象不相等。</p></td>
</tr>
<tr class="odd">
<td><p>E_INVALIDARG</p></td>
<td><p>一个或多个参数是无效的。 有关详细的错误信息，请参见[IParsingErrorInfo](iparsingerrorinfo.md) 。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[IProfileCollection](iprofilecollection.md)

 

 







