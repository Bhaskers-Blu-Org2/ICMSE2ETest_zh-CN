---
title: "共享和协作"
description: "共享和协作"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: A75836F3-237B-4283-9948-08AB22966A7D
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 459110ebdcdc349084cd9c8a81882b4ef0e1d154
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="sharing-and-collaboration"></a>共享和协作


可以将打包以及相应的会话中，注释，zip 文件中的跟踪和 （可选） 加载符号使用 WPA。 这使您可以与其他开发人员共享此包并替换[WPA 会话](save-state-at-the-end-of-a-wpa-session.md)。 WPA 包 （"跟踪包） 捕获整个分析会话︰

-   跟踪
-   选项卡
-   图表配置
-   筛选器
-   注释
-   符号**说明**WPA 只打包符号如果它们加载;如果是这样，WPA 将它们嵌入包中。 WPA 不保留堆栈展开。

     

## <a name="benefits-of-sharing-a-trace-package"></a>共享跟踪包的好处


除了能够与其他开发人员共享跟踪包，跟踪包提供了几种其他好处︰

-   由于跟踪包压缩较少空间
-   支持并能够在 WPA 打开压缩向上跟踪文件
-   打开跟踪包多次而无需多次提取相同的跟踪能力
-   插件的验证，并警告如果插件不存在 WPA 打开跟踪包时。

**请注意** 这个过程迅速向上跟踪包中。 如果您跟踪出现的问题和包含敏感材料，向我们发送以进行进一步的调查，确保保护任何敏感的资料，就像任何跟踪。 由于压缩，包可能有文件大小较小与跟踪;这并不意味着 zipping 进程中删除的任何敏感信息。

 

## <a name="sharing-a-trace-package"></a>共享跟踪包


若要创建一个配置文件，请首先为您希望其出现，然后执行下列配置视图布局︰

1.  在菜单上，选择**文件**，然后**导出包**。 另存为对话框将打开。

2.  导航到所需位置。

3.  导出包命名，请确保保存作为类型读取**WPA 包 (\*.wpapk)**，然后单击**保存**。 Wpapk 进度栏会显示指示打包过程。 您可以关闭窗口，如过程将继续运行在后台，直到完成。

## <a name="related-topics"></a>相关的主题


[WPA 常见方案](windows-performance-analyzer-common-scenarios.md)

 

 







