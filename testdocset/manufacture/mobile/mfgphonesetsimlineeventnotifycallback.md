---
author: kpacquer
Description: "基于回调的通知机制，用于接收基于 sim 卡的电话线路上的事件。"
ms.assetid: 58ca5582-71d0-4b33-a3b3-68374c6ed1d5
MSHAttr: PreferredLib:/library/windows/hardware
title: "MfgPhoneSetSimLineEventNotifyCallback 函数"
ms.openlocfilehash: 1066aef2dcb3330f405c5fb5d1940c728ba40238
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mfgphonesetsimlineeventnotifycallback-function"></a>MfgPhoneSetSimLineEventNotifyCallback 函数


基于回调的通知机制，用于接收基于 sim 卡的电话线路上的事件。

**MfgPhoneSetSimLineEventNotifyCallback**用于电话制造商，只能在制造模式下调用。

<a name="syntax"></a>语法
------

```ManagedCPlusPlus
HRESULT APIENTRY MfgPhoneSetSimLineEventNotifyCallback(
  _In_ MFGPHONE_SIMLINEEVENT_NOTIFY_CALLBACK  Callback,
  _In_ PVOID                                  Context
);
```

<a name="parameters"></a>参数
----------

*回叫*\[in\]  
该事件发生时调用的回调函数。

*上下文*\[in\]  
上下文。

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

 

 





