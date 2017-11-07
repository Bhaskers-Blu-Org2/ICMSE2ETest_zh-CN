---
author: kpacquer
Description: "导致电话才能拨打电话。"
ms.assetid: f01afc0d-70cf-4d13-8d99-fb27bb329376
MSHAttr: PreferredLib:/library/windows/hardware
title: "MfgPhoneDial 函数"
ms.openlocfilehash: f825cc0422ef996088b0912389364118ff50aa62
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mfgphonedial-function"></a>MfgPhoneDial 函数


导致电话才能拨打电话。

**MfgPhoneDial**用于电话制造商，只能在制造模式下调用。

<a name="syntax"></a>语法
------

```ManagedCPlusPlus
HRESULT APIENTRY MfgPhoneDial(
  _In_ UINT    SimSlot,
  _In_ PCWSTR  DialNumber
);
```

<a name="parameters"></a>参数
----------

*SimSlot*\[in\]  
若要使用基于 sim 卡的电话线路。

*DialNumber*\[in\]  
要拨打的电话号码。

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

 

 





