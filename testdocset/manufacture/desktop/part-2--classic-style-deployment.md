---
author: Justinha
Description: "实验室 2，经典样式部署 Windows ADK 在使用命令行工具自定义和部署 Windows 映像。"
ms.assetid: 31ec67f4-8a6b-4bc3-a8b8-12e6c537d6a6
MSHAttr: PreferredLib:/library/windows/hardware
title: "实验室 2︰ 经典样式映像和部署"
ms.openlocfilehash: c852145c24058f829a7bab2f56ee67ea4e48697e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="span-idpart2classic-styledeploymentspanlab-2-classic-style-imaging-and-deployment"></a><span id="part_2__classic-style_deployment"></span>实验室 2︰ 经典样式映像和部署

实验室 2，经典样式部署 Windows ADK 在使用命令行工具自定义和部署 Windows 映像。

## <a name="span-iddesignyourimagesspanspan-iddesignyourimagesspanspan-iddesignyourimagesspandesign-your-images"></a><span id="Design_your_images"></span><span id="design_your_images"></span><span id="DESIGN_YOUR_IMAGES"></span>设计您的图像

下面是您可以设计的硬件配置的一组示例。

|                              |              |                     |                                   |
|------------------------------|--------------|---------------------|-----------------------------------|
| 硬件配置︰      | 1            | 1B                  | 2                                 |
| 窗体因子                  | 小触 | 2--1              | 笔记本                          |
| RAM                          | 1 GB         | 2 GB                | 4 GB                              |
| 磁盘容量和类型       | 16 GB eMMC   | 32 GB eMMC          | 500 GB 的硬盘驱动器                        |
| 显示大小                 | 8"           | 10"                 | 14 英寸                               |
| Windows 的 SKU                  | 核心         | 专业人员                 | 核心                              |
| 语言                  | EN-US        | EN-US，FR-FR，ES-ES | EN GB，特拉华州的特拉华州，FR-FR，ES-ES ZH-CN |
| Cortana                      | 是          | 是                 | 是                               |
| 收件箱的应用程序 （通用）       | 是          | 是                 | 是                               |
| 绘图笔                          | 否           | 是                 | 否                                |
| 办公室 （通用）           | 是          | 是                 | 是                               |
| Windows 桌面应用程序 | 否           | 是                 | 是                               |
| Office 2016 年                  | 否           | 是                 | 是                               |
| 精简的操作系统                   | 是          | 是                 | 否                                |

 

实验室 2 覆盖自定义和部署 Windows 映像与硬件配置 1B 的可选步骤和 2 的所有步骤。 实验室 2a 演示如何继续通过 Windows 桌面应用程序中添加自定义图像。 实验室 2b 显示了如何处理与 Windows 更新自定义映像。

## <a name="span-idprepimagesspanspan-idprepimagesspancustomize-and-deploy-a-windows-image"></a><span id="prepimages"></span><span id="PREPIMAGES"></span>自定义和部署 Windows 映像


在此实验室中，您可以通过添加和删除语言、 驱动程序和程序包修改图像。 您可以将一种语言、 语言组件和 （如存储驱动程序或视频驱动程序） 启动关键驱动程序添加到 Windows 映像和内置的恢复工具，以及升级版，并将其设置为自动启动到审核模式工厂车间维修。

![图像︰ 复制图像文件和部署脚本](images/dep-win8-sxs-createmodelspecificfiles.jpg)

**第 1 步︰ 复制基本的 Windows 映像文件**

1.  单击**开始**，然后键入**部署**。 用鼠标右键单击**部署和图像处理工具环境**，然后选择**以管理员身份运行**。
2.  创建您想要修改的图像的一个副本。 该实验的目的，使用 x64 或 x86 的基本 Windows 10 图像文件︰

    ``` syntax
    copy "C:\Images\Win10_x64\sources\install.wim" C:\Images\WindowsWithOffice.wim
    ```

    这可能需要几分钟。

**步骤 2︰ 安装 Windows 图像文件**

-   将 Windows 映像进行安装。 安装过程将图像文件的内容映射到在其中您可以查看和修改已装入的映像的位置。

    ``` syntax
    md C:\mount\windows
    Dism /Mount-Image /ImageFile:"C:\Images\WindowsWithOffice.wim" /Index:1 /MountDir:"C:\mount\windows" /Optimize
    ```

    其中*C*是驱动器的包含图像和*1*的驱动器号是驱动器的您想要使用的图像的索引。

    此步骤可能需要几分钟。

    **故障排除**

    如果该命令失败，请确保您正在使用 DISM 安装与 Windows ADK 的 Windows 10 版本。

    如果您的技术人员计算机使用 Windows 8.1、 Windows 8 或 Windows 7，使用**部署和图像处理工具环境**来访问 Windows ADK 的 Windows 10 版本一起安装的工具。

    不装入图像到受保护的文件夹，例如，您的用户\\文档文件夹。

    如果 DISM 进程被打断，可以考虑暂时断开与公用网络的连接和禁用病毒防护。

    如果 DISM 进程被打断，可以考虑从 Windows PE 环境中运行命令。

**第 3 步︰ 装载 Windows RE 图像文件**

-   装载 Windows RE 图像文件。 Windows RE 图像文件是 Windows 映像的一部分。

    ``` syntax
    md C:\mount\winre
    ```

    ``` syntax
    Dism /Mount-Image /ImageFile:"C:\mount\windows\Windows\System32\Recovery\winre.wim" /Index:1 /MountDir:"C:\mount\winre"
    ```

    其中*C*是驱动器的包含图像的驱动器号。

    此步骤可能需要几分钟。

    **请注意**  我们建议您在同一时间，以帮助确保所有必需的文件都包括在这两个图像更新的 Windows 和 Windows RE 图像。

     

**步骤 4︰ 添加到 Windows 的驱动程序**

1.  添加所有.inf 式的驱动程序所需的硬件。

    ``` syntax
    Dism /Add-Driver /Image:"C:\mount\windows" /Driver:"C:\Drivers\PnP.Media.V1\media1.inf" /LogPath=C:\mount\dism.log
    ```

    其中"c:\\驱动程序\\PnP.Media.V1\\media1.inf"是驱动程序软件包中的基.inf 文件。

    **请注意** 为本部分我们将添加 /LogPath 什么不对劲--如果没有添加您的驱动程序有问题的情况下，打开此文件可快速检查有错误。
    
    要安装所有的驱动程序从某个文件夹及其所有子文件夹，请指向该文件夹并使用 /Recurse 选项。

    ``` syntax
    Dism /Add-Driver /Image:"C:\mount\windows" /Driver:c:\drivers /Recurse
    ```

    **警告** 尽管 /Recurse 可能很方便，很容易膨胀与图像。 某些驱动程序包包括多个.inf 驱动程序包，通常有效负载从共享文件所在的文件夹。 安装过程中，每个.inf 驱动程序包扩展到一个单独的文件夹，每个都有有效载荷文件的副本。 我们看到其中有 900 MB 文件夹中的常见驱动程序将添加到图像时使用 /Recurse 选项添加 10 GB 的情况。

2.  请验证该驱动程序是图像的一部分︰

    ``` syntax
    Dism /Get-Drivers /Image:"C:\mount\windows"
    ```

    检查生成的软件包列表并验证列表包含的驱动程序。

3.  如果这些驱动程序对硬件进行引导至关重要，将它们添加到 Windows RE 映像，太。

    ``` syntax
    Dism /Add-Driver /Image:"C:\mount\winre" /Driver:"C:\Drivers\PnP.Media.V1\media1.inf" /LogPath=C:\mount\dism.log
    ```

4.  可选︰ 您可以从之前进行的测试中删除所有.inf 驱动程序︰

    ``` syntax
    Dism /Remove-Driver /Image:"C:\mount\windows" /Driver:"VideoDriver-Old.inf" /LogPath=C:\mount\dism.log
    ```

5.  Setup.exe 样式的任何驱动程序，您需要它们以后在审核模式下安装或使用自动配置包。 稍后在本部分，我们将介绍如何设置电脑自动启动到审核模式。

在 Windows 10 Oem 可以修改默认的开始布局并通过创建 LayoutModification.xml 文件，并将该文件放在正确的系统位置指定 OEM 图块的布局。

**步骤 5︰ 添加的文件，您需要修改开始布局 （可选）**

1.  创建一个 LayoutModification.xml 文件。 对于此实验室中，您可以使用 Pre Requesites 文档中的示例。 该示例将固定办公室，OneNote 和读者开始如果设备 (步骤 8) 上预装。 若要通过使用 XML 编辑器创建您自己的 LayoutModification.xml 文件，请参阅[示例脚本](windows-deployment-sample-scripts-sxs.md)。
2.  将 LayoutModification.xml 文件添加到 Windows 映像。 您需要将文件放在第一次启动之前以下特定位置。 如果该文件存在，则应当替换图像中已包含 LayoutModification.XML。

    ``` syntax
    C:\Mount\Windows\Users\Default\AppData\Local\Microsoft\Windows\Shell\
    ```

3.  如果您锁定要求.url 或.lnk 文件的图块，请将文件添加到以下的传统开始菜单目录︰
    -   应用程序数据 %%\\Microsoft\\Windows\\「 开始 」 菜单\\程序\\
    -   %ALLUSERSPROFILE%\\Microsoft\\Windows\\「 开始 」 菜单\\程序\\

**请注意** 如果用户重置其 PC 使用内置的恢复工具，开始布局可能会丢失。 您将学习如何确保这些设置都保留在[示例脚本](windows-deployment-sample-scripts-sxs.md)中的设备上。

 

## <a name="span-idaddorchangelanguagesandcortanafeaturesondemandoptionalspanspan-idaddorchangelanguagesandcortanafeaturesondemandoptionalspanspan-idaddorchangelanguagesandcortanafeaturesondemandoptionalspanadd-or-change-languages-and-cortana-features-on-demand-optional"></a><span id="Add_or_change_languages_and_Cortana_features_on_demand__Optional_"></span><span id="add_or_change_languages_and_cortana_features_on_demand__optional_"></span><span id="ADD_OR_CHANGE_LANGUAGES_AND_CORTANA_FEATURES_ON_DEMAND__OPTIONAL_"></span>添加或更改语言和 Cortana 功能按需 （可选）


**请注意** 跳过这部分的硬件配置 1。

 

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
<td align="left"><code>lp.cab</code></td>
<td align="left">无</td>
<td align="left">包括基本的 Cortana 功能的用户界面文本。</td>
</tr>
<tr class="even">
<td align="left">语言界面包</td>
<td align="left"><code>lp.cab</code></td>
<td align="left">要求特定的完全本地化或部分本地化的语言包。 示例︰ ca-ES 要求 es-ES。 若要了解详细信息，请参阅[可用语言包的 Windows](available-language-packs-for-windows.md)。</td>
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
</tbody>
</table>

 

**第 6 步︰ 添加或更改语言**

1.  将语言和点播功能添加到 Windows 映像。

    对于具有依赖关系的软件包，请确保按顺序安装软件包。 例如，若要启用 Cortana，安装︰ **lp.cab**，然后**– 基本**，然后**– 字体**，然后**– TextToSpeech**，然后**– 语音**，按此顺序。 如果您不能确定的依赖项，则确定以将它们放在同一文件夹中，并将它们全部使用相同的 DISM /Add-Package 命令。 不是每个地区都有字体或对每个功能的功能包。

    例如︰

    ``` syntax
    Dism /Add-Package /Image:"C:\mount\windows" /PackagePath="C:\Languages\fr-fr x64\lp.cab" /PackagePath="C:\Languages\fr-fr x64\Microsoft-Windows-LanguageFeatures-Basic-fr-fr-Package.cab" /PackagePath="C:\Languages\fr-fr x64\Microsoft-Windows-LanguageFeatures-OCR-fr-fr-Package.cab" /PackagePath="C:\Languages\fr-fr x64\Microsoft-Windows-LanguageFeatures-Handwriting-fr-fr-Package.cab" /PackagePath="C:\Languages\fr-fr x64\Microsoft-Windows-LanguageFeatures-TextToSpeech-fr-fr-Package.cab" /PackagePath="C:\Languages\fr-fr x64\Microsoft-Windows-LanguageFeatures-Speech-fr-fr-Package.cab" /LogPath=C:\mount\dism.log
    ```

2.  验证语言包是图像的一部分︰

    ``` syntax
    Dism /Get-Packages /Image:"C:\mount\windows"
    ```

    其中*C*是驱动器的包含图像的驱动器号。

    检查生成的软件包列表并验证列表包含的软件包。 例如︰

    ``` syntax
    Package Identity : Microsoft-Windows-Client-LanguagePack  ...  fr-FR~10.0.10020.0
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
    Dism /Set-AllIntl:fr-fr /Image:C:\mount\windows
    ```

**步骤 7︰ 删除 （仅对于非英语区域需要） 的基本语言**

1.  为了节省空间，您可以删除英语语言组件部署到非英语地区时。 您将需要卸载它们从添加它们的顺序相反。

    ``` syntax
    Dism /Remove-Package /Image:"C:\mount\windows" /PackageName:Microsoft-Windows-LanguageFeatures-Speech-en-us-Package~31bf3856ad364e35~amd64~~10.0.10120.0 /LogPath=C:\mount\dism.fod2.log

    Dism /Remove-Package /Image:"C:\mount\windows" /PackageName:Microsoft-Windows-LanguageFeatures-TextToSpeech-en-us-Package~31bf3856ad364e35~amd64~~10.0.10120.0 /LogPath=C:\mount\dism.fod2.log

    Dism /Remove-Package /Image:"C:\mount\windows" /PackageName:Microsoft-Windows-LanguageFeatures-Handwriting-en-us-Package~31bf3856ad364e35~amd64~~10.0.10120.0 /LogPath=C:\mount\dism.fod2.log

    Dism /Remove-Package /Image:"C:\mount\windows" /PackageName:Microsoft-Windows-LanguageFeatures-OCR-en-us-Package~31bf3856ad364e35~amd64~~10.0.10120.0 /LogPath=C:\mount\dism.fod2.log

    Dism /Remove-Package /Image:"C:\mount\windows" /PackageName:Microsoft-Windows-LanguageFeatures-Basic-en-us-Package~31bf3856ad364e35~amd64~~10.0.10120.0 /LogPath=C:\mount\dism.fod2.log

    Dism /Remove-Package /Image:"C:\mount\windows" /PackageName:Microsoft-Windows-Client-LanguagePack-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0 /LogPath=C:\mount\dism.fod2.log
    ```

    其中*C*是驱动器的驱动器号。

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

4.  删除 Windows RE 可选组件。 删除后，请验证它们在图像中不再是。

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

5.  **已知问题**︰ 如果已经将英语语言包中，删除 Windows 10 构建 10240 中，您将需要启动到审核模式的图像，并使用命令︰`sfc.exe /scannow /verify`来修复 Windows 32 位应用程序的问题。 有关如何执行此操作的脚本的示例，请参见[实验室 2a︰ 答案文件︰ 更新设置并运行脚本](update-windows-settings-and-scripts-create-your-own-answer-file-sxs.md)。

**步骤 8︰ 重新安装 （需要时添加语言） 的收件箱应用程序**

1.  删除现有的收件箱应用程序。 **（如果使用的通用于 2015 年 8 月 18 日之后获得的应用程序，则不需要此步骤）**。 下面的示例演示如何删除收件箱获得启动应用程序。 用适当的包每个收件箱的应用程序 （除了 AppConnector) 重复上述步骤。

    ``` syntax
    Dism /Image:"c:\mount\windows" /Remove-ProvisionedAppxPackage /PackageName:Microsoft.Getstarted_2015.522.28.1146_neutral_~_8wekyb3d8bbwe
    ```

    **请注意** 若要一次删除所有应用程序，打开一个命令提示符，以管理员身份、 定位到图像的文件夹中，并运行示例脚本:"删除\_应用程序\_在\_脱机\_image.cmd"的[示例脚本](windows-deployment-sample-scripts-sxs.md)。

     

2.  重新安装应用程序。 下面的示例演示如何开始收件箱应用程序重新安装。 用适当的包每个收件箱的应用程序 （除了 AppConnector) 重复上述步骤。

    ``` syntax
    Dism /Image:"c:\mount\windows" /Add-ProvisionedAppxPackage /packagepath:<path to appxbundle>\2b362ab83144485d9e9629ad2889a680.appxbundle /licensepath:<path to license file>\2b362ab83144485d9e9629ad2889a680_License1.xml
    ```

**第 9 步︰ 添加 Windows 通用应用程序或 Windows 8.1 应用商店应用程序 （可选）**

1.  可以通过使用 DISM Windows 通用应用程序和 Windows 8.1 商店应用程序添加到映像。 在此示例中，将预安装 Office，OneNote，Windows 读者 8.1。

    请跳过此步骤 1 的硬件配置。

    添加 AppX 包。

    ``` syntax
    Dism /Image:c:\mount\windows /Add-ProvisionedAppxPackage /PackagePath:c:\samples\excelpreview\excel.appxbundle /LicensePath:c:\samples\excelpreview\excel_license.xml
    ```

    其中 PackagePath 是指向应用程序捆绑包。

2.  DISM 命令重复上述步骤 OneNote，读卡器，Word 和 PowerPoint 的预览应用程序捆绑包。

如果 PC 运行陷入困境时，您的用户可能不能阅读/理解恢复屏幕除非相应的语言资源添加到 Windows 恢复环境 (Windows RE)。

只要有可能，尝试中添加和删除语言 Windows RE 在同一时间您添加和删除 Windows 映像以确保一致的恢复体验中。 （这并不总是可行的因为并不是所有的语言都有 Windows RE 等价物。）

**第 10 步︰ 将语言添加到恢复环境 （强烈建议添加语言时）**

1.  添加语言。 这些语言还包括 Windows ADK。 您必须使用 Windows ADK 的匹配版本 Windows RE 映像提供服务。

    **请注意** Windows RE 现在需要 WinPE HTA 程序包，这是新的 Windows 10。

    **请注意** WinPE WiFi 包不是特定于语言的并且不需要添加其他语言时要添加。 这是新的 Windows 10。

    ``` syntax
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\lp.cab"

    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-Rejuv_fr-fr.cab"

    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-EnhancedStorage_fr-fr.cab"

    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-Scripting_fr-fr.cab"

    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-SecureStartup_fr-fr.cab"

    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-SRT_fr-fr.cab"

    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-WDS-Tools_fr-fr.cab"

    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-WMI_fr-fr.cab"

    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-StorageWMI_fr-fr.cab"

    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-HTA_fr-fr.cab"
    ```

2.  设置默认恢复语言以匹配您的客户的首选的语言。

    ``` syntax
    Dism /Set-AllIntl:fr-fr /Image:C:\mount\winre
    ```

3.  可选︰ 从 Windows RE （仅对于非英语区域需要） 删除语言

    当从 Windows 中删除语言时，请从 Windows RE 以节省空间移除它们。

    您可以使用 /PackagePath 开关 （这需要匹配版本的 Windows 和 Windows ADK） 或 /PackageName 交换机 （这需要标识包包括版本号）。

    示例：

    ``` syntax
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-Rejuv-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0 /LogPath=C:\mount\dism.fod2.log
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-HTA-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0 /LogPath=C:\mount\dism.fod2.log
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-StorageWMI-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0 /LogPath=C:\mount\dism.fod2.log
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-WMI-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0 /LogPath=C:\mount\dism.fod2.log
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-WDS-Tools-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0 /LogPath=C:\mount\dism.fod2.log
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-SRT-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0 /LogPath=C:\mount\dism.fod2.log
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-SecureStartup-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0 /LogPath=C:\mount\dism.fod2.log
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-Scripting-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0 /LogPath=C:\mount\dism.fod2.log
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:WinPE-EnhancedStorage-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0 /LogPath=C:\mount\dism.fod2.log
    Dism /Remove-Package /Image:"C:\mount\winre" /PackageName:Microsoft-Windows-WinPE-LanguagePack-Package~31bf3856ad364e35~amd64~en-US~10.0.10120.0 /LogPath=C:\mount\dism.fod2.log
    ```

4.  验证语言包是图像的一部分︰

    ``` syntax
    Dism /Get-Packages /Image:"C:\mount\winre"
    ```

    其中*C*是驱动器的包含图像的驱动器号。

5.  检查生成的软件包列表并验证列表包含的软件包。 例如︰

    ``` syntax
    Package Identity : Microsoft-Windows-WinPE-Rejuv_fr-fr ...  fr-FR~10.0.9926.0
    State : Installed
    ```

## <a name="span-idmodifyspanspan-idmodifyspanother-modifications"></a><span id="modify"></span><span id="MODIFY"></span>其他修改


**步骤 11︰ 升级版从核心到 Pro （可选）**

1.  使用此过程可以将版本升级。 不能设置为更低版本的 Windows 映像。 您不应该在图像已更改为较高版本上使用此过程。

    确定哪些图像可以升级到的图像︰ 注意版本 Id 可用。

    ``` syntax
    Dism /Get-TargetEditions /Image:C:\mount\windows
    ```

2.  升级版。

    ``` syntax
    Dism /Set-Edition:Professional /Image:C:\mount\windows
    ```

## <span id="unmount"></span><span id="UNMOUNT"></span>


**第 12 步︰ 卸载映像**

1.  关闭所有应用程序可能会访问从图像文件。
2.  提交更改并卸载 Windows RE 映像︰

    ``` syntax
    Dism /Unmount-Image /MountDir:"C:\mount\winre" /Commit
    ```

    其中*C*是驱动器的包含图像的驱动器号。

    此过程可能需要几分钟的时间。

3.  使已更新的 Windows RE 映像的备份副本 （可选）。 这可以帮助您在 Windows 映像被破坏的情况下，保存您的工作。

    ``` syntax
    xcopy C:\mount\windows\Windows\System32\Recovery\winre.wim C:\Images\winre_with_drivers_for_fabrikam_model_1.wim /ah
    ```

    出现提示时，请为文件指定**F** 。

    **请注意** 该实验假设您希望保密的 winre.wim 在 install.wim，使您的语言和驱动程序的同步。 如果您想要在工厂车间，节省时间和您单独确定管理这些图像，您可能想要从映像中删除 winre.wim 并将其分别应用。

     

4.  检查 Windows RE 映像的新大小。

    ``` syntax
    Dir "C:\mount\windows\Windows\System32\Recovery\winre.wim"
    ```

    如果分区的大小大于 524,288,000 字节，兆字节转换文件大小、 添加的可用空间，和修改部署脚本︰ CreatePartitions-&lt;固件&gt;.txt 的新值。 若要了解有关可用空间的建议的详细信息，请参阅[基于 UEFI/GPT 的硬盘分区](http://go.microsoft.com/fwlink/?LinkId=526950)。 示例：

    ``` syntax
    rem == 3. Windows RE tools partition ===============
    create partition primary size=600
    ```

5.  提交更改并卸载 Windows 映像︰

    ``` syntax
    Dism /Unmount-Image /MountDir:"C:\mount\windows" /Commit
    ```

    其中*C*是驱动器的包含图像的驱动器号。

    此过程可能需要几分钟。

**步骤 13︰ 将映像和部署脚本复制到 USB 钥匙**

1.  插入 Windows PE usb 闪存盘，请注意驱动器位置，例如， **d:**。
2.  复制图像和预制的部署脚本到 USB 钥匙，例如︰

    ``` syntax
    copy C:\Images\WindowsWithOffice.wim D:

    copy C:\Samples\Scripts\* D:
    ```

    **请注意** 如果 Windows PE 键没有足够的空间，将复制的图像和脚本到另一个 usb 闪存盘。

    **请注意** 如果图像大于 4 GB，您可能需要 preformat 使用 NTFS 文件格式的 usb 闪存盘。

     
**第 14 步︰ 应用 Windows 映像使用脚本**

-   使用部署脚本应用到测试设备上的新捕获的图像。 这些脚本设置硬盘分区，Windows 映像中的文件添加到分区。

    **请注意** 在 Windows 10 我们已经更改的分区布局。 虽然我们仍然使用单独的恢复工具图像，Windows 将不再需要一个单独的完整系统恢复的图像使用点击式重置功能。 这样可以节省几 GB 的驱动器空间。 我们还使用一个小的 MSR 分区 （下从 128 MB 到 16 MB）。
    
    **请注意** [示例脚本](windows-deployment-sample-scripts-sxs.md)可用于不同的设备固件类型 （更新的基于 UEFI 的 BIOS 或旧的 BIOS）。 某些基于 UEFI 的设备包括旧旧的 BIOS 支持。 有关详细信息，请参阅[UEFI 固件](http://go.microsoft.com/fwlink/?LinkId=526945)。

    ![图像显示，来创建参考计算机的自定义操作，您需要一台新电脑，一个图像文件和部署脚本。](images/dep-win8-sxs-createdeploymentscript.jpg)

**第 15 步︰ 设置格式并设置上参考设备的硬盘分区**

1.  引导到 Windows PE 中使用 Windows PE usb 闪存盘的参考设备。
2.  使用 diskpart 中找到 usb 闪存盘驱动器的号︰

    ``` syntax
    diskpart
    DISKPART> list volume
    DISKPART> exit
    ```

    例如，驱动器可以用字母标明如下︰ C = 窗口;D = USB 闪存驱动器。

3.  主硬盘进行格式化、 分区，通过创建和应用图像使用预制的[示例脚本](windows-deployment-sample-scripts-sxs.md)。 脚本**ApplyImage.bat**依赖这些脚本放在同一个文件夹中︰

    -   **CreatePartitions UEFI.txt**
    -   **CreatePartitions BIOS.txt**
    -   **HideRecoveryPartitions UEFI.txt**
    -   **HideRecoveryPartitions-BIOS.txt:**

    您可以从[Microsoft 下载中心](http://go.microsoft.com/fwlink/p/?LinkId=800657)下载这些脚本。 

    ``` syntax
    D:
    D:ApplyImage.bat D:\WindowswithOffice.wim
    ```

    其中*D*是 USB 闪存驱动器的驱动器号。

    当提示您的脚本︰ 
    
    -  按 Y 键来格式化驱动器 
    -  按 Y 键选择紧凑 OS 中，或 N 以选择一个非压缩的操作系统︰
        -   **Y**︰ 应用使用精简的操作系统映像。 这是最适合固态驱动器和驱动器可用空间受限的设备。 以此为 1 和 2 的硬件配置。
        -   **N**︰ 将作为完全未压缩图像的图像。 这是最适合于高性能的设备或使用传统硬盘旋转介质的设备。 使用此硬件配置 3。
    -  按 N 指示图像不包括扩展的属性 (EA)。

    这些脚本将映像应用到驱动器，然后完成。

**第 16 步︰ 重新启动设备**

-   拔下 USB 闪存驱动器和外部 USB 硬盘驱动器和类型`exit`。

    正在等待要完成的准备阶段，回到您的技术人员计算机而继续的实验室。

    **警告**  **疑难解答**︰ 如果该设备无法启动，打开该设备，然后按键打开引导设备选择菜单 （如**Esc**键）。

     

 

 





