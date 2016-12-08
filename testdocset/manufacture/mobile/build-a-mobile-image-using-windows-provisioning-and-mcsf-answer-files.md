---
title: "生成使用混合方法的移动图像"
description: "您可以利用福利由 Windows 供应框架和 MCSF 提供通过使用混合方法来生成自定义移动图像。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 3A6BEF64-BCE1-4BF9-8A2F-14A79F956F7B
ms.openlocfilehash: ce35385fb79bb0d8cfa4a914721e5d9dfcf2be16
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="build-a-mobile-image-using-a-hybrid-method"></a>生成使用混合方法的移动图像


您可以利用福利由 Windows 供应框架和 MCSF 提供通过使用混合方法来生成自定义移动图像。 这意味着︰

-   可以使用[自定义应答文件](https://msdn.microsoft.com/library/windows/hardware/dn757452)MCSF 可完全自定义的设备硬件和连接设置、 预加载应用程序、 添加资产，如铃声和本地化的字符串和配置任何其他[不支持在 Windows 中提供的 MCSF 设置](https://msdn.microsoft.com/library/windows/hardware/mt573153)。

-   您可以使用[Windows 设置的答案文件](https://msdn.microsoft.com/library/windows/hardware/dn916153)来定义新运行时设置、 企业策略，注册设置并配置任何其他[Windows 资源调配中只支持移动设置](https://msdn.microsoft.com/library/windows/hardware/mt560342)。

-   可以使用 Windows 图像处理和配置设计器 (ICD) CLI 来构建您的映像。

    **请注意** 只有 Windows ICD CLI 允许您使用 MCSF 自定义答案文件和 Windows 设置的答案文件来创建一个自定义的移动图像。

     

## <a name="to-build-a-customized-mobile-image-using-a-hybrid-method"></a>若要生成使用混合方法的自定义移动图像


以下是您需要生成一个自定义的移动图像使用 Windows ICD CLI 的高级步骤︰

1.  选择如何定义程序包和图像中包含的功能。

    -   如果选择此方法，应作为 BSP 工具包的一部分已经有这样或者可以生成您自己使用的 SoC 供应商提供的配置工具，您可以使用 BSP.config.xml 文件的。

    -   您可以使用一个 OEMInput.xml 文件和 OEMDevicePlatform.xml 来定义您的平台。 若要执行此操作，请按照步骤 1-4 在高级别列表中[生成使用 ImgGen.cmd 的移动图像](building-a-phone-image-using-imggencmd.md)的步骤。

2.  创建答案文件来定义您想要配置为您图像的设置。

    -   创建一个 MCSF[自定义答案文件](https://msdn.microsoft.com/library/windows/hardware/dn757452)中 MCSF 框架的可自定义的任何自定义。 有关详细信息，请参阅*的自定义&lt;功能&gt;*[自定义使用移动的 MCSF 框架](https://msdn.microsoft.com/library/windows/hardware/dn757433)中的部分。

    -   创建一个[Windows 设置的答案文件](https://msdn.microsoft.com/library/windows/hardware/dn916153)来定义 Windows 供应框架中的任何可用的设置。 有关详细信息，请参阅[Windows 资源调配设置参考](https://msdn.microsoft.com/library/windows/hardware/dn953942)。

    如果您要添加两个答案文件中的 multivariant 设置，验证这两个答案文件中的 multivariant 规则是否一致。 请参阅的部分*目标、 TargetState、 条件和优先级*中[创建具有 multivariant 设置的自动配置软件包](https://msdn.microsoft.com/library/windows/hardware/dn916108)列表支持的条件，但一定要遵循应答文件指定您在应答文件中的**目标**时要创建架构。

    此外，还要确保没有重复这两个答案文件中的设置。 可以使用[Windows 资源调配设置映射到 MCSF](https://msdn.microsoft.com/library/windows/hardware/mt450421)来帮助您识别与每个框架相对应的设置。

3.  运行 Windows ICD CLI 生成图像。 有关详细信息，请参阅[生成 Windows 10 移动的图像](https://msdn.microsoft.com/library/windows/hardware/dn916115#to_build_a_mobile_image)。

4.  签名图像，以便可以将其刷新为设备。 有关详细信息，请参阅[注册全闪存更新 (FFU) 图像](sign-a-full-flash-update--ffu--image.md)。

## <a name="related-topics"></a>相关的主题


[构建和闪烁移动图像](building-and-flashing-images.md)

 

 

[发送有关此主题的意见的评论](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_phFlashing\p_phFlashing%5D:%20Build%20a%20mobile%20image%20using%20a%20hybrid%20method%20%20RELEASE:%20%2810/4/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "发送有关此主题的意见的评论")





