---
title: "查询"
description: "查询"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 676f0ed9-641c-49ea-882f-0607e387f8d0
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 32a7cef399ab29cee540cea7e98a3d12c71cc122
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="query"></a>查询


查询会话和所有配置文件中的提供程序的属性。

## <a name="syntax"></a>语法


``` syntax
HRESULT Query
  ([out] BSTR* pbstrResults,
  [in] VARIANT_BOOL fValidateRuntimeState)
;
```

## <a name="parameters"></a>参数


<a href="" id="pbstrresults"></a>*pbstrResults*  
\[出\]WPRC 库启动包含会话和提供程序的所有配置文件属性的 XML 格式的字符串。

<a href="" id="fvalidateruntimestate"></a>*fValidateRuntimeState*  
\[在\]boolean 值，指示是否应确定库是否正在运行录制。

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
<td><p>S_OK</p></td>
<td><p>函数成功返回属性。</p></td>
</tr>
<tr class="even">
<td><p>E_POINTER</p></td>
<td><p>指针无效。</p></td>
</tr>
<tr class="odd">
<td><p>E_WPRC_FAILED_TO_QUERY_PROFILES</p></td>
<td><p>磁带库无法查询会话和中的所有配置文件提供程序的属性。 使用[IControlErrorInfo](icontrolerrorinfo.md)来获取详细的错误信息。</p></td>
</tr>
<tr class="even">
<td><p>E_WPRC_INVALID_PROFILES_RUNTIME_STATE</p></td>
<td><p>在系统运行的配置文件列表不匹配那些用来开始录制。 有关详细的错误信息，请参见<strong>IControlErrorInfo</strong> 。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[IControlManager](icontrolmanager.md)

 

 







