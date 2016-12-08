---
author: Justinha
Description: "DISM 应用程序服务 (.msp) 命令行选项"
ms.assetid: 78ed3303-1e79-4257-ad04-d5f68d34b758
MSHAttr: PreferredLib:/library/windows/hardware
title: "DISM 应用程序服务 (.msp) 命令行选项"
ms.openlocfilehash: 8a936ccba97650e16da7156f52f4713fa419ce0e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="dism-application-servicing-msp-command-line-options"></a>DISM 应用程序服务 (.msp) 命令行选项


检查 Windows 安装程序应用程序修补程序 （.msp 文件） 的适用性，并查询您脱机映像安装的 Windows 安装程序的应用程序和应用程序修补程序 （.msp 文件） 有关的信息，可以在脱机映像上使用应用程序服务命令行选项。

有关使用部署映像服务和管理 (DISM) 与应用程序软件包的信息，请参阅[DISM 应用程序包 （.appx 或.appxbundle） 服务命令行选项](dism-app-package--appx-or-appxbundle--servicing-command-line-options.md)。

服务使用 DISM 的 Windows 映像的基本语法如下︰

**DISM.exe** **/图像︰**&lt;*路径\_图像\_目录*&gt; \[ **dism\_全局\_选项**\] {**服务\_选项**} \[ &lt;*服务\_参数*&gt;\]

列出 Windows 安装程序的应用程序和.msp 应用程序修补程序，并检查应用程序修补程序脱机 Windows 映像的适用性，下列服务选项有︰

**DISM.exe /Image:**&lt;*路径\_到\_目录*&gt; \[ **/Check-AppPatch** | **/Get-AppPatchInfo:** | **/Get-AppPatches** | **/Get-AppInfo** | **/Get-Apps**\]

## <a name="span-idapplicationservicingoptionsspanspan-idapplicationservicingoptionsspanspan-idapplicationservicingoptionsspanapplication-servicing-options"></a><span id="Application_servicing_options"></span><span id="application_servicing_options"></span><span id="APPLICATION_SERVICING_OPTIONS"></span>应用程序服务选项


本部分介绍如何使用每个应用程序服务选项。 这些选项不是区分大小写的。

### <a name="span-idget-helpspanspan-idget-helpspanspan-idget-helpspanget-help-"></a><span id="_Get-Help___"></span><span id="_get-help___"></span><span id="_GET-HELP___"></span>/ 获取帮助 /？

当某个程序包服务命令行选项后紧接着使用，将显示选项和参数的信息。 其他主题可能会在指定了映像之后变为可用。

示例：

**Dism /image:C:\\测试\\脱机 /Check-AppPatch /？**

### <a name="span-idcheck-apppatchpatchlocationpathtopatchmspspanspan-idcheck-apppatchpatchlocationpathtopatchmspspanspan-idcheck-apppatchpatchlocationpathtopatchmspspancheck-apppatch-patchlocationlt-pathtopatchmspgt"></a><span id="_Check-AppPatch__PatchLocation___path_to_patch.msp__"></span><span id="_check-apppatch__patchlocation___path_to_patch.msp__"></span><span id="_CHECK-APPPATCH__PATCHLOCATION___PATH_TO_PATCH.MSP__"></span>/ 检查 AppPatch /PatchLocation:&lt;路径\_到\_patch.msp&gt;

只有当 MSP 修补程序应用到脱机映像，则显示的信息。 必须指定 MSP 修补程序文件的路径。 可以指定多个修补程序文件。

示例：

**Dism /image:C:\\测试\\脱机 /Check-AppPatch /PatchLocation:C:\\测试\\MSIPatches\\MsiTestPatch1.msp /PatchLocation:C:\\测试\\MSIPatches\\MsiTestPatch2.msp**

### <a name="span-idget-apppatchinfopatchcodepatchcodeguidproductcodeproductcodeguidspanspan-idget-apppatchinfopatchcodepatchcodeguidproductcodeproductcodeguidspanspan-idget-apppatchinfopatchcodepatchcodeguidproductcodeproductcodeguidspanget-apppatchinfo-patchcodelt-patchcodeguidgt-productcodelt-productcodeguidgt"></a><span id="_Get-AppPatchInfo____PatchCode___patch_code_GUID_____ProductCode___product_code_GUID___"></span><span id="_get-apppatchinfo____patchcode___patch_code_guid_____productcode___product_code_guid___"></span><span id="_GET-APPPATCHINFO____PATCHCODE___PATCH_CODE_GUID_____PRODUCTCODE___PRODUCT_CODE_GUID___"></span>/ Get-AppPatchInfo: \[/PatchCode:&lt;修补程序\_代码\_GUID&gt; \] \[/ProductCode:&lt;产品\_代码\_GUID&gt;\]

显示有关已安装的筛选的 MSP 修补程序的详细的信息&lt;修补程序\_代码\_GUID&gt;和&lt;产品\_代码\_GUID&gt;。

如果指定**/PatchCode**选项，Windows 安装程序的所有应用程序修补程序应用于为都显示详细的信息。

如果指定**/ProductCode**选项，则将显示在指定的应用程序中的所有 MSP 修补程序的信息。

如果指定了**/PatchCode**和**/ProductCode**选项，则只有在该特定的修补程序应用于指定 Windows 安装程序的应用程序被显示信息。

使用**/Get-AppPatches**选项查找修补程序代码 GUID 和产品代码特定于该修补程序的 GUID。 使用**/Get-Apps**选项列出已安装的 Windows 安装服务应用程序的所有产品代码 Guid。

如果没有指定**/PatchCode**和**/ProductCode** ，所有安装 Windows 安装程序程序包和 MSP 修补程序的显示。

示例：

**Dism /image:C:\\测试\\/Get-AppPatchInfo 脱机**

**Dism /image:C:\\测试\\脱机 /Get-AppPatchInfo: /PatchCode: {B0B9997C-GUID 的 GUID 的 GUID-74D866BBDFFF}**

**Dism /image:C:\\测试\\脱机 /Get-AppPatchInfo: /ProductCode: {B0F9497C-GUID 的 GUID 的 GUID-74D866BBDF59}**

**Dism /image:C:\\测试\\脱机 /Get-AppPatchInfo: /PatchCode: {B0B9997C-GUID 的 GUID 的 GUID-74D866BBDFFF} /ProductCode: {B0F9497C-GUID 的 GUID 的 GUID-74D866BBDF59}**

### <a name="span-idget-apppatchesproductcodeproductcodeguidspanspan-idget-apppatchesproductcodeproductcodeguidspanspan-idget-apppatchesproductcodeproductcodeguidspanget-apppatches-productcodelt-productcodeguidgt"></a><span id="_Get-AppPatches____ProductCode___product_code_GUID___"></span><span id="_get-apppatches____productcode___product_code_guid___"></span><span id="_GET-APPPATCHES____PRODUCTCODE___PRODUCT_CODE_GUID___"></span>/ Get-AppPatches: \[/ProductCode:&lt;产品\_代码\_GUID&gt;\]

显示有关所有的应用 MSP 修补程序的安装在脱机映像上的所有应用程序的基本信息。 如果 GUID 指定的产品代码，显示有关指定 Windows 安装程序的应用程序中的所有修补程序的信息。

示例︰

**Dism /image:C:\\测试\\/Get-AppPatches 脱机**

**Dism /image:C:\\测试\\脱机 /Get-AppPatches /ProductCode: {B0F9497C-GUID 的 GUID 的 GUID-74D866BBDF59}**

### <a name="span-idget-appinfoproductcodeproductcodeguidspanspan-idget-appinfoproductcodeproductcodeguidspanspan-idget-appinfoproductcodeproductcodeguidspanget-appinfo-productcodelt-productcodeguidgt"></a><span id="_Get-AppInfo____ProductCode___product_code_GUID___"></span><span id="_get-appinfo____productcode___product_code_guid___"></span><span id="_GET-APPINFO____PRODUCTCODE___PRODUCT_CODE_GUID___"></span>/ Get AppInfo: \[/ProductCode:&lt;产品\_代码\_GUID&gt;\]

显示详细的信息的特定安装 Windows 安装应用程序。

使用**/Get-Apps**选项可以查找安装 Windows 安装程序的应用程序的 GUID。 如果未指定 GUID 的产品代码，脱机映像中安装的所有 Windows 安装应用程序时都显示信息。

示例︰

**Dism /image:C:\\测试\\/Get-AppInfo 脱机**

**Dism /image:C:\\测试\\脱机 /Get-AppInfo /ProductCode: {B0F9497C-GUID 的 GUID 的 GUID-74D866BBDF59}**

### <a name="span-idget-appsspanspan-idget-appsspanspan-idget-appsspanget-apps"></a><span id="_Get-Apps_"></span><span id="_get-apps_"></span><span id="_GET-APPS_"></span>/ 应用程序获取

显示有关脱机映像中的所有 Windows 安装应用程序的基本信息。

示例：

**Dism /image:C:\\测试\\/Get-Apps 脱机**

## <a name="span-idlimitationsspanspan-idlimitationsspanspan-idlimitationsspanlimitations"></a><span id="Limitations"></span><span id="limitations"></span><span id="LIMITATIONS"></span>限制


**/Get-AppPatches**和**/Get-AppPatchInfo**只适用于安装的修补程序 （.msp 文件）。

在确定 MSP 修补程序的适用性时，将显示只有 Windows 安装程序的应用程序所适用的修补程序。 一个修补程序可应用于多个已安装的应用程序和多个修补程序可以应用于一个应用程序。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[DISM 是什么？](what-is-dism.md)

[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)

[部署映像服务和管理 (DISM) 命令行选项](deployment-image-servicing-and-management--dism--command-line-options.md)

[DISM 应用程序包 （.appx 或.appxbundle） 服务命令行选项](dism-app-package--appx-or-appxbundle--servicing-command-line-options.md)

 

 






