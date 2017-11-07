---
title: "构建和闪烁移动图像"
description: "下面是帮助您生成和 flash 图像到 10 Windows Mobile 设备的信息。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 4862b9a9-3619-45cd-a612-77bd4ebb6ca2
ms.openlocfilehash: 1540184993830ac40d42160252a8413454f9f497
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="building-and-flashing-mobile-images"></a>构建和闪烁移动图像


下面是帮助您生成和 flash 图像到 10 Windows Mobile 设备的信息。

## <a name="a-href-id1---define--customize--and-build-an-imagea1-define-customize-and-build-an-image"></a><a href="" id="1---define--customize--and-build-an-image"></a>1.定义、 自定义和生成图像


若要生成可以刷新到移动设备的自定义的映像，可以使用新的 Windows 映像和配置设计器 (ICD) 或经典的 ImgGen.cmd，或者使用 Windows ICD 命令行界面的这些方法中的混合体。 请参阅[Windows 10 移动的自定义项](https://msdn.microsoft.com/library/windows/hardware/mt481438)可帮助您确定哪种方法需要使用以满足自定义设备需要。

-   **使用 Windows ICD**︰ 此工具将引导您完成创建为使用 Windows 供应框架窗口 10 移动图像的过程。 如果您要构建一个基于 SoC 供应商参考设计的设备，请使用此工具。 若要了解有关此工具的详细信息，请参阅[Windows 图像处理和配置设计器](https://msdn.microsoft.com/library/windows/hardware/dn916113)。 若要开始生成移动图像，请参阅[生成使用 Windows ICD 的移动图像](build-a-mobile-image-using-windows-icd.md)。

-   **使用 ImgGen.cmd**︰ 如果您正在构建基于硬件设计的设备，或者使用 MCSF 自定义答案文件以及使用在 Windows Phone 8.1 售出的传统工具生成的其他资产，您可以生成自定义的移动图像，使用此工具。 若要开始，请参阅[构建使用 ImgGen.cmd 的移动图像](building-a-phone-image-using-imggencmd.md)。

-   **使用混合的方法**︰ 如果您想要使用 OEMInput.xml 文件来完全定义的图像的内容，利用所有新运行时设置、 企业策略和设置 Windows 中可用的注册设置也可以完全自定义的设备硬件和连接设置、 预加载应用程序，并添加资产，如铃声和本地化字符串通过 MCSF您可以使用 Windows ICD CLI 用于生成图像的混合方法。 若要了解详细信息，请参阅[生成使用混合方法的移动图像](build-a-mobile-image-using-windows-provisioning-and-mcsf-answer-files.md)。

## <a name="2-sign-an-image"></a>2.签名图像


无论哪种方法，用于自定义和构建您的映像，您需要加密签名图像之前可以将其部署到设备。

-   [签名的完整闪存更新 (FFU) 图像](sign-a-full-flash-update--ffu--image.md)

## <a name="3-flash-an-image-to-a-device"></a>3.闪存设备图像


使用以下主题中的信息了解闪烁和更新工具︰

-   [使用由 Microsoft 提供的闪烁工具](use-the-flashing-tools-provided-by-microsoft.md)

-   [更新设备上的程序包并获取包更新日志](update-packages-on-a-phone-and-get-package-update-logs.md)

-   [更新包。FFU 图像文件](update-packages-in-an-ffu-image-file.md)

 

 

[发送有关此主题的意见的评论](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_phFlashing\p_phFlashing%5D:%20Building%20and%20flashing%20mobile%20images%20%20RELEASE:%20%2810/4/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "发送有关此主题的意见的评论")




