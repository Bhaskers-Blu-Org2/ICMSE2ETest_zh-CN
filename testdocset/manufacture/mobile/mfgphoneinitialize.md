---
author: kpacquer
Description: "初始化的电话系统和由 DLL 实现 API 的内部状态。"
ms.assetid: b9a9f95e-32ca-49fe-8f8c-9bf00d899edf
MSHAttr: PreferredLib:/library/windows/hardware
title: "MfgPhoneInitialize 函数"
ms.openlocfilehash: 4be255041cdd76bc4f37e3161dcc42c4f9c12a99
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mfgphoneinitialize-function"></a>MfgPhoneInitialize 函数


初始化的电话系统和由 DLL 实现 API 的内部状态。

**MfgPhoneInitialize**用于电话制造商，只能在制造模式下调用。

<a name="syntax"></a>语法
------

```ManagedCPlusPlus
HRESULT APIENTRY MfgPhoneInitialize(void);
```

<a name="parameters"></a>参数
----------

该函数没有任何参数。

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

 

 





