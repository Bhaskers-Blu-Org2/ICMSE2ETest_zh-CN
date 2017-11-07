---
title: "功能清单文件的内容"
description: "功能清单 (FM) 文件用于定义特定类型的图像生成的包含不同的可选包。 本主题介绍了调频文件中的必需和可选元素。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: ffed39b7-4dd0-48f6-b284-ddaf897beade
ms.openlocfilehash: bdeff28ab8111ceb9b7150002dc2f0be009caf92
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="feature-manifest-file-contents"></a>功能清单文件的内容


*功能清单 (FM) 文件*用于定义特定类型的图像生成的包含不同的可选包。 本主题介绍了调频文件中的必需和可选元素。 有关如何生成图像时使用的调频文件的详细信息，请参阅[构建使用 ImgGen.cmd 电话映像](building-a-phone-image-using-imggencmd.md)。

**请注意**  
大部分 FM 文件中的元素包括一个包的路径。 如果该软件包是 Microsoft 包的根目录下 (%WPDKCONTENTROOT%\\MSPackages)，此路径可以在路径名称中使用 $(mspackageroot) 宏。 如果程序包位于其他位置，可以使用环境变量，例如，%oempackageroot%，并在命令行窗口中设置此环境变量。

 

## <a name="example-fm-file"></a>调频广播的示例文件


下面的示例演示一个示例 OEM FM 文件。

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<FeatureManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
  xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
  xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate">
  <BasePackages>
    <PackageFile Path="%oempackageroot%\common\" 
      Name="Contoso.Phone.Test.BaseOs.EnvPath.spkg" />
  </BasePackages>
  <Features>
    <OEM>
     <PackageFile Path="%oempackageroot%\test\" 
      Name="Contoso.Test.MinTE.spkg">
        <FeatureIDs>
          <FeatureID>TEST_FEATURE1</FeatureID>
        </FeatureIDs>
      </PackageFile>
   </OEM>
</Features>
  <ReleasePackages> 
    <PackageFile FeatureIdentifierPackage="true" Name="Contoso.BaseOS.BootApplications_Test.spkg" 
Path="%oempackageroot%\test" ReleaseType="Test"/> 
  </ReleasePackages> 
  <PrereleasePackages>
    <PackageFile ID="Contoso.MainOS.Protected_Replacement_Production" FeatureIdentifierPackage="true" 
Name="Contoso.MainOS.Protected_Replacement_Production.spkg" Path="%oempackageroot%\Merged\" Resolution="*" Type="replacement" Language="*"/>
  </PrereleasePackages>
<OEMDevicePlatformPackages>
    <PackageFile Name="SoCVendor.DCD6000.OEMDevicePlatform.spkg" Path="%oempackageroot%\DCD6000\" Device="DCD6000"/>  
</OEMDevicePlatformPackages>
</FeatureManifest>
```

您可能要检查所包含的 mobileOS packagesunder %WPDKCONTENTROOT%MSOptionalFeaturesFM.xml\\FMFiles 若要查看附加的 FM XML 文件。

## <a name="elements-in-a-fm-file"></a>FM 文件中的元素


以下各节描述了支持的 FM 文件中的元素。

### <a name="featuremanifest"></a>FeatureManifest

**FeatureManifest**元素是调频文件中的根 XML 元素。 此元素是该文件中的所有其他元素的基的容器元素。 它必须只出现一次。

### <a name="basepackages"></a>BasePackages

**BasePackages**元素指定如果 FM 文件引用 OEMInput XML 文件的**AdditionalFMs**元素中始终包括在映像中的程序包。 **BasePackages**元素具有不支持的属性。

下表描述的**BasePackages**元素的子元素。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>元素</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>PackageFile</strong></p></td>
<td><p>可选项。 此元素描述将在图像中包含的包。 此元素支持下列特性︰</p>
<ul>
<li><p><strong>路径</strong>– 必需。 包路径。</p></li>
<li><p><strong>名称</strong>– 必需。 包文件的名称。</p></li>
<li><p><strong>分辨率</strong>– 可选。 一个字符串，包含软件包支持的显示器分辨率。 可以指定此属性，使用下面的值︰</p>
<ul>
<li><p>&quot;*&quot;: &quot; * &quot;字符表示包支持每次解析。</p></li>
<li><p>&quot;（720 x 1280; 768 x 1280）&quot;︰ 此语法表示的一套程序包支持的分辨率。 程序包包含仅在生成一个在此列表中的分辨率的图像。</p></li>
<li><p>&quot;!（720 x 1280; 768 x 1280）&quot;: A '！' 前面分辨率列表指定程序包支持所有除与列表中的分辨率。 包包含只在不构建一个在此列表中的分辨率的图像。</p></li>
</ul></li>
<li><p><strong>语言</strong>– 可选。 一个字符串，包含软件包支持的显示语言代码。 可以指定此属性，使用下面的值︰</p>
<ul>
<li><p>&quot;*&quot;: &quot; * &quot;字符表示包支持每种语言。</p></li>
<li><p>&quot;（EN-US; ZH-CN）&quot;︰ 此语法所示软件包支持的语言集。 程序包包含仅在包含此列表中的显示语言之一的图像。</p></li>
<li><p>&quot;!（EN-US; ZH-CN）&quot;: A ' ！ 列表指定程序包支持除所有语言或列表中的那些语言的前面。 包包含仅在图像不包含在此列表中的显示语言之一。</p></li>
</ul></li>
<li><p><strong>分区</strong>– 可选。 一个字符串，指定程序包的目标分区。 默认情况下，除非显式指定了另一个包到 MainOS 分区中安装。</p></li>
</ul>
<p>这些元素是 Microsoft 仅供内部使用。</p>
<ul>
<li><p><strong>ID</strong> – 可选。 字符串值。 该 ID 是包名。 Oem 不应使用此特性。</p></li>
<li><p><strong>NoBasePackage</strong> – 可选。 布尔值。 设置为 true 的语言和/或不包含基本产品包的解决方案包。 Oem 不应使用此特性。</p></li>
<li><p><strong>FeatureIdentifierPackage</strong> – 可选。 布尔值。 Oem 不应使用此特性。</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

### <a name="features"></a>功能

有**Microsoft**和**OEM**的元素，其中每个可以包含**的功能**。 OEM 应该只添加到其功能**&lt;OEM&gt;**元素。 这提供了多种好处，包括更容易集成到 OEM 的生成系统 OEMInput.xml 文件的较新版本。

**功能**元素定义要在图像中包含可选包的 OEMInput 文件中的**功能**元素可以引用的一个或多个可选功能。 **功能**元素具有不支持的属性。

下表描述的**功能**元素的子元素。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>元素</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>PackageFile</strong></p></td>
<td><p>可选项。 此元素描述一个包，其中将包括在映像中，如果 OEMInput 文件引用了此功能。</p>
<p>此元素支持下列特性︰</p>
<ul>
<li><p><strong>路径</strong>– 必需。 包路径。</p></li>
<li><p><strong>名称</strong>– 必需。 包文件的名称。</p></li>
<li><p><strong>分辨率</strong>– 可选。 一个字符串，包含软件包支持的显示器分辨率。 可以指定此属性，使用下面的值︰</p>
<ul>
<li><p>&quot;*&quot;: &quot; * &quot;字符表示包支持每次解析。</p></li>
<li><p>&quot;（720 x 1280; 768 x 1280）&quot;︰ 此语法表示的一套程序包支持的分辨率。 程序包包含仅在生成一个在此列表中的分辨率的图像。</p></li>
<li><p>&quot;!（720 x 1280; 768 x 1280）&quot;: A '！' 前面分辨率列表指定该程序包支持所有除与列表中的分辨率。 包包含只在不构建一个在此列表中的分辨率的图像。</p></li>
</ul></li>
<li><p><strong>语言</strong>– 可选。 一个字符串，包含软件包支持的显示语言代码。 可以指定此属性，使用下面的值︰</p>
<ul>
<li><p>&quot;*&quot;: &quot; * &quot;字符表示包支持每种语言。</p></li>
<li><p>&quot;（EN-US; ZH-CN）&quot;︰ 此语法所示软件包支持的语言集。 程序包包含仅在包含此列表中的显示语言之一的图像。</p></li>
<li><p>&quot;!（EN-US; ZH-CN）&quot;: A ' ！ 在语言列表指定该程序包支持除与列表中的所有语言。 包包含仅在图像不包含在此列表中的显示语言之一。</p></li>
</ul></li>
<li><p><strong>分区</strong>– 可选。 一个字符串，指定程序包的目标分区。 默认情况下，除非显式指定了另一个包到 MainOS 分区中安装。</p></li>
</ul>
<p>此元素支持下列子元素︰</p>
<ul>
<li><p><strong>FeatureIDs</strong> – 必需。 包含一个或多个<strong>FeatureID</strong>元素。 <strong>FeatureID</strong>中的每个元素包含一个字符串值，指定的名称将与指定父<strong>PackageFile</strong>元素的包相关联的功能。</p></li>
</ul>
<p>这些元素是 Microsoft 仅供内部使用。</p>
<ul>
<li><p><strong>CPUType</strong> – 必需。 字符串值。 设置 CPU 类型。 可以设置为<em>x86</em>或<em>臂</em>。 Oem 不应使用此特性。</p></li>
<li><p><strong>ID</strong> – 可选。 字符串值。 该 ID 是包名。 Oem 不应使用此特性。</p></li>
<li><p><strong>NoBasePackage</strong> – 可选。 布尔值。 设置为 true 的语言和/或不包含基本产品包的解决方案包。 Oem 不应使用此特性。</p></li>
<li><p><strong>FeatureIdentifierPackage</strong> – 可选。 布尔值。 Oem 不应使用此特性。</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

### <a name="feature-groupings-and-constraints"></a>分组功能和约束

分组功能和约束可以用于管理功能。 有关详细信息，请参阅[功能分组和约束](feature-groupings-and-constraints.md)。

### <a name="releasepackages"></a>ReleasePackages

**ReleasePackages**元素指定特定的版本类型，指定的 OEMInput 文件中的**ReleaseType**元素的图像中包含的包。 **ReleasePackages**元素具有不支持的属性。

下表描述的**ReleasePackages**元素的子元素。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>元素</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>PackageFile</strong></p></td>
<td><p>可选项。 此元素描述一个包。</p>
<p>此元素支持下列特性︰</p>
<ul>
<li><p><strong>ReleaseType</strong> – 必需。 <strong>生产</strong>或<strong>测试</strong>软件包支持的版本的类型。 包将只包含在指定的版本类型的图像。</p></li>
<li><p><strong>路径</strong>– 必需。 包路径。</p></li>
<li><p><strong>名称</strong>– 必需。 包文件的名称。</p></li>
<li><p><strong>分辨率</strong>– 可选。 一个字符串，包含软件包支持的显示器分辨率。 可以指定此属性，使用下面的值︰</p>
<ul>
<li><p>&quot;*&quot;: &quot; * &quot;字符表示包支持每次解析。</p></li>
<li><p>&quot;（720 x 1280; 768 x 1280）&quot;︰ 此语法表示的一套程序包支持的分辨率。 程序包包含仅在生成一个在此列表中的分辨率的图像。</p></li>
<li><p>&quot;!（720 x 1280; 768 x 1280）&quot;: A '！' 前面分辨率列表指定程序包支持所有除与列表中的分辨率。 包包含只在不构建一个在此列表中的分辨率的图像。</p></li>
</ul></li>
<li><p><strong>语言</strong>– 可选。 一个字符串，包含软件包支持的显示语言代码。 可以指定此属性，使用下面的值︰</p>
<ul>
<li><p>&quot;*&quot;: &quot; * &quot;字符表示包支持每种语言。</p></li>
<li><p>&quot;（EN-US; ZH-CN）&quot;︰ 此语法所示软件包支持的语言集。 程序包包含仅在包含此列表中的显示语言之一的图像。</p></li>
<li><p>&quot;!（EN-US; ZH-CN）&quot;: A ' ！ 在语言列表指定程序包支持除与列表中的所有语言。 包包含仅在图像不包含在此列表中的显示语言之一。</p></li>
</ul></li>
<li><p><strong>分区</strong>– 可选。 一个字符串，指定程序包的目标分区。 默认情况下，除非显式指定了另一个包到 MainOS 分区中安装。</p></li>
</ul>
<p>这些元素是 Microsoft 仅供内部使用。</p>
<ul>
<li><p><strong>ID</strong> – 可选。 字符串值。 该 ID 是包名。 Oem 不应使用此特性。</p></li>
<li><p><strong>NoBasePackage</strong> – 可选。 布尔值。 设置为 true 的语言和/或不包含基本产品包的解决方案包。 Oem 不应使用此特性。</p></li>
<li><p><strong>FeatureIdentifierPackage</strong> – 可选。 布尔值。 Oem 不应使用此特性。</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

### <a name="prereleasepackages"></a>PrereleasePackages

描述可以在 OEMInput 文件中使用**ExcludePrereleaseFeatures**元素排除的包。 有关详细信息，请参阅[OEMInput 文件的内容](oeminput-file-contents.md)。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>元素</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>PackageFile</strong></p></td>
<td><p>可选项。 此元素描述 prelease 软件包。</p>
<p>此元素支持下列特性︰</p>
<ul>
<li><p><strong>类型</strong>– 必需。 可以是<strong>受保护</strong>或<strong>替换</strong>。</p>
<p><strong>保护</strong>包被排除时<code>ExcludePrereleaseFeatures</code>被设置为<strong>是</strong>和替换包将改为包含。 例如 OEM 实现方案等测试，同时不具有敏感功能分发生成的移动运营商可以创建替换功能。 这种方法是一种很多，并不是必需的但一个选项来考虑，来帮助管理功能泄露。 有关详细信息，请参阅<a href="oeminput-file-contents.md">OEMInput 文件的内容</a>。</p>
<div class="alert">
<strong>重要</strong>  
<p>未更换包应包括在零售映像。</p>
</div>
<div>
 
</div></li>
<li><p><strong>路径</strong>– 必需。 包路径。</p></li>
<li><p><strong>名称</strong>– 必需。 包文件的名称。</p></li>
<li><p><strong>分辨率</strong>– 可选。 一个字符串，包含软件包支持的显示器分辨率。 可以指定此属性，使用下面的值︰</p>
<ul>
<li><p>&quot;*&quot;: &quot; * &quot;字符表示包支持每次解析。</p></li>
<li><p>&quot;（720 x 1280; 768 x 1280）&quot;︰ 此语法表示的一套程序包支持的分辨率。 程序包包含仅在生成一个在此列表中的分辨率的图像。</p></li>
<li><p>&quot;!（720 x 1280; 768 x 1280）&quot;: A '！' 前面分辨率列表指定程序包支持所有除与列表中的分辨率。 包包含只在不构建一个在此列表中的分辨率的图像。</p></li>
</ul></li>
<li><p><strong>语言</strong>– 可选。 一个字符串，包含软件包支持的显示语言代码。 可以指定此属性，使用下面的值︰</p>
<ul>
<li><p>&quot;*&quot;: &quot; * &quot;字符表示包支持每种语言。</p></li>
<li><p>&quot;（EN-US; ZH-CN）&quot;︰ 此语法所示软件包支持的语言集。 程序包包含仅在包含此列表中的显示语言之一的图像。</p></li>
<li><p>&quot;!（EN-US; ZH-CN）&quot;: A ' ！ 在语言列表指定程序包支持除与列表中的所有语言。 包包含仅在图像不包含在此列表中的显示语言之一。</p></li>
</ul></li>
<li><p><strong>分区</strong>– 可选。 一个字符串，指定程序包的目标分区。 默认情况下，除非显式指定了另一个包到 MainOS 分区中安装。</p></li>
</ul>
<p>这些元素是 Microsoft 仅供内部使用。</p>
<ul>
<li><p><strong>ID</strong> – 可选。 字符串值。 该 ID 是包名。 Oem 不应使用此特性。</p></li>
<li><p><strong>NoBasePackage</strong> – 可选。 布尔值。 设置为 true 的语言和/或不包含基本产品包的解决方案包。 Oem 不应使用此特性。</p></li>
<li><p><strong>FeatureIdentifierPackage</strong> – 可选。 布尔值。 Oem 不应使用此特性。</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

### <a name="socpackages"></a>SOCPackages

**SOCPackages**元素指定为特定的 SoC，所指定的 OEMInput 文件中的**SOC**元素生成的图像中包含的包。 **SOCPackages**元素具有不支持的属性。

下表描述的**SOCPackages**元素的子元素。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>元素</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>PackageFile</strong></p></td>
<td><p>可选项。 此元素描述一个包。</p>
<p>此元素支持下列特性︰</p>
<ul>
<li><p><strong>SOC</strong> – 必需。 SoC 软件包支持的类型。 有关受支持的值的列表，请参阅[OEMInput 文件的内容](oeminput-file-contents.md)中的<strong>SOC</strong>元素的说明。 包将只包括在图像生成指定 SoC.</p></li>
<li><p><strong>路径</strong>– 必需。 包路径。</p></li>
<li><p><strong>名称</strong>– 必需。 包文件的名称。</p></li>
<li><p><strong>分辨率</strong>– 可选。 一个字符串，包含软件包支持的显示器分辨率。 可以指定此属性，使用下面的值︰</p>
<ul>
<li><p>&quot;*&quot;: &quot; * &quot;字符表示包支持每次解析。</p></li>
<li><p>&quot;（720 x 1280; 768 x 1280）&quot;︰ 此语法表示的一套程序包支持的分辨率。 程序包包含仅在生成一个在此列表中的分辨率的图像。</p></li>
<li><p>&quot;!（720 x 1280; 768 x 1280）&quot;: A '！' 前面分辨率列表指定程序包支持所有除与列表中的分辨率。 包包含只在不构建一个在此列表中的分辨率的图像。</p></li>
</ul></li>
<li><p><strong>语言</strong>– 可选。 一个字符串，包含软件包支持的显示语言代码。 可以指定此属性，使用下面的值︰</p>
<ul>
<li><p>&quot;*&quot;: &quot; * &quot;字符表示包支持每种语言。</p></li>
<li><p>&quot;（EN-US; ZH-CN）&quot;︰ 此语法所示软件包支持的语言集。 程序包包含仅在包含此列表中的显示语言之一的图像。</p></li>
<li><p>&quot;!（EN-US; ZH-CN）&quot;: A ' ！ 在语言列表指定程序包支持除与列表中的所有语言。 包包含仅在图像不包含在此列表中的显示语言之一。</p></li>
</ul></li>
<li><p><strong>分区</strong>– 可选。 一个字符串，指定程序包的目标分区。 默认情况下，除非显式指定了另一个包到 MainOS 分区中安装。</p></li>
</ul>
<p>这些元素是 Microsoft 仅供内部使用。</p>
<ul>
<li><p><strong>CPUType</strong>– 必需。 字符串值。 设置 CPU 类型。 可以设置为<em>x86</em>或<em>臂</em>。 Oem 不应使用此特性。 Oem 不应使用此特性。</p></li>
<li><p><strong>ID</strong> – 可选。 字符串值。 该 ID 是包名。 Oem 不应使用此特性。</p></li>
<li><p><strong>NoBasePackage</strong> – 可选。 布尔值。 设置为 true 的语言和/或不包含基本产品包的解决方案包。 Oem 不应使用此特性。</p></li>
<li><p><strong>FeatureIdentifierPackage</strong> – 可选。 布尔值。 Oem 不应使用此特性。</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

### <a name="svpackages"></a>SVPackages

**SVPackages**元素指定为特定的 SoC 生产厂家，所指定的 OEMInput 文件中的**SV**元素生成的图像中包含的包。 **SVPackages**元素具有不支持的属性。

下表描述的**SVPackages**元素的子元素。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>元素</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>PackageFile</strong></p></td>
<td><p>可选项。 此元素描述一个包。</p>
<p>此元素支持下列特性︰</p>
<ul>
<li><p><strong>SV</strong> – 必需。 支持的包 SoC 的供应商。 只为指定的 SoC 供应商生成的图像中包含包。</p></li>
<li><p><strong>路径</strong>– 必需。 包路径。</p></li>
<li><p><strong>名称</strong>– 可选。</p></li>
<li><p><strong>分辨率</strong>– 可选。 一个字符串，包含软件包支持的显示器分辨率。 可以指定此属性，使用下面的值︰</p>
<ul>
<li><p>&quot;*&quot;: &quot; * &quot;字符表示包支持每次解析。</p></li>
<li><p>&quot;（720 x 1280; 768 x 1280）&quot;︰ 此语法表示的一套程序包支持的分辨率。 程序包包含仅在生成一个在此列表中的分辨率的图像。</p></li>
<li><p>&quot;!（720 x 1280; 768 x 1280）&quot;: A '！' 前面分辨率列表指定程序包支持所有除与列表中的分辨率。 包包含只在不构建一个在此列表中的分辨率的图像。</p></li>
</ul></li>
<li><p><strong>语言</strong>– 可选。 一个字符串，包含软件包支持的显示语言代码。 可以指定此属性，使用下面的值︰</p>
<ul>
<li><p>&quot;*&quot;: &quot; * &quot;字符表示包支持每种语言。</p></li>
<li><p>&quot;（EN-US; ZH-CN）&quot;︰ 此语法所示软件包支持的语言集。 程序包包含仅在包含此列表中的显示语言之一的图像。</p></li>
<li><p>&quot;!（EN-US; ZH-CN）&quot;: A ' ！ 在语言列表指定程序包支持除与列表中的所有语言。 包包含仅在图像不包含在此列表中的显示语言之一。</p></li>
</ul></li>
<li><p><strong>分区</strong>– 可选。 一个字符串，指定程序包的目标分区。 默认情况下，除非显式指定了另一个包到 MainOS 分区中安装。</p></li>
</ul>
<p>这些元素是 Microsoft 仅供内部使用。</p>
<ul>
<li><p><strong>CPUType</strong>– 必需。 字符串值。 设置 CPU 类型。 可以设置为<em>x86</em>或<em>臂</em>。 Oem 不应使用此特性。 Oem 不应使用此特性。</p></li>
<li><p><strong>ID</strong> – 可选。 字符串值。 该 ID 是包名。 Oem 不应使用此特性。</p></li>
<li><p><strong>NoBasePackage</strong> – 可选。 布尔值。 设置为 true 的语言和/或不包含基本产品包的解决方案包。 Oem 不应使用此特性。</p></li>
<li><p><strong>FeatureIdentifierPackage</strong> – 可选。 布尔值。 Oem 不应使用此特性。</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

### <a name="oemdeviceplatformpackages"></a>OEMDevicePlatformPackages

**OEMDevicePlatformPackages**元素指定要在特定的设备类型的图像中包含的设备平台包。 Oem 必须通过 FM 文件中使用此元素指定设备平台包。 有关设备平台软件包的详细信息，请参阅[设置设备平台信息](set-device-platform-information.md)。 **OEMDevicePlatformPackages**元素具有不支持的属性。

下表描述的**OEMDevicePlatformPackages**元素的子元素。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>元素</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>PackageFile</strong></p></td>
<td><p>可选项。 此元素描述了要在特定设备类型的图像中包含的设备平台包。</p>
<p>此元素支持下列特性︰</p>
<ul>
<li><p><strong>设备</strong>– 必需。 设备类型所支持的设备平台软件包。 包将只包括在图像生成指定的设备类型。</p></li>
<li><p><strong>路径</strong>– 必需。 包路径。</p></li>
<li><p><strong>名称</strong>– 必需。 包文件的名称。</p></li>
</ul>
<p>这些元素是 Microsoft 仅供内部使用。</p>
<ul>
<li><p><strong>CPUType</strong>– 必需。 字符串值。 设置 CPU 类型。 可以设置为<em>x86</em>或<em>臂</em>。 Oem 不应使用此特性。</p></li>
<li><p><strong>ID</strong> – 可选。 字符串值。 该 ID 是包名。 Oem 不应使用此特性。</p></li>
<li><p><strong>NoBasePackage</strong> – 可选。 布尔值。 设置为 true 的语言和/或不包含基本产品包的解决方案包。 Oem 不应使用此特性。</p></li>
<li><p><strong>FeatureIdentifierPackage</strong> – 可选。 布尔值。 Oem 不应使用此特性。</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

### <a name="devicespecificpackages"></a>DeviceSpecificPackages

**DeviceSpecificPackages**元素指定对于特定的设备类型，指定的 OEMInput 文件中的**设备**元素生成的图像中包含的包。 **DeviceSpecificPackages**元素具有不支持的属性。

下表描述的**DeviceSpecificPackages**元素的子元素。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>元素</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>PackageFile</strong></p></td>
<td><p>可选项。 此元素描述了要在特定的设备类型的图像中包含的包。</p>
<p>此元素支持下列特性︰</p>
<ul>
<li><p><strong>设备</strong>– 必需。 设备类型所支持的设备平台软件包。 包将只包括在图像生成指定的设备类型。</p></li>
<li><p><strong>路径</strong>– 必需。 包路径。</p></li>
<li><p><strong>名称</strong>– 必需。 包文件的名称。</p></li>
<li><p><strong>分辨率</strong>– 可选。 一个字符串，包含软件包支持的显示器分辨率。 可以指定此属性，使用下面的值︰</p>
<ul>
<li><p>&quot;*&quot;: &quot; * &quot;字符表示包支持每次解析。</p></li>
<li><p>&quot;（720 x 1280; 768 x 1280）&quot;︰ 此语法表示的一套程序包支持的分辨率。 程序包包含仅在生成一个在此列表中的分辨率的图像。</p></li>
<li><p>&quot;!（720 x 1280; 768 x 1280）&quot;: A '！' 前面分辨率列表指定程序包支持所有除与列表中的分辨率。 包包含只在不构建一个在此列表中的分辨率的图像。</p></li>
</ul></li>
<li><p><strong>语言</strong>– 可选。 一个字符串，包含软件包支持的显示语言代码。 可以指定此属性，使用下面的值︰</p>
<ul>
<li><p>&quot;*&quot;: &quot; * &quot;字符表示包支持每种语言。</p></li>
<li><p>&quot;（EN-US; ZH-CN）&quot;︰ 此语法所示软件包支持的语言集。 程序包包含仅在包含此列表中的显示语言之一的图像。</p></li>
<li><p>&quot;!（EN-US; ZH-CN）&quot;: A ' ！ 在语言列表指定程序包支持除与列表中的所有语言。 包包含仅在图像不包含在此列表中的显示语言之一。</p></li>
</ul></li>
<li><p><strong>分区</strong>– 可选。 一个字符串，指定程序包的目标分区。 默认情况下，除非显式指定了另一个包到 MainOS 分区中安装。</p></li>
</ul>
<p>这些元素是 Microsoft 仅供内部使用。</p>
<ul>
<li><p><strong>CPUType</strong>– 必需。 字符串值。 设置 CPU 类型。 可以设置为<em>x86</em>或<em>臂</em>。 Oem 不应使用此特性。</p></li>
<li><p><strong>ID</strong> – 可选。 字符串值。 该 ID 是由 Oem 不应使用此特性的包名称。</p></li>
<li><p><strong>NoBasePackage</strong> – 可选。 布尔值。 设置为 true 的语言和/或不包含基本产品包的解决方案包。 Oem 不应使用此特性。</p></li>
<li><p><strong>FeatureIdentifierPackage</strong> – 可选。 布尔值。 Oem 不应使用此特性。</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

## <a name="microsoft-internal-use-only"></a>仅在 Microsoft 内部使用


以下组件是保留 Microsoft 仅供内部使用，但在此记录的完整性。

### <a name="cpupackages"></a>CPUPackages

留作内部 Microsoft 使用。 Oem 不应使用此元素。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>元素</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>PackageFile</strong></p></td>
<td><p>可选项。 此元素描述一个包。</p>
<p>此元素支持下列特性︰</p>
<ul>
<li><p><strong>CPUType</strong> – 必需。 字符串值。 设置 CPU 类型。 可以设置为<em>x86</em>或<em>臂</em>。 Oem 不应使用此特性。</p></li>
<li><p><strong>路径</strong>– 必需。 包路径。</p></li>
<li><p><strong>名称</strong>– 必需。 包文件的名称。</p></li>
<li><p><strong>ID</strong>– 可选。 字符串值。 该 ID 是包名。 Oem 不应使用此特性。</p></li>
<li><p><strong>NoBasePackage</strong> – 可选。 布尔值。 设置为 true 的语言和/或不包含基本产品包的解决方案包。 Oem 不应使用此特性。</p></li>
<li><p><strong>FeatureIdentifierPackage</strong> – 可选。 布尔值。 Oem 不应使用此特性。</p></li>
<li><p><strong>分辨率</strong>– 可选。 一个字符串，包含软件包支持的显示器分辨率。 可以指定此属性，使用下面的值︰</p>
<ul>
<li><p>&quot;*&quot;: &quot; * &quot;字符表示包支持每次解析。</p></li>
<li><p>&quot;（720 x 1280; 768 x 1280）&quot;︰ 此语法表示的一套程序包支持的分辨率。 程序包包含仅在生成一个在此列表中的分辨率的图像。</p></li>
<li><p>&quot;!（720 x 1280; 768 x 1280）&quot;: A '！' 前面分辨率列表指定程序包支持所有除与列表中的分辨率。 包包含只在不构建一个在此列表中的分辨率的图像。</p></li>
</ul></li>
<li><p><strong>语言</strong>– 可选。 一个字符串，包含软件包支持的显示语言代码。 可以指定此属性，使用下面的值︰</p>
<ul>
<li><p>&quot;*&quot;: &quot; * &quot;字符表示包支持每种语言。</p></li>
<li><p>&quot;（EN-US; ZH-CN）&quot;︰ 此语法所示软件包支持的语言集。 程序包包含仅在包含此列表中的显示语言之一的图像。</p></li>
<li><p>&quot;!（EN-US; ZH-CN）&quot;: A ' ！ 在语言列表指定该程序包支持除与列表中的所有语言。 包包含仅在图像不包含在此列表中的显示语言之一。</p></li>
</ul></li>
<li><p><strong>分区</strong>– 可选。 一个字符串，指定程序包的目标分区。</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

### <a name="bootuilanguagepackagefile"></a>BootUILanguagePackageFile

留作内部 Microsoft 使用。 Oem 不应使用此元素。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>元素</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>BootUILanguagePackageFile</strong></p></td>
<td><p>可选项。 此元素支持下列特性︰</p>
<ul>
<li><p><strong>路径</strong>– 必需。 包路径。</p></li>
<li><p><strong>名称</strong>– 必需。 包文件的名称。</p></li>
<li><p><strong>ID</strong> – 可选。 字符串值。 该 ID 是包名。 Oem 不应使用此特性。</p></li>
<li><p><strong>NoBasePackage</strong> – 可选。 布尔值。 设置为 true 的语言和/或不包含基本产品包的解决方案包。 Oem 不应使用此特性。</p></li>
<li><p><strong>FeatureIdentifierPackage</strong> – 可选。 布尔值。 Oem 不应使用此特性。</p></li>
<li><p><strong>分区</strong>– 可选。 一个字符串，指定程序包的目标分区。</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

### <a name="bootlocalepackagefile"></a>BootLocalePackageFile

留作内部 Microsoft 使用。 Oem 不应使用此元素。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>元素</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>BootLocalePackageFile</strong></p></td>
<td><p>可选项。 此元素支持下列特性︰</p>
<ul>
<li><p><strong>路径</strong>– 必需。 包路径。</p></li>
<li><p><strong>名称</strong>– 必需。 包文件的名称。</p></li>
<li><p><strong>ID</strong> – 可选。 字符串值。 该 ID 是包名。 Oem 不应使用此特性。</p></li>
<li><p><strong>NoBasePackage</strong> – 可选。 布尔值。 设置为 true 的语言和/或不包含基本产品包的解决方案包。 Oem 不应使用此特性。</p></li>
<li><p><strong>FeatureIdentifierPackage</strong> – 可选。 布尔值。 Oem 不应使用此特性。</p></li>
<li><p><strong>分区</strong>– 可选。 一个字符串，指定程序包的目标分区。</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

### <a name="devicelayoutpackages"></a>DeviceLayoutPackages

留作内部 Microsoft 使用。 Oem 不应使用此元素。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>元素</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>PackageFile</strong></p></td>
<td><p>可选项。 此元素描述一个包。</p>
<p>此元素支持下列特性︰</p>
<ul>
<li><p><strong>SOC</strong> – 必需。</p></li>
<li><p><strong>路径</strong>– 必需。 包路径。</p></li>
<li><p><strong>名称</strong>– 必需。 包文件的名称。</p></li>
<li><p><strong>分区</strong>– 可选。 一个字符串，指定程序包的目标分区。 默认情况下，除非显式指定了另一个包到 MainOS 分区中安装。</p></li>
<li><p><strong>ID</strong>– 可选。 字符串值。 该 ID 是包名。 Oem 不应使用此特性。</p></li>
<li><p><strong>NoBasePackage</strong> – 可选。 布尔值。 设置为 true 的语言和/或不包含基本产品包的解决方案包。 Oem 不应使用此特性。</p></li>
<li><p><strong>FeatureIdentifierPackage</strong> – 可选。 布尔值。 Oem 不应使用此特性。</p></li>
<li><p><strong>CPUType</strong>– 必需。 字符串值。 设置 CPU 类型。 可以设置为<em>x86</em>或<em>臂</em>。 Oem 不应使用此特性。 Oem 不应使用此特性。</p></li>
<li><p><strong>分区</strong>– 可选。 一个字符串，指定程序包的目标分区。</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

### <a name="keyboardpackages"></a>KeyboardPackages

留作内部 Microsoft 使用。 Oem 不应使用此元素。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>元素</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>PackageFile</strong></p></td>
<td><p>可选项。 此元素描述一个包。</p>
<p>此元素支持下列特性︰</p>
<ul>
<li><p><strong>路径</strong>– 必需。 包路径。</p></li>
<li><p><strong>名称</strong>– 必需。 包文件的名称。</p></li>
<li><p><strong>ID</strong>– 可选。 字符串值。 该 ID 是包名。 Oem 不应使用此特性。</p></li>
<li><p><strong>NoBasePackage</strong> – 可选。 布尔值。 设置为 true 的语言和/或不包含基本产品包的解决方案包。 Oem 不应使用此特性。</p></li>
<li><p><strong>FeatureIdentifierPackage</strong> – 可选。 布尔值。 Oem 不应使用此特性。</p></li>
<li><p><strong>语言</strong>– 可选。 一个字符串，包含软件包支持的显示语言代码。 可以指定此属性，使用下面的值︰</p>
<ul>
<li><p>&quot;*&quot;: &quot; * &quot;字符表示包支持每种语言。</p></li>
<li><p>&quot;（EN-US; ZH-CN）&quot;︰ 此语法所示软件包支持的语言集。 程序包包含仅在包含此列表中的显示语言之一的图像。</p></li>
<li><p>&quot;!（EN-US; ZH-CN）&quot;: A ' ！ 在语言列表指定程序包支持除与列表中的所有语言。 包包含仅在图像不包含在此列表中的显示语言之一。</p></li>
</ul></li>
<li><p><strong>分区</strong>– 可选。 一个字符串，指定程序包的目标分区。 默认情况下，除非显式指定了另一个包到 MainOS 分区中安装。</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

### <a name="speechpackages"></a>SpeechPackages

留作内部 Microsoft 使用。 Oem 不应使用此元素。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>元素</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>PackageFile</strong></p></td>
<td><p>可选项。 此元素描述一个包。</p>
<p>此元素支持下列特性︰</p>
<ul>
<li><p><strong>路径</strong>– 必需。 包路径。</p></li>
<li><p><strong>名称</strong>– 必需。 包文件的名称。</p></li>
<li><p><strong>ID</strong>– 可选。 字符串值。 该 ID 是包名。 Oem 不应使用此特性。</p></li>
<li><p><strong>NoBasePackage</strong> – 可选。 布尔值。 设置为 true 的语言和/或不包含基本产品包的解决方案包。 Oem 不应使用此特性。</p></li>
<li><p><strong>FeatureIdentifierPackage</strong> – 可选。 布尔值。 Oem 不应使用此特性。</p></li>
<li><p><strong>语言</strong>– 可选。 一个字符串，包含软件包支持的显示语言代码。 可以指定此属性，使用下面的值︰</p>
<ul>
<li><p>&quot;*&quot;: &quot; * &quot;字符表示包支持每种语言。</p></li>
<li><p>&quot;（EN-US; ZH-CN）&quot;︰ 此语法所示软件包支持的语言集。 程序包包含仅在包含此列表中的显示语言之一的图像。</p></li>
<li><p>&quot;!（EN-US; ZH-CN）&quot;: A ' ！ 在语言列表指定程序包支持除与列表中的所有语言。 包包含仅在图像不包含在此列表中的显示语言之一。</p></li>
</ul></li>
<li><p><strong>分区</strong>– 可选。 一个字符串，指定程序包的目标分区。 默认情况下，除非显式指定了另一个包到 MainOS 分区中安装。</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[构建使用 ImgGen.cmd 电话映像](building-a-phone-image-using-imggencmd.md)

 

 

[发送有关此主题的意见的评论](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_phFlashing\p_phFlashing%5D:%20Feature%20manifest%20file%20contents%20%20RELEASE:%20%2810/4/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "发送有关此主题的意见的评论")





