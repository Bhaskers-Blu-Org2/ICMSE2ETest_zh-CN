---
title: "系统生成器部署 Windows 10 的桌面版本"
author: Justinha
description: "获取有关系统构建者将 Windows 10 部署到台式机、 笔记本电脑和 2--1 的分步指导。"
ms.openlocfilehash: e94a13a258d49ec66ccfb2fa1ce068ec6f8d0dec
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="system-builder-deployment-of-windows-10-for-desktop-editions"></a>系统生成器部署 Windows 10 的桌面版本 

本指南可用于将 Windows 10 部署到的计算机的行。 它提供了说明性指导对于 Windows 10 部署，包括在线和离线的自定义，以及对特定方案的可选步骤。 它旨在帮助系统集成商 （级别 200 技工） 使用 64 位和 32 位的配置，并对于桌面版本 （家庭、 Pro、 企业和教育） 适用于 Windows 10。 

## <a name="prepare-your-lab-environment"></a>准备您的实验室环境

第一步是设置实验室环境，其中包括安装新的 Windows 评估和部署工具包 (Windows ADK) 到您指定的技术人员计算机上的工具。 技术人员计算机必须运行 Windows 10 x64，如果您打算部署 x64 映像或 x86 的运行的 Windows 10 x86 映像部署。 配置不正确可能会导致 Windows ADK 在使用部署工具时支持的结构不匹配。 另有说明，按照适当的准则两个 64 位和 32 位部署。

在开始之前部署过程，您需要下载将贯穿整个指南的工具包。 转到[OEM 合作伙伴中心](http://www.microsoft.com/oem/en/pages/index.aspx#fbid=7JcJYKYGEfo) > **的下载和安装** > **了解 ADKs 和 OPKs**。 资源和将使用的包和获取它们的位置的列表，请参阅[您的需要从哪里得到它](#what-you-will-need-and-where-to-get-it)。

您将需要两个 USB 驱动器。 USB 的可用于在 Windows 预安装环境 (WinPE) 引导系统。 USB B 将用于存储部署和恢复脚本的计算机之间移动文件、 存储和应用创建的映像。

<table>
<th>USB 硬盘名称</th>
<th>Format</th>
<th>最小大小</th>
<tr>
<td>USB 的</td>
<td>FAT32</td>
<td>~ 4 GB</td>
</tr>
<tr>
<td>USB-B</td>
<td>NTFS</td>
<td><p>~ 16 GB x86</p><p>~ 32 GB amd64</p></td>
</tr>
</table>

### <a name="creating-my-usb-b"></a>创建我的 USB-B

-   您的 USB 驱动器进行格式化并命名它，如下所示︰

    ![提取 USB](images/extract-usb.png) 

-   然后从 Microsoft 下载中心下载[USB B.zip](http://download.microsoft.com/download/5/8/4/5844EE21-4EF5-45B7-8D36-31619017B76A/USB-B.zip) 。 将该.zip 文件保存到 USB-B 和提取的内容。 

-   USB B 中所包含的配置文件的内容是根据品牌和制造选项，您可以更改的示例。 但是，文件的名称和文件夹和文件的层次结构必须是以便协调您的部署过程，本指南所示的相同。

## <a name="customizations-throughout-the-document"></a>整篇文档的自定义项

| **传递**        | **设置**                              | **操作**                                                            |
|-----------------|------------------------------------------|-----------------------------------------------------------------------|
| **WinPE**       | 安装程序用户界面语言                        | EN-US                                                                 |
|                 | 用户数据                                | ODR 的定义的预安装的产品密钥                         |
| **专门负责**  | Internet Explorer 主页              | 在应答文件中                                                    |
|                 | OEM 名称                                 | 在答案文件中定义                                            |
|                 | OEM 徽标                                 | 在答案文件中定义                                            |
|                 | 模型                                    | 在答案文件中定义                                            |
|                 | 支持信息                             | 在答案文件中定义                                            |
| **OOBE 系统** | 重新封装                                   | 审核/OOBE                                                            |
|                 | StartTiles                               | 方形麻将牌 / SquareOrDesktopTiles 设置锁定仅桌面应用程序      |
|                 | TaskbarLinks （最多 6 个固定的.lnk 文件） | 已设置绘画和控制面板的快捷键                       |
|                 | 主题                                   | 已设置为桌面背景的 OEM 徽标的自定义主题 |
|                 | 视觉效果                           | SystemDefaultBackground 集                                           |

## <a name="additional-customizations"></a>其他自定义设置

### <a name="product-deployment"></a>部署产品

-   预加载 office 单个图像 v15.4 OPK

### <a name="image-customization"></a>映像自定义

- 添加到 Windows 的语言界面包

- 添加驱动程序和更新包

- 向窗口中添加 OEM 特定徽标和背景文件

- 图像大小优化

- 锁定桌面应用程序的启动 sceen

## <a name="create-a-usb-drive-that-can-boot-to-winpe"></a>创建到 WinPE 可引导的 USB 驱动器

要自定义的图像，必须使用 Windows ADK 的匹配版本。 如果构建映像使用 RTM 映像，使用 Windows 10 为 Windows ADK。 如果使用的 Windows 10 版本 1511年图像，使用 Windows ADK 的 Windows 10 1511年版本。
有关 Windows ADK 的更多详细信息，请参阅[Windows 10 ADK 文档主页](https://technet.microsoft.com/library/mt297512.aspx)。

|  Windows 版本  | 要运行 ADKSetup.exe 的链接      |
|-------------------|-------------------------------|
| Windows 10 RTM    | [**Windows ADK**](http://download.microsoft.com/download/8/1/9/8197FEB9-FABE-48FD-A537-7D8709586715/adk/adksetup.exe)  |
| 第 10 Windows 版本 1511 | [**Windows ADK**](http://download.microsoft.com/download/3/8/B/38BBCA6A-ADC9-4245-BCD8-DAA136F63C8B/adk/adksetup.exe) |


1.  请按照屏幕说明来安装 Windows ADK，包括**部署工具**、 **Windows 预安装环境**和**评估 Toolkit Windows**功能。

    ![选择 ADK 功能](Images/adk-select-features.png)

1.  按 Windows 键以显示**开始**菜单。 类型：
    
        Deployment and Imaging Tools Environment

    用鼠标右键单击工具的名称，然后单击**以管理员身份运行**。

2.  Windows ADK 允许您创建**Windows 预安装环境**。 将基 WinPE 复制到新文件夹中。

    如果您使用**x64** Windows 10 图像，复制 x64 WinPE 文件夹结构︰

        Copype amd64 C:\winpe_amd64

    如果您使用**x86** Windows 10 图像，复制 x86 WinPE 文件夹结构︰

        Copype x86 C:\winpe_x86

1.  您可以添加包和/或驱动程序到 WinPE 此处。

2.  连接的 USB 驱动器中至少 4 GB。 此图中所示设置其格式︰

    ![连接 USB](Images/connect-usb.png)

3.  请插入的 USB 新 WinPE 可引导 USB。

    如果您使用**x64** Windows 10 图像，使 x64 WinPE USB:

        MakeWinPEMedia /UFD C:\winpe_amd64 F:

    如果您使用**x86** Windows 10 图像，使 x86 WinPE USB:

        MakeWinPEMedia /UFD C:\winpe_x86 F:

    （其中 f︰ 是 USB 驱动器号）

## <a name="install-windows-with-basic-customizations"></a>具有基本的自定义安装 Windows

请从 Microsoft 授权分销商处获取 Windows 10 x86/x64 DVD 介质。

要帮助您定制 unattend.xml 文件中定义的自定义项的文档，请参阅[Windows 系统构建的指导原则](http://www.microsoft.com/oem/en/pages/download.aspx?wpid=w_w8_129)和[Windows 系统构建的策略](https://oem.microsoft.com/downloads/worldwide/windows_10/Windows_10_Policy_SB.pdf)。

1.  复制源\\Install.wim 在您将部署到本地桌面 (~ 3 gb) Windows 10 媒体目录中的文件。

    ![复制 WIM](Images/copy-wim.png)

1.  运行**Windows 系统映像管理器**开始从头创建答案文件。 此工具允许您创建或应答文件管理变得简单而有条理的方式。

    ![运行 sim 卡](Images/run-sim.png)

1.  导航到**文件** &gt; **选择的 Windows 映像**。 浏览到本地桌面并选择**Install.wim**。 编录文件将为该指定 wim （.clg 文件） 创建。

    疑难解答︰ 目录创建可能失败由于几个原因。 请确保 install.wim 具有读/写权限。 如果您继续收到错误，请确保正确的技术人员计算机上已安装的体系结构 （x86 或 x64） Windows 10。 如果您正在创建的 x64 目录所需的 Windows 10 图像使用 x64 Windows 10 安装在 x64 Windows 10 计算机。 Install.wim 图像和 Windows 10 ADK 版本必须相同。

1.  打开示例答案文件或新建一个。

    -   这是包括在 USB b: 示例答案文件

        USB-B\ConfigSet\AutoUnattend.xml

1.  单击**确定**以将答案文件与 Windows 映像相关联。 

3.  将驱动程序添加到 Windows PE，单击**插入**选择**驱动程序路径**并选择传递**1 windowsPE** ，然后浏览到该驱动程序。 注︰ 此步骤是可选项，只有第三方驱动程序需要在 Windows 预安装环境中使用时所需。 

2.  添加文件包，单击**插入**，选择**包**，然后浏览到您想要添加的软件包。 此步骤是可选的。

### <a name="customize-the-answer-file"></a>自定义答案文件

解决︰ 专门负责**中的空白字符 |Microsoft Windows 外壳程序安装 |计算机名称**将导致 Windows 安装失败。

1.  请基本自定义答案文件的示例，参阅︰

    -   USB-B\ConfigSet\AutoUnattend.xml

    可以使用示例答案文件并修改相关部件或从头开始通过指定一些基本的自定义。

    请查看和使用 Windows 10**默认产品密钥**选项卡列出默认从[OEM 合作伙伴中心](https://www.microsoft.com/OEM/en/products/windows/Pages/windows-10-build.aspx#fbid=nV7H02bHHiv)的产品密钥。

1.  添加匹配的 Windows 版本的产品密钥。 此项不用来激活 Windows，以便可以重复使用相同的多个安装密钥︰

    -   在**应答文件**窗格中，选择**Components\1 windowsPE\amd64_Microsoft Windows Setup_neutral\UserData\ProductKey**。 在**产品密钥属性**窗格中的在**设置**，请输入键旁边的值。

    重要提示︰ 这些产品密钥*不能*用于激活。 您将需要激活的安装过程中输入软件的产品密钥。 将删除这些注册表项运行 sysprep 的一般化时。 最终用户需要在首次启动 Windows 10 时键入的真品证书 (COA) 标签中唯一的产品密钥。

1.  添加支持信息︰

    在**应答文件**窗格中，选择**Components\4 specialize\amd64_Microsoft-Windows 的外壳-Setup_neutral\OEMInformation**。

    在**OEMInformation 属性**窗格中的**设置**部分中，更新下面的值︰ 公司名称 （制造商） 小时 (SupportHours) 的电话号码 (SupportPhone) 和网站 (SupportURL)。

1.  准备您的计算机启动到审核模式下，Windows 安装完成后︰

    在**Windows 映像**窗格中，展开**组件**， **amd64_Microsoft Windows 部署**中，用鼠标右键单击，然后选择**将设置添加到传递 7 oobeSystem**。

    在**应答文件**窗格中，选择**Components\7 oobeSystem\amd64_Microsoft Windows 部署 _neutral\Reseal**。

    在**重新封装属性**窗格中的**设置**部分中，添加下面的值︰ 模式 = 审核。

1.  设置 Internet Explorer 主页︰

    在**Windows 映像**窗格中， **amd64_Microsoft Windows IE InternetExplorer**中，用鼠标右键单击，然后选择**将设置添加到传递 4 专用化**。

    在**应答文件**窗格中，选择**Components\4 specialize\amd64_Microsoft-Windows-Microsoft-Windows-IE-InternetExplorer_neutral**。

    在**IE InternetExplorer 属性**窗格中的**设置**部分中，选择 Home_page，并添加您的网站的 URL。

1.  Oem 可以指定用于创建/修改磁盘分区和设置映像安装分区的**磁盘配置**。 此步骤是可选的配置包含在示例答案文件 USB-B\ConfigSet\AutoUnattend.xml。

    将答案文件保存到 USB-B\ConfigSet\AutoUnattend.xml，然后关闭 Windows sim 卡。

### <a name="install-windows"></a>安装 Windows

1.  请跳过此步骤可确保 Windows 安装文件已复制到**myWindows**目录中 USB B.先完成[创建我 USB-B](#creating-my-usb-b)节

2.  参考计算机启动并插入 USB a。

3.  已启动 WinPE 之后，插入 USB b。

    疑难解答︰ 如果启动 USB 失败，请确保已确定优先级别而不是硬盘引导的 USB 启动。 为此，请进入 BIOS 菜单和调整启动顺序与选择 USB 启动的第一个选项。

1.  输入开始 Diskpart 类型*diskpart*和命中。 然后键入*列表卷*来识别 USB B 卷标 (例如︰ e:\)。 最后键入*退出*以退出 Diskpart。

    ![Diskpart](Images/diskpart.png)

1.  使用下面的命令以启动安装。 此命令使用答案文件安装 Windows 10 与其他自定义设置触发*setup.exe* 。

        Xcopy /herky e:\configset\$oem$ e:\MyWindows\Sources\$OEM$

        E:\myWindows\setup.exe /unattend:E:\ConfigSet\AutoUnattend.xml

1.  复制安装文件后，断开 USB a。

2.  计算机重新启动后，请拔下 USB B 右。

### <a name="verify-customizations-in-audit-mode"></a>验证在审核模式下自定义项

重要说明︰ 将计算机连接到 internet 不推荐在生产阶段。 不建议在审核模式中从 Windows Update 获取更新。 在审核模式下，这很可能会生成通用化 + syspreping 计算机时出错。

1.  在安装完成后已完成的计算机日志到 Windows 在审核模式下自动以管理员身份。

2.  单击*桌面上平铺*显示桌面，您应看到 Sysprep 窗口。

3.  验证所述应答文件 （请参阅制造商的名称、 支持电话号码和其他自定义） 的更改。

    ![Sysprep](Images/sysprep.png)

1.  图像必须推广之前被用作制造图像;选中复选框**通用化**。

2.  在系统清理操作框中选择**输入系统的现成经验**。

3.  在关机选项框中选择**关机**。

## <a name="capture-an-image"></a>捕获映像

1.  参考计算机启动并连接 USB a。

2.  已启动 WinPE 后连接 USB b。

    疑难解答︰ 如果使用 USB 引导失败，请确保已确定优先级别而不是硬盘引导的 USB 启动。 为此，请打开 BIOS 菜单和调整启动顺序，以使第一个选项是 USB 启动。 随着系统的不断从硬盘启动，Windows 将输入专用化，然后 OOBE 传递。 为了捕获通用且稳定的图像，无窗口刀必须完成。 若要再次一般化映像时，请按 Ctrl + Shift + F3 以跳过 OOBE 并在审核模式下引导。 在审核模式下，Sysprep 使用 OOBE 重新引导系统并对交换机进行一般化。 在系统重新启动后，请务必从 USB A 引导到 WinPE。

1.  输入开始 Diskpart 类型*diskpart*和命中。 然后确定 Windows 安装卷的卷标签类型*列表卷*标记为"窗口"(例如︰ c:\)。 最后键入*退出*以退出 Diskpart

2.  捕获的映像的 windows 分区到 USB b。 此过程需要几分钟的时间。

        MD E:\scratchdir

        Dism /Capture-Image /CaptureDir:C:\ /ImageFile:E:\Images\ThinImage.wim /Name:"myWinImage" /scratchdir:e:\scratchdir

    C:\ 是当前安装的 Windows 的卷标。 E:\ 是 USB B.的卷标

## <a name="update-images-for-each-model-offline-servicing"></a>更新每个模型的图像︰ 离线维修

1.  之前装载和编辑图像请相同的目录中执行的备份副本，然后重命名图像将被修改为 ModelSpecificImage.wim。

        Copy E:\Images\ThinImage.wim E:\Images\ModelSpecificImage.wim

### <a name="mount-images"></a>装入映像

1.  装载 Windows 映像 (ModelSpecificImage.wim) 这一过程中提取到一个位置，在其中您可以查看和修改已装入的映像的图像文件的内容。

        Md C:\mount\windows

        Dism /Mount-Wim /WimFile:E:\Images\ModelSpecificImage.wim /index:1 /MountDir:C:\mount\windows

    E:\ 所在的驱动器号的 USB b。

1.  图像文件重新安装 Windows。

        Md c:\mount\winre

        Dism /Mount-Image /ImageFile:C:\mount\windows\Windows\System32\Recovery\winre.wim /index:1 /MountDir:C:\mount\winre

    疑难解答︰ 如果装载操作失败，请确保正从技术人员计算机使用 DISM 安装与 Windows ADK 的 Windows 10 版本和旧版本的不。 不装入图像到受保护的文件夹，如 User\Documents 文件夹。 如果 DISM 进程被打断，可以考虑暂时断开与网络的连接和禁用病毒防护。

    ![装载](Images/mount.png)

    ![Windows 文件夹](Images/windows-folder.png)

### <a name="modify-images"></a>修改图像

#### <a name="add-drivers"></a>添加驱动程序

如果您使用 x64 Windows 10 图像，添加 x64 的驱动程序;如果您使用 x86 Windows 10 图像，添加 x86 驱动程序。

1.  添加驱动程序程序包一个一个地。 （.inf 文件）SampleDriver\driver.inf 是特定于计算机模型的**示例**驱动程序包。 键入您自己的特定驱动程序路径。 如果您有多个驱动程序程序包，请跳过下一步。

        Dism /Add-Driver /Image:C:\mount\windows /Driver:"C:\SampleDriver\driver.inf"

        Dism /Add-Driver /Image:C:\mount\winre /Driver:"C:\SampleDriver\driver.inf"

1.  如果您指定一个文件夹，而不是一个.inf 文件，可以在一个命令行添加多个驱动程序。 要安装所有的驱动程序文件夹及其所有子文件夹中，请使用**/recurse**选项。

        Dism /Image:C:\mount\windows /Add-Driver /Driver:c:\drivers /Recurse

1.  检查 %WINDIR%\Inf\ 中的内容 (C:\mount\windows\Windows\Inf\)目录中安装的 Windows 映像，以确保已安装程序的.inf 文件。 添加到 Windows 映像的驱动程序称为 Oem\*。 inf。 这是为了确保添加到计算机的新驱动程序命名的唯一性。 例如，MyDriver1.inf 和 MyDriver2.inf 的文件被重命名为 Oem0.inf 和 Oem1.inf。

2.  验证驱动程序已安装这两个图像。

        Dism /Image:C:\mount\windows /Get-Drivers

        Dism /Image:C:\mount\winre /Get-Drivers

重要说明︰ 如果该驱动程序包含仅安装程序包并没有.inf 文件，您可以在审核模式下安装驱动程序，双击相应的安装程序包。 某些驱动程序可能会使用 Sysprep 工具; 不兼容sysprep 一般化，即使他们有注入离线后，他们将被删除。

在这种情况下，您需要添加 USB-B\AnswerFiles\UnattendSysprep.xml 额外的参数，将通用图像时保留图像中的驱动程序。

&lt;PersistAllDeviceInstalls&gt;为&lt;/PersistAllDeviceInstalls&gt;

此属性必须被添加到 USB-B\AnswerFiles\UnattendSysprep.xml 通用化阶段才能持久地保存映像中的驱动程序。 此属性以及如何将其添加到答案文件的详细信息的详细信息，请参阅[PersistAllDeviceInstalls](http://technet.microsoft.com/library/ff716298.aspx)。

#### <a name="add-language-interface-packs"></a>添加语言界面包

从[OEM 合作伙伴中心](https://www.microsoft.com/OEM/en/installation/downloads/Pages/Windows-10-v1511-Language-Interface-Packs.aspx#fbid=nV7H02bHHiv)获取 Windows 10 语言界面包，**嘴唇**选项卡下。

嘴唇有关的详细信息，请参阅[添加语言界面包为 Windows 10](add-language-interface-packs-to-windows.md)。

**重要提示︰ 唇版本必须匹配其他 Windows 组件版本中的，图像和 ADK。**

如果您使用 x64 Windows 10 图像，x64 安装 Lip。如果您使用 x86 Windows 10 图像，x86 安装 Lip。

1.  将 LIP 文件夹复制到 USB B\LanguagePack\x64 或 USB B\LanguagePack\x86 文件夹︰

    ![复制唇](Images/copy-lip.png)

1.  将 LIP 应用到已装载的映像。

    *Amd64 体系结构*

        Dism /image:C:\mount\windows /add-package /packagepath:e:\LanguagePacks\amd64\ga-ie\lp.cab

    *X86 体系结构*

        Dism /image:C:\mount\windows /add-package /packagepath:e:\LanguagePacks\x86\ga-ie\lp.cab

**重要提示︰ 不要更新之后安装语言包。如果安装的更新 （修补程序、 常规分发版本 [GDR] 或服务包 [SP]） 是之前安装语言包包含依赖于语言的资源，则不会应用更新中包含的特定于语言的更改更新将需要重新安装。总是在安装更新之前安装语言包。**

#### <a name="add-update-packages"></a>添加更新程序包

如果您使用 x64 Windows 10 图像，添加 x64 更新包;如果您使用 x86 Windows 10 图像，添加 x86 更新包。

若要获取更新包，请从[Microsoft 更新目录](http://catalog.update.microsoft.com/v7/site/Home.aspx)下载它们。

1.  运行 Internet Explorer 并导航到[Microsoft 更新目录](http://catalog.update.microsoft.com/v7/site/Home.aspx)网页。 有关哪些软件包应从获取 Microsoft 更新目录的详细信息，请参阅[您的需要从哪里得到它](#what-you-will-need-and-where-to-get-it)。

2.  在搜索框中键入每个单个更新包，并单击**搜索**。

    ![更新目录](Images/update-catalog.png)

1.  搜索完成后，单击**添加**旁边的版本和您想要下载的程序包的体系结构。

    ![添加更新目录](Images/add-update-catalog.png)

1.  在添加了所有下列更新之后，单击**查看选择篮**，然后**下载**。

    ![下载更新目录](Images/download-update-catalog.png)
    
    ![下载完成](Images/download-update-catalog-complete.png)

    **解决︰**如果您遇到的错误，如"网站遇到问题"后单击"下载"，请尝试临时关闭 IE 或 IE 中禁用保护模式中弹出窗口阻止程序

    ![启用保护模式](Images/enable-protected-mode.png)

1.  下载后所有列出的重要更新，**更新程序包**（KB 包） 向映像中添加一个一个地通过使用下面的命令︰

    *Amd64 体系结构*

        Dism /Add-Package /Image:C:\mount\windows /PackagePath:"C:\SampleUpdatePackages\Windows10-KB3118754-x64.msu"

    *X86 体系结构*

        Dism /Add-Package /Image:C:\mount\windows /PackagePath:"C:\SampleUpdatePackages\Windows10-KB3118754-x86.msu"

1.  将更新添加到 winre.wim （其中它们应用; 并不是所有的更新应用到 winre.wim）

    *Amd64 体系结构*

        Dism /Add-Package /Image:C:\mount\winre /PackagePath:"C:\SampleUpdatePackages\Windows10-KB3118754-x64.msu"

    *X86 体系结构*

        Dism /Add-Package /Image:C:\mount\winre /PackagePath:"C:\SampleUpdatePackages\Windows10-KB3118754-x86.msu"

#### <a name="add-oem-specific-visual-customizations"></a>添加 OEM 特定的可视化自定义项

1.  创建 C:\mount\windows\Windows\system32\ 目录下的 OEM 文件夹。

2.  将 OEM 徽标复制到 C:\mount\windows\Windows\system32\OEM\**FabrikamLogo.bmp* *的目录中将映射的无人参与文件中的* *OEM 信息 |徽标** 属性。

    请参阅下面的图像在答案文件中添加 OEM 徽标。

    -   %windir%\system32\OEM\FabrikamLogo.bmp

    **引用︰**OEM 徽标文件必须以.bmp 格式和 120px x 120px 大小。 请参见窗口指导系统制造商 OEM 徽标的详细信息。

    ![OEM 徽标详细信息](Images/oem-logo-details.png)

1.  若要显示 OEM 特定桌面背景图片，图像文件必须放置在 %windir%\system32\OEM\**Fabrikam.bmp** 目录。 验证在 oobeSystem 所对应的应答文件中的路径是相同&gt;Microsoft Windows 外壳程序安装&gt;主题&gt;DesktopBackground 属性。 请参阅下面要添加答案文件中的桌面背景图像。

    ![添加桌面背景](Images/add-desktop-background.png)

#### <a name="modify-start-layout"></a>修改开始布局

在 Windows 10 开始麻将牌布局提供 Oem 追加默认开始布局包括 Web 链接、 辅助磁贴、 Windows 桌面应用程序和通用的 Windows 应用程序图块的能力。 Oem 可以使用此布局，使其适用于多个地区或市场而无需复制了大量的工作。 另外，Oem 可以添加最多三个默认的系统区域中，其中包括重要的或经常访问系统位置的用户提供系统驱动列表 o 中的常用应用程序部分应用程序和最近安装的应用程序。

1.  创建 Layoutmodification.xml。

    注意︰ 建议如符合本指南 （仅限示例） 样本与样本上**USB B**\StartLayout\layoutModification.xml 开始。

    示例 LayoutModification.xml 显示两组称为"Fabrikam 组 1"和"Fabrikam 组 2"，其中包含国家/地区设备匹配所指定区域中应用的拼贴 （在这种情况下，区域是德国和美国）。 每个组包含三个拼贴，您需要根据您想要开始锁定该图块使用的各种元素。

    创建 LayoutModification.xml 文件时，请牢记以下︰

    - 如果您不知道应用程序的应用程序用户模型 ID 固定使用**开始︰ DesktopApplicationTile**标记的 Windows 桌面应用程序，您需要在第一次启动之前传统 「 开始 」 菜单目录下创建一个.lnk 文件。

    - 如果**开始︰ DesktopApplicationTile**标记用于固定传统.url 的快捷方式启动，必须创建.url 文件，并将此文件添加到 「 开始 」 菜单目录前第一次启动传统。

    对于上述的情况中，可以使用以下目录放置.url 或.lnk 文件︰

    - %APPDATA%\Microsoft\Windows\Start Menu\Programs\

    - %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs\

1.  将 LayoutModification.xml 文件保存。

2.  将 LayoutModification.xml 文件添加到 Windows 映像。 您需要将文件放在第一次启动之前以下特定位置。 如果该文件存在，则应当替换图像中已包含 LayoutModification.XML。

        Copy E:\StartLayout\layoutmodification.xml c:\mount\windows\users\default\AppData\Local\Microsoft\Windows\Shell\

    E︰ 所在的驱动器号的 USB b。

1.  如果您锁定要求.url 或.lnk 文件的图块，请将文件添加到以下的传统开始菜单目录︰

    1.  %APPDATA%\Microsoft\Windows\Start Menu\Programs\

    2.  %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs\

            Copy e:\StartLayout\Bing.url "C:\mount\windows\ProgramData\Microsoft\Windows\Start Menu\Programs\"

            Copy e:\StartLayout\Paint.lnk "C:\mount\windows\ProgramData\Microsoft\Windows\Start Menu\Programs"

            Copy E:\StartLayout\Bing.url "C:\mount\windows\users\All Users\Microsoft\Windows\Start Menu\Programs"

            Copy E:\StartLayout\Paint.lnk "C:\Mount\Windows\Users\All Users\Microsoft\Windows\Start Menu\Programs"

    注意︰ 如果不创建 LayoutModification.xml 文件并继续使用启动无人参与的设置，操作系统将使用无人参与的答案文件并采取前 12 SquareTiles 或 DesktoporSquareTiles 中指定的设置无人参与文件。 系统将自动在新创建的组的这些图块末尾开始。 前六个拼贴都放置在 OEM 的第一组中，并且第二组 6 个拼贴都放在第二个的 OEM 组。 如果在无人参与文件中指定 OEMName，则此元素的值用于命名将要创建的 OEM 组。

#### <a name="modify-the-answer-file"></a>修改应答文件

系统构建商可能想要通过无人参与文件进行其他自定义设置。 在 USB B 样本无人参与文件包含其他常见的自定义设置。

    Copy /y E:\AnswerFiles\Unattend.xml C:\Mount\Windows\Windows\Panther

其中 E:\ 是 USB b。

### <a name="optimize-winre"></a>优化 WinRE

1.  增加 scratchspace 大小。

        Dism /image:c:\mount\winre /set-scratchspace:512

1.  清理未使用的文件并减少 winre.wim 的大小

        Dism /image:"c:\mount\winre" /Cleanup-Image /StartComponentCleanup /Resetbase

### <a name="unmount-images"></a>卸载映像

1.  关闭所有应用程序可以访问的文件从图像

2.  提交更改并卸载 Windows RE 映像︰

        Dism /Unmount-Image /MountDir:"C:\mount\winre" /Commit

    其中 C 是驱动器的包含图像的驱动器号。

    此过程可能需要几分钟的时间。

1.  使已更新的 Windows RE 映像的备份副本。

    疑难解答︰ 如果看不到的指定目录下的 winre.wim，使用下面的命令将文件设置为可见︰

        attrib -h -a -s C:\mount\windows\Windows\System32\Recovery\winre.wim

        Dism /export-image /sourceimagefile:c:\mount\windows\windows\system32\recovery\winre.wim /sourceindex:1 /DestinationImageFile:e:\images\winre_bak.wim

        Del c:\mount\windows\windows\system32\recovery\winre.wim

        Copy e:\images\winre_bak.wim c:\mount\windows\windows\system32\recovery\winre.wim

    出现提示时，为文件指定**F**

1.  检查 Windows RE 映像的新大小。

            Dir "C:\mount\windows\Windows\System32\Recovery\winre.wim"

    使用以下分区布局大小指导来确定以 createpartitions-您恢复分区的大小&lt;固件&gt;.txt 文件。 将 winre.wim 复制到隐藏分区后的剩余可用空间量。

    请有关详细信息，参阅[磁盘分区规则](https://technet.microsoft.com/library/hh824839.aspx#DiskPartitionRules)。

    - 如果小于 500 MB 的分区，必须至少 50 MB 的可用空间。

    - 如果分区是 500 MB 或更大，它必须具有至少 320 MB 的可用空间。

    - 如果分区大于 1 GB，我们建议，它应该有至少 1 GB 的空闲空间。

            rem == Windows RE tools partition =============== 
            create partition primary size=500

    可选︰ 本部分假定您希望保密的 winre.wim 在 install.wim，使您的语言和驱动程序的同步。 如果您想要在工厂车间，节省时间和您单独确定管理这些图像，您可能更愿意拉 winre.wim 图像并将其分别应用。

1.  提交更改并卸载 Windows 映像︰

        Dism /Unmount-Image /MountDir:"C:\mount\windows" /Commit
 
    其中 C 是驱动器的包含图像的驱动器号。

    此过程可能需要几分钟。

## <a name="deploy-the-image-to-new-computers-windows-installation"></a>将映像部署到新的计算机 （Windows 安装）

1.  在技术人员计算机上，找到 USB-B/部署中的下列文件。 请参阅[创建我 USB-B](#creating-my-usb-b)来创建，并将这些文件放在正确的路径。 

    ![查找 USB 文件](Images/locate-usb-files.png)

2.  参考计算机启动并连接 USB a。

3.  WinPE 启动后，连接 USB b。

4.  输入开始 Diskpart 类型*diskpart*和命中。 然后键入*列表卷*来识别 USB B 卷标 (例如︰ e:\)。 

        E:\Deployment\Walkthrough-Deploy.bat E:\Images\ModelSpecificImage.wim

    注意︰ 有几个脚本中的暂停。 您可以应用操作提示 Y/N，如果这是一种精简的操作系统部署。

1.  注意︰ 仅使用精简的操作系统基于闪存驱动器设备因为紧凑 OS 性能取决于存储设备功能。 精简的操作系统不建议在旋转设备上。 有关详细信息，请参阅[压缩的操作系统](compact-os.md)。

    删除 USB A 和 USB-B，然后键入︰

        Exit

## <a name="update-images-manually-by-using-audit-mode-online-servicing"></a>使用审核模式 （在线服务） 手动更新图像

重要说明︰ 将计算机连接到 internet 不推荐在生产阶段。 不建议在审核模式中从 Windows Update 获取更新。 在审核模式下，这很可能会生成通用化 + syspreping 计算机时出错。

1.  在审核模式下，默认情况下，可以启动 Windows，在泛化过程删除用户配置文件设置。

2.  如果安装 Office，请参阅[预加载 Microsoft Office 单个图像 v15.4 OPK](#preload-microsoft-office-single-image-v15.4-opk) Microsoft Office 单个图像 v15.4 或[预加载 Microsoft Office 2016年](#preload-microsoft-office-2016)办公室 2016 年。

### <a name="preload-microsoft-office-2016"></a>预加载 Microsoft Office 2016 年

本指南提供有关如何使用 Office 部署工具预办公室 2016年安装到运行 Windows 操作系统的设备许可的原始设备制造商 (Oem) 的信息。

注意︰ 本指南不覆盖 oem 在日本的 PIPC 方案。 

#### <a name="prepare-office-files-on-technician-pc"></a>在技术人员计算机上的 Office 文件准备

从 X20 92403 办公室 2016 v16 部署工具获取 OEM OPK 从 Office 部署工具。

1.  对于 OEM OPK\Software-OEM\x20 92404.img 的 DVD\X20 92404 软件 DVD5 办公室 2016 v16 部署工具装入 X20 92403 办公室 2016 v16 部署工具。
2.  已装入的驱动器的文件复制到 USB-B （其中 E:\ 是驱动程序号 USB-B） E:\OfficeV16。
3.  双击 e:\Officev16\officedeploymenttool.exe。
4.  提供要提取的文件 E:\Officev16 文件夹路径。

    Setup.exe 和 configuration.xml 到 E:\Officev16 提取。

    ![安装程序和 configuration.xml](Images/setup-and-configuation.png)
    
    获取所需的语言; 办公室 v16此示例使用 Engish X20 39283 Office 2016 v16 32 位 X64 英语 OPK。
    
5. 将 Office 文件夹复制从装入的驱动器 X20 39283 Office 2016 v16 32 位 X64 英语 OPK\Software-DVD\X20 37728 软件 DVD5 办公室专业 2016 32 64 英语 C2ROPK Pro HS HB OEM\X20-37728.img USB-B （其中 E:\ 是 USB-B 的驱动器号） 为 E:\OfficeV16。

    ![Office 文件夹](Images/office-folder.png)
    
    [可选]如果应用语言界面包时，您可能需要添加语言界面包办公室 2016 年也。 下面的示例将显示与应用的语言界面包。    

6. 记事本 E:\Officev16\ConfigureO365Home.xml

7. 添加语言 ID，然后验证源路径，如下面的屏幕快照中所示。

    ![语言 ID](Images/language-id.png)
    
8. 关闭并保存 ConfigureO365Home.xml。

9. 以管理员身份打开提升的命令提示符。

10. 从 E:\Officev16，键入并运行 setup.exe /download ConfigureO365Home.xml:

    CD E:\Officev16 Setup.exe /download ConfigureO365Home.xml
    
    这将下载德语和日语语言包。
    
11. 键入运行 echo %错误等级 %并验证返回代码是 0。

12. 从技术人员计算机中拔下 USB-B。 

#### <a name="install-office-2016-on-reference-pc"></a>在参考计算机上安装 Office 2016

1. 参考计算机，在审核模式中插入 USB-B。
2.  驱动器号查找 USB-B;对于本示例 USB-B 是 E:\。
3.  记事本 ConfigureO365Home.xml。
4.  配置源路径以指向 USB B E:\Officev16。

    ![配置源路径](Images/configure-source-path.png)
    
    注意︰ 唯一需要在 configuration.xml 文件中指定的产品 ID 是 O365HomePremRetail。 如果用户输入另一个产品密钥，如面向 Office 家庭及学生 2016年然后 Office 将自动配置为与该密钥关联的产品。
    
5.  关闭并保存 ConfigureO365Home.xml。
6.  打开命令提示窗口，定位到 d:\Officev16。
7.  类型：

    Setup.exe 配置 ConfigureO365Home.xml /

#### <a name="pin-office-tiles-to-the-start-menu"></a>附到 「 开始 」 菜单的办公室拼贴

您必须锁定到 「 开始 」 菜单的办公室拼贴，否则 Windows 将在 OOBE 引导阶段删除 Office 文件。

注意︰ 您必须使用至少 Windows 10 版本 10.0.10586.0。 使用早期版本的 Windows 10，以下步骤不起作用。

1. 打开一个命令提示符并键入︰

        notepad C:\Users\Default\AppData\Local\Microsoft\Windows\Shell\layoutmodification.xml.
        
2. 添加&lt;AppendOfficeSuiteChoice 选择 ="Desktop2016"/&gt; layoutmodification 为您请参阅下面的示例中突出显示︰

    ![修改布局](Images/layoutmodification.png)

    注意︰ 选择特性是新的。 这样，不同版本的 Office 可以在同一时间被固定到开始屏幕。 目前，Desktop2016 是唯一有效的值。 在将来将提供其他值。

3. 关闭并保存 layoutmodification.xml。

    注意︰ 出于恢复目的而 layoutmodification.xml 将需要在恢复过程中被复制。 
    
4.  打开一个命令提示符并键入︰

        copy C:\Users\Default\AppData\Local\Microsoft\Windows\Shell\layoutmodification.xml c:\recovery\OEM   

    一旦机器经过 OOBE 之后引导至桌面，开始菜单将具有这些附加以下图中所示的三个拼贴︰ 
    
    ![办公室的图块固定到开始菜单](Images/office-tiles-pinned-to-start-menu.png)
    
####  <a name="configure-the-setup-experience-for-the-user"></a>配置用户的安装体验   

在设备上安装 Office 之后，您还需要配置用户的安装体验。 这是体验用户可以看到他们时第一次在设备上打开 Office 应用程序。 这也是为了确保 Office 正确授权和激活。

|   安装模式  | 说明   |
|---------------|---------------|
|   OEM         | 在此模式下，客户可以选择重试、 购买或使用现有帐户、 PIN 或产品密钥激活 Office。 这种模式下不支持 Office (AFO) 或 AFO 后期绑定激活。 因此，如果您选择这种模式下，您需要向客户提供一个激活卡 （以前称为产品密钥卡或 Microsoft 产品标识符 (MPI) 卡）。 |
|   OEMTA       |   此模式支持尝试、 购买或激活的 OEM 模式以及支持 AFO 和 AFO 经验后期绑定。 该模式通过设备的 Windows 产品密钥，这意味着客户不需要输入一个 5 x 5 产品密钥代码支持 Office 激活。 |


OEM 模式-提供用户激活卡
1.  在命令提示符下转到驱动器盘符的 USB-B\Officev16
2.  键入并运行︰ 

    oemsetup.cmd 模式 = OEM

OEMTA 模式-激活是通过设备的 Windows 产品密钥。

1. 键入并运行︰
 
    oemsetup.cmd 模式 = OEMTA 引用 =####

### <a name="preload-microsoft-office-single-image-v154-opk"></a>预加载 Microsoft Office 单个图像 v15.4 OPK

Microsoft Office 下载单个图像从[OEM 合作伙伴中心](http://www.microsoft.com/OEM/en/installation/downloads/Pages/office-single-image-v15-opk.aspx)的 v15.4。

1.  打开提升的命令提示符。

2.  OPK 的内容复制到一个目录，将 OfficeSingleImagev15.4InstallationDirectory。

3.  导航到安装目录。 安装目录是包含下图所示的文件的文件夹。

        Cd C:\<OfficeSingleImagev15.4InstallationDirectory>

    ![安装目录](Images/installation-directory.png)

    重要提示︰ OPK 安装过程是相同的运行 32 位操作系统和 64 位操作系统的计算机。 您可以预先加载 32 位版本的 Office 2013 运行 32 位或 64 位操作系统的计算机上。 您可以预先加载 Office 2013 仅在运行 64 位操作系统的计算机上的 64 位版本。 若要使外接程序或第三方应用程序，预加载*只有 32 位版本*的 OPK 32 位和 64 位计算机上可能存在兼容性问题。

1.  运行 oemsetup.en-我们编写的脚本。

        oemsetup.en-us.cmd

1.  安装完成后，Microsoft Office 单个图像 v15.4 OOBE 应用程序图块将被放在应用程序视图上。

2.  对针到开始屏幕，请参阅*4.2.4 节锁定桌面应用程序启动屏幕和任务栏*，然后输入到**Office.lnk** &lt;AppIdOrPath&gt;属性。 请参阅此自定义已 USB-B\AnswerFiles\UnattendSysprep.xml 答案文件中采用的地方。

### <a name="prepare-the-system-for-recovery-with-push-button-reset"></a>准备用于恢复的下压按钮重置系统

请有关详细信息，参考[按钮重置](push-button-reset-overview.md)和[Windows 恢复环境 (Windows RE)](windows-recovery-environment--windows-re--technical-reference.md)和[硬盘驱动器和分区](hard-drives-and-partitions.md)。

1.  准备扫描状态工具。

    如果您使用**x64** Windows 10 图像︰

        md E:\ScanState_amd64

        copy "C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\User State Migration Tool\amd64" E:\ScanState_amd64

        copy /Y "C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Setup\amd64\Sources" E:\ScanState_amd64

    如果您使用 Windows 10 的**x86**映像︰

        md E:\ScanState_x86

        copy "C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\User State Migration Tool\x86" E:\ScanState_x86

        copy /Y "C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Setup\x86\Sources" E:\ScanState_x86

    其中 e︰ 是 USB-B 的驱动器号。

1.  创建配置文件。

    配置文件可用于还原和 PBR 过程中排除注册表项和文件。

    重要事项︰ 本部分包括解决已知问题的方法在 Windows 10。 您必须应用此解决办法以避免 PBR 过程中的问题。 

    在某些情况下，Windows Defender 设置和检测历史记录可能捕获到的自定义软件包扫描状态工具。 这可能会导致冲突的文件，因为恢复过程失败，将导致计算机重新启动并重复输入**安装 Windows**阶段。

    注意︰ 使用以前生成的 pbr_config.xml 配置文件。

1.  创建恢复软件包。

    使用扫描状态工具捕获到资源调配包，安装自定义项并将其保存在文件夹 c:\Recovery\customizations。 本文档使用从 USB B\Recovery\RecoveryImage 示例创建扫描状态包。

    重要提示︰ 使用 PBR 扫描状态包必须是存储在 C:\Recovery\Customizations 文件夹中的.ppkg 文件或 PBR 将不能恢复软件包。

2.  创建恢复的 USB B\Recovery\RecoveryImage OEM 文件夹和复制内容。

        Copy E:\Recovery\recoveryimage c:\recovery\OEM

        Copy E:\StartLayout\\*.\* c:\recovery\OEM

1.  运行扫描状态实用程序来收集应用程序和自定义项。

    如果您使用**x64** Windows 10 图像︰

        E:\ScanState_amd64\scanstate.exe /apps /ppkg C:\Recovery\Customizations\apps.ppkg /config:c:\Recovery\OEM\pbr_config.xml /o /c /v:13 /l:C:\ScanState.log

    如果您使用 Windows 10 的**x86**映像︰

        E:\ScanState_x86\scanstate.exe /apps /ppkg C:\Recovery\Customizations\apps.ppkg /config:C:\Recovery\OEM\pbr_config.xml /o /c /v:13 /l:C:\ScanState.log

    E︰ 所在的驱动器号的 USB b。

1.  创建扩展脚本来还原其他设置和自定义项。

    配置扩展点，可以自定义的按钮重置体验。 这使您可以运行自定义脚本、 安装其他应用程序，或保留更多的用户、 应用程序或注册表数据。

    示例脚本 EnableCustomizations.cmd PBR 过程中将调用，并将做两件事︰

    一。  将复制 unattend.xml 文件用于初始部署到 \windows\panther 文件夹中。

    b。  将 layoutmodification.xml 复制到系统中。

### <a name="finalize-and-capture-manufacturing-image"></a>确定和捕获制造图像

1.  删除安装文件夹和预加载应用程序所创建的文件。 例如， *C:\Office-SingleImagev15.4-Setup*，和*C:\LIPsToBeInstalled*文件夹。 获取捕获的映像的 Windows 驱动器时，这些文件夹中的存在可能会增加.wim 文件的大小。

2.  如果 Sysprep 处于打开状态，请将其关闭并打开提升的命令提示符。

3.  将 winre 备份复制到 windows。

        Copy e:\images\winre_bak.wim c:\windows\system32\recovery\winre.wim

1.  恢复文件夹，以便恢复到复制 unattend.xml unattend 下压按钮重置期间设置。

        Copy USB-B\answerfiles\unattendsysprep.xml c:\Recovery\OEM\unattend.xml

1.  连接到参考计算机的 USB-B。

2.  一般化映像时使用应答文件，其中反映[更新手动通过使用审核模式 （在线服务） 的图像](#update-images-manually-by-using-audit-mode-online-servicing)一节中所做的更改。

    这些更改包括 Microsoft Office 组件图块固定到开始屏幕。

        Cmd /c C:\Windows\System32\Sysprep\sysprep /unattend:c:\Recovery\OEM\Unattend.xml /generalize /oobe /shutdown

1.  参考计算机启动并连接 USB a。

2.  已启动 WinPE 后连接 USB b。

3.  输入开始 Diskpart 类型*diskpart*和命中。 然后键入*列表卷*标识 Windows 安装卷标记为"窗口"的卷标 (例如︰ e:\)。 最后键入*退出*以退出 Diskpart。

4.  开始清理的图像。

    重要︰ 默认情况下，非主要更新 （如 ZDPs 或 LCUs） 则不会还原。 若要确保在制造过程中预安装的更新不放弃恢复后，他们应将标记作为永久使用 DISM 中与 /StartComponentCleanup 和 /ResetBase 选项的 /Cleanup-Image 命令。 在恢复期间始终还原更新为永久性标记。 

        MD e:\scratchdir

        dism /Cleanup-Image /Image:e:\ /StartComponentCleanup /resetbase /scratchdir:e:\scratchdir

1.  捕获的映像的 windows 分区。 此过程需要几分钟的时间。

        dism /Capture-Image /CaptureDir:E:\ /ImageFile:F:\Images\ModelSpecificImage.wim /Name:"myWinImageWithMSIUpdated" /scratchdir:e:\scratchdir

    其中，E 是 Windows 和 F 的卷标是 USB B.的卷标

1.  将图像复制到 USB b。 此过程需要几分钟的时间。

        copy E:\ModelSpecificImage.wim H:\Images\

    其中 H 是 USB B.的卷标

    这将覆盖的部分[部署到新计算机的映像](#deploy-the-image-to-new-computers)创建的图像。

## <a name="deploy-the-image"></a>部署映像 

使用部署脚本布局到设备上的分区和应用映像。 USB B\deployment 文件夹中演练 deploy.bat 将分区的设备，根据设备模式。

**重要提示︰ 恢复分区必须是分区后 Windows 分区，以确保 winre.wim 可以保持最新的设备的生命周期内。**

在 Windows 10 版 1511，我们正在更改我们的推荐，以具有放置在操作系统分区后的 WinRE 分区。 这将允许未来增长的 WinRE 分区更新过程。 今天 WinRE 前部的磁盘分区，它的大小可以永远不会更改，因此很难更新时所需的 WinRE。 我们将继续支持有 WinRE 分区位于不同部分的磁盘，但我们鼓励您可以遵循的新建议。

E:\Deployment\walkthrough-deploy.bat E:\Images\BasicImage.wim

注意︰ 有几个脚本中的暂停。 您可以应用操作提示 Y/N，如果这是一种精简的操作系统部署。

注意︰ 只精简的操作系统上使用高端存储设备因为紧凑 OS 性能取决于存储设备功能。 精简的操作系统不建议在旋转设备或大于 32 GB 的存储上。 有关详细信息，请参阅[压缩的操作系统](compact-os.md)。

删除 USB A 和 USB B 输*退出*重新启动您的计算机使用 Windows 10。

## <a name="finalize-deployment"></a>完成部署

1.  一旦将模型特定映像部署到目标计算机，在审核模式下第一次启动与主映像的计算机

    重要提示︰ 为了最小化启动初次 (引导 > 专业化 > OOBE > 启动屏幕) 专用化必须在工厂中完成传递。 专门负责通过将配置硬件的特定信息的 Windows 上运行。

    关于第一项启动时间要求的详细信息，请参阅[Windows 系统构建的策略](http://www.microsoft.com/oem/en/pages/download.aspx?wpid=w_w8_008)。

1.  请注意[通过使用审核模式 （在线服务） 来手动更新图像](#update-images-manually-by-using-audit-mode-online-servicing-)部分的末尾，密封的系统被 OOBE 模式。 请继续执行审核。 如果在 OOBE 引导系统，按 Ctrl + Shift + F3 才能在审核模式下通过 OOBE 和引导。

2.  如果您想要应用其他步骤，如执行 OEM 诊断测试等等，它们在此处适用。

3.  最后，运行 Sysprep 工具 (C:\Windows\System32\Sysprep\sysprep.exe) 和密封系统回到**OOBE**和**关闭**而*没有***通用化**。

4.  系统已准备装运。

    重要提示︰ 如果不使用管理工具如磁盘程序或 Windows 部署服务的图像，制造少量的设备，您可以选择使用以下练习︰

    1. 您可以制造这些设备的第一启动 WinPE-插入 USB a。 
    2. 然后，插入 USB B 最终制造图像包含在其中。 
    3. 运行 Walktrough 部署脚本应用该映像。 
    4. 应用图像后，请按照此完成部署部分中的步骤。 
    5. 现在，该设备就可以随您的最终制造图像和 PBR 功能实现。 
    6. 最后，与其他设备进行复制相同的过程。

## <a name="appendix"></a>附录

### <a name="differences-between-64-bit-and-32-bit-deployment"></a>64 位和 32 位部署之间的差异

建议考虑将制造设备与 32 位部署磁盘空间需求量，根据存储 64 位部署。

本指南中提到的总体部署流程不不同部署 64 位和 32 位。 这些资源创建的只是一些资源版本和方式不同。 下表介绍 x64/x86 区别。

| **不同之处在于**                         | **说明**                                                                                                                                                                                                                                                                              | **相关的部分**                  |
|-----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------|
| 在技术人员计算机上安装了 Windows | 在技术人员计算机上安装 Windows ADK 获取时将根据体系结构的技术人员计算机上的 Windows 安装中 ADK 的部署工具。 简单地说如果 ADK 安装在 Windows x64 上，工具将安装的 64 位版本或进行相反的转换。 | [准备您的实验室环境](#prepare-your-lab-environment)         |
| 创建 WinPE 文件夹结构         | X64 和 x86 体系结构，因此您必须使用不同的命令来创建每个体系结构不同的 WinPE 文件夹之间不同 WinPE。                                                                                                                                                    | [创建可启动 USB 的 WinPE](#create-winpe-bootable-usb) |
| 驱动程序                                 | 不同的体系结构之间不同的驱动程序版本。 如果制造的 64 位的 Windows 映像，请为 32 位 Windows 使用 x64 的驱动程序，反之亦然。                                                                                                                                                   | [添加驱动程序](#add-drivers)         |
| Windows 映像的更新程序包       | 更新包版本间不同的体系结构各不相同。 如果您制造一个 64 位的 Windows 图像请使用 x64 的 32 位 Windows 更新包，反之亦然。                                                                                                                                   | [添加更新程序包](#add-update-packages) |
| 语言界面包                | 如果您使用 x64 安装 x64 嘴唇或如果您将使用 x86 的 Windows 10 图像窗口 10 映像安装 x86 嘴唇。                                                                                                                                                                    | [准备恢复与按钮重置系统](#prepare-the-system-for-recovery-with-push-button-reset)                          |

### <a name="what-you-will-need-and-where-to-get-it"></a>您将需要和从哪里获得它

OEM 需要下载某些包将使用本指南，例如 Microsoft Office 单个图像 v15.4 的部署过程开始之前更新包，语言界面包等等... 下面是下载和他们下载它们需要的资源/工具包 OEM 的完整列表。

| 资源/工具包  |   在可用    | 相关的部分   |
|---------------|-------------------|-------------------|
| Windows 10 ADK|   [http://www.microsoft.com/en-US/download/details.aspx?id=39982](http://www.microsoft.com/en-US/download/details.aspx?id=39982) | [创建可启动 USB 的 WinPE](#create-winpe-bootable-usb) |
| Windows 10 x64/x86 DVD 介质 （所需的语言） | 您将自定义 Windows 10 媒体获得 Microsoft 授权分销商 | [具有基本的自定义安装 Windows](#install-windows-with-basic-customizations) |
| 默认的 Windows 10 产品密钥 | 默认产品密钥位于**默认产品密钥**选项卡列出的[OEM 合作伙伴中心](https://www.microsoft.com/OEM/en/products/windows/Pages/windows-10-build.aspx#fbid=nV7H02bHHiv) | [自定义答案文件](#customize-the-answer-file) |
| 语言界面包 | 嘴唇位于[OEM 合作伙伴中心](https://www.microsoft.com/OEM/en/installation/downloads/Pages/Windows-10-v1511-Language-Interface-Packs.aspx#fbid=nV7H02bHHiv)列出**Lip**选项卡 | [准备用于恢复的下压按钮重置系统](#prepare-the-system-for-recovery-with-push-button-reset) |
| 更新包的 11 月到 2015 的重要更新程序列表、 KB 3118754 | 获取从[Microsoft 更新目录](http://catalog.update.microsoft.com/v7/site/Home.aspx)下载更新包。 在有关部分中提到下载更新程序包的详细的过程。 | [添加语言界面包](#add-language-interface-packs) |
| Microsoft Office v15.4 | 通过下载从[OEM 合作伙伴中心](http://www.microsoft.com/OEM/en/installation/downloads/Pages/office-single-image-v15-opk.aspx)获得 Microsoft Office v15.4 | [预加载 Microsoft Office 单个图像 v15.4 OPK](#preload-microsoft-office-single-image-v15-4-opk) |


## <a name="references"></a>参考

[Windows 系统构建的指导原则](http://www.microsoft.com/oem/en/pages/download.aspx?wpid=w_w8_129)

[Windows 系统构建的策略](http://www.microsoft.com/oem/en/pages/download.aspx?wpid=w_w8_008)


