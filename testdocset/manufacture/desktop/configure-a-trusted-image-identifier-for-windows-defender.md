---
author: Justinha
Description: "为 Windows Defender 配置受信任的图像标识符"
ms.assetid: b55f681f-94d7-4800-a927-ec186dc046e2
MSHAttr: PreferredLib:/library/windows/hardware
title: "为 Windows Defender 配置受信任的图像标识符"
ms.openlocfilehash: a8ef10dd1aff55c4243c85677aa18a9f62f77bb2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="configure-a-trusted-image-identifier-for-windows-defender"></a>为 Windows Defender 配置受信任的图像标识符


您可以通过将受信任的图像标识符添加到 Windows® Defender 加快最终用户计算机的初始性能。 Windows Defender 是 Microsoft® 应用程序可以帮助阻止、 删除和隔离恶意软件和间谍软件。

默认情况下，Windows Defender 计算机第一次访问文件时执行的每个计算机上的文件进行扫描。 这就是按访问扫描。 优化机制，例如高速缓存，可帮助减少不必要的已扫描的文件的扫描。 当 Windows Defender 执行快速扫描或完全扫描 （又称为按需扫描） 时，系统上的文件的其余部分将被标记为安全。

**请注意**  
如果已经部署了一系列计算机，后来又确定，没有图像的安全可能会出现问题，请联系在 Windows 生态系统合作小组内您深度项目经理 (PM)。 并提供图像的唯一标识符。 Microsoft 会将此唯一标识符添加到 Windows 更新。 具有此唯一标识符的计算机接收从 Windows Update 更新之后，Windows Defender 对所有在该计算机上的文件执行扫描。

 

## <a name="span-idaddingatrustedimageidentifierspanspan-idaddingatrustedimageidentifierspanspan-idaddingatrustedimageidentifierspanadding-a-trusted-image-identifier"></a><span id="Adding_a_Trusted_Image_Identifier"></span><span id="adding_a_trusted_image_identifier"></span><span id="ADDING_A_TRUSTED_IMAGE_IDENTIFIER"></span>添加受信任的图像标识符


为获得最佳性能，我们建议将此设置添加后执行完全扫描最终图像的最终部署，准备计算机时。

**若要添加受信任的图像标识符**

1.  创建要使用 Sysprep，答案文件并添加安全-恶意软件-Windows-Defender\\ `TrustedImageIdentifier`设置。 有关详细信息，请参阅[使用答案文件与 Sysprep](use-answer-files-with-sysprep.md)。

2.  值的`TrustedImageIdentifier`设置，指定一个唯一的标识符，如图像的 GUID。

3.  在参考计算机上安装 Windows 并执行[Sysprep （系统准备） 概述](sysprep--system-preparation--overview.md)主题的"常见 Sysprep 情况"部分所述的所有更新。

4.  使用 Windows Defender 或其他扫描工具执行扫描的图像。 这可以帮助确保该图像是安全。

5.  当您最后一次运行 Sysprep 时，使用 Sysprep 命令和 /oobe 和 /unattend 选项，如下所示︰

    ``` syntax
    Sysprep /oobe /shutdown /unattend:Unattend.xml
    ```

6.  执行其他脱机任务，例如，脱机映像的维护。 捕获并将映像应用到其他计算机，然后将计算机交付给客户。

    下次计算机启动时，Windows 标识的所有文件当前在系统上，并在以后的扫描过程中跳过这些文件。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Sysprep 过程概述](sysprep-process-overview.md)

[使用答案文件与 Sysprep 一起](use-answer-files-with-sysprep.md#bkmk_1)

 

 






