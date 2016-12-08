---
author: Justinha
Description: "确定 WinSxS 文件夹的实际大小"
ms.assetid: 059afbeb-3911-4e50-9ba5-ffd4fe6f38a4
MSHAttr: PreferredLib:/library/windows/hardware
title: "确定 WinSxS 文件夹的实际大小"
ms.openlocfilehash: e2990f62177a028034a9b5d1eb1d73f23107664f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="determine-the-actual-size-of-the-winsxs-folder"></a>确定 WinSxS 文件夹的实际大小


为什么会如此大 WinSxS 文件夹？ 这个常见的问题的简短答案是组件存储 （WinSxS 文件夹） 包含构成 Windows 允许您运行您的系统的所有组件。 这些组件将保留回滚任何有问题的更改，或者修复已损坏的文件。 有关组件存储的详细信息，请参阅[管理组件存储](manage-the-component-store.md)。 有关如何删除 WinSxS 文件夹中的文件的信息，请参阅[干净向上 WinSxS 文件夹](clean-up-the-winsxs-folder.md)。

对于操作系统文件，它可以显示多个相同版本的文件的副本存储在操作系统上的多个位置，但通常会有一个真正的文件副本。 其他副本都只是"投影"通过从组件存储的硬链接。 *硬链接*是文件系统对象，可用于引用磁盘上的同一位置的两个文件。 一些工具，如文件资源管理器中，确定目录的大小，不考虑帐户包含的文件可能是硬链接。 这可能导致您以为 WinSxS 文件夹占用更多的磁盘空间不是真的那样。

**警告**  
一些重要的系统文件都位于 WinSxS 文件夹。 从 WinSxS 文件夹中删除文件或删除整个 WinSxS 文件夹可能会严重，使您的 PC 可能不启动，并使其无法更新损坏您的系统。

 

一个新的选项具有已添加到 Windows 8.1 来帮助确定磁盘空间量的 DISM 工具 WinSxS 文件夹实际上使用。

**分析组件存储 （WinSxS 文件夹） 的大小**

-   打开提升的命令窗口并键入︰

    ``` syntax
    Dism.exe /Online /Cleanup-Image /AnalyzeComponentStore
    ```

    **请注意**  
    **/AnalyzeComponentStore**选项不被识别 Windows 8 上以及更早版本。

     

    返回的信息是︰

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left">标题</th>
    <th align="left">说明</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><p>Windows 资源管理器报告组件存储区大小</p></td>
    <td align="left"><p>如果 Windows 资源管理器中通过计算，该值 WinSxS 文件夹的大小。 此值不会考虑在 WinSxS 文件夹内的硬链接的使用。</p></td>
    </tr>
    <tr class="even">
    <td align="left"><p>组件存储的实际大小</p></td>
    <td align="left"><p>此值因素在 WinSxS 文件夹内的硬链接。 它并不排除与 Windows 共享使用硬链接的文件。</p></td>
    </tr>
    <tr class="odd">
    <td align="left"><p>与 Windows 共享</p></td>
    <td align="left"><p>此值提供大小的文件的硬链接，以便它们出现在组件存储和其他位置 （对于 Windows 的正常操作） 中。 这包括在实际的大小，但不应被视为组件存储开销的一部分。</p></td>
    </tr>
    <tr class="even">
    <td align="left"><p>备份和已禁用的功能</p></td>
    <td align="left"><p>这是以响应出现的故障，在较新的组件或提供选择启用更多的功能被保留的组件的大小。 它还包括组件存储元数据和通过并行组件的大小。</p>
    <p>这包括在实际大小，组件存储开销的一部分。</p></td>
    </tr>
    <tr class="odd">
    <td align="left"><p>缓存和临时数据</p></td>
    <td align="left"><p>这是由内部组件存储以使组件服务操作速度更快的文件的大小。 这包括在实际大小，组件存储开销的一部分。</p></td>
    </tr>
    <tr class="even">
    <td align="left"><p>上一次清除的日期</p></td>
    <td align="left"><p>这是最近完成的组件存储清除的日期。</p></td>
    </tr>
    <tr class="odd">
    <td align="left"><p>可回收的包的数量</p></td>
    <td align="left"><p>这是该组件清理可以删除系统上的软件包被取代。</p></td>
    </tr>
    <tr class="even">
    <td align="left"><p>组件存储清理建议</p></td>
    <td align="left"><p>这是组件存储清理建议。 当执行清理过程可能会降低组件存储开销大小，建议清理。</p></td>
    </tr>
    </tbody>
    </table>

     

    基于这种分析可以确定备份的总和 WinSxS 文件夹的开销和禁用缓存功能大小和临时的数据大小。

    输出示例︰

    ``` syntax
    C:\>dism /online /cleanup-image /analyzecomponentstore

    Deployment Image Servicing and Management tool
    Version: 6.3.XXXX.0

    Image Version: 6.3.XXXX.0

    [==========================100.0%==========================]

    Component Store (WinSxS) information:

    Windows Explorer Reported Size of Component Store : 4.98 GB

    Actual Size of Component Store : 4.88 GB

        Shared with Windows : 4.38 GB
        Backups and Disabled Features : 506.90 MB
        Cache and Temporary Data : 279.52 KB

    Date of Last Cleanup : 2013-06-10 23:32:22

    Number of Reclaimable Packages : 0
    Component Store Cleanup Recommended : No

    The operation completed successfully.
    ```

    在此示例中，WinSxS 文件夹显示为 4.98 GB，但实际的开销 （备份和已禁用的功能的大小和大小的缓存和临时数据的总和） 786.42 MB。

**确定是否您应该清理组件存储 （WinSxS 文件夹），根据分析结果**

1.  打开提升的命令窗口并键入︰

    ``` syntax
    Dism.exe /Online /Cleanup-Image /AnalyzeComponentStore
    ```

2.  如果清理建议按照相关主题，[干净向上 WinSxS 文件夹](clean-up-the-winsxs-folder.md)中的步骤。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[管理组件存储](manage-the-component-store.md)

[清理 WinSxS 文件夹](clean-up-the-winsxs-folder.md)

[我的共享空间在哪里？（日志）](http://blogs.technet.com/b/askcore/archive/2013/03/01/where-did-my-space-go.aspx)

[服务在 Windows 8.1/Server 2012 R2 中的更改](http://blogs.technet.com/b/joscon/archive/2013/07/29/servicing-changes-in-windows-8-1-server-2012r2.aspx)

[NTFS 图元文件博客张贴内容](http://blogs.technet.com/b/askcore/archive/2009/12/30/ntfs-metafiles.aspx)

[如何创建和操作 NTFS 联结点](http://support.microsoft.com/kb/205524)

[DISM 操作系统程序包服务命令行选项](dism-operating-system-package-servicing-command-line-options.md)

 

 






