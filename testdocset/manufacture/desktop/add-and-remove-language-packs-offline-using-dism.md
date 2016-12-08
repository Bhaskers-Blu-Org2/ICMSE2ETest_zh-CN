---
author: Justinha
Description: "添加和删除语言包使用 DISM 脱机"
ms.assetid: 128cffa3-8c53-41c8-add2-fa10197f36a3
MSHAttr: PreferredLib:/library/windows/hardware
title: "添加和删除语言包使用 DISM 脱机"
ms.openlocfilehash: 984bfc6c78d7e5d887ff95b720124392ff628cf6
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add-and-remove-language-packs-offline-using-dism"></a>添加和删除语言包使用 DISM 脱机


所有的 Windows® 安装包含至少一种语言包和构成核心操作系统的非特定于语言的二进制文件。 本主题包括有关如何使用部署映像服务和管理 (DISM.exe) 来添加或删除其他语言包并配置国际设置的信息。 可以使用相同的过程添加或删除语言界面包 (Lip)。 有关语言包和 LIP 之间的差异的详细信息，请参阅[将语言包添加到 Windows](add-language-packs-to-windows.md)。

最近已安装和已捕获的图像或默认零售映像必须是 Windows 映像。 这确保了 Windows 映像没有任何挂起的包操作。 Windows 映像可以在任何语言中。 例如，可以开始用英语 (EN-US) 图像并添加对日语 (JA-JP) 和朝鲜语 (KO-KR) 的支持。 此外，可以将嘴唇添加到 Windows 映像包含受支持的母语。 有关支持的语言包和 Lip 的详细信息，请参阅[语言包](language-packs-and-windows-deployment.md)。

本主题包括以下过程。

[添加语言包的 Windows 图像](#addlangpacktoimage)描述了如何将新语言包添加到脱机 Windows 映像。

[删除语言包的 Windows 映像](#removelangpackfromwin)介绍如何使用 DISM 脱机 Windows 映像中删除语言包。 您必须删除您不打算将新语言包添加到 Windows 映像之前，请使用的任何语言包。

[配置国际设置](#configintlsettings)介绍如何使用 DISM 可以更改默认的显示语言和 Windows 映像中配置其他国际设置。

有关如何将语言包添加到 Windows 预安装环境 (Windows PE) 映像的信息，请参阅添加语言包的 Windows PE 映像。

## <a name="span-idaddlangpacktoimagespanspan-idaddlangpacktoimagespanspan-idaddlangpacktoimagespanadd-a-language-pack-to-a-windows-image"></a><span id="AddLangPacktoImage"></span><span id="addlangpacktoimage"></span><span id="ADDLANGPACKTOIMAGE"></span>将语言包添加到 Windows 映像


语言包可用作.cab 文件和命名其区域设置;例如，Microsoft-Windows-Client-Language-Pack_x64_es-es.cab。 以.cab 文件形式提供的程序包可以添加到脱机 Windows 映像使用 DISM 命令行工具。 可以使用相同的过程添加语言包或语言界面包 (LIP)。

**重要**  
嘴唇会释放为.mlc 的文件中。 唇添加到脱机 Windows 映像使用 DISM 命令行工具时，您必须重命名唇文件从 LIP.mlc 到 LIP.cab。

 

仅在已安装的受支持的父语言 Windows 映像，才能安装 Lip。 例如，巴斯克语 （巴斯克） 唇可以仅在西班牙语 （西班牙） 或法语 （法国） 父语言包安装的 Windows 映像上安装。 为脱机 Windows 映像安装 LIP 之前，请验证已安装了受支持的母语。 有关支持的语言包和 Lip 的详细信息，请参阅[语言包](language-packs-and-windows-deployment.md)。

您可以向答案文件添加语言包和 Lip 并将答案文件应用于脱机 Windows 映像。 执行此操作时，您可以在同一操作中安装 LIP 和母语。

**重要**  
不要更新之后安装语言包。 如果您安装的更新 (修补程序后，常规分发版本\[GDR\]，或服务包\[SP\]) 之前安装的语言包更新中包含的特定于语言的更改不会应用，您将需要重新安装此更新包含依赖于语言的资源。 一定要安装该更新之前安装语言包。

 

**若要添加语言包使用 DISM**

1.  在将新语言包添加到 Windows 映像之前，必须从您不打算使用的 Windows 映像中删除所有语言包。 有关详细信息，请参阅[删除语言包的 Windows 映像](#removelangpackfromwin)。

2.  单击**开始**，然后键入**部署**。 用鼠标右键单击**部署和图像处理工具环境**，然后选择**以管理员身份运行**。

3.  如果上面的过程中已装载映像，则可以键入以下命令列出当前已装载的映像和有关已装载映像装入的映像的索引装载位置等信息。

    ``` syntax
    Dism /Get-MountedImageInfo
    ```

    如果未装入映像，则键入以下命令以检索名称或要修改的映像的索引号。

    ``` syntax
    Dism /Get-ImageInfo /ImageFile:C:\test\images\install.wim
    ```

    索引或名称值时需要指定图像文件的大多数操作。 键入以下命令以装载映像。

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\install.wim /Name:"Windows 7 HomeBasic" /MountDir:C:\test\offline
    ```

4.  键入以下命令以便将语言包添加到已装载的脱机映像。 您可以在一个命令行添加多个程序包。

    ``` syntax
    Dism /Image:C:\test\offline /ScratchDir:C:\Scratch /Add-Package /PackagePath:C:\packages\package1.cab /PackagePath:C:\packages\package2.cab ...
    ```

    **请注意**  
    暂存目录添加语言包必须至少为 1 GB。

5.  键入下列命令以提交更改。 使用**卸载**选项一直装入图像。

    ``` syntax
    Dism /Commit-Image /MountDir:C:\test\offline
    ```

6.  语言包添加到 Windows 映像。 下一步是[配置国际设置](#configintlsettings)。

**若要添加语言包使用 DISM 和答案文件**

1.  注意您想要向 Windows 映像中添加语言包的位置。 语言包存储在.cab 文件中。

2.  使用 Windows SIM 创建答案文件，其中包含您想要添加的语言包。 有关如何创建应答文件的详细信息，请参阅[创建或打开答案文件](https://msdn.microsoft.com/library/windows/hardware/dn915085)。

3.  在**包**节点下**的语言包**，用鼠标右键单击要添加的语言包，然后选择**添加到答案文件**。

4.  在**属性**窗格中，在**设置**中选择**安装****操作**设置为值。

5.  您还可以在答案文件中配置国际设置。 有关详细信息，请参阅[Windows 中配置国际设置](configure-international-settings-in-windows.md)。

6.  验证并保存答案文件。

7.  关闭 Windows sim 卡。

    **重要**  
    请确保该语言包被复制到在答案文件中指定的位置。

     

8.  如果没有已装入映像，使用 DISM 装载 Windows 映像。 例如，

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\install.wim /Index:1 /MountDir:C:\test\offline
    ```

9.  使用 DISM 应用无人参与的安装应答文件为安装的 Windows 映像。 例如，

    ``` syntax
    DISM /Image:C:\test\offline /Apply-Unattend:C:\test\answerfiles\myunattend.xml
    ```

    有关如何通过使用 DISM 应用无人参与的答案文件的详细信息，请参阅[无人参与服务 DISM 命令行选项](dism-unattended-servicing-command-line-options.md)。

10. 语言包添加到 Windows 映像，并配置国际设置。

## <a name="span-idremovelangpackfromwinspanspan-idremovelangpackfromwinspanspan-idremovelangpackfromwinspanremove-a-language-pack-from-a-windows-image"></a><span id="RemoveLangPackfromWin"></span><span id="removelangpackfromwin"></span><span id="REMOVELANGPACKFROMWIN"></span>从 Windows 映像中删除语言包


在将新语言包添加到 Windows 映像之前，必须删除您不想使用的任何语言包。 有两种方法删除语言包脱机使用 DISM。 您可以将无人参与的答案文件应用到脱机映像，也可以删除语言包直接从脱机映像，使用命令提示符。

**重要**  
如果有挂起的联机操作，不能从脱机 Windows 映像中删除语言包。 Windows 映像应最近已安装和已捕获的图像。 这将保证，Windows 映像不包括任何挂起的联机操作需要重新启动。

 

**若要删除语言包使用 DISM**

1.  查找 Windows 映像 (.wim) 文件或虚拟硬盘 （.vhd 或.vhdx），其中包含要从中删除语言的 Windows 映像。

2.  单击**开始**，然后键入**部署**。 用鼠标右键单击**部署和图像处理工具环境**，然后选择**以管理员身份运行**。

3.  在命令提示符下，键入以下命令以检索名称或要修改的映像的索引号。

    ``` syntax
    Dism /Get-ImageInfo /ImageFile:C:\test\images\install.wim 
    ```

    索引或名称值时需要指定图像文件的大多数操作。

4.  键入以下命令以装载脱机 Windows 映像。

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\install.wim /Name:"Windows 7 HomeBasic" /MountDir:C:\test\offline
    ```

5.  可选︰ 键入以下命令以列出脱机映像中的语言。

    ``` syntax
    Dism /Image:C:\test\offline /Get-Intl
    ```

6.  键入以下命令以从映像中删除语言包。 您可以通过一个命令行语句删除多个.cab 文件。

    ``` syntax
    Dism /Image:C:\test\offline /Remove-Package /PackagePath:C:\packages\package1.cab /PackagePath:C:\packages\package2.cab ...
    ```

7.  键入下列命令以提交更改。 使用**卸载**选项一直装入图像。

    ``` syntax
    Dism /Commit-Image /MountDir:C:\test\offline
    ```

8.  从映像中删除语言包。 下一步是将语言包添加到已装载的脱机映像。 若要继续，请参阅[添加语言包的 Windows 映像](#addlangpacktoimage)。

**若要删除语言包使用 DISM 和无人参与的答案文件**

1.  使用 Windows® 系统映像管理器 (Windows SIM) 来创建一个应答文件，其中包含要从中删除语言包。 使用 Windows SIM 打开 Windows 映像并创建新的应答文件。 有关如何使用 Windows sim 卡的详细信息，请参阅[创建或打开答案文件](https://msdn.microsoft.com/library/windows/hardware/dn915085)。

2.  在**包**节点下**的语言包**，右键单击您想要删除，并选择**添加到答案文件**的语言包。

3.  在**属性**窗格中，在**设置**中选择**删除****操作**设置为值。

4.  保存答案文件并关闭 Windows sim 卡。 答案文件必须类似于以下示例。

    ``` syntax
    <package action="remove">
       <assemblyIdentity name="Microsoft-Windows-LanguagePack-Package" version="6.0.5714.0" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="en-US" />
    </package>
    ```

5.  使用 DISM 将 Windows 映像安装。 例如，

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\install.wim /Index:1 /MountDir:C:\test\offline
    ```

6.  使用 DISM 将无人参与的答案文件应用到安装的 Windows 映像。 例如，

    ``` syntax
    Dism /Image:C:\test\offline /Apply-Unattend:C:\test\answerfiles\myunattend.xml
    ```

    有关如何使用 DISM 应用无人参与的答案文件的详细信息，请参阅[无人参与服务 DISM 命令行选项](dism-unattended-servicing-command-line-options.md)。

7.  键入下列命令以提交更改。 使用**卸载**选项一直装入图像。

    ``` syntax
    Dism /Commit-Image /MountDir:C:\test\offline
    ```

8.  从映像中删除语言包。 下一步是将语言包添加到已装载的脱机映像。 若要继续，请参阅[添加语言包的 Windows 映像](#addlangpacktoimage)。

## <a name="span-idconfigintlsettingsspanspan-idconfigintlsettingsspanspan-idconfigintlsettingsspanconfigure-international-settings"></a><span id="ConfigIntlSettings"></span><span id="configintlsettings"></span><span id="CONFIGINTLSETTINGS"></span>配置国际设置


添加或在 Windows 映像中删除语言包之后，您可以设置默认用户界面 (UI) 语言，即所谓的显示语言。 同时，可以使用 DISM Windows 映像中配置国际设置。

您还可以在答案文件中配置国际设置。 有关如何执行此操作的详细信息，请参阅[在 Windows 中配置国际设置](configure-international-settings-in-windows.md)。

**请注意**  
如果您使用 DISM 工具指定的默认用户界面语言和区域设置，然后在答案文件中指定不同的语言和区域设置的答案文件中的设置覆盖 DISM 工具指定的默认值。

 

**若要配置使用 DISM 国际设置**

1.  如果未安装，您必须先装配图像。 例如，

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\install.wim /Index:1 /MountDir:C:\test\offline
    ```

2.  若要更改所有国际语言已装载的脱机映像中的设置，以匹配 Microsoft 为给定语言，DISM 命令提示符下，设置的默认值，请键入以下命令，

    ``` syntax
    Dism /Image:C:\test\offline /Set-SKUIntlDefaults:en-us
    ```

    **请注意**  
    **/Set-SKUIntlDefaults**选项不会更改日语和朝鲜语键盘的键盘驱动程序。 您必须使用**/Set-LayeredDriver**选项更改此设置。 有关详细信息，请参阅[DISM 语言和国际服务命令行选项](dism-languages-and-international-servicing-command-line-options.md)。

     

    有关默认值的详细信息，请参阅[Windows 语言包默认值](windows-language-pack-default-values.md)。

    或者，您可以配置不同的设置，包括用户界面语言、 系统的区域设置、 用户区域设置、 输入法区域设置，和其他人不同的值。 有关如何指定各个值的每个设置的详细信息，请参阅[DISM 语言和国际服务命令行选项](dism-languages-and-international-servicing-command-line-options.md)。

3.  在命令提示符处，键入下列命令以提交更改并卸载映像。

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\test\offline /Commit
    ```

Windows 映像已准备就绪可以部署。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[将语言包添加到 Windows](add-language-packs-to-windows.md)

[使用 DISM Windows 映像提供服务](service-a-windows-image-using-dism.md)

[DISM 的部署 windows 映像服务和管理技术参考](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md)

[DISM 语言和国际服务命令行选项](dism-languages-and-international-servicing-command-line-options.md)

[DISM 无人参与服务命令行选项](dism-unattended-servicing-command-line-options.md)

[Windows 系统映像管理器技术参考](https://msdn.microsoft.com/library/windows/hardware/dn922445)

 

 






