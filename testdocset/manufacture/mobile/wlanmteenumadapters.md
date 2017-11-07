---
author: kpacquer
Description: WlanMTEEnumAdapters
ms.assetid: f89ddb61-0c2d-446b-9f81-3e2c88311d61
MSHAttr: PreferredLib:/library/windows/hardware
title: WlanMTEEnumAdapters
ms.openlocfilehash: 8c53e26ad60329b087063315073b779c7c83354e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wlanmteenumadapters"></a>WlanMTEEnumAdapters


返回识别的 Wi-Fi 堆栈的适配器的列表。

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>语法


``` syntax
DWORD WlanMTEEnumAdapters(
    __out_opt   WLAN_MTE_ADAPTER_LIST  **ppWlanAdapterList
);
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>参数


<span id="ppWlanAdapterList"></span><span id="ppwlanadapterlist"></span><span id="PPWLANADAPTERLIST"></span>*ppWlanAdapterList*  
\[出\]的检测到的 Wi-Fi 适配器列表。

## <a name="span-idreturnvaluespanspan-idreturnvaluespanspan-idreturnvaluespanreturn-value"></a><span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>返回值


如果此函数成功，返回值就是错误\_成功。 否则，该函数返回的系统错误代码。

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>要求


**标头︰** wifimte.w

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Wi-Fi 制造 API](wi-fi-manufacturing-api.md)

 

 






