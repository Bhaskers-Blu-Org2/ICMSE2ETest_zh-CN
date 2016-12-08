---
title: "生成使用 Windows ICD 的移动图像"
description: "如果您要构建一个基于 SoC 供应商参考设计的设备，或正在寻找简单而优化的过程来创建移动图像，请使用 Windows ICD。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 9F7346F3-688F-4DB7-B535-1A4A86DEB3B4
ms.openlocfilehash: 26adf46bc8fdf725ccb092c007dbd6161b9c3695
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="build-a-mobile-image-using-windows-icd"></a>生成使用 Windows ICD 的移动图像


Windows 图像处理和配置设计器 (ICD) 是一个 Windows 资源调配工具，可以简化自定义和提供的 Windows 映像。 它提供了一个 GUI 或命令行界面，您可以使用︰

-   配置设置和策略对于移动的图像，包括主要专注于企业和特定教育的方案，如大量登记和企业策略的新自定义项，然后生成的自定义的图像。
-   通过创建定义目标并添加时将应用设置 variant 类型值，指定的条件自动配置包并使用资源调配包作为构建移动图像的输入创建的 multivariant 图像。

如果您要构建一个基于 SoC 供应商参考设计的设备，或正在寻找简单而优化的过程来创建移动图像，请使用 Windows ICD。

## <a name="to-build-a-mobile-image-using-the-windows-icd-ui"></a>若要生成使用 Windows ICD 用户界面的移动图像


ICD Windows 用户界面 (UI) 提供了易于使用的界面生成自定义移动图像。 用户界面显示的所有设置，您可以配置为单个的 variant 类型的值移动图像，然后引导您完成一个分步过程，生成，并甚至闪存的自定义的图像。

但是，请注意 Windows 供应框架通过一些设置，这些都没有可供配置使用 Windows ICD。 这包括[在 Windows 设置中不支持 MCSF 设置](https://msdn.microsoft.com/library/windows/hardware/mt573153)以及数据资产 （如铃声、 已本地化的字符串，等等） 的支持。

如果您不需要配置这些设置或资产以实现您的映像，可以使用 Windows ICD UI 按照中的说明生成自定义的一个变体移动图像[生成和部署映像的 Windows 10 Mobile](https://msdn.microsoft.com/library/windows/hardware/dn916106)。

## <a name="to-build-a-mobile-image-using-the-windows-icd-cli"></a>若要生成使用 Windows ICD CLI 的移动图像


如果您想要将可用手机设置配置 Windows 供应框架中，但希望更灵活地构建映像，可以使用 Windows ICD 命令行界面 (CLI)。 使用 Windows ICD CLI，您可以︰

-   选择如何定义程序包和图像中包含的功能 — — 通过使用 OEMInput.xml 文件或 BSP.config.xml 文件作为输入。
-   构建一个 variant 类型的值移动图像。
-   使用 multivariant 的设置，可用于创建 multivariant 的移动图像用作输入之一创建配置包。

无论您构建 multivariant 或一个 variant 类型的值的图像，必须选择您希望定义的图像内容的方式。 这决定了包或功能，将图像的一部分，并且可以包括硬件支持，语言、 市场特定应用程序或功能，等等。

**定义图像的内容**

1.  **使用 BSP.config.xml 文件**。 您可以下载这些作为 BSP 工具包的一部分或从 SoC 供应商运行 BSP 包配置工具并选择驱动程序组件可以生成您自己的 BSP.config.xml 文件。

    BSP.config.xml 文件是必需的如果您尝试过或者想要使用 Windows ICD 用户界面来构建您的映像。 如果您要构建硬件参考设计的移动图像，您应该已经 BSP.config.xml 文件为您的硬件参考设计。

2.  **使用 OEMInput.xml 文件**。 OEMInput.xml 文件介绍了用于定义移动图像的必选和可选元素。 如果您创建移动图像硬件参考设计或您自己的硬件设计，并且还想要作为映像的一部分添加自己的功能，OEMInput.xml 文件允许您执行此操作。

    移动套件包括可用作起始点的 OEMInput.xml 示例。 您可以找到这些 Windows 安装文件夹，c:\\程序文件 (x86)\\窗口工具包\\10\\OEMInputSamples 在 x64 上的主机计算机或 c:\\程序文件\\窗口工具包\\10\\OEMInputSamples 在 x86 主机计算机。

    若要了解有关 OEMInput 目录和其他功能，您可以将其添加到您的映像的详细信息，请参阅[构建映像的可选功能](optional-features-for-building-images.md)和[OEMInput 文件的内容](oeminput-file-contents.md)。 如果您已经熟悉 OEMInput.xml 并且想要了解如何将您自己的功能到图像和其他可用的功能添加到您，请参阅下[定义图像使用 OEMInput 和功能清单文件](define-the-image-using-oeminput-and-feature-manifest-files.md)的其他主题。

若要生成移动的图像，还必须具有资源调配的包或 Windows 提供的应答文件用作输入。 这些文件指定的自定义设置和您想要在您的映像中包括的资产。

-   Windows ICD 用户界面可用于生成配置设置，然后导出设置包配置包。

-   可以使用 Windows ICD 用户界面来快速生成一个 Windows 提供的应答文件。 每当您启动一个新项目，使用用户界面，Windows ICD 总是会 customizations.xml 创建项目文件夹中。 这通常在文档中找到\\Windows 图像处理和配置设计器 (WICD)\\*项目\_名称*文件夹。 如果您想要创建一个从零开始，请参阅[Windows 设置的答案文件](https://msdn.microsoft.com/library/windows/hardware/dn916153)来了解架构，然后查看[Windows 资源调配设置参考](https://msdn.microsoft.com/library/windows/hardware/dn953942)以了解有关可用于您配置的设置。

    **请注意** 我们建议使用 Windows ICD 用户界面方便地生成供应包或 Windows 提供的答案文件。

     

按照这些说明来生成一个 variant 类型的值移动图像︰

**生成一个 variant 类型的值移动图像**

1.  请参阅[Windows ICD 入门](https://msdn.microsoft.com/library/windows/hardware/dn916112)和按照上启动 Windows ICD CLI 的说明。

2.  使用 Windows ICD CLI 后[生成 Windows 10 移动的图像](https://msdn.microsoft.com/library/windows/hardware/dn916115#to_build_a_mobile_image)。

Windows 支持允许您创建单个图像，它可以对多个市场起作用的机制。 您可以动态地配置语言、 商标、 应用程序和基于条件设置。 构建包含 multivariant 设置的移动图像，才可以通过 Windows ICD CLI。

构建一个 multivariant 的移动图像的过程是类似于构建一个 variant 类型的值移动图像，不同之处在于，您必须创建一个资源调配包 multivariant 设置第一个，然后必须使用此包作为一个输入时您就可以生成图像。

按照这些说明来生成 multivariant 的移动图像︰

**生成的 multivariant 移动图像**

1.  创建配置包。 有关详细信息，请参阅[创建具有 multivariant 设置的自动配置软件包](https://msdn.microsoft.com/library/windows/hardware/dn916108)。

    下一步，将作为一个输入使用此程序包。

2.  使用 Windows ICD CLI 后[生成 Windows 10 移动的图像](https://msdn.microsoft.com/library/windows/hardware/dn916115#to_build_a_mobile_image)。

## <a name="related-topics"></a>相关的主题


[构建和闪烁移动图像](building-and-flashing-images.md)

[生成使用混合方法的移动图像](build-a-mobile-image-using-windows-provisioning-and-mcsf-answer-files.md)

 

 

[发送有关此主题的意见的评论](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_phFlashing\p_phFlashing%5D:%20Build%20a%20mobile%20image%20using%20Windows%20ICD%20%20RELEASE:%20%2810/4/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "发送有关此主题的意见的评论")





