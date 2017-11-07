---
author: Justinha
Description: "（uefi） 安装媒体格式和默认引导行为"
ms.assetid: 983e25d4-ce72-463e-ad59-02467f19f4a4
MSHAttr: PreferredLib:/library/windows/hardware
title: "（uefi） 安装媒体格式和默认引导行为"
ms.openlocfilehash: 4dd4e79f8dbeda7c300b3dfc0d4262da7770b487
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="uefi-installation-media-format-and-default-boot-behavior"></a>（uefi） 安装媒体格式和默认引导行为


本部分介绍安装媒体格式和 UEFI 平台的缺省引导行为。

## <a name="span-idinstallationmediaguidelinesspanspan-idinstallationmediaguidelinesspanspan-idinstallationmediaguidelinesspaninstallation-media-guidelines"></a><span id="Installation_media_guidelines"></span><span id="installation_media_guidelines"></span><span id="INSTALLATION_MEDIA_GUIDELINES"></span>安装介质指南


-   Windows 安装媒体上这两种 BIOS 支持引导，通过利用多项 El Torito 引导目录 UEFI 平台支持。
-   El Torito 启动项的默认值是 BIOS 条目包含 80x86 平台 ID，它被定义为以十六进制格式"0x00"。
-   第二个 El Torito 引导条目是以十六进制形式包括平台 ID"0xEF"作为 EFI 项。 该条目引用 FAT 分区，其中包含可启动 EFI 应用程序在\\EFI\\启动\\BOOTX64。EFI。

## <a name="span-iddefaultbootbehaviorspanspan-iddefaultbootbehaviorspanspan-iddefaultbootbehaviorspandefault-boot-behavior"></a><span id="Default_boot_behavior"></span><span id="default_boot_behavior"></span><span id="DEFAULT_BOOT_BEHAVIOR"></span>缺省的引导行为


固件供应商必须确保满足下列条件︰

-   BIOS 将忽略没有 80x86 平台 ID，它被定义为以十六进制格式"0x00"的启动项目。 若要忽略其他启动项目的故障会导致混乱的启动菜单的显示给最终用户。
-   在基于 BIOS 不用提示条目上的 BIOS 启动。
-   （uefi） 启动管理器忽略引导项没有"0xEF"平台 id。
-   基于 EFI 项不用提示在 UEFI 引导管理器启动。

若要支持能够从 DVD 介质引导，Windows 安装 DVD 中包含启用启动 BIOS 或 UEFI 中的多个 El Torito 引导项。 El Torito 启动项目为 BIOS 默认值。

Windows 支持从 UEFI 2.3 规范"非可移动介质引导行为"一节。 在 Windows 安装和 bootmgfw.efi 为需要更新时，Windows 将复制 Windows 启动应用程序\\efi\\microsoft\\启动\\到 bootmgfw.efi \\efi\\启动\\在 EFI 系统分区上引导*{弧}*.efi。 此副本使 windows 默认启动选项，如果非易失性 RAM (NVRAM) 引导项不可用，例如当一个硬盘从一个平台转移到另一个。

当升级 Windows，Windows 会保留现有的引导顺序。 在执行全新安装的 Windows 时，Windows 更新启动顺序，以便在列表中第一个启动项。

## <a name="span-idothermediainformationspanspan-idothermediainformationspanspan-idothermediainformationspanother-media-information"></a><span id="Other_media_information"></span><span id="other_media_information"></span><span id="OTHER_MEDIA_INFORMATION"></span>其他媒体信息


下面的附加准则适用于引导介质︰

-   Windows 支持 CD 和 DVD 从通用磁盘格式 (UDF) 文件系统的引导。 Windows 安装媒体还使用 El Torito，并使用 UDF 桥格式支持 ISO 9660 和 UDF 版本 1.02 文件系统构建。
-   Windows 评估和部署工具包 (Windows ADK) 包括支持多项 El Torito 引导目录创建的 Oscdimg.exe 的更新的版本。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[UEFI 固件](uefi-firmware.md)

[BCDBoot 命令行选项](bcdboot-command-line-options-techref-di.md)

[引导至 UEFI 模式或传统 BIOS 模式](boot-to-uefi-mode-or-legacy-bios-mode.md)

[在 UEFI 或旧版 BIOS 模式下的 WinPE︰ 引导](winpe-boot-in-uefi-or-legacy-bios-mode.md)

 

 






