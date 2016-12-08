---
author: kpacquer
Description: We'll show you one of two ways to add a driver to the image.
title: "实验室 1e︰ 将驱动程序添加到映像"
ms.openlocfilehash: 5962a48636841044aedb381c0cabbe59c5e11355
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="lab-1e-add-a-driver-to-an-image"></a>实验室 1e︰ 将驱动程序添加到映像

在此实验室中，我们将添加示例驱动程序︰ [Hello，Blinky ！](https://developer.microsoft.com/windows/iot/samples/driverlab)、 打包，并将其部署到 Windows 10 IoT 核心设备。

## <a name="span-idprerequisitesspanspan-idprerequisitesspanspan-idprerequisitesspanprerequisites"></a><span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>系统必备组件

* 创建已设置为默认启动 (Bertha) 应用程序中，如中所示的产品文件夹 (ProductB)[实验室 1a︰ 创建基本映像](create-a-basic-image.md)或[实验室 1 c︰ 向图像中添加一个文件和注册表设置](add-a-registry-setting-to-an-image.md)。

## <a name="span-idcheckforsimilardriversspancheck-for-similar-drivers"></a><span id="Check_for_similar_drivers"></span>类似的驱动程序检查

然后再添加驱动程序，可能需要查看您预构建主板支持包 (BSP) 以确保尚没有类似的驱动程序。 

例如，查看文件中的驱动程序列表︰ \\IoT-ADK-AddonKit\\源臂\\BSP\\Rpi2\\软件包\\RPi2FM.xml。

- 如果不是现有的驱动程序，则通常只需添加一个。

- 如果一个驱动程序，但它不满足您的需求，您需要通过创建新的 BSP 来替换此驱动程序。 我们将[实验室 2](create-a-new-bsp.md)中介绍的。

## <a name="span-idcreateyourtestfilesspanspan-idcreateyourtestfilesspanspan-idcreateyourtestfilesspancreate-your-test-files"></a><span id="Create_your_test_files"></span><span id="create_your_test_files"></span><span id="CREATE_YOUR_TEST_FILES"></span>创建测试文件

-  完成[安装的示例驱动程序](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab1)生成 Hello，灾难从天而降的应用程序中的练习。 您将创建三个文件︰ ACPITABL.dat、 gpiokmdfdemo.inf 和 gpiokmdfdemo.sys，您将使用安装驱动程序。

   您还可以使用自己 IoT 核心的驱动程序，只要它不会发生冲突与现有的主板支持包 (BSP)。

-  复制每个文件︰ gpiokmdfdemo.sys、 gpiokmdfdemo.inf 和 ACPITABL.dat 的测试文件夹，例如，C:\gpiokmdfdemo\。

## <a name="span-idbuildapackageforyourdriverspanspan-idbuildapackageforyourdriverspanspan-idbuildapackageforyourdriverspanbuild-a-package-for-your-driver"></a><span id="Build_a_package_for_your_driver"></span><span id="build_a_package_for_your_driver"></span><span id="BUILD_A_PACKAGE_FOR_YOUR_DRIVER"></span>生成驱动程序软件包

1.  运行**c:\\IoT-ADK-AddonKit\\IoTCoreShell**作为管理员。

2.  创建驱动程序包的.inf 文件用作基︰

    ``` syntax
    newdrvpkg C:\gpiokmdfdemo\gpiokmdfdemo.inf Drivers.HelloBlinky
    ```

    在新文件夹**c:\\IoT-ADK-AddonKit\\源-&lt;弧&gt;\\软件包\\Drivers.HelloBlinky\\**。

3. 将该文件复制︰ 到新文件夹中，ACPITABL.dat **c:\\IoT-ADK-AddonKit\\源-_< 弧_>\\软件包\\Drivers.HelloBlinky\\**。

**验证示例文件位于包**

1.  更新驱动程序的软件包定义文件， **c:\\IoT-ADK-AddonKit\\源-&lt;弧&gt;\\软件包\\Drivers.HelloBlinky\\Drivers.HelloBlinky.pkg.xml**。

    默认程序包定义文件包括您可以对其进行修改以添加您自己的驱动程序文件的 XML 的示例。

    如果有必要，请更新值的文件源以指向您。SYS 文件和 ACPITABL.dat 文件。 (不需要添加。INF 文件）。 添加"$(runtime.drivers)"的 DestinationDir。
    
    ``` syntax
    <Package xmlns="urn:Microsoft.WindowsPhone/PackageSchema.v8.00" 
         Owner="$(OEMNAME)" OwnerType="OEM" ReleaseType="Production" 
         Platform="arm" Component="Drivers" SubComponent="HelloBlinky"> 
      <Components> 
        <Driver InfSource="gpiokmdfdemo.inf"> 
          <Reference Source="gpiokmdfdemo.sys" /> 
          <Files> 
            <File Source="gpiokmdfdemo.sys"  
                  DestinationDir="$(runtime.drivers)"  
                  Name="gpiokmdfdemo.sys" /> 
            <File Source="ACPITABL.dat"  
                  DestinationDir="$(runtime.system32)"  
                  Name="ACPITABL.dat" /> 
          </Files> 
        </Driver> 
      </Components> 
    </Package> 
    ```

2.  从 IoT 核心外壳，生成包。

    ``` syntax
    createpkg Drivers.HelloBlinky
    ```

    生成软件包时，显示为 c: **\\IoT-ADK-AddonKit\\生成\\&lt;弧&gt;\\pkgs\\&lt;OEM 名称&gt;。Drivers.HelloBlinky.cab**。

    
## <a name="span-idupdateyourfeaturemanifestspanspan-idupdateyourfeaturemanifestspanspan-idupdateyourfeaturemanifestspanupdate-your-feature-manifest"></a><span id="Update_your_feature_manifest"></span><span id="update_your_feature_manifest"></span><span id="UPDATE_YOUR_FEATURE_MANIFEST"></span>更新功能清单


**将驱动程序包添加到功能清单**

1.  打开特定于体系结构的功能清单文件， **c:\\IoT-ADK-AddonKit\\源-_< 弧_>\\软件包\\OEMFM.xml**

2.  在 XML 中，创建一个新的 PackageFile 分区，与包文件列出，并赋予其新的 FeatureID，如"OEM\_DriverHelloBlinky"。

    ``` syntax      
          <PackageFile Path="%PKGBLD_DIR%" Name="%OEM_NAME%.Drivers.HelloBlinky.cab">
            <FeatureIDs>
              <FeatureID>OEM_DriverHelloBlinky</FeatureID>
            </FeatureIDs>
          </PackageFile>
    ```

    现在，您将能够通过引用添加到此功能清单将您的驱动程序添加到您的产品。


## <a name="span-idupdatetheprojectsconfigurationfilesspanspan-idupdatetheprojectsconfigurationfilesspanspan-idupdatetheprojectsconfigurationfilesspanupdate-the-projects-configuration-files"></a><span id="Update_the_project_s_configuration_files"></span><span id="update_the_project_s_configuration_files"></span><span id="UPDATE_THE_PROJECT_S_CONFIGURATION_FILES"></span>更新项目的配置文件

1.  打开您的产品的测试配置文件︰ **c:\\IoT-ADK-AddonKit\\源-_< 弧_>\\产品\\ProductA\\TestOEMInput.xml**。

2.  请确保您的功能清单，OEMFM.xml，AdditionalFMs 列表中。 如果不是有已经存在，则将其添加︰

    ``` syntax
      <AdditionalFMs>
        <AdditionalFM>%AKROOT%\FMFiles\arm\IoTUAPNonProductionPartnerShareFM.xml</AdditionalFM>
        <AdditionalFM>%SRC_DIR%\Packages\OEMFM.xml</AdditionalFM>
      </AdditionalFMs>
    ```

3.  添加 FeatureID 驱动程序︰

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
      <Feature>OEM_DriverHelloBlinky</Feature> 
    </OEM>
    ```

## <a name="span-idbuildandtesttheimagespanspan-idbuildandtesttheimagespanspan-idbuildandtesttheimagespanbuild-and-test-the-image"></a><span id="Build_and_test_the_image"></span><span id="build_and_test_the_image"></span><span id="BUILD_AND_TEST_THE_IMAGE"></span>生成和测试映像

生成和闪烁的图像使用相同的过程，从[实验室 1a︰ 创建基本映像](create-a-basic-image.md)。 简版︰

1.  从 IoT 核心外壳，生成图像 (`buildimage ProductB Test`)。
2.  安装映像︰ 启动**Windows IoT 核仪表板**> 单击**安装新设备**选项卡 > 选择**设备类型︰ 自定义** >
3.  从**闪存到 SD 卡预下载的文件 (Flash.ffu)**: 单击**浏览**，浏览到您 FFU 文件 (c:\\IoT-ADK-AddonKit\\生成\\&lt;弧&gt;\\ProductB\\测试\\ProductB.ffu)，然后单击**下一步**。
4.  输入用户名和密码 (默认值是︰ minwinpc / p@ssw0rd) > 设备中放置微 SD 卡，选择它、 接受许可条款中，并单击*安装**。 
5.  将卡片放入 IoT 设备并启动它。

**请检查您的驱动程序是否正常工作**

1.  使用中的过程[Hello，Blinky ！ 实验室](https://developer.microsoft.com/windows/iot/samples/driverlab3)测试驱动程序。

## <a name="span-idnextstepsspanspan-idnextstepsspanspan-idnextstepsspannext-steps"></a><span id="Next_steps"></span><span id="next_steps"></span><span id="NEXT_STEPS"></span>下一步行动

[实验室 1f︰ 构建零售映像](build-retail-image.md)