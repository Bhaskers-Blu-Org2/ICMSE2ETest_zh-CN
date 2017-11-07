---
author: Justinha
Description: "DISM 操作系统程序包 （.cab 或.msu） 服务命令行选项"
ms.assetid: ddb5f223-1c65-4380-95eb-316918e880fc
MSHAttr: PreferredLib:/library/windows/hardware
title: "DISM 操作系统程序包 （.cab 或.msu） 服务命令行选项"
ms.openlocfilehash: 78d2240f0557b77875509a3c1ab5e55dda2b6aab
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="dism-operating-system-package-cab-or-msu-servicing-command-line-options"></a>DISM 操作系统程序包 （.cab 或.msu） 服务命令行选项


使用 DISM Windows.cab 或 Windows 更新独立安装程序 (.msu) 文件来安装或删除更新、 服务包、 语言包并启用或禁用 Windows 功能。 功能是核心操作系统的可选组件。 

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>语法

``` syntax
DISM.exe {/Image:<path_to_image_directory> | /Online} [dism_global_options] {servicing_option} [<servicing_argument>]
```

下列操作系统程序包服务选项可用于脱机映像︰

``` syntax
DISM.exe /Image:<path_to_image_directory> [/Get-Packages | /Get-PackageInfo | /Add-Package | /Remove-Package ] [/Get-Features | /Get-FeatureInfo | /Enable-Feature | /Disable-Feature ] [/Cleanup-Image]
```

下列操作系统程序包服务选项是可用于运行状态的操作系统︰

``` syntax
DISM.exe /Online [/Get-Packages | /Get-PackageInfo | /Add-Package | /Remove-Package ] [/Get-Features | /Get-FeatureInfo | /Enable-Feature | /Disable-Feature ] [/Cleanup-Image]
```

## <a name="span-idoperatingsystempackage-servicingoptionsspanspan-idoperatingsystempackage-servicingoptionsspanspan-idoperatingsystempackage-servicingoptionsspanoperating-system-package-servicing-options"></a><span id="Operating_system_package-servicing_options"></span><span id="operating_system_package-servicing_options"></span><span id="OPERATING_SYSTEM_PACKAGE-SERVICING_OPTIONS"></span>操作系统程序包服务选项

本部分介绍如何使用每个操作系统程序包服务选项。 这些选项不是区分大小写的。

### <a name="span-idget-helpspanspan-idget-helpspanspan-idget-helpspanget-help-"></a><span id="_Get-Help___"></span><span id="_get-help___"></span><span id="_GET-HELP___"></span>/ 获取帮助 /？

程序包服务命令行选项后紧接着使用，显示的选项和参数的信息。

其他主题可能会在指定了映像之后变为可用。

语法︰

``` syntax
Dism /Get-Help 
```

示例︰

``` syntax
Dism /Image:C:\test\offline /Add-Package /?
```

``` syntax
Dism /Online /Get-Packages /?
```

### <a name="span-idget-packagesformattablelistspanspan-idget-packagesformattablelistspanspan-idget-packagesformattablelistspanget-packages"></a><span id="_Get-Packages___Format__Table___List__"></span><span id="_get-packages___format__table___list__"></span><span id="_GET-PACKAGES___FORMAT__TABLE___LIST__"></span>/ 获取包 

显示有关映像中的所有程序包的基本信息。 使用 /Format:Table 或 /Format:List 参数将输出显示为一个表或列表。

语法︰

``` syntax
Dism /Get-Packages [/Format:{Table | List}]
```

示例︰

``` syntax
Dism /Image:C:\test\offline /Get-Packages
```

``` syntax
Dism /Image:C:\test\offline /Get-Packages /Format:Table
```

``` syntax
Dism /Online /Get-Packages
```

### <a name="span-idget-packageinfopackagenamenameinimagepackagepathpathtocabfilespanspan-idget-packageinfopackagenamenameinimagepackagepathpathtocabfilespanspan-idget-packageinfopackagenamenameinimagepackagepathpathtocabfilespanget-packageinfo"></a><span id="_Get-PackageInfo___PackageName___name_in_image_____PackagePath___path_to_cabfile__"></span><span id="_get-packageinfo___packagename___name_in_image_____packagepath___path_to_cabfile__"></span><span id="_GET-PACKAGEINFO___PACKAGENAME___NAME_IN_IMAGE_____PACKAGEPATH___PATH_TO_CABFILE__"></span>/ Get PackageInfo 

显示以.cab 文件形式提供的程序包的详细的信息。 可以指定仅.cab 文件。 不能使用此命令来获取.msu 文件的包信息。 / PackagePath 可以指向一个.cab 文件或文件夹。

您可以使用 /Get-Packages 选项查找图像中的包的名称，也可以指定.cab 文件的路径。 .Cab 文件的路径应指向该程序包的原始源，而不适用于文件在脱机映像上的安装位置。

语法︰

``` syntax
Dism /Get-PackageInfo {/PackageName:<name_in_image> | /PackagePath:<path_to_cabfile>}
```

示例︰

``` syntax
Dism /Image:C:\test\offline /Get-PackageInfo /PackagePath:C:\packages\package.cab
```

``` syntax
Dism /Image:C:\test\offline /Get-PackageInfo /PackageName:Microsoft.Windows.Calc.Demo~6595b6144ccf1df~x86~en~1.0.0.0
```

### <a name="span-idadd-packagepackagepathpathtocabfileignorecheckpreventpendingspanspan-idadd-packagepackagepathpathtocabfileignorecheckpreventpendingspanspan-idadd-packagepackagepathpathtocabfileignorecheckpreventpendingspanadd-package"></a><span id="_Add-Package__PackagePath___path_to_cabfile____IgnoreCheck_____PreventPending_"></span><span id="_add-package__packagepath___path_to_cabfile____ignorecheck_____preventpending_"></span><span id="_ADD-PACKAGE__PACKAGEPATH___PATH_TO_CABFILE____IGNORECHECK_____PREVENTPENDING_"></span>/ 添加程序包 

将指定的.cab 或.msu 包安装映像中。 仅当目标图像处于脱机状态，或者装载或应用支持.msu 包。 

可以在一个命令行添加多个程序包。 将检查每个程序包的适用性。 如果软件包不能应用于指定的图像，您将收到一条错误消息。 如果您想要处理而无需检查每个程序包的适用性的命令，请使用 /IgnoreCheck 参数。

使用 /PreventPending 选项可以跳过安装的包的包或 Windows 映像中有挂起的联机操作。 （在 Windows 8/Windows PE 4.0 中引入）。

/ PackagePath 可以指向︰

-   单个.cab 或.msu 文件。  

-   包含单个展开的.cab 文件的文件夹。

-   包含单个.msu 文件的文件夹。

-   包含多个.cab 或.msu 文件的文件夹。

**请注意**  
如果 /PackagePath 是指向包含其根部.cab 或.msu 文件的文件夹，所有子文件夹也将以递归方式为.cab 和.msu 文件签。

语法︰

``` syntax
Dism /Add-Package /PackagePath:<path_to_cabfile> [/IgnoreCheck] [/PreventPending]
```

示例︰

``` syntax
Dism /Image:C:\test\offline /LogPath:AddPackage.log /Add-Package /PackagePath:C:\packages\package.msu
```

``` syntax
Dism /Image:C:\test\offline /Add-Package /PackagePath:C:\packages\package1.cab /PackagePath:C:\packages\package2.cab /IgnoreCheck
```

``` syntax
Dism /Image:C:\test\offline /Add-Package /PackagePath:C:\test\packages\package.cab /PreventPending
```

### <a name="span-idremove-packagepackagenamenameinimagepackagepathpathtocabfilespanspan-idremove-packagepackagenamenameinimagepackagepathpathtocabfilespanspan-idremove-packagepackagenamenameinimagepackagepathpathtocabfilespanremove-package"></a><span id="_Remove-Package___PackageName___name_in_image_____PackagePath___path_to_cabfile__"></span><span id="_remove-package___packagename___name_in_image_____packagepath___path_to_cabfile__"></span><span id="_REMOVE-PACKAGE___PACKAGENAME___NAME_IN_IMAGE_____PACKAGEPATH___PATH_TO_CABFILE__"></span>/ 删除包 

从映像中删除指定的.cab 文件包。 可以指定仅.cab 文件。 您无法使用此命令删除.msu 文件。

**请注意**  
使用此命令从脱机映像中删除程序包将减小图像的大小。

您可以使用 /PackagePath 选项指向该程序包的原始源、 指定的 CAB 文件的路径或示图像中，可以按名称指定包。 使用 /Get-Packages 选项可以查找图像中的包的名称。

语法︰

``` syntax
/Remove-Package {/PackageName:<name_in_image> | /PackagePath:<path_to_cabfile>}
```

示例︰

``` syntax
Dism /Image:C:\test\offline /LogPath:C:\test\RemovePackage.log /Remove-Package /PackageName:Microsoft.Windows.Calc.Demo~6595b6144ccf1df~x86~en~1.0.0.0
```

``` syntax
Dism /Image:C:\test\offline /LogPath:C:\test\RemovePackage.log /Remove-Package /PackageName:Microsoft.Windows.Calc.Demo~6595b6144ccf1df~x86~en~1.0.0.0 /PackageName:Microsoft-Windows-MediaPlayer-Package~31bf3856ad364e35~x86~~6.1.6801.0
```

``` syntax
Dism /Image:C:\test\offline /LogPath:C:\test\RemovePackage.log /Remove-Package /PackagePath:C:\packages\package1.cab /PackagePath:C:\packages\package2.cab
```

### <a name="span-idget-featurespackagenamenameinimagepackagepathpathtocabfileformattablelistspanspan-idget-featurespackagenamenameinimagepackagepathpathtocabfileformattablelistspanspan-idget-featurespackagenamenameinimagepackagepathpathtocabfileformattablelistspanget-features"></a><span id="_Get-Features___PackageName___name_in_image_____PackagePath___path_to_cabfile_____Format__Table___List__"></span><span id="_get-features___packagename___name_in_image_____packagepath___path_to_cabfile_____format__table___list__"></span><span id="_GET-FEATURES___PACKAGENAME___NAME_IN_IMAGE_____PACKAGEPATH___PATH_TO_CABFILE_____FORMAT__TABLE___LIST__"></span>/ Get 功能 

在包中显示有关所有功能 （包括可选的 Windows 基础功能的操作系统组件） 的基本信息。 您可以使用 /Get-Features 选项查找图像中的包的名称，也可以指定该程序包的原始源的路径。 如果您不指定包名称或路径，则将列出映像中的所有功能。 / PackagePath 可以指向一个.cab 文件或文件夹。

功能的名称是区分大小写如果处理非 Windows 8 的 Windows 映像。

使用 /Format:Table 或 /Format:List 参数将输出显示为一个表或列表。

语法︰

``` syntax
/Get-Features {/PackageName:<name_in_image> | /PackagePath:<path_to_cabfile>} [/Format:{Table | List}]
```

示例︰

``` syntax
Dism /Image:C:\test\offline /Get-Features
```

``` syntax
Dism /Image:C:\test\offline /Get-Features /Format:List
```

``` syntax
Dism /Image:C:\test\offline /Get-Features /PackageName:Microsoft.Windows.Calc.Demo~6595b6144ccf1df~x86~en~1.0.0.0
```

``` syntax
Dism /Image:C:\test\offline /Get-Features /PackagePath:C:\packages\package1.cab
```

### <a name="span-idget-featureinfofeaturenamenameinimagepackagenamenameinimagepackagepathpathtocabfilespanspan-idget-featureinfofeaturenamenameinimagepackagenamenameinimagepackagepathpathtocabfilespanspan-idget-featureinfofeaturenamenameinimagepackagenamenameinimagepackagepathpathtocabfilespanget-featureinfo"></a><span id="_Get-FeatureInfo__FeatureName__name_in_image____PackageName___name_in_image_____PackagePath___path_to_cabfile___"></span><span id="_get-featureinfo__featurename__name_in_image____packagename___name_in_image_____packagepath___path_to_cabfile___"></span><span id="_GET-FEATUREINFO__FEATURENAME__NAME_IN_IMAGE____PACKAGENAME___NAME_IN_IMAGE_____PACKAGEPATH___PATH_TO_CABFILE___"></span>/ Get FeatureInfo

显示有关某个功能的详细的信息。 您必须使用 /FeatureName。 功能的名称是区分大小写如果处理 Windows 10 或 Windows 之外的 Windows 映像 8.x。 可以使用 /Get-Features 选项以查找图像中的功能的名称。

/ 包名和 /PackagePath 是可选的可以用于包中查找特定的功能。

语法︰

``` syntax
/Get-FeatureInfo /FeatureName:<name_in_image> [{/PackageName:<name_in_image> | /PackagePath:<path_to_cabfile>}]
```

示例︰

``` syntax
Dism /Image:C:\test\offline /Get-FeatureInfo /FeatureName:Hearts
```

``` syntax
Dism /Image:C:\test\offline /Get-FeatureInfo /FeatureName:Hearts /PackagePath:C:\packages\package.cab
```

### <a name="span-idenable-featurefeaturenamenameinimagepackagenamenameinimagesourcesourcelimitaccessallspanspan-idenable-featurefeaturenamenameinimagepackagenamenameinimagesourcesourcelimitaccessallspanspan-idenable-featurefeaturenamenameinimagepackagenamenameinimagesourcesourcelimitaccessallspanenable-feature"></a><span id="_Enable-Feature__FeatureName___name_in_image___PackageName___name_in_image_____Source___source_____LimitAccess___All_"></span><span id="_enable-feature__featurename___name_in_image___packagename___name_in_image_____source___source_____limitaccess___all_"></span><span id="_ENABLE-FEATURE__FEATURENAME___NAME_IN_IMAGE___PACKAGENAME___NAME_IN_IMAGE_____SOURCE___SOURCE_____LIMITACCESS___ALL_"></span>/ 启用的功能 

启用或更新映像中指定的功能。 您必须使用 /FeatureName 选项。 功能的名称是区分大小写如果处理非 Windows 8 的 Windows 映像。 使用 /Get-Features 选项可以查找图像中的功能的名称。

您可以共享同一个父包的功能的一个命令行中多次指定 /FeatureName 选项。

不需要指定使用 /PackageName 选项，如果包是一个 Windows 基础包的包名称。 否则，使用 /PackageName 来指定功能的父包。

您可以还原并启用以前已从图像中移除功能。 /Source 参数用于指定文件恢复功能所需的位置。 这些文件的来源可以由 Windows 文件夹中装入图像，例如 c:\test\mount\Windows。 您还可以用作 Windows 并排放置文件夹的源的文件，例如 z:\sources\SxS。

如果您指定多个 /Source 参数，从发现和位置的其余部分将被忽略的第一个位置收集文件。 如果不指定 /Source 功能已被移走，用于在注册表中的默认位置，或者，对于联机映像，使用 Windows 更新 (WU)。

使用 /LimitAccess 来防止 DISM 联系 WU 的在线图像。

使用/所有要启用所有父功能的指定功能。

/Source，/LimitAccess，和所有参数都可与 Windows 10，Windows/8.x 和 4.0 以上的 Windows PE 映像。

语法︰

``` syntax
/Enable-Feature /FeatureName:<name_in_image> [/PackageName:<name_in_image>] [/Source: <source>] [/LimitAccess] [/All]
```

示例︰

``` syntax
Dism /Online /Enable-Feature /FeatureName:Hearts /All
```

``` syntax
Dism /Online /Enable-Feature /FeatureName:Calc /Source:c:\test\mount\Windows /LimitAccess
```

``` syntax
Dism /Image:C:\test\offline /Enable-Feature /FeatureName:Calc /PackageName:Microsoft.Windows.Calc.Demo~6595b6144ccf1df~x86~en~1.0.0.0
```

### <a name="span-iddisable-featurefeaturenamenameinimagepackagenamenameinimageremovespanspan-iddisable-featurefeaturenamenameinimagepackagenamenameinimageremovespanspan-iddisable-featurefeaturenamenameinimagepackagenamenameinimageremovespandisable-feature"></a><span id="_Disable-Feature__FeatureName___name_in_image____PackageName___name_in_image_____Remove_"></span><span id="_disable-feature__featurename___name_in_image____packagename___name_in_image_____remove_"></span><span id="_DISABLE-FEATURE__FEATURENAME___NAME_IN_IMAGE____PACKAGENAME___NAME_IN_IMAGE_____REMOVE_"></span>/ 禁用功能 

禁用映像中指定的功能。 您必须使用 /FeatureName 选项。 功能的名称是区分大小写如果处理非 Windows 8 的 Windows 映像。 使用 /Get-Features 选项可以查找图像中的功能的名称。

您可以在同一父包中的功能的一个命令行中多次指定 /FeatureName。

您不需要指定包名称使用 /PackageName 选项，如果包是 Windows 基础程序包。 否则，使用 /PackageName 来指定功能的父包。

使用 /Remove 但不从图像中移除的功能清单中移除一项功能。 仅可以使用此选项可以与 Windows 10，Windows 使用 8.x 和 4.0 以上的 Windows PE 映像。 "删除"时可以使用 /Get-FeatureInfo 来显示功能的详细信息以及可以恢复和启用 /Enable-Feature 使用 /Source 选项将列出功能。

语法︰

``` syntax
/Disable-Feature /FeatureName:<name_in_image> [/PackageName:<name_in_image>] [/Remove]
```

示例︰

``` syntax
*Dism /Online /Disable-Feature /FeatureName:Hearts
```

``` syntax
Dism /Image:C:\test\offline /Disable-Feature /FeatureName:Calc /PackageName:Microsoft.Windows.Calc.Demo~6595b6144ccf1df~x86~en~1.0.0.0
```

### <a name="span-idcleanup-imagerevertpendingactionsspsupersededhidespstartcomponentcleanupresetbaseanalyzecomponentstorecheckhealthscanhealthrestorehealthsourcefilepathlimitaccessspanspan-idcleanup-imagerevertpendingactionsspsupersededhidespstartcomponentcleanupresetbaseanalyzecomponentstorecheckhealthscanhealthrestorehealthsourcefilepathlimitaccessspanspan-idcleanup-imagerevertpendingactionsspsupersededhidespstartcomponentcleanupresetbaseanalyzecomponentstorecheckhealthscanhealthrestorehealthsourcefilepathlimitaccessspancleanup-image"></a><span id="_Cleanup-Image___RevertPendingActions____SPSuperseded___HideSP_____StartComponentCleanup___ResetBase_____AnalyzeComponentStore____CheckHealth____ScanHealth____RestoreHealth___Source___filepath_____LimitAccess__"></span><span id="_cleanup-image___revertpendingactions____spsuperseded___hidesp_____startcomponentcleanup___resetbase_____analyzecomponentstore____checkhealth____scanhealth____restorehealth___source___filepath_____limitaccess__"></span><span id="_CLEANUP-IMAGE___REVERTPENDINGACTIONS____SPSUPERSEDED___HIDESP_____STARTCOMPONENTCLEANUP___RESETBASE_____ANALYZECOMPONENTSTORE____CHECKHEALTH____SCANHEALTH____RESTOREHEALTH___SOURCE___FILEPATH_____LIMITACCESS__"></span>/ 清理图像

执行清理或恢复操作在图像上。 / 可与 Windows 10、 Windows 8.1 和 Windows PE 映像 5.0 以上 AnalyzeComponentStore 和 /ResetBase。 开头第 10 Windows 版本 1607，可以在 /ResetBase 中指定 /Defer。 但我们极力建议您**只**将 /Defer 用作其中 DISM /Resetbase 需要 30 分钟以上才能完成的工厂中的一个选项。 / 可与 Windows 10，Windows StartComponentCleanup 8.x 和 4.0 以上的 Windows PE 映像。 / 与 Windows 10，Windows 可以使用 CheckHealth、 /ScanHealth、 /RestoreHealth、 /Source 和 /LimitAccess 8.x 和 4.0 以上的 Windows PE 映像。 / 处理的是早于 Windows 7 Service Pack 1 (SP1) 映像的 Windows 版本时，无法使用 HideSP 和 /SPSuperseded。

**提示**  
若要确定上次运行 /ResetBase 选项，请检查此注册表路径下的 LastResetBase_UTC 注册表项︰

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Component 基于服务

语法︰

``` syntax
/Cleanup-Image {/RevertPendingActions | /SPSuperseded [/HideSP] | /StartComponentCleanup [/ResetBase [/Defer]] | /AnalyzeComponentStore | /CheckHealth | /ScanHealth | /RestoreHealth [/Source: <filepath>] [/LimitAccess]}
```

|   参数     |   说明     |
|-----------------|-------------------|
| / RevertPendingActions | 如果您遇到启动故障，可以使用 /RevertPendingActions 选项来尝试恢复系统。 该操作将恢复从以前的服务操作的所有挂起的操作，因为这些操作可能会启动失败的原因。 在正在运行的操作系统 Windows PE 或 Windows 恢复环境 (Windows RE) 图像不支持 /RevertPendingActions 选项。 重要提示︰ 您应使用 /RevertPendingActions 选项仅在未启动的 Windows 映像上的系统恢复方案中。|
| SPSuperseded | 移除任何服务包的安装过程中创建的备份文件。 使用 /HideSP 来防止该 service pack 安装更新控制面板中列出。 /SPSuperseded 操作完成后无法卸载 service pack。 |
| / StartComponentCleanup | 清理被取代的组件，而组件存储将减小。 使用 /ResetBase 来重置基取代的组件，它们可以进一步减少组件存储大小。 安装的 Windows 更新无法卸载之后使用 /ResetBase 选项运行 /StartComponentCleanup。 使用 /ResetBase /Defer 将推迟到下一步的自动维护长时间运行清理操作。|
| / AnalyzeComponentStore | 创建组件存储的报表。 有关报表以及如何使用在报告中提供的信息的详细信息，请参阅[确定 WinSxS 文件夹的实际大小](determine-the-actual-size-of-the-winsxs-folder.md)。 |
| / CheckHealth | 检查是否图像被标记为损坏的故障过程，以及是否可以修复损坏。 |
| / ScanHealth | 扫描组件损坏存储的图像。 此操作将需要几分钟。  |
| / RestoreHealth | 扫描组件损坏存储的图像，然后自动执行修复操作。 此操作将需要几分钟。 |
| / 源 | 与 /RestoreHealth 一起使用，以指定的已知适用的版本，可用于修复，例如对已装载的映像的 Windows 目录的路径的文件的位置。|
| / LimitAccess | 防止 DISM 联系在线图像修复 Windows 更新。 | 

示例︰

``` syntax
Dism /Image:C:\test\offline /Cleanup-Image /RevertPendingActions
```

``` syntax
Dism /Image:C:\test\offline /Cleanup-Image /SPSuperseded /HideSP
```

``` syntax
Dism /Online /Cleanup-Image /ScanHealth
```

``` syntax
Dism /Online /Cleanup-Image /RestoreHealth /Source:c:\test\mount\windows /LimitAccess
```

若要了解详细信息，请参阅[修复 Windows 映像](repair-a-windows-image.md)。

## <a name="span-idlimitationsspanspan-idlimitationsspanspan-idlimitationsspanlimitations"></a><span id="Limitations"></span><span id="limitations"></span><span id="LIMITATIONS"></span>限制


-   当您在脱机映像中安装包时，该包的状态是"安装挂起"由于挂起的联机操作。 换句话说，引导映像和处理联机操作时，将安装包。 如果请求的后续操作，它们无法处理直到完成以前挂起的联机操作。 添加与 /AddPackage 在有挂起的联机操作时跳过包的安装包时，可以使用 /PreventPending 选项。
-   某些软件包需要首先安装其他程序包。 不应假定将满足依赖关系。 如果存在依存关系要求，您应使用答案文件来安装必需的软件包。 通过将答案文件传递给 DISM，多个程序包可以按正确的顺序安装。 这是安装多个程序包的首选的方法。 有关详细信息，请参阅[添加或删除程序包脱机使用 DISM](add-or-remove-packages-offline-using-dism.md)。
-   在命令行中列出的顺序安装软件包。
-   当使用 DISM 列出 Windows PE 映像中的可选组件，可选组件将始终被列为挂起即使服务操作已成功完成。 这是设计使然，并且需要您执行任何其他操作。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[DISM 是什么？](what-is-dism.md)

[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)

[部署映像服务和管理 (DISM) 命令行选项](deployment-image-servicing-and-management--dism--command-line-options.md)

 



