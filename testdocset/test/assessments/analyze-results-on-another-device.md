---
title: "分析结果在另一个设备"
description: "分析结果在另一个设备"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 2775a4c2-6eb5-467c-b7b3-35529930cc16
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: c119d4c54cea3c0f213a19e5006921842b3c24cc
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="analyze-results-on-another-device"></a>分析结果在另一个设备


您可以运行在一台 PC，收集跟踪评估和分析数据在另一台计算机上或者在其他时间。 您可能想要收集如果不进行分析，以便跟踪︰

-   在采用更多的内存或更快的处理器的个人电脑上运行分析

-   要释放其他高优先级的时间延迟分析使用的机器

-   在已配置的符号的 PC 上运行

-   重新分析评估数据以后使用更新的诊断模块或符号

-   收集的数据，在所有设备上，但只有那些满足特定条件的分析

**若要收集跟踪文件但不运行分析**

1.  选择作业或要运行的评估。

2.  在**配置作业**屏幕中，选择**仅跟踪收集**。

3.  运行该作业。

4.  跟踪文件的评估将被保存到*%userprofile%\\文档\\评估结果*。

    **请注意**  
    收集跟踪文件，如果不进行分析不是可用于所有的作业和评估的。

     

## <a name="run-analysis-on-another-device"></a>在另一台设备上运行分析


您可以加载在 PC 上想要分析跟踪文件的符号。 有关详细信息，请参见[符号支持](../wpt/symbol-support.md)。

**跟踪文件使用 WAC 运行分析**

1.  在 Windows 评估控制台中，单击**选项**，然后单击**打开结果**以查看可供查看的所有作业结果。

2.  在**选择的结果**窗口中，选择要分析的结果。

3.  单击**打开**以打开详细信息视图中的结果。

    结果的**完整分析**一行显示**False**。

4.  单击**分析**。

    如果您有多个可以进行分析的结果打开，您可以选择哪些分析。

## <a name="related-topics"></a>相关的主题


[打包作业，并在另一台计算机上运行它](package-a-job-and-run-it-on-another-computer.md)

[导入结果](import-results.md)

 

 







