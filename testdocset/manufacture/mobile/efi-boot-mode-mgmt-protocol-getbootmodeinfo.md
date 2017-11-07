---
author: kpacquer
Description: "使用此函数来从 UEFI 固件检索启动模式和可选配置文件名称。"
ms.assetid: 389dab4d-9f74-4c33-9d02-9b6510581fd8
MSHAttr: PreferredLib:/library/windows/hardware
title: "EFI\\_启动\\_模式\\_管理\\_协议。GetBootModeInfo"
ms.openlocfilehash: 9510b932ebb239b3d61be02b6a1744ac36669641
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="efibootmodemgmtprotocolgetbootmodeinfo"></a>EFI\_启动\_模式\_管理\_协议。GetBootModeInfo


使用此函数来从 UEFI 固件检索启动模式和可选配置文件名称。

``` syntax
typedef EFI_STATUS
(EFIAPI *EFI_GET_BOOT_MODE_INFO)(
    IN  struct _EFI_BOOT_MODE_MGMT_PROTOCOL *This,
    OUT EFI_OS_BOOT_MODE                    *BootMode,
    IN OUT UINT32                           *ProfileNameElements,
    OUT CHAR16                              *ProfileName
    );
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>参数


<span id="This"></span><span id="this"></span><span id="THIS"></span>*这*  
\[在\]一个指针，指向**EFI\_启动\_模式\_管理\_协议**实例。

<span id="BootMode"></span><span id="bootmode"></span><span id="BOOTMODE"></span>*启动模式*  
\[出\]一个指针，指向包含设备的启动模式的枚举。

<span id="ProfileNameElements"></span><span id="profilenameelements"></span><span id="PROFILENAMEELEMENTS"></span>*ProfileNameElements*  
\[在\] \[out\]接收配置文件名称中的字符数的 UINT32 值的指针。

<span id="ProfileName"></span><span id="profilename"></span><span id="PROFILENAME"></span>*ProfileName*  
\[出\]一个指针，指向当前配置文件的名称。

## <a name="span-idreturnvaluesspanspan-idreturnvaluesspanspan-idreturnvaluesspanreturn-values"></a><span id="Return_values"></span><span id="return_values"></span><span id="RETURN_VALUES"></span>返回值


返回以下状态代码之一︰

| 返回代码             | 说明                                                      |
|-------------------------|------------------------------------------------------------------|
| EFI\_成功            | 成功                                                          |
| EFI\_不\_找到         | 找不到启动模式的数据。                                |
| EFI\_卷\_已损坏  | 所需的存储分区未初始化或已损坏。 |
| EFI\_无效\_参数     | 无效的参数传递给该函数。                 |
| EFI\_缓冲区\_太\_小型 | 在提供的缓冲区空间不足。                         |

 

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>要求


**标头︰**用户生成

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[启动模式管理 UEFI 协议](boot-mode-management-uefi-protocol.md)

 

 






