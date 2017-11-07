---
title: IsEqual
description: IsEqual
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: b555fa8d-71fc-4ca1-a1e8-592cce52d738
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 2c7eb96c40a433b32ba3a9b1cef1a35b28f7df73
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="isequal"></a>IsEqual


比较两个[IProfile](iprofile.md)对象。

## <a name="syntax"></a>语法


``` syntax
HRESULT IsEqual
  ([in] IProfile* pProfile)
;
```

## <a name="parameters"></a>参数


<a href="" id="pprofile"></a>*pProfile*  
\[在\]到**IProfile**对象进行比较的指针。

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
<td><p>这些对象具有相同的配置文件、 会话和提供程序属性。</p></td>
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


[IProfile](iprofile.md)

 

 







