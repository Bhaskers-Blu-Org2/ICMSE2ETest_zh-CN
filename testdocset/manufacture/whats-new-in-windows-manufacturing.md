---
author: kpacquer
Description: "Windows 10 IoT 核心 （IoT 核心） 是专为较小的设备，带或不带显示器的 Windows 10 份。 IoT 核心可用于丰富、 可扩展通用 Windows 平台 (UWP) API 构建优秀的解决方案。"
MSHAttr: PreferredLib:/library
title: "什么是 IoT 核心制造中的新功能"
ms.openlocfilehash: cb3f0ca7a1f07e84a72583847f0fc68fb1d1d1e5
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="whats-new-in-windows-manufacturing"></a>Windows 制造中的新增功能

本主题包括桌面、 移动设备、 和 IoT 制造新的改进。 

## <a name="span-idwhatsnewindesktopmanufacturingspanwhats-new-in-desktop-manufacturing"></a><span id="Whats_new_in_desktop_Manufacturing"></span>什么是桌面制造中的新功能 

**2016 年 11 月 17日，**

[将语言包添加到 Windows](desktop/add-language-packs-to-windows.md)︰ 添加零售演示体验 (Microsoft-Windows-RetailDemo-OfflineContent-Content-fr-fr-Package) 的即需即装功能的列表。

**2016 年 11 月 11日，**

服务堆栈更新 (SSU): 应用最新的常规分发版本 （GDR） 当前 KB 3200970 或任何未来的 Gdr 之前，需要 KB3199209。

若要更新安装最新的更新︰ 

-  下载[SSU:KB3199209](http://www.catalog.update.microsoft.com/Search.aspx?q=KB3199209)和[最新的 GDR](https://support.microsoft.com/en-us/help/12387/windows-10-update-history) (当前[KB 3200970](http://www.catalog.update.microsoft.com/Search.aspx?q=3200970))，从[Microsoft 更新目录](http://www.catalog.update.microsoft.com)。

-  应用此 SSU，，然后将最新的 GDR，应用到 Windows 和 WinRE。

-  运行 DISM /Cleanup-Image /Resetbase。  任何累积更新之后，建议采用该步骤，在这种情况下，需要确保所做的更改实际上保持后用户将其 PC 重置回 OOBE。

   若要了解有关应用更新的详细信息，请参阅[实验室 4︰ 添加更新和升级版本](desktop/servicing-the-image-with-windows-updates-sxs.md)和[实验室 10︰ 更新恢复映像](desktop/update-the-recovery-image.md)。

SSU:KB3199209 解决两个问题︰
 
1.  故障注入到 winre.wim – Gdr 时这需要注入到 winre.wim 的 SSU

2.  依靠以点击方式重置失败使 OEM 预安装 Gdr:

    1.  此修复程序的一半需要注入到 Windows 映像的 SSU︰ 此部件允许 Gdr 标记作为永久使用 /ResetBase PBR 后出现。 

    2.  此修复程序的另一半需要注入 GDR 到 WinRE.wim。

**2016 年 9 月 30日，**

-  建议的分区大小为 Windows RE 分区为 450 MB 收缩从 500 MB。 自己 Windows RE 分区大小可能会有所不同，根据外接程序[启动关键驱动程序和语言](desktop/add-drivers-langs-universal-apps-sxs.md)等。 

-  新的主题︰[优化 Windows PE](desktop/winpe-optimize.md)可以帮助引导 Windows PE 更快地添加语言或启动关键驱动程序的自定义项之后。

**2016 年 9 月 20日，**

-  若要部署单个 Windows 桌面应用程序，使用[Siloed 调配包 (Spp)](desktop/siloed-provisioning-packages.md)。 若要执行此操作，您需要从 Windows ADK，不是从 Windows 或 Windows PE 的内置版本运行 DISM 版本。 DISM 安装程序中，应从非可移动驱动器运行 WimMountADKSetup(x86/amd64).exe。 有关的演练，请参见[实验室 1f︰ 与各自为政的供应包添加 Windows 桌面应用程序](desktop/add-desktop-apps-wth-spps-sxs.md)。 要获得命令行帮助，请使用**C:\ADKTools\DISM /Apply-SiloedPackage /？**。

**2016 年 9 月 6日，**

-  [即需即装功能](https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/features-on-demand-v2--capabilities)︰ 我们已经添加了[所有可用的语言功能](http://download.microsoft.com/download/8/3/0/830AC3A9-68CF-4F10-9357-F27E0A03148A/Windows%2010%201607%20FOD%20to%20LP%20Mapping%20Table.xlsx)的列表。

**2016 年 9 月 2日，**

-  更新[按钮重置](desktop/push-button-reset-overview.md)，请添加 Windows 10 版本 1607年功能变化有关的详细信息。  

**2016 年 9 月 1日，**

-  在 Windows 10 版本 1607年语言包的 Windows ADK 应该不用于 WinRE。 相反，使用 ISO 语言包中可用的语言包。

**2016 年 8 月 25日日，**

-  在第 10 Windows 版本 1607年是不再需要添加语言包时，请删除收件箱的应用程序。 如果要删除的应用程序，DISM 命令可能会失败。 
   已更新的主题︰ 
   -  [将语言包添加到 Windows](desktop/add-language-packs-to-windows.md)
   -  [实验室 1 d︰ 启动关键驱动程序、 语言和通用的 Windows 应用程序中添加](desktop/add-drivers-langs-universal-apps-sxs.md)。
   -  [桌面版本的 Windows 10 的 OEM 部署](desktop/oem-deployment-of-windows-10-for-desktop-editions.md)

**2016 年 8 月 15日，**

-  在第 10 Windows 版本 1607年基本恢复 (WinRE) 图像，包括新的可选组件︰ WinPE WiFi 包。 您不需要更改任何您的脚本;此程序包不是特定于语言的不需要添加或删除时更改可用的语言。

**2016 年 8 月 4日，**

-  桌面应用程序、 驱动程序和设置在审核模式下添加需要以便通过点击式恢复工具恢复分别捕获。 若要了解详细信息，请参阅[实验室 1 g︰ 在审核模式下更改](desktop/prepare-a-snapshot-of-the-pc-generalize-and-capture-windows-images-blue-sxs.md)。

-  自动配置的桌面应用程序、 驱动程序和设置添加从各自为政的供应包 (Spp)。 

**2016 年 7 月 26日，**

-  新的示例脚本︰ [WinPE︰ 使用脚本确定驱动器号](desktop/winpe-identify-drive-letters.md)

**2016 年 7 月 21日，**

第 10 Windows 版本 1607年熟悉以下更改︰

- Sysprep 支持准备从以前版本的 Windows 10 已升级的映像。 有关详细信息，请参阅[Sysprep 概述](desktop/sysprep--system-preparation--overview.md)。

- 各自为政的供应包是一种新型的可以分别捕获经典 Windows 应用程序的包、 驱动程序以及应用程序和资源调配。 他们为制造过程提供更大的灵活性，并帮助减少生成运行 Windows 的计算机出厂时间。 ScanState.exe 和 Dism.exe 是两者都提高了捕获和应用变得分散化提供包，分别。 

- 已重命名文件的语言包和语言界面包的名称。 新文件的名称的示例，请参阅[语言包](desktop/language-packs-and-windows-deployment.md)。

- 不再使用中文 （香港特别行政区） 语言包 （中文-香港）。 中文 （台湾） 语言包 (ZH-TW) 支持台湾和中国香港地区。 有关详细信息，请参阅[可用语言包的 Windows](desktop/available-language-packs-for-windows.md)。

- 语言包的 WinPE 和 WinRE 已移动到 DVD 的语言包。 Oem 和系统构建者与 Microsoft 软件许可条款如果可以则可从[Microsoft OEM 网站](http://go.microsoft.com/fwlink/?LinkId=131359)或[OEM 合作伙伴中心](http://go.microsoft.com/fwlink/?LinkId=131358)下载语言包和 Lip。

- 新的 /Defer 参数可以指定一起/ResetBase 当您[减少组件存储区的大小](desktop/reduce-the-size-of-the-component-store-in-an-offline-windows-image.md)将推迟到下一步的自动维护，但我们任何长时间运行清理操作高度建议，**仅**使用/推迟为 DISM /ResetBase 其中需要 30 分钟以上才能完成的工厂中的一个选项。

- 新的 /EA 参数已被添加到 Dism /Apply-Image 和 /Capture-Image 命令来捕获和应用扩展的属性。 对于 Windows，在收件箱进行身份验证的代码方案的扩展属性中捕获目录位置提示。 这使更快地验证哈希值，以确保系统文件/组件没有更改过。 创建的目录数据库和这些哈希的过程发生在首次启动 Sysprep 的一般化的映像。 如果扩展的属性用于捕获和应用映像，这些属性将办过来，删除的时间重新创建和启用更快的第一次启动。 有关详细信息，请参阅[DISM 图像管理命令行选项](desktop/dism-image-management-command-line-options-s14.md)。 

- 新的 Windows 硬件兼容性计划要求[Device.Graphics.AdapterBase.RunFromDriverStore](https://msdn.microsoft.com/windows/hardware/commercialize/design/compatibility/device-graphics#device-graphics-adapterbase)，可能会影响 OEM 预加载。 必须编写驱动程序，以便可以直接从驱动程序存储区运行及其组件。 %Systemroot%\system32\driverstore\filerepository 安装驱动程序。

## <a name="span-idwhatsnewinmobilemanufacturingspanwhats-new-in-mobile-manufacturing"></a><span id="Whats_new_in_Mobile_Manufacturing"></span>什么是移动制造中的新功能


**2016 年 10 月 4日，**

- 新的[可选功能](https://msdn.microsoft.com/library/windows/hardware/dn756780.aspx)︰ **16GBFEATURESONDATA**添加到 Windows 10，1607年版本中。 此功能将几种常见的收件箱应用程序移动到数据分区。 

## <a name="span-idwhatsnewiniotcoremanufacturingspanwhats-new-in-iot-core-manufacturing"></a><span id="Whats_new_in_IoT_Core_Manufacturing"></span>什么是 IoT 核心制造中的新功能

**2016 年 11 月 4日，**

- 添加的引用更改自动更新设置[实验室 1 d︰ 向图像中添加配置软件包](iot/add-a-provisioning-package-to-an-image.md)。
- 添加网络故障排除步骤[实验室 1 d︰ 向图像中添加资源调配包](iot/add-a-provisioning-package-to-an-image.md)︰ 检查的 Wi-Fi 广播的频率。 包括内置 Raspberry Pi 3，某些 Wi-Fi 适配器不支持 5 GHz Wi-Fi 网络。

**2016 年 10 月 17日，**

- 添加故障排除步骤[实验室 1 d︰ 向图像中添加配置软件包](iot/add-a-provisioning-package-to-an-image.md)。

**2016 年 10 月 12日，**

[实验室 1 d︰ 向图像中添加资源调配包](iot/add-a-provisioning-package-to-an-image.md): 
-  新的步骤，为了确保功能清单，OEMCommonFM.xml，包括在 TestOEMInput.xml 文件中。
-  新的网络连接和故障排除步骤添加。

**2016 年 10 月 5日，**

[Windows 10 IoT 核心现在是免费](iot/set-up-your-pc-to-customize-iot-core.md)的。 您不再需要 MSDN 订阅或帐户注册 Microsoft OEM，作为您需要 Microsoft 帐户也是如此。

**2016 年 10 月 4日，**

- [功能︰ **IOT\_SPEECHDATA\_EN\_美国**](iot/iot-core-feature-list.md)窗口 10，1607年版本中不建议使用。 不添加此功能。 默认的图像包含美国英语语音数据。

**2016 年 9 月 22日，**

- 在 Windows 10 版本 1607，以[防止自定义 Bsp 的自动更新](../service/iot/managing-iot-device-update.md)，请使用 IoT\_通用\_OemInput XML 中的 POP 包。 （您不能使用 Intel.Generic.DeviceInfo.cab，此文件已被删除）。

- 新的[命令行选项](iot/iot-core-adk-addons-command-line-options.md)︰ 

    - 每夜构建工具︰ **BuildAgent**、 **BuildKitAgent**。

    - 要转换驱动程序程序包的应用程序的工具︰ **Appx2pkg**、 **Inf2Pkg**

    - 创建更新程序包的工具︰ **newupdate.cmd**。 与**newpackage.cmd**一样，使跟踪变得更容易通过存储版本号 (versioninfo.txt) 和比较 (updateversions.txt) 这一更新的每个保持多个文件夹。

**2016 年 9 月 6日，**

您可以 IoT 核心将设备设置为[同步的时间](iot/update-the-time-server.md)从一个或多个时间服务器。

**2016 年 8 月 3日，**

默认情况下，Windows 10 版 1607，现已禁用内置管理员帐户。 

   -  要添加回默认的帐户，此功能清单中包括 IOT_ENABLE_ADMIN 功能添加的帐户的用户名︰ 管理员，密码︰ `p@ssw0rd`。
   
   -  若要添加自己的用户名和密码 （推荐） 使用新的帐户中，更新文件 OEMCustomizations.cmd，使用您自己的用户名和密码，并将其添加到您使用 OEM_CustomCmd 软件包的版本。 若要了解详细信息，请参阅[实验室 1b︰ 将应用程序添加到映像](iot/deploy-your-app-with-a-standard-board.md)。

添加的[功能 Windows 10，1607年版本的](iot/iot-core-feature-list.md)功能︰ 
   
   - IOT_UNIFIED_WRITE_FILTER – 添加要保护的数据写操作的物理存储介质[统一编写筛选器 (UWF)](https://developer.microsoft.com/windows/iot/docs/uwf) 。
   
   - IOT_GENERIC_POP – 添加 OS 的通用设备目标信息只更新。 
   
   - IOT_NANORDPSERVER – 添加[远程显示软件包](https://developer.microsoft.com/windows/iot/docs/remotedisplay)。
   
   - IOT_SHELL_HOTKEY_SUPPORT – 添加支持启动默认应用程序使用热键: [VK_LWIN （左 Windows 键）]
   
   - IOT_POWER_SETTINGS-（从 IOT_POWER_SETIINGS 已重命名）
   
   - IOT_ENABLE_ADMIN-测试功能
   
   语言： 
   
   -  IOT_SPEECHDATA_JA_JP︰ 添加日语语音数据
   
   -  IOT_SPEECHDATA_ZH_HK︰ 将语音数据添加为中文 （香港特别行政区）
   
   -  IOT_SPEECHDATA_ZH_TW︰ 为中文 （台湾） 添加语音数据
   

**2016 年 6 月 28日，**

-  有关签名的零售映像中添加详细信息︰[构建零售映像](iot/build-retail-image.md)

-  已更新的[说明进行操作来创建您自己的 BSP](iot/create-a-new-bsp.md)，添加有关[IoT 设备布局](iot/device-layout.md)的详细信息。

**2016 年 6 月 20日，**

*  新的 BSP 工具添加︰
   -  新的文件夹结构︰ Bsp 现在存储在单独的文件夹 \iot-adk-addonkit\Source-&lt;弧&gt;\BSP。 多个项目现在可以更方便地共享相同的 BSP 文件夹。
   -  已更新的工具︰ newproduct︰ 现在允许您要链接到自定义的 BSP。 默认情况下，arm 生成默认为 RPi2，x86 生成 MBM 的默认。
   -  更新的实验室︰[实验室 2︰ 创建主板支持软件包](iot/create-a-new-bsp.md)。

**2016 年 6 月 9日:** 

[命令行](iot/iot-core-adk-addons-command-line-options.md)工具的多个更新︰
*  新的工具︰ BuildImage.cmd。 与 CreateImage.cmd 类似，此工具可以生成多个图像时，可进行自动化测试。  

   要解决此问题，请参阅上的日志文件\\生成\\&lt;弧&gt;\\pkgs\\日志。   

*  更新时间︰[更新 IoT 核心设备上的应用程序](../service/iot/updating-iot-core-apps.md)。 可以使用相同的过程来构建应用程序软件包和应用程序更新软件包。 第 10 Windows 版本 1607，还可以更新您的应用程序通过 Windows 应用商店。 

**2016 年 5 月 18日:** 

[命令行](iot/iot-core-adk-addons-command-line-options.md)工具的多个更新︰
*  添加新的工具︰ 
   -  NewAppxPkg︰ 创建并准备工作文件夹创建基于.appx 文件、 证书和依赖项的应用程序软件包。
   
   -  NewDrvPkg︰ 创建并准备工作文件夹创建驱动程序包的.inf 文件的基础。
   
   -  NewCommonPkg︰ 创建并准备文件、 文件夹、 注册表项和不特定于体系结构的其他项目的工作文件夹。  
   
   -  Inf2Cab︰ 将.inf 文件转换到.cab 文件中。
   
   -  BuildPkg︰ 生成.cab 文件包使用工作文件夹。

*  不推荐使用的工具︰ 
   
   -  BuildAllPackages。 改为使用 BuildPkg。
   
   -  NewPkg。 改为使用 newappxpkg、 newdrvpkg 和 newcommonpkg。

*  故障排除和日志记录︰ 在生成包时，您将获得更清晰显示只显示已处理的文件包和任何错误。 要解决，现在可以看到完整的日志文件在\\生成\\&lt;弧&gt;\\pkgs\\日志。

*  更新︰ CreatePkg 现在支持添加的 Component.Subcomponent 名。 示例：

    ``` syntax
    createpkg Registry.SystemSettings
    ```

*  生产实验室︰ 更新以使用新的 NewAppPkg，NewDriverPkg，NewCommonPkg 工具的实验。