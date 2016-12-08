---
author: kpacquer
Description: "测试 IoT 设备上的一个 appx 文件。"
ms.assetid: ae043bb0-656e-4439-bdbe-a8d370629ab7
MSHAttr: PreferredLib:/library
title: "测试 IoT 设备上的 appx 文件"
ms.openlocfilehash: 103dec18becb969dcf16705c701bc33cb5d2c5e8
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="span-idtestanappxfileonaniotdevicespantest-an-appx-file-on-an-iot-device"></a><span id="TEST_AN_APPX_FILE_ON_AN_IOT_DEVICE"></span>测试 IoT 设备上的 appx 文件

从另一台 PC * * 连接到设备

1.  将网络电缆连接。

2.  请注意显示在设备的 IP 地址。

3.  在技术人员计算机，打开 Internet Explorer，然后键入以 http:// 前缀的地址和︰ 8080 后缀︰

    ``` syntax
    http://100.100.0.100:8080
    ```

    这将打开[Windows 设备门户](https://developer.microsoft.com/windows/iot/docs/deviceportal)。 从这里，您可以上载应用程序软件包，查看安装了哪些应用程序，并在它们之间切换。

4.  如果您已经在您的程序包中添加 IOT_ENABLE_ADMIN 功能，使用登录Administrator/p@ssw0rd.如果您创建了一个自定义的用户名和密码，使用的现在。 若要了解详细信息，请参阅[实验室 1b︰ 将应用程序添加到映像](deploy-your-app-with-a-standard-board.md)。

通过安装 it * * 测试应用程序

1.  单击**应用程序**。

2.  在**安装应用程序**，**应用程序软件包**, 下单击**浏览**并选择您的.appx 文件。
    **请注意** 如果生成您的应用程序作为一个包，您可能需要使用等 7-Zip 工具从包中提取这些文件。

3.  将您的应用程序**证书**添加相同的方式。

4.  单击**添加依赖项**，然后添加每个应用程序的依赖项文件。

5.  在**部署**中，单击**定位**。 应用程序安装。

6.  在**已安装的应用程序**，单击下拉列表框中，选择您的应用程序。 您的应用程序应在设备上启动。

不错，您的应用程序的工作方式 ！ 现在让我们将其打包以便可以保持您的应用程序，即使已交付给客户。
