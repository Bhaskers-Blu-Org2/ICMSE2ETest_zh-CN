---
author: kpacquer
Description: "取消初始化的电话系统和由 DLL 实现 API 的内部状态。"
ms.assetid: 7b82c8c8-6244-4f72-ab14-390a0757f120
MSHAttr: PreferredLib:/library/windows/hardware
title: "MfgPhoneUninitialize 函数"
ms.openlocfilehash: a2458c5607c225b301fa899cc65ff910f023dee4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mfgphoneuninitialize-function"></a>MfgPhoneUninitialize 函数


取消初始化的电话系统和由 DLL 实现 API 的内部状态。

**MfgPhoneUninitialize**用于电话制造商，只能在制造模式下调用。

<a name="syntax"></a>语法
------

```ManagedCPlusPlus
HRESULT APIENTRY MfgPhoneUninitialize(void);
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

 

 





