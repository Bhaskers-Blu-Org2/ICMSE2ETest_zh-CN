---
title: GetObjectType
description: GetObjectType
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 5df5ef07-aad9-4bbe-a293-05dd18c4b319
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 285f15e6a31d442488f123c75bda8ba4454cd711
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="getobjecttype"></a>GetObjectType


返回引发错误的对象的类型。

## <a name="syntax"></a>语法


``` syntax
HRESULT GetObjectType
  ([out, retval] CObjectType* pObjectType)
;
```

## <a name="parameters"></a>参数


<a href="" id="pobjecttype"></a>*pObjectType*  
\[出\]到**CObjectType**字段，它指示导致错误的元素的指针。

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
<td><p>函数成功返回对象类型。</p></td>
</tr>
<tr class="even">
<td><p>E_POINTER</p></td>
<td><p>无效的指针。</p></td>
</tr>
</tbody>
</table>

 

## <a name="remarks"></a>备注


对象类型可以是下列值之一︰

-   未知

-   配置文件

-   收集器

-   Provider

## <a name="related-topics"></a>相关的主题


[IControlErrorInfo](icontrolerrorinfo.md)

 

 







