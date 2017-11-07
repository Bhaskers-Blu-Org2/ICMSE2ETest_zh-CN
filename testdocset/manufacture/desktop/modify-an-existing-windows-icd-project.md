---
author: Justinha
Description: "通常可以转回 Windows 图像处理和配置设计器 (ICD) 项目，编辑并一次次地重新部署。"
ms.assetid: 88b2c902-4bd2-4d09-814b-be86c75c8085
MSHAttr: PreferredLib:/library/windows/hardware
title: "实验室 1 c︰ 修改现有的 Windows ICD 项目"
ms.openlocfilehash: 2f25e2bb65d4c2970894cc961bfe94961ffe531c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="lab-1c-modify-an-existing-windows-icd-project"></a>实验室 1 c︰ 修改现有的 Windows ICD 项目


通常可以转回 Windows 图像处理和配置设计器 (ICD) 项目，编辑并一次次地重新部署。

**请注意** 将资源调配程序包一样，任何新的源文件复制回电脑前开始技术人员。 这减少了中断生成过程从暂时的网络问题或断开 USB 设备的风险。

 

## <a name="span-idchangetheeditionforexamplefromcoretoprospanspan-idchangetheeditionforexamplefromcoretoprospanspan-idchangetheeditionforexamplefromcoretoprospanchange-the-edition-for-example-from-core-to-pro"></a><span id="Change_the_edition__for_example__from_Core_to_Pro_"></span><span id="change_the_edition__for_example__from_core_to_pro_"></span><span id="CHANGE_THE_EDITION__FOR_EXAMPLE__FROM_CORE_TO_PRO_"></span>更改 （例如，从核心到 Pro） 版


将 Windows ICD 项目导出到一个包中提供。 然后可以在 Windows ICD 使用该包提供快速建立在不同版本中的新图像创建一个新项目。

## <a name="span-idtousemorethanoneprovisioningpackagespanspan-idtousemorethanoneprovisioningpackagespanspan-idtousemorethanoneprovisioningpackagespanto-use-more-than-one-provisioning-package"></a><span id="To_use_more_than_one_provisioning_package_"></span><span id="to_use_more_than_one_provisioning_package_"></span><span id="TO_USE_MORE_THAN_ONE_PROVISIONING_PACKAGE_"></span>若要使用多个配置文件包︰


使用 ICD.exe 命令来组合配置包。

``` syntax
"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Imaging and Configuration Designer\x86\icd.exe" /Build-ImageFromWIM /MediaPath:"c:\WICDOutput" /SourceImage:"C:\Images\install.wim" /ImageIndex:1 /ProvisioningPackage:"c:\users\terry\Documents\Windows Imaging and Configuration Designer (WICD)\Fabrikam_Notebook_1\Fabrikam_Notebook_1.ppkg" /DeploymentConfigXml:"C:\Samples\DeploymentConfig.xml" /CustomizationXML:"C:\Samples\Customizations.xml" 
```

其中 /ImageIndex 是您想要使用的 Windows 映像的索引。 注意要使用的 Windows 映像。 客户端的 SKU install.wim 文件包括两个不同的图像︰

-   索引 1 是 Windows 10 专业版
-   索引 2 是 Windows 10 核心

## <a name="span-idcreateadeploymentconfigurationfilespanspan-idcreateadeploymentconfigurationfilespanspan-idcreateadeploymentconfigurationfilespancreate-a-deployment-configuration-file"></a><span id="Create_a_deployment_configuration_file"></span><span id="create_a_deployment_configuration_file"></span><span id="CREATE_A_DEPLOYMENT_CONFIGURATION_FILE"></span>创建一个部署配置文件


ICD.exe 命令要求部署配置 XML 文件。 当您使用 WICD 用户界面时，会为您创建此文件。 当使用命令行 ICD，必须创建它并将其指定为命令中的 DeploymentConfigXml 参数。 下面是一个示例，它可用于此实验室︰

``` syntax
<?xml version="1.0" encoding="UTF-8"?>
<DeploymentConfig xmlns="urn:schemas-Microsoft-com:Windows-ICD-Deployment-Config.v1.0">
    <EnableCompactOS>false</EnableCompactOS>
    <MediaScenario>Production</MediaScenario>
</DeploymentConfig>
 
```

ICD Windows 将在您选择的路径中创建项目。 然后可以将此数据复制到 USB 钥匙并加载新的 PC 上的图像。

## <a name="span-idcreateablankcustomizationsfilespanspan-idcreateablankcustomizationsfilespanspan-idcreateablankcustomizationsfilespancreate-a-blank-customizations-file"></a><span id="Create_a_blank_customizations_file"></span><span id="create_a_blank_customizations_file"></span><span id="CREATE_A_BLANK_CUSTOMIZATIONS_FILE"></span>创建一个空白的自定义文件


对于此版本的 Windows 10 中，必须使用 CustomizationXML 参数指定的自定义文件。 因此，我们将创建用于本实验室的空白的自定义 XML 文件供应包应包含所有自定义︰

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<WindowsCustomizations>
  <PackageConfig xmlns="urn:schemas-Microsoft-com:Windows-ICD-Package-Config.v1.0">
    <ID>{c4b32e84-249f-4a07-976a-e482f0a2ee58}</ID>
    <Name>Fabrikam_Notebook_1_Core</Name>
    <Version>1.0</Version>
    <OwnerType>OEM</OwnerType>
    <Rank>0</Rank>
  </PackageConfig>
  <Settings xmlns="urn:schemas-microsoft-com:windows-provisioning">
</Settings>
</WindowsCustomizations>

 
```

## <a name="span-idcongratulationsspanspan-idcongratulationsspanspan-idcongratulationsspancongratulations"></a><span id="Congratulations_"></span><span id="congratulations_"></span><span id="CONGRATULATIONS_"></span>祝贺您 ！


您完成了实验室的 Windows ICD 部分。 从这里，您可以了解有关在[实验室 2](part-2--classic-style-deployment.md)经典 Windows 部署技术。

 

 





