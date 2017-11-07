---
author: kpacquer
Description: WlanMTEResetAdapter
ms.assetid: bb87f719-3277-4fcc-aa9f-94ff1dac34f1
MSHAttr: PreferredLib:/library/windows/hardware
title: WlanMTEResetAdapter
ms.openlocfilehash: 687f30b445895cdcb0f8e961dbbd6f44b7d64c41
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wlanmteresetadapter"></a>WlanMTEResetAdapter


重置的 Wi-Fi 适配器。 应用程序可以指定一个可选回调和上下文句柄操作完成时调用。

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>语法


``` syntax
DWORD WlanMTEResetAdapter(
    __in        HANDLE                  hAdapter,
    __in        DOT11_RESET_REQUEST     *pDot11ResetRequest,
    __in        WLAN_MTE_RESET_CALLBACK ResetCallback,
    __in        PVOID                   pvContext
);
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>参数


<span id="hAdapter"></span><span id="hadapter"></span><span id="HADAPTER"></span>*hAdapter*  
\[在\]的 Wi-Fi 适配器，窗口的句柄获得通过调用[WlanMTEOpenHandle](wlanmteopenhandle.md)。

<span id="pDot11ResetRequest"></span><span id="pdot11resetrequest"></span><span id="PDOT11RESETREQUEST"></span>*pDot11ResetRequest*  
\[在\]将重置请求有关的信息。 如果应用程序需要更新的 MAC 地址来重置，还应指定**dot11\_重置\_类型\_mac**或**dot11\_重置\_类型\_phy\_和\_mac**写入 DPP 的更新 MAC 地址的顺序。 请注意该设备已在制造模式下启动时只将有效 MAC 地址的更改。

<span id="ResetCallback"></span><span id="resetcallback"></span><span id="RESETCALLBACK"></span>*ResetCallback*  
\[在中，可选\]上要调用的回调处理程序重置完成。

<span id="pvContext"></span><span id="pvcontext"></span><span id="PVCONTEXT"></span>*pvContext*  
\[在中，可选\]调用该处理程序时如果指定回调，则提供此上下文值。

## <a name="span-idremarksspanspan-idremarksspanspan-idremarksspanremarks"></a><span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>备注


Wi-Fi 重置适配器通知回调函数具有以下原型︰

``` syntax
typedef VOID (WINAPI *WLAN_MTE_RESET_CALLBACK)(
    __in    DWORD   dwError,
    __in    PVOID   pvContext
    );
```

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
<td align="left"><p><em>PDot11ResetRequest</em>参数为 NULL 或<em>pDot11ResetRequest</em>类型无效时返回。</p></td>
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

 

 






