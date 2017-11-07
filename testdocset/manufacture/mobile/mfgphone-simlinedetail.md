---
author: kpacquer
Description: "提供有关特定基于 sim 卡的电话线路的信息。"
ms.assetid: 004fe04e-48dc-4569-882a-035ca6918498
MSHAttr: PreferredLib:/library/windows/hardware
title: "MFGPHONE\\_SIMLINEDETAIL 结构"
ms.openlocfilehash: 079af4ab6a9521fe2c83935e5b933c4dab7413d0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mfgphonesimlinedetail-structure"></a>MFGPHONE\_SIMLINEDETAIL 结构


提供有关特定基于 sim 卡的电话线路的信息。 通过[**MfgPhoneGetSimLineDetail**](mfgphonegetsimlinedetail.md)函数中检索此**结构**。

**MFGPHONE\_SIMLINEDETAIL**为 iis 电话制造商和只能在制造模式下调用。

<a name="syntax"></a>语法
------

```ManagedCPlusPlus
typedef struct _MFGPHONE_SIMLINEDETAIL {
  UINT                       SimSlot;
  MFGPHONE_SIMSTATE          SimState;
  MFGPHONE_REGISTRATIONSTATE RegistrationState;
  WCHAR  [64]                NetworkName;
  MFGPHONE_LINESYSTEMTYPE    LineSystemType;
  UINT                       SignalStrength;
  MFGPHONE_CALLSTATUS        CallStatus;
} MFGPHONE_SIMLINEDETAIL, *PMFGPHONE_SIMLINEDETAIL;
```

<a name="members"></a>成员
-------

**SimSlot**  
在此结构中的详细信息与有关基于 sim 卡的电话线路。

**SimState**  
**枚举**指定基于 sim 卡的电话线路的当前状态。

**RegistrationState**  
**枚举**指定电话线路的当前注册状态。

**NetworkName**  
WCHAR 包含网络的名称。

**LineSystemType**  
**枚举**指定电话线路的线路系统类型。

**SignalStrength**  
无符号的整数，包含的电话线路的信号强度。

**CallStatus**  
**枚举**指定电话线路的呼叫状态。

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
</tbody>
</table>

 

 





