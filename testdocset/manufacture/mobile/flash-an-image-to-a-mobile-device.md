---
Description: "闪烁是进入移动设备的移动图像的过程。"
ms.assetid: 40d64242-b299-4cc5-ac6d-6b154c90d8b2
MSHAttr: PreferredLib:/library
title: "闪烁的图像到移动设备"
author: CelesteDG
ms.openlocfilehash: 2687fcdfd13aaa991df497db7f0ba98870fe79f2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="flash-an-image-to-a-mobile-device"></a>闪烁的图像到移动设备


闪烁是进入移动设备的移动图像的过程。 每个制造商都有不同的技术和工具，它们将用于制造和 Windows 移动设备提供服务，这意味着每个 OEM 需要用来确定哪些闪烁，制造工艺最适合它们。 有关详细信息，请参阅[闪烁工具](../mobile/flashing-tools.md)。

在本演练中，我们将使用 ffutool.exe，安装为 Windows ADK 的一部分，闪到移动设备的图像。 关于闪烁，并更多地了解您需要准备设备闪烁的详细信息，请参阅[的使用由 Microsoft 提供的闪烁的工具](https://msdn.microsoft.com/library/windows/hardware/dn789235)。

**快闪存储图像**

1.  引导至 FFU 闪灯模式连接到主机时的设备。

    如果没有包括 LABIMAGE 可选功能，生成测试映像时，可以强制 FFU 手动按下并松开电源按钮闪烁模式引导设备，然后立即按下并保持向上按钮卷到设备。 但是，请注意，此选项才可用 FFU 已经开始刷新到该设备。

2.  用管理员权限打开命令提示符。

3.  Ffutool.exe 从命令行运行以闪烁图像。

    **ffutool-闪存 TestFlash.ffu**

它将需要几分钟将完全刷新为设备的图像。 一旦完成闪烁，完成设备安装和验证您的自定义显示为图像的一部分。

 

 



