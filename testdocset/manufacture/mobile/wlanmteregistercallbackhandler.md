---
author: kpacquer
Description: WlanMTERegisterCallbackHandler
ms.assetid: 7a61e9e2-fa0c-4c01-96c2-f3720aab7cde
MSHAttr: PreferredLib:/library/windows/hardware
title: WlanMTERegisterCallbackHandler
ms.openlocfilehash: 15612147b5d91be0d956338e64eb85f155f7a77a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wlanmteregistercallbackhandler"></a>WlanMTERegisterCallbackHandler


注册驱动程序调用回调来制造功能时将调用的处理事件。

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>语法


``` syntax
DWORD WlanMTERegisterCallbackHandler(
    __in    HANDLE                          hAdapter,
    __in    WLAN_MTE_NOTIFICATION_CALLBACK Callback
);
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>参数


<span id="hAdapter"></span><span id="hadapter"></span><span id="HADAPTER"></span>*hAdapter*  
\[在\]的 Wi-Fi 适配器，窗口的句柄获得通过调用[WlanMTEOpenHandle](wlanmteopenhandle.md)。

<span id="Callback"></span><span id="callback"></span><span id="CALLBACK"></span>*回叫*  
\[在\]被用于制造回调应用程序注册的处理程序函数。

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
<td align="left"><p>返回由<em>hAdapter</em>参数指定的适配器句柄是否无效或为空。</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idremarksspanspan-idremarksspanspan-idremarksspanremarks"></a><span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>备注


回调函数具有以下原型︰

``` syntax
typedef VOID (WINAPI *WLAN_MTE_NOTIFICATION_CALLBACK)(
    __in    PDOT11_MANUFACTURING_CALLBACK_PARAMETERS    pMTECallback,
    __in    PVOID                                       pvReserved
    );
```

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>要求


**标头︰** wifimte.w

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Wi-Fi 制造 API](wi-fi-manufacturing-api.md)

 

 






