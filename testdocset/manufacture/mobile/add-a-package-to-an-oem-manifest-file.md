---
Description: "功能清单 (FM) 文件可用于定义特定类型的图像生成的包含不同的可选包。"
ms.assetid: 5355eea8-550f-4ab5-ba1c-a37689a88b95
MSHAttr: PreferredLib:/library
title: "将软件包添加到 OEM 的清单文件"
author: CelesteDG
ms.openlocfilehash: f38e04e7fc0c40ff742df0971a79134ca79a5b1a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add-a-package-to-an-oem-manifest-file"></a>将软件包添加到 OEM 的清单文件


功能清单 (FM) 文件可用于定义特定类型的图像生成的包含不同的可选包。 若要了解有关 FM 文件的详细信息，请参阅[功能清单文件的内容](https://msdn.microsoft.com/library/windows/hardware/dn756745)。 有关额外的逻辑，可以将其添加到生成系统的详细信息，请参阅[功能分组和约束](https://msdn.microsoft.com/library/windows/hardware/dn756740)。

在本演练中，我们将添加到 FM 文件来定义新的 OEM 功能，以后可以包含生成的移动操作系统映像中[创建移动包](creating-mobile-packages.md)，创建该程序包。

**将软件包添加到 FM 文件**

1.  创建一个新的调频文件或修改现有调频广播文件包括您创建的两个包并定义这些软件包的功能 Id。 有关示例的 FM 文件看起来，请参阅 %WPDKCONTENTROOT%\\FMFiles\\arm\\MSOptionalFeatures.xml 工具包安装文件夹中的。

    下面的示例演示 FM 文件可能如下所示。

    ```XML
    <?xml version="1.0" encoding="utf-8"?>
    <FeatureManifest 
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
      xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
      xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate">

      <!-- Other elements that you can configure
      <OEMDevicePlatformPackages>
        <PackageFile Name="Microsoft.Fake.OEMDevicePlatform.spkg" Path="$(mspackageroot)\firmware\Fake\$(cputype)\$(buildtype)" Device="Fake"/>
      </OEMDevicePlatformPackages>

      <BasePackages>
        <PackageFile Path="$(mspackageroot)\drivers\Fake\$(cputype)\$(buildtype)" Name="Microsoft.Fake.AX88772.spkg"/>
      </BasePackages>
      -->

      <Features>  
        <OEM>  
          <PackageFile Path="SourceDirectoryA" Name="MyEchoDriver.spkg">  
            <FeatureIDs>  
              <FeatureID>ECHO_DRIVER</FeatureID>  
            </FeatureIDs>  
          </PackageFile>  
          <PackageFile Path="SourceDirectoryB" Name="Contoso.Customization.Notifications.QuickActions.spkg">  
            <FeatureIDs>  
              <FeatureID>QUICK_ACTIONS</FeatureID>  
            </FeatureIDs>  
          </PackageFile>  
        </OEM>  
      </Features> 

    </FeatureManifest>
    ```

    **OEMDevicePlatformPackages**元素和**BasePackages**元素占位符，而仅有向您显示哪些其它选项均可用于配置 FM 文件中。

    有关创建调频广播文件以及其他元素，您可能需要完全定义您的功能的详细信息，请参阅[功能清单文件的内容](https://msdn.microsoft.com/library/windows/hardware/dn756745)。 有关额外的逻辑，可以将其添加到生成系统的详细信息，请参阅[功能分组和约束](https://msdn.microsoft.com/library/windows/hardware/dn756740)。

2.  在**OEM**部分中的第一个**PackageFile**元素，将*SourceDirectoryA*替换为包含 Echo 驱动程序包的文件夹的位置，将*MyEchoDriver.spkg*替换为包含驱动程序.spkg 的真实名称。

3.  在第二个**PackageFile**元素中的**OEM**部分中，将*SourceDirectoryB*替换为包含自定义设置包文件夹的位置并将*Contoso.Customization.Notifications.QuickActions.spkg*替换为包含自定义设置.spkg 的真实名称。

4.  FM 文件保存在 %WPDKCONTENTROOT%\\FMFiles\\臂文件夹。 对于此示例，让我们以 ContosoOptionalFeatures.xml 命名该文件。

 

 



