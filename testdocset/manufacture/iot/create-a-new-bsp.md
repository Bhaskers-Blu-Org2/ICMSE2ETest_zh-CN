---
author: kpacquer
Description: "创建您自己的主板支持包 (BSP)"
title: "实验室 2︰ 创建您的主板支持包 (BSP)"
ms.openlocfilehash: 46601569c767124d94150145af56cc7a619703c3
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="lab-2-creating-your-own-board-support-package-bsp"></a>实验室 2︰ 创建您的主板支持包 (BSP)

BSP 包含一组特定于组件/硅板中使用的设备驱动程序。 这些供应商提供的组件 / 芯片供应商，大多在.inf 和相关联的.sys/.dll 文件的窗体。 

当创建一个新的主板支持包 (BSP):

-  创建一个新的 hardare 设计

-  更换一个驱动程序或组件在现有的硬件设计

无论您是创建新的 BSP，还是修改现有的 BSP，您将成为所有者。 这样就可以决定是否允许在您的主板上安装的更新。

在我们实验室，我们将创建新的 BSP 基于 Raspberry Pi 2，删除现有的 GPIO 驱动程序并将它替换为示例 GPIO 驱动程序︰ [Hello，Blinky ！](https://developer.microsoft.com/windows/iot/samples/driverlab)。

## <a name="span-idcreateanewbspworkingfolderspanspan-idcreateanewbspworkingfolderspanspan-idcreateanewbspfilespancreate-a-new-bsp-working-folder"></a><span id="Create_a_new_BSP_working_folder"></span><span id="create_a_new_bsp_working_folder"></span><span id="CREATE_A_NEW_BSP_FILE"></span>创建新的 BSP 工作文件夹

1.  创建您想要修改的 BSP 工作文件夹。

    ``` syntax
    newbsp MyRPi2
    ```

## <a name="span-idaddpackagesintothefeaturemanifestspanadd-packages-into-the-feature-manifest"></a><span id="Add_packages_into_the_feature_manifest"></span>将程序包添加到功能清单

1.  打开的功能清单文件，您新的 BSP \\IoT-ADK-AddonKit\\源-&lt;弧&gt;\\BSP\\MyRpi2\\MyRpi2FM.xml。

    在另一个窗口中，打开要用作模板的 Raspberry Pi 2 功能清单。

2.  添加您的基本产品包 (BasePackages)。
   
    *  UEFI 驱动程序启动分区 (RASPBERRYPI。RPi2.BootFirmware.cab)

    *  驱动程序所需的 UpdateOS (SV。PlatExtensions.UpdateOS.cab)

    *  引导配置数据 (Microsoft-IoTUAP-RPi2-BCD-Package.cab)

    *  必需的设备驱动程序 （bcm2836sdhc.cab、 dwcUsbOtg.cab、 rpiq.cab）
       
       创建您自己的 BSP，时，通常需要显示驱动程序和存储驱动程序，以及有时网络驱动程序。

    *  特定于设备的自定义项
    
    **请不要复制中︰**
    
    *  **设备的目标信息 (DeviceTargetingInfo.cab)** 对于 Microsoft 支持的平台，如 RPi2、 MBM(x86) 和 Dragonboard，该软件包是必需的。  对于类似这样的自定义 Bsp，此程序包不应包含。 相反，将添加功能 ID: IOT_GENERIC_POP OEMInput 文件中的。 这可以防止您的设备从原先所做的更改无法清除的 BSP 制造商接收更新。 

        
4.  复制的设备布局和平台软件包 （DeviceLayoutPackages，OEMDevicePlatformPackages）。

    请注意 OEMDevicePlatform.xml 和 devicelayout.xml 都可以打包到一个包中，例如，DeviceLayout.MBR4GB。 然后可以作为输入这两个节指定相同的包 (例如，在<OEMDevicePlatformPackages>和<DeviceLayoutPackages>)。  若要了解详细信息，请参阅[设备布局](device-layout.md)。
    
5.  复制功能 （功能）。
    
    复制所需的功能。 排除任何不适用于您的项目。
    
    例如，复制中的每个驱动程序**除了**现有的 GPIO 驱动程序︰
    ``` syntax
     <PackageFile Path="$(mspackageroot)\Retail\$(cputype)\$(buildtype)" Name="RASPBERRYPI.RPi2.GPIO.cab">
        <FeatureIDs>
          <FeatureID>RPI2_DRIVERS</FeatureID>
        </FeatureIDs>
      </PackageFile>
    ```
    
    注意︰ 为便于分组包，您可以将它们组合为一个或多个功能 Id。 例如，所有可选 Raspberry Pi 2 驱动程序使用的功能 ID: RPI2_DRIVERS。

6.  添加 HelloBlinky 驱动程序︰
    
    ``` syntax
        <PackageFile Path="%PKGBLD_DIR%" Name="%OEM_NAME%.Drivers.HelloBlinky.cab">
          <FeatureIDs>
            <FeatureID>RPI2_DRIVERS</FeatureID>
          </FeatureIDs>
        </PackageFile>
    ```

## <a name="span-idcreateanewproductfolderspanspan-idcreateanewproductandfolderspanspan-idcreateanewproductfolderspancreate-a-new-product-folder"></a><span id="Create_a_new_product_folder"></span><span id="create_a_new_product_and_folder"></span><span id="CREATE_A_NEW_PRODUCT_FOLDER"></span>创建一个新的产品文件夹

1.  创建新的工作产品文件夹，将 BSP 名称添加到末尾。

    ``` syntax
    newproduct ProductB MyRpi2
    ```

    这将创建文件夹︰ c:\\IoT-ADK-AddonKit\\源-&lt;弧&gt;\\产品\\ProductB，链接到新的 BSP。

## <a name="span-idupdatetheprojectsconfigurationfilesspanspan-idupdatetheprojectsconfigurationfilesspanspan-idupdatetheprojectsconfigurationfilesspanupdate-the-projects-configuration-files"></a><span id="Update_the_project_s_configuration_files"></span><span id="update_the_project_s_configuration_files"></span><span id="UPDATE_THE_PROJECT_S_CONFIGURATION_FILES"></span>更新项目的配置文件

1.  打开您的产品的测试配置文件︰ **c:\\IoT-ADK-AddonKit\\源臂\\产品\\ProductB\\TestOEMInput.xml**。

2.  添加 FeatureIDs:
    
    -  添加 FeatureID: IOT_GENERIC_POP 来获得仅操作系统更新。

    -  添加 FeatureIDs: IOT_DISABLE_UMCI 和 IOT_ENABLE_TESTSIGNING，使测试二进制文件和包工作。

    -  可选︰ 添加其他应用程序的 FeatureID 和测试包︰ OEM_AppxHelloWorld，OEM_CustomCmd，OEM_FileAndRegKey，实验室 1 中创建的。

       ``` syntax
       <Microsoft>
          <Feature>IOT_GENERIC_POP</Feature>
       ...
       </Microsoft>
    
       <OEM> 
          <Feature>RPI2_DRIVERS</Feature> 
          <Feature>PRODUCTION</Feature> 
          <Feature>IOT_DISABLE_UMCI</Feature> 
          <Feature>IOT_ENABLE_TESTSIGNING</Feature> 
          <Feature>OEM_CustomCmd</Feature> 
          <Feature>OEM_AppxHelloWorld</Feature> 
          <Feature>OEM_FileAndRegKey</Feature> 
        </OEM>
    ```

## <a name="span-idbuildandtesttheimagespanspan-idbuildandtesttheimagespanspan-idbuildandtesttheimagespanbuild-and-test-the-image"></a><span id="Build_and_test_the_image"></span><span id="build_and_test_the_image"></span><span id="BUILD_AND_TEST_THE_IMAGE"></span>生成和测试映像

**生成图像**

1.  从 IoT 核心外壳程序中，创建映像︰

    ``` syntax
    createimage ProductB Test
    ```

    这在 c︰ 中创建产品二进制文件\\IoT-ADK-AddonKit\\生成\\&lt;弧&gt;\\ProductB\\Flash.FFU。

2.  启动**Windows IoT 核仪表板** &gt; **安装新设备** &gt; **自定义**、 并浏览到您的映像。 

    将微 SD 卡放入设备，选择它，接受许可协议条款，并单击**安装**。 这与我们新的图像替换的前一个图像。

3.  将卡片放入 IoT 设备并启动它。

    过了一会儿，该设备应自动启动，并且您应该会看到您的应用程序。

**请检查您的驱动程序是否正常工作**

1.  使用[Hello，Blinky 的测试过程 ！ 实验室](https://developer.microsoft.com/windows/iot/samples/driverlab3)测试驱动程序。

## <a name="span-idnextstepsspanspan-idnextstepsspanspan-idnextstepsspannext-steps"></a><span id="Next_steps"></span><span id="next_steps"></span><span id="NEXT_STEPS"></span>下一步行动
祝贺您，您已完成实验室 2。 

[实验室 3︰ 更新应用程序](../../service/iot/updating-iot-core-apps.md)

##  <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="Related_topics"></span>相关的主题
[设备布局](device-layout.md)