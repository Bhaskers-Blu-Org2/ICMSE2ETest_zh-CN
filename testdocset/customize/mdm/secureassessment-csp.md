---
title: "SecureAssessment 的 CSP"
description: "SecureAssessment 的 CSP"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 6808BE4B-961E-4638-BF15-FD7841D1C00A
ms.openlocfilehash: e1294917c23927e6ef0e81088a6aed3a460cfff2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="secureassessment-csp"></a>SecureAssessment 的 CSP


SecureAssessment 配置服务提供程序用于提供安全评估浏览器的配置信息。

下图显示的 SecureAssessment 配置服务提供程序管理对象以树格式由开放移动联盟设备管理 (OMA DM)，OMA 客户端资源调配和企业 DM。

![secureassessment](images/secureassessment-csp.png)

<a href="" id="--vendor-msft-secureassessment"></a>**./Vendor/MSFT/SecureAssessment**  
SecureAssessment 配置服务提供程序的根节点。

受支持的操作是获得。

<a href="" id="launchuri"></a>**LaunchURI**  
URI 指向安全评估浏览器启动时自动加载的评估。

受支持的操作是添加、 删除、 获取，并替换。

<a href="" id="testeraccount"></a>**TesterAccount**  
考虑测试的用户名称。

-   若要指定域帐户，请使用域\\用户。
-   若要指定 AAD 帐户，请使用 username@tenant.com。
-   若要指定本地帐户，使用的用户名。

受支持的操作是添加、 删除、 获取，并替换。

## <a name="related-topics"></a>相关的主题


[配置服务提供程序的引用](configuration-service-provider-reference.md)

 

 






