---
author: kpacquer
Description: WlanMTEOpenHandle
ms.assetid: 82017f67-a089-4c99-af7e-f10735db60c3
MSHAttr: PreferredLib:/library/windows/hardware
title: WlanMTEOpenHandle
ms.openlocfilehash: cf3e03f52ee4cb0a30b3e40371a8d28c33ae2a04
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wlanmteopenhandle"></a>WlanMTEOpenHandle


打开基于该接口的 GUID 指定的驱动程序上的控柄并向调用方返回的句柄。

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>语法


``` syntax
DWORD WlanMTEOpenHandle(
    __in    GUID    *pAdapterGuid,
    __out   HANDLE  *phAdapter
);
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>参数


<span id="pAdapterGuid"></span><span id="padapterguid"></span><span id="PADAPTERGUID"></span>*pAdapterGuid*  
\[在\]识别该句柄是要打开 Wi-fi® 适配器的 GUID 的指针。

<span id="phAdapter"></span><span id="phadapter"></span><span id="PHADAPTER"></span>*phAdapter*  
\[出\]一个指针，指向 Wi-Fi 控点，如果成功地打开了。

## <a name="span-idreturnvaluespanspan-idreturnvaluespanspan-idreturnvaluespanreturn-value"></a><span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>返回值


如果此函数成功，返回值就是错误\_成功。

返回如果函数失败，系统错误代码之一。 下表列出了可能会返回错误代码。

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
<td align="left"><p>返回的<em>pAdapterGuid</em>或<em>phAdapter</em>参数是否为空。</p></td>
</tr>
<tr class="even">
<td align="left"><p>ERROR_INVALID_STATE</p></td>
<td align="left"><p>返回当前的 DOT11 操作模式如果不能检索。</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idremarksspanspan-idremarksspanspan-idremarksspanremarks"></a><span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>备注


Wi-fi 接口的列表的 Guid 可以通过调用[WlanMTEEnumAdapters](wlanmteenumadapters.md)来获得。

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>要求


**标头︰** wifimte.w

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Wi-Fi 制造 API](wi-fi-manufacturing-api.md)

 

 






