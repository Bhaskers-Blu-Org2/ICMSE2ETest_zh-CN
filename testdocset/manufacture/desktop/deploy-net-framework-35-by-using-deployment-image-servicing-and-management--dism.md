---
author: Justinha
Description: "通过使用部署映像服务和管理 (DISM) 部署.NET Framework 3.5"
ms.assetid: c21b1e0f-d480-4f51-99d1-d5f7acba3a4a
MSHAttr: PreferredLib:/library/windows/hardware
title: "通过使用部署映像服务和管理 (DISM) 部署.NET Framework 3.5"
ms.openlocfilehash: 23eec125eb87af989c62687223f3e57997f59f9e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="deploy-net-framework-35-by-using-deployment-image-servicing-and-management-dism"></a>通过使用部署映像服务和管理 (DISM) 部署.NET Framework 3.5


可以使用部署映像服务和管理 (DISM) 命令行工具来创建部署.NET Framework 3.5 将修改后的图像。

**重要**  
对于将支持多种语言的映像，则必须添加的任何语言包之前添加.NET Framework 3.5 的二进制文件。 此顺序可确保.NET Framework 3.5 的语言资源是正确参考映像中安装并可供用户和应用程序。

 

**本主题︰**

-   [使用 DISM 与互联网连接](#internet)

-   [使用 DISM 无互联网连接](#nointerent)

## <a name="span-idinternetspanspan-idinternetspanusing-dism-with-internet-connectivity"></a><span id="internet"></span><span id="INTERNET"></span>使用 DISM 与互联网连接


### <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>要求

-   互联网连接

-   对 Windows 更新的访问。 如果计算机或服务器位于防火墙后面，或者使用代理服务器，请参阅[KB900935-如何使用 Windows 更新客户端确定哪个代理服务器用来连接到 Windows Update 网站](http://support.microsoft.com/kb/900935)。

-   Windows 8，Windows Server® 2012 或[Windows 评估和部署工具包 (ADK)](http://go.microsoft.com/fwlink/p/?linkid=325506)工具。

-   安装介质

-   用户的管理员权限。 当前用户必须是本地的管理员组的成员才能添加或删除 Windows 功能。

### <a name="span-idforanonlinereferenceimagethatcanaccesswindowsupdatespanspan-idforanonlinereferenceimagethatcanaccesswindowsupdatespanspan-idforanonlinereferenceimagethatcanaccesswindowsupdatespanfor-an-online-reference-image-that-can-access-windows-update"></a><span id="For_an_online_reference_image_that_can_access_Windows_Update"></span><span id="for_an_online_reference_image_that_can_access_windows_update"></span><span id="FOR_AN_ONLINE_REFERENCE_IMAGE_THAT_CAN_ACCESS_WINDOWS_UPDATE"></span>可以访问 Windows 更新的在线参考图像

1.  使用管理员用户权限 （以管理员身份运行） Windows 8 或 Windows Server 2012 中打开命令提示符。

2.  从 Windows Update 安装.NET Framework 3.5 功能文件，请使用以下命令︰

    ``` syntax
    DISM /Online /Enable-Feature /FeatureName:NetFx3 /All 
    ```

    使用*/all*要启用所有父功能的指定功能。 有关 DISM 参数的详细信息，请参阅[启用或禁用 Windows 功能使用 DISM](http://go.microsoft.com/fwlink/p/?linkid=259118)。

3.  在 Windows 8 的电脑，.NET Framework 3.5 英寸显示为在启用**Windows 功能打开或关闭**控制面板中安装后。 对于 Windows Server 2012 系统功能的安装状态可以查看在服务器管理器中。

### <a name="span-idforanofflinereferenceimagespanspan-idforanofflinereferenceimagespanspan-idforanofflinereferenceimagespanfor-an-offline-reference-image"></a><span id="For_an_offline_reference_image"></span><span id="for_an_offline_reference_image"></span><span id="FOR_AN_OFFLINE_REFERENCE_IMAGE"></span>离线参考图像

1.  运行以下 DISM 命令 (映像装载到**c:\\测试\\脱机**文件夹和安装媒体中**d:**\\驱动器) 来安装.NET 3.5:

    ``` syntax
    DISM /Image:C:\test\offline /Enable-Feature /FeatureName:NetFx3 /All /LimitAccess /Source:D:\sources\sxs
    ```

    使用*/all*要启用所有父功能的指定功能。

    使用*/LimitAccess*来防止 DISM 联系 Windows 更新/WSUS。

    */Source*用于指定文件来还原该功能所需的位置。

    若要从安装的 Windows ADK 使用 DISM，找到 Windows ADK 服务文件夹并导航至该目录。 默认情况下，DISM 安装在**c:\\程序文件 (x86)\\窗口工具包\\8.0\\评估和部署工具包\\部署工具\\**。 您可以安装 DISM 和其他部署映像工具，如 Windows 系统映像管理器 (Windows SIM)，在另一台支持 Windows ADK 操作系统。 有关 DISM 支持的平台的信息，请参阅[DISM 支持的平台](http://go.microsoft.com/fwlink/p/?LinkId=698536)。

2.  运行下面的命令来查找.NET Framework 3.5 的状态 (脱机映像装载到**c:\\测试\\脱机**):

    ``` syntax
    DISM /Image:c:\test\offline /Get-Features /Format:Table
    ```

    **启用挂起**状态表示的图像必须联机才能完成安装。

### <a name="span-idnointerentspanspan-idnointerentspanusing-dism-with-no-internet-connectivity"></a><span id="nointerent"></span><span id="NOINTERENT"></span>使用 DISM 无互联网连接

您可以使用 DISM 添加.NET Framework 3.5 和存取**\\源\\SxS**到未连接到 Internet 的 Windows® 安装在安装介质上的文件夹。

### <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>要求

-   Windows 8，Windows Server 2012 或[Windows ADK](http://go.microsoft.com/fwlink/p/?linkid=325506)工具。

-   安装介质

-   用户的管理员权限。 当前用户必须是本地的管理员组的成员才能添加或删除 Windows 功能。

### <a name="span-idstepsspanspan-idstepsspanspan-idstepsspansteps"></a><span id="Steps"></span><span id="steps"></span><span id="STEPS"></span>步骤

1.  使用管理员用户权限 （以管理员身份运行） Windows 8 或 Windows Server 2012 中打开命令提示符。

2.  要从安装介质的**d︰**驱动器上安装.NET Framework 3.5，使用下面的命令︰

    ``` syntax
    DISM /Online /Enable-Feature /FeatureName:NetFx3 /All /LimitAccess /Source:d:\sources\sxs
    ```

    使用*/all*要启用所有父功能的指定功能。

    使用*/LimitAccess*来防止 DISM 联系 Windows 更新/WSUS。

    */Source*用于指定文件来还原该功能所需的位置。

    有关 DISM 参数的详细信息，请参阅[启用或禁用 Windows 功能使用 DISM](http://go.microsoft.com/fwlink/p/?linkid=259118)。

在 Windows 8 的 Pc 上安装后，.NET Framework 3.5 将显示为**打开或关闭 Windows 功能**在控制面板中启用。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Microsoft.NET Framework 3.5 部署注意事项](microsoft-net-framework-35-deployment-considerations.md)

 

 






