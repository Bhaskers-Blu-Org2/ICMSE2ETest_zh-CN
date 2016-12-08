---
author: kpacquer
Description: WlanMTETxSignal
ms.assetid: 02a91cb8-de7b-4b96-aa41-7dab33a8d02e
MSHAttr: PreferredLib:/library/windows/hardware
title: WlanMTETxSignal
ms.openlocfilehash: 5ed45add3a07f1c78f6a8e75e4aacc498b46cf39
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wlanmtetxsignal"></a>WlanMTETxSignal


请求在指定带区和通道信号传输的驱动程序。

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>语法


``` syntax
DWORD WlanMTETxSignal(
    __in    HANDLE      hAdapter,
    __in    BOOLEAN     bEnable,
    __in    BOOLEAN     bOpenLoop,
    __in    DOT11_BAND  Dot11Band,
    __in    ULONG       uChannel,
    __in    LONG        SetPowerLevel,
    __out   LONG        *pADCPowerLevel
);
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>参数


<span id="hAdapter"></span><span id="hadapter"></span><span id="HADAPTER"></span>*hAdapter*  
\[在\]的 Wi-Fi 适配器，窗口的句柄获得通过调用[WlanMTEOpenHandle](wlanmteopenhandle.md)。

<span id="bEnable"></span><span id="benable"></span><span id="BENABLE"></span>*bEnable*  
\[在\]设置的值时，如果启用了传输。 否则，将禁用在指定带区和信道的传输。

<span id="bOpenLoop"></span><span id="bopenloop"></span><span id="BOPENLOOP"></span>*bOpenLoop*  
\[在\]设置为**True**时，驱动程序必须使用开环功率控制，并在*pADCPowerLevel*参数中返回的信号值。 如果此参数设置和硬件不支持开环功率控制，**错误\_不\_支持**将返回异常。

<span id="Dot11Band"></span><span id="dot11band"></span><span id="DOT11BAND"></span>*Dot11Band*  
\[在\]信号被检测到的带区。 *Dot11Band*参数的值由 DOT11\_带枚举，如下所示︰

``` syntax
typedef enum DOT11_BAND {
        dot11_band_2p4g = 1,
        dot11_band_4p9g,
        dot11_band_5g
    } DOT11_BAND, * PDOT11_BAND;
```

<span id="uChannel"></span><span id="uchannel"></span><span id="UCHANNEL"></span>*uChannel*  
\[在\]信号被传输的通道。 频道范围取决于带区和支持的 PHY 类型。

<span id="SetPowerLevel"></span><span id="setpowerlevel"></span><span id="SETPOWERLEVEL"></span>*SetPowerLevel*  
\[在\]的传输信号，以 dBm 的电源级别。

<span id="pADCPowerLevel"></span><span id="padcpowerlevel"></span><span id="PADCPOWERLEVEL"></span>*pADCPowerLevel*  
\[下班，可选\]天线，在检测当前的信号强度作为原始值返回。 由 IHV 实现此值的解释。 如果*bOpenLoop*为**True** ，并且硬件支持，此返回的参数才有效。

## <a name="span-idreturnvaluespanspan-idreturnvaluespanspan-idreturnvaluespanreturn-value"></a><span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>返回值


如果此函数成功，返回值就是错误\_成功。

如果函数失败，则返回值是系统错误代码之一。 下表列出了可能会返回错误代码之一。

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
<td align="left"><p>当使用<em>Dot11Band</em>或<em>uChannel</em>参数为 NULL，或者如果存在<em>bOpenLoop</em> ，但<em>pADCPowerLevel</em>是 NULL 返回。</p></td>
</tr>
<tr class="even">
<td align="left"><p>ERROR_INVALID_HANDLE</p></td>
<td align="left"><p>返回由<em>hAdapter</em>参数指定的适配器句柄是否无效。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>ERROR_OUTOFMEMORY</p></td>
<td align="left"><p>无法分配足够的内存来执行此操作时返回。</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>要求


**标头︰** wifimte.w

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Wi-Fi 制造 API](wi-fi-manufacturing-api.md)

 

 






