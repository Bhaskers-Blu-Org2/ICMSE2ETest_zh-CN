---
author: KPacquer
Description: "实验室 1︰ 自定义和安装 Windows 使用 Windows 图像处理和配置设计器 (ICD)"
ms.assetid: 97f2cc2b-ae4b-4117-a73b-42e508fe7a03
MSHAttr: PreferredLib:/library/windows/hardware
title: "实验室 1︰ 自定义和安装 Windows 使用 Windows 图像处理和配置设计器 (ICD)"
ms.openlocfilehash: 9e846ee5fb866fb7d589fd7bcbe0fa9795f36ac0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="lab-1-customize-and-install-windows-using-the-windows-imaging-and-configuration-designer-icd"></a>实验室 1︰ 自定义和安装 Windows 使用 Windows 图像处理和配置设计器 (ICD)


部署自定义的 Windows 设备的最快方法是通过创建可引导 USB 密钥使用 Windows 图像处理和配置设计器 (ICD)。 此工具可帮助您安装设备驱动程序、 系统设置，并添加语言，以便可以快速将 Windows 安装到测试或零售设备。

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
| 2013 年办公室                  | 否           | 是                 | 是                               |
| 精简的操作系统                   | 是          | 是                 | 否                                |

 
# # <span id="loadImage"> </span> <span id="loadimage"> </span><span id="LOADIMAGE"></span>第 1 步︰ 在 Windows ICD 中创建新项目


1.  单击**开始**，键入**icd**，，然后单击**Windows 图像处理和配置设计**。

    如果出现**用户帐户控制**窗口，请单击**是**。

2.  单击**新的 Windows 映像自定义项**。
3.  在**输入项目详细信息**页面上，使用下面的信息，然后单击**下一步**:
    -   在**名称**框中，键入**Fabrikam\_笔记本\_1**。
    -   将**项目文件夹**框中为的是。
    -   在**说明**框中，键入**Fabrikam 笔记本 PC 系列 1 的基本硬件设计**。

4.  在**选择图像源格式**页中，单击**Windows 图像基于 Windows 映像文件 (WIM)** &gt; **下一步**。
5.  在**选择图像**页中，单击**浏览**。
    -   浏览到**c:\\图像\\Win10\_x64\\源**，单击**install.wim**，然后单击**打开**。
    -   如果使用设计 1，选择主 Windows 10。 如果使用设计 1b，选择 Windows 10 专业。
    -   单击**下一步**。

6.  在**导入的资源调配包 （可选）**页上，如果有供应包 （类似于您在实验室 1b 中创建的一个），可以立即将添加并再单击**完成**。 否则为可以保留此步骤为空，并单击**完成**。

创建项目并显示主编辑窗口。

**进行故障排除︰**如果您在创建项目时出现错误，请确保为 Oem 和系统构建者从专用的下载中心上获得 Windows 映像。 可以使用媒体创建工具下载[Windows 10 安装介质](http://go.microsoft.com/fwlink/p/?LinkId=626022)不能使用与 Windows 图像处理工具。

## <a name="span-idstep2addtheuniversalwindowsappsandwindows81appsoptionalspanspan-idstep2addtheuniversalwindowsappsandwindows81appsoptionalspanstep-2-add-the-universal-windows-apps-and-windows-81-apps-optional"></a><span id="step_2__add_the_universal_windows_apps_and_windows_8.1_apps__optional_"></span><span id="STEP_2__ADD_THE_UNIVERSAL_WINDOWS_APPS_AND_WINDOWS_8.1_APPS__OPTIONAL_"></span>步骤 2︰ 添加通用的 Windows 应用程序和 Windows 8.1 应用程序 （可选）


因此，客户第一次启动电脑时，PC 上的可用，可以预先通用的 Windows 应用程序加载到您的映像。 与 Windows ICD 您添加 Windows 8.1 应用程序相同的方式将 Windows 通用应用程序添加到映像。

1 的硬件配置，您可以跳过这步不想将任何应用程序添加到您的磁盘空间不足的占地面积设备。

在本演练中，我们将添加 Office 预览应用程序 （Word、 Excel 和 powerpoint 中有效）。 您可以为任何通用的 Windows 应用程序和 Windows 8.1 应用程序想要向图像中添加重复这些步骤。

1.  在 Windows ICD，**可用的自定义项**下, 展开**部署资产**，，然后单击**应用程序**。
2.  在**程序包路径**框中，单击**浏览**。 将视图更改为**应用程序捆绑包 (\*.appxbundle)**，选择 Word 预览应用程序捆绑包，然后单击**打开。**
3.  在**名称**框中，键入**单词预览**。
4.  在**许可证路径**框中，单击**浏览**。 选择 Word 预览许可文件，，然后单击**打开**。
5.  单击**添加**。 应用程序的名称应显示在**所选自定义项**窗格中。

对 Excel 预览和 PowerPoint 预览应用程序捆绑包和其他通用的 Windows 应用程序和您想要添加到映像的 Windows 8.1 应用程序重复步骤 1 到 5。 OneNote 和读者 8.1 应用程序包含在事件提供 USB。

## <a name="span-idadddriverspanspan-idadddriverspanspan-idadddriverspanstep-3-add-a-driver-to-the-image"></a><span id="addDriver"></span><span id="adddriver"></span><span id="ADDDRIVER"></span>步骤 3︰ 将驱动程序添加到映像


可以使用 Windows ICD 要向图像中添加您自己的基于 INF 驱动程序。

1.  在 Windows ICD，**可用的自定义项**下, 展开**部署资产**，，然后单击**驱动程序**。
2.  **驱动程序的文件夹路径**，旁边的中间窗格中，单击**浏览**。 浏览到基于 INF 驱动程序，然后再单击确定。

    驱动程序.inf 文件应显示在**驱动程序**中。 如果该文件夹中有多个驱动程序，将添加所有的驱动程序在该文件夹中。

    **请注意** 某些驱动程序被打包为.zip 或.exe 文件。 您需要解压缩或解压缩这些文件，然后再添加它们。 一些驱动程序文件，如示例驱动程序，包括文件对于 x86 和 x64 的设备，这是确定。

     

3.  在**名称**框中，键入*Fabrikam 视频卡 100*。

    如果您要从您的硬件制造商测试新设备设计与原型或预发行版驱动程序，请选择**强制安装未签名**复选框，然后单击**添加**。 驱动程序的描述性名称应显示在**所选自定义项**窗格中。

## <a name="span-idaddsettingsspanspan-idaddsettingsspanspan-idaddsettingsspanstep-4-add-some-customized-settings-to-the-image"></a><span id="addSettings"></span><span id="addsettings"></span><span id="ADDSETTINGS"></span>第 4 步︰ 向映像中添加一些自定义的设置


1.  在 Windows ICD，在**可用的自定义**窗格中，展开**图像的时间设置**，然后单击**OEM**。
2.  在中间窗格中，在*名称*框中，键入**Fabrikam**。
3.  在**可用的自定义**窗格中的下**OEM**，单击**信息。**

    填写以下信息︰

    -   在**制造商**框中，键入**Fabrikam**。
    -   在**SupportHours**框中，键入**上午 8 点到下午 5 点**。
    -   在**SupportPhone**框中，键入**555-1212年**。
    -   在**SupportURL**框中，键入**http://support.fabrikam.com**。

设置出现在**所选自定义项**窗格中。

## <a name="span-idstep5customizethestartlayoutspanspan-idstep5customizethestartlayoutspanspan-idstep5customizethestartlayoutspanstep-5-customize-the-start-layout"></a><span id="Step_5__Customize_the_Start_layout"></span><span id="step_5__customize_the_start_layout"></span><span id="STEP_5__CUSTOMIZE_THE_START_LAYOUT"></span>第 5 步︰ 自定义开始布局


在 Windows 10 Oem 可以修改默认的开始布局并通过创建**LayoutModification.xml**文件，并将该文件放在正确的系统位置指定 OEM 图块的布局。

1.  创建一个 layoutmodification.xml 文件。 为此实验室中，可以在 USB 的使用示例。 该示例将收回办公室、 OneNote 并开始为读者 8.1 只有经过预加载设备 (步骤 2) 上。 若要通过使用 XML 编辑器创建您自己的 layoutmodification.xml 文件，请参阅[示例脚本](windows-deployment-sample-scripts-sxs.md)。
2.  在 Windows ICD，在**可用的自定义**窗格中，展开**运行库设置**，单击**开始**，然后单击**StartLayout**。
3.  在中间窗格中，单击**浏览。**
4.  导航到保存的 LayoutModification.xml 文件的位置。
5.  选择该文件，并单击**打开**。 这应该设置 StartLayout 的值。

    设置出现在所选自定义项窗格中。

    **请注意** 您不能直接在 Windows ICD 添加.url 和.lnk 文件。 如果您拥有这些文件，按照步骤 2 中实验室 2 节中"添加修改开始布局所需的文件"。

     

## <a name="span-idaddlangspanspan-idaddlangspanspan-idaddlangspanstep-6-add-a-language"></a><span id="addLang"></span><span id="addlang"></span><span id="ADDLANG"></span>第 6 步︰ 添加语言


Windows ICD 提供添加语言的一个基本方法。

1.  在 Windows ICD，在**可用的自定义**窗格中，展开**部署资产**，，然后单击**语言包**。
2.  **Cab 文件**，旁边的中间窗格中，单击**浏览**。 浏览到语言包文件，例如︰ **c:\\样本\\语言\\fr fr x64 的客户端**， **lp.cab**，请单击，然后单击**打开。**
3.  在**名称**框中，键入**法语的用户界面**，，然后单击**添加**。

    语言包应显示在**所选自定义项**窗格中。

此方法也不会更新为 Windows 应用程序的语言资源。 包括 Windows 的收件箱的应用程序。 通过 Windows 更新，将自动更新一些 Windows 应用程序，而其他人可能需要以后重新安装。

若要更新资源，为 Windows RE 和应用程序，修改 Windows install.wim 映像，使用中的说明进行操作[实验室 2︰ 经典样式部署](part-2--classic-style-deployment.md)。 您可以跳过步骤 4 和 5 （添加 windows 驱动程序并修改开始布局），并且可以跳过可选步骤 11 和 12 （升级的 Windows 版本和设置为启动到审核模式的图像）。

## <a name="span-idaddlangcompspanspan-idaddlangcompspanspan-idaddlangcompspanstep-7-add-features-on-demand"></a><span id="addLangComp"></span><span id="addlangcomp"></span><span id="ADDLANGCOMP"></span>第 7 步︰ 根据需要添加功能


按需 (FODs) 的功能是可以在任何时候添加的 Windows 功能包。 当用户需要一种新功能时，它们可以从 Windows Update 请求功能包。 Oem 可以预安装这些功能以启用这些开箱即用的设备上。

常见功能包括像手写识别的语言资源。 这些功能是启用完整的 Cortana 功能所需要的。 下表显示用于 Windows 和哪些适用于 Cortana 语言中可用的组件的类型。

此外，若要启用 Cortana 或笔支持，需要按特定的顺序添加功能。 例如，若要启用 Cortana，安装这些功能顺序如下︰ **lp.cab**，**基本**， **TextToSpeech**，再**语音**。 要启用笔支持，按此顺序安装这些功能︰ **lp.cab**，然后**基本**，然后**手写**。

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

 

1.  在 Windows ICD，在**可用的自定义**窗格中，展开**部署资产**，，然后单击**即需即装功能**。
2.  在中间窗格中，旁边**的功能包的路径**，单击**浏览**。 浏览到 FOD 文件，例如︰ **c:\\样本\\语言\\fr fr x64 的客户端**， **Microsoft-Windows-LanguageFeatures-Basic-fr-fr-Package.cab**，请单击，然后单击**打开。**
3.  在**名称**框中，键入**法语基本组件**，，然后单击**添加**。

    语言部分应显示在**已配置的自定义**窗格中。

4.  **Cab 文件**，旁边的中间窗格中，单击**浏览**。 浏览到 FOD 文件，例如︰ **c:\\样本\\语言\\fr fr x64 的客户端**， **Microsoft-Windows-LanguageFeatures-Speech-fr-fr-Package.cab**，请单击，然后单击**打开。**
5.  在**名称**框中，键入**法语语音语言组件**，，然后单击**添加**。

    语言组件应显示在**所选自定义项**窗格中。

6.  重复步骤以添加**文本到语音转换**和**语音**组件。 语言组件应显示在**所选自定义项**窗格中。
7.  对于要求字体，例如中文 （简体） 语言添加字体包。 若要了解哪些语言需要字体的信息，请参阅[第 2 版的功能上的需求 （功能）](features-on-demand-v2--capabilities.md)。

    **Cab 文件**，旁边的中间窗格中，单击**浏览**。 浏览到 FOD 文件，例如︰ **c:\\样本\\语言\\zh cn x64 的客户端**，单击**Microsoft-Windows-LanguageFeatures-Fonts-Hans-Package.cab**，然后单击**打开**。

    在**名称**框中，键入**中文 （简体） 字体语言组件**，，然后单击**添加**。

    语言组件应显示在**已配置的自定义**窗格中。

**请注意**  
-   无法更新 Windows ICD 从 Windows 恢复环境中的语言。 默认情况下，如果没有问题，该设备将显示恢复屏幕英文只。
-   您运行 Dism.exe （或脚本） 之后添加另一种语言去英语。 有关示例，请参见[实验室 2︰ 经典样式部署](part-2--classic-style-deployment.md)，第 7 步。
-   添加一种语言之后, 您需要重新添加 (APPX) 的通用应用程序。 此过程需要在审核模式期间执行。 有关如何删除并重新添加这些应用程序的详细信息，请参阅[实验室 2︰ 经典样式部署](part-2--classic-style-deployment.md)，第 8 步。 在 Windows 10 版本中**于 2015 年 8 月 18 日**之后，现在可以添加新通用应用程序 (APPX) 在现有的顶部。 不再需要删除以前的版本，然后再重新添加它们。

 

## <a name="span-idbuildusbkeyspanspan-idbuildusbkeyspanspan-idbuildusbkeyspanstep-8-save-the-image"></a><span id="buildUSBKey"></span><span id="buildusbkey"></span><span id="BUILDUSBKEY"></span>步骤 8︰ 将图像保存为


Windows ICD 可以将整个图像存储到一个。FFU 文件。 通过使用基于扇区的映像和安全标头以进行[更快、 更安全的部署](wim-vs-ffu-image-file-formats.md)开发 FFU 格式。

1.  单击**创建** &gt; **生产介质**。
2.  选择**FFU** &gt; **下一步**。
3.  对于硬件设计 1 和 1b，选择**是****启用压缩的操作系统**中，在，然后单击**下一步**。
4.  在**配置审核模式下启动**，默认情况下，应将所有选项，然后单击**下一步**。
5.  在**FFU 文件的保存位置的选择**，为文件提供一个名称，例如 c:\\图像\\MyFFUImage.ffu，然后单击**下一步**。
    **请注意** 我们建议选择某一位置上的硬盘，而不是 USB 密钥，因为它可使 FFU 创建过程更快。

     

6.  检查设置，并确保它们是正确的。 单击**生成**。 Windows ICD 创建 FFU 文件使用的名称和路径上一步中所示。 这将需要几分钟。 单击**完成**。

    **故障排除︰ 如果该项目的生成会失败︰**

    1.  检查以确保没有项目名称中的任何前导或尾随空格。 如果没有，请重新创建该项目。
    2.  **由于文件的大小限制，无法完成请求的操作**︰ 查看该驱动器使用 NTFS 文件格式的格式化，并带有至少 5 gb 可用空间。
    3.  如果在任何时候结束向上重复本演练中，如果您想要使用相同的项目，删除现有项目文件夹从**文档\\Windows 图像处理和配置设计器 (WICD)**之前重新启动。

7.  FFU 文件复制到可移动存储设备，如单独的 usb 闪存盘或外部 USB 驱动器。 您可能需要重新格式化，以便它可以接受非常大的文件-这取决于多少语言、 驱动程序和应用程序添加，使用 NTFS 格式的驱动器。FFU 文件很容易就能 5 GB 或更大。 您可能无法使用 Windows PE 键-它使用 FAT32 格式化的它只接受 4 GB 的文件或更小。

## <a name="span-idbootreferencepcspanspan-idbootreferencepcspanspan-idbootreferencepcspanstep-9-install-windows-on-the-reference-device"></a><span id="bootReferencePC"></span><span id="bootreferencepc"></span><span id="BOOTREFERENCEPC"></span>步骤 9︰ 安装 Windows 参考设备上


1.  插入引用设备**WinPE** USB 驱动器。
2.  引导设备选择菜单引用设备启动。 您通常执行此操作打开设备电源并快速按特定的键或按钮 （例如， **Esc**键或**音量**按钮），选择 usb 闪存盘。
3.  插入引用设备**FFU** USB 驱动器。 确定哪个驱动程序号指派给该驱动器上，通过执行以下操作︰

    1.  WinPE 命令提示符下，键入︰ **diskpart** ，然后按 enter 键。
    2.  在 diskpart 提示符下，键入**列表的卷**，然后按 Enter。

    这将列出所有系统里的卷。 确定驱动程序字母相对应的 FFU USB 密钥，例如，g。

4.  WinPE 命令提示符下，键入以下命令︰

    ``` syntax
    Dism.exe /apply-image /imagefile=G:\MyFFUImage.ffu /applydrive=\\.\physicaldrive0 /skipplatformcheck /logpath:G:\dism.applyffu.log
    ```

    其中 g:\\MyFFUImage.ffu 是 FFU 文件的文件位置。

**重复第 9 步︰ 使用新的 Windows 安装密钥设置更多的设备**。 在**获得快速转向**屏幕上，关闭设备，按下电源按钮。 不要为您的客户完成 OOBE。

没有一个已知的错误，如果您的电脑设置为自动启动到 usb 闪存盘，它将陷于循环在安装过程中︰ Windows 安装后，它将重新安装一次又一次。 若要避免此循环︰

**解决方法︰ 准备好参考设备**

1.  在引用您设备上，打开该设备的启动菜单。 您通常执行此操作打开设备电源并快速按特定的键或按钮 （例如， **Esc**键或**调高音量**按钮）。
2.  找到启动顺序菜单 （此菜单具有不同的名称和位置） 并确保**硬盘**设置在启动过程中，不在 USB 驱动器中的第一个。
3.  如果您的设备看上去没有一种方法在启动过程中更改引导顺序，则该选项可能被禁用。 查找类似"启用启动选项上启动"或"F12 引导菜单"选项，启用菜单。

## <a name="span-idtroubleshootingspanspan-idtroubleshootingspanspan-idtroubleshootingspantroubleshooting"></a><span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>故障排除


如果 Windows 没有引用在设备上安装的请尝试每个步骤︰

-   **在引导菜单中没有 USB 密钥**︰ 尝试使用不同的 USB 端口的计算机上。 避免使用 USB 集线器或电缆。

    重新启动计算机，然后打开设备的引导菜单。 查找的选项，以便在启动时引导设备选择菜单 (示例:"F12 引导菜单")。 如果找到一个，则启用它 ！

-   **（uefi） 或 BIOS**︰ 引导菜单提供了引导 UEFI 模式或 BIOS 模式之间进行选择，如果选择 （uefi） 模式。
-   如果设备启动到**驱动器选择**菜单中，选择主硬驱，这通常是驱动器**C** 。 如果您不确定哪个驱动器时，按**Shift F10**打开命令提示窗口。 键入**diskpart** ，然后按 enter 键。 在 Diskpart 提示符下，键入要显示分区的**卷列表**。 键入**exit**。 按**Alt-tab**再试一次。
-   如果该设备获取通过安装的 6%，再失败，可能需要准备驱动器︰

    1.  插入 usb 闪存盘。
    2.  选择**解决&gt;高级选项&gt;命令提示符**。
    3.  键入**diskpart** ，然后按 enter 键。 在 Diskpart 提示符下，键入要列出的驱动器的**卷列表**。 键入**退出**退出 Diskpart 提示。
    4.  类型**diskpart /s d:\\样本\\CreatePartitions UEFI.txt**

        其中 D 是 usb 闪存盘的驱动器号。

        对于基于 BIOS 的电脑，而是使用 CreatePartitions BIOS.txt。

    5.  键入**退出**以退出命令提示符。
    6.  选择**关闭 PC**。
    7.  打开该设备，然后打开选择引导设备。 如果您启动 BIOS 或 UEFI 模式之间进行选择，选择 UEFI 模式。 Windows ICD 都应正确安装。

-   如果该设备启动时达**中选择一个选项︰ 解决或关闭您的 PC**菜单，您可能会看到一个已知的错误，USB 3.0 和 Windows ICD 的图像。 请尝试再次使用**USB 2.0**键或端口。
-   确保您的设备和匹配的 Windows 映像。 如果它们不匹配，请尝试创建图像重新使用正确的体系结构。

## <a name="span-idverifyspanspan-idverifyspantest-the-customizations"></a><span id="verify"></span><span id="VERIFY"></span>测试自定义结果


执行以下步骤来测试图像。 注意，这要求完成首次用户体验，并创建一个用户帐户。 后执行这些步骤，您通常需要将其发送给客户之前重新 Windows 安装到设备上。

1.  请确保该设备没有插入到网络中，并将其打开。
2.  设备启动时，如果**语言**屏幕将出现并显示法语后，然后已正确添加语言包。 选择你最熟悉的语言、 选择键盘，然后单击**下一步**。
3.  完成全新体验 (OOBE): 这些步骤可能会有所不同取决于语言。
4.  在**那里的你好**屏幕上，单击**接受**。
5.  如果它要求您输入产品密钥，请单击**以后这样做**。 如果插入的网络连接的过程中，您可能需要提供产品密钥。 若要避免使用的产品密钥，请断开设备的连接，然后重试。
6.  单击**接受**，**跳过此步骤**，请单击，然后单击**使用快速设置**。
7.  在**谁拥有这台电脑？**页上，单击**我**，然后再单击**下一步**。
8.  在**您进行**页上，单击**跳过此步骤**。
9.  添加用户名 (示例:"Terry")，然后单击**下一步**。
10. 该设备完成安装并重新启动到桌面。
11. 桌面上出现时，在**设置**下**系统&gt;有关**，您应该会看到技术显示先前输入的支持信息 （公司名称、 客服电话号码和支持网站）。

 

 





