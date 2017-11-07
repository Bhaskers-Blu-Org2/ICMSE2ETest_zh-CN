---
author: kpacquer
Description: "启动模式管理协议用于确定在启动时，应使用操作系统的引导模式。"
ms.assetid: 9782c51d-8915-43ef-8a64-9c8be9dc228d
MSHAttr: PreferredLib:/library/windows/hardware
title: "启动模式管理 UEFI 协议"
ms.openlocfilehash: 6d572f877c2c6e8d2ac89d420588151d6621c407
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="boot-mode-management-uefi-protocol"></a>启动模式管理 UEFI 协议


启动模式管理协议用于确定在启动时，应使用操作系统的引导模式。

## <a name="span-idefibootmodemgmtprotocolspanspan-idefibootmodemgmtprotocolspanefibootmodemgmtprotocol"></a><span id="EFI_BOOT_MODE_MGMT_PROTOCOL"></span><span id="efi_boot_mode_mgmt_protocol"></span>EFI\_启动\_模式\_管理\_协议


本部分提供了详细的描述**EFI\_启动\_模式\_管理\_协议**。

**GUID**

``` syntax
#define EFI_BOOT_MODE_MGMT_PROTOCOL_GUID \
   { 0xBE464946, 0x9787, 0x4FEB, { 0xBD, 0x71, 0x14, 0xC1, 0xC5, 0x2D, 0x69, 0xD1 } }
```

**修订号**

``` syntax
#define EFI_BOOT_MODE_MGMT_PROTOCOL_REVISION 0x00010000
```

**协议界面结构**

``` syntax
typedef struct _EFI_BOOT_MODE_MGMT_PROTOCOL {
    UINT32                 Revision;
    EFI_SET_BOOT_MODE_INFO SetBootModeInfo;
    EFI_GET_BOOT_MODE_INFO GetBootModeInfo;
} EFI_BOOT_MODE_MGMT_PROTOCOL;
```

**成员**

<span id="Revision"></span><span id="revision"></span><span id="REVISION"></span>**修订**  
修订版**EFI\_启动\_模式\_管理\_协议**遵循。 所有未来的修订必须向后兼容。 如果将来的版本不兼容，则必须使用不同的 GUID。

<span id="GetBootModeInfo"></span><span id="getbootmodeinfo"></span><span id="GETBOOTMODEINFO"></span>**GetBootModeInfo**  
确定在启动时，应使用操作系统的引导模式。 请参阅 EFI[\_启动\_模式\_管理\_协议。GetBootModeInfo](efi-boot-mode-mgmt-protocol-getbootmodeinfo.md)

<span id="SetBootModeInfo"></span><span id="setbootmodeinfo"></span><span id="SETBOOTMODEINFO"></span>**SetBootModeInfo**  
指定启动，包括可选的配置文件名称时，应使用操作系统的引导模式。 请参阅 EFI[\_启动\_模式\_管理\_协议。SetBootModeInfo](efi-boot-mode-mgmt-protocol-setbootmodeinfo.md)

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>要求


**标头︰**用户生成

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[制造模式](manufacturing-mode.md)

 

 






