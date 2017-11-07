---
title: LoadFromString
description: LoadFromString
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: c1066650-2cf9-4ac0-bf68-9895465a844d
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: beadf42e90081242720646b94512b49114f4cd73
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="loadfromstring"></a>LoadFromString


加载跟踪合并 XML 定义字符串中的属性。

## <a name="syntax"></a>语法


``` syntax
HRESULT LoadFromString
  ([in] BSTR bstrTraceMerge)
;
```

## <a name="parameters"></a>参数


<a href="" id="bstrtracemerge"></a>*bstrTraceMerge*  
\[在\]的字符串，其中包含 XML 格式跟踪合并属性。

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
<td><p>函数成功加载属性。</p></td>
</tr>
<tr class="even">
<td><p>E_INVALIDARG</p></td>
<td><p>一个或多个参数是无效的。 使用[IParsingErrorInfo](iparsingerrorinfo.md)来获取详细的错误信息。</p></td>
</tr>
<tr class="odd">
<td><p>E_WPRC_FAILED_TO_VALIDATE_TRACEMERGE_PROPERTIES</p></td>
<td><p>磁带库未通过验证的 XML 跟踪合并属性。 使用<strong>IParsingErrorInfo</strong>来获取详细的错误信息。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[ITraceMergeProperties](itracemergeproperties.md)

 

 







