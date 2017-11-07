---
author: kpacquer
Description: "设置一个值，该值指示是否使用电话扬声器，而不是电话听筒耳机。"
ms.assetid: ae0382d0-01fc-40eb-ae3d-72242ac4aede
MSHAttr: PreferredLib:/library/windows/hardware
title: "MfgPhoneSetSpeaker 函数"
ms.openlocfilehash: c666e28a361ee4fedadf51a5064663f1899a1251
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mfgphonesetspeaker-function"></a>MfgPhoneSetSpeaker 函数


设置一个值，该值指示是否使用电话扬声器，而不是电话听筒耳机。

**MfgPhoneSetSpeaker**用于电话制造商，只能在制造模式下调用。

<a name="syntax"></a>语法
------

```ManagedCPlusPlus
HRESULT APIENTRY MfgPhoneSetSpeaker(
  _In_ BOOL bSpeakerOn
);
```

<a name="parameters"></a>参数
----------

*bSpeakerOn*\[in\]  
如果演讲者应使用，否则为 false，则返回 TRUE。

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

 

 





