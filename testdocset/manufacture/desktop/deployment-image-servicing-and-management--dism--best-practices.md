---
author: Justinha
Description: "部署映像服务和管理 (DISM) 最佳做法"
ms.assetid: b9629ef4-9b4f-47c4-8eca-d2469cfcbd9b
MSHAttr: PreferredLib:/library/windows/hardware
title: "部署映像服务和管理 (DISM) 最佳做法"
ms.openlocfilehash: a4013207c60781e56f55ec0144617b55d11c7e22
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="deployment-image-servicing-and-management-dism-best-practices"></a>部署映像服务和管理 (DISM) 最佳做法


本部分介绍一些与处理 Windows® 映像相关的最佳做法。 我们建议您尽可能实现这些做法。

本主题︰

[提升权限的命令行工具](#bkmk-elevate)

[禁用防病毒工具](#bkmk-av)

[处理映像](#bkmk-servicing)

[更改国际设置](#bkmk-intl)

[使用日志文件](#bkmk-log)

[程序包位置](#bkmk-pkg)

[存储在网络共享上的文件](#netshare)

[从 Windows PE 的 Windows 映像提供服务](#bkmk-pe)

[扫描的损坏，并验证系统文件的完整性](#bkmk-verify)

[对于 Windows 图像增强的安全性](#security)

## <a name="span-idbkmkelevatespanspan-idbkmkelevatespanspan-idbkmkelevatespanelevate-permissions-for-command-line-tools"></a><span id="BKMK_elevate"></span><span id="bkmk_elevate"></span><span id="BKMK_ELEVATE"></span>提升权限的命令行工具


很多部署命令行工具，包括部署映像服务和管理 (DISM)，需要提升的权限。

请确保您具有提升的权限。 单击**开始**，然后键入**部署**。 用鼠标右键单击**部署和图像处理工具环境**，然后选择**以管理员身份运行**。

这必须进行即使您以管理员身份登录。

## <a name="span-idbkmkavspanspan-idbkmkavspanspan-idbkmkavspandisable-antivirus-tools"></a><span id="BKMK_av"></span><span id="bkmk_av"></span><span id="BKMK_AV"></span>禁用防病毒工具


一些 DISM 命令可能阻止了防病毒程序或反恶意软件工具。 在处理映像之前, 要禁用防病毒程序或反恶意软件工具的技术人员计算机上。

## <a name="span-idbkmkservicingspanspan-idbkmkservicingspanspan-idbkmkservicingspanservicing-an-image"></a><span id="BKMK_servicing"></span><span id="bkmk_servicing"></span><span id="BKMK_SERVICING"></span>处理映像


Windows 映像提供服务的最佳办法是脱机使用 DISM 工具。 DISM 可以用于安装、 卸载、 配置和更新驱动程序、 功能和 Windows 映像和 Windows 预安装环境 (WinPE) 映像中的程序包，而不将映像启动。 有关详细信息，请参阅[DISM 的部署映像服务和管理技术参考的窗口](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md)。

可用于**/Commit-Image**选项的任意位置在服务期间保存目前为止所做的更改。 如果经常提交所做的更改，您可以恢复图像更方便地与**/Cleanup-Image /RestoreHealth**选项已损坏。

您可以装载和修改单个计算机上的多个图像。 但是，性能可能会降低某些函数，如**/Unmount-Image**，具体取决于计算机上的可用内存。 作为一种最佳做法，不应在同一时间装入 20 多个图像。

**请注意**  
如果.wim 文件拆分成更小的文件以便扩展到多个介质，则不能装载映像以便进行处理。

 

## <a name="span-idbkmkintlspanspan-idbkmkintlspanspan-idbkmkintlspanchanging-international-settings"></a><span id="BKMK_intl"></span><span id="bkmk_intl"></span><span id="BKMK_INTL"></span>更改国际设置


若要更改 Windows 10、 Windows 8.1、 Windows 8、 Windows 服务器 2016年技术预览、 Windows Server 2012 R2、 Windows Server 2012，Windows 7 和 Windows Server 2008 R2 图像中的国际设置，您必须使用 DISM。 有关详细信息，请参阅[DISM 语言和国际服务命令行选项](dism-languages-and-international-servicing-command-line-options.md)。

## <a name="span-idbkmklogspanspan-idbkmklogspanspan-idbkmklogspanuse-log-files"></a><span id="BKMK_log"></span><span id="bkmk_log"></span><span id="BKMK_LOG"></span>使用日志文件


DISM 将详细信息记录到 %WINDIR%\\日志\\Dism\\Dism.log，默认情况。 此外可以指定名称和为日志文件中，您选择的位置，并设置**/loglevel**参数，以便记录您感兴趣的信息的。 当错误发生时，控制台将显示错误代码、 错误消息和日志文件的位置。

**重要**  
如果您未加入到域的计算机的网络共享上指定日志路径，使用带有域凭据网络使用来设置访问权限，设置 DISM 日志的日志路径之前。

 

日志文件会自动存档。 将追加到文件名.bak 保存存档的日志文件，并将生成新的日志文件。 日志文件的归档，每次.bak 文件将被覆盖。

日志文件为您提供了可帮助您解决疑难问题已执行的操作的历史记录。

## <a name="span-idbkmkpkgspanspan-idbkmkpkgspanspan-idbkmkpkgspanpackage-locations"></a><span id="BKMK_pkg"></span><span id="bkmk_pkg"></span><span id="BKMK_PKG"></span>程序包位置


不要将一个包，您打算安装直接在 Windows 安装的分区的根目录中。

## <a name="span-idnetsharespanspan-idnetsharespanspan-idnetsharespanstoring-files-on-a-network-share"></a><span id="NetShare"></span><span id="netshare"></span><span id="NETSHARE"></span>存储在网络共享上的文件


虽然 DISM 支持图像和包的网络路径，将更快地文件复制到本地硬盘上执行大多数操作。

## <a name="span-idbkmkpespanspan-idbkmkpespanservicing-a-windows-image-from-winpe"></a><span id="BKMK_PE"></span><span id="bkmk_pe"></span>为 Windows 从 WinPE 映像提供服务


您可以为服务从 WinPE 的 Windows 映像。 但是，您必须计划处理策略时考虑某些因素。 检查用于处理来自 WinPE 映像的以下要求。

### <a name="span-idbootingwinpefromaharddrivespanspan-idbootingwinpefromaharddrivespanspan-idbootingwinpefromaharddrivespanbooting-winpe-from-a-hard-drive"></a><span id="Booting_WinPE_from_a_Hard_Drive"></span><span id="booting_winpe_from_a_hard_drive"></span><span id="BOOTING_WINPE_FROM_A_HARD_DRIVE"></span>从硬盘启动 WinPE

为了提高性能，您可以分配更多内存，当您从硬盘启动 WinPE。 您还可以创建存储更新文件，以容纳大型更新的临时文件夹。

### <a name="span-idaddpage-filesupporttoyourwinpeimagespanspan-idaddpage-filesupporttoyourwinpeimagespanspan-idaddpage-filesupporttoyourwinpeimagespanadd-page-file-support-to-your-winpe-image"></a><span id="Add_Page-File_Support_to_Your_WinPE_Image"></span><span id="add_page-file_support_to_your_winpe_image"></span><span id="ADD_PAGE-FILE_SUPPORT_TO_YOUR_WINPE_IMAGE"></span>将页面文件支持添加到 WinPE 映像

请确保您有足够的内存来加载和运行您自定义的 WinPE 映像。 除了图像大小应该至少为 256 MB 的可用工作内存。 如果您的内存有限，定义页面文件 (Pagefile.sys) 改进内存管理。 实现页文件的详细信息，请参阅[Wpeutil 命令行选项](wpeutil-command-line-options.md)。

### <a name="span-idcreateatemporarydirectoryinwhichtostoreupdatefilesspanspan-idcreateatemporarydirectoryinwhichtostoreupdatefilesspanspan-idcreateatemporarydirectoryinwhichtostoreupdatefilesspancreate-a-temporary-directory-in-which-to-store-update-files"></a><span id="Create_a_Temporary_Directory_in_Which_to_Store_Update_Files"></span><span id="create_a_temporary_directory_in_which_to_store_update_files"></span><span id="CREATE_A_TEMPORARY_DIRECTORY_IN_WHICH_TO_STORE_UPDATE_FILES"></span>创建要在其中存储更新文件的临时目录

应使用 DISM 与**/ScratchDir**选项来创建一个临时目录，在创建另一个驱动器或服务的 Windows 映像上。 捕获映像、 安装语言包，安装更新，或安装或删除 Windows 功能在 Windows 映像中包括的许多 DISM 操作中使用的临时目录。 它们应用于 Windows 映像之前，一些文件被扩展到此临时目录。

以容纳大型更新分区中必须有足够的空间。 特定的所需的可用空间大小取决于要安装的更新的大小。 当添加语言包，暂存目录必须有至少 1 GB 的空间用于临时文件。

默认情况下，如果您没有设置临时目录路径上使用**/ScratchDir**选项，WinPE 创建一个 32 MB 的临时目录。 您可以分配到使用 DISM **/Set-ScratchSpace**选项此默认位置的其他临时存储。 32、 64、 128、 256 和 512MB，包括有效的大小。 此功能仅在脱机时用和 WinPE 会话正在运行时，不能调整该设置。 作为最佳操作，应使用**/ScratchDir**选项而是有足够的空间来支持任何图像管理和服务执行的操作的另一个分区上指定的目录。

安装完成后，该目录的内容不再需要可以删除。 有关详细信息，请参阅[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)。

### <a name="span-idbootingwinpefromacd-romdvdspanspan-idbootingwinpefromacd-romdvdspanspan-idbootingwinpefromacd-romdvdspanbooting-winpe-from-a-cd-romdvd"></a><span id="Booting_WinPE_from_a_CD-ROM_DVD"></span><span id="booting_winpe_from_a_cd-rom_dvd"></span><span id="BOOTING_WINPE_FROM_A_CD-ROM_DVD"></span>从 CD-ROM/DVD 启动 WinPE

处理 Windows 映像需要额外的临时存储空间。 对于 WinPE RAM 磁盘，则可能需要额外的内存。 除了 WinPE 映像的 RAM 要求，更多的 RAM 则需要过程更新。 所需的 RAM 的数量取决于要应用的更新的大小。 请确保您的计算机具有足够的 RAM。

## <a name="span-idbkmkverifyspanspan-idbkmkverifyspanspan-idbkmkverifyspanscan-for-corruption-and-verify-the-integrity-of-system-files"></a><span id="BKMK_verify"></span><span id="bkmk_verify"></span><span id="BKMK_VERIFY"></span>扫描的损坏，并验证系统文件的完整性


在将计算机交付给最终用户之前，应验证 Windows 系统文件的完整性。 可以使用**/Cleanup-Image**选项来标识文件损坏和图像上执行修复操作。 有关 DISM 中的**/Cleanup-Image**选项的详细信息，请参阅[DISM 操作系统程序包服务命令行选项](dism-operating-system-package-servicing-command-line-options.md)。

您还可以在线或离线的参考图像上使用系统文件检查器 (Sfc.exe)。 系统文件检查器将释放与所有版本的 Windows.System 文件检查器需要提升的权限，您必须是管理员才能运行它。 它会扫描所有受保护的文件以验证文件版本。 要验证 Windows 系统文件的完整性，请运行**sfc.exe /verifyonly**选项。 对于完整的命令行语法，在提升的命令提示符下，键入**sfc.exe /？**。

运行 Sfc.exe 可能需要花费很长的时间。 预期的结果是没有系统的完整性受到破坏。 但是，如果 Windows 系统文件的问题，您应调查问题。 不建议使用 Sfc.exe 扫描选项来自动修复 Windows 系统文件。

## <a name="span-idsecurityspanspan-idsecurityspanspan-idsecurityspanimproving-security-for-windows-images"></a><span id="Security"></span><span id="security"></span><span id="SECURITY"></span>对于 Windows 图像增强的安全性


Windows 映像包含自定义配置数据、 自定义应用程序和其他知识产权。 有几种方法来提高 Windows 映像，在线和离线的安全。

-   **限制访问的 Windows 映像**。 根据您的环境中，您可以编辑访问控制列表 (Acl) 或文件的权限。 只有批准的帐户有权访问的 Windows 映像。

-   **更新您的最新修补程序和软件更新的 Windows 映像**。 有多种方法可以处理 Windows 映像。 提供服务的 Windows 映像之后, 测试的有效性和稳定性的计算机。

-   **在 Windows 安装，配置计算机，以便自动下载和安装 Windows 更新**。 这延长了安装时间，但可确保您正在安装的 Windows 映像包含最新的更新。 有关详细信息，请参阅`DynamicUpdate`设置在**无人参与的 Windows 安装程序参考**Microsoft Windows 安装程序组件中。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[DISM 的部署 windows 映像服务和管理技术参考](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md)

[了解处理策略](understanding-servicing-strategies.md)

 

 






