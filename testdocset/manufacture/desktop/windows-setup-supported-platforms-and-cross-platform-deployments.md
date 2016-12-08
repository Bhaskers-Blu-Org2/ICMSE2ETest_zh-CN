---
author: Justinha
Description: "Windows 安装程序支持的平台和跨平台部署"
ms.assetid: 044cbb4f-7330-473d-8654-3371b2d6aff1
MSHAttr: PreferredLib:/library/windows/hardware
title: "Windows 安装程序支持的平台和跨平台部署"
ms.openlocfilehash: b4a8d89666d56033d73360609cedb80830f17a58
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-setup-supported-platforms-and-cross-platform-deployments"></a>Windows 安装程序支持的平台和跨平台部署


本主题描述受支持的平台和运行 Windows 安装程序的部署方案。

当您部署的不同类型的 Pc 时，可以作为一种方式，您通过 Windows 安装程序用户界面以选择了特定图像的图像之间做出选择︰ 使用 Windows 安装程序。 您可以包括各种硬件平台 （如 BIOS 和 （uefi），32 位和 64 位的个人电脑） 的图像并跨不同版本的 Windows （如 Windows 8.1、 Windows Server 2012 R2，而 Windows 7）。

您还可以通过脚本来运行 Windows 安装程序。 启动到 Windows PE 中，PC，然后使用\\源\\setup.exe 文件以指定您的图像。

## <a name="span-idfirmwareconsiderationsbiosvsuefispanspan-idfirmwareconsiderationsbiosvsuefispanfirmware-considerations-bios-vs-uefi"></a><span id="firmware_considerations__bios_vs._uefi"></span><span id="FIRMWARE_CONSIDERATIONS__BIOS_VS._UEFI"></span>固件注意事项︰ BIOS 与 UEFI


支持引导到 UEFI 或旧版 BIOS 模式基于 UEFI 的计算机，请确保您的 PC 引导到正确的固件模式下启动 Windows 安装程序之前。 否则为 Windows 安装程序可能不正确，设置硬盘分区或可能中止安装，如果硬盘进行了预配置。 有关详细信息，请参阅[WinPE: UEFI 或旧版 BIOS 模式中的启动](winpe-boot-in-uefi-or-legacy-bios-mode.md)。

## <a name="span-idfirmwarebios32-bitand64-bitspanspan-idfirmwarebios32-bitand64-bitspanspan-idfirmwarebios32-bitand64-bitspanfirmware-bios-32-bit-and-64-bit"></a><span id="Firmware__BIOS_32-bit_and_64-bit"></span><span id="firmware__bios_32-bit_and_64-bit"></span><span id="FIRMWARE__BIOS_32-BIT_AND_64-BIT"></span>32 位和 64 位的固件︰ BIOS


若要设置单个环境或一套可以将 Windows 部署到 32 位和 64 位 BIOS Pc 的脚本，使用 32 位版本的 Windows PE 和 32 位版本的 Windows 安装。

64 位版本的 Windows 安装程序不运行 32 位版本的 Windows PE 上。

**要从 32 位版本的 Windows PE 安装的 Windows 64 位版本︰**

1.  引导使用 32 位版本的 Windows PE 的 PC。

2.  使用以下技术的任何安装的 Windows 64 位版本︰

    -   运行 32 位版本的 Windows 安装程序，然后使用**/InstallFrom**命令行选项选择 64 位 Windows 映像︰

        ``` syntax
        X:\windows\system32> D:\setup /InstallFrom:"N:\Windows_64-bit\sources\install.wim"
        ```

        -或者-

    -   运行 32 位版本的 Windows 安装程序，并使用`Microsoft-Windows-Setup\ImageInstall\OSImage\` [InstallFrom](http://go.microsoft.com/fwlink/?LinkId=275617)无人参与的设置，选择 64 位的 Windows 图像。

        ``` syntax
        X:\windows\system32> D:\setup /unattend:"D:\unattend_install_64-bit.xml"
        ```

        -或者-

    -   使用映像捕获工具应用到电脑的 Windows 64 位版本。

        ``` syntax
        Dism /Apply-Image /ImageFile:"Fabrikam_64-bit_image.wim" /Index:1 /ApplyDir:D:\
        ```

        有关详细信息，请参阅[使用 DISM 应用图像](apply-images-using-dism.md)。

**警告**  
此过程不支持部署 Windows 7。

 

## <a name="span-idusingwindowssetuptoinstallpreviousversionsofwindowsspanspan-idusingwindowssetuptoinstallpreviousversionsofwindowsspanspan-idusingwindowssetuptoinstallpreviousversionsofwindowsspanusing-windows-setup-to-install-previous-versions-of-windows"></a><span id="Using_Windows_Setup_to_Install_Previous_Versions_of_Windows"></span><span id="using_windows_setup_to_install_previous_versions_of_windows"></span><span id="USING_WINDOWS_SETUP_TO_INSTALL_PREVIOUS_VERSIONS_OF_WINDOWS"></span>使用 Windows 安装程序来安装 Windows 的先前版本


可以使用 Windows 安装程序的 Windows 8.1 和 Windows Server 2012 R2 版本要安装 Windows 的早期版本︰

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">主机操作系统</th>
<th align="left">Windows 8.1 安装支持</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Windows 8.1</p></td>
<td align="left"><p>是</p></td>
</tr>
<tr class="even">
<td align="left"><p>Windows Server 2012 R2</p></td>
<td align="left"><p>是</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Windows 8</p></td>
<td align="left"><p>是</p></td>
</tr>
<tr class="even">
<td align="left"><p>Windows Server 2012</p></td>
<td align="left"><p>是</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Windows 7</p></td>
<td align="left"><p>是</p></td>
</tr>
<tr class="even">
<td align="left"><p>Windows Server 2008 R2</p></td>
<td align="left"><p>是</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Windows Vista</p></td>
<td align="left"><p>否</p></td>
</tr>
<tr class="even">
<td align="left"><p>Windows Server 2008</p></td>
<td align="left"><p>否</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Windows XP sp3</p></td>
<td align="left"><p>否</p></td>
</tr>
<tr class="even">
<td align="left"><p>Windows Server 2003 R2 和以前的版本</p></td>
<td align="left"><p>否</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Windows XP SP2 和以前的版本</p></td>
<td align="left"><p>否</p></td>
</tr>
</tbody>
</table>

 

您还可以从 Windows 预安装环境 (Windows PE) 运行 Windows 安装程序。 下表列出了受支持的 Windows PE 环境︰

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Windows 安装程序的版本</th>
<th align="left">Windows PE 5.0 (Windows 8.1)</th>
<th align="left">Windows PE 4.0 (Windows 8)</th>
<th align="left">Windows PE 3.0 (Windows 7)</th>
<th align="left">Windows PE 2.0 (Windows Vista)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Windows 8.1 安装程序</p></td>
<td align="left"><p>是</p></td>
<td align="left"><p>是</p></td>
<td align="left"><p>是</p></td>
<td align="left"><p>否</p></td>
</tr>
<tr class="even">
<td align="left"><p>Windows 8 安装程序</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>是</p></td>
<td align="left"><p>是</p></td>
<td align="left"><p>是</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Windows 7 安装程序</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>是</p></td>
<td align="left"><p>是</p></td>
</tr>
<tr class="even">
<td align="left"><p>Windows Vista 安装程序</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>是</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idbkmkunsupportedspanspan-idbkmkunsupportedspancross-platform-deployment"></a><span id="bkmk_unsupported"></span><span id="BKMK_UNSUPPORTED"></span>跨平台部署


跨平台部署是不同的体系结构环境中安装 Windows 的特定体系结构的过程。 例如，您可以部署 Windows 8.1 或 Windows 8 的是 32 位版本的 Windows PE 从 64 位版本。 使用跨平台部署的解决方案的优点是不需要维护多个版本的 Windows PE 安装不同的体系结构版本的 Windows。 您可以构建一个 Windows PE 映像可用于安装 32 位和 64 位版本的 Windows。

从 32 位版本的 Windows PE 安装 64 位版本的 Windows 时，您必须使用 Windows PE 2.0 或更高版本。 Windows PE 版本有关详细信息，请参阅[Windows 10 的 WinPE](winpe-intro.md)。

下表列出了不同的体系结构类型的特定版本的 Windows 8.1 安装程序将无法安装的 Windows 映像 （32 位或 64 位）。

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"></th>
<th align="left">64 位 Windows 8.1 图像</th>
<th align="left">32 位 Windows 8.1 图像</th>
<th align="left">64 位 Windows 8 的图像</th>
<th align="left">32 位 Windows 8 的图像</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>64 位 Windows 8.1 安装程序</p></td>
<td align="left"><p>是</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>是</p></td>
<td align="left"><p>否</p></td>
</tr>
<tr class="even">
<td align="left"><p>32 位 Windows 8.1 安装程序</p></td>
<td align="left"><p>是</p></td>
<td align="left"><p>是</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>是</p></td>
</tr>
</tbody>
</table>

 

### <a name="span-idlimitationsofcross-platformdeploymentspanspan-idlimitationsofcross-platformdeploymentspanspan-idlimitationsofcross-platformdeploymentspanlimitations-of-cross-platform-deployment"></a><span id="Limitations_of_cross-platform_deployment"></span><span id="limitations_of_cross-platform_deployment"></span><span id="LIMITATIONS_OF_CROSS-PLATFORM_DEPLOYMENT"></span>跨平台部署的限制

不支持这些跨平台部署方案︰

-   在 32 位计算机上安装 64 位的 Windows 图像。

-   将部署从 64 位预安装环境的 32 位 Windows 映像。

-   使用 32 位版本的 Windows 安装程序进行升级系统的 64 位操作系统。

-   使用 32 位版本的 Windows 8 安装来部署 Windows 7 操作系统的 64 位版本。

    例如，必须使用 64 位版本的 Windows 8 安装来部署 Windows 7 的 64 位版本。 在以前版本中，Windows 安装程序版本的版本必须匹配将部署操作系统。 例如，您必须使用 Windows 7 Setup.exe 安装 Windows 7。

-   跨平台部署方案中使用 Microsoft Internet SCSI (iSCSI) 启动磁盘。

    例如，将 Windows （64-位版本） 跨平台的媒体，例如 Windows PE （32-位版本），从安装到 iSCSI 启动磁盘不受支持。 时必须使用相同的体系结构的 Windows PE 为目标部署体系结构将 Windows 部署 iSCSI 的启动盘。

-   在统一可扩展固件接口 (UEFI)，部署从 32 位版本的 Windows PE 是 64 位版本的 Windows。 上一些 （uefi） 的计算机，您不能在 BIOS 兼容性模式下安装 Windows 并必须切换到 UEFI 兼容性模式。 有关详细信息，请参阅[为 UEFI 模式或传统 BIOS 模式的引导](boot-to-uefi-mode-or-legacy-bios-mode.md)。

-   在 BIOS:

    -   作为全新的安装，或执行 Windows 部署服务部署的一部分，除执行跨平台部署。

    -   恢复为用户提供跨平台的安装媒体。

        若要防止用户对其计算机的体系结构的错误版本的 Windows 安装，不跨平台安装介质为用户提供用于恢复或重新安装。 此外，包括在媒体的 Windows 恢复环境 (Windows RE) 功能仅适用于 32 位 Windows 安装。

### <a name="span-idcreatingwimfilespanspan-idcreatingwimfilespanspan-idcreatingwimfilespancreating-a-wim-file-for-multiple-architecture-types"></a><span id="Creating_WIMFile"></span><span id="creating_wimfile"></span><span id="CREATING_WIMFILE"></span>创建一个.wim 文件进行多种体系结构类型

如果.wim 文件中包含 32 位和 64 位 Windows 版本，您必须选择要安装的 Windows 映像。 通常情况下，Windows 安装程序将使用您指定的产品密钥`ProductKey`设置来确定要安装的 Windows 映像。 但如果该文件包含 2 版本的相同的 Windows 版本，如 Windows 8.1 专业人员，您必须使用`MetaData`在应答文件中设置，以指定要安装的版本。

若要选择一个图像，指定图像索引、 名称、 说明或体系结构类型相对应的元数据。 为体系结构类型的元数据，使用 32 位版本和 64 位版本 9 0。 有关详细信息，请参阅`MetaData`[键](http://go.microsoft.com/fwlink/?LinkId=320263)设置。

答案文件必须包含特定于处理器的组件。 在[windowsPE](windowspe.md)配置阶段中的答案文件设置必须匹配预安装环境的体系结构的类型。 将应用于 Windows 映像的设置必须匹配图像的架构类型。 例如，如果您创建的应答文件中将部署从 32 位预安装环境的 64 位图像，windowsPE 配置阶段的应答文件中的所有组件必须都包括**x86**的处理器特性类型。 设置要应用刀必须[擅长](specialize.md)、 [oobeSystem](oobesystem.md)或其他配置中包括**amd64**处理器特性类型。

### <a name="span-idbkmk5spanspan-idbkmk5spaninstalling-64-bit-drivers"></a><span id="bkmk_5"></span><span id="BKMK_5"></span>安装 64 位驱动程序

Windows 附带的所有驱动程序进行签名。 在跨体系结构部署中，您可以使用现成的设备驱动程序。 但是，如果您使用不启动关键在 64 位安装中的未签名的现成的设备驱动程序，则安装可能会不可用。

用这些方法之一，可以在 Windows 安装过程中安装 64 位的 Windows 映像的驱动程序︰

-   在有人参与安装中，可以按 f6 键或单击 Windows 安装程序的**磁盘配置**页面上**加载驱动程序**按钮。

-   在无人参与安装中，您可以使用 Microsoft 的 Windows PnpCustomizationsWinPE 或 Microsoft 的 Windows PnpCustomizationsNonWinPE 组件答案文件中指定驱动程序路径。 有关如何自动完成您的安装的详细信息，请参阅[自动执行 Windows 安装程序](automate-windows-setup.md)。

## <a name="span-idhardwareconsiderationsencryptedharddrivese-drivesspanspan-idhardwareconsiderationsencryptedharddrivese-drivesspanspan-idhardwareconsiderationsencryptedharddrivese-drivesspanhardware-considerations-encrypted-hard-drives-e-drives"></a><span id="Hardware_considerations__Encrypted_Hard_Drives__e-Drives_"></span><span id="hardware_considerations__encrypted_hard_drives__e-drives_"></span><span id="HARDWARE_CONSIDERATIONS__ENCRYPTED_HARD_DRIVES__E-DRIVES_"></span>硬件注意事项︰ 加密硬盘 （e 驱动器）


我们在 Windows 8、 Windows Server 2012 和 Windows PE 4.0 添加加密硬驱动器设备 （也称为 E 驱动器） 的支持。

若要安装以前版本的 Windows (示例︰ Windows 7 或 Windows Vista) 到加密硬驱动器设备上，使用 Windows PE 4.0 或更高版本。

有关详细信息，请参阅[加密硬驱动器设备指南](http://go.microsoft.com/fwlink/?LinkId=290954)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[在 UEFI 或旧版 BIOS 模式下的 WinPE︰ 引导](winpe-boot-in-uefi-or-legacy-bios-mode.md)

[Windows 安装程序方案和最佳做法](windows-setup-scenarios-and-best-practices.md)

[Windows 安装程序安装过程](windows-setup-installation-process.md)

[Windows 安装程序自动化概述](windows-setup-automation-overview.md)

[审核模式概述](audit-mode-overview.md)

[Windows 安装程序配置阶段](windows-setup-configuration-passes.md)

 

 






