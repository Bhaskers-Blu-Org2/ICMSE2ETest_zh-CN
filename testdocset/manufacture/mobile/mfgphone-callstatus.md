---
author: kpacquer
Description: "提供调用的状态信息。"
ms.assetid: dcd0fe41-15bf-4615-a9ed-aaf15dde5078
MSHAttr: PreferredLib:/library/windows/hardware
title: "MFGPHONE\\_CALLSTATUS 枚举"
ms.openlocfilehash: 5ab0a9652869e20249b774fa33d12419b60c8ce0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mfgphonecallstatus-enumeration"></a>MFGPHONE\_CALLSTATUS 枚举


提供调用的状态信息。

**MFGPHONE\_CALLSTATUS**为电话制造商，并且只能在制造模式下调用。

<a name="syntax"></a>语法
------

```ManagedCPlusPlus
typedef enum _MFGPHONE_CALLSTATUS { 
  MFGPHONE_CALLSTATUS_UNKNOWN   = 0,
  MFGPHONE_CALLSTATUS_IDLE      = 1,
  MFGPHONE_CALLSTATUS_CALLING   = 2,
  MFGPHONE_CALLSTATUS_INCOMING  = 3,
  MFGPHONE_CALLSTATUS_ACTIVE    = 4
} MFGPHONE_CALLSTATUS;
```

<a name="constants"></a>常量
---------

<span id="MFGPHONE_CALLSTATUS_UNKNOWN_"></span><span id="mfgphone_callstatus_unknown_"></span>**MFGPHONE\_CALLSTATUS\_未知**   
呼叫状态是未知的。

<span id="MFGPHONE_CALLSTATUS_IDLE"></span><span id="mfgphone_callstatus_idle"></span>**MFGPHONE\_CALLSTATUS\_空闲**  
呼叫状态为空闲。

<span id="MFGPHONE_CALLSTATUS_CALLING"></span><span id="mfgphone_callstatus_calling"></span>**MFGPHONE\_CALLSTATUS\_调用**  
正在调用的调用状态。

<span id="MFGPHONE_CALLSTATUS_INCOMING"></span><span id="mfgphone_callstatus_incoming"></span>**MFGPHONE\_CALLSTATUS\_传入**  
呼叫状态是传入的。

<span id="MFGPHONE_CALLSTATUS_ACTIVE"></span><span id="mfgphone_callstatus_active"></span>**MFGPHONE\_CALLSTATUS\_活动**  
呼叫状态处于活动状态。

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

 

 





