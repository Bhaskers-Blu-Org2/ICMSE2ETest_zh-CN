---
author: kpacquer
Description: WlanMTESleep
ms.assetid: 36b6f1e4-15a3-4e2c-8afb-a455d945aede
MSHAttr: PreferredLib:/library/windows/hardware
title: WlanMTESleep
ms.openlocfilehash: b33dcf33def3154eb1d42ab7b3eb14fbe3f38850
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wlanmtesleep"></a>WlanMTESleep


驱动程序进入睡眠或者指定的时间间隔，或无限期直至清醒的请求将发送的请求。

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>语法


``` syntax
DWORD WlanMTESleep(
    __in                    HANDLE  hAdapter,
    __in                    ULONG   uSleepTime,
    __in                    PVOID   pvContext
);
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>参数


<span id="hAdapter"></span><span id="hadapter"></span><span id="HADAPTER"></span>*hAdapter*  
\[在\]的 Wi-Fi 适配器，窗口的句柄获得通过调用[WlanMTEOpenHandle](wlanmteopenhandle.md)。

<span id="uSleepTime"></span><span id="usleeptime"></span><span id="USLEEPTIME"></span>*uSleepTime*  
\[在\]的时间以毫秒为单位，使适配器可以一直处于休眠模式。 如果指定 − 1 的值，则适配器将休眠状态，直到发送一个[WlanMTEAwake](wlanmteawake.md)请求。

<span id="pvContext"></span><span id="pvcontext"></span><span id="PVCONTEXT"></span>*pvContext*  
\[在\]唯一地标识该回调中的此请求的上下文。

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
<td align="left"><p><em>USleepTime</em>参数为 NULL 时返回。</p></td>
</tr>
<tr class="even">
<td align="left"><p>ERROR_INVALID_HANDLE</p></td>
<td align="left"><p>返回如果<em>hAdapter</em>句柄无效。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>ERROR_OUTOFMEMORY</p></td>
<td align="left"><p>无法分配足够的内存来执行此操作时返回。</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idremarksspanspan-idremarksspanspan-idremarksspanremarks"></a><span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>备注


在睡眠模式下，关闭了所有的无线电收发器和 Wi-Fi 芯片处于关闭状态。 当适配器 reawakens 时， **dot11ManufacturingCallbackType**设置为被调用应用程序的回调处理程序，如果一个已注册的[WlanMTERegisterCallbackHandler](wlanmteregistercallbackhandler.md)， **dot11\_制造\_回调\_睡眠\_完成**并且包括睡眠操作的结果。

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>要求


**标头︰** wifimte.w

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[WlanMTEAwake](wlanmteawake.md)

[Wi-Fi 制造 API](wi-fi-manufacturing-api.md)

 

 






