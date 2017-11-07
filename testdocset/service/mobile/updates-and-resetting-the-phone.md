---
author: kpacquer
Description: "更新和重置设备"
ms.assetid: ad197224-ed30-4483-816e-a48ec385197d
MSHAttr: PreferredLib:/library/windows/hardware
title: "更新和重置设备"
ms.openlocfilehash: a8b3a3d6c96d24454d0bdb6e99aafc2c70b1d1b4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="updates-and-resetting-the-device"></a>更新和重置设备


Oem 必须考虑更新用户重置设备时如何受到影响。 若要了解如何重置设备改变操作系统的基础知识，请仔细检查[重置设备](../../manufacture/mobile/resetting-a-phone-during-manufacturing.md)。

## <a name="span-idosandbspupdatesspanspan-idosandbspupdatesspanspan-idosandbspupdatesspanos-and-bsp-updates"></a><span id="OS_and_BSP_updates"></span><span id="os_and_bsp_updates"></span><span id="OS_AND_BSP_UPDATES"></span>操作系统和 BSP 更新


微软操作系统和 OEM 主板支持包 (BSP) 的更新 — — 以及所有相关的注册表更改 — — 重置设备之后依然存在。 对于用户来说，这意味着更新不需要重置设备时，会下载。 对于 OEM，这意味着较新版本的 OS 和 BSP 更新需要被设计为允许与较旧的应用程序，其更新恢复时重置设备的兼容性。

## <a name="span-idpreloadedappsspanspan-idpreloadedappsspanspan-idpreloadedappsspanpreloaded-apps"></a><span id="Preloaded_apps"></span><span id="preloaded_apps"></span><span id="PRELOADED_APPS"></span>预加载应用程序


设备重置，预加载应用程序安装当前版本的 xap 外部存储在手机上。 当前版本是原始 xap 外部设备上提供或接收到的最新版本在 OEM 无线 (OTA) 更新。 用户可能仍需要将更新下载到应用程序，如果以后的版本发布到商店但尚未交货的 OTA 更新的一部分。

有更新预加载的系统设置应用程序的其他重要事项。 有关更多信息，请参阅[系统设置应用程序和更新](system-settings-apps-and-updates.md)。

## <a name="span-idplaceholderappsspanspan-idplaceholderappsspanspan-idplaceholderappsspanplaceholder-apps"></a><span id="Placeholder_apps"></span><span id="placeholder_apps"></span><span id="PLACEHOLDER_APPS"></span>占位符的应用程序


占位符的应用程序将在设备上当前应用程序软件包中重新安装。 当前版本是原始程序包附带的设备上或作为 OTA 更新的一部分收到的最新版本。

## <a name="span-iduserappsanddataspanspan-iduserappsanddataspanspan-iduserappsanddataspanuser-apps-and-data"></a><span id="User_apps_and_data"></span><span id="user_apps_and_data"></span><span id="USER_APPS_AND_DATA"></span>用户应用程序和数据


重置设备时，将移除所有用户安装应用商店应用程序和关联的数据。 用户可以使用备份和还原功能来恢复这些应用程序。 有关更多信息，请参阅[备份我的资料](http://go.microsoft.com/fwlink/p/?LinkId=331631)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[更新](index.md)

 

 






