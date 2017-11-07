---
title: Cancel
description: Cancel
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 282d79d5-7acd-442a-8528-f5894dfde2dc
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 49c4e016489e6144ec1e1d275d9fb711722f6bb1
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="cancel"></a>Cancel


取消记录而不保存任何数据。

## <a name="syntax"></a>语法


``` syntax
HRESULT Cancel
  ([in] IProfileCollection* pProfileCollection)
;
```

## <a name="parameters"></a>参数


<a href="" id="pprofilecollection"></a>*pProfileCollection*  
\[在\]到[IProfileCollection](iprofilecollection.md)对象，其中包含要取消配置文件的集合的指针。

## <a name="return-value"></a>返回值


下表描述了可能的值。

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
<td><p>E_INVALIDARG</p></td>
<td><p>指针无效。</p></td>
</tr>
<tr class="even">
<td><p>E_WPRC_RUNTIME_STATE_PROFILES_NOT_RUNNING</p></td>
<td><p>当前没有运行配置文件。</p></td>
</tr>
<tr class="odd">
<td><p>ERROR_WMI_INSTANCE_NOT_FOUND</p></td>
<td><p>找不到请求的实例。</p></td>
</tr>
<tr class="even">
<td><p>S_OK</p></td>
<td><p>函数成功返回<strong>IProfileCollection</strong>。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[IControlManager](icontrolmanager.md)

 

 







