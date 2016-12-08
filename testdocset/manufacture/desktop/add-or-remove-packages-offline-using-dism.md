---
author: Justinha
Description: "添加或删除程序包使用 DISM 脱机"
ms.assetid: 32785116-e5ed-40ae-8802-9c2a67cd9938
MSHAttr: PreferredLib:/library/windows/hardware
title: "添加或删除程序包使用 DISM 脱机"
ms.openlocfilehash: f69aa01e5dad324751a015e6f246ec41a018cbf8
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add-or-remove-packages-offline-using-dism"></a>添加或删除程序包使用 DISM 脱机


部署映像服务和管理 (DISM.exe) 是一个命令行工具，用于更新脱机 Windows® 图像。 有两种方法来安装或删除使用 DISM 脱机软件包。 可以将无人参与答案文件应用到脱机映像，也可以添加或直接从命令提示符下删除软件包。

如果多个程序包安装到 Windows 映像，并且存在依存关系要求，以确保正确顺序的最佳方式是安装的使用答案文件。 您可以使用 DISM 将 Unattend.xml 答案文件应用于映像。 当您使用 DISM 应用答案文件时， **offlineServicing**配置阶段中的无人参与设置应用于 Windows 映像。

您必须安装最新版本的 Windows 评估和部署工具包 (Windows ADK)，其中包含的所有需要包括 DISM 工具。

## <a name="to-add-packages-to-an-offline-image-by-using-dism"></a>若要通过使用 DISM 将包添加到脱机映像

1.  在提升的命令提示符下，查找 Windows ADK 服务文件夹，并键入下列命令以检索名称或要修改的映像的索引号。

    ``` syntax
    Dism /Get-ImageInfo /ImageFile:C:\test\images\install.wim
    ```

    索引或名称值时需要指定图像文件的大多数操作。

2.  键入以下命令以装载脱机 Windows 映像。

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\install.wim /Name:"Windows 7 HomeBasic" /MountDir:C:\test\offline
    ```

3.  在命令提示符处，键入下面的命令以将特定程序包添加到映像。 您可以在一个命令行添加多个程序包。 将命令行中列出的顺序安装它们。

    ``` syntax
    Dism /Image:C:\test\offline /Add-Package /PackagePath:C:\packages\package1.cab /PackagePath:C:\packages\package2.cab
    ```

4.  在命令提示符处，键入下列命令以提交更改并卸载映像。

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\test\offline /Commit
    ```

## <a name="to-remove-packages-from-an-offline-image-by-using-dism"></a>若要通过使用 DISM 脱机映像中删除程序包

1.  在提升的命令提示符下，查找 Windows ADK 服务文件夹，并键入下列命令以检索名称或要修改的映像的索引号。

    ``` syntax
    Dism /Get-ImageInfo /ImageFile:C:\test\images\install.wim
    ```

    索引或名称值时需要指定图像文件的大多数操作。

2.  键入以下命令以装载脱机 Windows 映像。

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\install.wim /Name:"Windows 7 HomeBasic" /MountDir:C:\test\offline
    ```

3.  可选︰ 键入以下命令以列出映像中的程序包。

    ``` syntax
    Dism /Image:C:\test\offline /Get-Packages
    ```

    您可以使用`>featurelist.txt`命令的输出重定向到名为功能列表的文本文件。

4.  查看在已装载的映像中可用，请注意该程序包的程序包标识包的列表。

5.  在命令提示符下，指定要从映像中删除程序包标识。 可以在一个命令行上的多个包中删除。

    ``` syntax
    DISM /Image:C:\test\offline /Remove-Package /PackageName:Microsoft.Windows.Calc.Demo~6595b6144ccf1df~x86~en~1.0.0.0 /PackageName:Microsoft-Windows-MediaPlayer-Package~31bf3856ad364e35~x86~~6.1.6801.0
    ```

    指向原始源的程序包，或指定.cab 文件的路径，可以使用**/PackagePath**选项，也可以使用**/PackageName**选项以示图像中按名称指定的包。 有关详细信息，请参阅[DISM 操作系统程序包服务命令行选项](dism-operating-system-package-servicing-command-line-options.md)。

6.  在命令提示符处，键入下列命令以提交更改并卸载映像。

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\test\offline /Commit
    ```

## <a name="to-add-or-remove-packages-offline-by-using-dism-and-an-answer-file"></a>若要添加或删除通过使用 DISM 和答案文件脱机软件包

1.  打开 Windows sim 卡。

2.  要添加新包，请在主菜单上，单击**插入**并选择**程序包**。 浏览到要添加程序包，然后单击**打开**。

3.  若要删除现有程序包，请在您要删除**答案文件**窗格中选择的包。 在**属性**窗格中，改**操作**属性**中删除**。

    **请注意**  
    必须将包添加到**offlineServicing**的配置阶段。

4.  验证并保存答案文件。

5.  在提升的命令提示符下，查找 Windows ADK 服务文件夹，然后键入下面的命令以检索名称或您要装载的映像的索引号。

    ``` syntax
    Dism /Get-ImageInfo /ImageFile:C:\test\images\install.wim
    ```

6.  键入以下命令以装载脱机 Windows 映像。

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\install.wim /name:"Windows 7 HomeBasic" /MountDir:C:\test\offline
    ```

    索引或名称值时需要指定图像文件的大多数操作。

7.  在命令提示符处，键入下面的命令以将无人参与的答案文件应用于映像。

    ``` syntax
    DISM /Image:C:\test\offline /Apply-Unattend:C:\test\answerfiles\myunattend.xml
    ```

8.  在命令提示符处，键入下列命令以提交更改并卸载映像。

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\test\offline /Commit
    ```

有关 Windows sim 卡的详细信息，请参阅[Windows 安装程序技术参考](windows-setup-technical-reference.md)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[DISM 的部署 windows 映像服务和管理技术参考](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md)

[DISM 操作系统程序包服务命令行选项](dism-operating-system-package-servicing-command-line-options.md)

[DISM 无人参与服务命令行选项](dism-unattended-servicing-command-line-options.md)

 

 






