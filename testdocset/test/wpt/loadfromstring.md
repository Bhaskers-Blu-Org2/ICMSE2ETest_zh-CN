---
title: LoadFromString
description: LoadFromString
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: c4661c55-e237-4143-af70-dff6de0afe9b
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 2d7507d96d0d9733d6888c496db8e573d09bc292
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="loadfromstring"></a>LoadFromString


从指定的 XML 配置文件定义字符串加载配置文件。

## <a name="syntax"></a>语法


``` syntax
HRESULT LoadFromString
  ([in] BSTR bstrProfile)
;
```

## <a name="parameters"></a>参数


<a href="" id="bstrprofile"></a>*bstrProfile*  
\[在\]字符串包含的 XML 配置文件定义。

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
<td><p>函数成功加载配置文件。</p></td>
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

 

 







