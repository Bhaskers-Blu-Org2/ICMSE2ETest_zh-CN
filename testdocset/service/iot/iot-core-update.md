---
author: kpacquer
Description: "Windows 10 IoT 核心 （IoT 核心） 设备将自动接收通过连接到 internet 时 Windows 更新的操作系统更新。"
ms.assetid: d8298c99-6fa7-4825-a0b8-181b99e40975
MSHAttr: PreferredLib:/library/windows/hardware
title: "IoT 核心更新"
ms.openlocfilehash: 0d4b5ead233fc6a1aae4dc0f76e8da5043905366
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="iot-core-update"></a>IoT 核心更新


Windows 10 IoT 核心 （IoT 核心） 设备自动接收通过连接到 internet 时 Windows 更新的操作系统更新。

-   **操作系统更新。** 操作系统更新包含安全更新的所有 Microsoft 程序包 (releasetype = 生产) 中的 ESP （EFI 系统分区） 和主操作系统分区。 这些更新将自动执行。 OEM 和企业客户可以选择管理使用 Windows 10 IoT 核心 Pro SKU 的操作系统更新。 若要了解详细信息，请参阅[管理更新](managing-iot-device-update.md)。

-   **Windows 应用商店应用程序更新。** 提交到 Windows 应用商店您更新已签名的软件包。 当您的设备连接到互联网时，他们将定期检查有更新的 Windows 应用商店，并自动安装更新。 

<!---   **OEM updates.** These are also referred to as Board Support Package (BSP) updates. OEMs develop specific BSP updates for their devices such as the Raspberry Pi 2 and the Minnowboard Max. These are then published to the Microsoft Update server where specified IoT Core devices can download and receive the OEM updates automatically. -->
