---
author: Justinha
Description: "修复上双重引导计算机的启动菜单"
ms.assetid: 166c9499-b9b2-48bb-9ff6-d91dc0e497a3
MSHAttr: PreferredLib:/library/windows/hardware
title: "修复上双重引导计算机的启动菜单"
ms.openlocfilehash: b5425c60f06bb859eee1a01ad4c198cbc34940ae
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="repair-the-boot-menu-on-a-dual-boot-pc"></a>修复上双重引导计算机的启动菜单


当设置启动多个操作系统的 PC，有时可能会丢失能够引导至操作系统之一。 BCDBoot 选项允许您快速地添加一个基于 Windows 操作系统的启动选项。

## <a name="span-idrepairingawindowspartitiononadual-bootpcspanspan-idrepairingawindowspartitiononadual-bootpcspanspan-idrepairingawindowspartitiononadual-bootpcspanrepairing-a-windows-partition-on-a-dual-boot-pc"></a><span id="Repairing_a_Windows_partition_on_a_dual-boot_PC"></span><span id="repairing_a_windows_partition_on_a_dual-boot_pc"></span><span id="REPAIRING_A_WINDOWS_PARTITION_ON_A_DUAL-BOOT_PC"></span>修复在双启动计算机上的 Windows 分区


1.  安装单独的硬盘或准备一个单独的分区，每个操作系统。

2.  安装操作系统。 例如，如果您的 PC 有 Windows 8.1，到其他硬盘或分区上安装 Windows 10。

3.  重新启动计算机。 显示启动菜单应列出这两个操作系统。

    如果没有列出这两个操作系统︰

    1.  打开命令行，请以管理员身份从窗口，在启动到命令行上使用的 Windows 安装盘和 presssing Shift + F10，或通过引导至 Windows PE ([WinPE︰ 创建 USB 可启动驱动器](winpe-create-usb-bootable-drive.md))。

    2.  添加 Windows 操作系统的引导选项。

        ``` syntax
        Bcdboot D:\Windows
        ```

    3.  重新启动计算机。 现在，启动菜单将显示两个菜单选项。

## <a name="span-idrepairanotheroperatingsystempartitionspanspan-idrepairanotheroperatingsystempartitionspanspan-idrepairanotheroperatingsystempartitionspanrepair-another-operating-system-partition"></a><span id="Repair_another_operating_system_partition"></span><span id="repair_another_operating_system_partition"></span><span id="REPAIR_ANOTHER_OPERATING_SYSTEM_PARTITION"></span>修复另一个操作系统分区


您可以手动添加使用 BCDEdit，创建分区，也可以使用诸如[EasyBCD](http://go.microsoft.com/fwlink/?LinkId=330254)之类的第三方工具设置引导分区。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[BCDboot 命令行选项](bcdboot-command-line-options-techref-di.md)

 

 






