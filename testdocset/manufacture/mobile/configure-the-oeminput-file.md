---
Description: "OEMInput 文件指定设备平台、 的功能清单文件、 版本类型、 设备模型、 生成类型，语言要支持、 引导用户界面语言、 设备分辨率和其他属性，如您想要包括图像的一部分的可选功能。"
ms.assetid: 67dc279e-a7f6-4686-bebf-6d0098d0f782
MSHAttr: PreferredLib:/library
title: "将 OEMInput 文件配置"
author: CelesteDG
ms.openlocfilehash: 6fed5046470a2e98da965906f9837942187fa8c2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="configure-the-oeminput-file"></a>将 OEMInput 文件配置


既然已经在 MCSF 咖啡馆中配置自定义设置，并在 OEM 清单文件中添加自定义的 OEM 功能，您需要创建的 OEMInput 文件，指定设备平台、 的功能清单文件、 版本类型、 设备模型、 生成类型，语言要支持、 引导用户界面语言、 设备分辨率和其他属性，如您想要包括图像的一部分的可选功能。

在 OEMInput 文件中的每个元素的详细信息，请参阅[OEMInput 文件的内容](https://msdn.microsoft.com/library/windows/hardware/dn756778)。

在本演练中，我们将添加[添加 OEM 清单文件包](#adding-a-package-to-an-oem-manifest-file)，指定我们想要支持的语言和定义图像的其余部分中，我们定义的两种功能。

**若要配置 OEMInput 文件**

1.  创建一个新的 OEMInput.xml 文件或修改现有的 OEMInput 文件。 示例中的 OEMInput.xml 文件看起来，请参阅 %WPDKCONTENTROOT%\\OEMInputSamples\\伪造工具包安装文件夹中。

    在以下示例中，我们复制内容的 %WPDKCONTENTROOT%\\OEMInputSamples\\虚假\\TestOEMInput.xml 文件并进行如下修改︰

    -   添加新的说明。

    -   添加英语 （英国），法语 （法国）、 西班牙语 （西班牙） 和中文 （简体） 到列表中包含的设备语言除了英语 （美国）。 我们在**UserInterface**部分添加此。 您可以向您的移动设备添加其他语言的详细信息，其中包括如何更改默认设备语言和区域的格式，请参阅[移动设备的语言](https://msdn.microsoft.com/library/windows/hardware/dn772212)。

    -   添加 ContosoOptionalFeatures.xml 功能清单文件，我们在[添加 OEM 清单文件包](#adding-a-package-to-an-oem-manifest-file)本演练中创建并放置它在 OEMInput 文件的**AdditionalFMs**部分下通过添加新的**AdditionalFM**项和指定的位置和名称的功能清单文件。

    -   添加回音\_驱动程序和快速\_操作功能，通过添加新的**OEM**节内的 OEMInput 文件的**功能**部分。 对于每个**OEM**部分中，我们添加的功能，我们将添加新的**功能**项，然后指定我们的功能清单文件中定义的功能的名称。

    **请注意** 如果您使用的是移动设备参考设备，请确保更新在 OEMInput.xml 的**SOC**、 **SV**和**设备**部分的值。 您还可以更改取决于您尝试**ReleaseType** 。 请确保您按照中[OEMInput 文件的内容](https://msdn.microsoft.com/library/windows/hardware/dn756778)的指南时指定这些元素的值。

     

    ```XML
    <?xml version="1.0" encoding="utf-8"?>
    <OEMInput xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
              xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
              xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate">
      <Description>Windows mobile image test FFU generation</Description>
      <SOC>FAKE_SOC_Test</SOC>
      <SV>Microsoft</SV>
      <Device>FAKE</Device>
      <ReleaseType>Test</ReleaseType>
      <BuildType>fre</BuildType>
      <SupportedLanguages>
        <UserInterface>
          <Language>en-US</Language>
          <Language>en-GB</Language>
          <Language>fr-FR</Language>
          <Language>es-ES</Language>
          <Language>zh-CN</Language>
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
        <AdditionalFM>%WPDKROOT%\FMFiles\arm\ContosoOptionalFeatures.xml</AdditionalFM>
        <AdditionalFM>%WPDKROOT%\FMFiles\arm\MSOptionalFeatures.xml</AdditionalFM>
      </AdditionalFMs>
      <Features>
        <Microsoft>
          <Feature>IMGFAKEMODEM</Feature>
          <Feature>TEST_DISABLE_DISK_IDLE</Feature>
          <Feature>STANDARD_FEATURE_1</Feature>
          <Feature>CODEINTEGRITY_TEST</Feature>
          <Feature>SELFHOST_AUTOMATIC_DEVICE_CONFIGURATOR</Feature>
          <Feature>LOCATIONFRAMEWORKAPP</Feature>
          <Feature>FACEBOOK</Feature>
          <Feature>COMMSENHANCEMENTGLOBAL</Feature> 
          <Feature>KDNETUSB_TEST_ON</Feature>
          <Feature>TESTINFRASTRUCTURE</Feature>
          <Feature>TEST</Feature>
          <Feature>STARTUPOVERRIDES</Feature>
          <Feature>GWPCERTTESTPROV</Feature>
          <Feature>MOBILECORE_TEST</Feature>
          <Feature>DRIVERS_WDTFINFRA</Feature>
          <Feature>SKYPE</Feature>
          <Feature>BOOTSEQUENCE_TEST</Feature>
          <Feature>SKIPOOBE</Feature>
          <Feature>CORTANADBG_TEST_PROTECTED</Feature>
          <Feature>TEST_PROTECTED</Feature>
          <Feature>PSEUDOLOCALES</Feature>
        </Microsoft>
        <OEM>
          <Feature>ECHO_DRIVER</Feature>
          <Feature>QUICK_ACTIONS</Feature>
        </OEM>
      </Features>
      <Product>Windows Phone</Product>
    </OEMInput>
    ```

2.  命名并保存您的 OEMInput.xml 文件。 对于我们的示例中，我们命名它为 ContosoTestOEMInput.xml，它保存在 %WPDKCONTENTROOT%\\ContosoOEMInput 文件夹。

 

 



