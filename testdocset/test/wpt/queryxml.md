---
title: QueryXML
description: QueryXML
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 1dd74aaf-f16c-47f8-9eda-876a404ef59a
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: e91500966ce819055f367e990285a82e1a4c7497
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="queryxml"></a>QueryXML


指示当前正在运行的配置文件和配置文件是否正确运行的 XML 格式。

## <a name="syntax"></a>语法


``` syntax
HRESULT QueryXML
  ([out] BSTR* pbstrResults,
  [in] VARIANT_BOOL fValidateRuntimeState)
;
```

## <a name="parameters"></a>参数


<a href="" id="bstr--pbstrresults"></a>*BSTR\* pbstrResults*  
\[出\]到结果字符串的指针。

<a href="" id="variant-bool-fvalidateruntimestate"></a>*Variant 类型的值\_BOOL fValidateRuntimeState*  
\[在\]boolean 类型的值，该值指示运行时状态是否有效。

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
<td><p>E_WPRC_RUNTIME_STATE_PROFILES_NOT_RUNNING</p></td>
<td><p>表示配置文件未在运行。</p></td>
</tr>
<tr class="even">
<td><p>S_OK</p></td>
<td><p>函数成功返回的 XML 格式。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[IControlManager](icontrolmanager.md)

 

 







