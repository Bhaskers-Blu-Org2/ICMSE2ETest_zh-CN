---
author: kpacquer
Description: "Windows 10 IoT 核心 ADK 加载项包括工具可帮助您自定义和创建新的图像的设备应用程序、 板级支持包 (Bsp)、 驱动程序和 Windows 功能，选择，和可用于快速创建新的图像示例结构。"
ms.assetid: 26cfbad0-9528-4f89-a174-f198ece325d4
MSHAttr: PreferredLib:/library
title: "Windows ADK IoT 核心附件︰ 内容"
ms.openlocfilehash: e43176dccf0873db9c5a3e2e80fa6bb7df3a516c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-adk-iot-core-add-ons-contents"></a>Windows ADK IoT 核心附件︰ 内容

[Windows 10 IoT 核心 ADK 加载项](http://go.microsoft.com/fwlink/?LinkId=735028)包括 OEM 特定工具来创建图像的 IoT 核心设备应用程序、 板级支持包 (Bsp)、 设置、 驱动程序和功能。

[IoT 核心制造指南](iot-core-manufacturing-guide.md)将引导您完成构建映像，使用这些工具。

## <a name="span-idrootfolderspanroot-folder"></a><span id="Root_folder"></span>根文件夹

-   **IoTCoreShell**︰ 启动[IoT 核心外壳程序命令行](iot-core-adk-addons-command-line-options.md#iotcoreshell.cmd)。

-   **README.md**︰ 链接到文档的版本信息

## <a name="span-idbuildspanspan-idbuildspanspan-idbuildspanbuild"></a><span id="Build"></span><span id="build"></span><span id="BUILD"></span>生成
这是生成内容的存储位置的输出目录。 它开始为空。

## <a name="span-idcommonfilesspanspan-idcommonfilesspanspan-idcommonfilesspancommon-files"></a><span id="Common_files"></span><span id="common_files"></span><span id="COMMON_FILES"></span>公共文件

共有的所有体系结构的包的源代码文件。

-   **Custom.Cmd**︰ 包包括 oemcustomization cmd. 这是特定于产品的挑选产品目录中的输入文件。 这也是带有产品名称的注册表项。

-   **Device.SystemInformation**︰ 文件包，向映像中添加的系统产品名称和制造商的名称。

-   **DeviceLayout.GPT4GB**︰ 包与基于 UEFI 的设备的 GPT[驱动器/分区布局](device-layout.md)具有 4 GB 驱动器。

-   **DeviceLayout.GPT2GB**︰ 包与基于 UEFI 的设备的 GPT[驱动器/分区布局](device-layout.md)具有 2 GB 驱动器。

-   **DeviceLayout.MBR4GB**︰ 与传统的基于 BIOS 的设备的 MBR[驱动器/分区布局](device-layout.md)的包具有 4 GB 驱动器。

-   **DeviceLayout.MBR2GB**︰ 包与传统的基于 BIOS 的设备的 MBR[驱动器/分区布局](device-layout.md)具有 2 GB 驱动器。

-   **ImageSettings.CrashSettings**︰ 具有系统崩溃的设置软件包。 替换前一个包︰ Registry.CrashSettings。

-   **ImageSettings.VideoMode**︰ 具有向或无头视频模式设置软件包。

-   **OemTools.InstallTools**: C:\OEMApps 文件夹中找到的 OEM 应用程序将自动安装的包。

-   **Provisioning.Auto**︰ 用于[添加到图像设置包](add-a-provisioning-package-to-an-image.md)的包。 这是特定产品，拾取输入的 ppkg 文件中的产品目录。

-   **Provisioning.Manual**︰ 手动配置包。 这取决于 Custom.Cmd 触发的调配。

-   **Registry.Version**︰ 包中包含的产品和版本信息的注册表设置。

-   **Settings.HotKey**︰ 示例包来演示如何[添加注册表设置的图像](add-a-registry-setting-to-an-image.md)。 此设置将更改左的 Windows 键、 右 Windows 键，并按 Alt + 向 Windows 键作为 Home 键的值。

-   **OEMCommonFM.xml**: OEM 通用软件包的功能清单。


## <a name="span-idsourcespanspan-idsourcespanspan-idsourcespansource-source-arm-source-x64-source-x86"></a><span id="Source"></span><span id="source"></span><span id="SOURCE"></span>源 (源臂，源-x64 源-x86)
 
特定于体系结构的包的源代码文件。

### <a name="span-idbspspanspan-idbspspanbsp"></a><span id="BSP"></span><span id="bsp"></span>BSP
源代码文件，以创建板支持包 (Bsp)。 

一些 Bsp 为启动包含在每个文件夹中。 您可以[创建您自己的 Bsp](create-a-new-bsp.md)基于这些包。

### <a name="span-idpackagesspanspan-idpackagesspanspan-idpackagesspanpackages"></a><span id="Packages"></span><span id="packages"></span><span id="PACKAGES"></span>软件包

-   **Appx.Main**︰ 示例包 Appx 安装显示系统和网络的信息。 您可以[将其替换为您自己的应用程序](deploy-your-app-with-a-standard-board.md)。

-   **Drivers.GPIO**︰ 示例驱动程序的软件包。

-   **OEMFM.xml:**OEM 包的功能清单

-   **versioninfo.txt:**当前版本的版本号。 用于[更新 IoT 核心应用程序](../../service/iot/updating-iot-core-apps.md)。

### <a name="span-idproductsspanspan-idproductsspanspan-idproductsspanproducts"></a><span id="Products"></span><span id="products"></span><span id="PRODUCTS"></span>产品

产品配置的源文件。 使用我们的示例 (SampleA，SampleB，SampleC) 或[创建您自己](iot-core-manufacturing-guide.md)。

### <a name="span-idupdatesspanspan-idupdatesspanspan-idupdatesspanupdates"></a><span id="Updates"></span><span id="updates"></span><span id="UPDATES"></span>更新

[应用程序软件包更新](../../service/iot/updating-iot-core-apps.md)的源代码文件。 它使用两个示例启动︰ Update1 和更新 2。

-   **UpdateVersions.txt**︰ 到目前为止使用的版本编号的日志。

## <a name="span-idtemplatesspanspan-idtemplatesspanspan-idtemplatesspantools"></a><span id="Templates"></span><span id="templates"></span><span id="TEMPLATES"></span>工具

包括[IoT 核心加载项的命令行选项](iot-core-adk-addons-command-line-options.md)用于创建新的包和 Bsp 的模板。 

## <a name="span-idtoolsspanspan-idtoolsspanspan-idtoolsspantools"></a><span id="Tools"></span><span id="tools"></span><span id="TOOLS"></span>工具

包括[IoT 核心加载项的命令行选项](iot-core-adk-addons-command-line-options.md)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题

[IoT 核心制造指南](iot-core-manufacturing-guide.md)

[IoT 核心功能列表](iot-core-feature-list.md)


 

 



