---
title: "创作自定义录制配置文件"
description: "创作自定义录制配置文件"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 4f33a662-0883-48b2-aa50-eb2dffc244d9
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: c0c11cbdeccc7b438355c7797d3b6afe8721dcaa
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="author-a-custom-recording-profile"></a>创作自定义录制配置文件


此过程介绍如何创作自定义录制配置文件在 Windows 性能记录器 (WPR)。 您可以创作自定义配置文件具有.wprp 扩展名的 XML 文件中。 是完整的架构，并参考信息的可用请参阅[记录配置文件 XML 参考](recording-profile-xml-reference.md)。 是有关创作录制配置文件的详细信息的可用请参阅[创作录制的配置文件](authoring-recording-profiles.md)。

**若要编写自定义录制配置文件**

1.  在 XML 编辑器中，创建新的 XML 文件。

2.  输入收集器定义。 有关详细信息，请参阅[1。收集器定义](1-collector-definitions.md)。

3.  输入系统和事件提供程序定义。 有关详细信息，请参阅[2。系统和事件提供程序定义](2-system-and-event-provider-definitions.md)。

4.  输入配置文件定义。 有关详细信息，请参阅[3。配置文件定义](3-profile-definitions.md)。

    **请注意**  
    如果您希望自定义的配置文件来停止和掷回如果某些提供程序不会启动，**严格**将属性设置为"true"。 有关此选项的详细信息，请参阅[严格的供应商](strict-providers.md)。

     

5.  以.wprp 扩展名保存该文件。

您可以定义派生的收集、 提供商和继承以前在同一个文件或另一个文件中定义的基版本的配置文件。 有关此选项的详细信息，请参阅[继承](inheritance.md)。

## <a name="related-topics"></a>相关的主题


[WPR 常见方案](windows-performance-recorder-common-scenarios.md)

 

 







