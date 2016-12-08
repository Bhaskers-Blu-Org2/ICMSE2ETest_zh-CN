---
author: kpacquer
ms.assetid: a6243b16-54fd-4a3d-8901-4b15cebdaf40
MSHAttr: PreferredLib:/library
title: "获取自定义 Windows IoT 核心所需的工具"
ms.openlocfilehash: e5bdd1ed8fb9ce2e5c45100d76adb9378ff6a4c0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="get-the-tools-needed-to-customize-windows-iot-core"></a>获取自定义 Windows IoT 核心所需的工具


这里是您将需要创建 OEM 映像，使用 Windows 10 IoT 核心 （IoT 核心） ADK 加载项的软件︰

## <a name="span-idpcsanddevicesspanspan-idpcsanddevicesspanspan-idpcsanddevicesspanpcs-and-devices"></a><span id="PCs_and_devices"></span><span id="pcs_and_devices"></span><span id="PCS_AND_DEVICES"></span>Pc 和设备


以下是我们将引用它们︰

-   **技术人员计算机**︰ 计算机所做的工作。 这台电脑应该有至少 15 GB 可用空间为安装软件和修改 IoT 核心映像。

    我们建议使用最新的更新的 Windows 10 或 Windows 8.1。 最低要求是 Windows 7 SP1，尽管这可能需要其他工具或解决办法的任务，如装入。ISO 映像。

-   **IoT 设备**︰ 测试设备或表示单个模型行中的设备的所有的主板。

    对于我们的示例中，您将需要 MinnowBoard 最大或 Raspberry Pi 2。 若要查看更多选项，请参阅[设备选项](https://developer.microsoft.com/windows/iot/explore/deviceoptions)。

-   **HDMI 电缆**和**显示器或电视**具有输入专用 hdmi 接口。 我们将使用此验证加载图像和我们的示例应用程序正在运行。

## <a name="span-idstoragespanspan-idstoragespanspan-idstoragespanstorage"></a><span id="Storage"></span><span id="storage"></span><span id="STORAGE"></span>存储


-   一**微 SD 卡**。 （请注意，我们只需使用这对于我们的指南。 您可以建立与其他驱动器的设备。 学习现有[支持存储](https://developer.microsoft.com/windows/iot/docs/hardwarecompatlist#Storage)选项的详细信息。

    如果您的技术人员计算机不包含微 SD 插槽，您可能还需要一个适配器。

## <a name="span-idsoftwarespanspan-idsoftwarespanspan-idsoftwarespansoftware"></a><span id="Software"></span><span id="software"></span><span id="SOFTWARE"></span>软件

**在技术人员计算机上安装以下工具**

1.  [Windows 评估和部署工具包 (Windows ADK)](http://go.microsoft.com/fwlink/?LinkId=526803)包括至少**部署工具**和**图像处理和配置设计器 (ICD)**功能。 您将使用这些工具来创建图像和配置包。

2.  [Windows 驱动程序工具包 (WDK) 10](http://developer.microsoft.com/windows/hardware/windows-driver-kit)

3.  [IoT 核心.iso 包](https://www.microsoft.com/download/confirmation.aspx?id=53898)。 此.iso 包添加 IoT 核心包和用于创建图像的 IoT 核心功能清单。 您将需要使用您的 Microsoft 帐户进行登录。 默认情况下，这些软件包安装到**c:\\程序文件 (x86)\\窗口工具包\\10\\MSPackages\\零售**。

4.  [IoT 核心 ADK 加载项](https://github.com/ms-iot/iot-adk-addonkit/)。  单击**克隆或下载** > **下载 ZIP**，例如，将其提取到一个文件夹，并**c:\\IoT-ADK-AddonKit**。 此工具包中包括的示例脚本和基础结构，您将使用它来创建您的映像。 若要了解有关内容，请参见[在 Windows ADK IoT 核心加载项](iot-core-adk-addons.md)）。

5.  [Windows 10 IoT 核仪表板](http://go.microsoft.com/fwlink/p/?LinkId=708576)。

其他有用的软件︰

-   **文本编辑器，如记事本 + +**。 尽管对于某些文件，您不会看到换行，除非您打开每个文件为 utf-8 文件，还可以使用记事本工具。

-   **如 7-Zip 压缩程序**，它可以解压缩 Windows 应用程序程序包。

-   [Visual Studio 2015年](http://go.microsoft.com/fwlink/?LinkId=715695)，用来创建一个应用程序在[实验室 1b︰ 将应用程序添加到映像](deploy-your-app-with-a-standard-board.md)。

-   [IoT 核心 Pro.iso 包](https://www.microsoft.com/download/confirmation.aspx?id=53899)︰ 用于更改自动更新设置 (所述[实验室 1 d︰ 向映像中添加程序包设置](add-a-provisioning-package-to-an-image.md)。)

## <a name="span-idothersoftwarespanspan-idothersoftwarespanspan-idothersoftwarespanother-software"></a><span id="Other_software"></span><span id="other_software"></span><span id="OTHER_SOFTWARE"></span>其他软件


-   **为 IoT 核心构建的应用程序**。 我们的示例将使用[Hello、 世界 ！](https://developer.microsoft.com/windows/iot/samples/helloworld) 应用程序中，虽然您可以使用您自己。

-   **为 IoT 核心构建的驱动程序**。 我们的示例使用[Hello，Blinky](https://developer.microsoft.com/windows/iot/samples/helloblinky)驱动程序时，虽然您可以使用您自己。

## <a name="span-idnextstepsspanspan-idnextstepsspanspan-idnextstepsspannext-steps"></a><span id="Next_steps"></span><span id="next_steps"></span><span id="NEXT_STEPS"></span>下一步行动

[实验室 1a︰ 创建基本映像](create-a-basic-image.md)