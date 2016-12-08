---
author: kpacquer
Description: "检索包含指定基于 sim 卡的电话线路的当前详细信息的结构。"
ms.assetid: 6ff31b2e-4a76-48cc-aefd-f015eb8cdf4a
MSHAttr: PreferredLib:/library/windows/hardware
title: "MfgPhoneGetSimLineDetail 函数"
ms.openlocfilehash: ffa72e5705333cedb68961a1ca9b82d3045147d8
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mfgphonegetsimlinedetail-function"></a>MfgPhoneGetSimLineDetail 函数


检索包含指定基于 sim 卡的电话线路的当前详细信息的结构。

**MfgPhoneGetSimLineDetail**用于电话制造商，只能在制造模式下调用。

<a name="syntax"></a>语法
------

```ManagedCPlusPlus
HRESULT APIENTRY MfgPhoneGetSimLineDetail(
  _In_  UINT                     SimSlot,
  _Out_ PMFGPHONE_SIMLINEDETAIL  SimLineDetail,
  _In_  ULONG                    SimLineDetailSize,
  _Out_ PULONG                   RequiredSize
);
```

<a name="parameters"></a>参数
----------

*SimSlot*\[in\]  
指定基于 sim 卡的电话线路。

*SimLineDetail*\[出\]  
指针，指向[**MFGPHONE\_SIMLINEDETAIL**](mfgphone-simlinedetail.md)结构，其中包含基于 sim 卡的电话线路由*SimSlot*指定的当前详细信息。

*SimLineDetailSize*\[in\]  
指定**SimLineDetail**参数的大小。

*RequiredSize*\[出\]  
指定**SimLineDetail**参数所需的大小。

<a name="return-value"></a>返回值
------------

S\_确定一旦成功则返回，否则返回的错误代码。

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>页眉</p></td>
<td align="left">Mfgphone.h （包括 Mfgphone.h）</td>
</tr>
<tr class="even">
<td align="left"><p>DLL</p></td>
<td align="left">MFGPHONE。DLL</td>
</tr>
</tbody>
</table>

 

 





