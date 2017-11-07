---
author: kpacquer
Description: "报告运营模式功能"
ms.assetid: 1beda5a7-63d7-4519-955c-cc240733fc49
MSHAttr: PreferredLib:/library/windows/hardware
title: "报告运营模式功能"
ms.openlocfilehash: c30f90714aaa4f933bb109ac10b8f064ff4d96f7
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="reporting-operating-mode-capabilities"></a>报告运营模式功能


如果 Wi-fi 驱动程序支持在制造模式下运行，它应将制造模式添加到其支持的功能的列表。 您可以使用查询的受支持的操作模式功能**OID\_DOT11\_操作\_模式\_功能**命令，将该驱动程序所支持的操作模式返回的信息。 有关更多信息**OID\_DOT11\_操作\_模式\_功能**，请参阅[支持的更新 OID 在制造模式下的行为](supporting-updated-oid-behavior-in-manufacturing-mode.md)。

若要切换到制造模式的驱动程序的操作模式，请使用**OID\_DOT11\_当前\_操作\_模式**命令以确保制造测试将不与冲突中的其他模式的任何驱动程序的行为。 有关更多信息**OID\_DOT11\_当前\_操作\_模式**，请参阅[支持的更新 OID 在制造模式下的行为](supporting-updated-oid-behavior-in-manufacturing-mode.md)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[添加 Wi-Fi 制造的 OID 接口的测试支持](adding-wi-fi-manufacturing-test-support-to-the-oid-interface.md)

 

 






