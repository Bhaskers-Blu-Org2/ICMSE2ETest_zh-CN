---
author: kpacquer
Description: "返回一个布尔值，该值指示是否使用电话扬声器，而不是电话听筒耳机。"
ms.assetid: 933f0816-a094-4f7b-a26f-5d31ed97f677
MSHAttr: PreferredLib:/library/windows/hardware
title: "MfgPhoneGetSpeaker 函数"
ms.openlocfilehash: 3615b10e84659966eeec7d28a75b840cc5b75419
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mfgphonegetspeaker-function"></a>MfgPhoneGetSpeaker 函数


返回一个布尔值，该值指示是否使用电话扬声器，而不是电话听筒耳机。

**MfgPhoneGetSpeaker**用于电话制造商，只能在制造模式下调用。

<a name="syntax"></a>语法
------

```ManagedCPlusPlus
HRESULT APIENTRY MfgPhoneGetSpeaker(
  _Out_ PBOOL pbSpeakerOn
);
```

<a name="parameters"></a>参数
----------

*pbSpeakerOn*\[出\]  
如果演讲者正在使用，否则为 FALSE，则返回 TRUE。

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

 

 





