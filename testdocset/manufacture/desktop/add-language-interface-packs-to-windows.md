---
author: Justinha
Description: "添加到 Windows 的语言界面包"
ms.assetid: 6acfeb8f-ce94-46e0-b679-1f58958fdd3e
MSHAttr: PreferredLib:/library/windows/hardware
title: "添加到 Windows 的语言界面包"
ms.openlocfilehash: acdc3311f62d4cc2d6501e390da4a44b5de1b8bb
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add-language-interface-packs-to-windows"></a>添加到 Windows 的语言界面包


语言界面包 (Lip) 包括 Windows 用户界面文本的区域。 Lip 必须与有效的父语言一起使用。

只有在已安装了以下语言之一，例如，可以安装加泰罗尼亚语 (ca-ES) 唇︰ 美国英语 (EN-US)、 英国 (en GB)、 西班牙语 (es-ES) 或法语 (FR-FR)。

若要向脱机 Windows 映像中添加唇，您必须验证支持的父语言包首先安装到 Windows 映像。

嘴唇和其父语言的列表，请参阅[可用语言包的 Windows](available-language-packs-for-windows.md)。

唇的版本必须匹配的 Windows 的版本。 例如，不能对 Windows 8 的图像中或 Windows 8 唇向 Windows 10 映像添加 Windows 10 唇。

对于 Windows 10 语言包和 Lip 是还可以从 Windows Update 下载。 您可以使用**控制面板**添加其他语言。 此过程需要访问互联网并访问 Windows Update。 IT 专业人员和最终用户可以使用 Windows Update 将其他语言添加到 Windows 安装。

-   Oem 可以查看和下载从[Microsoft OEM 网站](http://go.microsoft.com/fwlink/?LinkId=131359)的嘴唇。
-   系统构建者可以查看和下载从[OEM 合作伙伴中心](http://go.microsoft.com/fwlink/?LinkId=131358)的嘴唇。
-   用户可以从 Windows Update 获取语言或嘴唇。 转到**设置** &gt; **时间和语言** &gt; **地区和语言** &gt; **添加一种语言**。 选择您想要使用从列表，然后选择您要使用哪个地区版本使用的语言。 您下载的内容将立即开始。

## <a name="span-idinstalllipsspanspan-idinstalllipsspanspan-idinstalllipsspaninstall-lips"></a><span id="Install_LIPs"></span><span id="install_lips"></span><span id="INSTALL_LIPS"></span>安装 Lip

**若要安装 LIP 使用审核模式 （用于制造电脑）**

1.  下载适当的唇 (如有必要，其基本的语言)，并将其保存到可移动媒体上。
2.  引导到审核模式的目标计算机。 例如在 OOBE 屏幕上，按下 Ctrl + Shift + F3。 若要了解详细信息，请参阅[启动到审核模式或 OOBE 的 Windows](boot-windows-to-audit-mode-or-oobe.md)。
3.  插入可移动媒体和唇 （和基本的语言，如有必要） 复制到目标计算机。
4.  如果尚未安装的基本语言，可将其安装︰ 导航到该.cab 文件并双击它。 请按照说明进行操作以完成安装。
5.  安装 LIP︰ 导航到该.cab 文件并双击它。 请按照说明进行操作以完成安装。
6.  退出审核模式并准备 PC 图像捕获或部署中，例如︰

    打开一个命令提示符并运行︰ 
    
    ``` syntax
    sysprep /oobe /generalize
    ``` 
    
    若要了解详细信息，请参阅[Sysprep （通用化） 的 Windows 安装](sysprep--generalize--a-windows-installation.md)。

**若要向脱机 Windows 映像中安装 LIP**

1.  下载适当的唇 (如有必要，其基本的语言)。
2.  使用提升的权限打开命令提示符。
3.  您想要安装到唇将 Windows 映像装载。

    ``` syntax
    md "C:\mount\windows"

    Dism /Mount-Image /ImageFile:C:\images\Win10\sources\install.wim /Index:1 /MountDir:"C:\mount\windows"
    ```

4.  如果基本 LP 未在图像中，请添加它。

    ``` syntax
    Dism /Image:C:\mount\windows /Add-Package /PackagePath:C:\Languages\x64\langpacks\Microsoft-Windows-Client-Language-Pack_x64_es-es.cab
    ```

5.  添加唇。

    ``` syntax
    Dism /Image:C:\mount\windows /Add-Package /PackagePath:C:\Languages\x64\langpacks\Microsoft-Windows-Client-Language-Interface-Pack_x64_ca-es.cab
    ```

6.  如果您正在创建的 Windows 安装媒体或使用分布共享时，重新创建 lang.ini 文件。

    ``` syntax
    Dism /Image:C:\mount\windows /Gen-LangIni 
           /Distribution:C:\images\Win10\sources
    ```

    Lang.ini 文件 c:\\图像\\Win10\\源看起来与以下内容类似︰

    ``` syntax
    [Available UI Languages]
    ca-ES = 2
    es-ES = 3
     
    [Fallback Languages]
    es-ES = en-us
    ```

7.  可选︰ 将默认语言、 区域设置，以及其他国际设置更改为本地语言。

    ``` syntax
    Dism /image:C:\mount\windows /set-allIntl:ca-es
    ```

    可选︰ 查看默认区域设置。

    ``` syntax
    Dism /image:C:\mount\windows /get-intl
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

8.  卸载映像，并提交所做的更改。

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\mount\windows /Commit
    ```

    Windows 映像已准备就绪可以部署。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[将语言包添加到 Windows](add-language-packs-to-windows.md)

[可用语言包的 Windows](available-language-packs-for-windows.md)

[语言包默认值](http://go.microsoft.com/fwlink/?LinkId=206622)

 

 






