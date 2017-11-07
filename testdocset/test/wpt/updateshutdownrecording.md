---
title: UpdateShutdownRecording
description: UpdateShutdownRecording
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 0efaf47c-ca92-4be2-bfd4-f71a6b300297
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 18f10624ad93e2c7ddd75bfc1051d94acc719431
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="updateshutdownrecording"></a>UpdateShutdownRecording


更新关闭记录。

## <a name="syntax"></a>语法


``` syntax
HRESULT MergeShutdownRecording
  ([in] BSTR bstrFileName,
  [in] IProfileCollection* pProfileCollection,
  [in] ITraceMergeProperties* pTraceMergeProperties)
;
```

## <a name="parameters"></a>参数


<a href="" id="bstrfilename"></a>*bstrFileName*  
\[在\]指示记录了事件的事件跟踪日志 (ETL) 文件的名称。

<a href="" id="pprofilecollection"></a>*pProfileCollection*  
\[在\]表示**IProfileCollection**对象。

<a href="" id="ptracemergeproperties"></a>*pTraceMergeProperties*  
\[在\]表示**ITraceMergeProperties**对象。

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
<td><p>函数成功更新关闭记录。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[IOnOffTransitionManager](ionofftransitionmanager.md)

 

 







