---
author: Justinha
Description: "清理 WinSxS 文件夹"
ms.assetid: 67fe462d-cda1-4f2e-9652-62c374a6be97
MSHAttr: PreferredLib:/library/windows/hardware
title: "清理 WinSxS 文件夹"
ms.openlocfilehash: 26b1ec8f9fa9665af2e4f313ba6e59e4ad4db93b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="clean-up-the-winsxs-folder"></a>清理 WinSxS 文件夹


一个常见的问题是可以删除 WinSxS 文件夹来重新获得一些磁盘空间？ 简短的答案是没有。 但是，有办法减少 WinSxS 文件夹的大小。 有关 WinSxS 文件夹的详细信息，请参阅[管理组件存储](manage-the-component-store.md)。 编写本主题旨在提供信息的不同方法，以减少在运行版本的 Windows 10 WinSxS 文件夹的大小。

Windows 10 和 Windows 服务器 2016年自动将减小 WinSxS 通过使用类似于本文中描述的方法，但这些方法还包括内部流程，例如卸载和删除已由较新版本与其他组件的组件使用的包。 一些组件的以前版本的系统上保留一段时间，如有必要，允许您回滚。 后一段时间，这些组件会从安装中删除。

如下所述[减少组件存储在脱机 Windows 映像的大小](reduce-the-size-of-the-component-store-in-an-offline-windows-image.md)，还可以减少使用的相同的技术，一些 Windows 映像的大小。

**警告**  
从 WinSxS 文件夹中删除文件或删除整个 WinSxS 文件夹可能会严重，使您的 PC 不可能引导并使其无法更新损坏您的系统。

 

在 Windows 10 和 Windows 服务器 2016年，您有多种方法可以开始清理组件存储，包删除和组件压缩的组合用于清理 WinSxS 文件夹︰

## <a name="span-idtaskschedulerspanspan-idtaskschedulerspanspan-idtaskschedulerspantask-scheduler"></a><span id="Task_Scheduler"></span><span id="task_scheduler"></span><span id="TASK_SCHEDULER"></span>任务计划程序


在 Windows 8 定期清理组件自动不使用系统时创建**StartComponentCleanup**任务。 此任务将由操作系统触发时自动运行。 时自动运行，该任务将等待至少 30 天之后更新的组件已安装之前卸载以前的版本的组件。

如果您选择运行此任务，该任务将有 1 小时的超时限制，可能不完全清理的所有文件。

**任务计划程序来清除和压缩组件中运行 StartComponentCleanup 任务**

1.  如果**任务计划程序**未打开，请启动**任务计划程序**。 有关详细信息，请参阅[启动任务计划程序](http://technet.microsoft.com/library/cc721931.aspx)。

2.  展开控制台树中，导航到**任务计划程序库\\Microsoft\\Windows\\服务\\StartComponentCleanup**。

3.  在**所选项目**，单击**运行**

**请注意**  
也可以从命令行启动 StartComponentCleanup 任务︰

**schtasks.exe/运行 /TN"\\Microsoft\\Windows\\服务\\StartComponentCleanup"**

 

## <a name="span-iddismexespanspan-iddismexespandismexe"></a><span id="dism.exe"></span><span id="DISM.EXE"></span>Dism.exe


部署映像服务和管理 (DISM) 是一个命令行工具，允许您安装、 卸载、 配置和更新 Windows 功能、 程序包、 驱动程序和国际设置。 **Dism.exe**的**/Cleanup-Image**参数为高级的用户提供了更多的选项，以进一步减少 WinSxS 文件夹的大小。 有关详细信息，请参阅[DISM 操作系统程序包服务命令行选项](dism-operating-system-package-servicing-command-line-options.md)。

**使用 /StartComponentCleanup 参数**

-   在运行版本的 Windows 10 使用 Dism.exe 的**/StartComponentCleanup**参数使您运行**StartComponentCleanup**任务在**任务计划程序**，除早期版本更新的组件的结果将被立即删除 （没有一个 30 天宽限期），您将没有一个 1 小时的超时限制类似。

    从提升的命令提示符下，键入以下命令︰

    ``` syntax
    Dism.exe /online /Cleanup-Image /StartComponentCleanup
    ```

**使用 /StartComponentCleanup 参数中使用 /ResetBase 开关**

-   使用**/ResetBase**开关在运行版本的 Windows 10 DISM.exe 的**/StartComponentCleanup**参数将删除所有取代的版本的每个组件组件存储区中。

    从提升的命令提示符下，键入以下命令︰

    ``` syntax
    Dism.exe /online /Cleanup-Image /StartComponentCleanup /ResetBase
    ```

    **警告**  
    在此命令完成后，无法卸载所有现有的服务包和更新。 这不会阻止未来的 service pack 或更新卸载。

     

**使用 /SPSuperseded 参数**

-   为减少使用 Service Pack 的空间，使用在运行版本的 Windows 10 Dism.exe **/SPSuperseded**参数移除任何备份组件所需的 service pack 的卸载。 服务包是一套特定的 Windows 版本的累积更新。

    从提升的命令提示符下，键入以下命令︰

    ``` syntax
    Dism.exe /online /Cleanup-Image /SPSuperseded
    ```

    **警告**  
    完成此命令后，不能卸载 service pack。

     

## <a name="span-iddiskcleanupspanspan-iddiskcleanupspanspan-iddiskcleanupspandisk-cleanup"></a><span id="Disk_Cleanup"></span><span id="disk_cleanup"></span><span id="DISK_CLEANUP"></span>磁盘清理


可以使用磁盘清理来减少不必要的文件在您的驱动器，这可以帮助您的电脑运行得更快。 它可以删除临时文件和系统文件、 清空回收站，并删除各种可能不再需要其他项目。 清理选项更新有助于减小组件存储的大小。

**运行磁盘清理程序删除系统文件**

-   若要删除系统文件运行[使用磁盘清理删除文件](http://go.microsoft.com/fwlink/p/?LinkId=698648)中所述步骤。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[管理组件存储](manage-the-component-store.md)

[确定 WinSxS 文件夹的实际大小](determine-the-actual-size-of-the-winsxs-folder.md)

[减少脱机 Windows 映像中的组件存储区的大小](reduce-the-size-of-the-component-store-in-an-offline-windows-image.md)

[卸载-WindowsFeature](http://technet.microsoft.com/library/jj205471.aspx)

[如何降低 Winsxs 目录的大小和可用磁盘空间的即需即装 Windows Server 2012 使用功能](http://blogs.technet.com/b/askpfeplat/archive/2013/02/24/how-to-reduce-the-size-of-the-winsxs-directory-and-free-up-disk-space-on-windows-server-2012-using-features-on-demand.aspx)

[如何解决由大型 Windows 组件存储 (WinSxS) 目录的磁盘空间问题](http://support.microsoft.com/kb/2795190)

 

 






