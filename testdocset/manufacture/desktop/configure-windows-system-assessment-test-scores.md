---
author: Justinha
Description: "配置 Windows 系统评估考试成绩"
ms.assetid: b2906f26-8887-44fe-8894-f73caee41824
MSHAttr: PreferredLib:/library/windows/hardware
title: "配置 Windows 系统评估考试成绩"
ms.openlocfilehash: 0ec14fee71d0b4325dacc49371c1e85e068bc802
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="configure-windows-system-assessment-test-scores"></a>配置 Windows 系统评估考试成绩


Windows® 系统评估测试 (WinSAT) 用于分析性能的几个系统组件，包括 CPU、 内存、 磁盘和图形。

WinSAT 结果作为 Windows 体验索引 (WEI) 成绩总结中的**性能信息和工具**控制面板项目。 这些成绩向使用者显示其系统的性能特征。

在 OOBE，期间不再生成 WinEI 的成绩也不能 prepop xml 文件用于在 OOBE 期间创建 WinSAT 正式文件。 我们建议您生成 WinSAT 正式文件在销售给最终用户的系统上。 这使得 WinSAT 成绩可以，只要最终用户启动其系统，和允许取决于能够立即使用这些结果的优化。 由于评估服务将不会运行在全新的体验，WinSAT 并且 WEI 成绩不再生成当用户完成 OOBE。 相反，在其他两个时间，可以生成分数使用除了预设 WinSAT 将发货的系统上的其他机制。

-   最终用户可以通过使用**性能信息和工具**控制面板项中的**重新运行评估**选项明确请求进行评估。

-   在系统空闲时，首次启动时，将使用维护计划程序，如果没有预填充运行其余 WinSAT 评估。

## <a name="span-idtorunwinsatonacompletesystemspanspan-idtorunwinsatonacompletesystemspanspan-idtorunwinsatonacompletesystemspanto-run-winsat-on-a-complete-system"></a><span id="To_run_WinSAT_on_a_complete_system"></span><span id="to_run_winsat_on_a_complete_system"></span><span id="TO_RUN_WINSAT_ON_A_COMPLETE_SYSTEM"></span>在一个完整的系统上运行 WinSAT


使用**prepop**选项 WinSAT 命令行工具对系统组件进行评估。

按照每台计算机 （对于所有系统） 上运行 WinSAT:

1.  安装 Windows 8 和启动到审核模式。 有关审核模式的详细信息，请参阅[审核模式概述](http://go.microsoft.com/fwlink/?LinkId=214469)。

2.  添加补充组件，如全新的驱动程序。

3.  运行**WinSAT prepop**。

    这将生成 prepop.xml 结果文件的数据存储目录，位于 WinSAT:`%WINDIR%\performance\winsat\datastore\`

4.  \[可选\]如果您打算捕获部署到其他计算机，运行此安装**sysprep / 一般化/审核 /shutdown**然后捕获安装。 将映像部署到一个 PC，您打算发运，并启动它。

5.  请验证该 Windows 启动到审核模式，然后再运行**WinSAT moobe**。

    这从匹配的 prepop 文件，生成 WinSAT 正式文件，并确保最终用户进行第一次引导系统时，WinSAT 正式文件是可用。 Windows 可以扩展，某些功能基于 WinSAT 正式文件，并且如果此文件不存在于系统中，则系统可能会遇到性能问题，包括不必要的存储设备碎片整理，缺乏优化内存管理和预取优化。

    **请注意**  
    为了减少在工厂地板的一台电脑所花费的时间，我们建议使用**WinSAT prepop**创建主 Windows 映像时。 在工厂车间，您只需要运行**WinSAT moobe**。 但是，如果您想要在工厂运行**WinSAT prepop**和**WinSAT moobe** ，您可以使用**WinSAT 正式**。 此选项创建属于同一文件作为运行**WinSAT prepop**和**WinSAT moobe**套，并应在方案中使用时您将不能在主 Windows 映像上运行**WinSAT prepop** 。

     

6.  运行**sysprep /oobe**可以将 Windows 配置为启动到 OOBE。

    **警告**  
    运行**sysprep 一般化 /**运行**WinSAT moobe**将删除**WinSAT moobe**创建的结果之后。 我们建议您运行**WinSAT moobe**或**WinSAT 正式**在工厂车间的每台 PC 的想要交付给客户。

     

系统现在已准备发运给客户。 运行的每个计算机图像 WinSAT 评估所有的优点是客户的计算机始终有一套完整的 WinSAT 结果。 它还具有最精确的 WinSAT 结果。 在此，准确意味着如果使用者使用了按需分级的系统，系统将获取 winsat 预填充分级大于或等于。

预填充不打算启用之间传输 WinSAT 数据系统具有很大的不同功能，如在便携式计算机和台式机，因为数据不精确在非常不同的系统。 相反，它是为了更加轻松地重新使用 WinSAT 数据间相似的系统;那些包含相同的主板芯片组和类似的 CPU、 显卡和磁盘的系统。

下面的过程描述如何在相似的计算机中的某一行中的所选配置运行 WinSAT。 这涉及到多次运行**WinSAT prepop**命令。

## <a name="span-idtorunwinsatforselectivepcconfigurationsandpccomponentsspanspan-idtorunwinsatforselectivepcconfigurationsandpccomponentsspanspan-idtorunwinsatforselectivepcconfigurationsandpccomponentsspanto-run-winsat-for-selective-pc-configurations-and-pc-components"></a><span id="To_run_WinSAT_for_selective_PC_configurations_and_PC_components"></span><span id="to_run_winsat_for_selective_pc_configurations_and_pc_components"></span><span id="TO_RUN_WINSAT_FOR_SELECTIVE_PC_CONFIGURATIONS_AND_PC_COMPONENTS"></span>若要为选择的电脑配置和 PC 组件运行 WinSAT


1.  标识您要包括在 pc 端，包括视频处理器、 内存和存储设备配置。

2.  安装 Windows 8 和启动到审核模式。 有关审核模式的详细信息，请参阅[审核模式概述](http://go.microsoft.com/fwlink/?LinkId=214469)。

3.  添加补充组件，如全新的驱动程序。

4.  运行**WinSAT prepop**。

5.  运行**Sysprep / 一般化/审核 /reboot**。 这将删除所有非 prepop WinSAT.xml 文件。

6.  结果 WinSAT prepop.xml 文件从复制`%WINDIR%\performance\winsat\datastore`到网络共享使用 WinSAT 结果存储。

7.  升级的组件之一。 例如，增加计算机组中的一种配置的内存。

8.  运行**WinSAT prepop-记忆**测试。 使用这样的工具，可确保仅与指定组件相关的测试将运行。 将生成其他.xml 文件显示内存测试结果。

9.  还原原始内存配置，并升级不同的组件，例如，视频卡。

    **请注意**  
    因为 WinSAT 结果可用于相同或更高版本，如果还原为基本配置，则测试结果将惠及更多的计算机相关。

     

10. 重新运行测试使用**WinSAT prepop-图形**命令。 只有测试与运行指定的组件。 为图形结果生成其他.xml 文件。

11. 存储在网络共享上的原始.xml 结果文件与新的结果文件。

12. 预填充 WinSAT 结果类似的组件与新电脑，.xml 文件从网络共享复制到目标计算机的 WinSAT 数据存储目录︰ `%WINDIR%\performance\winsat\datastore`。 可以将整套 WinSAT prepop 文件从网络共享复制到本地 WinSAT 目录。 WinSAT 将当前计算机查找正确的设置。

13. 运行的新计算机上`WinSAT moobe`。 这从匹配的 prepop 文件，生成 WinSAT 正式文件，并确保最终用户进行第一次引导系统时，WinSAT 正式文件是可用。 Windows 可以扩展，某些功能基于 WinSAT 正式文件，并且如果此文件不存在于系统中，则系统可能会遇到性能问题，包括不必要的存储设备碎片整理，缺乏优化内存管理和预取优化。

当运行**WinSAT moobe** WinSAT 检查结果文件的以下目录︰ `%WINDIR%\performance\winsat\datastore`。 如果 WinSAT 没有发现相关设置的.xml 文件，它将忽略不相关的文件，并将该系统视为未分级。 DWM 测试将立即运行，并且作为维护任务，或在最终用户选择从**性能信息和工具**控制面板项目中运行测试时将运行其他测试。 如果 WinSAT 找到一套相关 prepop.xml 文件，它使用文件来生成最终用户第一次启动计算机时将使用的正式的.xml 文件。 这使缩放的功能，并允许 Windows 执行适当的优化。

WinSAT 使用硬件 Id 确定相关性。 这包括︰ CPUID、 内存 DIMM 的配置、 硬盘型号和大小和视频卡 PNP id。 如果没有相关的辅助评估，则 WinSAT 将运行这两种的主要和辅助评估;例如，CPU 和内存。

此选择的配置上运行的第二个选项的优点是 WinSAT 评估可能要运行较少的配置和复制到类似系统。 缺点未分级，如果 WinSAT 文件集与当前系统无关，将忽略这些测试，系统将会被视为，以及优化和功能扩展不会执行最终用户启动计算机时。

## <a name="span-idwinsatprepopcommand-lineoptionsspanspan-idwinsatprepopcommand-lineoptionsspanspan-idwinsatprepopcommand-lineoptionsspanwinsat-prepop-command-line-options"></a><span id="WinSAT_Prepop_Command-line_Options"></span><span id="winsat_prepop_command-line_options"></span><span id="WINSAT_PREPOP_COMMAND-LINE_OPTIONS"></span>WinSAT Prepop 命令行选项


**预填充的语法如下所示︰**

`Winsat prepop [-datastore <directory>][-graphics | -cpu | -mem | -disk | -dwm]`

以下命令将运行 WinSAT: `Winsat prepop`。

您只能预填充一个子系统，如 DWM，具体取决于以下依存关系︰

-   DWM 评估可独立运行。

-   磁盘评估可独立运行。

-   CPU 评估需要提供相关的内存评估。

-   内存评估需要提供相关 CPU 评估。

-   图形评估需要提供相关 CPU 和内存评估存在。

**Moobe 的语法如下所示︰**

`Winsat moobe [-datastore <directory>]`

**WinSAT 文件命名模式如下所示︰**

对于 Windows 8，`%type%`标识符， `Prepop`。 这标识作为预填充结果的数据存储文件。 命名模式为︰

`%IdentifierDerivedFromDate% %Component%.Assessment(Prepop).WinSAT.xml`

其中`%IdentifierDerivedFromDate%`是年-月-日和时间形式，例如，`0012-08-01 14.48.28`在其中运行测试时在 2012 年 8 月 1 日下午 2:48:28。

从运行**winsat prepop**跟**winsat moobe**; 创建 WinSAT 正式文件或从运行**winsat 正式**使用下面的模式命名︰

`%IdentifierDerivedFromDate% Formal.Assessment(Initial).WinSAT.xml`

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Windows 部署选项](windows-deployment-options.md)

 

 






