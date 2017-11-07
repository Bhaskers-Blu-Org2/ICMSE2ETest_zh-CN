---
Description: "您需要登录移动图像之前可以将其部署到设备。"
ms.assetid: b5f9d31b-7293-4308-a761-c5cc87801e3c
MSHAttr: PreferredLib:/library
title: "签名的移动图像"
author: CelesteDG
ms.openlocfilehash: 3d21999b9074ea9f241e351b523b3ed637cd5c33
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="sign-a-mobile-image"></a>签名的移动图像


您需要登录移动图像之前可以将其部署到设备。 有关签名图像的详细信息，请参阅[注册全闪存更新 (FFU) 图像](https://msdn.microsoft.com/library/windows/hardware/dn789216)。

在开始之前，请确保您按照中的步骤*第 5 步︰ 安装 OEM 测试证书*[准备 Windows 移动开发](preparing-for-windows-mobile-development.md)中。 如果您还没有这样这样做此首先之前继续进行进行签名图像的步骤。

在本演练中，我们将重点讨论手动签名图像的测试。 除了 ImageSigner，我们也将使用 Sign.cmd。

**若要测试签名图像**

1.  打开具有管理员权限的目录中包含的输出图像生成过程的开发人员的提示。

2.  通过运行以下命令提取签字 FFU 文件的目录︰

    **ImageSigner GETCATALOG TestFlash.ffu TestFlash.cat**

3.  签名使用 /pk 选项的目录。 有两个部分对此步骤︰

    **设置登录\_OEM = 1**

    **Sign.cmd /pk TestFlash.cat**

4.  对 FFU 签名与签名的编录文件使用 ImageSigner。

    **ImageSigner 号 TestFlash.ffu TestFlash.cat**

一旦图像进行签名，您就可以闪到移动设备的图像。

 

 



