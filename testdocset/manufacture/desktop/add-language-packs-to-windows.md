---
author: Justinha
Description: "将语言包添加到 Windows"
ms.assetid: 0734452f-aa09-4ec9-bbbf-fbc995dd803f
MSHAttr: PreferredLib:/library/windows/hardware
title: "将语言包添加到 Windows"
ms.openlocfilehash: 353957e0e2aaeeff674d3ae7b722d76e3a6a4de0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add-language-packs-to-windows"></a>将语言包添加到 Windows


Oem 可以添加语言包，以本地化为不同地区的客户的电脑和设备。

桌面版本的 Windows 10 （家庭、 Pro、 企业和教育） 语言包必须被拆分成语言组件和[第 2 版的功能上的需求 （功能）](features-on-demand-v2--capabilities.md)。 创建较小的存储设备成本较低的图像时，图像大小减少很有帮助。 它还可以减少创建和部署映像所需的时间。

## <a name="span-idlangpacktypesspanspan-idlangpacktypesspanspan-idlangpacktypesspanlanguage-pack-types"></a><span id="LangPackTypes"></span><span id="langpacktypes"></span><span id="LANGPACKTYPES"></span>语言包类型


您可以安装在同一个 Windows 10 图像上的多个语言。 为每种语言，其中可用︰

-   添加语言包和**基本**组件。
-   预先加载 Cortana 的功能，还添加**文本到语音转换**和**语音识别**。
-   添加**字体**和**光学字符识别**的区域以提高您的用户首次体验 （强烈推荐） 中最常用的语言。 如果尚未安装，Windows 将下载并安装它们在背景中，当用户首次选择该语言。
-   添加**手写识别**用笔输入设备。
-   添加 Windows 恢复环境 (WinRE) 组件，以便最终用户可以更轻松地恢复他们的 Pc。

其他可以预置自定义设置︰

-   货币、 时区或日历格式
-   [键盘标识符和 Windows 的输入的法编辑器](windows-language-pack-default-values.md)

不是所有的功能都是为每种语言。

若要限制的数量和类型的语言包中包含的每个图像的使用治疗。 小窗口 10 语言包时，有太多可以仍会影响磁盘空间，并可能会影响性能，尤其是同时更新和维护窗口。

一些功能具有附加依赖项，如下表所示。

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
<td align="left">语言包</td>
<td align="left"><code>Microsoft-Windows-Client-Language-Pack_x64_es-es.cab</code></td>
<td align="left">无</td>
<td align="left">包括基本的 Cortana 功能的用户界面文本。</td>
</tr>
<tr class="even">
<td align="left">语言界面包</td>
<td align="left"><code>Microsoft-Windows-Client-Language-Interface-Pack_x64_ca-es-valencia.cab</code></td>
<td align="left">要求特定的完全本地化或部分本地化的语言包。 示例︰ ca-es-valencia 要求 es-es。 若要了解详细信息，请参阅[可用语言包的 Windows](available-language-packs-for-windows.md)。</td>
<td align="left"><p>包括基本的 Cortana 功能的用户界面文本。</p>
<p>不是所有的用户界面语言资源纳入唇。 所以 Lip 需要至少一个语言包 （或父语言）。 父语言包提供了 LIP 的支持。 未翻译为 LIP 语言的用户界面部分以母语显示。 在国家或区域通常使用两种语言中，您可以通过应用 LIP 语言包通过提供更好的用户体验。</p></td>
</tr>
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
<p>所需的某些地区呈现出现在文档中的文本。 示例，TH-TH 要求泰国字体包。 若要了解详细信息，请参阅[第 2 版的功能上的需求 （功能）](features-on-demand-v2--capabilities.md)。</p></td>
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
<td align="left">基本的文本到语音识别</td>
<td align="left">识别语音输入，由 Cortana 和 Windows 语音识别。</td>
</tr>
<tr class="even">
<td align="left">零售演示体验</td>
<td align="left"><code>Microsoft-Windows-RetailDemo-OfflineContent-Content-fr-fr-Package</code></td>
<td align="left">基本</td>
<td align="left">[零售演示体验](https://msdn.microsoft.com/windows/uwp/monetize/retail-demo-experience)</td>
</tr>
<tr class="odd">
<td align="left">WinRE</td>
<td align="left">多个，请参阅[自定义 Windows RE](customize-windows-re.md)。</td>
<td align="left">无</td>
<td align="left">用来帮助最终用户修复和恢复他们的 Pc。 请参阅[自定义 Windows RE](customize-windows-re.md)。</td>
</tr>
</tbody>
</table>

 

## <a name="span-idwheredoidownloadthelanguagepacksspanspan-idwheredoidownloadthelanguagepacksspanspan-idwheredoidownloadthelanguagepacksspanwhere-do-i-download-the-language-packs"></a><span id="Where_do_I_download_the_language_packs_"></span><span id="where_do_i_download_the_language_packs_"></span><span id="WHERE_DO_I_DOWNLOAD_THE_LANGUAGE_PACKS_"></span>何处下载语言包？


Oem 和系统构建者可以获取程序包和功能从中心下载专用的 Oem 和系统构建者。

用户可以通过转到**设置**中安装多个语言和功能&gt;**时间和语言** &gt; **地区和语言** &gt; **添加一种语言**。 若要了解详细信息，请参阅[如何添加到您的 PC 的输入的语言](http://go.microsoft.com/fwlink/?LinkId=619289)。

若要查看可用，请参阅[可用语言包的 Windows](available-language-packs-for-windows.md)。

## <a name="span-idotherconsiderationsspanspan-idotherconsiderationsspanspan-idotherconsiderationsspanother-considerations"></a><span id="Other_considerations"></span><span id="other_considerations"></span><span id="OTHER_CONSIDERATIONS"></span>其他考虑事项


-   某些语言需要比其他人更多的硬盘存储空间。
-   尽管您可以添加多个语言包使用命令一次︰ **DISM /Add-Package**， **DISM /Apply-Unattend**或[LPKSetup](http://go.microsoft.com/fwlink/?LinkID=624512)，不要添加太多在一次，因为设备可能没有足够的内存来处理它。 一般性建议︰ 从 Windows 在审核模式下，不超过 20 将语言包添加一次。 从 Windows PE 中，不添加多 7 个。 如果 WinPE 仍然用尽了内存，您可以[自定义加上临时存储 （暂存空间） 的 WinPE](winpe-mount-and-customize.md)。
-   不支持跨语言升级。 这意味着，在升级或迁移，如果升级或迁移已安装多个语言包的操作系统可以升级或迁移到系统默认 UI 语言只。 例如，如果英语是默认语言，您可以升级或迁移到英语。
-   无法删除默认语言，因为它用于生成计算机安全标识符 (Sid)。 默认用户界面语言是语言中的所选期间出的框中体验 (OOBE)，如果您跳过 OOBE 指定在部署映像服务和管理 (DISM) 命令行工具或无人参与的应答文件中的用户界面语言。
-   若要添加语言包，使用 Windows PE，您可能需要将页面文件支持添加到 Windows PE。 有关详细信息，请参阅[部署映像服务和管理 (DISM) 最佳做法](deployment-image-servicing-and-management--dism--best-practices.md)。
-   不要更新之后安装语言包。 如果您安装的更新 (修补程序后，常规分发版本\[GDR\]，或服务包\[SP\]) 之前安装的语言包更新中包含的特定于语言的更改不会应用，您将需要重新安装此更新包含依赖于语言的资源。 总是在安装更新之前安装语言包。
-   语言包的版本必须匹配的 Windows 的版本。 例如，不能将 Windows 10 语言包添加到 Windows 8，或者将 Windows 8 语言包添加到 Windows 10。 此外必须匹配的内部版本号。

## <a name="span-idlpinstallmethodsspanspan-idlpinstallmethodsspanspan-idlpinstallmethodsspaninstallation-methods"></a><span id="LPInstallMethods"></span><span id="lpinstallmethods"></span><span id="LPINSTALLMETHODS"></span>安装方法


通过以下方式，可以向图像添加语言包︰

-   [**脱机安装**](#add-offline)。 如果您需要添加语言包或在自定义 Windows 映像上配置国际设置，您可以使用 DISM。
-   [**使用 Windows 安装程序。**](#add-setup)
-   **在正在运行的操作系统。** 如果您需要启动的操作系统安装应用程序或用于测试和验证安装，可以通过使用 DISM 或语言包安装工具 (Lpksetup.exe) 将语言包添加到正在运行的操作系统。 此方法仅用于存储在 Windows 映像之外的语言包。 有关详细信息，请参阅[添加和删除在运行 Windows 安装的语言包](add-and-remove-language-packs-on-a-running-windows-installation.md)，并[向窗口中添加语言界面包](add-language-interface-packs-to-windows.md)。

## <a name="span-idaddsetupspanspan-idaddsetupspanadd-or-remove-languages-using-windows-setup"></a><span id="add_setup"></span><span id="ADD_SETUP"></span>添加或删除 Windows 安装程序使用的语言


**若要使用 Windows 安装程序部署多语言 Windows 版本**

1.  添加或删除语言包中的**\\Langpacks**分布共享中的文件夹。
2.  重新创建 Lang.ini 文件。 Windows 安装程序使用 Lang.ini 文件来标识图像内和 Windows 分发共享中的语言包。 Lang.ini 文件还确定将在 Windows 安装过程中显示的语言。 如果您计划创建包含多种语言的映像的恢复媒体，还必须重新生成 Lang.ini 文件。

    您可以使用 DISM 国际服务命令行选项来重新创建 Lang.ini 文件基于任何语言包更新。 不要手动修改 Lang.ini 文件。 若要了解详细信息，请参阅[DISM 语言和国际服务命令行选项](dism-languages-and-international-servicing-command-line-options.md)。

3.  如果您部署多语言映像，或者需要将特定的语言包应用于 Windows 映像以获得特定的设备，您可以使用 Windows 安装程序和无人参与的答案文件添加语言包。 语言包必须添加到映像，然后才能配置国际设置。 有关如何将语言包添加到答案文件的详细信息，请参阅[添加到答案文件的包](https://msdn.microsoft.com/library/windows/hardware/dn915066)。 要添加语言包并配置国际设置，请使用**WindowsPE**配置阶段，若要添加语言包并配置国际设置其他配置阶段。 有关详细信息，请参阅[Windows 中配置国际设置](configure-international-settings-in-windows.md)
    
    **请注意** 如果答案文件中指定语言和区域设置，这些设置会覆盖任何先前的默认值。 例如，如果您先更改默认`UILanguage`到 FR-FR 设置通过使用 DISM 命令行工具在脱机映像上，然后以后应用的无人参与的应答文件中指定 EN-US 作为用户界面语言，EN-US 将默认用户界面语言。   

4.  使用安装程序来安装分发共享中的语言包。

若要了解详细信息，请参阅[添加多语言支持添加到 Windows 分发](add-multilingual-support-to-a-windows-distribution.md)或[Windows 安装程序将添加多语言支持](add-multilingual-support-to-windows-setup.md)。

## <a name="span-idaddofflinespanspan-idaddofflinespanadd-or-remove-languages-offline"></a><span id="add_offline"></span><span id="ADD_OFFLINE"></span>添加或删除语言脱机

下面介绍了如何添加和移除脱机映像 (install.wim) 上的语言。

为了节省空间，您可以删除英语语言组件部署到非英语地区时。 您将需要卸载它们从添加它们的顺序相反。

**将这些映像装载**

-   安装 Windows 和 Windows RE 映像。 Windows RE 图像文件是 Windows 映像的一部分。

    ``` syntax
    md C:\mount\windows
    Dism /Mount-Image /ImageFile:install.wim /Index:1 /MountDir:"C:\mount\windows"
    md C:\mount\winre
    Dism /Mount-Image /ImageFile:"C:\mount\windows\Windows\System32\Recovery\winre.wim" /index:1 /MountDir:"C:\mount\winre"
    ```

**添加语言**

1.  添加到 Windows 的语言。 可以使用 /Add-Package 或 /Add-Capabilities 命令来添加功能。

    对于具有依赖关系的软件包，请确保按顺序安装软件包。 例如，若要启用 Cortana，安装︰ 语言包**.cab**，然后**基本**， **TextToSpeech**，然后单击**语音**，按此顺序。

    如果您不能确定的依赖项，则确定以将它们放在同一文件夹中，并将它们同时使用相同的 DISM /Add-Package 命令。

    添加语言包之后, 确认，它是在图像中。

    ``` syntax
    rem Remove the paragraph marks to make this into one really big, long command. 
    Dism /Add-Package /Image:"C:\mount\windows"
         /PackagePath="C:\Languages\Microsoft-Windows-Client-Language-Pack_x64_fr-fr.cab"
         /PackagePath="C:\Languages\Microsoft-Windows-LanguageFeatures-Basic-fr-fr-Package.cab"
         /PackagePath="C:\Languages\Microsoft-Windows-LanguageFeatures-OCR-fr-fr-Package.cab"
         /PackagePath="C:\Languages\Microsoft-Windows-LanguageFeatures-Handwriting-fr-fr-Package.cab"
         /PackagePath="C:\Languages\Microsoft-Windows-LanguageFeatures-TextToSpeech-fr-fr-Package.cab"
         /PackagePath="C:\Languages\Microsoft-Windows-LanguageFeatures-Speech-fr-fr-Package.cab"
    Dism /Get-Capabilities /Image:"C:\mount\windows"
    ```

2.  添加其他功能，如该区域所需的字体。 若要了解详细信息，请参阅[第 2 版的功能上的需求 （功能）](features-on-demand-v2--capabilities.md)。

    ``` syntax
    rem Thai example (add th-TH first).
    Dism /Add-Package /Image:"C:\mount\windows"
         /PackagePath="C:\Languages\fr-fr x64\Microsoft-Windows-LanguageFeatures-Fonts-Thai-Package"
    Dism /Get-Capabilities /Image:"C:\mount\windows"
    ```

3.  当您添加语言到 Windows 中，如果可能，请将它们添加到 WinRE 以确保在恢复方案中提供一致的语言体验。 这就要求相匹配的窗口并在 Windows ADK 版本。 Windows RE 现在需要 WinPE HTA 程序包，这是新的 Windows 10。

    添加文件包后, 确认它们在图像中。

    ``` syntax
    Dism /Image:C:\mount\winre /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\lp.cab"
    Dism /Image:C:\mount\winre /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-Rejuv_fr-fr.cab"
    Dism /Image:C:\mount\winre /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-EnhancedStorage_fr-fr.cab"
    Dism /Image:C:\mount\winre /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-Scripting_fr-fr.cab"
    Dism /Image:C:\mount\winre /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-SecureStartup_fr-fr.cab"
    Dism /Image:C:\mount\winre /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-SRT_fr-fr.cab"
    Dism /Image:C:\mount\winre /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-WDS-Tools_fr-fr.cab"
    Dism /Image:C:\mount\winre /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-WMI_fr-fr.cab"
    Dism /Image:C:\mount\winre /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-StorageWMI_fr-fr.cab"
    Dism /Image:C:\mount\winre /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-HTA_fr-fr.cab"
    Dism /Get-Packages /Image:"C:\mount\winre"
    ```

    /Get-Packages 的输出示例︰ 程序包标识︰ Microsoft Windows WinPE Rejuv\_fr fr...FR-FR ~ 10.0.9926.0 状态︰ 安装

**添加语言界面包 (LIP)**

1.  将 LIP 和所需/可用的功能添加到 Windows 映像。 某些地区没有任何相关的功能，而其他人有部分或全部设置。

    添加文件包后, 确认它们在图像中。

    ``` syntax
    Dism /Image:C:\mount\windows /Add-Package /PackagePath:C:\Languages\Microsoft-Windows-Client-Language-Pack_x64_bn-in.cab
         /PackagePath="C:\Languages\bn-in x64\Microsoft-Windows-LanguageFeatures-Basic-bn-in-Package.cab"
    ```

2.  添加其他功能，如该区域所需的字体。

    ``` syntax
    Dism /Add-Package /Image:"C:\mount\windows"
         /PackagePath="C:\Languages\Microsoft-Windows-LanguageFeatures-Fonts-Beng-Package"
    ```

3.  验证它们在图像中。

    ``` syntax
    Dism /Get-Packages /Image:"C:\mount\windows" 
    ```

**删除语言**

1.  为了节省空间，可以从映像中删除语言。

    您将需要卸载它们从添加它们的顺序相反。

    您不能删除依赖于其他软件包的功能。 例如，如果有法语的手写和安装的基本功能，不能删除的基本功能。 此操作将失败。

    可以使用 DISM /Remove-Package 或 /Remove-Capability DISM 命令删除功能和 /DISM /Get-Packages 或 DISM /Get-Capabilities 来验证它们在图像中不再是。

    ``` syntax
    DISM /Remove-Capability /Image:"C:\mount\windows"
     /CapabilityName:Language.Speech~~~en-US~0.0.1.0 
    DISM /Remove-Capability /Image:"C:\mount\windows"
     /CapabilityName:Language.TextToSpeech~~~en-US~0.0.1.0
    DISM /Remove-Capability /Image:"C:\mount\windows"
     /CapabilityName:Language.Handwriting~~~en-US~0.0.1.0
    DISM /Remove-Capability /Image:"C:\mount\windows"
     /CapabilityName:Language.OCR~~~en-US~0.0.1.0
    DISM /Remove-Capability /Image:"C:\mount\windows"
     /CapabilityName:Language.Basic~~~en-US~0.0.1.0
    Dism /Remove-Package /Image:"C:\mount\windows" /PackageName:Microsoft-Windows-Client-LanguagePack-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0
    DISM /Get-Packages /Image:"C:\mount\windows"
    DISM /Get-Capabilities /Image:"C:\mount\windows"
    ```

    这也是确定，只需删除语言包，而不删除的语言功能。 一周后在用户完成 OOBE，如果用户没有添加语言到他们输入的语言的列表中，Windows 会自动清除出未使用的语言能力。

2.  删除 Windows RE 可选组件。 删除后，请验证它们在图像中不再是。 替换为您正在使用的生成生成号 10.0.10120.0。 

    ``` syntax
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-Rejuv-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0 
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-HTA-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-StorageWMI-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0 
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-WMI-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-WDS-Tools-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0 
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-SRT-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0 
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-SecureStartup-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0 
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-Scripting-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-EnhancedStorage-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:Microsoft-Windows-WinPE-LanguagePack-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0
    Dism /Get-Packages /Image:"C:\mount\winre"
    ```

3.  **已知问题**︰ 如果已经将英语语言包中，删除 Windows 10 构建 10240 中，您将需要启动到审核模式的图像，并使用命令︰`sfc.exe /scannow /verify`来修复 Windows 32 位应用程序的问题。 有关如何执行此操作的脚本的示例，请参见[实验室 2a︰ 答案文件︰ 更新设置并运行脚本](update-windows-settings-and-scripts-create-your-own-answer-file-sxs.md)。

**重新安装应用程序 （需要时添加语言）**

注意︰ Windows 10，1607，版本中不再需要删除收件箱的应用程序。 如果要这样做，DISM 命令可能会失败。

1.  重新安装应用程序。 下面的示例演示如何开始收件箱应用程序重新安装。 用适当的包每个收件箱的应用程序 （除了 AppConnector) 重复上述步骤。

    ``` syntax
    Dism /Image:"c:\mount\windows" /Add-ProvisionedAppxPackage /packagepath:<path to appxbundle>\2b362ab83144485d9e9629ad2889a680.appxbundle /licensepath:<path to license file> \2b362ab83144485d9e9629ad2889a680_License1.xml
    ```

2.  Windows 桌面应用程序︰ 将经常需要重新安装这些太，因为它们通常包括在安装时选择的特定于语言的文件。 您将无法更新这些使用脱机服务;相反，您将需要重新捕获映像，或者创建一个单独的资源调配软件包为 Windows 桌面应用程序。

**对于由 Windows 安装程序或分发共享的安装，更新语言列表**

1.  这只是要求如果您分发多语言 Windows 安装媒体，或通过一个共享分发 Windows。

    重新创建 lang.ini 文件。

    ``` syntax
    Dism /Image:C:\mount\windows /gen-langini /distribution:C:\my_distribution
    ```

    Lang.ini 文件 c:\\myDistribution\\源看起来与以下内容类似︰

    ``` syntax
    [Available UI Languages]
    ca-ES = 2
    es-ES = 3
     
    [Fallback Languages]
    es-ES = en-us
    ```

2.  通过使用 DISM 查看默认 Windows 映像中的国际设置。

    ``` syntax
    Dism /Image:C:\mount\windows /get-intl
    ```

    例如，您应该看到类似于下面的输出︰

    ``` syntax
    Reporting offline international settings.
     
    Default system UI language : es-ES
    System locale : ca-ES
    Default time zone : Romance Standard Time
    User locale for default user : ca-ES
    Location : Spain (GEOID = 217)
    Active keyboard(s) : 0403:0000040a
    Keyboard layered driver : PC/AT Enhanced Keyboard (101/102-Key)
     
    Installed language(s): ca-ES
      Type : Partially localized language, LIP type.
    Installed language(s): es-ES
      Type : Fully localized language.
     
    Reporting distribution languages.
     
    The default language in the distribution is:
    es-ES
    ```

**更改默认语言**

-   设置默认的 Windows 语言以匹配您的客户的首选的语言。

    ``` syntax
    Dism /Set-AllIntl:fr-fr /Image:C:\mount\windows
    ```

**卸载映像**

-   卸载 Windows RE 和 Windows 映像。

    ``` syntax
    Dism /Unmount-Image /MountDir:"C:\mount\winre" /Commit
    Dism /Unmount-Image /MountDir:"C:\mount\windows" /Commit
    ```

## <a name="span-idlpremovaltimerspanspan-idlpremovaltimerspanspan-idlpremovaltimerspanthe-language-pack-removal-task"></a><span id="LPRemovalTimer"></span><span id="lpremovaltimer"></span><span id="LPREMOVALTIMER"></span>语言包删除任务


在 Windows 10 语言包删除任务在所有 Windows 版本上运行。 但是，不会删除任何通过控制面板的语言首选项部分中的用户选择的语言。 用户可以选择运行多种语言并不由用户的任何语言包从计算机中删除。 此外，不会删除任何由用户安装的语言包。

运行 Sysprep 工具将语言包删除时钟重置。 直到下一次 OOBE 运行并重新启动计算机，不会重新启动时钟。 如果自定义 Windows 映像时，请考虑启动到审核模式下进行自定义。 引导到审核模式时，语言包删除任务将不会启动。 有关审核模式的详细信息，请参阅[启动到审核模式或 OOBE 的 Windows](boot-windows-to-audit-mode-or-oobe.md)。 也可以更新脱机 Windows 映像而不启动映像。 有关详细信息，请参阅[Windows 映像使用 DISM 服务](service-a-windows-image-using-dism.md)

使用`SkipMachineOobe`Microsoft Windows 外壳程序安装组件中的设置不跳过语言包删除任务。

**请注意**  
语言包删除任务将不删除嘴唇。

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[语言包](language-packs-and-windows-deployment.md)

[可用语言包的 Windows](available-language-packs-for-windows.md)

[功能需求 V2 （功能）](features-on-demand-v2--capabilities.md)

[Windows 语言包默认值](windows-language-pack-default-values.md)

[对于 Windows 语言包默认输入法区域设置](default-input-locales-for-windows-language-packs.md)

 

 






