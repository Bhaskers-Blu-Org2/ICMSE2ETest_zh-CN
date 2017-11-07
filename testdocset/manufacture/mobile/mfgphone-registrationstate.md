---
author: kpacquer
Description: "提供有关电话线路的状态信息。通话吗？。"
ms.assetid: 0157eda2-5066-4f2e-95f8-1ae990db2540
MSHAttr: PreferredLib:/library/windows/hardware
title: "MFGPHONE\\_REGISTRATIONSTATE 枚举"
ms.openlocfilehash: b44f5a403a2b60d1861dd0d16b1f0c8ef1fa9030
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mfgphoneregistrationstate-enumeration"></a>MFGPHONE\_REGISTRATIONSTATE 枚举


提供有关电话线路的状态信息。如何称呼？

**MFGPHONE\_REGISTRATIONSTATE**为电话制造商，并且只能在制造模式下调用。

<a name="syntax"></a>语法
------

```ManagedCPlusPlus
typedef enum _MFGPHONE_REGISTRATIONSTATE { 
  MFGPHONE_REGISTRATIONSTATE_UNKNOWN           = 0,
  MFGPHONE_REGISTRATIONSTATE_NOSIGNAL          = 1,
      MFGPHONE_REGISTRATIONSTATE_UNREGISTERED  = 2,
  MFGPHONE_REGISTRATIONSTATE_REGISTERING       = 3,
  MFGPHONE_REGISTRATIONSTATE_REGISTERED        = 4,
  MFGPHONE_REGISTRATIONSTATE_DENIED            = 5
} MFGPHONE_REGISTRATIONSTATE;
```

<a name="constants"></a>常量
---------

<span id="MFGPHONE_REGISTRATIONSTATE_UNKNOWN"></span><span id="mfgphone_registrationstate_unknown"></span>**MFGPHONE\_REGISTRATIONSTATE\_未知**  
注册状态未知。

<span id="MFGPHONE_REGISTRATIONSTATE_NOSIGNAL"></span><span id="mfgphone_registrationstate_nosignal"></span>**MFGPHONE\_REGISTRATIONSTATE\_NOSIGNAL**  
没有信号检测的注册状态。

<span id="____MFGPHONE_REGISTRATIONSTATE_UNREGISTERED"></span><span id="____mfgphone_registrationstate_unregistered"></span>**MFGPHONE\_REGISTRATIONSTATE\_未注册**  
注册状态为未注册。

<span id="MFGPHONE_REGISTRATIONSTATE_REGISTERING"></span><span id="mfgphone_registrationstate_registering"></span>**MFGPHONE\_REGISTRATIONSTATE\_注册**  
正在注册的注册状态。

<span id="MFGPHONE_REGISTRATIONSTATE_REGISTERED"></span><span id="mfgphone_registrationstate_registered"></span>**MFGPHONE\_REGISTRATIONSTATE\_已注册**  
已注册的注册状态。

<span id="MFGPHONE_REGISTRATIONSTATE_DENIED"></span><span id="mfgphone_registrationstate_denied"></span>**MFGPHONE\_REGISTRATIONSTATE\_被拒绝**  
注册状态将被拒绝。

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

 

 





