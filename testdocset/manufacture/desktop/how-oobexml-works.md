---
author: Justinha
Description: "Oobe.xml 原理"
ms.assetid: 6df5c611-96f3-4268-9208-8455aa293954
MSHAttr: PreferredLib:/library/windows/hardware
title: "Oobe.xml 原理"
ms.openlocfilehash: 2c1bf500400e3dc2e0932bd37c60abe7e1a1e0cb
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="how-oobexml-works"></a>Oobe.xml 原理


**Oobe.xml**是内容文件，您可以使用组织的文本和图像以及指定预设值的设置为自定义 Windows 第一次遇到。 可用于多个**Oobe.xml**文件特定于语言和地区许可条款和设置，以便用户查看相应的信息，一旦他们开始他们的 Pc。 通过在**Oobe.xml**文件中指定的信息，Oem 直接用户执行设置他们的 Pc 所需的核心任务。

Windows 检查并加载**Oobe.xml**在下列位置，顺序如下︰

1.  **%WINDIR%\\System32\\Oobe\\信息\\Oobe.xml**

2.  **%WINDIR%\\System32\\Oobe\\信息\\默认\\Oobe.xml**

3.  **%WINDIR%\\System32\\Oobe\\信息\\默认\\**&lt;*语言*&gt;\\**Oobe.xml**

4.  **%WINDIR%\\System32\\Oobe\\信息\\***国家/地区*&gt;**\\Oobe.xml**

5.  **%WINDIR%\\System32\\Oobe\\信息\\***国家/地区*&gt;\\&lt;*语言*&gt;\\**Oobe.xml**

如果您具有跨所有国家/地区以及语言的自定义项，则可以在位置 1 中放 Oobe.xml 文件。

正在传送单一地区、 单一语言系统，如果您自定义的**Oobe.xml**文件应放置在\\信息 (位置 1) 或\\(位置 2) 默认目录。 这些位置是等价的。

如果在发往多个国家/地区和 OOBE 设置需要的自定义项的各个国家/地区，每个都有一种语言，所有**Oobe.xml**文件应放在位置 4 和 5 中。

如果您发往多个国家/地区的多种语言，将遵循以下原则︰

-   将特定于国家/地区的信息放在位置 4。

-   将每个相应的国家/地区的语言特定信息放置在位置 5。

## <a name="span-idsingle-languagedeploymentsspanspan-idsingle-languagedeploymentsspanspan-idsingle-languagedeploymentsspansingle-language-deployments"></a><span id="Single-language_deployments"></span><span id="single-language_deployments"></span><span id="SINGLE-LANGUAGE_DEPLOYMENTS"></span>单语言部署


如果您为一种语言中的一个国家/地区提供个人电脑，应放在一个**Oobe.xml**文件**\\%WINDIR%\\System32\\Oobe\\信息**。 此文件可以包含所有自定义 Windows 首次体验到。

例如，英文版的 Windows 交付给美国可以具有以下目录结构︰

**\\%WINDIR%\\System32\\Oobe\\信息\\Oobe.xml**

如果打算改变中不同位置的自定义为一种语言，在多个国家/地区提供个人电脑，放置在**Oobe.xml**文件**\\%WINDIR%\\System32\\Oobe\\信息。**

此文件可以包含您计划要向用户显示的默认区域设置。 用户选择您未对特定自定义设置的国家/地区的情况下，还应包括一组默认的自定义配置。 **Oobe.xml**文件还应包含&lt; *eulafilename* &gt;与您打算使用的自定义的许可证条款的名称的节点。

为每个国家/地区的唯一包含自定义中的内容将**Oobe.xml**文件**\\%WINDIR%\\System32\\**&lt;*您要部署到的国家/地区*&gt;\\&lt;*正在部署中的语言*&gt;。 用户已选择某个国家/地区后，这些文件用于显示其他自定义设置。

例如，英文版的 Windows 传送到美国和加拿大可以有以下目录结构︰

** \\%WINDIR%\\System32\\Oobe\\信息\\Oobe.xml**（最终用户许可协议文件名称和区域设置）

** \\%WINDIR%System32\\Oobe\\信息\\244\\1033年\\Oobe.xml**（美国自定义内容）

**\\%WINDIR%\\System32\\Oobe\\信息\\39\\1033年\\Oobe.xml （加拿大自定义内容）**

## <a name="span-idmultiple-languageorregiondeploymentsspanspan-idmultiple-languageorregiondeploymentsspanspan-idmultiple-languageorregiondeploymentsspanmultiple-language-or-region-deployments"></a><span id="Multiple-language_or_region_deployments"></span><span id="multiple-language_or_region_deployments"></span><span id="MULTIPLE-LANGUAGE_OR_REGION_DEPLOYMENTS"></span>多语言或区域部署


如果 Pc 提供到一个或多个国家/地区，提供与其他语言包运行 Windows 的个人电脑，放置在**Oobe.xml**文件**\\%WINDIR%\\System32\\Oobe\\信息**。 此文件可以包含您计划要向用户显示的默认区域设置。 用户选择您未对特定自定义设置的国家/地区的情况下，还应包括一组默认的自定义配置。 此外应包含此**Oobe.xml** &lt; *eulafilename* &gt;与您打算使用的自定义的许可证条款的名称的节点。

为每个国家/地区的唯一包含自定义中的内容将**Oobe.xml**文件\\%WINDIR%\\System32\\&lt;*您要部署到的国家/地区*&gt;\\&lt;*正在部署中的语言*&gt;。 用户已选择某个国家/地区后，该文件用于显示其他自定义设置。

例如，英文版的 Windows 交付到美国和加拿大将使用以下目录结构︰

** \\%WINDIR%\\System32\\Oobe\\信息\\Oobe.xml**（徽标、 最终用户许可协议文件的名称和区域设置）

** \\%WINDIR%\\System32\\Oobe\\信息\\244\\1033年\\Oobe.xml**（美国自定义内容）

\\%WINDIR%\\System32\\Oobe\\信息\\39\\1033年\\**Oobe.xml** （加拿大自定义内容）

如果 Pc 提供到一个或多个国家/地区，提供与其他语言包运行 Windows 的个人电脑，放置在**Oobe.xml**文件**\\%WINDIR%\\System32\\Oobe\\信息**。 此**Oobe.xml**文件应包含*&lt;eulafilename&gt;*与您打算使用自定义最终用户许可协议的名称的节点。

将您要包含在每个 Windows 语言**Oobe.xml** ** \\%WINDIR%\\System32\\默认\\**&lt;*语言，如果部署在*&gt;。 这些文件应当包含要显示给定的语言，以及一组默认的自定义设置，以防用户选择您未对特定自定义设置的国家/地区的默认区域设置。

为自定义的包含每个国家/地区中的内容将**Oobe.xml**文件**\\%WINDIR%\\System32\\***您要部署到的国家/地区*&gt;\\&lt;*正在部署中的语言*&gt;。 用户已选择某个国家/地区后，该文件用于显示附加的自定义项。

例如，用英语和法语语言包的 Windows 传送到美国和加拿大的版本将使用以下目录结构︰

-   徽标和最终用户许可协议︰

    ** \\%WINDIR%\\System32\\Oobe\\信息\\Oobe.xml**（徽标和最终用户许可协议文件名称）

-   区域设置和回退未本地化为特定国家/地区的内容︰

    ** \\%WINDIR%\\System32\\Oobe\\信息\\默认\\1033年\\Oobe.xml**（默认区域设置和英文内容如果用户选择美国或加拿大以外的其他国家/地区）

    ** \\%WINDIR%\\System32\\Oobe\\信息\\默认\\1036年\\Oobe.xml**（默认区域设置和法语内容如果用户选择美国或加拿大以外的其他国家/地区）

-   在相应的语言特定国家或特定区域的内容

    ** \\%WINDIR%\\System32\\Oobe\\信息\\244\\1033年\\Oobe.xml**（美国自定义内容为英文）

    ** \\%WINDIR%\\System32\\Oobe\\信息\\244\\1036年\\Oobe.xml**（法语中美国自定义内容）

    ** \\%WINDIR%\\System32\\Oobe\\信息\\39\\1033年\\Oobe.xml**（加拿大自定义内容为英文）

    ** \\%WINDIR%\\System32\\Oobe\\信息\\39\\1036年\\Oobe.xml**（法语加拿大自定义内容）

### <a name="span-idcountryregionfolderformatspanspan-idcountryregionfolderformatspanspan-idcountryregionfolderformatspancountryregion-folder-format"></a><span id="Country_region_folder_format"></span><span id="country_region_folder_format"></span><span id="COUNTRY_REGION_FOLDER_FORMAT"></span>国家/地区文件夹格式

若要标识国家/地区︰

1.  查找在**MSDN**上使用[地理位置表](http://go.microsoft.com/fwlink/?LinkId=131360)的国家/地区 GeoID 标识符。 这些值以十六进制格式显示。

2.  将值从十六进制转换为十进制数字，并使用该值的文件夹名称。 例如，若要创建用于智利 (GeoID 0x2E) 的文件夹，文件夹命名为"46"。

    ``` syntax
    \%WINDIR%\System32\Oobe\Info\46\Oobe.xml
    ```

### <a name="span-idlanguagefolderformatspanspan-idlanguagefolderformatspanspan-idlanguagefolderformatspanlanguage-folder-format"></a><span id="Language_folder_format"></span><span id="language_folder_format"></span><span id="LANGUAGE_FOLDER_FORMAT"></span>语言文件夹格式

若要识别的语言，使用的区域设置 ID (LCID) 值的十进制版本。 例如，若要创建一个西班牙的文件夹，文件夹命名为"3082"。

``` syntax
%WINDIR%\System32\Oobe\Info\Default\3082\Oobe.xml
```

有许多比语言的多个 Lcid。 少数的 Lcid 关联到可以释放与 Windows 的语言。 有关发行的语言使用 Windows，在哪个级别的本地化，以及它们的十进制标识符的详细信息请参阅**TechNet**上的[可用语言包](http://go.microsoft.com/fwlink/?LinkId=206620)。

 

 





