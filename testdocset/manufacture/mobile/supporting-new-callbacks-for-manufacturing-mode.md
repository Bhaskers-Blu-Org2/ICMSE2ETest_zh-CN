---
author: kpacquer
Description: "支持新的回调的制造模式"
ms.assetid: c94468fa-4581-4d51-9e48-e751d070db28
MSHAttr: PreferredLib:/library/windows/hardware
title: "支持新的回调的制造模式"
ms.openlocfilehash: 69c656c35fb1deb36951e80e9baa7dfa2901372f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="supporting-new-callbacks-for-manufacturing-mode"></a>支持新的回调的制造模式


在制造模式下运行时，Wi-Fi 微型端口驱动程序必须添加对以下新回调的支持。

## <a name="span-idndisstatusdot11manufacturingcallbackspanspan-idndisstatusdot11manufacturingcallbackspanndisstatusdot11manufacturingcallback"></a><span id="NDIS_STATUS_DOT11_MANUFACTURING_CALLBACK"></span><span id="ndis_status_dot11_manufacturing_callback"></span>NDIS\_状态\_DOT11\_制造\_回调


**NDIS\_状态\_DOT11\_制造\_回调**回调用于指示特定请求的完成状态。 在此处定义为该回调所使用的数据结构。

``` syntax
typedef enum _DOT11_MANUFACTURING_CALLBACK_TYPE {
    dot11_manufacturing_callback_unknown = 0,
    dot11_manufacturing_callback_self_test_complete = 1,
    dot11_manufacturing_callback_sleep_complete = 2,
    dot11_manufacturing_callback_IHV_start = 0x80000000,
    dot11_manufacturing_callback_IHV_end = 0xffffffff
} DOT11_MANUFACTURING_CALLBACK_TYPE, * PDOT11_MANUFACTURING_CALLBACK_TYPE;

typedef struct DOT11_MANUFACTURING_CALLBACK_PARAMETERS {
#define DOT11_MANUFACTURING_CALLBACK_REVISION_1  1
    NDIS_OBJECT_HEADER                Header;
    DOT11_MANUFACTURING_CALLBACK_TYPE dot11ManufacturingCallbackType;
    ULONG                             uStatus;
    PVOID                             pvContext;
} DOT11_MANUFACTURING_CALLBACK_PARAMETERS, * PDOT11_MANUFACTURING_CALLBACK_PARAMETERS;
```

<span id="dot11_manufacturing_callback_self_test_complete"></span><span id="DOT11_MANUFACTURING_CALLBACK_SELF_TEST_COMPLETE"></span>**dot11\_制造\_回调\_self\_测试\_完成**  
**dot11\_制造\_回调\_自\_测试\_完成**驱动程序在请求时调用自我测试驱动程序完成。 此回调必须返回自我测试请求，以及自我测试结果的上下文。 然后，驱动程序将调用**OID\_DOT11\_制造\_测试**OID 与**dot11\_制造\_测试\_自我\_查询\_结果**命令来获取测试的详细的结果。

<span id="dot11_manufacturing_callback_sleep_complete"></span><span id="DOT11_MANUFACTURING_CALLBACK_SLEEP_COMPLETE"></span>**dot11\_制造\_回调\_睡眠\_完成**  
**dot11\_制造\_回调\_睡眠\_完成**驱动程序执行请求的睡眠命令时调用。 此回调必须返回休眠请求，以及这一状态的上下文是否成功或失败。 当应用程序发送一个请求，以唤醒从睡眠状态的驱动程序，驱动程序也被称为此回调。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[添加 Wi-Fi 制造的 OID 接口的测试支持](adding-wi-fi-manufacturing-test-support-to-the-oid-interface.md)

 

 






