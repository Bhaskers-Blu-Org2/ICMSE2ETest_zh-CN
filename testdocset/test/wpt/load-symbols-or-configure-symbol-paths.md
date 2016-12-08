---
title: "加载符号或符号路径进行配置"
description: "加载符号或符号路径进行配置"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 1f29aadf-a323-4c24-8d46-3eae3e0c2b76
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: c8c259aa589c14fc2de1f032f1654a27b1da91cd
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="load-symbols-or-configure-symbol-paths"></a>加载符号或符号路径进行配置


在 Windows 性能分析器 (WPA)，您可以设置记录加载符号或更改符号路径。

**若要设置录制加载符号**

-   在**跟踪**菜单中，单击**加载符号**。

**请注意**  
当您单击图形资源管理器窗口和分析选项卡上方**加载符号**，进度栏 （以及找到的符号的计数）。 此外，在关系图本身，数据方面成为灰和每个数据区域中显示一个进度栏。

 

**若要更改符号路径**

1.  在**跟踪**菜单中，单击**配置符号路径**。 默认情况下，打开对话框的路径选项卡上

2.  输入或选择所需的路径，然后再单击**确定**。

**可被缓存的符号文件复制到 SymCache 文件夹**

1.  在**跟踪**菜单中，单击**配置符号路径**。 默认情况下，在路径选项卡上打开对话框。

2.  单击**SymCache**。 所有正文中的 SymCache 选项卡，您可以滚动以查找特定的 SymCache 文件路径存储 （使用相应的路径） 的文件显示。

    **请注意**  
    无效的路径显示为红色。

     

3.  选择 SymCache 生成文件夹，然后单击**浏览文件夹**图标可搜索的位置您的 SymCache 文件存储，然后在浏览文件夹对话框上单击**确定**。

4.  选择要保存到 SymCache 生成文件夹中前面的步骤中，指定每个 SymCache 路径，然后单击**确定**。

5.  选择要保存到 SymCache 生成文件夹中前面的步骤中，指定每个 SymCache 路径，然后单击**确定**。

**若要更改加载设置配置符号时**

1.  在**跟踪**菜单中，单击**配置符号路径**。 默认情况下，在路径选项卡上打开对话框。

2.  单击**加载设置**。

3.  选择要加载符号根据以下选项︰

    -   装载后加载符号
    -   加载符号按以下限制︰

    **请注意**  
    当选择**加载符号按以下限制条件︰**选项，您可以指定是否要加载的指定进程的符号，也可以选择不加载特定的图像符号。 您可以选择指定的流程和图像的限制。

     

4.  单击**确定**。

## <a name="related-topics"></a>相关的主题


[WPA 常见方案](windows-performance-analyzer-common-scenarios.md)

[加载符号](loading-symbols.md)

 

 







