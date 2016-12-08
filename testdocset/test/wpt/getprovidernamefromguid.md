---
title: GetProviderNameFromGuid
description: GetProviderNameFromGuid
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 65612d2b-6fa2-4bda-b183-8e25d62605c1
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 3b668cc021c4e3e92b954034d8cf84eb59d39ebc
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="getprovidernamefromguid"></a>GetProviderNameFromGuid


获取与 GUID 标识符关联的提供程序名称。

## <a name="syntax"></a>语法


``` syntax
HRESULT GetProviderNameFromGuid
  ([out] BSTR* bstrProviderIdStr,
  [in] REFGUID ProviderId)
;
```

## <a name="parameters"></a>参数


<a href="" id="bstr--bstrprovideridstr"></a>*BSTR\* bstrProviderIdStr*  
\[出\]string 类型的值，该值指示提供程序的名称。

<a href="" id="refguid-providerid"></a>*REFGUID ProviderId*  
\[在\]指示提供程序标识符的 GUID。

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
<td><p>E_WPRC_FAILED_TO_TRANSLATE_GUID_TO_EVENT_PROVIDER_NAME</p></td>
<td><p>WPR 未能转换为事件提供程序名称的 GUID。</p></td>
</tr>
<tr class="even">
<td><p>S_OK</p></td>
<td><p>函数成功返回该名称。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[IControlManager](icontrolmanager.md)

 

 







