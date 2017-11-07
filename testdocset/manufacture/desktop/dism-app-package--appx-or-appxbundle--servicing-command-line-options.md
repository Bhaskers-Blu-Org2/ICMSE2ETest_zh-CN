---
author: Justinha
Description: "DISM 应用程序包 （.appx 或.appxbundle） 服务命令行选项"
ms.assetid: 3a2de7c0-d132-41ec-9603-a54e958fee2c
MSHAttr: PreferredLib:/library/windows/hardware
title: "DISM 应用程序包 （.appx 或.appxbundle） 服务命令行选项"
ms.openlocfilehash: 6aeedd8aae97a87a63c83cc85c1ed5edd13e4fc8
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="dism-app-package-appx-or-appxbundle-servicing-command-line-options"></a>DISM 应用程序包 （.appx 或.appxbundle） 服务命令行选项


应用程序包服务命令可用于添加、 删除和列表在 Windows 映像中设置应用程序包 （.appx 或.appxbundle）。 新的 Windows 10，.appxbundle，是一起使用以丰富的应用程序体验，同时最小化在给定计算机上的磁盘占用空间的应用程序和资源包的集合。 详细介绍.appxbundle 软件包和存储管道的详细内容，请参阅[应用程序打包](http://go.microsoft.com/fwlink/p/?LinkId=698643)。 仅在.appxbundle 中的软件包的子集可能添加到映像中，观音菩萨向提供使用 DISM。 有关详细信息，请参阅[了解如何 DISM 增添.appxbundle 资源程序包添加到映像](#bkmk-understanding)。

设置应用程序的包添加到 Windows 映像，然后安装每个新的或现有的用户配置文件在下次用户登录。 有关详细信息，包括要求对应用程序资源调配包，请参阅[使用 DISM 的 Sideload 应用程序](sideload-apps-with-dism-s14.md)。

您还可以使用 PowerShell 来添加、 删除和列出应用程序软件包 （.appx 或.appxbundle） 每个图像或 Windows 安装中每个用户。 有关详细信息，请参阅[部署映像服务管理 (DISM) 在 Windows PowerShell 的 Cmdlet](http://go.microsoft.com/fwlink/?LinkId=239926)和[应用程序安装在 Windows PowerShell 的 Cmdlet](http://go.microsoft.com/fwlink/?LinkId=247300)。

服务使用 DISM 的 Windows 映像的基本语法如下︰

**DISM.exe** {**/图像︰**&lt;*路径\_到\_图像\_目录*&gt; | **/Online**} \[ **dism\_全局\_选项**\] {**服务\_选项**} \[ &lt;*服务\_参数*&gt;\]

下列应用程序软件包 （.appx 或.appxbundle） 服务选项可用于脱机映像。

**DISM.exe /Image:**&lt;*路径\_到\_图像\_目录*&gt; \[ **/Get-ProvisionedAppxPackages** | **/Add-ProvisionedAppxPackage** | **/Remove-ProvisionedAppxPackage** | **/Set-ProvisionedAppxDataFile**\]

下列应用程序软件包 （.appx 或.appxbundle） 服务选项都可用于正在运行的操作系统。

**DISM.exe / 在线**\[ **/Get-ProvisionedAppxPackages** | **/Add-ProvisionedAppxPackage** | **/Remove-ProvisionedAppxPackage** | **/Set-ProvisionedAppxDataFile**\]

## <a name="span-idapppackageservicingoptionsspanspan-idapppackageservicingoptionsspanspan-idapppackageservicingoptionsspanapp-package-servicing-options"></a><span id="App_package_servicing_options"></span><span id="app_package_servicing_options"></span><span id="APP_PACKAGE_SERVICING_OPTIONS"></span>应用程序包服务选项


本部分介绍如何使用每个应用程序服务选项。 这些选项不是区分大小写的。

### <a name="span-idget-helpspanspan-idget-helpspanspan-idget-helpspanget-help-"></a><span id="_Get-Help___"></span><span id="_get-help___"></span><span id="_GET-HELP___"></span>/ 获取帮助 /？

应用程序程序包服务命令行选项后紧接着使用，显示的选项和参数的信息。 其他主题可能会在指定了映像之后变为可用。

示例︰

**Dism /image:C:\\测试\\脱机 /Add-ProvisionedAppxPackages /？**

**Dism 在线 / /Get-ProvisionedAppxPackages /？**

### <a name="span-idget-provisionedappxpackagesspanspan-idget-provisionedappxpackagesspanspan-idget-provisionedappxpackagesspanget-provisionedappxpackages"></a><span id="_Get-ProvisionedAppxPackages"></span><span id="_get-provisionedappxpackages"></span><span id="_GET-PROVISIONEDAPPXPACKAGES"></span>/ Get ProvisionedAppxPackages

显示有关应用程序程序包信息 （.appx 或.appxbundle），在图像中，设置要安装的每个新用户。

**Dism /Image:C:\\测试\\/Get-ProvisionedAppxPackages 脱机**

### <a name="span-idadd-provisionedappxpackagespanadd-provisionedappxpackage"></a><span id="Add-ProvisionedAppxPackage"></span>/ 添加-ProvisionedAppxPackage

**/ 添加-ProvisionedAppxPackage {/FolderPath:&lt;应用程序\_文件夹\_路径&gt; \[/SkipLicense\] \[/CustomDataPath:&lt;自定义\_文件\_路径&gt;\] | /PackagePath:&lt;主\_包\_路径&gt; \[/DependencyPackagePath:&lt;依赖项\_包\_路径&gt;\] {\[/LicenseFile:&lt;许可证\_文件\_路径&gt;\]|\[/SkipLicense\]} \[/CustomDataPath:&lt;自定义\_文件\_路径&gt;\] }**

向图像中添加一个或多个应用程序软件包。

将添加到 Windows 映像的应用程序，并将其注册为每个现有或新的用户配置文件在下次用户登录时。 如果该应用程序添加到联机映像时，该应用程序将不能注册为当前用户直到下一次用户登录时。

使用**/FolderPath**来指定包含主包、 任何依赖关系的软件包，并许可文件解包应用程序文件的文件夹。 这只支持对解包应用程序软件包。

**/PackagePath**用于指定应用程序软件包 （.appx 或.appxbundle）。 资源调配业务线应用程序联机时，您可以使用**/PackagePath** 。

**重要**  
使用**/PackagePath**参数设置.appxbundle 软件包。

从一台主机正在运行 Windows 预安装环境 (WinPE) 4.0，Windows Server 2008 R2 或较早版本的 Windows 的计算机不支持**/PackagePath** 。

 

如果包有体系结构特定的依赖项，您必须安装所有依赖项的适用体系结构目标在图像上。 例如，在 x64 上目标图像，包括通往这两个 x86 和 x64 依赖关系的软件包或这两个解包应用程序文件的文件夹中。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">计算机体系结构</th>
<th align="left">若要安装的依赖项︰</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>x64</p></td>
<td align="left"><p>x64 和 x86</p></td>
</tr>
<tr class="even">
<td align="left"><p>x86</p></td>
<td align="left"><p>x86</p></td>
</tr>
<tr class="odd">
<td align="left"><p>ARM</p></td>
<td align="left"><p>Windows 仅 RT (ARM)</p></td>
</tr>
</tbody>
</table>

 

使用**/CustomDataPath**可以指定可选的自定义数据文件的应用程序。 您可以指定任何文件名。 该文件将重命名为 Custom.dat，将其添加到图像时。

使用**/LicensePath**与**/PackagePath**选项指定包含您的应用程序许可证的.xml 文件的位置。

仅使用**/SkipLicense**应用程序不需要支持 sideloading 的计算机上的许可证。 在其他情况下使用**/SkipLicense**可以破坏图像。

示例︰

**Dism /Image:C:\\测试\\脱机 /Add-ProvisionedAppxPackage /FolderPath:c:\\测试\\应用程序\\MyUnpackedApp /CustomDataPath:c:\\测试\\应用程序\\CustomData.xml**

**Dism / 在线 /Add-ProvisionedAppxPackage /PackagePath:C:\\测试\\应用程序\\MyPackedApp\\MainPackage.appx /DependencyPackagePath:C:\\测试\\应用程序\\MyPackedApp\\框架 x86.appx /DependencyPackagePath:C:\\测试\\应用程序\\MyPackedApp\\框架 x64.appx /LicensePath:C:\\测试\\应用程序\\MyLicense.xml**

**Dism / 在线 /Add-ProvisionedAppxPackage /FolderPath:C:\\测试\\应用程序\\MyUnpackedApp /SkipLicense**

**Dism /Image:C:\\测试\\脱机 /Add-ProvisionedAppxPackage /PackagePath:C:\\测试\\应用程序\\MyPackedApp\\MainPackage.appxbundle /SkipLicense**

### <a name="span-idremove-provisionedappxpackagespanremove-provisionedappxpackage"></a><span id="Remove-ProvisionedAppxPackage"></span>/ 删除 ProvisionedAppxPackage

**/ 删除 ProvisionedAppxPackage /PackageName:&lt;软件包名称&gt;**

提供应用程序软件包 （.appx 或.appxbundle） 从图像中删除。 应用程序软件包不能注册到新创建的用户帐户中。

**重要**  
此选项将只删除为包设置，如果已注册到任何用户配置文件。 使用 PowerShell 中[删除 AppxPackage](http://go.microsoft.com/fwlink/?LinkId=215772) cmdlet 删除该应用程序为每个用户的已注册到要完全从映像中删除该应用程序。

如果应用程序未注册到任何用户配置文件，/Remove-ProvisionedAppxPackage 选项将完全删除此程序包。

 

要从已安装桌面体验 Windows Server 2012 映像删除应用程序软件包，必须先删除桌面体验删除应用程序软件包。 桌面体验是 Windows Server 2012 的服务器核心安装的**/Remove-ProvisionedAppxPackage**选项的要求。

示例︰

**Dism /Image:C:\\测试\\脱机 /Remove-ProvisionedAppxPackage /PackageName:microsoft.devx.appx.app1\_1.0.0.0\_中性\_ac4zc6fex2zjp**

### <a name="span-idset-provisionedappxdatafilecustomdatapathcustomfilepathpackagenamepackagenamespanspan-idset-provisionedappxdatafilecustomdatapathcustomfilepathpackagenamepackagenamespanspan-idset-provisionedappxdatafilecustomdatapathcustomfilepathpackagenamepackagenamespanset-provisionedappxdatafile-customdatapathlt-customfilepathgt-packagenamelt-packagenamegt"></a><span id="_Set-ProvisionedAppxDataFile___CustomDataPath___custom_file_path____PackageName___PackageName_"></span><span id="_set-provisionedappxdatafile___customdatapath___custom_file_path____packagename___packagename_"></span><span id="_SET-PROVISIONEDAPPXDATAFILE___CUSTOMDATAPATH___CUSTOM_FILE_PATH____PACKAGENAME___PACKAGENAME_"></span>/ 一组 ProvisionedAppxDataFile \[/CustomDataPath:&lt;自定义\_文件\_路径&gt;\] /PackageName:&lt;软件包名称&gt;

将自定义数据文件添加到指定应用程序软件包 （.appx 或.appxbundle）。

添加自定义数据文件使用此选项时，指定的应用程序 （.appx 或.appxbundle） 包必须已添加到之前的图像中。 使用**/Add-ProvisionedAppxPackage**选项时，您还可以添加自定义数据文件。

使用**/CustomDataPath**可以指定可选的自定义数据文件的应用程序。 您可以指定任何文件名。 该文件将重命名为 Custom.dat，将其添加到图像时。 如果 Custom.dat 文件已经存在，它将被覆盖。

**/PackageName**用于指定应用程序软件包 （.appx 或.appxbundle）。

示例︰

**DISM.exe /Image:C:\\测试\\脱机 /Set-ProvisionedAppxDataFile /CustomDataPath:c:\\测试\\应用程序\\Custom.dat /PackageName:microsoft.appx.app1\_1.0.0.0\_中性\_ac4zc6fex2zjp**

## <a name="span-idbkmkunderstandingspanspan-idbkmkunderstandingspanspan-idbkmkunderstandingspanunderstanding-how-dism-adds-appxbundle-resource-packages-to-an-image"></a><span id="BKMK_understanding"></span><span id="bkmk_understanding"></span><span id="BKMK_UNDERSTANDING"></span>了解如何 DISM 将.appxbundle 资源包添加到映像


当.appxbundle 添加到图像时，并不是所有的资源包，包内都适用。 例如，如果一个应用程序添加到 Windows 映像与西班牙语 （西班牙） 的默认语言，法语 （法国） 资源不应包含。 若要确定哪些资源添加到映像，包适用性取决于使用︰

-   **语言资源包**︰ 如果操作系统语言不存在，则不添加相应的应用程序语言资源包。 例如，可能有英语 （美国） 与一个 Windows 10 以及默认语言，西班牙语 （西班牙） 语言包包含的图像。 英语 （美国） 和西班牙语 （西班牙） 的应用程序资源包将添加到映像中。 如果可用的应用程序捆绑中法语 （法国） 资源包 （或任何其他语言），它将不会添加。

-   **规模和 DirectX (DXFL) 资源包**︰ 规模和 DirectX (DXFL) 的资源包取决于 Windows 设备的硬件配置。 由于当时无法知道的目标硬件类型运行 DISM 命令，所有规模和 DXFL 资源包都添加到在资源调配时图像。 有关开发比例资源与应用程序的详细信息，请参阅[扩展到像素密度 （Windows 应用商店应用程序） 的准则](http://go.microsoft.com/fwlink/?LinkId=320890)。

包含多个语言包的图像，应用程序资源文件包将添加到该图像的每种语言。 一旦第一个用户登录到已部署的图像电脑和用户选择的语言不匹配在 OOBE、 不适用的资源包、 （语言资源包、 比例资源包和 DXFL 资源包） 将删除用户配置文件设置。

例如，应用程序可能支持英语 （美国）、 法语 （法国） 和西班牙语 （西班牙） 语言。 如果该应用程序添加到映像使用英语 （美国） 和西班牙语 （西班牙） 语言包显示，只有英语 （美国） 和西班牙语 （西班牙） 资源包将添加到图像。 然后，如果用户第一次登陆，并在 OOBE，期间选择作为他们的操作系统语言的英语 （美国），西班牙语 （西班牙） 资源包将被删除的登录完成后。

**重要**  
如果您添加或从映像中删除语言包，您将更改适用性上下文可能会导致图像中保留的资源包的不正确或不完整的组。 当添加或删除语言包时，必须再一次向映像中添加所有的.appxbundle 软件包 （包括任何依赖关系的软件包和 Windows 应用商店的许可证文件）。 这样可以确保正确的资源包集资源调配。

## <a name="span-idlimitationsspanspan-idlimitationsspanspan-idlimitationsspanlimitations"></a><span id="Limitations"></span><span id="limitations"></span><span id="LIMITATIONS"></span>限制


-   操作系统不支持 Windows 8 应用程序上，则无法安装应用程序软件包 (.appx)。 不能至少不支持的操作系统上安装应用程序捆绑包 (.appxbundle) Windows 8.1 应用程序。 应用程序不支持在 WinPE 4.0 中，Windows Server 2012 服务器核心安装选项，或在任何 Windows 版本早于 Windows 8 和 Windows Server 2012。

    要安装并运行在 Windows Server 2012 的应用程序，您必须安装[桌面体验](http://go.microsoft.com/fwlink/?LinkId=247330)。

-   **/FolderPath**选项仅支持基于.appx 格式的应用程序软件包。

-   **/PackagePath**必须始终使用.appxbundle 软件包。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[DISM 是什么？](what-is-dism.md)

[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)

[部署映像服务和管理 (DISM) 命令行选项](deployment-image-servicing-and-management--dism--command-line-options.md)

[使用 DISM 的 sideload 应用程序](sideload-apps-with-dism-s14.md)
