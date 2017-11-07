---
author: Justinha
Description: "DISM 图像管理命令行选项"
ms.assetid: a6382d83-5748-4b08-9d9a-46ff576bac54
MSHAttr: PreferredLib:/library/windows/hardware
title: "DISM 图像管理命令行选项"
ms.openlocfilehash: 82ddf698b02150b0bdc0333f48a8d5c3d12ac671
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="dism-image-management-command-line-options"></a>DISM 图像管理命令行选项


部署映像服务和管理 (DISM.exe) 装载 Windows 映像 (.wim) 文件或虚拟硬盘 （.vhd 或.vhdx） 来处理。 您还可以使用 DISM 图像管理命令列出图像索引号，以验证您要装载的映像的体系结构、 添加图像、 应用映像、 捕获映像和删除图像。 更新映像后，您必须卸载它，要么提交或放弃所做的更改。

本主题讨论 DISM 命令与图像管理相关。 若要查看其他命令行选项，请参阅[部署映像服务和管理 (DISM) 命令行选项](deployment-image-servicing-and-management--dism--command-line-options.md)。 有关 DISM 的常见方案的详细信息，请参阅[DISM 是什么？](what-is-dism.md)。

除了命令行工具，DISM 是可通过使用 Windows PowerShell。 有关详细信息，请参阅[部署映像服务管理 (DISM) 在 Windows PowerShell 的 Cmdlet](http://go.microsoft.com/fwlink/?LinkId=239926)。

可以使用以下命令以装载、 卸载、 捕获、 添加和删除及查询.wim、.vhd 文件和.vhdx 文件。 这些选项不是区分大小写的。

## <a name="append-image"></a>/ 附加的图像

.Wim 文件中添加了附加图像。 **/Append-Image**比较新的由**/ImageFile**参数，指定现有.wim 文件中的资源文件，并存储只有唯一的每个文件的一个副本，以便每个文件只能一次捕获。 .Wim 文件可以有一个已分配的压缩类型。 因此，您只可以具有相同的压缩类型附加文件。

此命令行选项不适用于虚拟硬盘 (VHD) 文件。

**重要**  

确保您有足够的磁盘空间用于运行的**/Append-Image**选项。 如果您运行磁盘空间不足而被追加图像，可能会破坏.wim 文件。

语法︰

``` syntax
DISM.exe /Append-Image /ImageFile:<path_to_image_file> /CaptureDir:<source_directory> /Name:<image_name> [/Description:<image_description>] [/ConfigFile:<configurtion_file.ini>] [/Bootable] /WIMBoot [/CheckIntegrity] [/Verify] [/NoRpFix]
```

|   参数     |   说明     |
|-----------------|-------------------|
|   / WIMBoot | 使用 /WIMBoot 附加图像与 Windows 图像文件 (WIMBoot) 的启动配置。 这仅适用于 Windows 8.1 映像被捕获或导出为 WIMBoot 的文件。 在 Windows 10 中不支持此功能。|
| / ConfigFile | 指定列出排除项的图像捕获和压缩命令的配置文件的位置。 有关详细信息，请参阅[DISM 配置列表和 WimScript.ini 文件](dism-configuration-list-and-wimscriptini-files-winnext.md)。 |
| / 引导 | 标记为可引导映像的卷映像。 此参数是只可用于 Windows 预安装环境 (WinPE) 图像。 .Wim 文件中只有一个卷映像标记为可引导映像。|
| / CheckIntegrity | 检测到并跟踪.wim 文件损坏时用于捕获，卸载、 导出和提交操作。 / 如果 DISM 检测到.wim 文件已损坏与应用和装载操作一起使用时，CheckIntegrity 停止操作。 |
| / 验证 |  检查错误和文件复制。 |
| / NoRpFix  | 禁用该重分析点标记修补程序。 重新分析点是一个包含指向另一个文件在文件系统上的文件。 如果没有指定 /NoRpFix，则解析为路径由 /ImageFile 指定的值以外的重分析点不会被捕获。|

示例：

``` syntax
Dism /Append-Image /ImageFile:install.wim /CaptureDir:D:\ /Name:Drive-D
```

## <a name="apply-image"></a>/ 应用的图像

对于 WIM，此命令仅适用 Windows 映像文件 (.wim) 或拆分窗口的图像 (.swm) 文件复制到指定的分区。 开头第 10 Windows 版本 1607，DISM 可以应用来捕获扩展的属性 (EA)。

对于 FFU，此命令适用于指定的驱动器完全闪存更新 (.ffu) 图像。 它不支持的映像应用从虚拟硬盘 (.vhdx) 文件，虽然您可以使用此命令将完整图像应用到 VHD。 FFU 仅适用于 Windows 10。

虽然您可以使用此命令将映像应用于.vhdx 文件已被附加、 分区，并格式化该选项不支持从虚拟硬盘 (VHD) 应用映像。

如果 Dism /Apply-Image 失败与错误代码 5，并且您使用 Windows 10 版本 1607年与 Windows 子系统为 Linux (WSL) 功能，请参阅[知识库文章 319598](https://support.microsoft.com/kb/3179598)。

WIM 参数︰

``` syntax
DISM.exe /Apply-Image /ImageFile:<path_to_image_file> [/SWMFile:<pattern>] /ApplyDir:<target_directory> {/Index:< image_index> | /Name:<image_name>} [/CheckIntegrity] [/Verify] [/NoRpFix] [/ConfirmTrustedFile] [/WIMBoot (deprecated)] [/Compact] [/EA]
```

FFU 的参数

``` syntax
DISM.exe /Apply-Image /ImageFile:<path_to_image_file> /ApplyDrive:<target_drive> [/SFUFile:<pattern>] [/SkipPlatformCheck]
```

|   参数     |   说明     |
|-----------------|-------------------|
| / CheckIntegrity | 检测到并跟踪.wim 文件损坏时用于捕获，卸载、 导出和提交操作。 / 如果 DISM 检测到.wim 文件已损坏与应用和装载操作一起使用时，CheckIntegrity 停止操作。 |
| / 验证 | 检查错误和文件复制。 |
| / NoRpFix | 禁用该重分析点标记修补程序。 重新分析点是一个包含指向另一个文件在文件系统上的文件。 如果没有指定 /NoRpFix，则解析为指定 /ImageFile 的值以外的路径的重新分析点不会被捕获。 |
| / SWMFile | 使您能够引用拆分.wim 文件 (SWMs)。 *模式*是命名模式和拆分文件的位置。 您还可以指定通配符。 例如，"E:\image\install.swm"将 E:\image 中的拆分文件的所有目录命名为 install1.swm、 install2.swm，等等。 |
| / ConfirmTrustedFile | 验证受信任的 Windows 10、 Windows 8.1 或 Windows 8 上的桌面图像。 此选项只能至少运行的计算机上运行 WinPE 4.0。 在使用 /Apply-Image 使用 WinPE 中的 /ConfirmTrustedFile 选项时，始终指定指向物理介质位置的 /ScratchDir 选项。 这可以确保始终将使用短文件名。 [DISM 命令行语法的全局选项](dism-global-options-for-command-line-syntax.md)的默认行为的 /ScratchDir 选项的详细信息，请参见 开头第 10 Windows 版本 1607，您可以使用 /EA 应用扩展的属性。  |
|   / WIMBoot | 使用 /WIMBoot 附加图像与 Windows 图像文件 (WIMBoot) 的启动配置。 这仅适用于 Windows 8.1 映像被捕获或导出为 WIMBoot 的文件。 在 Windows 10 中不支持此功能。|
| / 压缩 | 将图像在紧凑模式下，节省的驱动器空间。 将替换 WIMBoot。 （家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 只。 | 
| /EA      | Windows 10，1607年版本中的新增功能。 应用扩展的属性。 |
| / ApplyDrive  | 指定的逻辑驱动器，使用 DeviceID。 要从命令行获取设备 ID，请键入"wmic 磁盘驱动器列表短暂"。 注意︰ VHD 可能显示其中包含名称"PhysicalDrive"中的说明，例如， \.\PhysicalDrive2。|
| / SFUFile  | 使用 /SFUFile 来引用拆分 FFU 文件 (SFUs)。 *模式*是命名模式和拆分文件的位置。 |
|  / SkipPlatformCheck | 如果应用 FFU 文件针对于执行该应用程序的设备以外的设备，请使用 /SkipPlatformCheck。 特殊的 FFU 文件是必需的。 |

示例︰

``` syntax
Dism /apply-image /imagefile:install.wim /index:1 /ApplyDir:D:\
```

``` syntax
Dism /apply-image /imagefile:install.swm /swmfile:install.swm /index:1 /applydir:D:
```

``` syntax
DISM.exe /Apply-Ffu /ImageFile:flash.ffu /ApplyDrive:\\.\PhysicalDrive0
```

``` syntax
DISM.exe /Apply-Ffu /ImageFile:flash.sfu /SFUFile:flash*.sfu /ApplyDrive:\\.\PhysicalDrive0
```

## <a name="capture-customimage"></a>/ 捕获-CustomImage

捕获基于特定的 install.wim 文件到一个新文件、 custom.wim WIMBoot 图像的增量文件更改。 不能捕获空目录。 捕获的文件会被转换为指针文件。 Custom.wim 位于相同的文件夹旁边的 install.wim。

**重要**

- / 捕获 CustomImage 仅捕获自定义文件。 它不能用于捕获到新 WIM 的安装文件。
- 将 install.wim 和 custom.wim 文件放在一起。 不切换 custom.wim 文件或 install.wim 文件。
- 您可以一次只捕获自定义图像。 不要删除或重新 custom.wim 捕获捕获增量文件更改后。

语法︰ 

``` syntax
Dism /Capture-CustomImage /CaptureDir:<source_directory> [/ConfigFile:<configuration_file.ini>] [/CheckIntegrity] [/Verify] [/ConfirmTrustedFile]
```

|   参数     |   说明     |
|-----------------|-------------------|
| / CaptureDir | 指定图像的应用和自定义的目录。 |
| / ConfigFile | 指定列出排除项的图像捕获和压缩命令的配置文件的位置。 有关详细信息，请参阅[DISM 配置列表和 WimScript.ini 文件](dism-configuration-list-and-wimscriptini-files-winnext.md)。
| / CheckIntegrity | 检测到并跟踪.wim 文件损坏时用于捕获，卸载、 导出和提交操作。 / 如果 DISM 检测到.wim 文件已损坏与应用和装载操作一起使用时，CheckIntegrity 停止操作。 |
| / 验证 | 检查错误和文件复制。 |
| [/ConfirmTrustedFile | 验证受信任的 Windows 10、 Windows 8.1 或 Windows 8 上的桌面图像。 此选项只能至少运行的计算机上运行 WinPE 4.0。 |

示例：

``` syntax
Dism /Capture-CustomImage /CaptureDir:D:\
```

## <a name="capture-image"></a>/ 捕获图像

捕获到一个新的.wim 文件的驱动器的映像。 捕获的目录包括所有子文件夹和数据。 不能捕获空目录。 目录必须包含至少一个文件。

您可以捕获映像为 Windows 映像 (.wim) 文件或一组拆分窗口的图像 (.swm) 文件;此选项不支持捕获 (.vhd/.vhdx) 的虚拟硬盘文件或全闪存更新 (.ffu) 的图像。 开头第 10 Windows 版本 1607，DISM 可以应用来捕获扩展的属性 (EA)。

语法︰

``` syntax
Dism /Capture-Image /ImageFile:<path_to_image_file> /CaptureDir:<source_directory> /Name:<image_name> [/Description:<image_description>]
[/ConfigFile:<configuration_file.ini>] {[/Compress:{max|fast|none}] [/Bootable] | [/WIMBoot]} [/CheckIntegrity] [/Verify] [/NoRpFix] [/EA]
```

|   参数     |   说明     |
|-----------------|-------------------|
| / ConfigFile | 指定列出排除项的图像捕获和压缩命令的配置文件的位置。 有关详细信息，请参阅[DISM 配置列表和 WimScript.ini 文件](dism-configuration-list-and-wimscriptini-files-winnext.md)。
| / 压缩 |   指定初始捕获操作使用的压缩类型。 **最大**选项提供了最佳压缩效果，但花费更多时间来捕获图像。 **快速**选项提供了更快的图像压缩，但生成的文件要比使用最大选项压缩的大。 这也是如果不指定该参数，则使用默认压缩类型。 **无**选项不压缩捕获的图像。 |
| / 引导 | 标记为可引导映像的卷映像。 此参数是仅用于 WinPE 映像。 .Wim 文件中只有一个卷映像标记为可引导映像。|
| / CheckIntegrity | 检测到并跟踪.wim 文件损坏时用于捕获，卸载、 导出和提交操作。 / 如果 DISM 检测到.wim 文件已损坏与应用和装载操作一起使用时，CheckIntegrity 停止操作。 |
| / 验证 | 检查错误和文件复制。 |
| / NoRpFix  | 禁用该重分析点标记修补程序。 重新分析点是一个包含指向另一个文件在文件系统上的文件。 如果没有指定 /NoRpFix，则解析为路径由 /ImageFile 指定的值以外的重分析点不会被捕获。|
|   / WIMBoot | 使用 /WIMBoot 附加图像与 Windows 图像文件 (WIMBoot) 的启动配置。 这仅适用于 Windows 8.1 映像被捕获或导出为 WIMBoot 的文件。 在 Windows 10 中不支持此功能。|
| /EA      | Windows 10，1607年版本中的新增功能。 扩展属性捕获。 必须显式指定该开关来捕获扩展的属性。 DISM 将捕获扩展的属性位，如果他们在中设置组件捕获 WIM 映像中。 如果未设置了位，DISM 将不会设置这些属性。 这些扩展的属性位、 而不是 AppX 软件包组件或 Win32 应用程序组件必须只收件箱组件的 CAB 文件包和驱动程序。 扩展的属性前缀"$Kernel"。 在名称将跳过因为捕获仅用户模式的扩展属性。 如果您在 Windows 10 使用 DISM，1607 捕获扩展的属性并使用较早版本的 DISM 应用映像的版本，该操作将会成功，但应用的图像将不会设置扩展的属性。  |

示例︰

``` syntax
Dism /Capture-Image /ImageFile:install.wim /CaptureDir:D:\ /Name:Drive-D
```

```syntax
dism /Capture-Image /CaptureDir:C:\ /ImageFile:"C:\WindowsWithOffice.wim" /Name:"Chinese Traditional" /ea
```

## <a name="cleanup-mountpoints"></a>/ 装入点清理

删除所有已装载的映像已损坏与关联的资源。 此命令不会卸载已装载的映像，也不会删除图像，可以使用**/Remount-Image**命令来恢复。 

示例： 

``` syntax
Dism /Cleanup-Mountpoints
```

若要了解详细信息，请参阅[修复 Windows 映像](repair-a-windows-image.md)

## <a name="commit-image"></a>/ 提交映像

应用到已装载的映像所做的更改。 使用**/Unmount-Image**选项时才装入图像。

语法︰

``` syntax
Dism /Commit-Image /MountDir:<path_to_mount_directory> [/CheckIntegrity] [/Append]
```

|   参数     |   说明     |
|-----------------|-------------------|
| / CheckIntegrity | 检测到并跟踪.wim 文件损坏时用于捕获，卸载、 导出和提交操作。 / 如果 DISM 检测到.wim 文件已损坏与应用和装载操作一起使用时，CheckIntegrity 停止操作。 |
| / 附加   |  将修改后的图像添加到现有.wim 文件而不是覆盖原始图像。 /CheckIntegrity 和 /Append 参数不适用于虚拟硬盘 (VHD) 文件。 |

示例： 

``` syntax
Dism /Commit-Image /MountDir:C:\test\offline
```

## <a name="delete-image"></a>/ 删除图像

从具有多个卷映像的.wim 文件中删除指定的卷映像。 此选项将删除元数据条目和 XML 条目。 它并不会删除流数据，并且不会优化.wim 文件。

此命令行选项不适用于虚拟硬盘 (VHD) 文件。

语法︰

``` syntax
Dism /Delete-Image /ImageFile:<path_to_image_file> {/Index:<image_index> | /Name:<image_name>} [/CheckIntegrity]
```

|   参数     |   说明     |
|-----------------|-------------------|
| / CheckIntegrity | 检测到并跟踪.wim 文件损坏时用于捕获，卸载、 导出和提交操作。 / 如果 DISM 检测到.wim 文件已损坏与应用和装载操作一起使用时，CheckIntegrity 停止操作。 |

示例： 

``` syntax
Dism /Delete-Image /ImageFile:install.wim /Index:1
```

## <a name="export-image"></a>/ 导出图像

将指定图像的副本导出到另一个文件。 源文件和目标文件必须使用相同的压缩类型。 也可以通过导出到新的映像文件优化图像。 当您修改图像时，DISM 存储增加图像的总体大小的其他资源文件。 导出图像时，将删除不必要的资源文件。

此命令行选项不适用于虚拟硬盘 (VHD) 文件。

语法︰

``` syntax
Dism /Export-Image /SourceImageFile:<path_to_image_file> {/SourceIndex:<image_index> | /SourceName:<image_name>} /DestinationImageFile:<path_to_image_file> [/DestinationName:<Name>] [/Compress:{fast|max|none|recovery}] [/Bootable] [/WIMBoot] [/CheckIntegrity]
```

|   参数     |   说明     |
|-----------------|-------------------|
|  / SWMFile     |  使您能够引用拆分.wim 文件。 模式是命名模式和拆分文件的位置。 您还可以指定通配符。 例如，"E:\image\install*.swm"将 E:\image 中的拆分文件导出目录命名为 install1.swm、 install2.swm，等等。|
| / 压缩 | 指定初始捕获操作使用的压缩类型。 /Compress 参数不适用于图像导出到现有.wim 文件时，您将图像导出到新的.wim 文件时才能使用此参数。 **最大**选项提供了最佳压缩效果，但花费更多时间来捕获图像。 **快速**选项提供了更快的图像压缩，但生成的文件要比使用**最大**选项压缩的大。 这也是如果不指定该参数，则使用默认压缩类型。 使用**恢复**选项导出按钮重置图像。 结果文件也小得多的大小，这样反过来极大地减少所需的保存按钮重置图像恢复驱动器上的磁盘空间量。 目标文件必须指定扩展名为.esd。 **无**选项不压缩捕获的图像。 |
| / 引导 | 标记为可引导映像的卷映像。 此参数是仅用于 WinPE 映像。 .Wim 文件中只有一个卷映像标记为可引导映像。|
|   / WIMBoot | 使用 /WIMBoot 附加图像与 Windows 图像文件 (WIMBoot) 的启动配置。 这仅适用于 Windows 8.1 映像被捕获或导出为 WIMBoot 的文件。 在 Windows 10 中不支持此功能。|
| / CheckIntegrity | 检测到并跟踪.wim 文件损坏时用于捕获，卸载、 导出和提交操作。 / 如果 DISM 检测到.wim 文件已损坏与应用和装载操作一起使用时，CheckIntegrity 停止操作。 |

示例： 

``` syntax
Dism /Export-Image /SourceImageFile:install.wim /SourceIndex:1 /DestinationImageFile:install2.wim
```

## <a name="get-mountedimageinfo"></a>/ Get MountedImageInfo

列出当前已装载的映像和有关已装载映像是否有效，如图像信息读/写权限、 装载位置、 已安装的文件路径和装入的映像的索引。

示例： 

``` syntax
Dism /Get-MountedImageInfo
```

## <a name="get-imageinfo"></a>/ Get ImageInfo

显示有关.wim、 vhd 或.vhdx 文件中包含的图像信息。 与 /Index 或 /Name 参数使用时，显示指定的图像信息，其中包括 WIMBoot 图像图像时，如果 Windows 8.1 的图像，请参阅图像或组件使用 DISM 的花费清单。 /Name 参数不适用于 VHD 文件。 您必须指定 /Index:1 的 VHD 文件。

语法︰ 

``` syntax
Dism /Get-ImageInfo /ImageFile:<path_to_image.wim> [{/Index:<Image_index> | /Name:<Image_name>}]
```

示例︰ 

``` syntax
Dism /Get-ImageInfo /ImageFile:C:\test\offline\install.wim
```

``` syntax
Dism /Get-ImageInfo /ImageFile:C:\test\images\myimage.vhd /Index:1
```

## <a name="get-wimbootentry"></a>/ Get WIMBootEntry

使用 /Get-WIMBootEntry 来显示指定的磁盘卷的 WIMBoot 配置项。

有关如何显示 WIMBoot 配置条目的详细信息，请参阅映像或组件使用 DISM 的花费清单。

这仅适用于 Windows 8.1;在 Windows 10 中不支持此功能。

语法︰

``` syntax
Dism /Get-WIMBootEntry /Path:<volume_path>
```

示例： 

``` syntax
Dism /Get-WIMBootEntry /Path:C:\
```

## <a name="list-image"></a>/ 列表图像

指定图像中显示的文件和文件夹的列表。

此命令行选项不适用于虚拟硬盘 (VHD) 文件。

语法︰

``` syntax
Dism /List-Image /ImageFile:<path_to_image_file> {/Index:<image_index> | /Name:<image_name>}
```

示例： 

``` syntax
Dism /List-Image /ImageFile:install.wim /Index:1
```

## <a name="mount-image"></a>/ 装载映像

从.wim、.vhd 或.vhdx 文件装载到指定的目录的图像，以便它可用于处理。 索引或名称值时需要指定.wim 文件的大多数操作。 

语法︰

``` syntax
Dism /Mount-Image /ImageFile:<path_to_image_file> {/Index:<image_index> | /Name:<image_name>} /MountDir:<path_to_mount_directory> [/ReadOnly] [/Optimize] [/CheckIntegrity]
```

|   参数     |   说明     |
|-----------------|-------------------|
| / 只读  | 设置具有只读权限已装载的映像。 可选项。 |
| / 优化 |   减少了初始装载时间。 |
| / CheckIntegrity | 检测到并跟踪.wim 文件损坏时用于捕获，卸载、 导出和提交操作。 / 如果 DISM 检测到.wim 文件已损坏与应用和装载操作一起使用时，CheckIntegrity 停止操作。 |

示例︰ 

``` syntax
Dism /Mount-Image /ImageFile:C:\test\images\myimage.wim /index:1 /MountDir:C:\test\offline
```

``` syntax
Dism /Mount-Image /ImageFile:C:\test\images\myimage.vhd /index:1 /MountDir:C:\test\offline /ReadOnly
```

## <a name="optimize-image-wimboot"></a>/ /WIMBoot 优化的图像

执行指定的配置为脱机映像。

|   参数     |   说明     |
|-----------------|-------------------|
| / WIMBoot  | 配置脱机 Windows 映像文件启动 (WIMBoot) 系统上安装的映像。 |
| / 优化 |   减少了初始装载时间。 / /WIMBoot 优化的图像仅适用于 Windows 8.1 映像被捕获或导出为 WIMBoot 的文件中。 仅使用 /Optimize-Image 的图像用于 WIMBoot 支持的系统。 如果非 WIMBoot 支持系统映像使用 /Optimize-Image，则 Windows 可能无法工作，如预期的那样，在非 WIMBoot 支持的设备上安装后。 |

示例： 

``` syntax
Dism /Image:C:\test\offline /Optimize-Image /WIMBoot
```

## <a name="remount-image"></a>/ 重新装载映像

重新装载已装载的映像，变得不可访问，并使其可用于处理。

语法︰ 

``` syntax
Dism /Remount-Image /MountDir:<path_to_mount_directory>
```

示例：

``` syntax
Dism /Remount-Image /MountDir:C:\test\offline
```

## <a name="split-image"></a>/ 分割图像

对于 WIM，此命令将现有.wim 文件拆分成多个只读的拆分.swm 文件。

此选项在指定的目录中，命名每个文件相同作为指定*path_to_swm*，但有一个附加的编号创建的.swm 文件。 例如，如果您将设置为*path_to_swm* `c:\Data.swm`、 Data.swm 文件、 Data2.swm 文件、 一个 Data3.swm 文件，此选项可创建和等等，定义每个部分的拆分.wim 文件并将其保存至 C:\ 目录。

此命令行选项不适用于虚拟硬盘 (VHD) 文件。

对于 FFU，此命令将现有全闪存更新 (.ffu) 文件拆分成多个只读的拆分.sfu 文件。

/Split-Ffu 选项仅适用于桌面版本的 Windows 10。

此选项在指定的目录中，命名每个文件相同作为指定的 /SFUFile，但有一个附加的编号创建的.sfu 文件。 例如，如果您使用`c:\flash.sfu`，您将获得一个 flash.sfu 文件，flash2.ffu 文件，一个 flash3.sfu 文件，并等等，定义每个部分的拆分的.sfu 文件并将其保存至 C:\ 目录。

WIM 的语法︰

``` syntax
Dism /Split-Image /ImageFile:<path_to_image_file> /SWMFile:<path_to_swm> /FileSize:<MB-Size> [/CheckIntegrity]
```

FFU 的语法︰

``` syntax
Dism /Split-Ffu /ImageFile:<path_to_image_file> /SFUFile:<pattern> /FileSize:<MB-Size>
```

|   参数     |   说明     |
|-----------------|-------------------|
| / 文件大小     | 指定最大大小，以兆字节 (MB) 为创建的每个文件。 如果一个文件大于 /FileSize 选项，其中一个结果将是 /FileSize 选项，为适应大型文件中指定的值大于拆分.swm 文件中指定的值。  |
| / CheckIntegrity | 检测到并跟踪.wim 文件损坏时用于捕获，卸载、 导出和提交操作。 / 如果 DISM 检测到.wim 文件已损坏与应用和装载操作一起使用时，CheckIntegrity 停止操作。 |
| / ImageFile  | 指定的路径。FFU 文件示例︰ flash.ffu。 |
|  / SFUFile  | 引用将拆分 FFU 文件 (SFUs)。 *模式*是命名模式和拆分文件的位置。

示例︰

``` syntax
Dism /Split-Image /ImageFile:install.wim /SWMFile:split.swm /FileSize:650
```

``` syntax
DISM.exe /Split-Ffu /ImageFile:flash.ffu /SFUFile:flash.sfu /FileSize:650
```

## <a name="unmount-image"></a>/ 卸载映像 

卸载.wim、.vhd 或.vhdx 文件并提交或放弃装载映像时所做的更改。

当您使用 /Unmount-Image 选项，则必须使用 /commit 或 /discard 参数。

语法︰ 

``` syntax
Dism /Unmount-Image /MountDir:<path_to_mount_directory> {/Commit | /Discard} [/CheckIntegrity] [/Append]
```

|   参数     |   说明     |
|-----------------|-------------------|
| / CheckIntegrity | 检测到并跟踪.wim 文件损坏时用于捕获，卸载、 导出和提交操作。 / 如果 DISM 检测到.wim 文件已损坏与应用和装载操作一起使用时，CheckIntegrity 停止操作。 |
| / 附加   |  将修改后的图像添加到现有.wim 文件而不是覆盖原始图像。 /CheckIntegrity 和 /Append 参数不适用于虚拟硬盘 (VHD) 文件。 |

示例︰

``` syntax
Dism /Unmount-Image /MountDir:C:\test\offline /commit
```

``` syntax
Dism /Unmount-Image /MountDir:C:\test\offline /discard
```

## <a name="update-wimbootentry"></a>/ 更新 WIMBootEntry

更新 WIMBoot 配置项，与指定的数据源 id，重命名的图像文件或移动的图像的文件路径。

**注意︰****/Update-WIMBootEntry**需要重新启动以使更新生效。

语法︰

```
Dism /Update-WIMBootEntry /Path:<Volume_path> /DataSourceID:<Data_source_id> /ImageFile:<Renamed_image_path>
```

|   参数     |   说明     |
|-----------------|-------------------|
| / 路径 | 指定的 WIMBoot 配置的磁盘卷。 |
|  / 建议  | 由 /Get-WIMBootEntry 显示指定数据源 ID。 |

示例：

``` syntax
DISM.exe /Update-WIMBootEntry /Path:C:\ /DataSourceID:0 /ImageFile:R:\Install.wim
```

## <a name="apply-siloedpackage"></a>/ 应用-SiloedPackage

适用于指定图像的一个或多个孤立供应包 (Spp)。 从 ADK 的 Windows 10 版本 1607年运行 CopyDandI.cmd 并运行后此选项才可用``` dism.exe /Apply-SiloedPackage ```由 CopyDandI.cmd 创建的目标文件夹中。 

**注意︰****/Apply-SiloedPackage**可以只运行一次根据 Windows 映像，但**/PackagePath**可以多次使用同一命令中要应用多个 Spp。 Spp 将按指定的顺序应用，因此应取决于它的 SPP 之前指定依赖项。 

有关孤立的供应包，以及如何使用 CopyDandI.cmd 的详细信息，请参阅[变得分散化配置软件包。](siloed-provisioning-packages.md)

若要了解如何处理孤立的供应包，请参阅[实验室 12︰ 添加桌面应用程序和设置变得分散化配置软件包 (Spp)](add-desktop-apps-wth-spps-sxs.md)。

``` Syntax
/Apply-SiloedPackage /PackagePath:<package_path> /ImagePath:<applied_image_path>
```

|  参数   | 说明  |
|--------------|--------------|
| / PackagePath | 指定一个孤立的供应包文件的路径。 |
| / ImagePath   | 指定在应用 SPP.的 Windows 映像的路径 |

示例：

``` syntax
Dism.exe /apply-SiloedPackage /PackagePath:C:\test\Word.spp /PackagePath:C:\test\spp2.spp /ImagePath:C:\
```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[DISM 的部署 windows 映像服务和管理技术参考](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md)

[DISM 是什么？](what-is-dism.md)

[DISM 命令行语法的全局选项](dism-global-options-for-command-line-syntax.md)

[部署 Windows 使用全闪存更新 (FFU)](deploy-windows-using-full-flash-update--ffu.md)

[WIM 与 VHD 与 FFU︰ 比较图像文件格式](wim-vs-ffu-image-file-formats.md)
