---
author: kpacquer
Description: WlanMTEQueryData
ms.assetid: 3def2451-5c4e-490b-ad6c-dbd703d7574a
MSHAttr: PreferredLib:/library/windows/hardware
title: WlanMTEQueryData
ms.openlocfilehash: 3ad5fdbbcbc4a296452aa6cde4ea6ca356cf5929
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wlanmtequerydata"></a>WlanMTEQueryData


查询定义的键和偏移值的特定位置中存储的数据的驱动程序。

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>语法


``` syntax
DWORD WlanMTEQueryData(
    __in                        HANDLE  hAdapter,
    __in                        ULONG   uKey,
    __in                        ULONG   uOffset,
    __out                       ULONG   *puBytesWrittenOut,
    __in                        ULONG   uOutBufLen,
    __out_bcount(uOutBufLen)    PUCHAR  pucOutBuffer
);
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>参数


<span id="hAdapter"></span><span id="hadapter"></span><span id="HADAPTER"></span>*hAdapter*  
\[在\]的 Wi-Fi 适配器，窗口的句柄获得通过调用[WlanMTEOpenHandle](wlanmteopenhandle.md)。

<span id="uKey"></span><span id="ukey"></span><span id="UKEY"></span>*uKey*  
\[在\]查询请求的键。

<span id="uOffset"></span><span id="uoffset"></span><span id="UOFFSET"></span>*uOffset*  
\[在\]查询请求的偏移量。

<span id="puBytesWrittenOut"></span><span id="pubyteswrittenout"></span><span id="PUBYTESWRITTENOUT"></span>*puBytesWrittenOut*  
\[出\]查询请求中返回的数据的字节数。

<span id="uOutBufLen"></span><span id="uoutbuflen"></span><span id="UOUTBUFLEN"></span>*uOutBufLen*  
\[在\]返回所请求的信息的缓冲区的长度。

<span id="pucOutBuffer"></span><span id="pucoutbuffer"></span><span id="PUCOUTBUFFER"></span>*pucOutBuffer*  
\[出\]将包含的数据的缓冲区返回的每个查询请求。

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
<td align="left"><p><em>PuBytesWrittenOut</em>、 <em>uOutBufLen</em>或<em>pucOutBuffer</em>参数为 NULL 时返回。</p></td>
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

 

 






