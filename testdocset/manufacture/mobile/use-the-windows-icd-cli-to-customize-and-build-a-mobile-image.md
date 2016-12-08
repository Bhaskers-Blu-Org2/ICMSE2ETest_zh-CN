---
Description: "Windows 图像处理和配置设计器 (ICD) 命令行界面 (CLI) 可用于生成新的 Windows 10 移动图像。"
ms.assetid: 941023d3-14d5-415f-817b-a48ac2a4ec87
MSHAttr: PreferredLib:/library
title: "使用 Windows ICD CLI 可以自定义和增强的移动图像"
author: CelesteDG
ms.openlocfilehash: f8c138400079c3a4e5abc05e1b24cdbb1ccca693
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="use-the-windows-icd-cli-to-customize-and-build-a-mobile-image"></a>使用 Windows ICD CLI 可以自定义和增强的移动图像


Windows 图像处理和配置设计器 (ICD) 命令行界面 (CLI) 可用于生成新的 Windows 10 移动图像。

该成像方法要求预装的操作系统套件因此必须具有所有必需的微软操作系统软件包和功能清单文件在您的默认安装路径。 您还需要一个 BSP.config.xml 文件，其中包含有关您的主板支持包 (BSP) 的硬件组件程序包信息或者您可以使用 OEMInput.xml 文件。

如果您使用的 BSP.config.xml 文件，您可以︰

-   您下载的 BSP.config.xml 文件用作 BSP 工具包的一部分;

-   从 SoC 供应商运行 BSP 包配置工具并选择驱动程序组件生成您自己的 BSP.config.xml。

## <a name="span-idcreateawpafwithmultivariantsupportspanspan-idcreateawpafwithmultivariantsupportspanspan-idcreateawpafwithmultivariantsupportspancreate-a-wpaf-with-multivariant-support"></a><span id="Create_a_WPAF_with_multivariant_support"></span><span id="create_a_wpaf_with_multivariant_support"></span><span id="CREATE_A_WPAF_WITH_MULTIVARIANT_SUPPORT"></span>创建 WPAF multivariant 的支持


Multivariant 提供了一个用于创建单个图像，它可以适用于多个市场的一般机制。 您可以使用它来动态配置在运行时基于移动运营商和区域/国家/地区的语言、 品牌和网络设置。

与 Windows ICD 的用户界面，可用于 Windows ICD CLI 为创建图像，具有 multivariant 的支持。 为此，首先必须编辑 Windows 资源调配的应答文件 (WPAF)，customizations.xml，并将**目标**和**变体**部分添加到该文件。 [创建具有 multivariant 设置的自动配置软件包](https://msdn.microsoft.com/library/windows/hardware/dn916108)提供了有关 Windows 10 和 Windows 支持以及他们的优先事务的条件的列表中的 multivariant 支持的详细信息。 它还提供一个分步示例，在您需要做什么。

在本节中，我们将修改已创建[使用 Windows ICD 用户界面进行自定义和生成的移动图像](use-the-windows-icd-ui-to-customize-and-build-a-mobile-image.md)，包括**目标**和**variant 类型的值**的部分，以支持 multivariant 的 customizations.xml 文件。 如果您要构建一个 variant 类型的值图像，可以跳过此部分。

1.  找到该资源调配的包文件，customizations.xml。 如果未更改默认的项目位置，您可以找到在包*&lt;驱动器︰&gt;*\\用户\\*&lt;用户\_名称&gt;*\\文档\\Windows 图像处理和配置设计器 (WICD)\\*&lt;项目\_名称&gt;*。

2.  使用 XML 或文本编辑器中打开 customizations.xml 文件。

    下面的示例演示在[使用 Windows ICD 用户界面进行自定义和生成的移动图像](use-the-windows-icd-ui-to-customize-and-build-a-mobile-image.md)中创建的 customizations.xml 文件的内容。

    ```XML
    <?xml version="1.0" encoding="utf-8"?>
    <WindowsCustomizations>
      <PackageConfig xmlns="urn:schemas-Microsoft-com:Windows-ICD-Package-Config.v1.0">
        <ID>{239b9121-9f26-42db-8ae2-0d62989caa66}</ID>
        <Name>Contoso_ppkg</Name>
        <Version>1.0</Version>
        <OwnerType>OEM</OwnerType>
        <Rank>0</Rank>
      </PackageConfig>
      <Settings xmlns="urn:schemas-microsoft-com:windows-provisioning">
        <Customizations>
          <Common>
            <Policies>
              <DeviceLock>
                <MaxInactivityTimeDeviceLock>15</MaxInactivityTimeDeviceLock>
                <ScreenTimeoutWhileLocked>15</ScreenTimeoutWhileLocked>
              </DeviceLock>
            </Policies>
            <Start>
              <StartLayout>C:\Contoso\Customizations\LayoutModification1.xml</StartLayout>
            </Start>
          </Common>
        </Customizations>
      </Settings>
    </WindowsCustomizations> 
      
    ```

3.  编辑 customizations.xml 文件并创建一个**目标**分区，描述将处理您的 multivariant 设置的条件。

    下面的示例演示 customizations.xml，若要包括条件**MCC**和**mnc**已修改。 奇偶校验、 该示例一节*创建 MCSF 自定义答案文件*中[配置自定义设置](configure-customization-settings.md)使用同一个虚构 Id 和所使用的条件。

    ```XML
    <?xml version="1.0" encoding="utf-8"?>
    <WindowsCustomizations>
      <PackageConfig xmlns="urn:schemas-Microsoft-com:Windows-ICD-Package-Config.v1.0">
        <ID>{239b9121-9f26-42db-8ae2-0d62989caa66}</ID>
        <Name>Contoso_ppkg</Name>
        <Version>1.0</Version>
        <OwnerType>OEM</OwnerType>
        <Rank>0</Rank>
      </PackageConfig>
      <Settings xmlns="urn:schemas-microsoft-com:windows-provisioning">
        <Customizations>
          <Common>
            <Policies>
              <DeviceLock>
                <MaxInactivityTimeDeviceLock>15</MaxInactivityTimeDeviceLock>
                <ScreenTimeoutWhileLocked>15</ScreenTimeoutWhileLocked>
              </DeviceLock>
            </Policies>
            <Start>
              <StartLayout>C:\Contoso\Customizations\LayoutModification1.xml</StartLayout>
            </Start>
          </Common>
          <Targets> 
            <Target Id="Id_PhoneCo"> 
              <TargetState> 
                <Condition Name="MCC" Value="410" /> 
                <Condition Name="MNC" Value="510" /> 
              </TargetState> 
            </Target> 
            <Target Id="Id_Fabrikam"> 
              <TargetState> 
                <Condition Name="MCC" Value="310" /> 
                <Condition Name="MNC" Value="610" /> 
              </TargetState> 
            </Target>
          </Targets> 
        </Customizations>
      </Settings>
    </WindowsCustomizations> 
      
    ```

4.  在 customizations.xml 文件中，创建两个**款式**的部分︰

    1.  指定每个变量，该变量的**名称**。

    2.  添加一个子**TargetRefs**元素。

    3.  在**TargetRefs**元素中，添加**TargetRef**元素。

    下面的示例显示 customizations.xml 添加 ThePhoneCompany 和 Fabrikam，两个变体，然后使用**TargetRef Id**为使用的每种款式上一步中，我们定义两个**目标 Id**s 后的外观。

    ```XML
    <?xml version="1.0" encoding="utf-8"?>
    <WindowsCustomizations>
      <PackageConfig xmlns="urn:schemas-Microsoft-com:Windows-ICD-Package-Config.v1.0">
        <ID>{239b9121-9f26-42db-8ae2-0d62989caa66}</ID>
        <Name>Contoso_ppkg</Name>
        <Version>1.0</Version>
        <OwnerType>OEM</OwnerType>
        <Rank>0</Rank>
      </PackageConfig>
      <Settings xmlns="urn:schemas-microsoft-com:windows-provisioning">
        <Customizations>
          <Common>
            <Policies>
              <DeviceLock>
                <MaxInactivityTimeDeviceLock>15</MaxInactivityTimeDeviceLock>
                <ScreenTimeoutWhileLocked>15</ScreenTimeoutWhileLocked>
              </DeviceLock>
            </Policies>
            <Start>
              <StartLayout>C:\Contoso\Customizations\LayoutModification1.xml</StartLayout>
            </Start>
          </Common>
          <Targets> 
            <Target Id="Id_PhoneCo"> 
              <TargetState> 
                <Condition Name="MCC" Value="410" /> 
                <Condition Name="MNC" Value="510" /> 
              </TargetState> 
            </Target> 
            <Target Id="Id_Fabrikam"> 
              <TargetState> 
                <Condition Name="MCC" Value="310" /> 
                <Condition Name="MNC" Value="610" /> 
              </TargetState> 
            </Target>
          </Targets> 
          <Variant Name="ThePhoneCompany"> 
            <TargetRefs> 
              <TargetRef Id="Id_PhoneCo" /> 
            </TargetRefs> 
          </Variant> 
          <Variant Name="Fabrikam"> 
            <TargetRefs> 
              <TargetRef Id="Id_Fabrikam" /> 
            </TargetRefs> 
          </Variant> 
        </Customizations>
      </Settings>
    </WindowsCustomizations> 
      
    ```

5.  移从**常见**的部分兼容设置**variant 类型的值**的节。

    **请注意** 每个触发事件无条件地应用驻留在**常规**部分中的设置。

     

    在以下示例中，我们使用`DeviceLock/MaxInactivity`策略下，ThePhoneCompany 变体时`DeviceLock/ScreenTimeoutWhileLocked`策略的移动下 Fabrikam variant 类型的值。

    ```XML
    <?xml version="1.0" encoding="utf-8"?>
    <WindowsCustomizations>
      <PackageConfig xmlns="urn:schemas-Microsoft-com:Windows-ICD-Package-Config.v1.0">
        <ID>{239b9121-9f26-42db-8ae2-0d62989caa66}</ID>
        <Name>Contoso_ppkg</Name>
        <Version>1.0</Version>
        <OwnerType>OEM</OwnerType>
        <Rank>0</Rank>
      </PackageConfig>
      <Settings xmlns="urn:schemas-microsoft-com:windows-provisioning">
        <Customizations>
          <Common>
            <Start>
              <StartLayout>C:\Contoso\Customizations\LayoutModification1.xml</StartLayout>
            </Start>
          </Common>
          <Targets> 
            <Target Id="Id_PhoneCo"> 
              <TargetState> 
                <Condition Name="MCC" Value="410" /> 
                <Condition Name="MNC" Value="510" /> 
              </TargetState> 
            </Target> 
            <Target Id="Id_Fabrikam"> 
              <TargetState> 
                <Condition Name="MCC" Value="310" /> 
                <Condition Name="MNC" Value="610" /> 
              </TargetState> 
            </Target>
          </Targets> 
          <Variant Name="ThePhoneCompany"> 
            <TargetRefs> 
              <TargetRef Id="Id_PhoneCo" /> 
            </TargetRefs> 
            <Policies>
              <DeviceLock>
                <MaxInactivityTimeDeviceLock>15</MaxInactivityTimeDeviceLock>
              </DeviceLock>
            </Policies>
          </Variant> 
          <Variant Name="Fabrikam"> 
            <TargetRefs> 
              <TargetRef Id="Id_Fabrikam" /> 
            </TargetRefs> 
            <Policies>
              <DeviceLock>
                <ScreenTimeoutWhileLocked>15</ScreenTimeoutWhileLocked>
              </DeviceLock>
            </Policies>
          </Variant> 
        </Customizations>
      </Settings>
    </WindowsCustomizations> 
      
    ```

6.  保存已更新的 customizations.xml 文件，并注意此更新文件的路径。 时还可以生成图像，您将需要为一个值的路径。

7.  使用 Windows ICD 命令行界面 (CLI) 来创建资源调配使用更新后的 customizations.xml 包。 有关如何生成设置包和命令开关和参数的说明，请参见**生成配置软件包**在[使用 Windows ICD 命令行界面](https://msdn.microsoft.com/library/windows/hardware/dn916115)。

    例如︰

    ``` syntax
    icd.exe /Build-ProvisioningPackage /CustomizationXML:"C:\CustomProject\customizations.xml" /PackagePath:"C:\CustomProject\output.ppkg" /StoreFile:C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Imaging and Configuration Designer\x86\Microsoft-Common-Provisioning.dat"
    ```

    在此示例中， **StoreFile**对应用于创建所需的 Windows 版本的程序包设置存储的位置。

    **请注意** 在此步骤中创建的资源调配包将包含 multivariant 设置。 您可以使用此程序包为独立软件包可应用于 Windows 设备，将其用作基时启动另一个项目，或使用它作为一个输入 (**/ProvisioningPackage**) 在生成 Windows 10 时两个桌面版本 （家庭、 Pro、 企业和教育） 的图像或 Windows 10 移动图像。

     

## <a name="span-idbuildamobileimageusingthewindowsicdclispanspan-idbuildamobileimageusingthewindowsicdclispanbuild-a-mobile-image-using-the-windows-icd-cli"></a><span id="build_a_mobile_image_using_the_windows_icd_cli"></span><span id="BUILD_A_MOBILE_IMAGE_USING_THE_WINDOWS_ICD_CLI"></span>生成使用 Windows ICD CLI 的移动图像


本演练演示如何使用 Windows ICD CLI 生成移动图像。 有关 Windows ICD CLI，包括用法示例和参数的说明，请参阅[使用 Windows ICD 命令行界面](https://msdn.microsoft.com/library/windows/hardware/dn916115)。

1.  使用管理员权限打开命令行窗口。

2.  从命令行中，导航到 Windows ICD 安装目录︰

    -   在 x64 计算机上，请转到︰ c:\\程序文件 (x86)\\窗口工具包\\10\\评估和部署工具包\\图像处理和配置设计器\\x86

    -   在 x86 计算机上，请转到︰ c:\\程序文件\\窗口工具包\\10\\评估和部署工具包\\图像处理和配置设计器\\x86

3.  使用 （使用 multivariant 设置） 更新的 customizations.xml 和 MCSF 咖啡馆中[配置自定义设置](configure-customization-settings.md)创建，请使用 Windows ICD CLI 生成移动图像。

    若要执行此操作的示例文件，并使用 bsp.config.xml，请参阅下面的命令︰

    **icd.exe /Build-ImageFromPackages /ImagePath:"***C:\\Contoso\\的自定义\\TestFlash2.ffu***"/BSPConfigFile:"***C:\\ContosoXDevice.bsp.config.xml***"/ImageType:***测试***/CustomizationXML:"***C:\\Contoso\\的自定义\\customizations.xml***"/OEMCustomizationVer:***1.0.0.0* **/MCSFCustomizationXML:"***c:\\Contoso\\的自定义\\MobileCustomizations.xml***"**

    下面是需要记住的一些事项︰

    -   对于每个参数的所有占位符值都替换匹配您的资产和目录位置的值
    -   指定 /ImageType，因为我们使用的 /BSPConfigFile
    -   使用 /CustomizationXML 指向 customizations.xml
    -   如果定义了 ProvisioningPackage，Windows ICD 要求 /OEMCustomizationVer
    -   确保 /OEMCustomizationVer 版本编号是*格式&lt;主要&gt;。&lt;次要&gt;。&lt;SubVersion&gt;。&lt;SubMinorVersion&gt;*，如 1.0.0.0

    若要执行此操作的示例文件，并使用 OEMInput.xml 文件，请参阅下面的命令︰

    **icd.exe /Build-ImageFromPackages /ImagePath:"***C:\\Contoso\\的自定义\\TestFlash2.ffu***"/OEMInputXML:"***C:\\ContosoTestOEMInput.xml***"/CustomizationXML:"***C:\\Contoso\\的自定义\\customizations.xml***"/OEMCustomizationVer:***1.0.0.0* **/MCSFCustomizationXML:"***c:\\Contoso\\的自定义\\MobileCustomizations.xml***"**

一旦生成图像 (FFU)，您可以通过使用 Windows ICD 用户界面中的 ffutool.exe 或**部署**选项向您的移动设备闪烁它。 请参阅下一节的详细信息。

## <a name="span-idflashanimagetoamobiledevicespanspan-idflashanimagetoamobiledevicespanspan-idflashanimagetoamobiledevicespanflash-an-image-to-a-mobile-device"></a><span id="Flash_an_image_to_a_mobile_device"></span><span id="flash_an_image_to_a_mobile_device"></span><span id="FLASH_AN_IMAGE_TO_A_MOBILE_DEVICE"></span>闪烁的图像到移动设备


有两种方法可以用来刷新到移动设备的图像︰

-   使用 ffutool.exe，或者，
-   在 Windows ICD 中使用内置的闪烁功能

本节演示如何执行上述操作。 选择这些方法以 flash 您向您的移动设备的图像之一。

如果出现闪烁图像与使用 Windows ICD 的设备，请执行以下步骤。

**闪存使用 Windows ICD 的图像**

1.  引导设备到图像或 FFU 下载模式。 为图像或 FFU 强制手机下载模式手动按下并释放电源按钮以重新启动电话，然后立即按下并保持向上按钮卷。 请注意仅在初始 FFU 已经刷新到电话之后，此选项才可用。

    如果这不起作用，请检查并按照闪烁 SoC 供应商提供的说明进行操作的设备。

2.  使用 USB 电缆，将您的电话连接到主机。

3.  启动 Windows ICD。

4.  单击**部署**从主菜单，然后选择**设备连接到 USB** FFU 映像部署到该设备。

5.  在**选择 FFU 图像**窗口中，单击**浏览...**以启动文件资源管理器，然后选择要与目标设备，快闪 FFU，然后单击**下一步**。

6.  从列表中选择目标设备或驱动器。 如果未列出您的设备或驱动器，请单击**刷新**。

7.  单击**下一步**。

8.  在**部署到设备**窗口中，选择**Flash**开始闪烁图像。

9.  单击**完成**以关闭**部署**页。

如果出现闪烁到使用 ffutool.exe 的设备图像，请执行以下步骤。

**闪存使用 ffutool.exe 的图像**

1.  引导至 FFU 闪灯模式连接到主机时的设备。

    如果没有包括 LABIMAGE 可选功能，生成测试映像时，可以强制 FFU 手动按下并松开电源按钮闪烁模式引导设备，然后立即按下并保持向上按钮卷到设备。 但是，请注意，此选项才可用 FFU 已经开始刷新到该设备。

2.  用管理员权限打开命令提示符。

3.  Ffutool.exe 从命令行运行以闪烁图像。

    **ffutool-闪存 TestFlash.ffu**

无论哪种方法，用于闪存设备的图像，它会完全刷新此图像的几分钟。 一旦完成闪烁，完成设备安装和验证您的自定义显示为图像的一部分。

 

 



