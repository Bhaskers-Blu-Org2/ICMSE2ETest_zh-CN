---
title: "什么是新的 Windows ADK 和 ADK 工具中"
description: "什么是新在 Windows ADK 和 ADK 工具"
Search.SourceType: Video
ms.assetid: EE27ABF7-C197-4E8E-AC1B-77266E2B9FD9
ms.openlocfilehash: 6e407e97f48b2a4ff15d86f8684943598e922f0c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="whats-new-in-adk-kits-and-tools"></a>在 ADK 工具包和工具中的新增功能

## <a name="a-href-idadkawhats-new-in-the-the-windows-adk-for-windows-10-version-1607"></a><a href="" id="adk"></a>什么是新 Windows ADK 的 Windows 10 版本 1607年

### <a name="pick-and-choose-desktop-applications"></a>选择桌面应用程序

与[各自为政调配程序包](manufacture/desktop/siloed-provisioning-packages.md)，您可以立即挑选哪个桌面的应用程序在部署过程中将添加到您的图像。 您不再需要重新捕获到恢复图像的应用程序的整个一套，它们是在自动添加。 这些产品包支持如 OS 压缩和单实例存储节省空间的功能。 

### <a name="build-iot-core-images-for-large-scale-deployment"></a>大规模部署的映像构建 IoT 核心

捕获您的应用程序、 驱动程序和设置，并将它们部署到安全新设备。 学习如何与[IoT 核心制造指南](manufacture/iot/iot-core-manufacturing-guide.md)。

### <a name="the-chinese-hong-kong-sar-language-pack-zh-hk-is-no-longer-used"></a>不再使用中文 （香港特别行政区） 语言包 （中文-香港）。

中文 （台湾） 语言包 (ZH-TW) 支持台湾和中国香港地区。 有关详细信息，请参阅可用语言包的 Windows。

### <a name="you-can-limit-access-to-a-single-windows-app-assigned-accesshttpsmsdnmicrosoftcomlibrarywindowshardwaremt620043"></a>您可以限制访问单个 Windows 应用程序 （分配访问权限）] (https://msdn.microsoft.com/library/windows/hardware/mt620043)

### <a name="new-answer-file-settings-added"></a>添加新的答案文件设置

-  将多个拼贴添加到开始菜单上︰ [Microsoft Windows 外壳程序安装 |StartTiles |SquareTiles |SquareTiles |SquareOrDesktopTile7](https://msdn.microsoft.com/library/windows/hardware/dn915881)至[SquareOrDesktopTile12](https://msdn.microsoft.com/library/windows/hardware/dn915868)

-  添加[高级的笔设置应用程序](https://msdn.microsoft.com/library/windows/hardware/mt757353)

-  允许[远程访问会话中的聊天窗口](https://msdn.microsoft.com/library/windows/hardware/mt752384)

-  设置[自动亮度控制](https://msdn.microsoft.com/library/windows/hardware/dn757391)

-  请参阅更多[新的答案文件设置](https://msdn.microsoft.com/library/windows/hardware/mt750416.aspx)

### <a name="mdm-enhanced-device-and-pc-management"></a>MDM︰ 增强的设备和 PC 管理

签出[新 Csp 设置](https://msdn.microsoft.com/en-us/library/windows/hardware/mt299056(v=vs.85).aspx#whatsnew_1607)。

### <a name="more-changes"></a>更多的更改

请参见什么是新[设计](https://msdn.microsoft.com/library/windows/hardware/mt703371.aspx)、[自定义](https://msdn.microsoft.com/en-us/library/windows/hardware/mt723363(v=vs.85).aspx)、[制造](manufacture/whats-new-in-windows-manufacturing.md)。

## <a name="a-href-idadkawhats-new-in-the-windows-adk-version-1511"></a><a href="" id="adk"></a>什么是 Windows ADK，1511年版本中的新增功能

Windows ADK 现在包括[Windows 图像处理和配置设计器](https://msdn.microsoft.com/library/windows/hardware/dn916113.aspx)[窗口评估 Toolkit](test/assessments/index.md)、 [Windows 性能 Toolkit](test/wpt/index.md)，和几个新的和改进的部署工具，可以帮助您自动执行 Windows 10 大规模部署。

### <a name="windows-imaging-and-configuration-designer-icd"></a>Windows 图像处理和配置设计器 (ICD)

-   快速创建可用于自定义设备，而无需重新映像配置包。
-   生成针对特定的市场领域和区域的自定义的 Windows 10 映像。

有关详细信息，请参阅[Windows ICD 入门](https://msdn.microsoft.com/library/windows/hardware/dn916112.aspx)。

### <a name="push-button-reset-incorporates-system-updates-by-default"></a>依靠以点击方式重置默认情况下包含系统更新

现在，用户可以刷新，或将其计算机还原到系统文件，您不需要分别重新安装每个更新的更新版本。

### <a name="partial-language-packs-now-available"></a>现已推出的部分语言包

要添加的用户更多语言，当他们打开他们的设备？ 添加完整语言包，而不是通过添加只是基本的用户界面语言的文件来节省空间。 稍后，如果您的用户需要手写或语音识别功能，Windows 可以根据需要下载它们。

有关详细信息，请参阅[语言包 (lp.cab)](manufacture/desktop/language-packs-and-windows-deployment.md)。

### <a name="new-package-type-capabilities"></a>新的包类型︰ 功能

这个新的 Windows 程序包类型允许您请求服务，如 Microsoft.NET 或语言而不指定版本。 使用 DISM 工具来搜索多个源如 Windows 更新或您公司的服务器来查找并安装最新版本。

### <a name="save-space-by-running-windows-from-compressed-os-files"></a>通过运行 Windows 操作系统的压缩文件来节省空间

您现在可以直接从压缩文件运行 Windows。 这是类似于 WIMBoot，在 Windows 8.1 更新 1 中引入的。 这新的过程而不是静态的 WIM 文件使用单独的文件。 当更新系统文件，Windows 现在将替换旧文件而不是令这两个副本。


## <a name="related-topics"></a>相关的主题

- [工具包和工具概述](kits-and-tools-overview.md)

- [什么是驱动程序开发中的新功能](https://msdn.microsoft.com/windows/hardware/drivers/what-s-new-in-driver-development)

- [Windows 性能 Toolkit 的新增功能](https://msdn.microsoft.com/en-us/library/windows/hardware/dn927303(v=vs.85).aspx)

- [什么是硬件实验室工具包中的新功能](https://msdn.microsoft.com/library/windows/hardware/mt187880.aspx)
 

[发送有关此主题的意见的评论](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_getstarted\p_getstarted%5D:%20What's%20new%20in%20kits%20and%20tools%20%20RELEASE:%20%286/15/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "发送有关此主题的意见的评论")





