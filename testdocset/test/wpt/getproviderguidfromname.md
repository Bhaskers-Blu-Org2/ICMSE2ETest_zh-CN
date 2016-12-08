---
title: GetProviderGuidFromName
description: GetProviderGuidFromName
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 855b63df-307e-4e10-bb83-561fa71e13c2
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: d6a290dac5a2a01bbd788eb3a6f8e91867b668a2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="getproviderguidfromname"></a>GetProviderGuidFromName


获取具有指定名称的 GUID 关联的提供程序。

## <a name="syntax"></a>语法


``` syntax
HRESULT GetProviderGuidFromName
  ([out] GUID* ProviderId,
  [in] BSTR bstrProViderName)
;
```

## <a name="parameters"></a>参数


<a href="" id="guid--providerid"></a>*GUID\* ProviderId*  
\[出\]指示提供程序标识符的 GUID。

<a href="" id="bstr-bstrprovidername"></a>*BSTR bstrProViderName*  
\[在\]string 类型的值，该值指示提供程序的名称。

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
<td><p>E_WPRC_FAILED_TO_TRANSLATE_EVENT_PROVIDER_NAME_TO_GUID</p></td>
<td><p>WPR 无法转换为 GUID 的事件提供程序名称。</p></td>
</tr>
<tr class="even">
<td><p>S_OK</p></td>
<td><p>函数成功返回 GUID。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[IControlManager](icontrolmanager.md)

 

 







