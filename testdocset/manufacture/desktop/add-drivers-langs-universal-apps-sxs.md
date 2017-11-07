---
author: KPacquer
Description: "实验室 5︰ 添加语言"
MSHAttr: PreferredLib:/library/windows/hardware
title: "实验室 5︰ 添加语言"
ms.openlocfilehash: dd2be5018db5793ad4e72818f4c11590b62ba557
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="span-idaddlanguagesspanlab-5-add-languages"></a><span id="Add_languages"></span>实验室 5︰ 添加语言

**备注** 

*    **添加更新语言之前。** 其中包括的修补程序、 常规分发版本或服务包。 如果您以后添加更新，您将需要重新添加该语言。

*    **在应用程序之前添加语言**。 这包括通用的 Windows 应用程序、**收件箱 （必需的） 的应用程序**和桌面应用程序。 我们将向您展示如何将这些内容添加随后在[实验室 6︰ 添加通用的 Windows 应用程序，开始拼贴和任务栏针脚](add-universal-apps-sxs.md)

*    **添加到您的恢复映像，您的语言太**︰ 许多公共语言可以添加到恢复映像。 我们将向您展示如何将这些内容添加随后在[实验室 10︰ 更新恢复映像](update-the-recovery-image.md)。

## <a name="span-idmounttheimagespanmount-the-image"></a><span id="Mount_the_image"></span>装入该映像

**步骤 1︰ 装载映像**

使用步骤，可从[实验室 3︰ 添加设备驱动程序 （.inf 样式）](add-device-drivers.md)装载映像。 短的版本︰

1.  打开命令行以管理员身份 (**开始**> 键入**部署**> 右键单击**部署和图像处理工具环境** > **以管理员身份运行**。)

2.  对该文件进行备份 (`copy "C:\Images\Win10_x64\sources\install.wim" C:\Images\install-backup.wim`)

3.  装入该映像 (`md C:\mount\windows`，然后`Dism /Mount-Image /ImageFile:"C:\Images\install.wim" /Index:1 /MountDir:"C:\mount\windows" /Optimize`)

## <a name="span-idaddlanguagestotheimagespanadd-languages-to-the-image"></a><span id="Add_languages_to_the_image"></span>将语言添加到映像

始终使用的语言包和按需登录功能 (FOD) 包相匹配的语言和平台的 Windows 映像。

按需 (FODs) 的功能是可以在任何时候添加的 Windows 功能包。 当用户需要一种新功能时，它们可以从 Windows Update 请求功能包。 Oem 可以预安装这些功能以启用这些开箱即用的设备上。

常见功能包括像手写识别的语言资源。 这些功能是启用完整的 Cortana 功能所需要的。

下表显示 Windows 10 的语言包和可用的组件的类型︰

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
<td align="left"><code>Microsoft-Windows-Client-Language-Pack_x64_es-es</code></td>
<td align="left">无</td>
<td align="left">包括基本的 Cortana 功能的用户界面文本。</td>
</tr>
<tr class="even">
<td align="left">语言界面包</td>
<td align="left"><code>Microsoft-Windows-Client-Language-Interface-Pack_x64_ca-es</code></td>
<td align="left">要求特定的完全本地化或部分本地化的语言包。 示例︰ ca-ES 要求 es-ES。 若要了解详细信息，请参阅<a href="available-language-packs-for-windows.md">可用语言包的 Windows</a>。</td>
<td align="left"><p>包括基本的 Cortana 功能的用户界面文本。</p></td>
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
<p>所需的某些地区呈现出现在文档中的文本。 示例，TH-TH 要求泰国字体包。 若要了解详细信息，请参阅<a href="features-on-demand-v2--capabilities.md">第 2 版的功能上的需求 （功能）。</p></td>
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
</tbody>
</table>

**步骤 2︰ 添加或更改语言**

1.  将语言和点播功能添加到 Windows 映像。

    语言的更新具有他们需要安装在特定的顺序。 例如，若要启用 Cortana，安装︰ **Microsoft 的 Windows 的客户端的语言包**，然后**– 基本**，然后**– 字体**，然后**– TextToSpeech**，然后**– 语音**，按此顺序。 如果您不能确定的依赖项，则确定以将它们放在同一文件夹中，并将它们全部使用相同的 DISM /Add-Package 命令。 
    
    用于添加法语，x64 的示例︰

    ``` syntax
    Dism /Add-Package /Image:"C:\mount\windows" /PackagePath="C:\Languages\fr-fr x64\Microsoft-Windows-Client-Language-Pack_x64_fr-fr" /PackagePath="C:\Languages\fr-fr x64\Microsoft-Windows-LanguageFeatures-Basic-fr-fr-Package.cab" /PackagePath="C:\Languages\fr-fr x64\Microsoft-Windows-LanguageFeatures-OCR-fr-fr-Package.cab" /PackagePath="C:\Languages\fr-fr x64\Microsoft-Windows-LanguageFeatures-Handwriting-fr-fr-Package.cab" /PackagePath="C:\Languages\fr-fr x64\Microsoft-Windows-LanguageFeatures-TextToSpeech-fr-fr-Package.cab" /PackagePath="C:\Languages\fr-fr x64\Microsoft-Windows-LanguageFeatures-Speech-fr-fr-Package.cab" /LogPath=C:\mount\dism.log
    ```

    用于添加日语，x64 的示例。 请注意，日语要求字体包。

    ``` syntax
    Dism /Add-Package /Image:"C:\mount\windows" /PackagePath="C:\Languages\ja-jp x64\Microsoft-Windows-Client-Language-Pack_x64_ja-jp" /PackagePath="C:\Languages\ja-jp x64\Microsoft-Windows-LanguageFeatures-Basic-ja-jp-Package.cab" /PackagePath="C:\Languages\ja-jp x64\Microsoft-Windows-LanguageFeatures-OCR-ja-jp-Package.cab" /PackagePath="C:\Languages\ja-jp x64\Microsoft-Windows-LanguageFeatures-Handwriting-ja-jp-Package.cab" /PackagePath="C:\Languages\ja-jp x64\Microsoft-Windows-LanguageFeatures-TextToSpeech-ja-jp-Package.cab" /PackagePath="C:\Languages\ja-jp x64\Microsoft-Windows-LanguageFeatures-Speech-ja-jp-Package.cab" /PackagePath:"C:\Languages\ja-jp x64\Microsoft-Windows-LanguageFeatures-Fonts-Jpan-Package.cab"  /LogPath=C:\mount\dism.log
    ```

    不是每个地区都有字体或对每个功能的功能包。

2.  验证语言包是图像的一部分︰

    ``` syntax
    Dism /Get-Packages /Image:"C:\mount\windows"
    ```

    其中*C*是驱动器的包含图像的驱动器号。

    检查生成的软件包列表并验证列表包含的软件包。 例如︰

    ``` syntax
    Package Identity : Microsoft-Windows-Client-LanguagePack  ...  fr-FR~10.0.14393.0
    State : Installed
    ```

3.  验证语言组件是图像的一部分︰

    ``` syntax
    Dism /Get-Capabilities /Image:"C:\mount\windows"
    ```

    其中*C*是驱动器的包含图像的驱动器号。

    检查生成的软件包列表并验证列表包含的软件包。 例如︰

    ``` syntax
    Capability Identity : Language.Basic~~~fr-fr~0.0.1.0
    State : Installed
    ...
    Capability Identity : Language.Handwriting~~~fr-fr~0.0.1.0
    State : Installed
    ```

4.  更改默认的语言以匹配您的客户的首选的语言。

    ``` syntax
    Dism /Set-AllIntl:fr-fr /Image:"C:\mount\windows"
    ```
    
5.  更改默认时区与时区匹配为您的客户。 [时区的列表](default-time-zones.md)，请参阅。

    ``` syntax
    Dism /Set-TimeZone:"W. Europe Standard Time" /Image:"C:\mount\windows"
    ```

**步骤 3︰ 删除 （仅对于非英语区域需要） 的基本语言**

1.  为了节省空间，您可以删除英语语言组件部署到非英语地区时。 可以卸载它们按相反的顺序从如何添加它们，或者相同的 DISM /remove-package 命令中同时删除。

    ``` syntax
    dism /Remove-Package /Image:"c:\mount\windows" /PackageName:Microsoft-Windows-Client-LanguagePack-Package~31bf3856ad364e35~amd64~en-US~10.0.14393.0 /PackageName:Microsoft-Windows-LanguageFeatures-Basic-en-us-Package~31bf3856ad364e35~amd64~~10.0.14393.0 /PackageName:Microsoft-Windows-LanguageFeatures-Handwriting-en-us-Package~31bf3856ad364e35~amd64~~10.0.14393.0 /PackageName:Microsoft-Windows-LanguageFeatures-OCR-en-us-Package~31bf3856ad364e35~amd64~~10.0.14393.0 /PackageName:Microsoft-Windows-LanguageFeatures-Speech-en-us-Package~31bf3856ad364e35~amd64~~10.0.14393.0 /PackageName:Microsoft-Windows-LanguageFeatures-TextToSpeech-en-us-Package~31bf3856ad364e35~amd64~~10.0.14393.0  /LogPath=C:\mount\dism.fod2.log
    ```

    其中*C*是驱动器的驱动器号。

    **故障排除**如果删除此程序包由于挂起的更新失败，请再次尝试该命令。 

2.  验证语言包不再是图像的一部分︰

    ``` syntax
    Dism /Get-Packages /Image:"C:\mount\windows"
    ```

    其中*C*是驱动器的包含图像的驱动器号。

3.  验证语言组件不再是图像的一部分︰

    ``` syntax
    Dism /Get-Capabilities /Image:"C:\mount\windows"
    ```

    其中*C*是驱动器的包含图像的驱动器号。
    ```


## <span id="Unmount_the_images"></span> Unmount the images

**Step 4: Unmount the images**

1.  Close all applications that might access files from the image.

2.  Commit the changes and unmount the Windows image:

    ``` syntax
    Dism /Unmount-Image /MountDir:"C:\mount\windows" /Commit
    ```

## <a name="span-idtryitoutspantry-it-out"></a><span id="Try_it_out"></span>试一下

**步骤 5︰ 将映像应用到新计算机**

使用步骤，可从[实验室 2︰ 使用脚本的部署 Windows](deploy-windows-with-a-script-sxs.md)将该图像复制到 USB 驱动器的存储，应用该映像，并启动它。 短的版本︰

1.  将图像文件复制到的存储驱动器。
2.  [引导到 Windows PE 中使用 Windows PE usb 闪存盘的参考设备](install-windows-pe-sxs.md)。
3.  查找存储驱动器的驱动器号 (`diskpart, list volume, exit`)。
4.  将映像应用︰ `D:\ApplyImage.bat D:\Images\install.wim`。
5.  断开连接的驱动器，然后重新启动 (`exit`)。

**第 6 步︰ 检查更新**

1.  PC 启动时，如果您安装了多种语言后，您应该在现成的体验过程收到一份 lanugages。 

2.  无论是创建新的用户帐户，或者按 Ctrl + Shift + F3 要重新启动到内置的管理员帐户 （也称为是审核模式）。

3.  用鼠标右键单击**开始**按钮，然后选择**命令提示符 （管理员）**。

4.  验证正确显示语言包︰

    ``` syntax
    C:\Windows\System32\Dism /Get-Packages /Online
    ```

    检查生成的软件包列表并验证列表包含的软件包。 例如︰

    ``` syntax
    Package Identity : Microsoft-Windows-Client-LanguagePack  ...  fr-FR~10.0.14393.0
    State : Installed
    ```
    
下一步︰[实验室 6︰ 添加通用的 Windows 应用程序，开始拼贴和任务栏针脚](add-universal-apps-sxs.md)