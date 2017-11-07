---
author: Justinha
Description: "使用 DISM 使用资源调配包 (.ppkg) 文件。 例如，可以添加设置和 Windows 桌面应用程序与 Windows 10 或缩小您的 Windows 安装。"
ms.assetid: 205d296e-fced-429a-9e74-c445743ed7e9
MSHAttr: PreferredLib:/library/windows/hardware
title: "DISM 调配包 (.ppkg) 的命令行选项"
ms.openlocfilehash: 33ae13d4232b9ef4a1242d0522302fa1f2330039
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="span-iddismprovisioningpackagecommand-lineoptionsspandism-provisioning-package-ppkg-command-line-options"></a><span id="dism_provisioning_package_command-line_options"></span>DISM 调配包 (.ppkg) 的命令行选项


使用 DISM 使用资源调配包 (.ppkg) 文件。 例如，可以添加设置和 Windows 桌面应用程序与 Windows 10 或缩小您的 Windows 安装。

## <a name="span-idadd-provisioningpackagespanspan-idadd-provisioningpackagespanspan-idadd-provisioningpackagespanadd-provisioningpackage"></a><span id="_Add-ProvisioningPackage"></span><span id="_add-provisioningpackage"></span><span id="_ADD-PROVISIONINGPACKAGE"></span>**/ 添加-ProvisioningPackage**

添加资源调配到指定的图像包适用的负载。

语法︰

``` syntax
DISM.exe /Add-ProvisioningPackage /PackagePath:<package_path> [/CatalogPath:<path>]
```

示例：

``` syntax
DISM.exe /Image=C:\ /Add-ProvisioningPackage /PackagePath:C:\oem.ppkg
```

## <a name="span-idget-provisioningpackageinfospanspan-idget-provisioningpackageinfospanspan-idget-provisioningpackageinfospanget-provisioningpackageinfo"></a><span id="_Get-ProvisioningPackageInfo"></span><span id="_get-provisioningpackageinfo"></span><span id="_GET-PROVISIONINGPACKAGEINFO"></span>**/ Get ProvisioningPackageInfo**

获取资源调配包的信息。

语法︰

``` syntax
DISM.exe /Get-ProvisioningPackageInfo /PackagePath:<package_path>
```

示例：

``` syntax
DISM.exe /Image=C:\ /Get-ProvisioningPackageInfo /PackagePath:C:\oem.ppkg
```

## <a name="span-idapply-customdataimagespanspan-idapply-customdataimagespanspan-idapply-customdataimagespanapply-customdataimage"></a><span id="_Apply-CustomDataImage"></span><span id="_apply-customdataimage"></span><span id="_APPLY-CUSTOMDATAIMAGE"></span>**/ 应用-CustomDataImage**

Dehydrates 文件中的自定义数据图像以节省空间。 对于客户端版本，此包使用点击式恢复工具。

语法︰

``` syntax
/Apply-CustomDataImage /CustomDataImage:<path_to_image_file> /ImagePath:<target_drive> /SingleInstance
```


|   参数     |   说明     |
|-----------------|-------------------|
|   / CustomDataImage | 指定存储资源调配的包的位置。 |
| / ImagePath | 指定的驱动器，其中包含 Windows 映像。 DISM 扫描该驱动器有在此驱动器上的任何非系统文件，并将它们合并到配置包。 |
| / SingleInstance | DISM 捕获到一个压缩的供应包的非系统文件后，DISM 将驱动器指针添加到资源调配新压缩包，并删除原始文件。 这样一来，文件到系统中，仍可见但占用更少的驱动器空间。|


示例：

``` syntax
DISM.exe /Apply-CustomDataImage /CustomDataImage:C:\oem.ppkg /ImagePath:C:\ /SingleInstance
```

适用于︰ Windows 桌面版本 （家庭、 Pro、 企业和教育） 的 10 只。

 