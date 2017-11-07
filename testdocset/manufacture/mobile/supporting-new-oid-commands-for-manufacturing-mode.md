---
author: kpacquer
Description: "支持新的 OID 命令制造模式"
ms.assetid: 0ebb9581-043e-47f8-84c9-6fa97c0900cc
MSHAttr: PreferredLib:/library/windows/hardware
title: "支持新的 OID 命令制造模式"
ms.openlocfilehash: 6b54c5ec5aacae5a18a9ec480d1f6a5e9d665c83
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="supporting-new-oid-commands-for-manufacturing-mode"></a>支持新的 OID 命令制造模式


在制造模式下运行时，Wi-Fi 微型端口驱动程序必须添加对以下新的 OID 命令的支持。 驱动程序应确保该设备目前在制造模式下调用这些命令。 有关更多信息，请参阅[确定是否运行 MMO](determine-if-mmos-is-running.md)。 一些 API 中指定的参数可能 IHV 特有。

## <a name="span-idoiddot11manufacturingtestspanspan-idoiddot11manufacturingtestspanoiddot11manufacturingtest"></a><span id="OID_DOT11_MANUFACTURING_TEST"></span><span id="oid_dot11_manufacturing_test"></span>OID\_DOT11\_制造\_测试


OID\_DOT11\_制造\_测试称为执行特定测试驱动程序中的方法请求。 该 OID 决不会在正常操作期间使用。

``` syntax
typedef struct _DOT11_MANUFACTURING_TEST {
    DOT11_MANUFACTURING_TEST_TYPE dot11ManufacturingTestType;
    ULONG uBufferLength;
    UCHAR ucBuffer[1];
} DOT11_MANUFACTURING_TEST, * PDOT11_MANUFACTURING_TEST;
```

<span id="dot11ManufacturingTestType"></span><span id="dot11manufacturingtesttype"></span><span id="DOT11MANUFACTURINGTESTTYPE"></span>*dot11ManufacturingTestType*  
\[在\]指定制造测试运行。 此成员数据类型是其中一个的值**DOT11\_制造\_测试\_类型**枚举。

DOT11 制造测试类型枚举定义如下︰

``` syntax
typedef enum _DOT11_MANUFACTURING_TEST_TYPE {
    dot11_manufacturing_test_unknown = 0,
    dot11_manufacturing_test_self_start = 1,
    dot11_manufacturing_test_self_query_result = 2,
    dot11_manufacturing_test_rx = 3,
    dot11_manufacturing_test_tx = 4,
    dot11_manufacturing_test_set_data = 5,
    dot11_manufacturing_test_query_data = 6,
    dot11_manufacturing_test_sleep = 7,
    dot11_manufacturing_test_awake = 8,
    dot11_manufacturing_test_IHV_start = 0x80000000,
    dot11_manufacturing_test_IHV_end = 0xffffffff
} DOT11_MANUFACTURING_TEST_TYPE, * PDOT11_MANUFACTURING_TEST_TYPE;
```

<span id="uBufferLength"></span><span id="ubufferlength"></span><span id="UBUFFERLENGTH"></span>*uBufferLength*  
\[在\]的长度，以字节为单位的**DOT11\_制造\_测试**结构和特定于测试附加在结尾的任何其他数据。

<span id="ucBuffer"></span><span id="ucbuffer"></span><span id="UCBUFFER"></span>*ucBuffer*  
\[在\]包含所指定的**dot11DiagnosticsTestType**成员的可选数据的缓冲区。

## <a name="span-iddot11manufacturingtestselfstartspanspan-iddot11manufacturingtestselfstartspandot11manufacturingtestselfstart"></a><span id="dot11_manufacturing_test_self_start"></span><span id="DOT11_MANUFACTURING_TEST_SELF_START"></span>dot11\_制造\_测试\_self\_开始


**Dot11\_制造\_测试\_self\_启动**命令调用以请求测试 IC WLAN 连接、 FEM IC 连接或 WLAN BT 共存接口的驱动程序。

**DOT11\_诊断\_SELF\_测试\_BT\_共存**才适用 WLAN 和 Bluetooth 芯片位于单独的 ICs。 如果它们位于同一个模块，此测试不支持和微型端口应返回**NDIS\_状态\_不\_支持**。

在调用时，驱动程序应该运行请求的测试**DOT11\_制造\_自我\_测试\_设置\_PARAMS**结构并返回成功时测试已经启动。 完成后，是否测试已成功或失败，则驱动程序应指示测试状态通过**NDIS\_状态\_DOT11\_制造\_回调**回调处理程序，通过将设置为*dot11ManufacturingCallbackType* **dot11\_制造\_回调\_自\_测试\_完成**和状态描述测试的结果。 驱动程序将调用**OID\_DOT11\_制造\_测试**使用 oid **dot11\_制造\_测试\_self\_查询\_结果**命令查询测试的详细的结果。

``` syntax
typedef struct _DOT11_MANUFACTURING_SELF_TEST_SET_PARAMS {
    DOT11_MANUFACTURING_SELF_TEST_TYPE SelfTestType;
    ULONG uTestID;
    ULONG uPinBitMask;
    PVOID pvContext;
    ULONG uBufferLength;
    UCHAR ucBufferIn[1];
} DOT11_MANUFACTURING_SELF_TEST_SET_PARAMS, *PDOT11_MANUFACTURING_SELF_TEST_SET_PARAMS;
```

<span id="SelfTestType"></span><span id="selftesttype"></span><span id="SELFTESTTYPE"></span>*SelfTestType*  
\[在\]指定的自我测试运行驱动程序的类型。 数据类型为此成员**DOT11\_制造\_SELF\_测试\_类型**枚举具有下列值之一︰

<span id="DOT11_MANUFACTURING_SELF_TEST_INTERFACE"></span><span id="dot11_manufacturing_self_test_interface"></span>**DOT11\_制造\_SELF\_测试\_接口**  
-   Wlan 的控制和数据接口

-   时钟的请求

-   休眠时钟

-   中断和电源的电源线

-   所有相关的连接

<span id="DOT11_MANUFACTURING_SELF_TEST_RF_INTERFACE"></span><span id="dot11_manufacturing_self_test_rf_interface"></span>**DOT11\_制造\_SELF\_测试\_射频\_接口**  
-   FEM IC 控制和射频接口

-   FEM 电源

-   从得克萨斯州接口到 RX 接口的环回路径上的信号传输并验证。

<span id="DOT11_MANUFACTURING_SELF_TEST_BT_COEXISTENCE"></span><span id="dot11_manufacturing_self_test_bt_coexistence"></span>**DOT11\_制造\_SELF\_测试\_BT\_共存**  
-   从 Bluetooth 侧设置行状态和读来自 WLAN 端的行状态

-   验证每个插针的状态

<span id="uTestID"></span><span id="utestid"></span><span id="UTESTID"></span>*uTestID*  
\[在\]的测试运行 ID。

<span id="uPinBitMask"></span><span id="upinbitmask"></span><span id="UPINBITMASK"></span>*uPinBitMask*  
\[在\]的端口可供测试的位掩码。

<span id="pvContext"></span><span id="pvcontext"></span><span id="PVCONTEXT"></span>*pvContext*  
\[在\]的上下文值返回给应用程序使用**dot11\_制造\_回调\_自\_测试\_完成回调**驱动程序完成测试。

<span id="uBufferLength"></span><span id="ubufferlength"></span><span id="UBUFFERLENGTH"></span>*uBufferLength*  
\[在中，可选\]包含更多的自我测试输入缓冲区的长度。

<span id="ucBufferIn"></span><span id="ucbufferin"></span><span id="UCBUFFERIN"></span>*ucBufferIn*  
\[在中，可选\]包含其它设置自检程序的缓冲区。

## <a name="span-iddot11manufacturingtestselfqueryresultspanspan-iddot11manufacturingtestselfqueryresultspandot11manufacturingtestselfqueryresult"></a><span id="dot11_manufacturing_test_self_query_result"></span><span id="DOT11_MANUFACTURING_TEST_SELF_QUERY_RESULT"></span>dot11\_制造\_测试\_self\_查询\_结果


此命令获得了自我测试以前请求的结果。 它应该时才调用该驱动程序已经指出，自我测试已完成使用**NDIS\_状态\_DOT11\_制造\_回调**与*dot11ManufacturingCallbackType*设置为**dot11\_制造\_回调\_自\_测试\_完成**和状态描述测试的结果。

``` syntax
typedef struct _DOT11_MANUFACTURING_SELF_TEST_QUERY_RESULTS {
    DOT11_MANUFACTURING_SELF_TEST_TYPE SelfTestType;
    ULONG uTestID;
    BOOLEAN bResult;                    // PASS/FAIL
    ULONG uPinFailedBitMask;            // Detected PIN faults
    PVOID pvContext;
    ULONG uBytesWrittenOut;
    UCHAR ucBufferOut[1];               // Additional output from self-test (optional)
} DOT11_MANUFACTURING_SELF_TEST_QUERY_RESULTS, *PDOT11_MANUFACTURING_SELF_TEST_QUERY_RESULTS;
```

<span id="SelfTestType"></span><span id="selftesttype"></span><span id="SELFTESTTYPE"></span>*SelfTestType*  
\[在\]指定的自我测试被查询的结果的类型。 数据类型为此成员**DOT11\_制造\_SELF\_测试\_类型**枚举。

<span id="uTestID"></span><span id="utestid"></span><span id="UTESTID"></span>*uTestID*  
\[在\]的测试运行 ID。

<span id="bResult"></span><span id="bresult"></span><span id="BRESULT"></span>*bResult*  
\[出\]的测试结果。 **如此**如果通过测试，**假**如果失败。

<span id="uPinFailedBitMask"></span><span id="upinfailedbitmask"></span><span id="UPINFAILEDBITMASK"></span>*uPinFailedBitMask*  
\[出\]位掩码的任何检测到的错误的 PIN。

<span id="pvContext"></span><span id="pvcontext"></span><span id="PVCONTEXT"></span>*pvContext*  
\[在\]驱动程序指示测试是完成时使用的上下文。

<span id="uBytesWrittenOut"></span><span id="ubyteswrittenout"></span><span id="UBYTESWRITTENOUT"></span>*uBytesWrittenOut*  
\[出\]包含自我测试任何其他返回的输出缓冲区的长度。

<span id="ucBufferOut"></span><span id="ucbufferout"></span><span id="UCBUFFEROUT"></span>*ucBufferOut*  
\[传入、 传出，可选\] *uBytesWrittenOut*的长度，包含从自我测试的其他输出缓冲区。

## <a name="span-iddot11manufacturingtestrxspanspan-iddot11manufacturingtestrxspandot11manufacturingtestrx"></a><span id="dot11_manufacturing_test_rx"></span><span id="DOT11_MANUFACTURING_TEST_RX"></span>dot11\_制造\_测试\_rx


**Dot11\_制造\_测试\_rx**只读命令测试并验证没有 WLAN IC 与天线端口之间的连接。

若要测试此连接，信号发生器具有特定频率和电源，将测量和设备进行测试 (DUT) 返回生成非调制载波 (CW)。 如果带区和/或通道设置不一致，则驱动程序返回**状态\_无效\_参数**。

``` syntax
typedef struct _DOT11_MANUFACTURING_FUNCTIONAL_TEST_RX {
    BOOLEAN bEnabled;
    DOT11_BAND Dot11Band;
    ULONG uChannel;
    LONG  PowerLevel;
} DOT11_MANUFACTURING_FUNCTIONAL_TEST_RX, * PDOT11_MANUFACTURING_FUNCTIONAL_TEST_RX;
```

<span id="bEnabled"></span><span id="benabled"></span><span id="BENABLED"></span>*bEnabled*  
\[出\]**真**如果驱动程序检测到的信号在指定带区和通道。 **假**如果检测到任何信号。

<span id="Dot11Band"></span><span id="dot11band"></span><span id="DOT11BAND"></span>*Dot11Band*  
\[在\]信号被检测到的带区。

<span id="uChannel"></span><span id="uchannel"></span><span id="UCHANNEL"></span>*uChannel*  
\[在\]信号被检测到的通道。 频道范围取决于带区，支持 PHYs。

<span id="PowerLevel"></span><span id="powerlevel"></span><span id="POWERLEVEL"></span>*PowerLevel*  
\[出\]接收到的信号的天线，以 dBm 度量的 RSSI 返回时检测到的电源级别。 这是*bEnabled*为**True**时才有效。

## <a name="span-iddot11manufacturingtesttxspanspan-iddot11manufacturingtesttxspandot11manufacturingtesttx"></a><span id="dot11_manufacturing_test_tx"></span><span id="DOT11_MANUFACTURING_TEST_TX"></span>dot11\_制造\_测试\_tx


**Dot11\_制造\_测试\_tx**仅设置命令将验证与 FEM 输出芯片组之间的连接。

若要执行此测试，信号分析器物理连接到天线端口和 DUT 传输特定波段、 通道和电源级别设置与 CW 请求。 驱动程序还测量自己 ADC 读取传输信号，并将其返回给应用程序。

``` syntax
typedef struct _DOT11_MANUFACTURING_FUNCTIONAL_TEST_TX {
    BOOLEAN bEnable;
    BOOLEAN bOpenLoop;
    DOT11_BAND Dot11Band;
    ULONG uChannel;
    ULONG uSetPowerLevel;
    LONG  ADCPowerLevel;
} DOT11_MANUFACTURING_FUNCTIONAL_TEST_TX, * PDOT11_MANUFACTURING_FUNCTIONAL_TEST_TX;
```

<span id="bEnable"></span><span id="benable"></span><span id="BENABLE"></span>*bEnable*  
\[在\]如果设置时，此命令使传输。 如果不集中，在指定带区和信道传输都将被禁用。

<span id="bOpenLoop"></span><span id="bopenloop"></span><span id="BOPENLOOP"></span>*bOpenLoop*  
\[在\]如果设置为**true**时，此参数指示驱动程序被请求使用开环功率控制，并在*ADCPowerLevel*返回读取的信号值。 如果设置为**false**，则驱动程序将不使用开环功率控制。

如果设置了此值，并且硬件不支持开环功率控制，驱动程序将返回**NDIS\_状态\_不\_支持**。

<span id="Dot11Band"></span><span id="dot11band"></span><span id="DOT11BAND"></span>*Dot11Band*  
\[在\]信号被传输带。

<span id="uChannel"></span><span id="uchannel"></span><span id="UCHANNEL"></span>*uChannel*  
\[在\]信号被传输的通道。 频道范围取决于带区，支持 PHYs。

<span id="uSetPowerLevel"></span><span id="usetpowerlevel"></span><span id="USETPOWERLEVEL"></span>*uSetPowerLevel*  
\[在\]的传输信号的电源级别。 这将返回的最大可能的电源级别的百分比。

<span id="ADCPowerLevel"></span><span id="adcpowerlevel"></span><span id="ADCPOWERLEVEL"></span>*ADCPowerLevel*  
\[下班，可选\]天线，在检测当前的信号强度作为原始值返回。 由 IHV 指定此值的解释。

该选项必须设置如果*bOpenLoop*为**True** ，并且硬件支持。

## <a name="span-iddot11manufacturingtestsetdataspanspan-iddot11manufacturingtestsetdataspandot11manufacturingtestsetdata"></a><span id="dot11_manufacturing_test_set_data"></span><span id="DOT11_MANUFACTURING_TEST_SET_DATA"></span>dot11\_制造\_测试\_设置\_数据


**Dot11\_制造\_测试\_设置\_数据**仅设置命令允许应用程序写入数据中的特定位置。

``` syntax
typedef struct _DOT11_MANUFACTURING_TEST_SET_DATA {
    ULONG uKey;
    ULONG uOffset;
    ULONG uBufferLength;
    UCHAR ucBufferIn[1];
} DOT11_MANUFACTURING_TEST_SET_DATA, * PDOT11_MANUFACTURING_TEST_SET_DATA;
```

<span id="uKey"></span><span id="ukey"></span><span id="UKEY"></span>*uKey*  
\[在\]的键是特定 IHV 和可以是对特定收银机的引用或命名表中的条目。

<span id="uOffset"></span><span id="uoffset"></span><span id="UOFFSET"></span>*uOffset*  
\[在\]内数据的偏移量。

<span id="uBufferLength"></span><span id="ubufferlength"></span><span id="UBUFFERLENGTH"></span>*uBufferLength*  
\[在\]中包含其他测试数据缓冲区中的数据字节数。

<span id="ucBufferIn"></span><span id="ucbufferin"></span><span id="UCBUFFERIN"></span>ucBufferIn  
\[在\]包含长度*uBufferLength*的附加测试数据的缓冲区。

## <a name="span-iddot11manufacturingtestquerydataspanspan-iddot11manufacturingtestquerydataspandot11manufacturingtestquerydata"></a><span id="dot11_manufacturing_test_query_data"></span><span id="DOT11_MANUFACTURING_TEST_QUERY_DATA"></span>dot11\_制造\_测试\_查询\_数据


**Dot11\_制造\_测试\_查询\_数据**命令使该应用程序读取数据中的特定位置。

``` syntax
typedef struct _DOT11_MANUFACTURING_TEST_QUERY_DATA {
    ULONG uKey;
    ULONG uOffset;
    ULONG uBufferLength;
    ULONG uBytesRead;
    UCHAR ucBufferOut[1];
} DOT11_MANUFACTURING_TEST_QUERY_DATA, * PDOT11_MANUFACTURING_TEST_QUERY_DATA;
```

<span id="uKey"></span><span id="ukey"></span><span id="UKEY"></span>*uKey*  
\[在\]的键是特定 IHV 和可以是对特定收银机的引用或命名表中的条目。

<span id="uOffset"></span><span id="uoffset"></span><span id="UOFFSET"></span>*uOffset*  
\[在\]内数据的偏移量。

<span id="uBufferLength"></span><span id="ubufferlength"></span><span id="UBUFFERLENGTH"></span>*uBufferLength*  
\[在\]的数据缓冲区中读取的字节数。

<span id="uBytesRead"></span><span id="ubytesread"></span><span id="UBYTESREAD"></span>uBytesRead  
\[出\]驱动程序读取的数据的字节的实际数目。

<span id="ucBufferOut"></span><span id="ucbufferout"></span><span id="UCBUFFEROUT"></span>ucBufferOut  
\[出\]包含驱动程序读取的数据。

## <a name="span-iddot11manufacturingtestsleepspanspan-iddot11manufacturingtestsleepspandot11manufacturingtestsleep"></a><span id="dot11_manufacturing_test_sleep"></span><span id="DOT11_MANUFACTURING_TEST_SLEEP"></span>dot11\_制造\_测试\_睡眠


**Dot11\_制造\_测试\_睡眠**命令指示进入低电源状态，用于指定时间或无限期的 Wi-Fi 芯片组。

对于此测试，应关闭所有无线电收发器，并应关闭 Wi-fi® 芯片组。 此项测试确认 Wi-Fi 可以进入睡眠状态，即当前消耗量限值内，并且有 Wi-Fi 在关闭时没有电流。

驱动程序可以唤醒从睡眠状态在任何时候通过使用**dot11\_制造\_测试\_唤醒**命令。 如果睡眠超时设置为 − 1，当驱动程序除非要求通过唤醒，应无限期地休眠**dot11\_制造\_测试\_唤醒**。 当驱动程序唤醒，由于超时过期或唤醒命令的结果是时，它应通过使用来表示其清醒状态**NDIS\_状态\_DOT11\_制造\_回调**回调处理程序设置为*dot11ManufacturingCallbackType*和**dot11\_制造\_回调\_睡眠\_完成**。

``` syntax
typedef struct _DOT11_MANUFACTURING_TEST_SLEEP {
    ULONG uSleepTime;
    PVOID pvContext;
} DOT11_MANUFACTURING_TEST_SLEEP, * PDOT11_MANUFACTURING_TEST_SLEEP;
```

<span id="uSleepTime"></span><span id="usleeptime"></span><span id="USLEEPTIME"></span>*uSleepTime*  
\[在\]的驱动程序进入睡眠状态，以毫秒为单位的时间量。 如果设置为 − 1 时，驱动程序将进入休眠状态，直到由使用**dot11\_制造\_测试\_唤醒**命令。

<span id="pvContext"></span><span id="pvcontext"></span><span id="PVCONTEXT"></span>*pvContext*  
\[在\]驱动程序返回给应用程序使用的测试完成状态时使用的上下文**dot11\_制造\_回调\_睡眠\_完成**。

## <a name="span-iddot11manufacturingtestawakespanspan-iddot11manufacturingtestawakespandot11manufacturingtestawake"></a><span id="dot11_manufacturing_test_awake"></span><span id="DOT11_MANUFACTURING_TEST_AWAKE"></span>dot11\_制造\_测试\_清醒


**Dot11\_制造\_测试\_唤醒**命令会从它的低功耗休眠状态唤醒的 Wi-Fi 芯片组。 驱动程序返回**状态\_无效\_参数**如果芯片组已处于唤醒状态时发送此命令。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[添加 Wi-Fi 制造的 OID 接口的测试支持](adding-wi-fi-manufacturing-test-support-to-the-oid-interface.md)

 

 






