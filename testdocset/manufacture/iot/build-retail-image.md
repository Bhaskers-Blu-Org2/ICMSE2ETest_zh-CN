---
author: kpacquer
Description: We'll take our test image and convert it to a retail build.
MS-HAID: p\_iot\_core.build\_retail\_image
MSHAttr: PreferredLib:/library
title: "实验室 1f︰ 构建零售映像"
ms.openlocfilehash: 66e8cdbd78c765dcf4399bc222c0da949a8864f2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="lab-1f-build-a-retail-image"></a>实验室 1f︰ 构建零售映像

我们 ' ll 采取我们的自定义项，将它们放在一起，和零售版本中测试它们。 

## <a name="span-idprerequisitesspanspan-idprerequisitesspanspan-idprerequisitesspanprerequisites"></a><span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>系统必备组件

-   [实验室 1a︰ 创建基本映像](create-a-basic-image.md)
-   [实验室 1b︰ 将应用程序添加到映像](deploy-your-app-with-a-standard-board.md)
-   [实验室 1 c︰ 向图像中添加一个文件和注册表设置](add-a-registry-setting-to-an-image.md)
-   [实验室 1 d︰ 将网络和其他设置的包添加到映像](add-a-provisioning-package-to-an-image.md)
-   [实验室 1e︰ 将驱动程序添加到映像](add-a-driver-to-an-image.md)

## <a name="span-idaddyourapptotheretailconfigurationfilespanspan-idaddyourapptotheretailconfigurationfilespanspan-idaddyourapptotheretailconfigurationfilespanadd-your-app-to-the-retail-configuration-file"></a><span id="Add_your_app_to_the_retail_configuration_file"></span><span id="add_your_app_to_the_retail_configuration_file"></span><span id="ADD_YOUR_APP_TO_THE_RETAIL_CONFIGURATION_FILE"></span>将您的应用程序添加到零售配置文件

1.  打开您的产品的零售配置文件︰ **c:\\IoT-ADK-AddonKit\\源-&lt;弧&gt;\\产品\\ProductA\\RetailOEMInput.xml**.

2.  添加功能清单，OEMFM.xml，列表中的 AdditionalFMs。 同时，添加功能清单︰ OEMCommonFM.xml，其中包含 OEM\_CustomCmd 包，用于配置您的应用程序首次启动︰

    ``` syntax
    <AdditionalFMs>
        <AdditionalFM>%AKROOT%\FMFiles\arm\IoTUAPRPi2FM.xml</AdditionalFM>
        <AdditionalFM>%AKROOT%\FMFiles\arm\RPi2FM.xml</AdditionalFM>
        <AdditionalFM>%SRC_DIR%\Packages\OEMFM.xml</AdditionalFM>
        <AdditionalFM>%COMMON_DIR%\Packages\OEMCommonFM.xml</AdditionalFM>
      </AdditionalFMs>
    ```

3.  添加的 FeatureIDs 应用程序软件包，以及 OEM\_CustomCmd 软件包。

    ``` syntax
    <OEM> 
       <!-- Include BSP Features -->
       <Feature>RPi2_DRIVERS</Feature> 
       <Feature>RPi3_DRIVERS</Feature>
       <!-- Include OEM features -->
       <Feature>OEM_CustomCmd</Feature> 
       <Feature>OEM_ProvAuto</Feature>
       <Feature>OEM_AppxHelloWorld</Feature> 
       <Feature>OEM_FilesAndRegKeys</Feature>
       <Feature>OEM_DriverHelloBlinky</Feature> 
    </OEM>
    ```
    
    OEM_CustomCmd 需要触发应用程序安装。
    
    OEM_ProvAuto 需要资源调配包中拉出。
    
    OEM_FilesAndRegKeys、 OEM_AppxHelloWorld 和 OEM_DriverHelloBlinky 已在前一实验中添加示例包。

## <a name="span-idcopyinprovisioningpackagesspancopy-in-the-provisioning-package-from-productb-into-producta"></a><span id="Copy_in_provisioning_packages"></span>将复制配置包中从 ProductB 到 ProductA。

1.  在文件资源管理器中，创建一个新文件夹，c:\\IoT-ADK-AddonKit\\产品\\ProductA\\技术

2.  将.ppkg、.cat 和 customizations.xml 文件复制到此文件夹。
    
    将文件重命名为 （产品 name)Prov.cat 和 (您产品 name)Prov.ppkg，例如，ProductAProv.cat 和 ProductAProv.ppkg。

### <a name="span-idbuildandcreatetheimagespanspan-idbuildandcreatetheimagespanspan-idbuildandcreatetheimagespanbuild-and-create-the-image"></a><span id="Build_and_create_the_image"></span><span id="build_and_create_the_image"></span><span id="BUILD_AND_CREATE_THE_IMAGE"></span>生成并创建映像

**生成图像**

1.  [获取代码签名证书](https://msdn.microsoft.com/library/windows/hardware/hh801887(v=vs.85).aspx)。

2.  配置跨签名证书用于零售签名。 编辑 setsignature.cmd 文件来设置 SIGNTOOL_OEM_SIGN:

    ``` syntax
    set SIGNTOOL_OEM_SIGN=/s my /i "Issuer" /n "Subject" /ac "CrossCertRoot" /fd SHA256
    ```
    
    -  颁发者︰ 颁发者的证书 (请参阅证书-> 详细信息-> 颁发者)
    
    -  主题︰ 主题证书中 (请参阅证书-> 详细信息-> 主题)
    
    -  CrossCertRoot: Microsoft 提供交叉证书根。 请参阅交叉证书列表中[交叉证书的内核模式代码签名](https://msdn.microsoft.com/windows/hardware/drivers/install/cross-certificates-for-kernel-mode-code-signing#cross-certificate-list)。
    
    
2.  从 IoT 核心外壳，使零售签名。

    ``` syntax
    retailsign On
    ```
    
3.  重建所有软件包，以便它们零售签名。

    ``` syntax
    buildpkg all
    ```

4.  从 IoT 核心外壳程序中，创建映像︰

    ``` syntax
    buildimage ProductA Retail
    ```

    这在 c︰ 中创建产品二进制文件\\IoT-ADK-AddonKit\\生成\\&lt;弧&gt;\\ProductA\\零售\\Flash.FFU。

5.  启动**Windows IoT 核仪表板** &gt; **安装新设备** &gt; **自定义**、 并浏览到您的映像。 将微 SD 卡放入设备，选择它，接受许可协议条款，并单击**安装**。 这与我们新的图像替换的前一个图像。

6.  将卡片放入 IoT 设备并启动它。

    过了一会儿，该设备应自动启动，并且您应该会看到您的应用程序。

**检查以查看是否工作的一切**

与零售版本中，您将无法登录到使用 SSH 客户端设备或通过 web 界面。 但是，所有的文件和注册表键依赖于您的应用程序应仍正常工作。

## <a name="span-idnextstepsspanspan-idnextstepsspanspan-idnextstepsspannext-steps"></a><span id="Next_steps"></span><span id="next_steps"></span><span id="NEXT_STEPS"></span>下一步行动

- [实验室 2︰ 创建您的主板支持包](create-a-new-bsp.md)