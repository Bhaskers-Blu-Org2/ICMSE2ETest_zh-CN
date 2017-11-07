---
author: kpacquer
Description: To get started, we'll create a basic Windows 10 IoT Core (IoT Core) image, flash it to a micro SD card, and put it into a device to make sure that everything's working properly.
ms.assetid: aeba79b8-d8dd-481a-a8bf-03ae28174632
MSHAttr: PreferredLib:/library
title: "实验室 1a︰ 创建基本映像"
ms.openlocfilehash: f26acb8d359127a29b1499f4b1f772faa4d36400
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="lab-1a-create-a-basic-image"></a>实验室 1a︰ 创建基本映像

若要开始，我们将创建一个基本的 Windows 10 IoT 核心 （IoT 核心） 映像、 闪存它微 SD 卡，并将其放入设备以确保一切都正常工作。

我们将创建产品文件夹表示我们的第一个设计。 我们第一个产品设计中，我们将自定义足够 IoT 核心设备，要启动并运行内置 OOBE app，我们应该能够看到 HDMI 兼容显示器上。

## <a name="span-idprerequisitesspanspan-idprerequisitesspanspan-idprerequisitesspanprerequisites"></a><span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>系统必备组件

请参阅[获取自定义 Windows IoT 核心所需的工具](set-up-your-pc-to-customize-iot-core.md)准备您的技术人员计算机。

## <a name="span-idcreateabasicimagespanspan-idcreateabasicimagespanspan-idcreateabasicimagespancreate-a-basic-image"></a><span id="Create_a_basic_image"></span><span id="create_a_basic_image"></span><span id="CREATE_A_BASIC_IMAGE"></span>创建一个基本映像

**设置您的 OEM 名称 (一次性仅)**

-   打开的文件**c:\\IoT-ADK-AddonKit\\工具\\setOEM.cmd**在记事本中，并与您的公司名称对其进行修改。 我们已经添加了此变量，以帮助您创建程序包具有易于区分开来从您正在使用其他制造商提供的名称。

    ``` syntax
    set OEM_NAME=Fabrikam
    ```

**启动 IoT 核心外壳程序，选择您的体系结构，并安装测试证书**

1.  在 Windows 资源管理器中，转到该文件夹中安装 IoT 核心 ADK 加载项，例如， **c:\\IoT-ADK-AddonKit**，并打开**IoTCoreShell.cmd**。 它应提示您以管理员身份运行。

    OEM 的新值\_启动工具时，应该显示名称。
    
    故障排除︰ 错误:"系统无法找到指定的路径"。 如果您收到此，右键单击该图标并修改到您已选择安装该工具的位置的"目标"中的路径。

2.  **设置环境的体系结构**系统提示时，请选择 ARM，x86，或 3 2 对于 x64，基于体系结构的主板，您将开发的 1。 例如，按**1**创建 Raspberry Pi 2 或第 3 Raspberry Pi 与兼容的图像或按**2**创建 Minnowboard 的最大值与兼容的图像。

    启动工具设置默认的体系结构，并设计，可用于将来的更新的版本号。 第一个版本编号默认为 10.0.0.0。

    （为何由四部分构成的版本号？ 了解版本化方案中[更新需求](../../service/mobile/update-requirements.md)。）

**一次性的任务**

这些任务只需完成首次安装 IoT ADK AddonKit。

1.  安装 OEM 测试证书。 您将使用这些对测试二进制文件进行签名。

    ``` syntax
    InstallOEMCerts
    ```
    这些证书添加到根。 若要了解详细信息，请参阅[设置签名的环境](https://msdn.microsoft.com/library/windows/hardware/dn756804)
    
2.  生成所有的工作文件夹中的文件包。

    ``` syntax
    BuildPkg All
    ```
        
### <a name="span-idcreateatestprojectspancreate-a-test-project"></a><span id="Create_a_test_project"></span>创建测试项目

1.  创建一个新的产品文件夹。 此文件夹表示我们想要建立，新的设备和包含示例自定义文件，我们可以使用它来开始我们的项目。

    ``` syntax
    newproduct ProductA
    ```

    这将创建文件夹︰ c:\\IoT-ADK-AddonKit\\源-&lt;弧&gt;\\产品\\ProductA。

### <a name="span-idbuildanimagespanbuild-an-image"></a><span id="Build_an_image"></span>生成图像

1.  弹出任何可移动存储驱动器，包括微 SD 卡和 USB 闪存驱动器。

2.  构建可更新测试映像使用的默认文件。 测试图像包含额外的工具，并且您可以创建测试图像，使用任何一个有符号或无符号的测试包。

    ``` syntax
    buildimage ProductA Test
    ```

    这生成 FFU 文件的基本映像在 c:\\IoT-ADK-AddonKit\\生成\\&lt;弧&gt;\\ProductA\\测试。

    故障排除︰
    
    -  错误代码︰ 0x80070005 或 0x800705b4: IoT 核心外壳以管理员身份重新打开，请拔下所有外部驱动器 （包括微 SD 卡和 USB 拇指驱动器），再试一次。  
    如果这不起作用，请返回[设置上您的 PC 和下载示例](set-up-your-pc-to-customize-iot-core.md)，请确保已安装的所有内容。

### <a name="span-idflashanimagespanflash-the-image-to-a-memory-card"></a><span id="Flash_an_image"></span>闪烁的图像到内存卡

1.  启动**Windows IoT 核仪表板**。

2.  您微 SD 卡插入您的技术人员计算机上，并在该工具中进行选择。

3.  在**安装新的设备**，选择设备类型︰**自定义**。

4.  从**闪存到 SD 卡预下载的文件 (Flash.ffu)**，单击**浏览**，浏览到您 FFU 文件 (c:\\IoT-ADK-AddonKit\\生成\\&lt;弧&gt;\\ProductA\\测试\\ProductA.ffu)，然后单击**下一步**。

5.  可选︰ 更改的默认设备名称 （默认值为 minwinpc）。 

6.  输入您的设备密码 (默认值是︰ p@ssw0rd)。

7.  接受许可条款，然后单击**安装**。 Windows IoT 核仪表板设置微 SD 卡，并安装新的图像。

### <a name="span-idtryitoutspantry-it-out"></a><span id="Try_it_out"></span>试一下

1.  连接到监视器使用 HDMI 线 Raspberry Pi 2，等您 IoT 设备。
    **请注意** 如果可能，请使用 HDMI 端口直接连接。 使用 DVI/VGA 适配器或集线器时，不会显示。

2.  放入微型 SD 卡的映像。

3.  打开电源。

    片刻时，该设备应自动启动，并且您应该会看到[默认 IoT 测试应用程序](https://developer.microsoft.com/windows/iot/samples/iotdefaultapp)(代码名称为"Bertha")，其中显示有关图像的基本信息。

    **请注意** 某些设备可能会极其缓慢启动首次启动时使用某些 8 GB 10 类 SD 卡。 较慢的启动时间可能会超过 15 分钟。 后续启动将受影响的卡上要快得多。

## <a name="span-idnextstepsspanspan-idnextstepsspanspan-idnextstepsspannext-steps"></a><span id="Next_steps"></span><span id="next_steps"></span><span id="NEXT_STEPS"></span>下一步行动

现在，在离开此设备，然后继续[实验室 1b︰ 将应用程序添加到映像](deploy-your-app-with-a-standard-board.md)。