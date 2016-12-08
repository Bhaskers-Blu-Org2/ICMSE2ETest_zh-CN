---
author: kpacquer
Description: We'll create a provisioning package that contains some sample Wi-Fi settings.
ms.assetid: d9a50f87-e8c0-48da-89e7-0cdd542ce053
MSHAttr: PreferredLib:/library
title: "实验室 1 d︰ 将网络和其他设置的包添加到映像"
ms.openlocfilehash: 1664c0ded9d1259082aeca3090798f8068443573
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="lab-1d-add-networking-and-other-provisioning-package-settings-to-an-image"></a>实验室 1 d︰ 将网络和其他设置的包添加到映像

我们将创建包含一些设置示例 Wi-Fi 的供应包。 要添加应用程序、 驱动程序、 功能，或修改许多常见的设置，例如 IT 设备管理和策略设置，可以使用 Windows 图像处理和配置设计器 (ICD) 中的资源调配包。

注意，与 Wi-Fi，您的主板测试还需要 Wi-Fi 的支持。 您可以使用 Wi-Fi 适配器/转换器，或者使用像拥有 Wi-fi 内置 Raspberry Pi 3 板。

为此实验室中，我们将使用 ProductB，包含默认的应用程序 (Bertha)，它显示网络状态。

使用自动配置包的其他设置︰

* **更改自动更新的运行时映像中的设置**︰ [Windows 10 IoT 核心 Pro 更新控件文件](https://developer.microsoft.com/en-us/windows/iot/docs/createiotcorepro)   

## <a name="span-idprerequisitesspanspan-idprerequisitesspanspan-idprerequisitesspanprerequisites"></a><span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>系统必备组件

* 请参阅[获取自定义 Windows IoT 核心所需的工具](set-up-your-pc-to-customize-iot-core.md)准备您的技术人员计算机。

* 创建已设置为默认启动 (Bertha) 应用程序中，如中所示的产品文件夹 (ProductB)[实验室 1a︰ 创建基本映像](create-a-basic-image.md)或[实验室 1 c︰ 向图像中添加一个文件和注册表设置](add-a-registry-setting-to-an-image.md)。

## <a name="span-idcreateyourprovisioningpackageinwindowsicdspanspan-idcreateyourprovisioningpackageinwindowsicdspanspan-idcreateyourprovisioningpackageinwindowsicdspancreate-your-provisioning-package-in-windows-icd"></a><span id="Create_your_provisioning_package_in_Windows_ICD"></span><span id="create_your_provisioning_package_in_windows_icd"></span><span id="CREATE_YOUR_PROVISIONING_PACKAGE_IN_WINDOWS_ICD"></span>在 Windows ICD 创建配置软件包
1.  启动**Windows 图像处理和配置设计器**。

2.  单击**文件&gt;新的项目**。

3.  对于此示例，起名为"**ProductBProv**"的产品名称、 接受默认值，并单击**下一步**。

4.  选择**资源调配包&gt;窗口 10 IoT 酷睿**。

5.  在**导入设置包 （可选）**页上，单击**完成**。

6.  添加示例设置︰

    1.  展开**运行时设置&gt;连接配置文件&gt;WLAN &gt; WLANSetting &gt; SSID**。

    2.  键入名称，Wi-Fi 网络名称，例如，ContosoWiFi，然后单击**添加**。

    3.  展开**SSID > WLANXmlSettings > SecurityType** ，然后选择设置，如**打开**。

    4.  展开**SSID > WLANXmlSettings > 自动连接**和选择的设置，如**，则返回 TRUE**。

    5.  可选︰ 若要添加多个 WLAN 网络，回到 WLANSetting，并重复该过程。

7.  可选︰ 添加其他应用程序、 驱动程序和通过用户界面设置。 若要了解详细信息，请参阅[配置自定义项使用 Windows ICD](https://msdn.microsoft.com/library/windows/hardware/dn916109)。

8.  导出配置包。 例如，单击**导出&gt;资源调配包&gt;下一步&gt;（取消选择加密包框）&gt;下&gt;生成**。 （若要了解详细信息，请参阅[导出配置包](https://msdn.microsoft.com/library/windows/hardware/dn916110)。 )

9.  在**全部完成 ！** 页面上，单击链接到**输出位置**。

**在您测试的产品创建供应包文件夹**

1.  在文件资源管理器中，创建一个新文件夹，c:\\IoT-ADK-AddonKit\\通用\\产品\\ProductB\\技术

    此文件夹是由脚本使用结构︰ Provisioning.Auto 文件夹中的 Provisioning.Auto.pkg.xml 文件。 需要不进行任何更改。

2.  将.ppkg、.cat 和 customizations.xml 文件复制到此文件夹。
    
    如有必要，以匹配您的产品名称，重命名文件︰

    *  C:\\IoT-ADK-AddonKit\\通用\\产品\\ProductB\\提供商\\ProductBProv.cat
    *  C:\\IoT-ADK-AddonKit\\通用\\产品\\ProductB\\提供商\\ProductBProv.ppkg
    *  C:\\IoT-ADK-AddonKit\\通用\\产品\\ProductB\\提供商\\customizations.xml    
        
3.  可选︰ 使用所需的更改来更新 customizations.xml。 更多的信息，请参阅[Windows 设置的答案文件](https://msdn.microsoft.com/library/windows/hardware/dn916153)。

**功能清单和产品配置文件中添加自动配置脚本**

1.  查看程序包定义文件︰ Provisioning.Auto.pkg.xml: c:\\IoT-ADK-AddonKit\\通用\\软件包\\Provisioning.Auto\\Provisioning.Auto.pkg.xml。 

    请确保正确的文件源解析。 ($PROD)Prov.ppkg 将解析为 c:\\IoT-ADK-AddonKit\\通用\\产品\\ProductB\\提供商\\ProductBProv.ppkg，这应匹配配置软件包的文件的名称。

    ``` syntax
    <?xml version="1.0" encoding="utf-8"?>
      <Package xmlns="urn:Microsoft.WindowsPhone/PackageSchema.v8.00"
        Owner="$(OEMNAME)"
        OwnerType="OEM"
        ReleaseType="Production"
        Platform="$(BSPARCH)"
        Component="Provisioning"
        SubComponent="Auto">
        <Components>
           <OSComponent>
           <Files>
            <!--
            Source : Provisioning is product specific, so copied from the Product directory
            Destination : Auto provisioning folder which is C:\Windows\Provisioning\Packages
            -->
            <File Source="$(PRJDIR)\Products\$(PROD)\prov\$(PROD)Prov.ppkg"
                    DestinationDir="$(runtime.windows)\Provisioning\Packages" Name="ProvAuto.ppkg"/>
            </Files>
           </OSComponent>
        </Components>
    </Package>
    ```

2.  请确保包定义文件**%oem\_名称 %。Provisioning.Auto.cab"**和功能 ID: **OEM\_ProvAuto** c: 常见功能清单中引用\\IoT-ADK-AddonKit\\通用\\包\\OEMCommonFM.xml:

    ``` syntax
    <PackageFile Path="%PKGBLD_DIR%" Name="%OEM_NAME%.Provisioning.Auto.cab">
      <FeatureIDs>
        <FeatureID>OEM_ProvAuto</FeatureID>
        <FeatureID>OEMCommon_ALL</FeatureID>
      </FeatureIDs>
    </PackageFile>    
    ...
    <OEMFeatureGroups>
    <!-- Feature Constraints below -->
    <!-- This ensures that only one of the Provisioning package is included -->
      <FeatureGroup Constraint="ZeroOrOne">
        <FeatureIDs>
          <FeatureID>OEM_ProvAuto</FeatureID>
          <FeatureID>OEM_ProvManual</FeatureID>        
        </FeatureIDs>
    ```

3.  更新测试配置文件 c:\\IoT-ADK-AddonKit\\源-_< 弧_>\\产品\\ProductB\\TestOEMInput.xml:

    1.  确保公共功能清单︰ OEMCommonFM.xml 是包括在内。 （删除注释标记，如有必要）。

        ``` syntax
        <AdditionalFMs>
          <!-- Including BSP feature manifest -->
          <AdditionalFM>%BSPSRC_DIR%\RPi2\Packages\RPi2FM.xml</AdditionalFM>
          <!-- Including OEM feature manifest-->
          <AdditionalFM>%COMMON_DIR%\Packages\OEMCommonFM.xml</AdditionalFM>
          <AdditionalFM>%SRC_DIR%\Packages\OEMFM.xml</AdditionalFM>
          <!-- Including the test features -->
          <AdditionalFM>%AKROOT%\FMFiles\arm\IoTUAPNonProductionPartnerShareFM.xml</AdditionalFM>
        </AdditionalFMs>
        ```

    2.  请确保该功能︰ OEM_ProvAuto 是包括在内。 （删除注释标记，如有必要）。

        ``` syntax
        <OEM>
          <!-- Include BSP Features -->
          <Feature>RPI2_DRIVERS</Feature>
          <Feature>RPI3_DRIVERS</Feature>
          <!-- Include OEM features-->
          <Feature>OEM_AppxMain</Feature>
          <Feature>OEM_CustomCmd</Feature>
          <Feature>OEM_ProvAuto</Feature>
          <Feature>OEM_FilesAndRegKeys</Feature>
        </OEM>
        ```

## <a name="span-idbuildandtesttheimagespanspan-idbuildandtesttheimagespanspan-idbuildandtesttheimagespanbuild-and-test-the-image"></a><span id="Build_and_test_the_image"></span><span id="build_and_test_the_image"></span><span id="BUILD_AND_TEST_THE_IMAGE"></span>生成和测试映像

生成和闪烁的图像使用相同的过程，从[实验室 1a︰ 创建基本映像](create-a-basic-image.md)。 简版︰

1.  从 IoT 核心外壳，生成图像 (`buildimage ProductB Test`)。
2.  安装映像︰ 启动**Windows IoT 核仪表板**> 单击**安装新设备**选项卡 > 选择**设备类型︰ 自定义** >
3.  从**闪存到 SD 卡预下载的文件 (Flash.ffu)**: 单击**浏览**，浏览到您 FFU 文件 (c:\\IoT-ADK-AddonKit\\生成\\&lt;弧&gt;\\ProductB\\测试\\ProductB.ffu)，然后单击**下一步**。
4.  输入用户名和密码 (默认值是︰ minwinpc / p@ssw0rd) > 设备中放置微 SD 卡，选择它、 接受许可条款中，并单击*安装**。 
5.  将卡片放入 IoT 设备并启动它。

注意︰ 在这些菜单中忽略的"Wi-Fi 网络连接"设置，将不使用这些设置。 

过了一会儿，您应该会看到[IoT 测试 (Bertha) 应用程序](https://developer.microsoft.com/windows/iot/samples/iotdefaultapp)显示有关图像的基本信息。

**进行测试以查看是否已应用配置设置**

1.  拔下从 IoT 设备的所有网线。

2.  选择默认值。 在**让我们获取连接**屏幕中，选择**跳过此步骤**。

3.  如果您的无线网络处于范围内时，此屏幕应显示网络成功连接，并显示网络的 IP 地址。

## <a name="span-idtestnetworkconnectionsspantest-network-connections-and-upload-apps"></a><span id="Test_network_connections"></span>测试网络连接并上传的应用程序

您可以连接到您的设备的门户页后，可以解决网络连接问题，上载应用程序，或有关设备的更多详细信息，请参阅。

1.  将您的技术人员计算机和设备连接到同一网络。 

    例如，可以通过有线网络连接，插上的以太网电缆。  要通过无线连接，请确保您的技术人员计算机和 IoT 核心设备都连接到同一无线网络。    

2.  在技术人员计算机，打开 Internet Explorer 并键入 http:// 前缀与该设备的 IP 地址和︰ 8080 的后缀。 

    ``` syntax
    http://10.123.45.67:8080
    ```

3.  出现提示时，输入设备的默认用户名和密码。 (默认值是︰ 管理员 \p@ssw0rd)

    这将打开[Windows 设备门户](https://developer.microsoft.com/windows/iot/win10/tools/deviceportal)。 从这里，您可以上载应用程序软件包，查看安装了哪些应用程序，并在它们之间切换。

4.  单击**网络** > **配置文件**。  您应看到您创建的 Wi-Fi 配置文件。 
    
    如果设备都能自动连接到 WiFi 网络，然后在**可用的网络**，您应看到您配置网络旁边的复选标记。

    如果您的网络要求的步骤，如接受许可协议条款，该设备可能不自动连接。

## <a name="span-idtroubleshootingspantroubleshooting"></a><span id="Troubleshooting"></span>故障排除

**检查 Wi-fi 广播的频率 （2.4 g h z 和 5ghz）**。 一些 Wi-Fi 适配器，例如 Raspberry Pi 3，内置 Wi-fi® 适配器仅支持 2.4 g h z Wi-Fi 网络。 虽然这是最常见的 Wi-Fi 广播的频率，许多 Wi-Fi 网络广播在 5 GHz 的频率。 更改该广播的频率，或者使用不同的适配器。

**确认包设置您的网络上工作**。 使用膝上型电脑测试︰

1.  从网络中断开便携式计算机︰ 单击系统托盘中的网络图标，选择的无线网络，单击**断开连接**。 

2.  确认网络已断开连接。

3.  双击 ProductAProv.ppkg 安装配置包。 应自动连接的无线网络。

**请检查是否已添加设备配置文件**

1.  使用以太网连接到设备的连接。

2.  使用如[PuTTY](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe)SSH 客户机连接。

3.  当连接时，检查已安装了哪些配置文件︰

    ```syntax
    netsh wlan show profiles
    ``` 

    网络应出现在列表中的用户配置文件。

## <a name="span-idnextstepsspanspan-idnextstepsspanspan-idnextstepsspannext-steps"></a><span id="Next_steps"></span><span id="next_steps"></span><span id="NEXT_STEPS"></span>下一步行动

[实验室 1e︰ 将驱动程序添加到映像](add-a-driver-to-an-image.md) 
