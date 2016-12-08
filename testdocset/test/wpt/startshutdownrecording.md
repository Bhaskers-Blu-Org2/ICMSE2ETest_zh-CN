---
title: StartShutdownRecording
description: StartShutdownRecording
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 763c2f77-aeed-43af-9238-c0a041e02867
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 861ed47cb4687eedea3ccd778726e9baedf9bed5
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="startshutdownrecording"></a>StartShutdownRecording


启动关机录制。

## <a name="syntax"></a>语法


``` syntax
HRESULT StartShutdownRecording
  ([in] IProfileCollection* pProfileCollection)
;
```

## <a name="parameters"></a>参数


<a href="" id="pprofilecollection"></a>*pProfileCollection*  
\[在\]表示**IProfileCollection**对象。

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
<td><p>已成功启动关闭录音功能。</p></td>
</tr>
<tr class="even">
<td><p>E_POINTER</p></td>
<td><p>至少一个函数参数为空。</p></td>
</tr>
<tr class="odd">
<td><p>E_WPRC_RUNTIME_STATE_PROFILES_RUNNING</p></td>
<td><p>录制已在运行 （它应停止/取消之前对此函数的调用）。</p></td>
</tr>
<tr class="even">
<td><p>E_WPRC_RUNTIME_STATE_BOOT_RECORDING</p></td>
<td><p>正在运行启动录制 （它应停止/取消之前对此函数的调用）。</p></td>
</tr>
<tr class="odd">
<td><p>E_WPRC_RUNTIME_STATE_EVENT_SESSION_RUNNING</p></td>
<td><p>一个应启动的事件会话已在运行。 它可能被其他应用程序 （或由于 WPR 状态损坏，例如 WPR 崩溃之后） 早启动。</p></td>
</tr>
<tr class="even">
<td><p>E_WPRC_INVALID_STARTSHUTDOWN_OPERATION</p></td>
<td><p>关闭录音的无效配置文件 （例如，日志记录模式是内存，但只有关机所支持的文件）。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[IOnOffTransitionManager](ionofftransitionmanager.md)

 

 







