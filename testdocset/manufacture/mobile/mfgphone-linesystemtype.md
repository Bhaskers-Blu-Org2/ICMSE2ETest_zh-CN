---
author: kpacquer
Description: "提供有关行系统的类型信息。"
ms.assetid: 03dd827c-00f4-4288-b79d-7cfb3d4feab0
MSHAttr: PreferredLib:/library/windows/hardware
title: "MFGPHONE\\_LINESYSTEMTYPE 枚举"
ms.openlocfilehash: 1773d27ef49434b6dbecf9a29045a0ae413494ab
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mfgphonelinesystemtype-enumeration"></a>MFGPHONE\_LINESYSTEMTYPE 枚举


提供有关行系统的类型信息。

**MFGPHONE\_LINESYSTEMTYPE**为电话制造商，并且只能在制造模式下调用。

<a name="syntax"></a>语法
------

```ManagedCPlusPlus
typedef enum _MFGPHONE_LINESYSTEMTYPE { 
  MFGPHONE_LINESYSTEMTYPE_UNKNOWN   = 0,
  MFGPHONE_LINESYSTEMTYPE_GSM       = 1,
  MFGPHONE_LINESYSTEMTYPE_CDMA      = 2,
  MFGPHONE_LINESYSTEMTYPE_IMS       = 3
} MFGPHONE_LINESYSTEMTYPE;
```

<a name="constants"></a>常量
---------

<span id="MFGPHONE_LINESYSTEMTYPE_UNKNOWN_"></span><span id="mfgphone_linesystemtype_unknown_"></span>**MFGPHONE\_LINESYSTEMTYPE\_未知**   
线路系统类型是未知的。

<span id="MFGPHONE_LINESYSTEMTYPE_GSM"></span><span id="mfgphone_linesystemtype_gsm"></span>**MFGPHONE\_LINESYSTEMTYPE\_GSM**  
行的系统类型为 GSM。

<span id="MFGPHONE_LINESYSTEMTYPE_CDMA"></span><span id="mfgphone_linesystemtype_cdma"></span>**MFGPHONE\_LINESYSTEMTYPE\_CDMA**  
线路系统的类型是 CDMA。

<span id="MFGPHONE_LINESYSTEMTYPE_IMS"></span><span id="mfgphone_linesystemtype_ims"></span>**MFGPHONE\_LINESYSTEMTYPE\_IMS**  
线路系统的类型是 IMS。

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

 

 





