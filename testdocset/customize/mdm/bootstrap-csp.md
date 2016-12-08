---
title: "引导的 CSP"
description: "引导的 CSP"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: b8acbddc-347f-4543-a45b-ad2ffae3ffd0
ms.openlocfilehash: 53ea409c6f2c2437ab402f3b7be4982786e5f016
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="bootstrap-csp"></a>引导的 CSP


启动程序配置服务提供程序设置受信任的资源调配服务器 (TPS) 的设备。

> **请注意** 在 Windows 10 Mobile 只支持引导 CSP。

 

> **请注意**  此配置服务提供商要求使用 ID\_CAP\_CSP\_基础和 ID\_CAP\_设备\_管理\_管理功能从网络配置应用程序进行访问。

 

下面的图像显示启动程序配置服务提供商以树格式由开放移动联盟 (OMA) 客户端资源调配使用。 OMA 设备管理协议不支持此配置服务提供商。

![引导 csp (cp)](images/provisioning-csp-bootstrap-cp.png)

<a href="" id="context-allow"></a>**上下文允许**  
可选项。 指定一个上下文的 TPS。 只有一个上下文被支持，则忽略此参数，并假定其值为"0"。

<a href="" id="provurl"></a>**PROVURL**  
必需。 指定的受信任的资源调配服务器 (TPS) 的位置。 PROVURL 值必须是一个完整的 URL 字符串，最大长度为 256 个字符。

## <a name="related-topics"></a>相关的主题


[配置服务提供程序的引用](configuration-service-provider-reference.md)

 

 






