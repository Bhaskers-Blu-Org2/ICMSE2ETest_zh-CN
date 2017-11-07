---
author: kpacquer
Description: "定义在启动时，操作系统可以使用的可能的引导模式。"
ms.assetid: cb78662f-8ce0-4adb-97ad-e8520c8513fd
MSHAttr: PreferredLib:/library/windows/hardware
title: "EFI\\_启动\\_模式\\_信息枚举"
ms.openlocfilehash: a049094786b7ad4767391ec4b25b9bba871f75ef
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="efibootmodeinfo-enumeration"></a>EFI\_启动\_模式\_信息枚举


定义在启动时，操作系统可以使用的可能的引导模式。

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>语法


``` syntax
typedef enum _EFI_OS_BOOT_MODE {
    EfiOsBootModeFullOs = 0,
    EfiOsBootModeManufacturingOs = 1
    EfiOsBootModeMax
} EFI_OS_BOOT_MODE, *PEFI_OS_BOOT_MODE;
```

## <a name="span-idconstantsspanspan-idconstantsspanspan-idconstantsspanconstants"></a><span id="Constants"></span><span id="constants"></span><span id="CONSTANTS"></span>常量


<span id="EfiOsBootModeFullOs"></span><span id="efiosbootmodefullos"></span><span id="EFIOSBOOTMODEFULLOS"></span>**EfiOsBootModeFullOs**  
设备应正常引导至操作系统。

<span id="EfiOsBootModeManufacturingOs"></span><span id="efiosbootmodemanufacturingos"></span><span id="EFIOSBOOTMODEMANUFACTURINGOS"></span>**EfiOsBootModeManufacturingOs**  
设备处于制造模式。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[启动模式管理 UEFI 协议](boot-mode-management-uefi-protocol.md)

 

 






