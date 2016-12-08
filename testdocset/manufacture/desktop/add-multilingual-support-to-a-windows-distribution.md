---
author: Justinha
Description: "向 Windows 分发添加多语言支持"
ms.assetid: 2da53fc7-4c4d-4cea-9a98-0db4eacd33d2
MSHAttr: PreferredLib:/library/windows/hardware
title: "向 Windows 分发添加多语言支持"
ms.openlocfilehash: 891b373bfe0f974f7f751ff35a44725467befb94
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add-multilingual-support-to-a-windows-distribution"></a>向 Windows 分发添加多语言支持


可以使用 Windows® 安装来部署 Windows 多语言版本。 这是在由用户必须能够显示之间切换语言在一台计算机上的多种语言的多语言环境中部署 Windows 的公司的典型情况。 此过程需要执行下列步骤︰

-   复制一个或多个语言包链接到**\\Langpacks**在*Windows 分发*目录。 Windows 分发是 Windows 零售 DVD 的内容。

-   更新 Lang.ini 文件。

-   使用安装程序来安装分发共享中的语言包。

**重要**  
添加语言包链接到**\\Langpacks**目录可以扩展 Windows 安装程序的安装时间。 在包**\\Langpacks**目录添加到 Windows 映像在**windowsPE**配置阶段，实际安装 Windows 之前。 如果 Windows 安装程序必须安装多个语言包，安装可能会延迟。

 

**将语言包添加到 Windows 分发**

1.  将 Windows 分发复制到一个本地目录。 例如，Windows 产品 DVD 的内容复制到名为的目录**c:\\我\_通讯组**。

2.  找到您想要添加到 Windows 分发并将其复制到一个本地目录的语言的语言包.cab 文件。 

3.  创建**\\Langpacks**目录分布共享中。 例如︰

    ``` syntax
    mkdir C:\my_distribution\langpacks 
    ```

4.  复制该语言包链接到**\\Langpacks**分布共享的目录。 例如︰

    ``` syntax
    mkdir C:\my_distribution\langpacks
    xcopy C:\LPs\Microsoft-Windows-Client-Language-Pack_x64_fr-fr.cab C:\my_distribution\langpacks\Microsoft-Windows-Client-Language-Pack_x64_fr-fr.cab
    ```

5.  （可选）要使其他语言可以在 Windows 安装程序，将本地化的 Windows 安装程序源复制到分布共享中。 例如︰

    ``` syntax
    xcopy E:\sources\fr-fr C:\my_distribution\sources\fr-fr /cherkyi 
    xcopy E:\sources\de-de C:\my_distribution\sources\de-de /cherkyi
    ```

    其中*e︰*是 Windows 分发，其中包含本地化的 Windows 安装程序资源的位置。

    **Xcopy**命令的**/cherkyi**参数复制所有隐藏的文件和子目录，并将覆盖目标目录中的所有文件。

6.  安装的 Windows 映像的分布共享中。 此步骤是必需的部署映像服务和管理工具 (DISM.exe) 报告在.wim 文件中，然后重新创建 Lang.ini 文件安装的语言的列表。 使用 DISM 将 Windows 映像安装。 例如︰

    ``` syntax
    DISM.exe /Mount-Image /ImageFile:C:\my_distribution\sources\install.wim /index:1 /MountDir:C:\mount\windows
    ```

7.  报告的语言，通过使用**/Get-Intl**选项并指定分发共享将分布共享中可用或安装到 Windows 映像。 例如︰

    ``` syntax
    DISM.exe /image:c:\mount\windows /distribution:c:\my_distribution /Get-Intl
    ```

    验证正确的语言将显示为可用的语言和**通讯的其他可用语言**显示正确的语言。 例如︰

    ``` syntax
    Default system UI language : en-US
    System locale : en-US
    Default time zone : Pacific Standard Time
    User locale for default user : en-US
    Location : United States (GEOID = 244)
    Active keyboard(s) : 0409:00000409
    Keyboard layered driver : PC/AT Enhanced Keyboard (101/102-Key)

    Installed language(s): en-US
    Type : Fully localized language.

    Reporting distribution languages.

    The default language in the distribution is:
    en-US

    The other available languages in the distribution are:
    es-es, fr-fr
    ```

8.  重新创建 Lang.ini 文件。 例如︰

    ``` syntax
    DISM.exe /image:c:\mount\windows /Gen-LangINI /distribution:c:\my_distribution
    ```

    当添加或删除语言包从 Windows 分发时，您必须重新创建 Lang.ini 文件。 Lang.ini 文件位于 Windows 分发的源目录中，而在 Windows 安装过程中使用。 Lang.ini 文件在源目录中的应类似于以下形式︰

    ``` syntax
    [Available UI Languages]
    en-US = 3
    de-de = 0
    fr-fr = 0

    [Fallback Languages]
    en-US = en-us
    ```

    **请注意**  
    从分布共享中可用从一个完整的操作系统只运行安装程序时，可以为 Windows 安装程序选择一种语言。 如果您运行 Windows 安装程序可启动的介质或 Windows PE 时，必须向多语言支持的 Boot.wim 文件添加可选组件。 有关详细信息，请参阅[Windows 安装程序将添加多语言支持](add-multilingual-support-to-windows-setup.md)。

     

9.  卸载.wim 文件并提交所做的更改。 例如︰

    ``` syntax
    DISM.exe /Unmount-Image /MountDir:C:\mount\windows /commit 
    ```

    现在可以运行 Windows 安装程序。 安装期间，会提示您选择一种语言添加到分布共享。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[DISM 语言和国际服务命令行选项](dism-languages-and-international-servicing-command-line-options.md)

[在 Windows 中配置国际设置](configure-international-settings-in-windows.md)

 

 






