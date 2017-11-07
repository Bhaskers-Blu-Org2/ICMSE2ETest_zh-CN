---
title: IOnOffTransitionManager
description: IOnOffTransitionManager
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 9d719b05-f720-4464-be7a-c991a1d7639e
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 6c8c0baada8cf7fff6fc162a54381e2e5c639b9f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="ionofftransitionmanager"></a>IOnOffTransitionManager


使客户端在[IProfileCollection](iprofilecollection.md)启动跟踪的注册表中存储配置文件但不是运行配置文件。 这种现象与[IControlManager](icontrolmanager.md)，它立即运行该配置文件的完全不同。 当系统启动时，Windows 事件跟踪 (ETW) 读取注册表项，并使提供程序跟踪进行相应的引导。 磁带库通过 PCW 数据集合启动任务计划程序作业配置为在启动运行。

## <a name="syntax"></a>语法


``` syntax
{
  [id(1), helpstring("EnableBootRecording")] HRESULT EnableBootRecording
    ([in] IProfileCollection* pProfileCollection);
  [id(2), helpstring("DisableBootRecording")] HRESULT DisableBootRecording
    ([in] IProfileCollection* pProfileCollection);
  [id(3), helpstring("StartShutdownRecording")] HRESULT StartShutdownRecording
    ([in] IProfileCollection* pProfileCollection);
  [id(4), helpstring("UpdateShutdownRecording")] HRESULT UpdateShutdownRecording
    ([in] IProfileCollection* pProfileCollection);
  [id(5), helpstring("MergeShutdownRecording")] HRESULT MergeShutdownRecording
    ([in] BSTR bstrFileName,
    [in] IProfileCollection* pProfileCollection,
    [in] ITraceMergeProperties* pTraceMergeProperties)
  ;
};
```

## <a name="functions"></a>函数


此接口提供下表中描述的功能。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>函数</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[EnableBootRecording](enablebootrecording.md)</p></td>
<td><p>启用启动记录找不到指定的配置文件。</p></td>
</tr>
<tr class="even">
<td><p>[DisableBootRecording](disablebootrecording.md)</p></td>
<td><p>禁用启动记录找不到指定的配置文件。</p></td>
</tr>
<tr class="odd">
<td><p>[StartShutdownRecording](startshutdownrecording.md)</p></td>
<td><p>启动关机录制。</p></td>
</tr>
<tr class="even">
<td><p>[UpdateShutdownRecording](updateshutdownrecording.md)</p></td>
<td><p>更新关闭记录。</p></td>
</tr>
<tr class="odd">
<td><p>[MergeShutdownRecording](mergeshutdownrecording.md)</p></td>
<td><p>将合并关闭录制。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[接口](interfaces-wprcontrol.md)

 

 







