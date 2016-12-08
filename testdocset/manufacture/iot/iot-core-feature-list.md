---
author: kpacquer
Description: Here's the features you can add to Windows 10 IoT Core (IoT Core) images.
ms.assetid: cbae6949-ccfe-4015-a9b0-a269f6f30d5a
MSHAttr: PreferredLib:/library
title: "IoT 核心功能列表"
ms.openlocfilehash: ed12d251b3a4775483f9e1e1d65242ca12834efc
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="iot-core-feature-list"></a>IoT 核心功能列表

下面是您可以将其添加到 Windows 10 IoT 核心 （IoT 核心） 图像的功能。

添加使用 OEMInput XML 文件的功能。 若要了解详细信息，请参阅[IoT 核心制造指南](iot-core-manufacturing-guide.md)。

## <a name="span-idretailfeaturesdefinedbymicrosoftspanspan-idretailfeaturesdefinedbymicrosoftspanspan-idretailfeaturesdefinedbymicrosoftspanretail-features-defined-by-microsoft"></a><span id="Retail_features_defined_by_Microsoft"></span><span id="retail_features_defined_by_microsoft"></span><span id="RETAIL_FEATURES_DEFINED_BY_MICROSOFT"></span>由 Microsoft 零售功能

下表描述可以在**零售**生成的**OEMInput**文件中的功能元素中使用 oem Microsoft 定义的功能。

创建您的设备的图像时，决定哪些功能是必需的哪些功能是可选的。 

### <a name="span-idrequiredfeaturesspanrequired-features"></a><span id="Required_features"></span>所需的功能

以下功能必须包括在所有的图像，但可以自定义。

| 功能              | 说明                                                                                             |
|-----------------------|---------------------------------------------------------------------------------------------------------|
| **IOT\_应用程序\_工具包** | 添加 Appx 安装和管理所需的工具                                                |
| **IOT\_EFIESP**       | 启动使用 UEFI 的设备                                                                             |
| **IOT\_UAP\_OOBE**    | 包括收件箱 OOBE 应用程序在首次启动过程中以及安装过程中应用程序的启动 |

### <a name="span-idvisualstudiodebugtoolsspan-visual-studio-debug-tools"></a><span id="Visual_Studio_debug_tools"></span>Visual Studio 调试工具

| 功能                   | 说明                                                                                             |
|----------------------------|---------------------------------------------------------------------------------------------------------|
| **IOT\_CRT140**            | 添加 CRT 的二进制文件                                                                                       |
| **IOT\_DIRECTX\_工具**    | 添加 DirectX 工具                                                                                      |
| **IOT\_UMDFDBG\_设置** | 包括用户模式驱动程序框架调试设置                                                      |

### <a name="span-iddevelopertoolsspandeveloper-tools"></a><span id="Developer_tools"></span>开发人员工具

| 功能                   | 说明                                                                                                                 |
|----------------------------|-----------------------------------------------------------------------------------------------------------------------------|
| **IOT\_NETCMD**            | 添加命令行工具︰ net.exe，用于配置网络连接                                              |
| **IOT\_POWERSHELL**        | 添加 PowerShell                                                                                                             |
| **IOT\_SIREP**             | 使 TShell 连接的 SIREP 服务                                                                               |
| **IOT\_SSH**               | 使安全外壳协议 (SSH) 连接性                                                                                     |
| **IOT\_工具包**           | 包括开发工具，如︰ 内核调试组件、 FTP、 网络诊断、 基本设备门户和 XPerf。 这也解放的防火墙规则，并使不同的端口。  **请注意**我们建议不要在零售映像中包含此功能。                                                                                           |
| **IOT\_WEBB\_EXTN**        | 启用 IOTCore 特定扩展到 Windows 设备门户。 基本设备门户网站将包括在 IoT Toolkit。   |

### <a name="span-idappsspanapps-and-related-features"></a><span id="Apps"></span>应用程序和相关的功能
| 功能                        | 说明                                                                                                                 |
|---------------------------------|-----------------------------------------------------------------------------------------------------------------------------|
| **IOT\_ALLJOYN\_应用程序**           | 添加 AllJoyn 应用程序，用于无头 ZwaveAdapterAppx。 需要**IOT\_应用程序\_工具包**上首次启动安装此 appx。                             |
| **IOT\_BERTHA**                 | 示例应用程序中添加:"Bertha"。 此应用程序提供基本的版本信息和连接状态。  需要**IOT\_应用程序\_工具包**上首次启动安装此 appx。            |
| **IOT\_CP210x\_MAKERDRIVER**    | 添加 SiliconLabs USB 串行驱动程序                                                                                   |
| **IOT\_通用\_POP**             | 添加通用的操作系统只更新目标信息的设备。 Windows 10，1607年版本中的新增功能。                                |
| **IOT\_FTSER2K\_MAKERDRIVER**   | 添加 FTDI USB 串口驱动程序                                                                                          |
| **IOT\_NANORDPSERVER**          | 添加[远程显示软件包](https://developer.microsoft.com/windows/iot/docs/remotedisplay)。 Windows 10，1607年版本中的新增功能。                      |
| **IOT\_NETCMD**                 | 添加命令行工具︰ net.exe，用于配置网络连接                                              |
| **IOT\_外壳\_热键\_支持** | 添加支持启动默认应用程序使用热键︰ [VK_LWIN （左 Windows 键）](https://msdn.microsoft.com/library/windows/desktop/dd375731(v=vs.85).aspx)。 Windows 10，1607年版本中的新增功能。                                                    |  
| **IOT\_UAP\_DEFAULTAPP**        | 添加一个示例应用程序，"Chucky"。 此应用程序是类似于"Bertha"。  需要**IOT\_应用程序\_工具包**上首次启动安装此 appx。                             |
| **IOT\_统一\_编写\_筛选器** | 添加要保护的数据写操作的物理存储介质[统一编写筛选器 (UWF)](https://developer.microsoft.com/windows/iot/docs/uwf) 。 Windows 10，1607年版本中的新增功能。        |

### <a name="span-idspeechdataspanspeech-data"></a><span id="Speech_data"></span>语音数据

| 功能                       | 说明                                                                        |
|--------------------------------|------------------------------------------------------------------------------------|
| **IOT\_SPEECHDATA\_DE\_DE**    | 德语中添加语音数据                                                        |
| **IOT\_SPEECHDATA\_EN\_GB**    | 添加语音数据用来英国英语                                                    |
| **IOT\_SPEECHDATA\_EN\_美国**    | Windows 10，1607年版本中不建议使用。 不添加此功能。 默认的图像包含美国英语语音数据。 |
| **IOT\_SPEECHDATA\_ES\_ES**    | 将语音数据添加西班牙语                                                       |
| **IOT\_SPEECHDATA\_FR\_FR**    | 法语中添加语音数据                                                        |
| **IOT\_SPEECHDATA\_IT\_IT**    | 意大利语中添加语音数据                                                       |
| **IOT\_SPEECHDATA\_JA\_JP**    | 有日语的语音数据。 Windows 10，1607年版本中的新增功能                     |
| **IOT\_SPEECHDATA\_ZH\_CN**    | 将语音数据添加为中文 （中华人民共和国）                                                 |
| **IOT\_SPEECHDATA\_ZH\_香港**    | 将语音数据添加中文 （香港特别行政区）。 Windows 10，1607年版本中的新增功能   |
| **IOT\_SPEECHDATA\_ZH\_TW**    | 中文 （台湾） 添加语音数据。 Windows 10，1607年版本中的新增功能             |

### <a name="span-idfeatures-in-the-iot-core-add-onsspanfeatures-in-the-iot-core-add-ons"></a><span id="Features in the IoT Core Add-Ons"></span>IoT 核心加载项中的新功能


| 功能                  | 说明                                                          |
|---------------------------|----------------------------------------------------------------------|
| **IOT\_OEM\_CustomCmd**   | 添加脚本的支持添加 OEM 应用程序使用 ADK 加载项     |


## <a name="span-idtestfeaturesdefinedbymicrosoftspanspan-idtestfeaturesdefinedbymicrosoftspanspan-idtestfeaturesdefinedbymicrosoftspantest-features-defined-by-microsoft"></a><span id="Test_features_defined_by_Microsoft"></span><span id="test_features_defined_by_microsoft"></span><span id="TEST_FEATURES_DEFINED_BY_MICROSOFT"></span>定义由 Microsoft 的测试功能

下表描述可以在**测试**生成的**OEMInput**文件中的功能元素中使用 oem 的 Microsoft 定义测试功能。

| 功能                         | 说明                                                                                                               |
|----------------------------------|---------------------------------------------------------------------------------------------------------------------------|
| **IOT\_禁用\_TESTSIGNING**    | 禁用运行时安装测试签名的包                                                                     |
| **IOT\_禁用\_UMCI**           | 禁用代码完整性检查                                                                                         |
| **IOT\_EFIESP\_测试**            | UEFI 包所需的启动测试映像。 不应使用 IOT_EFIESP                                        |
| **IOT\_启用\_管理**           | Windows 10，1607年版本中的新增功能                                                                                           |
| **IOT\_启用\_TESTSIGNING**     | 允许运行时安装测试签名的软件包。 允许测试签名的驱动程序和 (.appx) 应用程序来运行                 |
| **IOT\_KD\_ON**                  | 启用内核调试程序                                                                                                   |
| **IOT\_KDNETUSB\_设置**      | 包括所有内核调试器传输并使 KDNET 可以通过 USB。 此功能的默认调试传输设置的 IP 地址为&quot;1.2.3.4&quot;，端口地址&quot;50000&quot;，并且调试器项的&quot;4.3.2.1&quot;。 若要使用默认 IP 地址为 1.2.3.4，运行 VirtEth.exe /autodebug 标志。  例如，若要建立一个内核调试器连接到电话，可使用命令︰`Windbg -k net:port=50000,key=4.3.2.1`  **注**不包括任何一个**IOT\_KDUSB\_设置**或**IOT\_KDNETUSB\_设置**如果您需要在图像中启用 USB 相比 MTP 或 IP。 在图像中启用了内核调试器和调试运输用来连接到该设备，如果内核调试器已独占使用 USB 端口并防止 MTP 和 IP 通过 USB 工作。   |
| **IOT\_KDSERIAL\_设置**      | 包括所有内核调试器传输和下面的设置启用 KDSERIAL︰ 为 115200 波特、 8 位、 无奇偶校验   |
| **IOT\_KDUSB\_设置**         | 包括所有内核调试器传输，使 KDUSB。 此功能的默认调试传输目标名称是**WOATARGET**。 要建立内核调试器连接到电话时，请使用命令︰ `Windbg -k usb:targetname=WOATARGET`。 **请注意**不包括任何**IOT_KDUSB_SETTINGS**或**IOT\_KDNETUSB\_设置**如果您需要在图像中启用 USB 相比 MTP 或 IP。 在图像中启用了内核调试器和调试运输用来连接到该设备，如果内核调试器已独占使用 USB 端口并防止 MTP 和 IP 通过 USB 工作。      |
| **IOT\_WDTF**                    | 包括 Windows 驱动程序测试框架 HLK 验证所需的组件                                        |

## <a name="span-iddevice-specificfeaturesspanspan-iddevice-specificfeaturesspanspan-iddevice-specificfeaturesspandevice-specific-features"></a><span id="Device-specific_features"></span><span id="device-specific_features"></span><span id="DEVICE-SPECIFIC_FEATURES"></span>设备特定的功能

某些功能所需的某些主板只 (Raspberry Pi 2 =**RPi2**，Qualcomm Dragonboard =**DB**，Minnowboard 最大 =**MBM**)。

| 功能                             | 说明                                                | 设备                                                               |
|--------------------------------------|------------------------------------------------------------|----------------------------------------------------------------------|
| **IOT\_DISABLEBASICDISPLAYFALLBACK** | 禁用收件箱基本呈现器驱动程序。                    | 此功能仅应使用与 Qualcomm DragonBoard (DB)。 |
| **IOT\_DMAP\_驱动程序**                | 添加 DMAP 的驱动程序。                                         | MBM 和 RPi2 所需。 不支持的数据库。                     |
| **IOT\_EFIESP\_BCD** |设置引导配置数据 (BCD) 基于 GPT 的驱动器。                    | MBM 的要求。                                                    |
| **IOT\_电源\_设置**             | 防止设备进入睡眠状态，由于处于非活动状态。 | MBM 和其他 x86/amd64 平台所需。 **请注意**该包的名称从 IOT 更改\_电源\_SETIINGS 1607 版本 Windows 10 中的。 |

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题

[什么是在 Windows ADK IoT 核心加载项](iot-core-adk-addons.md)

[IoT 核心制造指南](iot-core-manufacturing-guide.md)
