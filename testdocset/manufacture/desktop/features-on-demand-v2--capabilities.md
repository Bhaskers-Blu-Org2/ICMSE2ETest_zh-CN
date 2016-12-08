---
author: Justinha
Description: "功能需求 v2 （功能），Windows 10 中引入的都可以在任何时候添加的 Windows 功能包。 常见功能包括例如手写识别或.NET Framework 语言资源 (。NetFx3)。"
ms.assetid: 6390f427-a201-487e-928f-964e7b84327c
MSHAttr: PreferredLib:/library/windows/hardware
title: "功能需求 V2 （功能）"
ms.openlocfilehash: cef6ea515039e9f87c53cc2df4219f99b07daebe
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="features-on-demand-v2-capabilities"></a>功能需求 V2 （功能）


功能需求 v2 （功能），Windows 10 中引入的都可以在任何时候添加的 Windows 功能包。 常见功能包括例如手写识别或.NET Framework 语言资源 (。NetFx3)。

当电脑需要一项新功能时，它可以从 Windows Update 请求功能包。

与以前的功能包，不同功能需求 V2 也可能适用于多个 Windows 版本，并可以使用 DISM 不知道内部版本号添加。 始终使用需求相匹配的操作系统体系结构上的功能。 添加错误的体系结构的即需即装功能可能不会返回一个错误，但可能会引起在操作系统中的功能问题。 

## <a name="span-idaddingorremovingfeaturescapabilitiesspanspan-idaddingorremovingfeaturescapabilitiesspanspan-idaddingorremovingfeaturescapabilitiesspanadding-or-removing-featurescapabilities"></a><span id="Adding_or_removing_features_capabilities"></span><span id="adding_or_removing_features_capabilities"></span><span id="ADDING_OR_REMOVING_FEATURES_CAPABILITIES"></span>添加或删除功能中的功能


使用 DISM 中添加或删除功能︰

-   使用 /Online 选项将功能添加到您的 PC。

-   使用 /Image:&lt;装载路径&gt;选项可添加到 Windows 映像文件 (.wim) 的功能。
 

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">命令</th>
<th align="left">说明</th>
<th align="left">示例</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">/ 添加功能</td>
<td align="left"><p>将功能添加到图像中。</p>
<p>程序包依赖项还可以提取相关程序包。 例如，如果添加语音包，您将获得的文本到语音转换和除语音之外的基本包。</p></td>
<td align="left">DISM.exe /Online /Add-Capability /CapabilityName:Language.Basic~\~\~EN-US ~ 0.0.1.0</td>
</tr>
<tr class="even">
<td align="left">/ 获取能力</td>
<td align="left">在图像中获得能力。</td>
<td align="left">DISM / 在线 /Get-Capabilities</td>
</tr>
<tr class="odd">
<td align="left">/ Get CapabilityInfo</td>
<td align="left">在图像中获取信息的能力。</td>
<td align="left">DISM /Online /Get-CapabilityInfo /CapabilityName:Language.Basic~\~\~EN-US ~ 0.0.1.0</td>
</tr>
<tr class="even">
<td align="left">/ 删除功能</td>
<td align="left"><p>删除图像中的一种能力。</p>
<p>注意︰ 您不能删除依赖于其他软件包的功能。 例如，如果有法语的手写和安装的基本功能，不能删除的基本功能。 此操作将失败。</p></td>
<td align="left">DISM.exe / 在线 /Remove-Capability /CapabilityName:Language.Basic~~~en-US~0.0.1.0</td>
</tr>
</tbody>
</table>

 

## <a name="span-idcapabilitiesreferencespanspan-idcapabilitiesreferencespanspan-idcapabilitiesreferencespancapabilities-reference"></a><span id="Capabilities_reference"></span><span id="capabilities_reference"></span><span id="CAPABILITIES_REFERENCE"></span>功能参考


### <a name="net-framework"></a>.NET Framework  

| 组件 | 说明                                                             |
|-----------|-------------------------------------------------------------------------|
| NetFx3    | .NET 框架中，许多应用程序所需的软件框架 3.x。 |

 

### <a name="language-capabilities"></a>语言能力

不是所有的功能都是为每种语言。

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">组件</th>
<th align="left">示例文件名称</th>
<th align="left">Dependencies</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">基本</td>
<td align="left"><code>Microsoft-Windows-LanguageFeatures-Basic-fr-fr-Package</code></td>
<td align="left">无</td>
<td align="left"><p>拼写检查，文本预测、 断字，断字和可用的语言。</p>
<p>添加任何以下组件之前，您必须添加此组件。</p></td>
</tr>
<tr class="even">
<td align="left">字体</td>
<td align="left"><code>Microsoft-Windows-LanguageFeatures-Fonts-Thai-Package</code></td>
<td align="left">无</td>
<td align="left"><p>字体。</p>
<p>所需的某些地区呈现出现在文档中的文本。 示例，TH-TH 要求泰国字体包。 </p></td>
</tr>
<tr class="odd">
<td align="left">光学字符识别</td>
<td align="left"><code>Microsoft-Windows-LanguageFeatures-OCR-fr-fr-Package</code></td>
<td align="left">基本</td>
<td align="left">识别并输出图像中的文本。</td>
</tr>
<tr class="even">
<td align="left">手写识别</td>
<td align="left"><code>Microsoft-Windows-LanguageFeatures-Handwriting-fr-fr-Package</code></td>
<td align="left">基本</td>
<td align="left">使设备用笔输入的手写识别。</td>
</tr>
<tr class="odd">
<td align="left">文本到语音转换</td>
<td align="left"><code>Microsoft-Windows-LanguageFeatures-TextToSpeech-fr-fr-Package</code></td>
<td align="left">基本</td>
<td align="left">使文本到语音转换，由 Cortana 和讲述人。</td>
</tr>
<tr class="even">
<td align="left">语音识别</td>
<td align="left"><code>Microsoft-Windows-LanguageFeatures-Speech-fr-fr-Package</code></td>
<td align="left">基本的文本到语音转换</td>
<td align="left">识别语音输入，由 Cortana 和 Windows 语音识别。</td>
</tr>
</tbody>
</table>

### <a name="font-capabilities"></a>字体的功能

当添加某些地区的语言，您需要添加字体功能。

| 地区      | 说明                            | 所需的字体功能                              |
|-------------|----------------------------------------|-------------------------------------------------------|
| 上午 ET       | 阿姆哈拉语                                | Microsoft-Windows-LanguageFeatures-Fonts-Ethi-Package |
| ar SA       | 阿拉伯语 （沙特阿拉伯）                  | Microsoft-Windows-LanguageFeatures-Fonts-Arab-Package |
| ar SY       | 阿拉伯语 （叙利亚）                         | Microsoft-Windows-LanguageFeatures-Fonts-Syrc-Package |
| 作为 IN       | 阿萨姆                               | Microsoft-Windows-LanguageFeatures-Fonts-Beng-Package |
| bn BD       | 孟加拉语 （孟加拉）                    | Microsoft-Windows-LanguageFeatures-Fonts-Beng-Package |
| bn IN       | 孟加拉语 （印度）                         | Microsoft-Windows-LanguageFeatures-Fonts-Beng-Package |
| chr Cher 美国 | 切罗基文 （切罗基文）                    | Microsoft-Windows-LanguageFeatures-Fonts-Cher-Package |
| fa 红外线 （ir)       | 波斯语                                | Microsoft-Windows-LanguageFeatures-Fonts-Arab-Package |
| gu IN       | 古吉拉特语                               | Microsoft-Windows-LanguageFeatures-Fonts-Gujr-Package |
| 他 IL       | 希伯来语                                 | Microsoft-Windows-LanguageFeatures-Fonts-Hebr-Package |
| 你在       | 印度语                                  | Microsoft-Windows-LanguageFeatures-Fonts-Deva-Package |
| ja JP       | 日语                               | Microsoft-Windows-LanguageFeatures-Fonts-Jpan-Package |
| km KH       | 高棉语                                  | Microsoft-Windows-LanguageFeatures-Fonts-Khmr-Package |
| kn IN       | 卡纳达语                                | Microsoft-Windows-LanguageFeatures-Fonts-Knda-Package |
| kok IN      | 贡根语                                | Microsoft-Windows-LanguageFeatures-Fonts-Deva-Package |
| ko-KR       | 朝鲜语                                 | Microsoft-Windows-LanguageFeatures-Fonts-Kore-Package |
| ku-阿拉伯-IQ  | 中央库尔德 （阿拉伯语）               | Microsoft-Windows-LanguageFeatures-Fonts-Arab-Package |
| lo LA       | 老挝语                                    | Microsoft-Windows-LanguageFeatures-Fonts-Laoo-Package |
| ml IN       | 马拉雅拉姆语                              | Microsoft-Windows-LanguageFeatures-Fonts-Mlym-Package |
| 先生在       | 马拉地语                                | Microsoft-Windows-LanguageFeatures-Fonts-Deva-Package |
| 内布拉斯加州-NP       | 尼泊尔语                                 | Microsoft-Windows-LanguageFeatures-Fonts-Deva-Package |
| 或在       | Odia                                   | Microsoft-Windows-LanguageFeatures-Fonts-Orya-Package |
| pa-阿拉伯 PK  | 旁遮普语 （阿拉伯语）                       | Microsoft-Windows-LanguageFeatures-Fonts-Arab-Package |
| pa IN       | 旁遮普语                                | Microsoft-Windows-LanguageFeatures-Fonts-Guru-Package |
| prs AF      | 达里语                                   | Microsoft-Windows-LanguageFeatures-Fonts-Arab-Package |
| sd-阿拉伯 PK  | 信德语 （阿拉伯文）                        | Microsoft-Windows-LanguageFeatures-Fonts-Arab-Package |
| si LK       | 僧伽罗语                                | Microsoft-Windows-LanguageFeatures-Fonts-Sinh-Package |
| syr SY      | 古叙利亚语                                 | Microsoft-Windows-LanguageFeatures-Fonts-Syrc-Package |
| 选项卡中       | 泰米尔语                                  | Microsoft-Windows-LanguageFeatures-Fonts-Taml-Package |
| te IN       | 泰卢固语                                 | Microsoft-Windows-LanguageFeatures-Fonts-Telu-Package |
| th TH       | 泰语                                   | Microsoft-Windows-LanguageFeatures-Fonts-Thai-Package |
| ti-ET       | Tigrinya                               | Microsoft-Windows-LanguageFeatures-Fonts-Ethi-Package |
| ug-CN       | 维吾尔语                                 | Microsoft-Windows-LanguageFeatures-Fonts-Arab-Package |
| 您 PK       | 乌尔都语                                   | Microsoft-Windows-LanguageFeatures-Fonts-Arab-Package |
| zh CN       | 中文 （简体）                   | Microsoft-Windows-LanguageFeatures-Fonts-Hans-Package |
| zh 香港       | 中文 (繁体，中国香港 （特别行政区）) | Microsoft-Windows-LanguageFeatures-Fonts-Hant-Package |
| zh TW       | 中文 (繁体，中国台湾地区)          | Microsoft-Windows-LanguageFeatures-Fonts-Hant-Package |

### <a name="additional-fonts-available"></a>其他的可用字体︰

这些字体是可选的不需要任何地区。

| 名称                                                                          | 说明                                                                                                                                         |
|-------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
| Microsoft-Windows-LanguageFeatures-Fonts-PanEuropeanSupplementalFonts-Package | 泛欧洲语言附加的字体。 包括其他字体︰ 宋体新、 格鲁吉亚 Pro、 细黑 San 新、 Neue Haas Grotesk、 姚新、 宋体 Pro。 |

### <a name="other-region-specific-requirements"></a>其他特定于区域的要求

| 地区 | 说明                   | Capability                                             | 说明                                                                                                            |
|--------|-------------------------------|--------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| zh TW  | 中文 (繁体，中国台湾地区) | Microsoft 的 Windows-InternationalFeatures-台湾-包 | 附加支持台湾的日期的格式要求。 包将提供给客户位于台湾地区。 |

### <a name="list-of-all-language-related-features-on-demand"></a>即需即装所有与语言相关的功能的列表
[下载所有可用语言 FODs 的列表](http://download.microsoft.com/download/8/3/0/830AC3A9-68CF-4F10-9357-F27E0A03148A/Windows 10 1607 FOD to LP Mapping Table.xlsx)

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题

[将语言包添加到 Windows](add-language-packs-to-windows.md)

[DISM 功能程序包服务命令行选项](dism-capabilities-package-servicing-command-line-options.md)

