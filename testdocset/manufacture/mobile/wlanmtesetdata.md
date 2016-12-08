---
author: kpacquer
Description: WlanMTESetData
ms.assetid: cf0cf3b4-a4e0-4818-bc78-8b5547903f4b
MSHAttr: PreferredLib:/library/windows/hardware
title: WlanMTESetData
ms.openlocfilehash: 72a96b3895b2d8a5db493252027970523950812f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wlanmtesetdata"></a>WlanMTESetData


该驱动程序将数据写入的请求的特定位置定义的键和偏移值。

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>语法


``` syntax
DWORD WlanMTESetData(
    __in                    HANDLE  hAdapter,
    __in                    ULONG   uKey,
    __in                    ULONG   uOffset,
    __in                    ULONG   uInBufLen,
    __in_bcount(uInBufLen)  PUCHAR  pucInBuffer
);
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>参数


<span id="hAdapter"></span><span id="hadapter"></span><span id="HADAPTER"></span>*hAdapter*  
\[在\]的 Wi-Fi 适配器，窗口的句柄获得通过调用[WlanMTEOpenHandle](wlanmteopenhandle.md)。

<span id="uKey"></span><span id="ukey"></span><span id="UKEY"></span>*uKey*  
\[在\]写请求的键。

<span id="uOffset"></span><span id="uoffset"></span><span id="UOFFSET"></span>*uOffset*  
\[在\]的写入请求的偏移量。

<span id="uInBufLen"></span><span id="uinbuflen"></span><span id="UINBUFLEN"></span>*uInBufLen*  
\[在\]包含要写入数据的缓冲区的长度。

<span id="pucInBuffer"></span><span id="pucinbuffer"></span><span id="PUCINBUFFER"></span>*pucInBuffer*  
\[在\]包含要写入数据的缓冲区。

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
<td align="left"><p><em>UInBufLen</em>参数存在，但<em>pucInBuffer</em>参数为 NULL 时返回。</p></td>
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

 

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>要求


**标头︰** wifimte.w

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Wi-Fi 制造 API](wi-fi-manufacturing-api.md)

 

 






