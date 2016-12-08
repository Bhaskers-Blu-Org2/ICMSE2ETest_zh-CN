---
author: kpacquer
Description: "在制造模式下支持更新的 OID 行为"
ms.assetid: 1ae614a7-fbf9-4c3b-834e-d62d7f7ab352
MSHAttr: PreferredLib:/library/windows/hardware
title: "在制造模式下支持更新的 OID 行为"
ms.openlocfilehash: 35d980a65afcf99fec7c858afda7d32975d5bf14
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="supporting-updated-oid-behavior-in-manufacturing-mode"></a>在制造模式下支持更新的 OID 行为


在制造模式下运行时，Wi-Fi 微型端口驱动程序必须添加对已更新了下列 Oid 的支持。

## <a name="span-idoiddot11operationmodecapabilityspanspan-idoiddot11operationmodecapabilityspanoiddot11operationmodecapability"></a><span id="OID_DOT11_OPERATION_MODE_CAPABILITY"></span><span id="oid_dot11_operation_mode_capability"></span>OID\_DOT11\_操作\_模式\_功能


**OID\_DOT11\_操作\_模式\_功能**命令调用中返回列表中的操作模式驱动程序支持的查询模式。 此命令作为以前的记录，但现在所需的驱动程序以支持新的操作模式， **DOT11\_操作\_模式\_制造**，即在其中执行加工操作的上下文。 该 OID 的完整文档，请参阅[OID\_DOT11\_操作\_模式\_功能](http://msdn.microsoft.com/library/ff569396.aspx)在 MSDN 上。

``` syntax
#define DOT11_OPERATION_MODE_UNKNOWN            0x00000000
#define DOT11_OPERATION_MODE_STATION            0x00000001
#define DOT11_OPERATION_MODE_AP                 0x00000002
#define DOT11_OPERATION_MODE_EXTENSIBLE_STATION 0x00000004
#define DOT11_OPERATION_MODE_EXTENSIBLE_AP      0x00000008
#define DOT11_OPERATION_MODE_WFD_DEVICE         0x00000010
#define DOT11_OPERATION_MODE_WFD_GROUP_OWNER    0x00000020
#define DOT11_OPERATION_MODE_WFD_CLIENT         0x00000040
#define DOT11_OPERATION_MODE_MANUFACTURING      0x40000000
#define DOT11_OPERATION_MODE_NETWORK_MONITOR    0x80000000

typedef struct _DOT11_OPERATION_MODE_CAPABILITY {
    ULONG uReserved;
    ULONG uMajorVersion;
    ULONG uMinorVersion;
    ULONG uNumOfTXBuffers;
    ULONG uNumOfRXBuffers;
    ULONG uOpModeCapability;
} DOT11_OPERATION_MODE_CAPABILITY, * PDOT11_OPERATION_MODE_CAPABILITY;
```

## <a name="span-idoiddot11currentoperationmodespanspan-idoiddot11currentoperationmodespanoiddot11currentoperationmode"></a><span id="OID_DOT11_CURRENT_OPERATION_MODE"></span><span id="oid_dot11_current_operation_mode"></span>OID\_DOT11\_当前\_操作\_模式


**OID\_DOT11\_当前\_操作\_模式**命令可以调用在组或查询模式下配置或返回驱动程序的当前操作模式。

此命令作为以前的记录，但现在需要驱动程序以支持**DOT11\_操作\_模式\_制造**操作模式。 该 OID 的完整文档，请参阅[OID\_DOT11\_当前\_操作\_模式](https://msdn.microsoft.com/library/windows/hardware/ff569132)在 MSDN 上。

``` syntax
typedef struct _DOT11_CURRENT_OPERATION_MODE {
    ULONG uReserved;
    ULONG uCurrentOpMode;
} DOT11_CURRENT_OPERATION_MODE, * PDOT11_CURRENT_OPERATION_MODE; 
```

<span id="uCurrentOpMode"></span><span id="ucurrentopmode"></span><span id="UCURRENTOPMODE"></span>*uCurrentOpMode*  
\[在\]指定要设置的驱动程序操作模式。 此参数还用作占位符的驱动程序返回时在查询模式下调用的操作模式。 如果驱动程序不支持请求的操作模式，则应返回**NDIS\_状态\_坏\_版本**。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[添加 Wi-Fi 制造的 OID 接口的测试支持](adding-wi-fi-manufacturing-test-support-to-the-oid-interface.md)

 

 






