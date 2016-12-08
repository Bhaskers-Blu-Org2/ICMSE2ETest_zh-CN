---
author: Justinha
Description: "DISM 驱动程序服务 (.inf) 命令行选项"
ms.assetid: 39beacf3-7982-477c-93f6-4c6883efd69e
MSHAttr: PreferredLib:/library/windows/hardware
title: "DISM 驱动程序服务 (.inf) 命令行选项"
ms.openlocfilehash: f1857e018eff1397fee3868c5b9f49770d316e44
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="dism-driver-servicing-inf-command-line-options"></a>DISM 驱动程序服务 (.inf) 命令行选项


使用 DISM INF 样式的驱动程序来添加、 删除或列出为联机或脱机 Windows 映像 (.wim) 的驱动程序。 不支持 Microsoft Windows Installer 或其他类型 （如.exe 文件） 的驱动程序软件包。

您可以指定一个目录位于驱动程序 INF 文件，或可以通过指定 INF 文件的名称来指向驱动程序的位置。

服务使用 DISM 的 Windows 映像的基本语法如下︰

**DISM.exe** {**/图像︰**&lt;*路径\_到\_图像\_目录*&gt; | **/Online**} \[ **dism\_全局\_选项**\] {**服务\_选项**} \[ &lt;*服务\_参数*&gt;\]

下列驱动程序服务选项可用于脱机映像。

**DISM.exe /image:**&lt;*路径\_到\_图像\_目录*&gt; \[ **/Get-Drivers** | **/Get-DriverInfo** | **/Add-Driver** | **/Remove-Driver** | **/Export-Driver**\]

下列驱动程序服务选项可用于正在运行的操作系统。

**DISM.exe / 在线**\[ **/Get-Drivers** | **/Get-DriverInfo** | **/Export-Driver**\]

下表描述了可以如何使用每个驱动程序服务选项。 这些选项不是区分大小写的。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">选项/参数</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>选项︰ <strong>/Get-Help /？</strong></p></td>
<td align="left"><p>驱动程序服务命令行选项后紧接着使用，显示的选项和参数的信息。 其他主题可能会在指定了映像之后变为可用。</p>
<p>示例︰</p>
<p><strong>Dism /image:C:\test\offline /Add-Driver /？</strong></p>
<p><strong>Dism 在线 / /Get-Drivers /？</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>选项︰ <strong>/Get-Drivers</strong></p>
<p>参数︰</p>
<p><strong>/All</strong></p>
<p><strong>/ 格式: {表 |列表}</strong></p></td>
<td align="left"><p>显示有关联机或脱机映像中的驱动程序包的基本信息。</p>
<p>默认情况下，将列出仅第三方驱动程序。 使用<strong>/all</strong>参数来显示有关默认驱动程序和第三方驱动程序的信息。 使用<strong>/Format:Table</strong>或<strong>/Format:List</strong>参数将输出显示为一个表或列表。</p>
<p>如果您指向图像，您可以确定驱动程序位于图像的状态 （已安装或转移） 的驱动程序的补充。</p>
<p>示例：</p>
<p><strong>Dism /image:C:\test\offline /Get-Drivers</strong></p>
<p><strong>Dism / 在线 /Get-Drivers</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>选项︰ <strong>/Get-DriverInfo</strong></p>
<p>参数︰</p>
<p><strong>/ 驱动程序︰</strong>&lt;<em>installed_INF_FileName</em>&gt;</p>
<p><strong>/ 驱动程序︰</strong>&lt;<em>path_to_driver.inf</em>&gt;</p></td>
<td align="left"><p>显示有关特定驱动程序包的详细的信息。</p>
<p>您可以指向该图像，或者尚未安装中安装的 INF 文件。 在设备驱动程序存储区中，可以指定卸载的驱动程序或第三方驱动程序的名称。 在驱动程序存储区中安装的第三方驱动程序将被命名为 Oem0.inf、 Oem1.inf，等等。 这被称为已发布的名称。</p>
<p>通过多次使用了<strong>/driver</strong>选项，可以在命令行上指定多个驱动程序。</p>
<p>示例：</p>
<p>首先，使用<strong>/Get-Drivers</strong>选项，以便您可以确定驱动程序 INF 文件。 然后运行下面的命令︰</p>
<p><strong>Dism /image:C:\test\offline /Get-DriverInfo /driver:&lt;path_to_driver.inf&gt;</strong></p>
<p><strong>Dism / 在线 /Get-DriverInfo /driver:C:\test\drivers\usb\usb.inf</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>选项︰ <strong>/Add-Driver</strong></p>
<p>参数︰</p>
<p><strong>/ 驱动程序︰</strong>&lt;<em>folder_containing_INF</em>&gt;</p>
<p><strong>/ 驱动程序︰</strong>&lt;<em>path_to_driver.inf</em>&gt;</p>
<p><strong>/ 递归</strong></p>
<p><strong>/ ForceUnsigned</strong></p></td>
<td align="left"><p>脱机 Windows 映像中添加第三方驱动程序包。</p>
<p>当您使用<strong>/Driver</strong>选项指向一个文件夹时，将忽略无效驱动程序包的 INF 文件。 这些文件报告在控制台上运行该命令，并在日志文件中包括警告。 您不会收到一条错误消息。</p>
<p>如果您指向路径并使用<strong>/recurse</strong>选项，所有子文件夹会询问要添加的驱动程序。</p>
<p>为进行测试，可以使用<strong>/ForceUnsigned</strong>添加未签名驱动程序，并覆盖在基于 X64 的计算机上安装的驱动程序必须具有数字签名的要求。 有关驱动程序签名要求的详细信息，请参阅[设备驱动程序和部署概述](device-drivers-and-deployment-overview.md)。</p>
<p>示例︰</p>
<p><strong>Dism /image:C:\test\offline /Add-Driver /driver:C:\test\drivers\</strong></p>
<p><strong>Dism /image:C:\test\offline /Add-Driver /driver:C:\test\drivers /recurse</strong></p>
<p><strong>Dism /image:C:\test\offline /Add-Driver /driver:C:\test\drivers\mydriver.inf</strong></p>
<p><strong>Dism /image:C:\test\offline /Add-Driver /driver:C:\test\drivers\mydriver.inf /ForceUnsigned</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>选项︰ <strong>/Remove-Driver</strong></p>
<p>参数︰</p>
<p><strong>/ 驱动程序︰</strong>&lt;<em>published_name</em>&gt;</p></td>
<td align="left"><p>从脱机映像中删除第三方驱动程序。</p>
<p>添加第三方驱动程序，它们被命名为 Oem0.inf、 Oem1.inf，等等。 您必须指定&lt;<em>发布名称</em>&gt; (例如，Oem1.inf) 来删除该驱动程序。 您不能删除默认驱动程序。</p>
<div class="alert">
<strong>警告</strong>  
<p>删除启动关键驱动程序程序包可以使脱机 Windows 映像无法启动。</p>
</div>
<div>
 
</div>
<p></p>
<p>通过多次使用了<strong>/Driver</strong>选项，可以在命令行上指定多个驱动程序。</p>
<p>示例︰</p>
<p><strong>Dism /image:C:\test\offline /Remove-Driver /driver:oem1.inf</strong></p>
<p><strong>Dism /image: C:\test\offline /Remove-Driver /driver:oem1.inf /driver:oem2.inf</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>选项︰ <strong>/Export-Driver</strong></p>
<p>参数︰</p>
<p><strong>/ 目标︰</strong>&lt;<em>path_to_destination_folder</em>&gt;</p></td>
<td align="left"><p>将从 Windows 映像的所有第三方驱动程序包导出到的目标路径。 通过运行<strong>DISM 添加驱动程序</strong>命令之前，然后可以被导出驱动程序注入到脱机映像。 此命令是用于 Windows 8.1 更新的新功能。</p>
<p>示例︰</p>
<p><strong>DISM / 在线导出驱动程序 /Destination:C:\destpath</strong></p>
<p><strong>DISM /Image:C\test\offline 导出驱动程序 /Destination:C:\destpath</strong></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idlimitationsspanspan-idlimitationsspanspan-idlimitationsspanlimitations"></a><span id="Limitations"></span><span id="limitations"></span><span id="LIMITATIONS"></span>限制


-   驱动程序服务命令仅支持.inf 文件。 不支持 Windows 安装程序或其他驱动程序软件包类型 （如.exe 文件）。
-   在命令行中列出的顺序安装驱动程序。 在下面的示例、 1.inf、 2.inf 和 3.将在命令行中列出的顺序安装 inf。

    ``` syntax
    Dism /Image:C:\test\offline /Add-Driver /Driver:C:\test\drivers\1.inf /Driver:C:\test\drivers\2.inf /Driver:C:\test\drivers\3.inf
    ```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[DISM 是什么？](what-is-dism.md)

[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)

[部署映像服务和管理 (DISM) 命令行选项](deployment-image-servicing-and-management--dism--command-line-options.md)

 

 






