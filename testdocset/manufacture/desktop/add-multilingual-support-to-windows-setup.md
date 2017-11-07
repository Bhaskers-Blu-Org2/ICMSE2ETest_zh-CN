---
author: Justinha
Description: "Windows 安装程序中添加多语言支持"
ms.assetid: 242b963c-79fc-450b-90d7-c736965797b7
MSHAttr: PreferredLib:/library/windows/hardware
title: "Windows 安装程序中添加多语言支持"
ms.openlocfilehash: f29a6619203d76892aa3f12add2f6fe3c9ca6de0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add-multilingual-support-to-windows-setup"></a>Windows 安装程序中添加多语言支持

多语言支持的 Windows 安装程序使您可以选择为 Windows 安装程序和 Windows 安装的不同语言。 这种情况下允许技术人员以运行 Windows 安装程序以一种语言，并将 Windows 安装到另一种语言。 

本演练提供了用于创建带有多语言支持的 Windows 安装媒体。 

## <a name="prerequisites"></a>先决条件


若要完成本演练，您需要以下各项︰

-   具有 Windows 评估和部署工具包 (Windows ADK) 安装的技术人员计算机

-   您创建的介质的所有语言的 Windows 安装媒体

-   ISO Windows 的语言包


## <a name="step-1-prepare-your-environment"></a>第 1 步。 准备您的环境 

若要开始，将 Windows 安装文件从介质复制到本地目录。 如果您正在使用的自定义映像创建供使用的媒体，您必须使用对应于您的自定义映像的版本 Windows media。 例如，如果您要构建一个自定义的 Windows 10 安装映像，必须使用原始的 Windows 10 产品介质。

-   在技术人员计算机上，创建一个新目录，Windows 分发您的软件包并将 Windows 媒体内容复制到该目录。 例如︰

    ``` syntax
    md C:\my_distribution
    xcopy /E D: C:\my_distribution
    md C:\mount\boot 
    md C:\mount\windows
    ```

    其中， *d︰*是 Windows 产品媒体的位置。

## <a name="step-2-customize-languages-available-for-windows-setup"></a>第 2 步。 自定义可供 Windows 安装程序语言
这一节演示如何自定义语言执行 Windows 安装时所提供的技术人员。

### <a name="add-windows-pe-setup-language-packs-to-the-default-boot-image"></a>将 Windows PE 安装语言包添加到默认启动映像

在此步骤中，对第二个映像 （索引 2） 默认 Boot.wim 中添加语言支持和 Windows 安装可选组件。

1.  在技术人员计算机上︰ 单击**开始**，并且类型**部署**。 用鼠标右键单击**部署和图像处理工具环境**，然后选择**以管理员身份运行**。

2.  第二个映像装载 （索引 2） Boot.wim 中使用**Dism /Mount-Image**的本地装入目录。 例如︰

    ``` syntax
    Dism /mount-image /imagefile:C:\my_distribution\sources\boot.wim /index:2 /mountdir:C:\Mount\boot
    ```

3.  将 Windows PE 安装可选组件和语言包添加到已装载的映像使用**Dism /Add-Package**为您想要支持的每种语言。 添加*lp.cab*， *WinPE-setup_\<语言 >.cab*，和*WinPE-设置-client_\<语言 >.cab*为每个要添加的语言。

    Windows PE 语言包有 Windows ADK。

    例如︰

    ``` syntax
    Dism /image:C:\mount\boot /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\lp.cab"

    Dism /image:C:\mount\boot /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-Setup_fr-fr.cab"

    Dism /image:C:\mount\boot /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-Setup-Client_fr-fr.cab"
    ```

    **重要**  
    针对 Windows 服务器 2016，您必须使用客户端安装 WinPE 可选组件 WinPE 设置服务器的可选组件。

     
4.  日语 (JA-JP)、 朝鲜 (KO-KR) 和中文 （zh 香港、 ZH-CN，ZH-TW），您必须向图像添加其他字体的支持。 例如，若要添加日语字体的支持︰

    ``` syntax
    Dism /image:C:\mount\boot /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-FontSupport-JA-JP.cab"
    ```


## <a name="step-3-customize-the-languages-available-in-windows"></a>第 3 步。 自定义 Windows 中可用的语言

### <a name="add-language-packs-to-the-windows-image"></a>将语言包添加到 Windows 映像

**您必须添加相同的语言支持 Windows 映像文件，到 install.wim，当您未 boot.wim 文件。** 安装过程中需要这两个图像包含一组相同的语言包。 有关详细信息，请参阅[添加和删除语言包脱机使用 DISM](add-and-remove-language-packs-offline-using-dism.md)。

1.   使用 DISM 将 Windows 映像安装

        ``` syntax
        Dism /mount-image /imagefile:C:\my_distribution\sources\install.wim /index:1 /mountdir:C:\mount\windows    
        ```
        其中*1*是您要装载的图像的索引。

2.   将一个或多个语言包添加到 Windows 映像。

        ``` syntax
        Dism /image:C:\mount\windows /add-package /packagepath:F:\x64\langpacks\Microsoft-Windows-Client-Language-Pack_x64_fr-fr.cab 
        ```

        其中*f︰*是 ISO 语言包的位置。

此外必须将相同的一组语言添加到 Windows 恢复环境图像 (winre.wim)。 有关详细信息，请参阅[自定义 Windows RE](customize-windows-re.md)。

## <a name="step-4-add-localized-windows-setup-resources-to-the-windows-distribution"></a>步骤 4︰ 添加到 Windows 分发本地化的 Windows 安装程序资源


在此步骤中复制的特定于语言的安装程序资源从每个语言特定 Windows 分发到源文件夹在 Windows 分发。 例如，为 FR-FR 插入 Windows DVD，DVD 驱动器 （e:） 中，将 FR-FR 源文件夹复制到 Windows 分发。

-   将本地化的 Windows 安装程序文件复制到 Windows 分发。

    ``` syntax
    xcopy E:\sources\fr-fr C:\my_distribution\sources\fr-fr /cherkyi 
    ```

    其中*e︰*是包含 Windows 安装程序的本地化的资源的 Windows 安装媒体的位置。

## <a name="step-5-recreate-the-langini"></a>步骤 5︰ 重新创建 Lang.ini

在此步骤中重新创建 Lang.ini 文件，并指定的默认语言设置。

1.  重新创建 Lang.ini 文件，以反映使用*Dism /Gen-LangINI*的其他语言。

    ``` syntax
    Dism /image:C:\mount\windows /gen-langINI /distribution:C:\my_distribution
    ```

2.  使用 DISM 将 Windows 安装程序默认语言更改。 例如︰

    ``` syntax
    Dism /image:C:\mount\windows /Set-SetupUILang:fr-FR /distribution:C:\my_distribution
    ```

    有关指定不同的区域设置输入法区域设置，以及其他项目的详细信息，请参阅[DISM 语言和国际服务命令行选项](dism-languages-and-international-servicing-command-line-options.md)。

3.  在 Windows 分发到 boot.wim 文件复制 lang.ini 文件。

    ``` syntax
    Xcopy C:\my_distribution\sources\lang.ini C:\mount\boot\sources\lang.ini
    ```

## <a name="step-6-commit-the-changes-to-the-windows-images"></a>步骤 6︰ 将更改提交到 Windows 映像


在此步骤中您将更改提交到的所有已更新的图像

-   使用 DISM 卸载，然后将更改提交到 Windows 和引导映像。

    ``` syntax
    Dism /unmount-image /mountdir:C:\mount\boot /commit 
    Dism /unmount-image /mountdir:C:\mount\windows /commit
    ```

## <a name="step-7-create-a-boot-order-file-optional"></a>第 7 步︰ 创建启动顺序文件 （可选）


在此步骤中，您将创建启动顺序文件。 由于图像的大小，您必须这样做才能创建.iso 文件。

-   创建一个引导顺序文件 (bootorder.txt)。 例如︰

    ``` syntax
    Oscdimg -m -n -yo C:\temp\bootOrder.txt -bC:\winpe_amd64\Efisys.bin C:\winpe_amd64\winpeamd64.iso
    ```

    其中 Bootorder.txt 包含以下文件的列表︰

    ``` syntax
    boot\bcd
    boot\boot.sdi
    boot\bootfix.bin
    boot\bootsect.exe
    boot\etfsboot.com
    boot\memtest.efi
    boot\memtest.exe
    boot\en-us\bootsect.exe.mui
    boot\fonts\chs_boot.ttf
    boot\fonts\cht_boot.ttf
    boot\fonts\jpn_boot.ttf
    boot\fonts\kor_boot.ttf
    boot\fonts\wgl4_boot.ttf
    sources\boot.wim
    ```

## <a name="next-steps"></a>下一步行动


您现在可以使用多语言映像创建分布的介质。 若要创建可引导介质，如 USB 闪存驱动器，请参阅[WinPE︰ 创建 USB 可启动驱动器](winpe-create-usb-bootable-drive.md)。 您还可以创建可引导 CD 或 DVD。 但是，由于多语言映像的大小，您必须首先创建启动顺序文件之前创建 CD 或 DVD 上的可启动映像 (.iso) 文件。 有关详细信息，请参阅[Oscdimg 命令行选项](oscdimg-command-line-options.md)。

## <a name="related-topics"></a>相关的主题


[Windows 安装程序技术参考](windows-setup-technical-reference.md)

[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)

[DISM Windows PE 服务命令行选项](dism-windows-pe-servicing-command-line-options.md)

[Oscdimg 命令行选项](oscdimg-command-line-options.md)

[WinPE︰ 安装和自定义](winpe-mount-and-customize.md)

[WinPE︰ 安装在硬盘上 （平面引导或非 RAM）](winpe-install-on-a-hard-drive--flat-boot-or-non-ram.md)

 

 






