---
author: Justinha
Description: "使用 DISM 的 sideload 应用程序"
ms.assetid: ce95f34a-b9a4-4130-89ed-b7a7126fe21b
MSHAttr: PreferredLib:/library/windows/hardware
title: "使用 DISM 的 sideload 应用程序"
ms.openlocfilehash: 97e89dc47c6304aad9cfc32012155a628d8bdfd4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="sideload-apps-with-dism"></a>使用 DISM 的 sideload 应用程序


可以通过使用 PowerShell 或部署映像服务和管理 (DISM) 为 Windows 10 sideload 的业务线 (LOB) Windows 应用程序。 Windows 应用程序包括︰

-   Windows 应用程序和通用设备︰ Windows 应用程序建立在通用的 Windows 应用程序平台上，面向通用设备系列。
-   通用的 Windows 8 应用程序︰ Windows 应用程序面向 Windows 8.x。

通常情况下，Windows 应用程序都只能通过 Windows 应用商店。 可以提交到 Windows 应用商店的 LOB 的 Windows 应用程序并使其可在企业之外。 但是，可也仅在企业内开发用于 Windows 应用程序，并将其添加到 Windows 设备管理通过一个过程，我们称之为*sideloading*。 Sideloaded 应用程序无需通过 Windows 应用商店安装或通过认证。

以下是您需要了解到 sideload 应用程序的顺序︰

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">如何？</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>[了解 Sideloading 概念](#understandingconcepts)</p></td>
<td align="left"><p>介绍了您将需要了解的有关 sideloading 应用程序的一些基本概念。</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Sideloading 要求配置的 Pc](#sideloadingrequirements)</p></td>
<td align="left"><p>显示按顺序运行不同 Windows 版本的设备上的 sideload 应用程序必须满足的要求。 包含有关如何使用组策略来配置 sideloading 应用程序的个人电脑企业。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[为开发 Windows 应用商店应用程序配置的 Pc](#bkmk-developerlicense)</p></td>
<td align="left"><p>演示如何配置您的计算机有一个开发许可证，不会过期。 PC 可以用于开发 Windows 应用商店应用程序或企业应用程序将被添加到您的企业设备。</p></td>
</tr>
<tr class="even">
<td align="left"><p>[添加应用程序](#addapps)</p></td>
<td align="left"><p>演示如何开发的 sideload 应用程序。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[为应用程序添加多语言](#bkmk-mulitlang)</p></td>
<td align="left"><p>演示如何准备多语言映像，登录到图像，安装任何所需的应用程序资源包 （包括语言），然后使用复制配置文件来捕获图像。</p></td>
</tr>
<tr class="even">
<td align="left"><p>[库存应用程序](#inventoryapps)</p></td>
<td align="left"><p>演示如何列出安装在您的企业或脱机 Windows 映像中的设备上的 LOB 应用程序。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[删除应用程序](#removeapps)</p></td>
<td align="left"><p>演示如何删除各个实例的应用程序或删除应用程序的配置设置。</p></td>
</tr>
</tbody>
</table>

 

## <span id="UnderstandingConcepts"></span><span id="understandingconcepts"></span><span id="UNDERSTANDINGCONCEPTS"></span>


**了解 Sideloading 概念**

Windows 应用程序与的 Windows 桌面应用程序在它们的设计和方法的用户可以与它们进行交互。 若要了解有关 Windows 应用程序的详细信息，请参阅[应用 Windows 商店应用程序是什么？](http://go.microsoft.com/fwlink/?LinkId=264710)。

您不能从 Windows 应用商店下载了一个应用程序 sideload。 若要安装 Windows 的应用程序不是业务线的一部分，您必须使用 Windows 应用商店。 若要了解详细信息，请参阅[Windows 应用商店管理客户端访问](http://go.microsoft.com/fwlink/?LinkId=264712)。

LOB 的 Windows 不是签名的 Windows 应用商店应用程序可以是 sideloaded，或添加到脚本在运行时基于每个用户通过企业中的 PC。 他们可以还会提供图像中企业，以便应用程序注册为在 PC 创建每个新用户配置文件。 Sideload 每个用户的应用程序或图像中的要求是相同的但要添加，请您使用的 Windows PowerShell cmdlet 获得，并删除应用程序不同。 本主题提供了有关这两种方法的步骤。

可不是签名的 Windows 应用商店 sideload LOB 的 Windows 应用程序之前，必须配置 PC，请参阅[配置的 Pc Sideloading 要求](#sideloadingrequirements)。

**当您在开发 LOB Windows 应用程序为您的企业**

必须加密签名不被签名的 Windows 应用商店的 LOB Windows 应用程序。 应用程序仅在信任该签名的证书的计算机上安装。

有关如何对应用程序和使用证书进行签名的详细信息，请参阅[应用程序打包工具](http://go.microsoft.com/fwlink/?LinkId=242873)。

但是，可以使用开发人员许可证添加到您的 PC 的开发中的应用程序。 有关测试正在开发中的应用程序的详细信息，请参阅[获取开发许可](http://go.microsoft.com/fwlink/?LinkId=241313)。

您可以使用组策略来配置具有不过期来支持应用程序开发的开发人员许可加入域的计算机。 一旦配置了电脑，您不需要连接到互联网来获取或续订许可证。 有关更多信息，请参见[开发 Windows 应用商店应用程序的配置 Pc](#bkmk-developerlicense) 。

## <a name="span-idsideloadingrequirementsspanspan-idsideloadingrequirementsspanspan-idsideloadingrequirementsspanconfigure-pcs-for-sideloading-requirements"></a><span id="SideloadingRequirements"></span><span id="sideloadingrequirements"></span><span id="SIDELOADINGREQUIREMENTS"></span>Sideloading 要求配置的 Pc


设备符合 sideloading 要求的所有，直到应用程序图块在开始菜单上的将显示在框的右下角，以表明某个故障阻止运行该应用程序的"X"。

在某些情况下，这些要求的一部分包括使用 sideloading 产品密钥。 此项提供直接到设备部署 Windows 8 或 Windows 8.1 应用程序，而无需通过公共 Windows 应用商店安装它们所需的使用权限。

您可以添加并运行 sideloaded LOB 的 Windows 应用程序不是签名的 Windows 应用商店之前必须配置设备中基于以下条件︰

1.  对于那些加入了工作组的设备，您必须︰

    -   启用在设备上的 sideloading 产品密钥。

    -   并启用了**允许所有受信任的应用程序若要安装**组策略设置。 请参阅[使用组策略来配置 Pc sideloading 应用程序为您的企业](#usegp)。

    适用于︰

    -   Windows 10 企业
    -   Windows 8.1 企业
    -   Windows 8 企业版
    -   Windows 嵌入式 8.1 行业企业
    -   Windows 8.1 Pro 更新

2.  这些设备将加入到活动目录域，您必须︰

    -   加入到 Active Directory 域的设备。

    -   并启用了**允许所有受信任的应用程序若要安装**组策略设置。 请参阅[使用组策略来配置 Pc sideloading 应用程序为您的企业](#usegp)。

    适用于︰

    -   Windows 10 企业
    -   Windows 8.1 企业
    -   Windows 8 企业版
    -   Windows 嵌入式 8.1 行业企业
    -   Windows 8.1 Pro 更新
    -   Windows 服务器 2016年技术预览
    -   Windows Server 2012 R2 更新
    -   Windows Server 2012

3.  对于 sideloading 的产品密钥，该设备是否已加入域或工作组的成员将需要这些设备，您必须︰

    -   启用在设备上的 sideloading 产品密钥。

    -   并启用了**允许所有受信任的应用程序若要安装**组策略设置。 请参阅[使用组策略来配置 Pc sideloading 应用程序为您的企业](#usegp)。

    适用于︰

    -   Windows 10 专业
    -   Windows RT 8.1
    -   Windows 8.1 专业
    -   Windows RT
    -   Windows 8 专业版
    -   Windows 嵌入式 8.1 行业专业人员

4.  对于某些 Windows 嵌入式 8 行业设备，不再需要 sideloading 产品密钥设备是否加入域或工作组的成员。 在这种情况下，您必须︰

    -   使设备上的**允许所有受信任的应用程序若要安装**组策略设置。

    在 Windows 嵌入式 8 行业 sideloading 的详细信息，请参阅[企业指南安装 Windows 嵌入式 8 行业的通用 Windows 8 应用程序](http://go.microsoft.com/fwlink/?LinkId=391812)。

    适用于︰

    -   Windows 嵌入式 8.1 行业专业人员更新
    -   Windows 嵌入式 8.1 行业企业更新

<span id="UseGP"></span><span id="usegp"></span><span id="USEGP"></span>
**使用组策略来配置企业 Pc sideloading 应用程序的**

1.  打开组策略管理编辑器域 — — 基于组策略对象 (GPO) 的应用组策略设置，如下所示，您所选的 pc。

    **请注意**  
    在此过程中提供的步骤假定您了解组策略的设计和操作的基础知识。 若要管理域 — — 基于组策略在 Windows 8.1 PC 上，您将需要安装与[远程服务器管理工具进行 Windows 8.1](http://go.microsoft.com/fwlink/?LinkId=299896)安装组策略管理控制台。 有关组策略的详细信息，请参阅[为初级用户的组策略](http://go.microsoft.com/fwlink/?LinkId=330723)和[组策略技术中心](http://go.microsoft.com/fwlink/?LinkId=330564)。

     

2.  单击以展开**计算机配置**、**管理模板**、 **Windows 组件**，然后**应用程序包的部署**。

3.  双击**允许所有受信任的应用程序若要安装**设置。

4.  在**允许所有受信任的应用程序若要安装**窗口中，单击**启用**，然后单击**确定**。

设置组策略以使受信任的应用程序更新以下注册表设置︰ **HKEY\_本地\_机\\软件\\策略\\Microsoft\\Windows\\Appx\\AllowAllTrustedApps = 1**

**若要激活 sideloading 产品密钥**

1.  使用管理员权限打开命令提示符，键入以下命令以添加 sideloading 产品密钥︰

    ``` syntax
    Slmgr /ipk <sideloading product key>
    ```

    其中*&lt;sideloading 产品密钥&gt;*25 位键以启用计算机上的 sideloading。

2.  激活通过键入 sideloading 键︰

    ``` syntax
    slmgr /ato ec67814b-30e6-4a50-bf7b-d55daf729d1e
    ```

    **请注意**  
    GUID 激活不是 sideloading 的产品密钥相同。 激活的 GUID 将始终为 ec67814b-30e6-4a50-bf7b-d55daf729d1e。

     

有关 sideloading 产品密钥的详细信息，请参阅[Windows 8 许可指南](http://go.microsoft.com/fwlink/?LinkId=267899)。

## <a name="span-idbkmkdeveloperlicensespanspan-idbkmkdeveloperlicensespanspan-idbkmkdeveloperlicensespanconfigure-pcs-for-developing-windows-apps"></a><span id="BKMK_DeveloperLicense"></span><span id="bkmk_developerlicense"></span><span id="BKMK_DEVELOPERLICENSE"></span>为开发 Windows 应用程序中配置的 Pc


您可以配置您的 Pc 有一个开发许可证，不会过期。 一旦配置了电脑，您不需要连接到互联网来获取或续订许可证。 您的计算机必须是域的成员并将运行以下操作系统之一︰

-   Windows 10 企业
-   Windows 8.1 企业
-   Windows 8 专业版

**请注意**  
若要启用 Windows 8 专业版设备上的 sideloading，您必须使用 sideloading 产品激活密钥。 有关详细信息，请参阅[配置 Sideloading 要求的 Pc](#sideloadingrequirements)

 

**使用开发人员许可证配置企业 Pc**

1.  打开组策略管理编辑器域 — — 基于组策略对象 (GPO) 的应用的组策略设置，如下所示，您所选的 pc。

    **请注意**  
    在此过程中提供的步骤假定您了解组策略的设计和操作的基础知识。 若要管理域 — — 基于组策略在 Windows 8.1 PC 上，您将需要安装与[远程服务器管理工具进行 Windows 8.1](http://go.microsoft.com/fwlink/?LinkId=299896)安装组策略管理控制台。 有关组策略的详细信息，请参阅[为初级用户的组策略](http://go.microsoft.com/fwlink/?LinkId=330723)和[组策略技术中心](http://go.microsoft.com/fwlink/?LinkId=330564)。

     

2.  单击以展开**计算机配置**、**管理模板**、 **Windows 组件**，然后**应用程序包的部署**。

3.  双击**Windows 应用程序而不安装开发人员许可证允许开发**设置。

4.  在**允许开发，但不安装开发人员许可证的 Windows 应用程序的**窗口中，单击**启用**，然后单击**确定**。

5.  双击**允许所有受信任的应用程序若要安装**设置。

6.  在**允许所有受信任的应用程序若要安装**窗口中，单击**启用**，然后单击**确定**。

设置下面的注册表设置的组策略，允许 Windows 应用程序的开发，而不安装开发人员许可证更新︰ **HKEY\_本地\_机\\软件\\策略\\Microsoft\\Windows\\Appx\\AllowDevelopmentWithoutDevLicense = 1**

设置组策略以使受信任的应用程序更新以下注册表设置︰ **HKEY\_本地\_机\\软件\\策略\\Microsoft\\Windows\\Appx\\AllowAllTrustedApps = 1**

## <a name="span-idaddappsspanspan-idaddappsspanspan-idaddappsspanadd-apps"></a><span id="AddApps"></span><span id="addapps"></span><span id="ADDAPPS"></span>添加应用程序


有两种方法来添加应用程序。 用户可以添加应用程序程序包，这将使应用程序可对该用户只。 或者，应用程序可以安装在 Windows 映像，这样会使应用程序可用每个用户的 Windows 映像，在首次登录，或在下次登录时，如果已创建的用户帐户。 这第二种情况被称为资源调配 app 包装箱。

**添加应用程序封装**

通过*添加 appxpackage* PowerShell cmdlet，您可以基于每个用户安装应用程序软件包 （.appx 或.appxbundle）。 对 LOB 应用程序，您可以为每个用户的数目没有限制。

**将 LOB 应用程序添加到用户帐户**

-   Windows PowerShell 提示 Windows 8 或 Windows Server 2012 计算机上时，添加.appx （或.appxbundle） 的文件包。 添加应用程序时，请包括任何所需的依赖项的应用程序软件包。 例如，键入︰

    ``` syntax
    add-appxpackage C:\app1.appx -DependencyPath C:\winjs.appx
    ```

    有关详细信息，请参阅[应用程序安装在 Windows PowerShell 的 Cmdlet](http://go.microsoft.com/fwlink/?LinkId=393919)。

**将提供的 LOB 应用程序添加到 Windows 映像**

在 Windows 映像中安装的应用程序被称为*配置*应用程序。 提供应用程序映像中转移，如果已经创建的用户帐户计划为每个用户首次登录时或在下次登录时，Windows 映像的安装。

之前通过使用 DISM 应用程序资源调配命令部署映像启动到审核模式时，可以向 Windows 映像中添加这些应用程序。 有关审核模式的详细信息，请参阅[审核模式概述](audit-mode-overview.md)。

提供应用程序特定于 PC 并不会随用户一起漫游。 在图像中只能安装 24 置备的应用程序。

在已部署的 Windows 映像，则应改用添加 AppxPackage cmdlet PowerShell 中。 如果您使用 DISM 应用程序活动用户配置部署 Windows 映像上的命令，应记录从图像上时，所有用户，以便您是唯一的用户登录，才能运行此命令。

**请注意**  
Windows 8 上要更新置备的应用程序，必须先删除已设置的应用程序，然后再部署应用程序的新版本。 然后将应用更新每个用户在下次登录的时。

在 Windows 8.1 和更新版本不再需要删除部署配置的应用程序的新版本之前已设置的应用程序。

 

**将提供的 LOB 应用程序添加到 Windows 映像**

-   使用部署映像服务和管理 (DISM) 命令行工具或 PowerShell cmdlet 将 LOB 应用程序没有 Windows 应用商店的许可。 例如，在提升的命令提示符下，键入︰

    ``` syntax
    DISM /Online /Add-ProvisionedAppxPackage /PackagePath:C:\App1.appx /SkipLicense
    ```

    或者，在 Windows PowerShell 提示符下，键入︰

    ``` syntax
    Add-AppxProvisionedPackage -Online -FolderPath C:\Appx -SkipLicense
    ```

    有关详细信息，请参阅[DISM 应用程序包 （.appx 或.appxbundle） 服务命令行选项](dism-app-package--appx-or-appxbundle--servicing-command-line-options.md)或[DISM Cmdlet](http://go.microsoft.com/fwlink/?LinkId=393917)。 有关 DISM 支持平台的信息，请参阅[DISM 支持的平台](dism-supported-platforms.md)。

**请注意**  
计算机没有加入域或已激活的 sideloading 产品密钥安装调配的 LOB 应用程序之前。 但是，除非计算机满足此 sideloading 要求，否则将不会运行应用程序。 有关详细信息，请参阅[自定义开始屏幕](customize-the-start-screen.md)。

 

**更新配置 LOB 应用程序后已被添加到 Windows 映像**

Windows 8 上要更新置备的应用程序，必须先删除已设置的应用程序，然后再部署应用程序的新版本。 然后将应用更新每个用户在下次登录的时。

在 Windows 8.1，较新更新配置的应用程序，您需要更新为已登录到 Windows 映像使用应用程序配置每个用户的应用程序︰

**更新到 Windows 映像配置 LOB 应用程序**

1.  使用 PowerShell 更新 LOB 应用程序没有 Windows 应用商店的许可。 这必须针对每个已登录到计算机的用户运行的 Windows 映像。 例如，如果您已经安装的原始版本 1.0.0.0，app，，现在需要能够更新到版本 1.0.0.1，PowerShell 会话，然后在键入︰

    ``` syntax
    Add-AppxPackage -Path App1_1.0.0.2 -DependencyPath C:\appx\WinJS.appx
    ```

    其中`c:\appx\WinJS.appx`是依赖包的路径。

2.  一旦您已更新了您的应用程序，您可以验证已更新的应用程序的版本。 从 PowerShell 会话，请键入︰

    ``` syntax
    Get-AppxPackage | Out-GridView
    ```

## <a name="span-idbkmkmulitlangspanspan-idbkmkmulitlangspanspan-idbkmkmulitlangspanadd-multiple-languages-for-apps"></a><span id="BKMK_MulitLang"></span><span id="bkmk_mulitlang"></span><span id="BKMK_MULITLANG"></span>为应用程序添加多语言


准备一个多语言映像，登录到该图像时，安装任何所需的应用程序资源包 （包括语言），然后使用复制配置文件捕获映像。

**多语言映像准备应用程序**

1.  创建包含以下内容为 c: unattend.xml\\unattend.xml:

    ``` syntax
    <?xml version="1.0" encoding="utf-8"?>
    <unattend xmlns="urn:schemas-microsoft-com:unattend">
        <settings pass="specialize">
            <component name="Microsoft-Windows-Shell-Setup" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
                <CopyProfile>true</CopyProfile>
                <RegisteredOrganization />
                <RegisteredOwner />
            </component>
        </settings>
        <cpi:offlineImage cpi:source="catalog:d:/desktop/x86 clgs/install_windows vista ultimate.clg" xmlns:cpi="urn:schemas-microsoft-com:cpi" />
    </unattend>
    ```

    **请注意**  
    设置语言和从 Windows 应用商店安装更新的信息，请参阅[更改应用程序中使用的语言](http://go.microsoft.com/fwlink/?LinkId=389195)。

     

2.  登录到本地管理员用户帐户从 OOBE 干净的图像上。

    **重要**  
    时将一种特定语言添加到 Windows 应用程序，您还需要[将语言包添加到 Windows](add-language-packs-to-windows.md)的相同语言的 Windows 应用程序一样。

     

3.  向当前用户的语言首选项列表中添加所需的语言。

4.  **安装使用 Windows 应用商店帐户 （MSA） 的应用程序更新**

    1.  登录到具有 MSA 帐户的存储区。

        **请注意**  
        仅存储区。 不转换为 MSA 的本地帐户。

        如果您没有 MSA 帐户，您可以更新没有 Windows 存储帐户的应用程序。

         

    2.  检查更新并安装新的语言资源包。

    3.  注销 Windows 应用商店和 MSA 帐户删除。

5.  打开提升的命令提示符并键入︰

    ``` syntax
    Sysprep.exe /generalize /oobe /reboot /unattend:C:\unattend.xml
    ```

    然后按 enter 键。

6.  您应该看到计算机引导到 OOBE。 此时应出现在复制配置文件之前已添加的任何语言。

**不使用 Windows 应用商店帐户 （MSA） 的情况下安装应用程序更新**

1.  电脑程序完成安装后，打开提升的命令提示符。

2.  类型**启动 ms-windows-更新存储区︰**

3.  您将看到 Windows 存储更新页面。 您会看到显示挂起的更新。

4.  点击**安装**以安装更新。

## <a name="span-idinventoryappsspanspan-idinventoryappsspanspan-idinventoryappsspaninventory-apps"></a><span id="InventoryApps"></span><span id="inventoryapps"></span><span id="INVENTORYAPPS"></span>库存应用程序


可以列出在脱机或联机 Windows 映像上安装在 LOB 应用程序并获取有关这些程序包的其他信息。

**每个用户帐户列表的 LOB 应用程序**

1.  您可以为特定的用户帐户在计算机上安装的 Windows 应用程序的列表。 您必须具有管理员特权才能列出的包不是当前用户的用户打开 PowerShell。 例如，PowerShell 提示时，请键入︰

    ``` syntax
    Get-AppxPackage -AllUsers
    ```

2.  您可以为特定的用户安装的包的列表。 您必须具有管理员特权才能列出的包不是当前用户的用户打开 PowerShell。 例如，PowerShell 提示时，请键入︰

    ``` syntax
    Get-AppxPackage -Name Package1 -User domain\username
    ```

3.  您还可以获取清单的 app 包装箱 (.appx)，其中包括以下信息︰ 包 id。 例如，PowerShell 提示时，请键入︰

    ``` syntax
    Get-AppxPackageManifest -Package Package1
    ```

4.  可以使用管道来获取对应用程序软件包 (.appx) 清单，如果您不知道完整的包的名称。 例如，PowerShell 提示时，请键入︰

    ``` syntax
    (Get-AppxPackage -Name "*WinJS*" | Get-AppxPackageManifest).package.applications.application.id
    ```

**在 Windows 映像中提供的列表 LOB 应用程序**

-   您可以配置将使用 Dism.exe 或 PowerShell 为每个新用户安装的 Windows 映像中的程序包的列表。 例如，在 PowerShell 提示符下，键入︰

    ``` syntax
    Get-AppxProvisionedPackage -Path c:\offline
    ```

    或者，在命令提示符处，键入︰

    ``` syntax
    DISM.exe /Image:C:\test\offline /Get-ProvisionedAppxPackages
    ```

有关详细信息，请参阅[映像或组件使用 DISM 的花费清单](take-inventory-of-an-image-or-component-using-dism.md)。

## <a name="span-idremoveappsspanspan-idremoveappsspanspan-idremoveappsspanremove-apps"></a><span id="RemoveApps"></span><span id="removeapps"></span><span id="REMOVEAPPS"></span>删除应用程序


您可以删除各个实例的应用程序，或删除应用程序的配置设置。

**每个用户帐户的 LOB 应用程序中移除**

-   您可以删除某个应用程序的当前用户。 例如，在命令提示符处，键入︰

    ``` syntax
    Remove-AppxPackage Package1
    ```

**在 Windows 映像中删除已设置的 LOB 应用程序**

-   当您删除已设置的应用程序时，应用程序将不安装为新用户帐户。 对于当前登录的用户都处于活动状态的计算机上其他用户帐户，该应用程序不会从这些帐户。 该应用程序将需要对这些现有的应用程序被卸载。

    例如，若要删除已设置的 LOB 应用程序，MyAppxPkg，从 Windows 映像，在提升 PowerShell 提示符下，键入︰

    ``` syntax
    Remove-AppxProvisionedPackage -Online -PackageName MyAppxPkg
    ```

    或者，在命令提示符处，键入︰

    ``` syntax
    DISM.exe /Online /Remove-ProvisionedAppxPackage /PackageName:microsoft.app1_1.0.0.0_neutral_en-us_ac4zc6fex2zjp
    ```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[应用程序安装在 Windows PowerShell 的 Cmdlet](http://go.microsoft.com/fwlink/?LinkId=243074)

[DISM 应用程序包 （.appx 或.appxbundle） 服务命令行选项](dism-app-package--appx-or-appxbundle--servicing-command-line-options.md)

[应用程序打包工具](http://go.microsoft.com/fwlink/?LinkId=242873)

[AppX 模块 Cmdlet](http://go.microsoft.com/fwlink/?LinkId=393919)

[更改应用程序中使用的语言](http://go.microsoft.com/fwlink/?LinkId=389195)

[DISM Cmdlet](http://go.microsoft.com/fwlink/?LinkId=393917)

[DISM 支持的平台](dism-supported-platforms.md)

[企业安装 Windows 嵌入式 8 行业通用的 Windows 8 应用程序指南](http://go.microsoft.com/fwlink/?LinkId=391812)

[获取开发人员许可证](http://go.microsoft.com/fwlink/?LinkId=241313)

[初级用户的组策略](http://go.microsoft.com/fwlink/?LinkId=330723)

[组策略技术中心](http://go.microsoft.com/fwlink/?LinkId=330564)

[自定义开始屏幕](customize-the-start-screen.md)

[管理客户端访问的 Windows 应用商店](http://go.microsoft.com/fwlink/?LinkId=264712)

[Microsoft 批量许可](http://go.microsoft.com/fwlink/?LinkId=264711)

[对于 Windows 8.1 的远程服务器管理工具](http://go.microsoft.com/fwlink/?LinkId=299896)

[Windows 商店应用程序是什么？](http://go.microsoft.com/fwlink/?LinkId=264710)

[Windows 8 许可指南](http://go.microsoft.com/fwlink/?LinkId=267899)

 

 






