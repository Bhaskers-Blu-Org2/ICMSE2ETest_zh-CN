---
title: "保存"
description: "保存"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: eedd3310-1f95-4e44-9be2-b33ed98dfa9a
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: afdfca25fdaf0cb5f9b7a58836f2d78ed4fd3684
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="save"></a>保存


保存录制登录到指定的事件跟踪日志 (ETL) 文件到内存中的循环缓冲区。 录制继续运行。

## <a name="syntax"></a>语法


``` syntax
HRESULT Save
  ([in] BSTR bstrFileName,
  [in] IProfileCollection* pProfileCollection,
  [in] ITraceMergeProperties* pTraceMergeProperties)
;
```

## <a name="parameters"></a>参数


<a href="" id="bstrfilename"></a>*bstrFileName*  
\[在\]从录制的所有配置文件保存到的合并事件的文件的名称。

<a href="" id="pprofilecollection"></a>*pProfileCollection*  
\[在\]到[IProfileCollection](iprofilecollection.md)对象，包含要保存配置文件的集合的指针。

<a href="" id="ptracemergeproperties"></a>*pTraceMergeProperties*  
\[在\]到[ITraceMergeProperties](itracemergeproperties.md)对象，其中包含要合并的记录属性的指针。

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
<td><p>函数成功保存录制。</p></td>
</tr>
<tr class="even">
<td><p>E_INVALIDARG</p></td>
<td><p>一个或多个参数是无效的。</p></td>
</tr>
<tr class="odd">
<td><p>E_WPRC_FAILED_TO_SAVE_PROFILE</p></td>
<td><p>磁带库无法保存配置文件的配置文件集合中。 使用[IControlErrorInfo](icontrolerrorinfo.md)来获取详细的错误信息。</p></td>
</tr>
<tr class="even">
<td><p>E_WPRC_TRACE_MERGE_LOST_EVENTS</p></td>
<td><p>事件跟踪 Windows (ETW) 会话丢失事件，并合并来自会话的事件跟踪日志 (ETL) 文件可能会创建一个不完整的 ETL 文件。</p></td>
</tr>
</tbody>
</table>

 

## <a name="remarks"></a>备注


此函数仅用于为循环缓冲区日志的配置文件。 保存会话后，记录将继续运行。

## <a name="related-topics"></a>相关的主题


[IControlManager](icontrolmanager.md)

 

 







