---
title: MergeShutdownRecording
description: MergeShutdownRecording
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 3f8ac92e-53f4-4f48-8862-d165c84b697e
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 3518cd581cf404884f76f73ce4be3160730102f6
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mergeshutdownrecording"></a>MergeShutdownRecording


合并在上次关机过程中收集的唱片。

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
\[在\]指示要记录的事件跟踪的 Windows (ETL) 文件的名称。

<a href="" id="pprofilecollection"></a>*pProfileCollection*  
\[在\]到**IProfileCollection**对象的指针。

<a href="" id="ptracemergeproperties"></a>*pTraceMergeProperties*  
\[在\]到**ITraceMergeProperties**对象的指针。

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
<td><p>E_POINTER</p></td>
<td><p>至少一个函数的参数为空。</p></td>
</tr>
<tr class="even">
<td><p>E_WPRC_INVALID_MERGESHUTDOWN_OPERATION</p></td>
<td><p>指示不成功的操作。 如果没有关闭录制运行上次关机时都会出现此问题。</p></td>
</tr>
<tr class="odd">
<td><p>E_WPRC_RUNTIME_STATE_PROFILES_NOT_RUNNING</p></td>
<td><p>表示配置文件未在运行。 如果没有关闭录制运行上次关机时都会出现此问题。</p></td>
</tr>
<tr class="even">
<td><p>S_OK</p></td>
<td><p>函数成功合并关闭记录。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[IOnOffTransitionManager](ionofftransitionmanager.md)

 

 







