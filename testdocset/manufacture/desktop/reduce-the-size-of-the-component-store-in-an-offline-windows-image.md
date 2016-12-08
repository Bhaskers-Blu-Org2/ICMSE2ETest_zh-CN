---
author: Justinha
Description: "减少脱机 Windows 映像中的组件存储区的大小"
ms.assetid: 2cdff215-30b9-4360-9e2c-cc2c3d695608
MSHAttr: PreferredLib:/library/windows/hardware
title: "减少脱机 Windows 映像中的组件存储区的大小"
ms.openlocfilehash: 04ace359dbb7f5755977318ae001d460cdb20b76
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="reduce-the-size-of-the-component-store-in-an-offline-windows-image"></a>减少脱机 Windows 映像中的组件存储区的大小


部署映像服务和管理 (DISM) 工具可用于将 Windows 映像装载 WIM、 VHD 或 VHDX 文件中，并对其进行修改。

## <a name="span-idanalyzeandcleanupthecomponentstorewinsxsfolderinanofflinewindowsimagespanspan-idanalyzeandcleanupthecomponentstorewinsxsfolderinanofflinewindowsimagespanspan-idanalyzeandcleanupthecomponentstorewinsxsfolderinanofflinewindowsimagespananalyze-and-clean-up-the-component-store-winsxs-folder-in-an-offline-windows-image"></a><span id="Analyze_and_clean_up_the_Component_Store__WinSxS_folder__in_an_offline_Windows_image"></span><span id="analyze_and_clean_up_the_component_store__winsxs_folder__in_an_offline_windows_image"></span><span id="ANALYZE_AND_CLEAN_UP_THE_COMPONENT_STORE__WINSXS_FOLDER__IN_AN_OFFLINE_WINDOWS_IMAGE"></span>分析并清理脱机 Windows 映像中的组件存储 （WinSxS 文件夹）


若要完成本演练，您需要以下各项︰

-   与 Windows 8.1 版本的 Windows ADK 工具安装在其上运行 Windows 10、 Windows 8.1、 Windows 8，Windows 7、 Windows 服务器 2016年技术预览、 Windows Server 2012 R2、 Windows Server 2012 或 Windows Server 2008 R2 的计算机。

-   Windows 10 或 Windows 服务器 2016年技术预览图像一个.wim、.vhd 或.vhdx 文件。

**分析组件存储在脱机 Windows 映像的大小**

1.  将复制.vhd 或.vhdx，其中包含 Windows 映像，到本地驱动器.wim 文件。 例如，c:\\测试\\图像。

2.  单击**开始**，然后键入**部署**。 用鼠标右键单击**部署和图像处理工具环境**，然后选择**以管理员身份运行**。

3.  创建已装载的映像的文件夹。 例如，c:\\测试\\脱机。

4.  运行**DISM /Get-ImageInfo**命令的名称或索引号，则需要更新的图像检索。 例如︰

    ``` syntax
    Dism /Get-ImageInfo /ImageFile:C:\test\images\MyImage.wim
    ```

5.  将 Windows 映像进行安装。 例如︰

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\MyImage.wim /Index:1 /MountDir:C:\test\offline
    ```

    由于 WIM 文件可以包含一个或多个图像，您必须指定索引或名称值。 装载从 VHD 映像，您必须指定`/Index:1`。

6.  分析组件存储的大小。 例如︰

    ``` syntax
    Dism /Image:C:\test\offline /Cleanup-Image /AnalyzeComponentStore
    ```

    在显示中提供不同的值，请参阅[确定 WinSxS 文件夹的实际大小](determine-the-actual-size-of-the-winsxs-folder.md)。

7.  如果组件存储清理已显示报告中的建议，您可以开始清理图像。 例如︰

    ``` syntax
    Dism /Image:C:\test\offline /Cleanup-Image /StartComponentCleanup
    ```

8.  可以通过添加 /ResetBase 参数来减小组件存储更多的大小。 例如︰

    ``` syntax
    Dism /Image:C:\test\offline /Cleanup-Image /StartComponentCleanup /ResetBase
    ```
    
    开头第 10 Windows 版本 1607，可以在 /Resetbase 将推迟到下一步的自动维护任何长时间运行清理操作中指定 /Defer 参数。 但我们极力建议您**只**将 /Defer 用作其中 DISM /Resetbase 需要 30 分钟以上才能完成的工厂中的一个选项。 
   
    每周运行两周截止日期计划的维护任务。  第一周，维护任务才会运行在系统空闲的维护窗口期间。  如果无法完成时 （例如，计算机关闭时未在使用） 则任务计划程序运行更频繁，并且该任务可能会运行时系统正忙。
 
    若要查看性能效果，该任务正在运行时，单击开始 > 运行，然后键入下面的命令︰
    
    ```syntax
    Schtasks.exe /Run /I /TN \Microsoft\Windows\Servicing\StartComponentCleanup
    ```
    
9.  提交更改并卸载映像才能保存所做的更改。 例如︰

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\test\offline /Commit
    ```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[管理组件存储](manage-the-component-store.md)

[清理 WinSxS 文件夹](clean-up-the-winsxs-folder.md)

[确定 WinSxS 文件夹的实际大小](determine-the-actual-size-of-the-winsxs-folder.md)

[我的共享空间在哪里？（日志）](http://blogs.technet.com/b/askcore/archive/2013/03/01/where-did-my-space-go.aspx)

[NTFS 图元文件博客张贴内容](http://blogs.technet.com/b/askcore/archive/2009/12/30/ntfs-metafiles.aspx)

[如何创建和操作 NTFS 联结点](http://support.microsoft.com/kb/205524)

[DISM 操作系统程序包服务命令行选项](dism-operating-system-package-servicing-command-line-options.md)

 

 






