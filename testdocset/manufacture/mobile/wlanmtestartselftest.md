---
author: kpacquer
Description: WlanMTEStartSelfTest
ms.assetid: 6c583601-3d26-4a4a-b225-11c2b54ea59b
MSHAttr: PreferredLib:/library/windows/hardware
title: WlanMTEStartSelfTest
ms.openlocfilehash: e63c684a7fb1f1379b775a3aae05a32ed9022207
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wlanmtestartselftest"></a>WlanMTEStartSelfTest


启动预配置的自我测试。

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>语法


``` syntax
DWORD WlanMTEStartSelfTest(
    __in                        HANDLE                              hAdapter,
    __in                        DOT11_MANUFACTURING_SELF_TEST_TYPE  eTestType,
    __in                        ULONG                               uTestID,
    __in                        PVOID                               pvContext,
    __in                        ULONG                               uPinBitMask,
    __in                        ULONG                               uInBufLen,
    __in_bcount_opt(uInBufLen)  PUCHAR                              pucInBuffer
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
\[在\]的上下文，用于唯一标识此请求回调和中后续的结果查询。

<span id="uPinBitMask"></span><span id="upinbitmask"></span><span id="UPINBITMASK"></span>*uPinBitMask*  
\[在\]适配器端口可供测试的位掩码。

<span id="uInBufLen"></span><span id="uinbuflen"></span><span id="UINBUFLEN"></span>*uInBufLen*  
\[在\]在自检的任何附加信息传递缓冲区的长度。

<span id="pucInBuffer"></span><span id="pucinbuffer"></span><span id="PUCINBUFFER"></span>*pucInBuffer*  
\[在\]将包含有关自我测试的其他信息的缓冲区。

## <a name="span-idremarksspanspan-idremarksspanspan-idremarksspanremarks"></a><span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>备注


自我测试完成后，应用程序的回调处理程序调用时，如果其中一个已注册， **dot11ManufacturingCallbackType**设置为与**dot11\_制造\_回调\_自我\_测试\_完成**，并且包括自我测试的结果。

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

 

 






