---
author: kpacquer
Description: We'll create some test files and registry keys to the image, again packaging them up so that they can be serviced after they reach your customers.
ms.assetid: 7ca2b835-4d36-43d9-b46f-d5d5d8410335
MSHAttr: PreferredLib:/library
title: "实验室 1 c︰ 向图像中添加一个文件和注册表设置"
ms.openlocfilehash: 5366dd09e57cf508a725ffad4286ef99b5ebacc4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="lab-1c-add-a-file-and-a-registry-setting-to-an-image"></a>实验室 1 c︰ 向图像中添加一个文件和注册表设置

文件和注册表项，您将添加到您的映像通常将特定于体系结构。 对于这些数据，我们建议您创建常用的程序包，您可以使用所有设备的体系结构。
 
我们将创建一些测试文件和注册表项的图像，并再次将其打包以便它们后到达您的客户可以提供服务。

我们将它们添加到常见的功能清单 (OEMCommonFM.xml) 用于 x86，x 64 和 ARM 的生成，并赋予它新的功能 ID，OEM\_FilesAndRegKeys。

此实验室中，我们将启动新的产品，ProductB，以便稍后我们可以使用 IoT 示例应用程序来获取我们设备的 IP 地址，并验证我们的文件和注册表项所做它。 

## <a name="span-idprerequisitesspanspan-idprerequisitesspanspan-idprerequisitesspanprerequisites"></a><span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>系统必备组件

请参阅[获取自定义 Windows IoT 核心所需的工具](set-up-your-pc-to-customize-iot-core.md)准备您的技术人员计算机。

## <a name="span-idcreateyourtestfilesspanspan-idcreateyourtestfilesspanspan-idcreateyourtestfilesspancreate-your-test-files"></a><span id="Create_your_test_files"></span><span id="create_your_test_files"></span><span id="CREATE_YOUR_TEST_FILES"></span>创建测试文件

-   创建使用记事本几个示例文本文件，标题它们 TestFile1.txt 和 TestFile2.txt。

## <a name="span-idbuildapackageforyourtestfilesspanspan-idbuildapackageforyourtestfilesspanspan-idbuildapackageforyourtestfilesspanbuild-a-package-for-your-test-files"></a><span id="Build_a_package_for_your_test_files"></span><span id="build_a_package_for_your_test_files"></span><span id="BUILD_A_PACKAGE_FOR_YOUR_TEST_FILES"></span>生成用于测试文件的包

1.  运行**c:\\IoT-ADK-AddonKit\\IoTCoreShell**作为管理员。

2.  创建注册表项的工作文件夹和测试文件，例如︰

    ``` syntax
    newcommonpkg Registry.FilesAndRegKeys
    ```

    在新文件夹**c:\\IoT-ADK-AddonKit\\通用\\软件包\\Registry.FilesAndRegKeys\\**。

### <a name="span-idaddsamplefilestothepackagespanadd-sample-files-to-the-package"></a><span id="Add_sample_files_to_the_package"></span>向包中添加示例文件

1.  将 （TestFile1.txt 和 TestFile2.txt），您的示例文件复制到新文件夹中**c:\\IoT-ADK-AddonKit\\通用\\软件包\\Registry.FilesAndRegKeys\\**。

2.  更新程序包定义文件， **c:\\IoT-ADK-AddonKit\\通用\\软件包\\Registry.FilesAndRegKeys\\Registry.FilesAndRegKeys.pkg.xml**:

    一。  删除批注标记和说明。

    b。  更新注册密钥以包括新的键名、 名称和值的值。

    c。  对 TestFile1.txt 和 TestFile2.txt 更新的文件的源名称。 默认情况下，文件停放在 c:\\Windows\\系统。 若要更改目标位置，添加 DestinationDir 和名称。
    
    像 $(runtime.root) 一样的变量定义在 c:\\程序文件 (x86)\\窗口工具包\\10\\工具\\bin\\i386\\pkggen.cfg.xml。

    ``` syntax
      <OSComponent> 
         <RegKeys> 
             <RegKey KeyName="$(hklm.software)\$(OEMNAME)\Test">
                <RegValue Name="StringValue" Value="Test string" Type="REG_SZ"/>
                <RegValue Name="DWordValue" Value="12AB34CD" Type="REG_DWORD"/>
                <RegValue Name="BinaryValue" Value="12,AB,CD,EF" Type="REG_BINARY"/>
             </RegKey>
             <RegKey KeyName="$(hklm.software)\$(OEMNAME)\EmptyKey"/> 
         </RegKeys> 
         <Files> 
            <File Source="TestFile1.txt" /> 
            <File Source="TestFile2.txt"
                DestinationDir="$(runtime.root)\OEMInstall" Name="TestFile2.txt"/>  
         </Files> 
      </OSComponent> 
    ```

2.  从 IoT 核心外壳，生成包。 (`BuildPkg All`命令生成的源文件夹中的所有内容。)

    ``` syntax
    buildpkg Registry.FilesAndRegKeys
    ```

    生成软件包时，显示为 c: **\\IoT-ADK-AddonKit\\生成\\&lt;弧&gt;\\pkgs\\&lt;OEM 名称&gt;。Registry.FilesAndRegKeys.cab**。

    体系结构特定文件夹中显示所有生成的软件包。 提示︰ 若要快速重建的另一种体系结构，使用**setenv&lt;弧&gt;**，然后**`BuildPkg All`**重建为其他体系结构的所有内容。

    **故障排除**︰ 如果您收到错误:"elementRegKeys urn:Microsoft.WindowsPhone/PackageSchema.v8.00 的命名空间中有内容不完整"，删除的注释和说明。 如果您不想包括注册表项或文件，然后删除这些 XML 元素。 

## <a name="span-idupdateyourfeaturemanifestspanspan-idupdateyourfeaturemanifestspanspan-idupdateyourfeaturemanifestspanupdate-your-feature-manifest"></a><span id="Update_your_feature_manifest"></span><span id="update_your_feature_manifest"></span><span id="UPDATE_YOUR_FEATURE_MANIFEST"></span>更新功能清单

1.  打开常用的功能清单文件， **c:\\IoT-ADK-AddonKit\\通用\\软件包\\OEMCommonFM.xml**

2.  在 XML 中，创建一个新的 PackageFile 分区，与包文件列出，并赋予其新的 FeatureID，如"OEM\_FilesAndRegKeys"。

    ``` syntax
    <Features>
      <OEM>
        <!-- Feature definitions below -->
        <PackageFile Path="%PKGBLD_DIR%" Name="%OEM_NAME%.Registry.FilesAndRegKeys.cab">
          <FeatureIDs>
            <FeatureID>OEM_FilesAndRegKeys</FeatureID>
          </FeatureIDs>
        </PackageFile>
    ```

    您现在可以为您的文件和注册表项添加到您的产品的任何通过引用添加到此功能清单和特征标识。


## <a name="span-idcreateanewproductspanspan-idcreateabasicimagespanspan-idcreateabasicimagespancreate-a-new-product"></a><span id="Create_a_new_product"></span><span id="create_a_basic_image"></span><span id="CREATE_A_BASIC_IMAGE"></span>创建新产品

1.  创建一个新的产品文件夹。 

    ``` syntax
    newproduct ProductB
    ```

## <a name="span-idupdateyourconfigurationfilespanupdate-your-product-configuration-file"></a><span id="Update_your_configuration_file"></span>更新您的产品配置文件

1.  更新测试配置文件 c:\\IoT-ADK-AddonKit\\源-_< 弧_>\\产品\\ProductB\\TestOEMInput.xml:

    确保功能清单︰ **OEMCommonFM.xml**是包括在内，如有必要，请删除批注标记。

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

2.  更新该产品中包含的功能︰ 

    一。 请确保包含示例应用程序 （尤其是 IOT_BERTHA 应用程序）。

    b。 添加 OEM 功能︰ OEM_AppxMain、 OEM_CustomCmd 和 OEM_ProvAuto，通过移除注释标记 (_< ！-_>) 在这一节。 

    c。 添加注册表包，FeatureID 示例︰ OEM_FilesAndRegKeys。
    
    ``` syntax
    <Features>
      <Microsoft>
    
      ...
      
      <!-- Sample Apps, remove this when you introduce OEM Apps -->
      <Feature>IOT_BERTHA</Feature>
      <Feature>IOT_ALLJOYN_APP</Feature>
      <Feature>IOT_NANORDPSERVER</Feature>
      <Feature>IOT_SHELL_HOTKEY_SUPPORT</Feature>
      <Feature>IOT_APPLICATIONS</Feature>
      <Feature>IOT_ENABLE_ADMIN</Feature>
      </Microsoft>
      <OEM>
        <!-- Include BSP Features -->
        <Feature>RPI2_DRIVERS</Feature>
        <Feature>RPI3_DRIVERS</Feature>
        <!-- Include OEM features -->
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
4.  输入用户名和密码 (默认值是︰ minwinpc / p@ssw0rd) > 设备中放置微 SD 卡，选择它、 接受许可条款中，并单击**安装**。 
5.  将卡片放入 IoT 设备并启动它。

过了一会儿，您应该会看到[IoT 测试 (Bertha) 应用程序](https://developer.microsoft.com/windows/iot/samples/iotdefaultapp)显示有关图像的基本信息。

## <a name="span-idseeyourfilesspansee-if-your-files-made-it"></a><span id="See_your_files"></span>如果您的文件进行查看

1.  将您的技术人员计算机和设备连接到同一个以太网网络。 

    例如，可以通过有线网络连接，插上的以太网电缆。 直接连接到该设备，将网线直接从您的 PC 的技术人员与设备。   

2.  在测试应用程序中，记下 IP 地址，例如，10.100.0.100。 

3.  在技术人员计算机，打开文件资源管理器中，并在与该设备的 IP 地址键入\\\\前缀和\\c$ 后缀︰

    ``` syntax
    \\10.100.0.100\c$
    ```

    使用设备名称、 默认的管理员帐户和密码登录。 (默认值是︰ minwinpc\\管理员 /p@ssw0rd)

4.  请检查文件是否存在。 查找：

    \\\\10.100.0.100\c$\\Windows\\system32\\TestFile1.txt

    \\\\10.100.0.100\c$\\OEMInstall\\TestFile2.txt

## <a name="span-idseeyourregkeysspansee-if-your-registry-keys-exist"></a><span id="See_your_regkeys"></span>查看您的注册表项是否存在

1.  在技术人员计算机，连接到您的设备使用 SSH 客户端，如[PuTTY](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe)。 例如，使用 IP 地址和端口 22 以连接到该设备，然后使用管理员帐户和密码登录。 （要了解更多信息，请参见[SSH](https://developer.microsoft.com/en-us/windows/iot/docs/ssh)。）

2.  从 SSH 客户端的命令行，注册表项在系统中查询。

    ``` syntax
    reg query HKLM\Software\Fabrikam\Test
    ```

    其中，Fabrikam 是 OEM 名称。 注册表工具应返回的测试值。

## <a name="span-idnextstepsspanspan-idnextstepsspanspan-idnextstepsspannext-steps"></a><span id="Next_steps"></span><span id="next_steps"></span><span id="NEXT_STEPS"></span>下一步行动

[实验室 1 d︰ 将供应包添加到映像](add-a-provisioning-package-to-an-image.md)
