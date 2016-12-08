---
Description: "可以使用 Windows 图像处理和配置设计器 (ICD) 用户界面创建新的 Windows 10 移动图像和自定义添加设置和某些资产。"
ms.assetid: bf897b96-2ab4-42c0-b825-34e7979b3761
MSHAttr: PreferredLib:/library
title: "使用 Windows ICD 用户界面进行自定义和生成的移动图像"
author: CelesteDG
ms.openlocfilehash: 0ac852099a0c334fc35fd4030dac9d4657b2f5ee
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="use-the-windows-icd-ui-to-customize-and-build-a-mobile-image"></a>使用 Windows ICD 用户界面进行自定义和生成的移动图像


可以使用 Windows 图像处理和配置设计器 (ICD) 用户界面创建新的 Windows 10 移动图像和自定义添加设置和某些资产。

该成像方法要求预装的操作系统套件因此必须具有所有必需的微软操作系统软件包和功能清单文件在您的默认安装路径。 数据配置文件 (BSP.config.xml)，其中包含有关您的主板支持包 (BSP) 的硬件组件程序包的信息，也是必需的。 对于 BSP.config.xml 文件中，您可以︰

-   您下载的 BSP.config.xml 文件用作 BSP 工具包的一部分;

-   从 SoC 供应商运行 BSP 包配置工具并选择驱动程序组件生成您自己的 BSP.config.xml。

## <a name="span-idtobuildamobileimageusingthewindowsicduispanspan-idtobuildamobileimageusingthewindowsicduispanbuild-a-mobile-image-using-the-windows-icd-ui"></a><span id="to_build_a_mobile_image_using_the_windows_icd_ui"></span><span id="TO_BUILD_A_MOBILE_IMAGE_USING_THE_WINDOWS_ICD_UI"></span>生成使用 Windows ICD 用户界面的移动图像


本演练演示如何使用 Windows ICD 用户界面自定义、 生成和闪烁移动的图像。

1.  从 Windows ICD 起始页中，选择**新的 Windows 映像自定义项**。

    或者，也可以从**文件**菜单中选择**新建项目...** 。

2.  在**输入项目详细信息**窗口中，为项目指定**名称**和**位置**。 您还可以输入简短**说明**来描述您的项目。

3.  单击**下一步**。

4.  如果您从开始页中创建项目，请跳过此步骤。

    在**选择工作流项目**窗口中，**成像**从列表中选择可用的项目工作流，然后单击**下一步**。

5.  在**选择图像源格式**窗口中，选择**Windows 映像基于 Microsoft 程序包**，，然后单击**下一步**。

    系统将提示您指定一个 BSP.config.xml 文件。

6.  在**选择硬件组件的驱动程序**窗口中，单击**浏览**要启动文件资源管理器并搜索您的 BSP.config.xml 文件的位置。

7.  单击**完成**。

    这样会加载所有自定义设置，您可以配置基于所选的 Windows 版本。 所有可用的自定义加载后，您可以查看**自定义页**。

8.  在**自定义页**中，选择您要从**可用的自定义**窗格中自定义的设置。

    在本演练中，列表，请参见[配置自定义 Windows ICD UI 中的](#configure-customizations-in-the-windows-icd-ui)作为示例，我们使用的设置。 在完成后配置设置，请转到下一步。

9.  虽然可选，导出设置包封装刚配置的设置，并且允许您重新使用所有或大多数其他项目的自定义项。

    为此，请单击主菜单中的**导出**下拉列表，选择**资源调配包**，添加所需的程序包信息。

    -   **名称**-包，例如，使用名称*Contoso\_ppkg*。
    -   **ID** — 自动生成包 GUID。
    -   **所有者**— 包所有者。 设置为*OEM*。
    -   **版本**的版本信息。 这是最新的包版本号或"1.0"预先填充。 它可以将其设置为默认情况下， *1.0*，尽管您可以将其设置为所需的任何版本的离开。
    -   **秩**-包秩，这是一个 0 到 99 （含） 之间的值。 将它设置为默认值*0*。

    直到转到**生成资源调配包**屏幕，请单击**下一步**。 单击**生成**以生成包，然后单击**完成**。

10. 从主菜单中选择**创建**，然后选择**FFU**。

11. 在**选择图像类型**屏幕中，选择图像类型**测试**。

    尽管有其他图像类型，测试图像类型时好尚未最终图像并在图像中您仍在测试各个组件。 图像也已解锁，并不包含任何安全执行进行。

12. 单击**下一步**。

13. 在**描述图像**屏幕中，选择想要包括图像的一部分的语言。

    如果您有机会去[第 1 部分︰ 经典移动部署](lab-1--classic-mobile-deployment.md)，在此步骤中设置是类似于将[配置的 OEMInput 文件](configure-the-oeminput-file.md)中设置设备语言方式。

    -   **用户界面语言**-这些是安装在设备上的显示语言。

        选择*en gb*， *en-我们*， *es-es*、 *fr fr*和*中文 cn*。

    -   **键盘语言**-这些是在设备上打字时使用文本更正，并建议其他键盘语言。

        选择*en-我们*。

    -   **语音语言**-这些是您想要在您的设备上安装的语音语言。

        选择*en-我们*。

14. 因为我们在**用户界面语言**中选择了多种语言，我们必须选择用户将首次开启时，将使用设备的默认显示语言。 若要执行此操作，选择**引导语言**，选择您要设置的默认设备语言。 例如，将它设置为*en-我们*。

15. 若要设置的国家或地区，选择**引导区域设置**并选择默认区域或国家/地区的区域设置。 任何区域设置可以用作区域的格式，但使用仅国家 (GeoID) 值。 例如，将它设置为*en-我们*。

16. 单击**下一步**。

17. 要更改保存文件的位置，请单击下**选择要保存文件的位置**的**浏览...** 。

    您可以更改的位置保存文件，但通常情况下的默认位置是很好。

18. 可选项。 如果您创建了某个咖啡馆文件的以下[配置自定义设置](configure-customization-settings.md)，可以通过选择**自定义答案文件 （可选）**在**浏览...**并指定保存咖啡馆的位置包括这。

    例如， *c:\\Contoso\\的自定义\\MobileCustomizations.xml*。

19. 若要更改要用来保存图像的默认位置，请单击**浏览...**以启动文件资源管理器并指定一个新位置。

    要使用的默认位置，请单击**下一步**。

20. 单击**生成**以开始构建图像。 项目信息将显示在生成页上，进度条会指示生成的状态。

    如果您需要取消该生成，请单击**取消**。 这取消当前的构建过程，关闭该向导，并重新转到**自定义页**。

21. 在图像生成过程中，生成输出窗口中显示生成过程中发生的情况很多。 此窗口显示︰

    -   在构建映像时可能会出现的警告。

    -   详细生成消息，以指示在图像内的阶段生成过程。

    -   例如，当输入的文件具有架构错误或图像的生成会失败的错误消息。

    如果生成失败，则将显示一条错误消息。 您可以查看生成日志以确定问题，通过单击**记事本中的视图**。

    如果您的生成成功，则将显示图像和它的位置的名称。

    -   如果您选择，可以通过选择不同的图像类型，选择不同的语言，然后启动另一个生成重新生成图像。 要做到这一点，**回**以选择要进行更改，请单击，然后单击**下一步**要启动另一个生成。

    -   引导设备到图像或 FFU 下载模式。 为图像或 FFU 强制手机下载模式手动按下并释放电源按钮以重新启动电话，然后立即按下并保持向上按钮卷。 请注意仅在初始 FFU 已经刷新到电话之后，此选项才可用。

        如果这不起作用，请检查并按照闪烁 SoC 供应商提供的说明进行操作的设备。

    -   如果您已准备 flash 构建到您的设备图像，单击**闪烁**和选择目标设备，以闪存 FFU。 如果找不到设备的可用目标设备列表中列出，请单击**刷新**。

        如果要快闪到设备后面的图像，请按照[部署到移动设备的图像](#deploy-an-image-to-a-mobile-device)当准备好快闪存储到您的设备图像。

        它将需要几分钟将完全刷新为设备的图像。 一旦完成闪烁，完成设备安装和验证您的自定义显示为图像的一部分。

    -   如果执行此操作，请单击**完成**关闭此向导并返回到**的自定义页面**。

## <a name="span-idconfigurecustomizationsinthewindowsicduispanspan-idconfigurecustomizationsinthewindowsicduispanconfigure-customizations-in-the-windows-icd-ui"></a><span id="configure_customizations_in_the_windows_icd_ui"></span><span id="CONFIGURE_CUSTOMIZATIONS_IN_THE_WINDOWS_ICD_UI"></span>配置 Windows ICD UI 中的自定义项


**请注意** 配置自定义项使用 Windows ICD 时, 不使用**图像的时间设置**，而应使用**运行时设置**。 如果您配置的图像的时间设置，这将导致由于设置冲突错误，如果 WPAF 和 MCSF 咖啡馆中配置该设置。

 

如果您没有这样做，您必须首先创建 LayoutModification.xml 文件，如中所示[配置开始布局](configure-the-start-layout.md)之前使用此部分中的步骤。

**若要配置开始布局**

1.  在**可用的自定义**窗格中的在 Windows ICD，展开**运行时设置**，选择**开始**，，然后选择**StartLayout**。

2.  在中间窗格中，单击**浏览**以打开文件资源管理器。

3.  在文件资源管理器窗口中，导航到保存 LayoutModification1.xml 从步骤 1; 位置例如， *c:\\Contoso\\的自定义*。

4.  选择 LayoutModification1.xml，然后单击**打开**。

    这将**StartLayout**的值设置，该设置应显示在**所选自定义项**页。

企业策略和注册设置是一些只能通过 Windows 资源调配使用自定义设置。 在这里，我们将配置这些策略的几个以包括作为映像的一部分。 有关其他可配置的策略的详细信息，请参阅 （对于 Windows 设置设置） 的[策略](https://msdn.microsoft.com/library/windows/hardware/dn965797)。 请注意，Windows 资源调配设置主题不提供详细的说明每个策略;相反，每个主题的链接[策略 CSP](https://msdn.microsoft.com/library/windows/hardware/dn904962)中的更多详细信息。

**要设置的策略**

1.  在**可用的自定义**窗格中，展开**运行库设置**，选择**策略**。

2.  查找**策略/DeviceLock** ，并将**MaxInactivityTimeDeviceLock**设置为"15"。

    此参数指定该设备空闲了 15 分钟后，该设备将成为 PIN 或密码锁定。

3.  查找**策略/DeviceLock** ，并将**ScreenTimeoutWhileLocked**设置为"15"。

    这指定持续时间，以秒为单位的屏幕超时锁定屏幕上。 对于此示例，持续时间为 15 秒。

## <a name="span-iddeployanimagetoamobiledevicespanspan-iddeployanimagetoamobiledevicespanspan-iddeployanimagetoamobiledevicespandeploy-an-image-to-a-mobile-device"></a><span id="Deploy_an_image_to_a_mobile_device"></span><span id="deploy_an_image_to_a_mobile_device"></span><span id="DEPLOY_AN_IMAGE_TO_A_MOBILE_DEVICE"></span>将映像部署到移动设备


如果您推迟后它构建的闪烁的图像的设备，请执行以下步骤。

1.  引导设备到图像或 FFU 下载模式。 为图像或 FFU 强制手机下载模式手动按下并释放电源按钮以重新启动电话，然后立即按下并保持向上按钮卷。 请注意仅在初始 FFU 已经刷新到电话之后，此选项才可用。

    如果这不起作用，请检查并按照闪烁 SoC 供应商提供的说明进行操作的设备。

2.  使用 USB 电缆，将您的电话连接到主机。

3.  单击**部署**从主菜单，然后选择**设备连接到 USB** FFU 映像部署到该设备。

4.  在**选择 FFU 图像**窗口中，单击**浏览...**以启动文件资源管理器，然后选择要与目标设备，快闪 FFU，然后单击**下一步**。

5.  从列表中选择目标设备或驱动器。 如果未列出您的设备或驱动器，请单击**刷新**。

6.  单击**下一步**。

7.  在**部署到设备**窗口中，选择**Flash**开始闪烁图像。

8.  单击**完成**以关闭**部署**页。

 

 



