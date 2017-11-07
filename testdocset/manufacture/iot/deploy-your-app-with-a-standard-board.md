---
author: kpacquer
Description: We're now going to take an app (like the sample Hello, World! app), and package it up so that it can be serviced after it reaches your customers.
ms.assetid: a801d768-0397-4f85-b68f-bd85ddcc3f1f
MSHAttr: PreferredLib:/library
title: "实验室 1b︰ 将应用程序添加到映像"
ms.openlocfilehash: 1867f00397c07604a20c5cfcaf13c496b4c830d4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="lab-1b-add-an-app-to-your-image"></a>实验室 1b︰ 将应用程序添加到映像

现在我们要使一个应用程序 (如下所示的示例[Hello、 世界 ！](https://developer.microsoft.com/windows/iot/samples/helloworld) 应用程序），它打包，并创建新的图像可以加载到新的设备上。 

用于背景的应用程序，使用相同的方法来安装和运行它们。 请注意，只有一个应用程序可以选择作为默认应用程序，使用此方法作为背景应用程序运行安装的所有其他应用程序。

**请注意** 在我们本制造指南，项目将开始类似于在 c: SampleA 图像\\IoT-ADK-AddonKit\\源臂\\产品\\SampleA。

## <a name="span-idprerequisitesspanspan-idprerequisitesspanspan-idprerequisitesspanprerequisites"></a><span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>系统必备组件

我们将使用我们创建的项目图像[实验室 1a︰ 创建基本映像](create-a-basic-image.md)。

## <a name="span-idcreateandtestanwindowsappspanspan-idcreateandtestanwindowsappspanspan-idcreateandtestanwindowsappspancreate-and-test-an-windows-app"></a><span id="Create_and_test_an_Windows_app"></span><span id="create_and_test_an_windows_app"></span><span id="CREATE_AND_TEST_AN_WINDOWS_APP"></span>创建和测试 Windows 应用程序
如果您已经创建并测试您的应用程序，则可以跳过这些步骤。

1.  创建一个应用程序。 这可以是任何为 IoT 核心，另存为一个 Appx 包而设计的应用程序。 对于我们的示例中，我们使用[Hello，世界上](https://developer.microsoft.com/windows/iot/samples/helloworld)的应用程序。

2.  在 Visual Studio 中，要保存 Hello，世界应用程序作为一个 Appx 包中，请单击**项目 > 存储 > 创建应用程序软件包** > **No** > **下一步**。 

3.  选择**输出位置︰ C:\HelloWorld** （或其他任何不包含空格的路径）。
    
4.  选择**生成应用程序捆绑︰ 从不**
    
5.  单击**创建**。

    Visual Studio 创建到 C:\HelloWorld\HelloWorld_1.0.0.0_Debug_Test 的 Appx 文件 

6.  可选︰[测试应用程序](test-the-app.md)。 请注意，您已测试该应用程序生成项目的一部分。 


## <a name="span-idpackagetheappspanspan-idpackagetheappspanspan-idpackagetheappspanpackage-the-app"></a><span id="Package_the_app"></span><span id="package_the_app"></span><span id="PACKAGE_THE_APP"></span>打包应用程序

**为应用程序创建程序包**

1.  打开**c:\\IoT-ADK-AddonKit\\IoTCoreShell**作为管理员。


2.  创建工作文件夹的应用程序，例如︰

    ``` syntax
    newAppxPkg "C:\HelloWorld\HelloWorld_1.0.0.0_ARM_Debug_Test\HelloWorld_1.0.0.0_ARM_Debug.appx" Appx.HelloWorld
    ```

    这在 c︰ 中创建一个新的工作文件夹\\IoT-ADK-AddonKit\\源-&lt;弧&gt;\\软件包\\Appx.HelloWorld，其中包含将用于帮助生成包的文件。

    故障排除︰ 如果您收到消息:"系统无法找到指定的文件"，则可能是因为包没有任何定义的依赖项。
    
3.  从 IoT 核心外壳，生成包。

    ``` syntax
    buildpkg Appx.HelloWorld
    ```

    生成软件包时，显示为 c: **\\IoT-ADK-AddonKit\\生成\\&lt;弧&gt;\\pkgs\\&lt;OEM 名称&gt;。Appx.HelloWorld.cab**。

    监视的任何生成错误，并对其进行更正-这些通常是在不同的实际文件名的程序包定义文件中的文件名的结果。

## <a name="span-idupdatethefeaturemanifestspanspan-idupdatethefeaturemanifestspanspan-idupdatethefeaturemanifestspanupdate-the-feature-manifest"></a><span id="Update_the_feature_manifest"></span><span id="update_the_feature_manifest"></span><span id="UPDATE_THE_FEATURE_MANIFEST"></span>更新功能清单


**将您的应用程序的软件包添加到功能清单**

1.  打开您的功能清单文件， **c:\\IoT-ADK-AddonKit\\源-&lt;弧&gt;\\软件包\\OEMFM.xml**

2.  在 XML 中，创建一个新的 PackageFile 分区，与包文件列出，并赋予其新的 FeatureID，如"Appx\_HelloWorld"。

    ``` syntax
    <?xml version="1.0" encoding="utf-8"?>
    <FeatureManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate">
      <BasePackages/>
      <Features>
        <OEM>
          <!-- Feature definitions below -->
          <PackageFile Path="%PKGBLD_DIR%" Name="%OEM_NAME%.Appx.Main.cab">
            <FeatureIDs>
              <FeatureID>OEM_AppxMain</FeatureID>
            </FeatureIDs>
          </PackageFile>
        <PackageFile Path="%PKGBLD_DIR%" Name="%OEM_NAME%.Appx.HelloWorld.cab">
            <FeatureIDs>
              <FeatureID>OEM_AppxHelloWorld</FeatureID>
            </FeatureIDs>
          </PackageFile>
        </OEM>
        <OEMFeatureGroups/>
      </Features>
    </FeatureManifest>
    ```

    您现在可以将您的应用程序添加到任何您的产品，通过引用添加到此功能清单和特征标识。

## <a name="span-idupdatetheprojectsconfigurationfilesspanspan-idupdatetheprojectsconfigurationfilesspanspan-idupdatetheprojectsconfigurationfilesspanupdate-the-projects-configuration-files"></a><span id="Update_the_project_s_configuration_files"></span><span id="update_the_project_s_configuration_files"></span><span id="UPDATE_THE_PROJECT_S_CONFIGURATION_FILES"></span>更新项目的配置文件

**替换为您自己的产品的默认应用程序**

1.  打开您的产品的测试配置文件︰ **c:\\IoT-ADK-AddonKit\\源-&lt;弧&gt;\\产品\\ProductA\\TestOEMInput.xml**。

2.  确保功能清单、 OEMFM.xml 和功能清单︰ OEMCommonFM.xml，AdditionalFMs 一节中列出的两个。

    ``` syntax
    <AdditionalFMs>
       <!-- Including BSP feature manifest -->
       <AdditionalFM>%BSPSRC_DIR%\RPi2\Packages\RPi2FM.xml</AdditionalFM>
       <!-- Including OEM feature manifest -->
       <AdditionalFM>%COMMON_DIR%\Packages\OEMCommonFM.xml</AdditionalFM>
       <AdditionalFM>%SRC_DIR%\Packages\OEMFM.xml</AdditionalFM>
       <!-- Including the test features -->
       <AdditionalFM>%AKROOT%\FMFiles\arm\IoTUAPNonProductionPartnerShareFM.xml</AdditionalFM>
    </AdditionalFMs>
    ```

3.  更改该产品中包含的功能︰ 

    一。 通过添加注释标记删除示例测试应用程序︰ _< ！-_>。 （我们将使用这些应用程序再次在以后的实验中。

    b。 添加 OEM 功能︰ OEM_AppxMain、 OEM_CustomCmd 和 OEM_ProvAuto，通过移除注释标记 (_< ！-_>) 在这一节。 

    c。 添加为您的应用程序数据包，FeatureID 示例︰ OEM_AppxHelloWorld。
    
    ``` syntax
    <Features>
      <Microsoft>
    
      ...
      
      <!-- Sample Apps, remove this when you introduce OEM Apps -->
      <!--
      <Feature>IOT_BERTHA</Feature>
      <Feature>IOT_ALLJOYN_APP</Feature>
      <Feature>IOT_NANORDPSERVER</Feature>
      <Feature>IOT_SHELL_HOTKEY_SUPPORT</Feature>
      <Feature>IOT_APPLICATIONS</Feature>
      <Feature>IOT_ENABLE_ADMIN</Feature>
      -->
      </Microsoft>
      <OEM>
        <!-- Include BSP Features -->
        <Feature>RPI2_DRIVERS</Feature>
        <Feature>RPI3_DRIVERS</Feature>
        <!-- Include OEM features -->
        <Feature>OEM_AppxMain</Feature>
        <Feature>OEM_CustomCmd</Feature>
        <Feature>OEM_ProvAuto</Feature>
        <Feature>OEM_AppxHelloWorld</Feature>
     </OEM>
    ```

**设置应用程序自动安装，并将设置为默认应用程序**

1.  打开**c:\\IoT-ADK-AddonKit\\源-&lt;弧&gt;\\产品\\ProductA\\OEMCustomization.cmd**

2.  建议︰ 更改设备的默认用户名和密码。

3.  从开头的代码块中删除 REM 语句中的第一套"REM 如果存在 C:\AppInstall\AppInstall.cmd..."，这样，AppInstall.cmd 命令以自动安装您的应用程序。

    ``` syntax
    @echo off
    REM OEM Customization Script file
    REM This script if included in the image, is called everytime the system boots.

    REM Enable Administrator User
    net user Administrator p@ssw0rd /active:yes

    if exist C:\OEMTools\InstallAppx.cmd (
        REM Run the Appx Installer. This will install the appx present in C:\OEMApps\
        call C:\OEMTools\InstallAppx.cmd
    )

    if exist C:\AppInstall\AppInstall.cmd (
        REM Enable Application Installation for onetime only, after this the files are deleted.
        call C:\AppInstall\AppInstall.cmd > %temp%\AppInstallLog.txt
        if %errorlevel%== 0 (
            REM Cleanup Application Installation Files. Change dir to root so that the dirs can be deleted
            cd \
            rmdir /S /Q C:\AppInstall
         )
    )
    ```

## <a name="span-idbuildandtesttheimagespanspan-idbuildandtesttheimagespanspan-idbuildandtesttheimagespanbuild-and-test-the-image"></a><span id="Build_and_test_the_image"></span><span id="build_and_test_the_image"></span><span id="BUILD_AND_TEST_THE_IMAGE"></span>生成和测试映像

生成和闪烁的图像使用相同的过程，从[实验室 1a︰ 创建基本映像](create-a-basic-image.md)。 简版︰

1.  从 IoT 核心外壳，生成图像 (`buildimage ProductA Test`)。
2.  安装映像︰ 启动**Windows IoT 核仪表板**> 单击**安装新设备**选项卡 > 选择**设备类型︰ 自定义** >
3.  从**闪存到 SD 卡预下载的文件 (Flash.ffu)**: 单击**浏览**，浏览到您 FFU 文件 (c:\\IoT-ADK-AddonKit\\生成\\&lt;弧&gt;\\ProductA\\测试\\ProductA.ffu)，然后单击**下一步**。
4.  输入用户名和密码 (默认值是︰ minwinpc / p@ssw0rd) > 设备中放置微 SD 卡，选择它、 接受许可条款中，并单击**安装**。 
4.  将卡片放入 IoT 设备并启动它。

过了一会儿，该设备应自动启动，并且您应该会看到您的应用程序。

## <a name="span-idnextstepsspanspan-idnextstepsspanspan-idnextstepsspannext-steps"></a><span id="Next_steps"></span><span id="next_steps"></span><span id="NEXT_STEPS"></span>下一步行动

[实验室 1 c︰ 向图像中添加一个文件和注册表设置](add-a-registry-setting-to-an-image.md)

 ## <a name="span-idrelatedtopicsspanspan-idrelatedtopicsspanspan-idrelatedtopicsspanrelated-topics"></a><span id="Related_topics"></span><span id="related_topics"></span><span id="RELATED_TOPICS"></span>相关的主题

[更新 IoT 核心设备上的应用程序](../../service/iot/updating-iot-core-apps.md)