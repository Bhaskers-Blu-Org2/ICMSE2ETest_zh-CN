---
author: Justinha
Description: "Windows 10 包括的工具来帮助您使用较少的驱动器空间。"
ms.assetid: f58ee9cf-0dd1-4c46-9b1f-d16891247f2f
MSHAttr: PreferredLib:/library/windows/hardware
title: "压缩的操作系统，单实例存储和图像优化"
ms.openlocfilehash: 30860699b5024a6437d913d375129f05100007e7
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="compact-os-single-instancing-and-image-optimization"></a>压缩的操作系统，单实例存储和图像优化


Windows 10 包括的工具来帮助您使用较少的驱动器空间。 现在，您可以压缩整个操作系统，包括预加载桌面应用程序的文件。 精简的操作系统允许您压缩的文件 （类似于 Windows 更新 1 8.1 中的 WIMBoot） 和单实例存储可帮助您在压缩文件运行预装的 Windows 桌面应用程序中运行的操作系统。 新的流程有助于随着时间的推移保持较小的占地面积，通过使用单个文件，而不是将它们合并到 WIM 文件中。

这里有一些方法来缩小图像、 优化图像和一些注意事项，部署到低成本的设备时。

## <a name="span-iddeploymenttoolsthathelpsavespacespanspan-iddeploymenttoolsthathelpsavespacespanspan-iddeploymenttoolsthathelpsavespacespandeployment-tools-that-help-save-space"></a><span id="Deployment_tools_that_help_save_space"></span><span id="deployment_tools_that_help_save_space"></span><span id="DEPLOYMENT_TOOLS_THAT_HELP_SAVE_SPACE"></span>部署工具，可帮助节省空间


### <a name="span-idcompactosspanspan-idcompactosspanspan-idcompactosspancompact-os"></a><span id="Compact_OS"></span><span id="compact_os"></span><span id="COMPACT_OS"></span>精简的操作系统

精简的操作系统安装操作系统的文件压缩文件的形式。 同时基于 UEFI 的和基于 BIOS 的设备都支持精简的操作系统。

与 WIMBoot，文件将不能再合并成一个 WIM 文件中，因为 Windows 更新可以替换或删除单个文件，根据需要以保证随着时间的推移驱动器空间大小。

**请注意** 在 PC 上运行以前版本的 Windows 中，如 Windows 8.1 运行 Windows 图像处理和配置设计器 (ICD) 时您需要安装与 Windows ICD 和**部署工具**功能的[Windows 评估和部署工具包 (ADK)](http://go.microsoft.com/fwlink/?LinkId=526803) 。 这将安装最新版本的驱动程序所需的用于创建压缩的 OS 映像的 DISM （wimmount.sys 和 adkwof.sys）。

 

**要使用可引导的 USB 驱动器部署精简的操作系统**

1.  在技术人员计算机，打开 Windows ICD，并创建您的项目。
2.  插入 USB 闪存驱动器，请注意驱动器盘符 (示例︰ d:)。
3.  单击**创建** &gt; **生产介质** &gt; **WIM** &gt; **启用操作系统文件压缩︰ 是** &gt; **下** &gt; **可引导 USB 驱动器**&gt;驱动器 （d:）&gt; **Next** &gt; **Build**.
4.  启动目标计算机使用 USB 闪存驱动器。 Windows 会自动安装。

**若要部署精简的操作系统使用 WIM 文件**

1.  在 WinPE 创建页面文件设置为 256 MB。

    ``` syntax
    Wpeutil createpagefile C:\pagefile /size=256
    ```

    其中，"C"是 Windows 分区。

2.  启动目标设备与 Windows 10 版本的 Windows PE。 （若要使用以前版本的 Windows PE，请确保使用 DISM 的 Windows 10 版本。 若要了解详细信息，请参阅[将 DISM 复制到另一台计算机](copy-dism-to-another-computer.md)）。
3.  格式设置和准备这两个分区，然后将映像应用到分区使用 DISM 应用图像 /Compact 选项︰

    ``` syntax
    DISM /Apply-Image /ImageFile:install.wim /Index:1 /ApplyDir:D:\ /compact
    ```

    这通常是通过运行部署脚本。 若要了解详细信息，请参阅[使用 DISM 应用图像](apply-images-using-dism.md)。

**从 FFU 映像部署精简的操作系统**

1.  要部署 FFU 图像压缩，必须将原始 FFU 图像创建为压缩图像。

    单击**创建**从 Windows ICD &gt; **生产媒体** &gt; **FFU** &gt; **启用操作系统文件压缩︰ 是**&gt;命名该文件，例如 d:\\flash.ffu &gt; **生成**。

2.  从 Windows ICD 或 Windows 预安装环境 (WinPE)，您可以部署 FFU 图像直接到驱动器。 若要了解详细信息，请参阅[部署 Windows 使用全闪存更新 (FFU)](deploy-windows-using-full-flash-update--ffu.md)。

**若要部署精简的操作系统 Windows 安装程序**

-   设置使用 unattend.xml 文件︰ Microsoft Windows 安装程序\\ImageInstall\\OSImage\\[紧凑](https://msdn.microsoft.com/library/windows/hardware/dn949267)。

**命令行支持**在 Windows 10 和 WinPE 的下一个版本中，您可以查询操作系统是否运行精简的操作系统，并更改它在任何时候，使用[Compact.exe]( http://go.microsoft.com/fwlink/?LinkId=623487)命令。

**从 Windows PE 中，确定是否操作系统将压缩︰**


``` syntax
Compact.exe /CompactOS:Query /WinDir:E:\Windows
```

其中 e:\\窗口是安装 Windows 的文件夹。

**从联机安装，从改为非压缩压缩的操作系统︰**


``` syntax
Compact.exe /CompactOS:always
```

### <a name="span-idsingle-instancingofprovisioningpackagesspanspan-idsingle-instancingofprovisioningpackagesspanspan-idsingle-instancingofprovisioningpackagesspansingle-instancing-of-provisioning-packages"></a><span id="Single-instancing_of_provisioning_packages"></span><span id="single-instancing_of_provisioning_packages"></span><span id="SINGLE-INSTANCING_OF_PROVISIONING_PACKAGES"></span>单实例存储资源调配功能包

Windows 10 时添加新的 Windows 桌面应用程序到设备，您将捕获到一个压缩供应包中使用这些更改自动恢复工具。 而不是维护原始文件和资源调配的包，您可以使用 DISM 删除原始文件，并改为运行从直接从压缩的供应包。 这被称为单实例存储图像。

尽管单实例存储支持固态驱动器和旋转驱动器，出于性能原因，建议，单实例存储仅可用于具有固态驱动器设备。

示例：

``` syntax
DISM /Apply-CustomDataImage /CustomDataImage:C:\Recovery\Customizations\USMT.ppkg /ImagePath:C:\ /SingleInstance
```

其中*C*是 Windows 分区的驱动器号。

**警告** 不要将报价单与 /ImagePath:C:\\选项。

您可以确定是否设置软件包 (.ppkg) 是单一实例使用 fsutil.exe:

``` syntax
fsutil.exe wim enumwims C:
```

其中*C*是包含配置软件包，该驱动器。 驱动器上的任何单一实例设置包将在命令输出中列出。 如果没有，则命令将返回"错误︰ 系统找不到指定的文件。"

### <a name="span-idimageoptimizationspanspan-idimageoptimizationspanspan-idimageoptimizationspanimage-optimization"></a><span id="Image_optimization"></span><span id="image_optimization"></span><span id="IMAGE_OPTIMIZATION"></span>图像优化

后应用更新到 Windows 映像，清理图像，然后将其导出到新文件中︰

``` syntax
md c:\mount\Windows
md C:\mount\temp

Dism /Mount-Image /ImageFile:"C:\Images\install.wim" /Index:1 /MountDir:C:\mount\Windows

Dism /Cleanup-Image /Image=C:\mount\Windows /StartComponentCleanup /ResetBase /ScratchDir:C:\mount\temp

Dism /Unmount-Image /MountDir:C:\mount\Windows /Commit

Dism /Export-Image /SourceImageFile:C:\Images\install.wim /SourceIndex:1 /DestinationImageFile:C:\Images\install_cleaned.wim
```

其中*c:\\图像\\install.wim*是一个要更新的 Windows 映像文件。 开头第 10 Windows 版本 1607，您可以选择指定 /Defer 参数与 /ResetBase 将推迟到下一步的自动维护，任何长时间运行清理操作，但我们极力建议，**仅**使用 DISM /ResetBase 其中需要 30 分钟以上才能完成的工厂中的一个选项为 /Defer。 

## <a name="span-idsizerequirementsandconsiderationsspanspan-idsizerequirementsandconsiderationsspanspan-idsizerequirementsandconsiderationsspansize-requirements-and-considerations"></a><span id="Size_requirements_and_considerations"></span><span id="size_requirements_and_considerations"></span><span id="SIZE_REQUIREMENTS_AND_CONSIDERATIONS"></span>空间大小要求和注意事项


您仍然需要满足最小硬盘、 RAM、 应用程序资源使用情况和数据存储。

### <a name="span-idharddrivespanspan-idharddrivespanspan-idharddrivespanhard-drive"></a><span id="Hard_Drive"></span><span id="hard_drive"></span><span id="HARD_DRIVE"></span>硬驱

Windows 10 16 千兆字节 (GB) 的 32 位设备上的空间和 64 位设备上 20 GB 至少需要。

虽然某些配置的 Windows 可能会显示以适应较小的驱动器上，第一次安装 Windows 时，8GB SSDs 是不足够大。 即使用户对 8 GB 的硬盘与第二个驱动器，4gb 或更大的应用程序和数据文件存储，8 GB 的硬盘不允许会发生用户工作在其计算机上的 Windows 内存需求量的增加。

一些一段时间中的内存需求量增加的主要原因包括︰

-   **提供服务**。 必须对操作系统的软件修补程序和 service pack 版本保留硬盘空间。
-   **系统还原点**。 Windows 自动生成的还原点。 默认情况下需要量是空间的相对于硬盘的大小。 有关还原点的详细信息，请参阅 MSDN 上的[还原点](http://go.microsoft.com/fwlink/?LinkId=142170)主题。
    **请注意**  用户可以调整时使用计算机上的系统还原使用 (Sysdm.cpl)**系统属性**对话框中的**系统保护**用户界面的空间量。 用户还可以使用存储在外部硬盘来还原系统的系统映像备份。

-   **日志和缓存**。 操作系统存储文件，如事件日志和错误日志驱动器上。

### <a name="span-idramspanspan-idramspanram"></a><span id="RAM"></span><span id="ram"></span>RAM

Pagefile.sys 和 Hiberfil.sys 文件的大小成正比的计算机上的 RAM 量增加。 限制为 1 GB RAM 的计算机时，16 GB 的驱动器上安装 Windows 具有较小的内存需求量。 为大小大于 1 GB RAM 的增加将导致增加大小的系统文件和更少的其他应用程序和文件在硬盘上的空间。 增加硬盘的大小，但是，不会影响这些系统文件的大小。

### <a name="span-idapplicationsspanspan-idapplicationsspanspan-idapplicationsspanapplications"></a><span id="Applications_"></span><span id="applications_"></span><span id="APPLICATIONS_"></span>应用程序

在计算机安装的软件应用程序可能需要额外的空间，用于缓存、 日志和更新。 此外必须安装应用程序、 修补程序和更新的过程考虑临时提高资源使用的驱动器上可用磁盘空间。

### <a name="span-iduserdataspanspan-iduserdataspanspan-iduserdataspanuser-data"></a><span id="User_Data"></span><span id="user_data"></span><span id="USER_DATA"></span>用户数据

支持可移动媒体，如 SD 卡或 USB 闪存驱动器的计算机，用户可以轻松地扩展使用该可移动媒体的个人数据文件存储的用户文档。 但是，我们建议用户保留这些类型的文件的硬驱上的一些空间。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Windows 图像处理和配置设计器](https://msdn.microsoft.com/library/windows/hardware/dn916113)

[捕获和应用 Windows、 系统和恢复分区](capture-and-apply-windows-system-and-recovery-partitions.md)

[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)

 

 






