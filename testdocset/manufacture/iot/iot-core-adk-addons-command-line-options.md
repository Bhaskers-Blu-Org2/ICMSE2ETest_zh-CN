---
author: kpacquer
Description: These tools are part of the Windows 10 IoT Core (IoT Core) ADK Add-Ons, in the \\Tools folder. To learn more about these tools, see What's in the Windows ADK IoT Core Add-ons.
ms.assetid: ae043bb0-656e-4439-bdbe-a8d370629ab7
MSHAttr: PreferredLib:/library
title: "IoT 核心加载项的命令行选项"
ms.openlocfilehash: 0e6d7edcf40c8a12207c42ec8cae03e836c52d25
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="span-idcommand-lineoptionstomanufactureiotcoreimagesspaniot-core-add-ons-command-line-options"></a><span id="command-line_options_to_manufacture_iot_core_images"></span>IoT 核心加载项的命令行选项

这些工具是属于[Windows 10 IoT 核心 （IoT 核心） ADK 加载项](http://go.microsoft.com/fwlink/?LinkId=735028)中，在[\\工具文件夹](iot-core-adk-addons-command-line-options.md)。 若要了解有关这些工具的详细信息，请参见[在 Windows ADK IoT 核心加载项](iot-core-adk-addons.md)。

## <a name="span-idappx2pkgcmdspanappx2pkgcmd"></a><span id="appx2pkg.cmd"></span>appx2pkg.cmd

创建文件夹结构并复制一个新包的模板文件。

## <a name="span-idbuildagentcmdspanbuildagentcmd"></a><span id="BuildAgent.cmd"></span>BuildAgent.cmd

对于附件工具包目录下的所有 OEMInputSamples 生成 FFUs。 可用于自动执行夜间生成。

## <a name="span-idbuildimagecmdspanbuildimagecmd"></a><span id="BuildImage.cmd"></span>BuildImage.cmd

[生成的图像文件 (FFU)](create-a-basic-image.md)，使用特定于产品的软件包。 使用 CreateImage.cmd，包含附加选项。

**用法**︰`buildimage [Product]/[All]/[Clean] [BuildType]`

**参数**︰
- `ProductName`....... 所需的产品名称创建。
- `All`...............内置 \Products 目录下的所有产品
- `Clean`............. 清除输出目录。  应指定一个以上。
- `BuildType`.........生成可选、 零售/测试，如果未指定这两种类型
- `[version]`.........可选的软件包版本。 如果未指定，则使用 BSP_VERSION
- `[/?]`.............. 显示此用法的字符串。

**示例**︰

``` syntax
buildimage SampleA Test
buildimage SampleA Retail
buildimage SampleA
buildimage All Test
buildimage All
buildimage Clean
```

## <a name="span-idbuildkitagentcmdspanbuildkitagentcmd"></a><span id="BuildKitAgent.cmd"></span>BuildKitAgent.cmd

为核心的套件包中的所有 OEMInputSamples 生成 FFUs。 可用于自动执行夜间生成。

## <a name="span-idbuildkitsamplescmdspanbuildkitsamplescmd"></a><span id="BuildKitSamples.cmd"></span>BuildKitSamples.cmd

核心的套件包中的 OEMInputSamples 生成特定于体系结构的 FFUs。  可用于自动执行夜间生成。

## <a name="span-idbuildpkgcmdspanbuildpkgcmd"></a><span id="buildpkg.cmd"></span>buildpkg.cmd

生成包从 \Sources-\<弧\>\Packages。

Buildpkg 将该包保存在 \Build\\< 弧\>\pkgs 为.cab 文件的文件夹 (示例︰ Contoso.Provisioning.Auto.cab)。

进行故障诊断，Buildpkg 将保存日志在 \Build\\< 弧\>\pkgs\logs。 

**用法**︰`buildpkg [CompName.SubCompName]/[packagefile.pkg.xml]/[All]/[Clean] [version]`

**参数**︰

-   `<CompName.SubCompName>`︰ 用于指通过其 ComponentName.SubComponent 名称的包。

-   `<packagefile.pkg.xml>`︰ 用于指由其包定义的 XML 文件的包。

-   `<All>`︰ 用于此生成 \Sources-中的所有程序包\<弧\>\Packages 文件夹。 这是相同`BuildPkg All`命令。

-   `<Clean>`︰ 用于清除所有在 \Build\\< 弧\>\pkgs 文件夹。 建议构建所有包前。

-   `<version>`︰ 可选的用来指定一个版本号。 如果不指定，默认值是使用变量 %bsp 中已定义的版本\_版本 %。 

**示例**︰

``` syntax
buildpkg Appx.Main
buildpkg Appx.Main 10.0.1.0
buildpkg sample.pkg.xml
buildpkg sample.pkg.xml 10.0.1.0
buildpkg All
buildpkg All 10.0.2.0
buildpkg Clean
```

## <a name="span-idcreateimagecmdspancreateimagecmd"></a><span id="createimage.cmd"></span>createimage.cmd

创建图像文件 (FFU) 使用特定于产品的软件包。 它使用 createpkg.cmd 和 imggen 工具和命令环境中设置的**参数**。 输出文件是在生成中可用 (%BLD\_DIR %) 文件夹。

createimage 将保存在 %BLD FFU\_DIR %\\<productname>\(测试或零售)。

**用法**︰`createimage <productname> <buildtype>`

**参数**︰

-   `<productname>`︰ 生成的产品名称。

-   `<buildtype>`︰**零售**或**测试**

**示例**︰

``` syntax
createimage.cmd ProductA Retail
```


## <a name="span-idcreatepkgcmdspancreatepkgcmd"></a><span id="createpkg.cmd"></span>createpkg.cmd

创建一个组包定义文件 (。 pkg.xml) 在由**IoTCoreShell.cmd**和**setversion.cmd**所定义的环境中使用 pkggen 工具和**参数**设置。 

Createpkg 将该包保存在 \Build\\< 弧\>\pkgs 为.cab 文件的文件夹 (示例︰ Contoso.Provisioning.Auto.cab)。

**用法**︰`createpkg <packagefile.pkg.xml>/<CompName.SubCompName> [version]`

**参数**︰

-   `<packagefile.pkg.xml>`︰ 用于标识由其包定义的 XML 文件的包。

-   `<CompName.SubCompName>`︰ 用于标识按 ComponentName.SubComponent 名称的包。   

-   `<version>`︰ 可选的用来指定一个版本号。 如果不指定，默认值是使用变量 %bsp 中已定义的版本\_版本 %。 


**示例**︰

``` syntax
createpkg %SRC_DIR%\Packages\Appx.Main\Appx.Main.pkg.xml
createpkg %SRC_DIR%\Packages\Appx.Main\Appx.Main.pkg.xml 10.0.1.0
createpkg Registry.FilesAndRegKeys 
```

## <a name="span-idcreateprovpkgcmdspancreateprovpkgcmd"></a><span id="createprovpkg.cmd"></span>createprovpkg.cmd

创建使用 icd.exe 工具和由**IoTCoreShell.cmd**和**setversion.cmd**所定义的环境中设置**参数**的自动配置包。 指定的输出位置创建的输出文件 (.ppkg)。

**用法**︰`createprovpkg <customizations.xml> <outputfilename>`

**参数**︰

-   `<customizations.xml>`︰ 用 Windows 自定义内容输入文件
-   `<outputfilename>`: 输出的完整路径的文件名 (.ppkg)

**示例**︰

``` syntax
createprovpkg %PRJ_DIR%\Products\SampleA\Prov\customizations.xml %PRJ_DIR%\Products\SampleA\Prov\SampleAProv.ppkg
```

## <a name="span-idcreateupdatepkgscmdspancreateupdatepkgscmd"></a><span id="createupdatepkgs.cmd"></span>createupdatepkgs.cmd

创建使用包装定义文件更新软件包 (。 pkg.xml) 更新文件夹中。 它使用 pkggen 工具，在**IoTCoreShell.cmd**和**setversion.cmd**所定义的环境中设置**参数**。

在生成目录中存储输出文件 (%BLD\_DIR %)，在\<updatename\>文件夹。

**用法**︰`createupdatepkgs <updatename>`

**参数**︰

-  `<updatename>`︰ 更新的名称。

**示例**︰

``` syntax
createupdatepkgs Update1
```

在此示例中，输出存储在 %bld\_DIR %\\Update1\\。

## <a name="span-idinf2cabcmdspaninf2cabcmd"></a><span id="inf2cab.cmd"></span>inf2cab.cmd

将转换为.cab 文件.inf 驱动程序包。

Inf2cab 将该包保存在 \Build\\< 弧\>\pkgs 文件夹 (示例︰ Drivers.GPIO.cab)。

**用法**︰`inf2cab filename.inf [CompName.SubCompName]`

**参数**︰

- `filename.inf` ........... 所需的驱动程序的输入文件。

- `<CompName.SubCompName>`.. 可选，是指通过 ComponentName.SubComponent 名该驱动程序包。

**示例**︰

``` syntax
inf2cab C:\test\gpiodriver.inf
inf2cab C:\test\gpiodriver.inf Drivers.GPIO
```

## <a name="span-idinf2pkgcmdspaninf2pkgcmd"></a><span id="inf2pkg.cmd"></span>inf2pkg.cmd

创建文件夹结构，并复制一个新的包的模板文件

**用法**︰`inf2pkg input.inf [CompName.SubCompName]`
- `input.inf`...............所需的输入.inf 文件
- `CompName.SubCompName`.... 可选的默认值是 Drivers.input
- `[/?]`.................... 显示此用法的字符串。

**示例**︰
``` syntax
inf2pkg C:\test\testdriver.inf
```

## <a name="span-idiotcoreshellcmdspanspan-idiotcoreshellcmdspaniotcoreshellcmd"></a><span id="iotcoreshell.cmd"></span><span id="IOTCORESHELL.CMD"></span>IoTCoreShell.cmd

以管理员身份打开 IoT 核心外壳。 （此文件位于根文件夹中，并使用 LaunchTool.cmd）

打开 IoTCoreShell 后，将会提示您选择一个默认的体系结构 （ARM 或 x86） 您将构建的设备。 这将设置您的默认启动设置的系统变量。  

## <a name="span-idlaunchtoolcmdspanlaunchtoolcmd"></a><span id="LaunchTool.cmd"></span>LaunchTool.cmd

由 LaunchTool.cmd （根文件夹） 中来打开 IoT 核心外壳命令方式。 

## <a name="span-idnewappxpkgcmdspannewappxpkgcmd"></a><span id="newappxpkg.cmd"></span>newappxpkg.cmd

创建新的工作文件夹以帮助您将 Appx 软件包转换为.cab 文件。 

注意︰ 此工具需要一个子文件夹命名"依赖项".appx 的任何依赖关系的软件包。

此命令创建工作文件夹中的 \Source-\<弧\>\Packages\ 文件夹。

如果您运行此命令而不使用任何变量，您还会看到其他工作文件夹中的 \Source-\<弧\>\Packages\ 文件夹。

**用法**︰`newappxpkg filename.appx [CompName.SubCompName]`

**参数**︰

-   `filename.appx`︰ Appx 包必需、 输入文件。

-   `<CompName.SubCompName>`︰ 可选创建工作文件夹使用的名称︰ ComponentName.SubComponent。

**示例**︰

``` syntax
newappxpkg C:\test\MainAppx_1.0.0.0_arm.appx AppX.Main
```

若要了解详细信息，请参阅[实验室 1b︰ 将应用程序添加到映像](deploy-your-app-with-a-standard-board.md)。

## <a name="span-idnewbspcmdspannewbspcmd"></a><span id="newbsp.cmd"></span>newbsp.cmd
创建文件夹结构，并将复制的模板文件[创建新的主板](create-a-new-bsp.md)支持包 (BSP)。

**用法**︰`newbsp BSPName`

**参数**︰

- `BSPName`........... 必填，BSP 要使用的名称

**示例**︰
``` syntax
newbsp CustomRPi2
```


## <a name="span-idnewcommonpkgcmdspannewcommonpkgcmd"></a><span id="newcommonpkg.cmd"></span>newcommonpkg.cmd

创建新的工作文件夹可帮助您[添加文件、 文件夹、 注册表项和资源调配包](add-a-registry-setting-to-an-image.md)以.cab 文件。 使用此命令之后, 使用 buildpkg 命令来创建最终的.cab 文件。

此命令创建的 \Common\Packages\ 文件夹中的工作文件夹。

如果您运行此命令而不使用任何变量，您还将看到其他工作文件夹中的 \Common\Packages\ 文件夹。

**用法**︰`newcommonpkg CompName.SubCompName`

**参数**︰

-   `<CompName.SubCompName>`︰ 需要时，将使用名称 ComponentName.SubComponent 的工作文件夹。

**示例**︰

``` syntax
newcommonpkg Registry.FilesAndRegKeys
```

若要了解详细信息，请参阅[实验室 1 c︰ 向图像中添加一个文件和注册表设置](add-a-registry-setting-to-an-image.md)。



## <a name="span-idnewdrvpkgcmdspannewdrvpkgcmd"></a><span id="newdrvpkg.cmd"></span>newdrvpkg.cmd

用于[添加到映像的驱动程序](add-a-driver-to-an-image.md)。 创建新的工作文件夹以帮助您将驱动程序软件包转换为.cab 文件。 使用此命令之后, 使用 buildpkg 命令来创建最终的.cab 文件。

此命令创建工作文件夹中的 \Source-\<弧\>\Packages\ 文件夹。

如果您运行此命令而不使用任何变量，您还会看到其他工作文件夹中的 \Source-\<弧\>\Packages\ 文件夹。

**用法**︰`newdrvpkg filename.inf [CompName.SubCompName]`

**参数**︰

-   `filename.inf`︰ 需要，请输入该驱动程序包的.inf 文件。

-   `<CompName.SubCompName>`︰ 可选创建工作文件夹使用的名称︰ ComponentName.SubComponent。 默认情况下的驱动程序。\<文件名\>。

**示例**︰

``` syntax
newdrvpkg C:\test\GPIO.inf Drivers.GPIO
```

## <a name="span-idnewproductcmdspan-newproductcmd"></a><span id="newproduct.cmd"></span>newproduct.cmd

用于[创建新产品图像](create-a-basic-image.md)。 创建新的工作产品目录下 \Products，从模板文件中复制的内容。

**用法**︰`newproduct <productname>`

**参数**︰

-   `<productname>`︰ 产品要创建的名称

**示例**︰

``` syntax
newproduct ProductA
```

## <a name="span-idnewupdatecmdspannewupdatecmd"></a><span id="NEWUPDATE.CMD"></span>newupdate.cmd

创建新的工作目录下 \Updates，从模板文件中复制的内容。

**用法**︰`newupdate <UpdateName>  <Version>`

**参数**︰

-   `<UpdateName>`︰ 更新以创建名称

-   `<Version>`︰ 版本号 (x.y.z.a)

**示例**︰

``` syntax
newupdate Update2 10.0.2.0
```

## <a name="span-idretailsigncmdspanretailsigncmd"></a><span id="retailsign.cmd"></span>retailsign.cmd

交叉证书用于签名并使 OEM 测试签名的证书之间进行切换

**用法**︰`retailsign [On/Off]`

**参数**︰
- `On` ................... 用于签名使交叉证书
- `Off`................... 禁用交叉证书进行签名，并允许 OEM 测试签名

**示例**︰

```syntax
retailsign On
retailsign Off
```


## <a name="span-idsetenvcmdspansetenvcmd"></a><span id="setenv.cmd"></span>setenv.cmd
重置环境变量，包括**IOTADK\_根**，**通用\_DIR**， **SRC\_DIR**， **BLD\_DIR**， **PKGBLD\_DIR**，**工具\_DIR**，等等。 

设置变量的完整列表，请参阅文本编辑器中打开 setenv.cmd。

**用法**︰`setenv <arch>`

**参数**︰

-   `<arch>`︰ 设置的结构。 (`arm`, `x86`, or `x64`).

**示例**︰

``` syntax
setenv.cmd arm
```

## <a name="span-idsetoemcmdspansetoemcmd"></a><span id="setOEM.cmd"></span>setOEM.cmd
设置您的 OEM 公司名称。 使用文本编辑器中编辑此文件。

``` syntax
set OEM_NAME=Contoso
```


## <a name="span-idsetsignaturecmdspansetsignaturecmd"></a><span id="setsignature.cmd"></span>setsignature.cmd
设置[交叉证书的内核模式代码签名](https://msdn.microsoft.com/windows/hardware/drivers/install/cross-certificates-for-kernel-mode-code-signing)

## <a name="span-idsetversioncmdspansetversioncmd"></a><span id="setversion.cmd"></span>setversion.cmd

设置[版本号](../../service/mobile/update-requirements.md)与**createpkg.cmd**或**createprovpkg.cmd**与资源调配包创建包时使用。

此版本信息存储在**%prj\_DIR %\\versioninfo.txt**和 IoT 核心外壳程序重新启动时加载。 每当程序包的内容更改时，版本已更新并需要重新创建所有的软件包。

**用法**︰`setversion x.y.z.a`

**参数**︰

-   `x.y.z.a`︰ 由四部分构成的版本号用于包

**示例**︰

``` syntax
setversion 10.0.0.1
```


<!--- ## <span id="UPDATEIMAGE.CMD"></span> updateimage.cmd


**Usage**: `updateimage <productname> <buildtype> <updatename>`

**Parameters**:

-   `<productname>`: Name of the product to be updated.
-   `<buildtype>`: **Retail** or **Test**
-   `<updatename>`: Name of the update to be applied

Description: This tool copies the specified product build and updates with the contents specified by &lt;updatename&gt; using ImageApp tool with the correct parameters set in the environment. The output files are available in the Build (%BLD\_DIR%) folder.

**Example**:

``` syntax
updateimage ProductA Retail Update1
```

Output is available at %BLD\_DIR%\\ProductA\\Update1\\Retail

-->

## <a name="span-idoldertoolsspanolder-tools"></a><span id="older_tools"></span>旧工具

### <a name="span-idbuildallpackagescmdspanbuildallpackagescmd"></a><span id="buildallpackages.cmd"></span>buildallpackages.cmd

此工具已被取代的工具︰ buildpkg 所有。

### <a name="span-idnewpkgcmdspan-newpkgcmd"></a><span id="newpkg.cmd"></span>newpkg.cmd

此工具已被取代的工具︰ newappxpkg，newdrvpkg，和 newcommonpkg。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题

[IoT 核心加载项](iot-core-adk-addons.md)

[IoT 核心制造指南](iot-core-manufacturing-guide.md)
