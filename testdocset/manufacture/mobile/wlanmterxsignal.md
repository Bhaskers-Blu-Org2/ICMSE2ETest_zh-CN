---
author: kpacquer
Description: WlanMTERxSignal
ms.assetid: eb475d1a-0692-44de-aada-1c8c85f2f500
MSHAttr: PreferredLib:/library/windows/hardware
title: WlanMTERxSignal
ms.openlocfilehash: cd03290bc97866e0583a90aed28446a92361fb18
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wlanmterxsignal"></a>WlanMTERxSignal


查询有关在特定频段和通道接收到的信号的信息。

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>语法


``` syntax
DWORD WlanMTERxSignal(
    __in    HANDLE      hAdapter,
    __out   BOOLEAN     *pbEnabled,
    __in    DOT11_BAND  Dot11Band,
    __in    ULONG       uChannel,
    __out   LONG        *pPowerLevel
);
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>参数


<span id="hAdapter"></span><span id="hadapter"></span><span id="HADAPTER"></span>*hAdapter*  
\[在\]的 Wi-Fi 适配器，窗口的句柄获得通过调用[WlanMTEOpenHandle](wlanmteopenhandle.md)。

<span id="pbEnabled"></span><span id="pbenabled"></span><span id="PBENABLED"></span>*pbEnabled*  
\[出\]**真**如果驱动程序检测到的信号在指定带区和通道。 **假**如果检测到任何信号。

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
\[在\]信号被检测到的通道。 频道范围 dependa 和受支持的 PHY 类型带区上。

<span id="pPowerLevel"></span><span id="ppowerlevel"></span><span id="PPOWERLEVEL"></span>*pPowerLevel*  
\[出\]接收到的信号的天线，以 dBm 度量的 RSSI 返回时检测到的电源级别。 这是*bEnabled*为**True**时才有效。

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
<td align="left"><p><em>PbEnabled</em>、 <em>Dot11Band</em>、 <em>uChannel</em>或<em>pPowerLevel</em>参数为 NULL 时返回。</p></td>
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

 

 






