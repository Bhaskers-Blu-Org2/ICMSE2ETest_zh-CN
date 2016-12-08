---
author: kpacquer
Description: WlanMTEQuerySelfTestResult
ms.assetid: 7c728c46-7adb-4b1c-8b0e-85eb58ddd026
MSHAttr: PreferredLib:/library/windows/hardware
title: WlanMTEQuerySelfTestResult
ms.openlocfilehash: 8c87cebcb9e53e4b907b4ed27b096f434a5beeda
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wlanmtequeryselftestresult"></a>WlanMTEQuerySelfTestResult


查询以前请求的自我测试结果的驱动程序。

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>语法


``` syntax
DWORD WlanMTEQuerySelfTestResult(
    __in                            HANDLE                              hAdapter,
    __in                            DOT11_MANUFACTURING_SELF_TEST_TYPE  eTestType,
    __in                            ULONG                               uTestID,
    __in                            PVOID                               pvContext,
    __out                           BOOLEAN                             *pbResult,
    __out                           ULONG                               *puPinFailedBitMask,
    __out                           ULONG                               *puBytesWrittenOut,
    __in                            ULONG                               uOutBufLen,
    __out_bcount_opt(uOutBufLen)    PUCHAR                              pucOutBuffer
);
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>参数


<span id="hAdapter"></span><span id="hadapter"></span><span id="HADAPTER"></span>*hAdapter*  
\[在\]的 Wi-Fi 适配器，窗口的句柄获得通过调用[WlanMTEOpenHandle](wlanmteopenhandle.md)。

<span id="eTestType"></span><span id="etesttype"></span><span id="ETESTTYPE"></span>*eTestType*  
\[在\]类型的自我测试请求。 *ETestType*的值由 DOT11\_制造\_SELF\_测试\_类型枚举，如下所示︰

``` syntax
typedef enum DOT11_MANUFACTURING_SELF_TEST_TYPE {
        DOT11_MANUFACTURING_SELF_TEST_TYPE_INTERFACE = 1,
        DOT11_MANUFACTURING_SELF_TEST_TYPE_RF_INTERFACE,
        DOT11_MANUFACTURING_SELF_TEST_TYPE_BT_COEXISTENCE
    } DOT11_MANUFACTURING_SELF_TEST_TYPE, * PDOT11_MANUFACTURING_SELF_TEST_TYPE;
```

<span id="uTestID"></span><span id="utestid"></span><span id="UTESTID"></span>*uTestID*  
\[在\]的自测试请求的 ID。

<span id="pvContext"></span><span id="pvcontext"></span><span id="PVCONTEXT"></span>*pvContext*  
\[在\]原始自我测试请求中指定的上下文。

<span id="pbResult"></span><span id="pbresult"></span><span id="PBRESULT"></span>*pbResult*  
\[出\]自我测试的最终结果。 **如此**如果传递，**假**如果失败。

<span id="puPinFailedBitMask"></span><span id="pupinfailedbitmask"></span><span id="PUPINFAILEDBITMASK"></span>*puPinFailedBitMask*  
\[出\]适配器针脚，未通过测试的位掩码。

<span id="puBytesWrittenOut"></span><span id="pubyteswrittenout"></span><span id="PUBYTESWRITTENOUT"></span>*puBytesWrittenOut*  
\[出\]的可选数据的字节数返回从自我测试结果。

<span id="uOutBufLen"></span><span id="uoutbuflen"></span><span id="UOUTBUFLEN"></span>*uOutBufLen*  
\[在\]返回自我测试的任何其他信息的缓冲区的长度。

<span id="pucOutBuffer"></span><span id="pucoutbuffer"></span><span id="PUCOUTBUFFER"></span>*pucOutBuffer*  
\[出\]的缓冲区的长度*\*puBytesWrittenOut* ，提供了有关自行测试的其他信息。 值*\*puBytesWrittenOut*必须小于或等于*uOutBufLen*的值。

## <a name="span-idremarksspanspan-idremarksspanspan-idremarksspanremarks"></a><span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>备注


应用程序必须已经收到**dot11\_制造\_回调\_自\_测试\_完成**回调调用此命令。 它还应提供相同原始自我测试中使用的上下文值请求以便获取适当的自我测试请求的结果。

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
<td align="left"><p>返回如果<em>pbResult</em>、 <em>puPinFailedBitMask</em>或<em>puBytesWrittenOut</em>参数为 NULL，或者由<em>eTestType</em>参数指定的测试类型无效。</p></td>
</tr>
<tr class="even">
<td align="left"><p>ERROR_INVALID_HANDLE</p></td>
<td align="left"><p>返回如果<em>hAdapter</em>句柄无效。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>ERROR_OUTOFMEMORY</p></td>
<td align="left"><p>返回如果无法分配足够的内存来执行此操作。</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>要求


**标头︰** wifimte.w

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Wi-Fi 制造 API](wi-fi-manufacturing-api.md)

 

 






