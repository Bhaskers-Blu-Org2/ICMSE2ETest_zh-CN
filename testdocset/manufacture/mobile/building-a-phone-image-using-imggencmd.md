---
title: "生成使用 ImgGen.cmd 的移动图像"
description: "您可以使用 ImgGen.cmd 生成的 10 Windows Mobile 设备的硬件设计为基础的图像，或如果您正使用 MCSF 自定义答案文件以及使用旧生成其他资产工具附带的 Windows Phone 8.1。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 284a2ca2-d973-44a4-9e6c-5caebc088c75
ms.openlocfilehash: 94c66b5a8593332c1d64a44d6c6eb347c6f7a6ff
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="build-a-mobile-image-using-imggencmd"></a>生成使用 ImgGen.cmd 的移动图像


您可以使用 ImgGen.cmd 生成的 10 Windows Mobile 设备的硬件设计为基础的图像，或如果您正使用 MCSF 自定义答案文件以及使用旧生成其他资产工具附带的 Windows Phone 8.1。

下面是生成使用 ImgGen.cmd 图像时将采取的步骤的高级视图︰

1.  标识要在图像中包含的包。 有关更多信息，请参阅[获得包的映像](#gettingpackages)。

2.  通过将它们添加到一个或多个功能清单文件引用包并将这些文件保存在 Microsoft 文件包，例如，%WPDKCONTENTROOT%的根目录\\MSPackages。 更多的信息，请参阅[指定程序包包含在图像中使用的功能清单文件](#specifyingpackagestoinclude)。

3.  为每个设备平台，执行以下操作︰

    1.  创建*设备平台软件包*，并将其保存为 Microsoft 产品包的根目录中。 有关更多信息，请参阅[设置设备平台信息](set-device-platform-information.md)。

    2.  通过使用**OEMDevicePlatformPackages**元素中引用的设备平台包中的功能清单文件。

        功能清单文件中可以包含多个设备平台。 OEMInput 文件将指定的设备要使用的设备名称。

        除非有效的设备平台包指定的图像，图像创建都会失败。

4.  创建指定的设备平台、 功能清单文件，以及其他属性用于定义图像的*OEMInput 文件*。 有关更多信息，请参阅[创建 OEMInput 文件来定义图像](#adding)。

5.  创建一个 MCSF 自定义答案文件。 至少，指定所需的设备平台信息和移动运营商网络所需的信息。 有关更多信息，请参见[自定义答案文件](https://msdn.microsoft.com/library/windows/hardware/dn757452)和[电话 DeviceTargetingInfo 中的元数据](https://msdn.microsoft.com/library/windows/hardware/dn772214)。

    **请注意** 如果您想要支持在答案文件中的 multivariant 设置，相同的一组条件支持 MCSF 与 Windows 资源调配。 请参阅的部分*目标、 TargetState、 条件和优先级*中[创建具有 multivariant 设置的自动配置软件包](https://msdn.microsoft.com/library/windows/hardware/dn916108)列表支持的条件，但请确保在答案文件中指定您的**目标**时，应遵循 MCSF 自定义答案文件的架构。

     

6.  运行 ImgGen.cmd 后，生成图像。 有关更多信息，请参阅[使用 ImgGen.cmd 生成图像](#usingimggen)下面。

7.  签名图像，以便可以将其刷新为设备。 更多的信息，请参阅[注册全闪存更新 (FFU) 图像](sign-a-full-flash-update--ffu--image.md)。

## <a name="a-href-idgettingpackagesagetting-packages-for-the-image"></a><a href="" id="gettingpackages"></a>获取包的映像


图像之前，必须首先确定图像所需的所有包。 通常情况下，有三种类别的用于生成图像的包︰

-   **Microsoft 的包**。 其中包括所有操作系统和 Microsoft 实现驱动程序软件包所需的任何图像，以及其他特定于平台的驱动程序和固件包 （例如，特定于特定设备分辨率或 SoC 的组件的程序包）。 这些包中包含的 MobileOS 和必须安装在 %WPDKCONTENTROOT%\\MSPackages。 可以使用下面的命令显示 WPDKCONTENTROOT 的当前值。

    ``` syntax
    ECHO %WPDKCONTENTROOT%
    ```

    抽象的功能清单文件的位置和 Microsoft 提供的软件包的分组。 这样的一组相关的程序包规范通过指定一个单一功能的名称。 例如，指定 TESTINFRASTRUCTURE 功能包括支持测试执行的多个程序包。 有关更多信息，请参阅[构建映像的可选功能](optional-features-for-building-images.md)。

-   **SoC 供应商包**。 其中包括驱动程序和固件组件实现 SoC 供应商包。 有关这些程序包的详细信息，请参阅 SoC 供应商提供的文档。

    **请注意**  
    多个 UEFI 包都需要从 SoC 的供应商联系，以创建可引导映像。 这些产品包设备和 SoC 供应商的布局而异。 大部分包填充二进制设备上的分区。 有关创建两个分区包来填充这些分区的详细信息，请参阅[指定组件的包项目文件中](https://msdn.microsoft.com/library/windows/hardware/dn789218)。 EFI 系统分区 (ESP) 是使用 Microsoft 内容和 OEM 内容填充的。

     

-   **OEM 包**。 这些都是由 Oem 为内容，如驱动程序和应用程序创建的包。 有关创建对象包的信息，请参阅[创建程序包](creating-mobile-packages.md)。

## <a name="a-href-idaddingacreating-an-oeminput-file-to-define-the-image"></a><a href="" id="adding"></a>创建 OEMInput 文件来定义图像


若要定义图像，必须创建一个*OEMInput*文件。 这是一个 XML 文件，可以指定以下︰

-   生成的图像的类型。 例如，您可以指定是否映像包含只有 Microsoft 生产包或混合的生产和测试包中的**ReleaseType**元素，并且可以指定图像**解析**元素中支持的屏幕分辨率。

    **请注意**  
    Oem 可以通过选择不同的**ReleaseType**元素的值或通过引用 Microsoft 定义功能**功能**元素下图像中包含哪些 Microsoft 文件包一些控制。 更多的信息，请参阅本主题中后面的[指定程序包包含在图像中使用的功能清单文件](#specifyingpackagestoinclude)。

     

-   在图像中包含 OEM 包。 若要指定在图像中包含哪些 OEM 文件包，请创建一个*功能清单*文件和 OEMInput 文件中引用 this。 更多的信息，请参阅本主题中后面的[指定程序包包含在图像中使用的功能清单文件](#specifyingpackagestoinclude)。

在 OEMInput 文件中的受支持元素的完整列表，请参阅[OEMInput 文件的内容](oeminput-file-contents.md)。

Oem 应该使用示例 OEMInput 文件 MobileOS 中包含为自己的图像的起始点。 这些示例文件提供一套标准的图像类型，包括零售、 生产、 测试和制造图像的起始配置。 Oem 应该扩展软件包包含驱动程序、 应用程序和为其特定设备所需的其他组件的每个文件。 这些示例文件位于 %WPDKCONTENTROOT%\\OEMInputSamples。 对于指导有关如何维护 OEMInput 文件，以便对 Microsoft 的示例文件的最新更改可以集成到它，请参阅本主题中后面[配置集成功能更改 Microsoft 样本中的 OEMInput 文件](#configuringtheoeminputfile)。

Oem 应该与 SoC 供应商为特定设备使用，包括那些在 OEMInput 文件中的功能清单文件。

**请注意**  
OEMInput XML 文件支持显式路径和环境变量。 如果在包和其他文件的路径中使用环境变量，环境变量将映像工具处理 OEMInput XML 文件时展开。 MobileOS 中包含的示例文件在某些路径中使用 %WPDKCONTENTROOT%环境变量。

 

### <a name="image-types"></a>图像类型

下表列出的 Oem 可以生成的图像和 OEMInput 示例用作起始配置为每个图像类型的类型。

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>图像类型</th>
<th>说明</th>
<th>OEMInput 示例</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>零售</p></td>
<td><p>零售的图像是图像，刷新为最终零售电话。 零售的图像必须使用 Microsoft 签名的包使用 OEM 提交工具提交给 Microsoft 生产图像后返回给 Oem。 更多的信息，请参阅[提交二进制文件是零售签名](https://msdn.microsoft.com/library/windows/hardware/dn789223)。</p>
<p>零售的图像如下所示︰</p>
<ul>
<li><p>生产版本的 Windows 中 10 Windows Mobile 的核心组件</p></li>
<li><p>生产 Windows 10 移动组件。</p></li>
</ul></td>
<td><p>RetailOEMInput.xml</p></td>
</tr>
<tr class="even">
<td><p>Production</p></td>
<td><p>生产图像是类似于最终零售的图像，但它们具有启用运行 OEM 签名组件以及生产签名的组件测试签名和它们可能包含与测试相关的包，以及生产包。 生产的图像可以用于工程设计工作，以及移动运营商试验和其他认证过程。 生产图像使用 OEM 提交工具要生产由 Microsoft 签名生成最终的零售映像之前提交给 Microsoft。 更多的信息，请参阅[提交二进制文件是零售签名](https://msdn.microsoft.com/library/windows/hardware/dn789223)。</p>
<p>生产图像如下所示︰</p>
<ul>
<li><p>生产版本的 Windows 中 10 Windows Mobile 的核心组件。</p></li>
<li><p>生产 Windows 10 移动组件。</p></li>
<li><p>测试启用签名。</p></li>
</ul></td>
<td><p>ProductionOEMInput.xml</p></td>
</tr>
<tr class="odd">
<td><p>测试</p></td>
<td><p>可以在场外测试实验室测试功能的操作系统和驱动程序在设备上的运行测试映像。 测试图像如下所示︰</p>
<ul>
<li><p>测试版本的 Windows 中 10 Windows Mobile 的核心组件。</p></li>
<li><p>生产 Windows 10 移动组件。</p></li>
<li><p>测试启用签名。</p></li>
<li><p>测试应用程序、 驱动程序和其他组件，用于测试在不同情况下的操作系统。</p></li>
</ul>
<div class="alert">
<strong>请注意</strong>  
<p>若要生成包含操作系统的映像工具，例如 ipconfig.exe、 kill.exe、 ping.exe、 minshutdown.exe、 reg.exe、 tracelog.exe、 sc.exe，以及 tlist.exe，构建测试映像。</p>
</div>
<div>
 
</div></td>
<td><p>TestOEMInput.xml</p></td>
</tr>
<tr class="even">
<td><p>状况</p></td>
<td><p>健康状态图像，将运行在非现场测试实验室测试设备的功能和性能的功能。 健康图像是类似于生产映像，添加的组件运行相关的功能和性能测试。</p></td>
<td><p>HealthOEMInput.xml</p></td>
</tr>
<tr class="odd">
<td><p>制造</p></td>
<td><p>制造业在生产环境中使用的图像。 有关更多信息，请参见[MMO 图像定义](mmos-image-definition.md)。</p></td>
<td><p>MfgOEMInput.xml</p></td>
</tr>
<tr class="even">
<td><p>客户服务</p></td>
<td><p>客户医疗图像包括 MMO 零售客户的治疗方案。 有关更多信息，请参见[MMO 图像定义](mmos-image-definition.md)。</p></td>
<td><p>CustomerCareOEMInput.xml</p></td>
</tr>
</tbody>
</table>

 

### <a name="oeminput-file-example"></a>OEMInput 文件示例

下面的示例演示一个示例 ProductionOEMInput.xml 文件的内容。

``` syntax
<?xml version="1.0" encoding="utf-8" ?> 
<OEMInput xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate">
<Description>Test FFU generation for {SOC TYPE} with build number XXXXX</Description> 
<SOC>{PROCESSOR_NAME}</SOC> 
<SV>{SV_NAME}</SV> 
<Device>{DEVICE_NAME}</Device> 
<ReleaseType>Test</ReleaseType> 
<BuildType>fre</BuildType> 
<SupportedLanguages>
  <UserInterface>
      <Language>en-US</Language> 
  </UserInterface>
  <Keyboard>
     <Language>en-US</Language> 
  </Keyboard>
  <Speech>
    <Language>en-US</Language> 
  </Speech>
</SupportedLanguages>
<BootUILanguage>en-US</BootUILanguage> 
<BootLocale>en-US</BootLocale> 
<Resolutions>
  <Resolution>480x800</Resolution> 
</Resolutions>
<AdditionalFMs>
  <AdditionalFM>%WPDKCONTENTROOT%\FMFiles\MSOptionalFeatures.xml</AdditionalFM> 
  <!-- Add OEM FM files here -->
</AdditionalFMs>
<Features>
  <Microsoft>
    <Feature>CODEINTEGRITY_TEST</Feature> 
    <Feature>PRODUCTION_CORE</Feature> 
    <Feature>BOOTKEYACTIONS_RETAIL</Feature> 
  </Microsoft>
<!-- Insert OEM\SOC features here
  <OEM>
    <Feature>xxx</Feature>
  </OEM>
-->
</Features>
</OEMInput>
```

### <a name="a-href-idspecifyingpackagestoincludeaspecifying-packages-to-include-in-images-by-using-feature-manifest-files"></a><a href="" id="specifyingpackagestoinclude"></a>指定要包含图像中使用的功能清单文件的包

功能清单文件指定一组功能、 软件包和应用程序在构建映像时所提供。 OEMInput.xml 文件以后选择所需的功能，可从这些功能清单，以包括在映像中。

除了一组核心的 Microsoft 程序包添加到每个图像，还有其他程序包添加只为某些类型的图像。 例如，测试映像包含一组不同的 Microsoft 程序包比生产图像。

某些类型的图像中包含的包的集合是通过使用功能清单文件控制。 功能清单提供给不同类型的图像添加可选包套的可扩展基础结构生成。 WDK 包括名为 MSOptionalFeaturesFM.xml，一个功能清单，Oem 还可以创建他们自己。 功能清单引用**AdditionalFMs** OEMInput XML 文件的元素中。 功能清单的内容的详细信息，请参阅[功能清单文件的内容](feature-manifest-file-contents.md)。

当 OEMInput XML 文件引用功能清单时，有很多种其他的可选软件包将包括在映像中︰

-   功能清单文件中的**BasePackages**元素下面列出的任何包会自动包括在映像中。

-   如**ReleasePackages**和**DeviceSpecificPackages**是包括如果图像定义匹配功能清单文件中的元素指定的参数在元素下，功能清单文件中所列其他包。 例如，如果功能清单文件列出了**ReleasePackages**元素的版本类型是**测试**下一个包，包将包括只有在配置了 OEMInput 文件来生成测试映像。

-   在 OEMInput 文件中添加其他可选的软件包中的 OEM 或 Microsoft**的功能**元素可以引用任何的功能清单中定义的可选功能。 功能是一个字符串，标识可以在图像中包含的一个或多个可选包。 通常情况下，功能标识一组与特定组件或功能区域相关的软件包。 有关在 OEMInput 文件中使用由 Microsoft 提供的可选功能的详细信息，请参阅构建映像的可选功能。

-   这取决于谁将使用图像，可能适合使用**ExcludePrereleaseFeatures**元素的预发行功能中排除。 有关详细信息，请参阅[OEMInput 文件的内容](oeminput-file-contents.md)。

### <a name="a-href-idconfiguringtheoeminputfileaconfiguring-the-oeminput-file-to-integrate-feature-changes-from-the-microsoft-samples"></a><a href="" id="configuringtheoeminputfile"></a>配置集成功能更改 Microsoft 样本从 OEMInput 文件

任何 MobileOS 发行版中，从以前的版本可能会改变由 Microsoft 提供的 OEMInput 示例。 例如，Microsoft 定义功能可添加到示例才能引入最新的操作系统组件可用，或者可能从示例删除 Microsoft 定义的特征，如果他们不再支持某些图像类型。 若要确保 Oem 构建每个 MobileOS 发布正确的图像，Microsoft 建议 Oem 遵守以下过程。

1.  结构的**AdditionalFMs**和功能相关的元素，如下面的示例中所示的 OEMInput 文件中。 在每个部分，包括的功能清单和第一次，由 Microsoft 示例的功能，则包括 OEM 指定的功能清单和功能。 使用注释来清晰地分隔每个组的功能清单和功能，并清楚地解释了为什么在文件中包含每个 OEM 特定的功能。

    如果从 Microsoft 样本偏差的 OEMInput 文件中的**AdditionalFMs**和**功能**元素的内容，包括详细解释为什么发生了更改的注释。 如果任何更改引入作为临时解决办法的问题，临时的解决方法应做出解释这样的工程师使用文件以后可以确定是否要保留更改或 OEM 集成新的 BSP 或套件时，将恢复与 Microsoft 的示例。

    ``` syntax
    <!-- From Microsoft sample OEMInput.xml file -->
    <AdditionalFMs>
      <AdditionalFM>%WDKCONTENTROOT%\FMFiles\MSOptionalFeatures.xml</AdditionalFM> 
        <!-- Add OEM FM files here -->
    </AdditionalFMs>

    <Features>
       <Microsoft>
        <!-- Features from Microsoft OEMInput sample -->
        <!-- Additional OEM-selected features defined by Microsoft
             Include detailed comments about why each feature was chosen for this image -->
       </Microsoft>
       <OEM>
        <!-- Additional OEM-selected features defined by the OEM
             Include detailed comments about why each feature was chosen for this image  -->
       </OEM>
    </Features>
    ```

2.  当 OEM 集成新的 WDK 和 MobileOS 版中，比较 OEMInput 示例从 oem 创建的 OEMInput 文件中的相同元素的最新版本中的**功能**元素。

3.  标识在最新的示例中，Microsoft 指定功能的任何更改和端口为**功能**元素，由 OEM 创建的 OEMInput 文件中的更改。

## <a name="a-href-idusingimggenausing-imggencmd-to-generate-the-image"></a><a href="" id="usingimggen"></a>在使用 ImgGen.cmd 生成图像


ImgGen.cmd 是配合适当的参数以创建 FFU 映像运行图像处理工具 (ImageApp.exe) 的命令文件。 ImgGen.cmd 还运行实用程序的应用程序，DeviceNodeCleanup，ImageApp.exe 每次运行之后。 运行 DeviceNodeCleanup 有助于确保开发计算机上的注册表是干净而不会增加启动时间。 ImgGen.cmd 和其他相关组件都位于 %WPDKCONTENTROOT%\\工具\\bin\\i386。

若要使用 ImgGen.cmd 生成一个图像︰

1.  开发计算机的配置，如下所示︰

    -   以管理员身份打开**开发人员为 VS2013 的命令提示符**窗口 （如果安装了 Visual Studio 2013年） 或**命令提示符**窗口 （如果您没有安装 Visual Studio 2013年）。

    -   请确认 TEMP 环境变量，指的是未压缩或加密使用的加密文件系统 (EFS) 功能的目录。 如果 TEMP 环境变量引用的目录不能满足这些要求，并且不希望修改该变量或目录属性，或者可以创建一个二进制文件\_根环境变量并将其设置为同时满足这些要求的现有目录。 如果这些位置都不存在，或者如果它们存在，但会压缩或加密，就不能生成图像和 ImageApp.exe 工具将返回错误。

    -   如果您运行的 Windows 8.1，完成其他步骤以在生成计算机上将 USN 日志的注册表大小设置为 1 Mb。

        1.  通过管理员命令提示符下运行以下命令来更改 USN 的最小大小注册表项︰

            ``` syntax
            reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\FileSystem  /v NtfsAllowUsnMinSize1Mb  /t REG_DWORD  /d 1
            ```

        2.  生成图像之前，重新启动电脑。

2.  在命令提示符窗口中，使用下面的语法运行 ImgGen.cmd。 请参阅下一节有关参数的详细信息。

    ``` syntax
    ImgGen.cmd OutputFile OEMInputXML MSPackageRoot OEMCustomizationXML OEMCustomizationVer
    ```

### <a name="command-line-syntax-for-imggencmd"></a>ImgGen.cmd 的命令行语法

下表介绍的 ImgGen.cmd 命令行参数。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>参数</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>输出文件</em></p></td>
<td><p>要创建 FFU 文件的名称。 如果不包括路径，则将在当前目录中创建 FFU 文件。 包含的路径时，如果指定的路径必须已经存在。 FFU 文件使用 ffu 的文件扩展名。</p></td>
</tr>
<tr class="even">
<td><p><em>OEMInputXML</em></p></td>
<td><p>OEMInput xml 文件定义要创建的映像的名称。 如果此文件不在当前目录中，则必须包括文件的路径。</p></td>
</tr>
<tr class="odd">
<td><p><em>MSPackageRoot</em></p></td>
<td><p>为包含 Microsoft 文件包的根目录路径。 默认情况下，此目录是 %programfiles(x86) %\Windows Kits\10\MSPackages （或下 %programfiles%运行 32 位版本的 Windows 的计算机上的相应路径）。</p></td>
</tr>
<tr class="even">
<td><p><em>OEMCustomizationXML</em></p></td>
<td><p>OEM 自定义 XML 文件的路径。 有关自定义答案文件的详细信息，请参阅<a href="https://msdn.microsoft.com/library/windows/hardware/dn75745">自定义答案文件</a>
</tr>
<tr class="odd">
<td><p><em>OEMCustomizationVer</em></p></td>
<td><p>将用于生成 OEM 自定义软件包的版本号。</p></td>
</tr>
</tbody>
</table>

 

### <a name="usage-samples"></a>用法示例

下面的示例显示 ImgGen.cmd 的基本用法。

``` syntax
ImgGen Flash.ffu OEMInput.xml "%WPDKCONTENTROOT%\MSPackages" OEMCustomization.XML 8.1.0.1
```

### <a name="output-files"></a>输出文件

由指定的文件夹中已成功生成一个映像后*FFU\_文件*命令行参数、 成像工具复制以下文件复制到输出 FFU 文件的文件夹︰

-   &lt;*FFUName*&gt;。ImageApp.log︰ 此文件包含有关创建映像的所有日志记录信息。 此文件以及控制台窗口中报告任何故障。

-   &lt;*FFUName*&gt;。UpdateOutput.xml︰ 该文件介绍了每个软件包应用于图像。

-   &lt;*FFUName*&gt;。UpdateHistory.xml︰ 此文件包含所有更新和成像图像发生的事件的列表。

-   &lt;*FFUName*&gt;。UpdateInput.xml︰ 此文件列出的所有货物包括在映像中。

-   &lt;FFUName&gt;。PackageList.xml︰ 这是在图像中所包含的包文件的列表。

-   &lt;FFUName&gt;.cat︰ 这是代码签名可以用于签名图像的目录。 有关详细信息，请参阅[全闪存更新 (FFU) 图像符号](sign-a-full-flash-update--ffu--image.md)。

如果提供自定义答案文件，则会生成此文件︰

-   &lt;所有者&gt;。&lt;设备名称&gt;。自定义项。&lt;分区&gt;.spkg

如果任何自定义项包括静态应用程序时，将生成以下文件。

-   &lt;所有者&gt;。&lt;设备名称&gt;。CustomizationsApps.spkg

## <a name="generating-customization-packages-without-creating-an-image"></a>如果未创建映像生成自定义软件包


若要处理自定义答案文件而无需创建图像，请使用**CustomizationGen.cmd**。 CustomizationGen.cmd 应用的所有自定义规则并生成自定义软件包。 它跳过生成 ffu 图像的最后一步。 语法是类似于 ImgGen.cmd。

例如，为了处理应答文件和构建自定义软件包，可使用此命令。

``` syntax
CustomizationGen.cmd C:\OEMCustomization OEMInput.xml "%WPDKCONTENTROOT%\MSPackages" OEMCustomization.XML 8.0.0.1
```

### <a name="command-line-syntax-for-customizationgencmd"></a>CustomizationGen.cmd 的命令行语法

下表介绍的 CustomizationGen.cmd 命令行参数。 所有的参数都是必需的。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>参数</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>输出目录</em></p></td>
<td><p>对于 OEM 自定义软件包将创建输出目录的路径。</p></td>
</tr>
<tr class="even">
<td><p><em>OEMInputXML</em></p></td>
<td><p>OEMInput xml 文件定义要创建的映像的名称。 如果此文件不在当前目录中，则必须包括文件的路径。</p></td>
</tr>
<tr class="odd">
<td><p><em>MSPackageRoot</em></p></td>
<td><p>为包含 Microsoft 文件包的根目录路径。 默认情况下，此目录是 %programfiles(x86) %\Windows Kits\10\MSPackages （或下 %programfiles%运行 32 位版本的 Windows 的计算机上的相应路径）。</p></td>
</tr>
<tr class="even">
<td><p><em>OEMCustomizationXML</em></p></td>
<td><p>OEM 自定义 XML 文件的路径。</p></td>
</tr>
<tr class="odd">
<td><p><em>OEMCustomizationVer</em></p></td>
<td><p>这是将用于生成 OEM 自定义软件包的版本号。</p></td>
</tr>
</tbody>
</table>

 

## <a name="large-scale-image-generation-recommendations"></a>大规模的图像生成建议


在工作站上反复生成图像，时，可能不时地出现可以虚拟硬盘 (VHD) 操作错误。 如果发生下列错误，您可以重新运行图像生成过程。 所有中间文件应自动清除由 ImageApp。 本节提供配置信息的电脑，将在尽量减少可能发生的错误数的大规模自动化的图像生成环境中生成图像的指导。

若要生成大量的图像，请考虑以下建议︰

-   删除或禁用图像生成计算机上的防病毒软件。 防病毒软件，并在特定的文件系统筛选器通常用于监视的活动，存在可以在图像生成过程产生重大影响。 至少，病毒扫描应禁用输入和输出目录和所有进程所涉及的生成，但这通常不禁用文件系统筛选器感兴趣。 某些防病毒软件的供应商可能会提供设置，以允许扫描活动要推迟或计划可能减轻对图像生成过程的影响。 其他安全措施可就地隔离系统免受病毒和其他软件的风险，如果删除或禁用图像生成计算机上的病毒软件。 暂时删除病毒软件可帮助隔离对图像生成过程，以确定进一步调查属于保修范围的影响。

-   Windows Server 2012 Microsoft 实验室里使用，建议使用。 应将服务器配置的最大文件输入/输出性能。

-   映像创建过程不应运行在虚拟机 (Vm)，但在物理计算机上相反。

-   不与文件系统相关的所有其他服务 （如打印或 HTTP 服务） 应该在服务器上禁用。

-   系统活动跟踪可帮助您识别互动安装 Vhd 的生成计算机上的进程。 任何并非由成像工具的交互应该避免如果可能的话，可能会禁用磁盘装入对其执行操作的服务。

-   在 PC 上的输出驱动器应该写入缓存缓冲区刷新被禁用。 在文件服务器上，使用此设置在一定的风险，但与图像生成，此设置是可以接受的因为如果发生断电的成像数据可以重新创建。 如果其他数据不能在服务器上重新创建，使用时要格外小心，此设置，因为可能会损坏数据。

## <a name="related-topics"></a>相关的主题


[构建和闪烁移动图像](building-and-flashing-images.md)

[OEMInput 文件的内容](oeminput-file-contents.md)

[签名的完整闪存更新 (FFU) 图像](sign-a-full-flash-update--ffu--image.md)

 

 

[发送有关此主题的意见的评论](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_phFlashing\p_phFlashing%5D:%20Build%20a%20mobile%20image%20using%20ImgGen.cmd%20%20RELEASE:%20%2810/4/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "发送有关此主题的意见的评论")





