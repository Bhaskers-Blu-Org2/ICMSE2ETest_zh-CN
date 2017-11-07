---
author: kpacquer
Description: "在制造模式下支持现有的 OID 命令"
ms.assetid: 8b26ab8e-00b8-4f4c-a7c5-8fca4c5b1e3f
MSHAttr: PreferredLib:/library/windows/hardware
title: "在制造模式下支持现有的 OID 命令"
ms.openlocfilehash: 0faf01e3e7b1ecb551c043bf2fa569c3b4fac91d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="supporting-existing-oid-commands-in-manufacturing-mode"></a>在制造模式下支持现有的 OID 命令


在制造模式下运行时，Wi-Fi 微型端口驱动程序必须添加对下列现有 Oid 的支持。

## <a name="span-idoidgensupportedguidsspanspan-idoidgensupportedguidsspanoidgensupportedguids"></a><span id="OID_GEN_SUPPORTED_GUIDS"></span><span id="oid_gen_supported_guids"></span>OID\_GEN\_支持\_的 GUID


**OID\_GEN\_支持\_GUID**命令调用在查询模式中获得支持的 GUID 的集。 有关完整文档，请参阅[OID\_GEN\_支持\_GUID](http://msdn.microsoft.com/library/ff569641.aspx)在 MSDN 上。

**请注意**  
出于兼容性目的通常调用此 OID。 驱动程序可以选择忽略它，如果需要，并返回**NDIS\_状态\_不\_支持**相反。

 

## <a name="span-idoidgenvendoridspanspan-idoidgenvendoridspanoidgenvendorid"></a><span id="OID_GEN_VENDOR_ID"></span><span id="oid_gen_vendor_id"></span>OID\_GEN\_供应商\_ID


**OID\_GEN\_供应商\_ID**查询模式返回跟单字节标识特定网卡与供应商指派的 3 位 IEEE 注册供应商代码中调用命令 有关完整文档，请参阅[OID\_GEN\_供应商\_ID](http://msdn.microsoft.com/library/ff569651.aspx)在 MSDN 上。

## <a name="span-idoidgenvendordescriptionspanspan-idoidgenvendordescriptionspanoidgenvendordescription"></a><span id="OID_GEN_VENDOR_DESCRIPTION"></span><span id="oid_gen_vendor_description"></span>OID\_GEN\_供应商\_说明


**OID\_GEN\_供应商\_说明**命令调用中返回 NULL 结尾的字符串，用于描述以 ANSI 格式的 NIC 的查询模式。 有关完整文档，请参阅[OID\_GEN\_供应商\_说明](http://msdn.microsoft.com/library/ff569649.aspx)在 MSDN 上。

## <a name="span-idoidgencurrentlookaheadspanspan-idoidgencurrentlookaheadspanoidgencurrentlookahead"></a><span id="OID_GEN_CURRENT_LOOKAHEAD"></span><span id="oid_gen_current_lookahead"></span>OID\_GEN\_当前\_预测先行


**OID\_GEN\_当前\_预测先行**命令调用中设置模式，可以指定接收到的数据包发送到协议驱动程序的数据的字节数。 有关完整文档，请参阅[OID\_GEN\_当前\_预测先行](http://msdn.microsoft.com/library/ff569574.aspx)在 MSDN 上。

**请注意**  
出于兼容性目的通常调用此 OID。 驱动程序可以选择忽略它，如果需要，并返回**NDIS\_状态\_不\_支持**相反。

 

## <a name="span-idoidpmaddwolpatternspanspan-idoidpmaddwolpatternspanoidpmaddwolpattern"></a><span id="OID_PM_ADD_WOL_PATTERN"></span><span id="oid_pm_add_wol_pattern"></span>OID\_PM\_添加\_WOL\_模式


**OID\_PM\_添加\_WOL\_模式**命令调用中指定 WOL 模式的设置模式。 有关完整文档，请参阅[OID\_PM\_添加\_WOL\_模式](http://msdn.microsoft.com/library/ff569764.aspx)在 MSDN 上。

**请注意**  
出于兼容性目的通常调用此 OID。 驱动程序可以选择忽略它，如果需要，并返回**NDIS\_状态\_不\_支持**相反。

 

## <a name="span-idoiddot11resetrequestspanspan-idoiddot11resetrequestspanoiddot11resetrequest"></a><span id="OID_DOT11_RESET_REQUEST"></span><span id="oid_dot11_reset_request"></span>OID\_DOT11\_重置\_请求


**OID\_DOT11\_重置\_请求**命令调用中返回驱动程序所使用的 IEEE MAC 地址的查询模式。 有关完整文档，请参阅[OID\_DOT11\_重置\_请求](http://msdn.microsoft.com/library/ff569409.aspx)在 MSDN 上。

## <a name="span-idoiddot11currentaddressspanspan-idoiddot11currentaddressspanoiddot11currentaddress"></a><span id="OID_DOT11_CURRENT_ADDRESS"></span><span id="oid_dot11_current_address"></span>OID\_DOT11\_当前\_地址


**OID\_DOT11\_当前\_地址**命令调用中返回驱动程序所使用的 IEEE MAC 地址的查询模式。 有关完整文档，请参阅[OID\_DOT11\_当前\_地址](http://msdn.microsoft.com/library/ff569125.aspx)在 MSDN 上。

## <a name="span-idoiddot11supportedphytypesspanspan-idoiddot11supportedphytypesspanoiddot11supportedphytypes"></a><span id="OID_DOT11_SUPPORTED_PHY_TYPES"></span><span id="oid_dot11_supported_phy_types"></span>OID\_DOT11\_支持\_PHY\_类型


**OID\_DOT11\_支持\_PHY\_类型**命令调用在查询模式中请求支持 802.11 站 PHY 类型的列表。 有关完整文档，请参阅[OID\_DOT11\_支持\_PHY\_类型](http://msdn.microsoft.com/library/ff569426.aspx)在 MSDN 上。

## <a name="span-idoiddot11currentphyidspanspan-idoiddot11currentphyidspanoiddot11currentphyid"></a><span id="OID_DOT11_CURRENT_PHY_ID"></span><span id="oid_dot11_current_phy_id"></span>OID\_DOT11\_当前\_PHY\_ID


**OID\_DOT11\_当前\_PHY\_ID**命令调用在集中模式下设置当前 PHY id。 有关完整文档，请参阅[OID\_DOT11\_当前\_PHY\_ID](http://msdn.microsoft.com/library/ff569135.aspx)在 MSDN 上。

## <a name="span-idoiddot11hardwarephystatespanspan-idoiddot11hardwarephystatespanoiddot11hardwarephystate"></a><span id="OID_DOT11_HARDWARE_PHY_STATE"></span><span id="oid_dot11_hardware_phy_state"></span>OID\_DOT11\_硬件\_PHY\_状态


**OID\_DOT11\_硬件\_PHY\_状态**命令调用中返回的 PHY 电源状态的查询模式。 有关完整文档，请参阅[OID\_DOT11\_硬件\_PHY\_状态](http://msdn.microsoft.com/library/ff569370.aspx)在 MSDN 上。

## <a name="span-idoiddot11nicpowerstatespanspan-idoiddot11nicpowerstatespanoiddot11nicpowerstate"></a><span id="OID_DOT11_NIC_POWER_STATE"></span><span id="oid_dot11_nic_power_state"></span>OID\_DOT11\_NIC\_电源\_状态


**OID\_DOT11\_NIC\_电源\_状态**命令调用中返回的 NIC 电源状态的查询模式。 有关完整文档，请参阅[OID\_DOT11\_NIC\_电源\_状态](http://msdn.microsoft.com/library/ff569392.aspx)在 MSDN 上。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[添加 Wi-Fi 制造的 OID 接口的测试支持](adding-wi-fi-manufacturing-test-support-to-the-oid-interface.md)

 

 






