---
author: kpacquer
Description: "提供 sim 卡的状态信息。"
ms.assetid: 8533be42-70de-433c-89ac-2c623d9b4397
MSHAttr: PreferredLib:/library/windows/hardware
title: "MFGPHONE\\_SIMSTATE 枚举"
ms.openlocfilehash: 768de8a27a6d6ec9abad48c088136afa6eea917d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mfgphonesimstate-enumeration"></a>MFGPHONE\_SIMSTATE 枚举


提供 sim 卡的状态信息。

**MFGPHONE\_SIMSTATE**为电话制造商，并且只能在制造模式下调用。

<a name="syntax"></a>语法
------

```ManagedCPlusPlus
typedef enum _MFGPHONE_SIMSTATE { 
  MFGPHONE_SIMSTATE_UNKNOWN   = 0,
  MFGPHONE_SIMSTATE_NONE      = 1,
  MFGPHONE_SIMSTATE_ACTIVE    = 2,
  MFGPHONE_SIMSTATE_INVALID   = 3,
  MFGPHONE_SIMSTATE_LOCKED    = 4,
  MFGPHONE_SIMSTATE_DISABLED  = 5
} MFGPHONE_SIMSTATE;
```

<a name="constants"></a>常量
---------

<span id="MFGPHONE_SIMSTATE_UNKNOWN"></span><span id="mfgphone_simstate_unknown"></span>**MFGPHONE\_SIMSTATE\_未知**  
Sim 卡状态是未知的。

<span id="MFGPHONE_SIMSTATE_NONE"></span><span id="mfgphone_simstate_none"></span>**MFGPHONE\_SIMSTATE\_无**  
Sim 卡状态为无。 没有任何的 sim 卡。

<span id="MFGPHONE_SIMSTATE_ACTIVE"></span><span id="mfgphone_simstate_active"></span>**MFGPHONE\_SIMSTATE\_活动**  
Sim 卡状态处于活动状态。

<span id="MFGPHONE_SIMSTATE_INVALID"></span><span id="mfgphone_simstate_invalid"></span>**MFGPHONE\_SIMSTATE\_无效**  
Sim 卡状态无效。

<span id="MFGPHONE_SIMSTATE_LOCKED"></span><span id="mfgphone_simstate_locked"></span>**MFGPHONE\_SIMSTATE\_锁定**  
已锁定 sim 卡状态。

<span id="MFGPHONE_SIMSTATE_DISABLED"></span><span id="mfgphone_simstate_disabled"></span>**MFGPHONE\_SIMSTATE\_被禁用**  
Sim 卡状态为禁用。

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

 

 





