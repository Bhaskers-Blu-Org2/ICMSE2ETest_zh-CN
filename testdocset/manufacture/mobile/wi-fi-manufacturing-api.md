---
author: kpacquer
Description: "Wi-Fi 制造 API"
ms.assetid: 014c7111-cb2f-43a9-a0d0-4b097261493e
MSHAttr: PreferredLib:/library/windows/hardware
title: "Wi-Fi 制造 API"
ms.openlocfilehash: 1b4ba91982b7039067871f6245a5491cc58a603d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wi-fi-manufacturing-api"></a>Wi-Fi 制造 API


作为制造过程的一部分，您必须运行测试以确保组件集成、 运行正常，和校准正确，并且它们符合所有法规要求。

在本节中介绍的 API 成员是定义 Ihv 编写的 Wi-Fi 芯片组测试应用程序使用的接口。 此 API 集需要 Wi-fi 驱动程序符合 OID 规范的驱动程序。

只有必须在制造模式下使用此测试 API。 有关更多信息，请参阅[确定是否运行 MMO](determine-if-mmos-is-running.md)。

## <a name="span-idinthissectionspanspan-idinthissectionspanspan-idinthissectionspanin-this-section"></a><span id="In_this_section"></span><span id="in_this_section"></span><span id="IN_THIS_SECTION"></span>在这一节


为此 API 定义了以下接口。

<span id="WlanMTEEnumAdapters"></span><span id="wlanmteenumadapters"></span><span id="WLANMTEENUMADAPTERS"></span>[WlanMTEEnumAdapters](wlanmteenumadapters.md)  
返回列表中的适配器识别的 Wi-Fi 堆栈。

<span id="WlanMTEOpenHandle"></span><span id="wlanmteopenhandle"></span><span id="WLANMTEOPENHANDLE"></span>[WlanMTEOpenHandle](wlanmteopenhandle.md)  
打开驱动程序基于接口的 GUID 指定的句柄，并向调用方返回的句柄。

<span id="WlanMTECloseHandle"></span><span id="wlanmteclosehandle"></span><span id="WLANMTECLOSEHANDLE"></span>[WlanMTECloseHandle](wlanmteclosehandle.md)  
关闭先前打开的[WlanMTEOpenHandle](wlanmteopenhandle.md)驱动程序句柄。

<span id="WlanMTERegisterCallbackHandler"></span><span id="wlanmteregistercallbackhandler"></span><span id="WLANMTEREGISTERCALLBACKHANDLER"></span>[WlanMTERegisterCallbackHandler](wlanmteregistercallbackhandler.md)  
注册驱动程序调用回调来制造功能时将调用的处理事件。

<span id="WlanMTEDeRegisterCallbackHandler"></span><span id="wlanmtederegistercallbackhandler"></span><span id="WLANMTEDEREGISTERCALLBACKHANDLER"></span>[WlanMTEDeRegisterCallbackHandler](wlanmtederegistercallbackhandler.md)  
注销回调处理程序，以便它将不再是与制造业相关的功能事件发生时调用。

<span id="WlanMTEGetVendorInfo"></span><span id="wlanmtegetvendorinfo"></span><span id="WLANMTEGETVENDORINFO"></span>[WlanMTEGetVendorInfo](wlanmtegetvendorinfo.md)  
请求特定供应商的信息，如供应商 ID 和供应商说明。

<span id="WlanMTEResetAdapter"></span><span id="wlanmteresetadapter"></span><span id="WLANMTERESETADAPTER"></span>[WlanMTEResetAdapter](wlanmteresetadapter.md)  
重置的 Wi-Fi 适配器。

<span id="WlanMTEQueryMacAddress"></span><span id="wlanmtequerymacaddress"></span><span id="WLANMTEQUERYMACADDRESS"></span>[WlanMTEQueryMacAddress](wlanmtequerymacaddress.md)  
查询的 Wi-Fi 适配器的 MAC 地址。

<span id="WlanMTEQueryPhyTypes"></span><span id="wlanmtequeryphytypes"></span><span id="WLANMTEQUERYPHYTYPES"></span>[WlanMTEQueryPhyTypes](wlanmtequeryphytypes.md)  
查询列表中的适配器上配置的 802.11 PHY 类型。

<span id="WlanMTEStartSelfTest"></span><span id="wlanmtestartselftest"></span><span id="WLANMTESTARTSELFTEST"></span>[WlanMTEStartSelfTest](wlanmtestartselftest.md)  
启动预配置的自我测试。

<span id="WlanMTEQuerySelfTestResult"></span><span id="wlanmtequeryselftestresult"></span><span id="WLANMTEQUERYSELFTESTRESULT"></span>[WlanMTEQuerySelfTestResult](wlanmtequeryselftestresult.md)  
查询以前请求的自我测试结果的驱动程序。

<span id="WlanMTERxSignal"></span><span id="wlanmterxsignal"></span><span id="WLANMTERXSIGNAL"></span>[WlanMTERxSignal](wlanmterxsignal.md)  
查询有关在特定频段和通道接收到的信号的信息。

<span id="WlanMTETxSignal"></span><span id="wlanmtetxsignal"></span><span id="WLANMTETXSIGNAL"></span>[WlanMTETxSignal](wlanmtetxsignal.md)  
请求在指定带区和通道信号传输的驱动程序。

<span id="WlanMTEQueryADC"></span><span id="wlanmtequeryadc"></span><span id="WLANMTEQUERYADC"></span>[WlanMTEQueryADC](wlanmtequeryadc.md)  
请求时执行开放环上的传输信号的值。

<span id="WlanMTESetData"></span><span id="wlanmtesetdata"></span><span id="WLANMTESETDATA"></span>[WlanMTESetData](wlanmtesetdata.md)  
该驱动程序数据写入指定的位置和偏移量从该位置的请求。

<span id="WlanMTEQueryData"></span><span id="wlanmtequerydata"></span><span id="WLANMTEQUERYDATA"></span>[WlanMTEQueryData](wlanmtequerydata.md)  
查询在特定位置并从该位置的偏移量数据的驱动程序。

<span id="WlanMTESleep"></span><span id="wlanmtesleep"></span><span id="WLANMTESLEEP"></span>[WlanMTESleep](wlanmtesleep.md)  
驱动程序进入睡眠或者指定的时间间隔或无限期直至清醒的请求将发送的请求。

<span id="WlanMTEAwake"></span><span id="wlanmteawake"></span><span id="WLANMTEAWAKE"></span>[WlanMTEAwake](wlanmteawake.md)  
从其当前的睡眠状态唤醒的驱动程序的请求。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[添加 Wi-Fi 制造的 OID 接口的测试支持](adding-wi-fi-manufacturing-test-support-to-the-oid-interface.md)

 

 






