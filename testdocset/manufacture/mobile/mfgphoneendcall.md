---
author: kpacquer
Description: "结束电话呼叫。"
ms.assetid: 2f6ce0fe-177b-4af5-8673-a9a4316309e4
MSHAttr: PreferredLib:/library/windows/hardware
title: "MfgPhoneEndCall 函数"
ms.openlocfilehash: 4cba6ae738c4ab8ba4dae75a4aa9cca2fefdb1c7
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mfgphoneendcall-function"></a>MfgPhoneEndCall 函数


结束电话呼叫。

**MfgPhoneEndCall**用于电话制造商，只能在制造模式下调用。

<a name="syntax"></a>语法
------

```ManagedCPlusPlus
HRESULT APIENTRY MfgPhoneEndCall(
  _In_ UINT SimSlot  
);
```

<a name="parameters"></a>参数
----------

*SimSlot*\[in\]  
应结束其调用基于 sim 卡的电话线路。

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

 

 





