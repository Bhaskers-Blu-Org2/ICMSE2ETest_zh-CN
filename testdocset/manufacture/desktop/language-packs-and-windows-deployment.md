---
author: Justinha
Description: "语言包"
ms.assetid: 051a9952-c160-4f51-8575-bde6e4868b03
MSHAttr: PreferredLib:/library/windows/hardware
title: "语言包"
ms.openlocfilehash: e52f6ea346fd5c160282b9bafa3ea2b38bffd498
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="language-packs"></a>语言包 


若要设计更适合在不同地区的客户的电脑，您可以将 Windows 设置包含正确的本地语言、 设置和键盘或其他输入的设备。

## <a name="span-idwhatsnewwithlanguagepacksforwindows10spanspan-idwhatsnewwithlanguagepacksforwindows10spanspan-idwhatsnewwithlanguagepacksforwindows10spanwhats-new-with-language-packs-for-windows-10"></a><span id="What_s_new_with_Language_Packs_for_Windows_10_"></span><span id="what_s_new_with_language_packs_for_windows_10_"></span><span id="WHAT_S_NEW_WITH_LANGUAGE_PACKS_FOR_WINDOWS_10_"></span>语言包的 Windows 10 的新功能是什么？


为了帮助您缩小您的图像的大小，语言包有现在被分成以下语言组件和[第 2 版的功能上的需求 （功能）](features-on-demand-v2--capabilities.md):

-   用户界面文本 （语言包.cab 文件）
-   基本 (拼写检查，键入)
-   字体
-   手写输入
-   光学字符识别
-   文本到语音转换
-   语音
-   零售演示体验

您现在可以选择将只有核心语言包 UI 资源添加到您的映像，大大降低了图像的大小。

预先加载 Cortana 功能，根据需要添加以下功能︰ 用户界面文本基本、 语音功能和语音语言组件。 

不是所有组件和即需即装功能都可为每种语言。

若要了解详细信息，请参阅[将语言包添加到 Windows](add-language-packs-to-windows.md)。

## <a name="span-idlanguagepacksforwindowsspanspan-idlanguagepacksforwindowsspanspan-idlanguagepacksforwindowsspanlanguage-packs-for-windows"></a><span id="Language_packs_for_Windows"></span><span id="language_packs_for_windows"></span><span id="LANGUAGE_PACKS_FOR_WINDOWS"></span>Windows 的语言包


语言包包含的文本的对话框、 菜单项和窗口中见到的 helpfiles。

对于某些地区，语言界面包 (Lip) 可以提供更多广泛使用的对话框、 菜单项和帮助文件的内容翻译。 嘴唇依赖于父语言包提供内容的其余部分。

### <a name="span-idgetlanguagepacksandlipsspanspan-idgetlanguagepacksandlipsspanspan-idgetlanguagepacksandlipsspanget-language-packs-and-lips"></a><span id="Get_language_packs_and_LIPs"></span><span id="get_language_packs_and_lips"></span><span id="GET_LANGUAGE_PACKS_AND_LIPS"></span>获取语言包和 Lip

-   Oem 和系统构建者与 Microsoft 软件许可条款如果可以则可从[Microsoft OEM 网站](http://go.microsoft.com/fwlink/?LinkId=131359)或[OEM 合作伙伴中心](http://go.microsoft.com/fwlink/?LinkId=131358)下载语言包和 Lip。
-   IT 专业人员可以从[Microsoft 卷授权网站](http://go.microsoft.com/fwlink/?LinkId=125893)下载语言包。
-   在安装 Windows 之后，最终用户可以下载并安装其他语言包，在**设置** > **时间和语言** > **地区和语言** > **添加一种语言**。 

相关的信息︰

-   [可用语言包的 Windows](available-language-packs-for-windows.md)。 为多个版本的 Windows 中和其标识符代码中列出的所有支持的语言包和 Lip。

### <a name="span-idaddlanguagestowindowsspanspan-idaddlanguagestowindowsspanspan-idaddlanguagestowindowsspanadd-languages-to-windows"></a><span id="Add_languages_to_Windows"></span><span id="add_languages_to_windows"></span><span id="ADD_LANGUAGES_TO_WINDOWS"></span>将语言添加到 Windows

当包含多个语言或唇到 Windows 时，您的客户将能够选择在 Windows OOBE 期间最能满足其需要的语言。

还有几个不同的方法安装语言包︰

-   您可以通过使用**Dism /Add-Package**工具到 Windows 添加语言包。 请参阅[添加和删除在运行 Windows 安装语言包](add-and-remove-language-packs-on-a-running-windows-installation.md)或[添加和删除语言包使用 DISM 脱机](add-and-remove-language-packs-offline-using-dism.md)。
-   若要部署多语言版本的 Windows 使用 Windows 安装程序 （例如，企业形象窗口 DVD 或一套在公司网络上可用的图像），可以添加到安装程序语言资源。 请参阅[添加到 Windows 分发的多语言支持](add-multilingual-support-to-a-windows-distribution.md)。

    对于企业或基于网络的部署，可能还需要更新 Windows 预安装环境 (Windows PE) 用户可以看到他们在选择如何以及在何处可以将 Windows 安装到他们的 PC。 有关详细信息，请参阅[WinPE︰ 安装和自定义](winpe-mount-and-customize.md)。

-   在安装 Windows 之后，最终用户可以下载并从**语言**控制面板中安装其他语言包和 Lip。 有关详细信息，请参阅[本地语言编写程序](http://go.microsoft.com/fwlink/?LinkId=262343)。

## <a name="span-idlanguagepacksforrecoverytoolsspanspan-idlanguagepacksforrecoverytoolsspanspan-idlanguagepacksforrecoverytoolsspanlanguage-packs-for-recovery-tools"></a><span id="Language_packs_for_recovery_tools"></span><span id="language_packs_for_recovery_tools"></span><span id="LANGUAGE_PACKS_FOR_RECOVERY_TOOLS"></span>恢复工具的语言包


遇到问题时，Windows 恢复环境 (Windows RE) 可以帮助恢复系统和数据。 对于 Windows 更新可用的语言时，更新恢复工具中可用的语言︰[自定义 Windows RE](customize-windows-re.md)。

## <a name="span-idpreparekeyboardstimezonesandotherregionalsettingsspanspan-idpreparekeyboardstimezonesandotherregionalsettingsspanspan-idpreparekeyboardstimezonesandotherregionalsettingsspanprepare-keyboards-time-zones-and-other-regional-settings"></a><span id="Prepare_keyboards__time_zones__and_other_regional_settings_"></span><span id="prepare_keyboards__time_zones__and_other_regional_settings_"></span><span id="PREPARE_KEYBOARDS__TIME_ZONES__AND_OTHER_REGIONAL_SETTINGS_"></span>准备键盘、 次区域和其他区域设置


在配置过程中或安装 Windows 后，您可以指定默认的键盘布局、 语言或区域设置。

-   [在 Windows 中配置国际设置](configure-international-settings-in-windows.md)
-   [在 Windows 的默认输入文件 （输入法区域设置）](default-input-locales-for-windows-language-packs.md)︰ 列出的默认输入配置文件 （语言和键盘对） 用于每个地区。
-   [默认时区](default-time-zones.md)︰ 列出了用于每个区域的默认时区。
-   [对于 Windows 键盘标识符](windows-language-pack-default-values.md)︰ 列出配置输入的配置文件时使用的键盘十六进制值。

## <a name="span-idlanguagesforappsspanspan-idlanguagesforappsspanspan-idlanguagesforappsspanlanguages-for-apps"></a><span id="Languages_for_apps"></span><span id="languages_for_apps"></span><span id="LANGUAGES_FOR_APPS"></span>应用程序的语言


许多应用程序包括支持多语言，但有些需要单独安装语言包才能正常工作。 向应用程序开发人员咨询。

一般情况下，在安装应用程序前安装所有您拖到 Windows 的语言。 这有助于确保语言资源文件可用于每个可用的应用程序。

有关详细信息，请参阅[多语言用户界面 (Windows)](http://go.microsoft.com/fwlink/p/?LinkId=698642)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[将语言包添加到 Windows](add-language-packs-to-windows.md)

[功能需求 V2 （功能）](features-on-demand-v2--capabilities.md)

 

 






