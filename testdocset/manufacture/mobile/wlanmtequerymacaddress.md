---
author: kpacquer
Description: WlanMTEQueryMacAddress
ms.assetid: 62953a75-4956-494f-983f-ca6475db2b43
MSHAttr: PreferredLib:/library/windows/hardware
title: WlanMTEQueryMacAddress
ms.openlocfilehash: e70a15eba90575aef27a93faf653f245427b2c34
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wlanmtequerymacaddress"></a>WlanMTEQueryMacAddress


返回的 Wi-Fi 适配器的 MAC 地址。

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>语法


``` syntax
DWORD WlanMTEQueryMacAddress(
    __in    HANDLE              hAdapter,
    __out   DOT11_MAC_ADDRESS   *pDot11MacAddress
);
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>参数


<span id="hAdapter"></span><span id="hadapter"></span><span id="HADAPTER"></span>*hAdapter*  
\[在\]的 Wi-Fi 适配器，窗口的句柄获得通过调用[WlanMTEOpenHandle](wlanmteopenhandle.md)。

<span id="pDot11MacAddress"></span><span id="pdot11macaddress"></span><span id="PDOT11MACADDRESS"></span>*pDot11MacAddress*  
\[出\]的 Wi-Fi 适配器的当前 MAC 地址。

## <a name="span-idreturnvaluespanspan-idreturnvaluespanspan-idreturnvaluespanreturn-value"></a><span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>返回值


如果此函数成功，返回值就是错误\_成功。

如果函数失败，则返回值是系统错误代码之一。 下表列出了可能会返回错误代码。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">错误代码</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>ERROR_INVALID_PARAMETER</p></td>
<td align="left"><p><em>PDot11MacAddress</em>参数为 NULL 时返回。</p></td>
</tr>
<tr class="even">
<td align="left"><p>ERROR_INVALID_HANDLE</p></td>
<td align="left"><p>返回如果<em>hAdapter</em>句柄无效。</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>要求


**标头︰** wifimte.w

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Wi-Fi 制造 API](wi-fi-manufacturing-api.md)

 

 






