---
author: kpacquer
Description: "获取当前检测到的 sim 卡插槽的数量。"
ms.assetid: 432b3748-4444-41b8-ac0b-f227d0f36aef
MSHAttr: PreferredLib:/library/windows/hardware
title: "MfgPhoneGetSimLineCount 函数"
ms.openlocfilehash: dbfbdce8bc351b701972f43d5e06053a7a37a3e4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mfgphonegetsimlinecount-function"></a>MfgPhoneGetSimLineCount 函数


获取当前检测到的 sim 卡插槽的数量。

**MfgPhoneGetSimLineCount**用于电话制造商，只能在制造模式下调用。

<a name="syntax"></a>语法
------

```ManagedCPlusPlus
HRESULT APIENTRY MfgPhoneGetSimLineCount(
  _Out_ PUINT SimLineCount
);
```

<a name="parameters"></a>参数
----------

*SimLineCount*\[出\]  
指针，指向**UINT** ，指定当前检测到的 sim 卡插槽的数量。 活动和非活动的 sim 卡插槽包含在计数中。

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

 

 





