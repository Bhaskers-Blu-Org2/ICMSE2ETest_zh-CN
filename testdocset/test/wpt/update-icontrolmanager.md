---
title: Update
description: Update
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 4d3707c3-2694-47e9-845b-8d3767c0b2cc
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: e46e4d41257b5bb0915c53f02e7e615534ce363e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="update"></a>Update


更新配置文件集合。

## <a name="syntax"></a>语法


``` syntax
HRESULT Update
  ([in] IProfileCollection* pProfileCollection)
;
```

## <a name="parameters"></a>参数


<a href="" id="pprofilecollection"></a>*pProfileCollection*  
\[在\] [IProfileCollection](iprofilecollection.md)对象，其中包含要更新配置文件的集合的指针。

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
<td><p>函数成功更新<strong>IProfileCollection</strong>。</p></td>
</tr>
<tr class="even">
<td><p>E_INVALIDARG</p></td>
<td><p>一个或多个参数是无效的。</p></td>
</tr>
<tr class="odd">
<td><p>E_WPRC_FAILED_TO_UPDATE_PROFILE</p></td>
<td><p>磁带库未通过更新配置文件的配置文件集合中。 使用[IControlErrorInfo](icontrolerrorinfo.md)来获取详细的错误信息。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[IControlManager](icontrolmanager.md)

 

 







