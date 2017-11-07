---
title: Start
description: Start
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 58474a2e-2e53-487e-8cca-a09959559fb7
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: c8bba10d7e9176eaa7c1e57db0e2746fda799905
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="start"></a>Start


开始录制。

## <a name="syntax"></a>语法


``` syntax
HRESULT Start
  ([in] IProfileCollection* pProfileCollection,
  [out, retval] CLoggingMode* pLoggingMode)
;
```

## <a name="parameters"></a>参数


<a href="" id="pprofilecollection"></a>*pProfileCollection*  
\[在\] **IProfileCollection**对象，其中包含配置文件开始的集合的指针。

<a href="" id="ploggingmode"></a>*pLoggingMode*  
\[出\] **CLoggingMode**枚举元素，它指示配置文件登录到内存或写入文件的指针。

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
<td><p>已成功启动录制功能。</p></td>
</tr>
<tr class="even">
<td><p>E_INVALIDARG</p></td>
<td><p>一个或多个参数是无效的。</p></td>
</tr>
<tr class="odd">
<td><p>一个或多个参数是无效的。</p></td>
<td><p>指针无效。</p></td>
</tr>
<tr class="even">
<td><p>E_WPRC_FAILED_TO_START_PROFILE</p></td>
<td><p>磁带库未通过启动配置文件集合中的一个配置文件。 使用[IControlErrorInfo](icontrolerrorinfo.md)来获取详细的错误信息。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[IControlManager](icontrolmanager.md)

 

 







