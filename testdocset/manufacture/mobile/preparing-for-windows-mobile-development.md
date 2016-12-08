---
Description: Here's what you'll need to start customizing, testing, and deploying Windows on mobile devices.
ms.assetid: 57bc2066-0b27-4fcb-b938-1c73a361b212
MSHAttr: PreferredLib:/library
title: "为 Windows 移动开发做准备"
author: CelesteDG
ms.openlocfilehash: e5fdd1fce8bf6a6926487df060b4785a6596ccd8
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="prepare-for-windows-mobile-development"></a>为 Windows 移动开发做准备


这里是您将需要启动自定义、 测试和部署 Windows，在移动设备上。

## <a name="span-idmeetalltheprerequisitesspanspan-idmeetalltheprerequisitesspanstep-1-meet-all-the-prerequisites"></a><span id="meet_all_the_prerequisites"></span><span id="MEET_ALL_THE_PREREQUISITES"></span>步骤 1︰ 满足所有系统必备组件


您可以在 Windows 移动开发开始之前，请确保满足以下要求︰

-   您可以访问 Microsoft 连接站点位置移动的合作伙伴可以下载最新的移动操作系统包和包。

    如果您不具有访问权限，或者需要更多的信息，请与您的 Microsoft 代表联系。

-   开发工作站或技术人员计算机

    这台电脑将运行在开发过程中所需的工具。 计算机必须运行下列操作系统之一︰

    -   Windows 10 (x86) 的 32 位或 64 位 (x64)
    -   Windows 8.1 (x86) 的 32 位或 64 位 (x64)
    -   Windows 7 (x86) 的 32 位或 64 位 (x64)

    您必须安装所有的 Windows 重要更新，以使用移动包时，避免出现任何问题。

-   卸载早期版本的工具和工具包

    如果您使用的是不同版本的工具和工具包工具包的*配对信息*一节中列出的不同发行说明，您首先需要卸载所有与这些组件相关联的程序。

-   下载工具包和 OS 程序包

    对于 Windows 10 移动从 Microsoft 连接站点下载最新的工具包和工具。 请参阅移动版本的内容，以了解更多有关不同的硅体系结构的 MobileOS 工具包的内容。

-   引用的移动硬件

    该移动设备应该表示在单个模型行; 所有移动设备例如，Contoso Windows Phone。 有关运行 Windows 10 移动的任何设备的详细的硬件需求的详细信息，请参阅*一节 2.0-10 Windows mobile 的最低硬件要求*的[最低硬件要求](https://msdn.microsoft.com/library/windows/hardware/dn915086)。

-   主板支持包 (BSP) 系统必备组件

    请确保您具有所有必要的 BSP 文件参考硬件。 BSP 是一套文件和 Windows 10 移动使用通信设备来启动操作系统，以及创建可在您引用的硬件运行的 OS 映像上的硬件的驱动程序。 SoC 供应商提供参考硬件 BSP。

## <a name="span-idinstallthetoolsanddevelopmentkitsspanspan-idinstallthetoolsanddevelopmentkitsspanstep-2-install-the-tools-and-development-kits"></a><span id="install_the_tools_and_development_kits"></span><span id="INSTALL_THE_TOOLS_AND_DEVELOPMENT_KITS"></span>步骤 2︰ 安装的工具和开发工具包


下面的工具包和工具用于 Windows 移动开发︰

-   Visual Studio 2015 年，这是您的主开发环境编写的应用程序和驱动程序。

-   Windows 10 移动操作系统，MobileOS 包中包含其中。

-   可以使用 Windows 评估和部署工具包 (ADK)，其中包含用于生成和自定义映像，因为和几个其他部署工具，您可以使用这些工具可以帮助您自动执行 Windows 的大规模部署。

-   Windows 驱动程序工具包 (WDK) 和 Windows 10 独立 SDK，您可以单独安装或安装企业 WDK (EWDK)，其中包含驱动程序工具包和 SDK 版本。

-   Windows 硬件实验室工具包 (HLK)，这是一个测试框架，可用于测试 Windows 硬件设备。

下表指定了哪些开发方案要求每个工具包和工具。

| 开发方案                                                                   | MobileOS 工具包 | Windows ADK  | Windows 独立 SDK | WDK          | Visual Studio 2015 年 |
|----------------------------------------------------------------------------------------|--------------|--------------|------------------------|--------------|--------------------|
| 在移动设备 （例如，驱动程序、 服务和应用程序） 运行的编译代码 | 必需     | 必需     | 必需               | 必需     | 必需           |
| 生成包                                                                         | 不需要 | 是否必需     | 不需要           | 不需要 | 不需要       |
| 签名的二进制文件和包                                                             | 不需要 | 是否必需     | 不需要           | 不需要 | 不需要       |
| 构建和自定义命令行上使用 ImgGen 上的移动图像                     | 是否必需     | 不需要 | 必需               | 必需     | 不需要       |
| 构建和自定义使用 Windows ICD 的移动图像                                    | 必需     | 必需     | 不需要           | 不需要 | 不需要       |

 

**若要安装工具包和工具**

1.  按照说明下载和安装[Visual Studio 2015年](https://go.microsoft.com/fwlink/p/?LinkId=533470)、 [Windows 驱动程序工具包 (WDK) 10](https://go.microsoft.com/fwlink/p/?LinkId=733614)和[Windows 10 SDK](https://go.microsoft.com/fwlink/p/?LinkId=616887)。

    **请注意** Visual Studio 2015年才需要编译将在移动设备上，如驱动程序和应用程序运行的代码。

     

    若要确认已正确安装了 Windows SDK，确保在下表中列出的子目录存在于您的技术人员计算机。 一些这些子目录可能不出现在工具包安装目录如果没有在 Windows SDK 安装向导中选择它们。

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left">Windows 安装目录树</th>
    <th align="left">在目录树中的子目录</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><p>对于 32 位操作系统︰ <strong>C:\Program Files\Windows Kits\10</strong></p>
    <p>对于 64 位操作系统︰ <strong>C:\Program 文件 (x86) \Windows Kits\10</strong></p></td>
    <td align="left"><ul>
    <li><strong>纸盒</strong></li>
    <li><strong>目录</strong></li>
    <li><strong>调试程序</strong></li>
    <li><strong>DesignTime</strong></li>
    <li><strong>包括</strong></li>
    <li><strong>Lib</strong></li>
    <li><strong>发行</strong></li>
    <li><strong>引用</strong></li>
    <li><strong>快捷方式</strong></li>
    <li><strong>测试</strong></li>
    </ul></td>
    </tr>
    </tbody>
    </table>

     

    要确认 WDK 已正确安装，请确保在下表中列出的子目录存在于您的技术人员计算机。

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left">Windows 安装目录树</th>
    <th align="left">在目录树中的子目录</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><p>对于 32 位操作系统︰ <strong>C:\Program Files\Windows Kits\10</strong></p>
    <p>对于 64 位操作系统︰ <strong>C:\Program 文件 (x86) \Windows Kits\10</strong></p></td>
    <td align="left"><ul>
    <li><strong>生成</strong></li>
    <li><strong>BuildLabSupport</strong></li>
    <li><strong>CodeAnalysis</strong></li>
    <li><strong>CrossCertificates</strong></li>
    <li><strong>调试</strong></li>
    <li><strong>帮助</strong></li>
    <li><strong>远程</strong></li>
    <li><strong>工具</strong></li>
    </ul></td>
    </tr>
    </tbody>
    </table>

     

2.  安装[窗口 10 ADK](http://go.microsoft.com/fwlink/p/?LinkId=526740)。

    确保**安装路径**被设置到工具包安装目录中， **c:\\程序文件\\窗口工具包\\10** （对于 32 位操作系统） 或**c:\\程序文件 (x86)\\窗口工具包\\10** （对于一个 64 位的操作系统）。

    在**选择要安装的功能**页上，选择下列设置︰

    -   **部署工具**
    -   **Windows 预安装环境 (Windows PE)**
    -   **图像处理和配置设计器 (ICD)**
    -   **配置设计器**
    -   **用户状态迁移工具 (USMT)**

    若要确认已正确安装了 Windows ADK，确保**评估和部署工具包**出现在您的 Windows 安装目录下。

3.  从 Microsoft 连接网站下载最新的移动操作系统包和包，并将内容复制到您的开发工作站上的本地目录。

    包和包包含的文件和生成 Windows 10 移动图像所需的工具。

4.  提取的文件包以及包安装位置的文件。

    1.  解压缩该 MobileOS-臂-fre.zip 软件包。
    2.  打开提取的包和所有子文件夹和其内容复制到工具包安装目录， **c:\\程序文件\\窗口工具包\\10** （对于 32 位操作系统） 或**c:\\程序文件 (x86)\\窗口工具包\\10** （对于一个 64 位的操作系统）。 文件夹应该是︰ FieldMedic、 FMFiles、 MSPackages、 OEMCustomization 和 OEMInputSamples。

5.  在**OEM**文件夹中，双击**Setup.exe**安装下面移动的组件︰

    -   Windows Phone 驱动程序工具包 (WPDK)
    -   调试器符号
    -   电话的 Windows 硬件实验室工具包内容
    -   测试外壳 (TShell)
    -   核心操作系统程序包

## <a name="span-idinstallothertoolsspanspan-idinstallothertoolsspanstep-3-install-other-tools"></a><span id="install_other_tools"></span><span id="INSTALL_OTHER_TOOLS"></span>步骤 3︰ 将安装其他工具


您可以从移动套件单独安装一些工具。 这些工具，包含在 IHV\_工具文件夹，如下所示。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">安装程序包</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>WP_CPTT_NT-x86-fre.msi</p></td>
<td align="left"><p>Windows 电话常见的包装和测试工具。</p></td>
</tr>
<tr class="even">
<td align="left"><p>WP8KDConn.msi</p></td>
<td align="left"><p>KDBG 连接软件包，其中包含以下组件︰</p>
<ul>
<li><p>虚拟以太网工具 (VirtEth.exe)</p></li>
<li><p>虚拟的网络驱动程序 (虚拟 PC 2007 筛选器，VmNetSrv），它是虚拟以太网工具所必需的除非已安装虚拟 PC 2007;将提示用户安装两个未签名驱动程序。</p></li>
<li><p>USB 串行驱动程序 （usb2ethernet 和 usbcompcom）</p></li>
<li><p>USB 调试程序驱动程序 (usb2dbg);将提示用户安装一个签名的驱动程序。</p></li>
</ul>
<p>虚拟的网络驱动程序安装在 %ProgramFiles%\Microsoft 虚拟的 PC\Utility\VMNetSrv （或 %programfiles (x86) %\Microsoft 为 64 位操作系统的虚拟 PC\Utility\VMNetSrv） 目录。</p>
<p>其他三个组件安装在 %ProgramFiles%\Microsoft Windows Phone 8 KDBG 连接 （或 %programfiles (x86) %\Microsoft 64 位操作系统的 Windows Phone 8 KDBG 连接） 目录树中，用虚拟以太网工具在 bin 子目录、 USB 串行驱动程序的 drivers\Usb2Eth 子目录中和 drivers\Usb2Dbg 子目录中的调试器 USB 驱动程序。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>TShell.msi</p></td>
<td align="left"><p>测试外壳，这是一套中携带使用的命令行工具和移动设备的测试。 为任务例如，将文件复制到移动设备，然后查看日志，可以使用 TShell。</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idsetupenvironmentvariablesspanspan-idsetupenvironmentvariablesspanstep-4-set-up-environment-variables"></a><span id="set_up_environment_variables"></span><span id="SET_UP_ENVIRONMENT_VARIABLES"></span>步骤 4︰ 设置环境变量


按照下面的步骤来设置所需的工作生产环境的环境变量。

**若要设置在 Visual Studio 2015年的生成环境**

1.  打开**开发人员为 VS2015 的命令提示符**窗口。

2.  将 WPDKCONTENTROOT 环境变量设置为 Windows 10 移动套件安装目录的位置。

    -   计算机运行 32 位版本的 Windows 中，默认情况下这是 %programfiles%\\窗口工具包\\10。

        **设置 WPDKCONTENTROOT = %programfiles%\\窗口工具包\\10**

    -   计算机运行 64 位版本的 Windows 中，默认情况下这是 %programfiles(x86)%\\窗口工具包\\10。

        **设为 WPDKCONTENTROOT=%ProgramFiles(x86) %\\窗口工具包\\10**

3.  将 WDKCONTENTROOT 环境变量设置为 WDK 工具包安装目录的位置。

    -   计算机运行 32 位版本的 Windows 中，默认情况下这是 %programfiles%\\窗口工具包\\10。

        **设置 WDKCONTENTROOT = %programfiles%\\窗口工具包\\10**

    -   计算机运行 64 位版本的 Windows 中，默认情况下这是 %programfiles(x86)%\\窗口工具包\\10。

        **设为 WDKCONTENTROOT=%ProgramFiles(x86) %\\窗口工具包\\10**

4.  添加 x86 工具目录窗口工具包和 Windows 工具包工具目录到 PATH 环境变量。

    **设置路径 = %PATH%; %WDKCONTENTROOT%\\bin\\x86; %WPDKCONTENTROOT%\\工具\\bin\\i386**

## <a name="span-idinstalloemtestcertsspanspan-idinstalloemtestcertsspanspan-idinstalloemtestcertsspanstep-5-install-oem-test-certs"></a><span id="install_OEM_test_certs"></span><span id="install_oem_test_certs"></span><span id="INSTALL_OEM_TEST_CERTS"></span>步骤 5: OEM 安装测试证书


要签名的二进制文件和软件包，您必须安装 OEM 测试证书。

**若要安装 OEM 测试证书**

-   确认，将 WPDKCONTENTROOT 设置为工具包安装位置的路径，使用下面的命令运行 InstallOEMCerts.cmd:

    **%WPDKCONTENTROOT%\\工具\\bin\\i386\\InstallOEMCerts.cmd**

    有关详细信息，请参阅[设置签名的环境](https://msdn.microsoft.com/library/windows/hardware/dn756804)。

 

 



