---
title: LoadFromFile
description: LoadFromFile
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 73d323b7-1a32-4f0a-aa5a-bd61d96af687
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 373d41207a35324b0065b3c5f797db49dce01b3e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="loadfromfile"></a>LoadFromFile


从文件加载跟踪合并属性。

## <a name="syntax"></a>语法


``` syntax
HRESULT LoadFromFile
  ([in] BSTR bstrTraceMergeName,
  [in] BSTR bstrFileName)
;
```

## <a name="parameters"></a>参数


<a href="" id="bstrtracemergename"></a>*bstrTraceMergeName*  
\[在\]要加载的合并属性的名称。

<a href="" id="bstrfilename"></a>*bstrFileName*  
\[在\] *bstrTraceMergeName*合并属性包含的文件的名称。

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
<td><p>磁带库未通过验证的 XML 定义跟踪合并属性。 使用<strong>IParsingErrorInfo</strong>来获取详细的错误信息。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[ITraceMergeProperties](itracemergeproperties.md)

 

 







