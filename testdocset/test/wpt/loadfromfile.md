---
title: LoadFromFile
description: LoadFromFile
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 8816f97e-aa11-4e02-ade7-537e0b288cce
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: d8e973f3cde02a6e5fc5ee93dc80bede41540a27
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="loadfromfile"></a>LoadFromFile


从文件中加载配置文件。

## <a name="syntax"></a>语法


``` syntax
HRESULT LoadFromFile
  ([in] BSTR bstrProfileName,
  [in] BSTR bstrFileName)
;
```

## <a name="parameters"></a>参数


<a href="" id="bstrprofilename"></a>*bstrProfileName*  
\[在\]要加载的配置文件的名称。

<a href="" id="bstrfilename"></a>*bstrFileName*  
\[在\]文件包含配置文件的名称。

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
<td><p>表示成功。</p></td>
</tr>
<tr class="even">
<td><p>E_INVALIDARG</p></td>
<td><p>一个或多个参数是无效的。 使用[IParsingErrorInfo](iparsingerrorinfo.md)来获取详细的错误信息。</p></td>
</tr>
<tr class="odd">
<td><p>E_WPRC_FAILED_TO_VALIDATE_PROFILE</p></td>
<td><p>磁带库未通过验证的配置文件。 使用<strong>IParsingErrorInfo</strong>来获取详细的错误信息。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[IProfile](iprofile.md)

 

 







