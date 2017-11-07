---
title: DisableBootRecording
description: DisableBootRecording
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 9de515ce-d77e-4a5d-95d8-b611eea5394a
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: f3acd804f134a00ea38f514d7e7b1f0a4b242b95
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="disablebootrecording"></a>DisableBootRecording


禁用启动记录找不到指定的配置文件。

## <a name="syntax"></a>语法


``` syntax
HRESULT DisableBootRecording
  ([in] IProfileCollection* pProfileCollection)
;
```

## <a name="parameters"></a>参数


<a href="" id="pprofilecollection"></a>*pProfileCollection*  
\[在\]到[IProfileCollection](iprofilecollection.md)对象包含的配置文件，以便它们在启动过程中无法启动必须删除的集合的指针。

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
<td><p>已成功禁用的函数启动录音。</p></td>
</tr>
<tr class="even">
<td><p>E_WPRC_FAILED_TO_DISABLE_PROFILES_FOR_BOOT_TRACING</p></td>
<td><p>磁带库无法删除的配置文件。 使用[IControlErrorInfo](icontrolerrorinfo.md)来获取详细的错误信息。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[IOnOffTransitionManager](ionofftransitionmanager.md)

 

 







