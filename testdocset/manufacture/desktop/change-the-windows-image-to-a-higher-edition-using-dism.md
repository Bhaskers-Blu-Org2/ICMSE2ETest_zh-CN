---
author: Justinha
Description: "将 Windows 映像更改为较高版本使用 DISM"
ms.assetid: 754e7ef2-85fe-4b45-94d7-d7bd1db6eaa1
MSHAttr: PreferredLib:/library/windows/hardware
title: "将 Windows 映像更改为较高版本使用 DISM"
ms.openlocfilehash: 466f0acbe2be0476183f1787d379591d010cf536
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="change-the-windows-image-to-a-higher-edition-using-dism"></a>将 Windows 映像更改为较高版本使用 DISM


Windows® 版服务命令可用于更改为较高版本的 Windows 的一个版本的 Windows。 每个潜在的目标版本的版本程序包 Windows 映像中转移。 这被称为版本系列图像。 您可以使用命令行选项列出可能的目标版本。 由于转移目标版本，可以处理单个映像，并且更新将适当地应用于图像中的每个版本。

您需要更改在线的 Windows 版本的产品密钥。 脱机更改不需要产品密钥。 如果将映像更改为较高版本使用脱机服务时，您可以使用下列方法之一添加产品密钥︰

-   过程的全新体验 (OOBE) 中输入产品密钥。

-   使用无人参与的答案文件在**specialize**配置阶段输入的产品密钥。

-   使用部署映像服务和管理 (DISM) 和 Windows 版本服务命令行选项**/Set-ProductKey**脱机设置版本之后。

有关产品密钥的详细信息，请参阅[使用产品密钥和激活](work-with-product-keys-and-activation-auth-phases.md)。

## <a name="span-idfindandchangecurrenteditionofwindowsspanspan-idfindandchangecurrenteditionofwindowsspanspan-idfindandchangecurrenteditionofwindowsspanfind-and-change-current-edition-of-windows"></a><span id="Find_and_Change_Current_Edition_of_Windows"></span><span id="find_and_change_current_edition_of_windows"></span><span id="FIND_AND_CHANGE_CURRENT_EDITION_OF_WINDOWS"></span>查找和更改当前版本的 Windows


您可以找到的版本 Windows 映像的属性当前设置为装载映像并在已装载的映像上运行 DISM 命令。

**若要查找当前版本**

1.  单击**开始**，然后键入**部署**。 用鼠标右键单击**部署和图像处理工具环境**，然后选择**以管理员身份运行**。

2.  在命令提示符下，键入以下命令以检索名称或要修改的映像的索引号。

    ``` syntax
    Dism /Get-ImageInfo /ImageFile:C:\test\images
    ```

3.  键入以下命令以装载脱机 Windows 映像。

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images /Index:1 /MountDir:C:\test\offline
    ```

    索引或名称值时需要指定图像文件的大多数操作。

4.  键入以下命令查找 Windows 映像的版本当前被设置为。

    ``` syntax
    Dism /Image:C:\test\offline /Get-CurrentEdition
    ```

    请注意您的映像当前被设置为 Windows 的版本。 如果映像已更改为较高版本不应更改它再次。 我们建议您开始使用最低版本。

5.  卸载该映像或继续执行下一步的过程。 若要卸载映像，请键入以下命令。

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\test\offline /Commit
    ```

**若要更改为较高版本的 Windows**

1.  键入以下命令以装载脱机 Windows 映像 （如果它未装载）。

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images /Name:<Image_name> /MountDir:C:\test\offline
    ```

2.  键入下面的命令来查找版本的 Windows，您可以更改您的图像。

    ``` syntax
    Dism /Image:C:\test\offline /Get-TargetEditions
    ```

    注意为您想要更改到的版本的版本 ID。

    **请注意**  
    不能设置为更低版本的 Windows 映像。 当您运行**/Get-TargetEditions**选项时，不会出现的最低版本。 您不应该在图像已更改为较高版本上使用此过程。

     

3.  键入以下命令指定版本 ID 更改为较高版本的 Windows 映像。

    ``` syntax
    Dism /Image:C:\test\offline /Set-Edition:Professional
    ```

4.  键入下面的命令以卸载映像并提交更改。

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\test\offline /Commit
    ```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[了解处理策略](understanding-servicing-strategies.md)

[DISM Windows 版本服务命令行选项](dism-windows-edition-servicing-command-line-options.md)

[DISM 的部署 windows 映像服务和管理技术参考](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md)

 

 






