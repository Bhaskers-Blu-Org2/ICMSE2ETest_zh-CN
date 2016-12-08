---
author: Justinha
Description: "获取自定义 Windows 所需的工具"
ms.assetid: a52b4efe-ead0-4319-ae19-799d4e9d9e7b
MSHAttr: PreferredLib:/library/windows/hardware
title: "获取自定义 Windows 所需的工具"
ms.openlocfilehash: fe6e727e80712af4385014dfeb61f8ba1384a8d5
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="get-the-tools-needed-to-customize-windows"></a>获取自定义 Windows 所需的工具


以下是您需要开始测试和部署的设备︰

## <a name="span-idpcspanspan-idpcspanpcs"></a><span id="pc"></span><span id="PC"></span>个人电脑


以下是我们将引用它们︰

-   **技术人员计算机**︰ 计算机所做的工作。 这台电脑应该有至少 15 GB 可用空间为安装[Windows 的评估和部署工具包 (Windows ADK)](http://go.microsoft.com/fwlink/?LinkId=526803)和修改 Windows 映像。 我们建议使用最新的更新 Windows 10 或 Windows 8.1。 最低要求是 Windows 7 SP1，尽管这可能需要其他工具或解决办法的任务，如装入。ISO 映像。

    对于大多数任务，您可以使用 x86 或 x64 的 PC。 如果您正在创建 x86 映像，您需要基于 x86 的 PC 为一个特定的一次性任务，[生成编录文件的基于 x86 的 Pc](update-windows-settings-and-scripts-create-your-own-answer-file-sxs.md)。

-   **参考设备**︰ 一个测试 PC 或 tablet 表示的所有设备中的单个模型行;例如， *Fabrikam 笔记本 PC 系列 1*。 此设备必须满足的 Windows 10 最低硬件要求。

    您将重新格式化该设备作为演练的一部分。

## <a name="span-idhwspanspan-idhwspanstorage"></a><span id="hw"></span><span id="HW"></span>存储


-   **WinPE usb 闪存盘**︰ 必须至少 512 MB 和最大 32GB。 该驱动器将被格式化，因此首先保存您的数据离开它。 它不应为 Windows 到转键或键标记为非可移动驱动器。

-   **存储 usb 闪存盘**(USB-B): 第二个 usb 闪存盘或外部 USB 硬盘驱动器上用于存储文件。 最小可用空间︰ 8 GB，使用 NTFS，ExFAT，或者任何其他允许文件超过 4 GB 的文件系统。  如果您的硬件允许，使用 USB 3.0 的键驱动器和 USB 3.0 端口来加快文件复制过程。 请注意，一些 USB 2.0 端口，带有某些 USB 3.0 键不起作用。 我们将不会被重新格式化的驱动器，因此，只要您有足够的可用空间，您可以重新使用现有的存储驱动器。 

## <a name="span-idswspanspan-idswspansoftware"></a><span id="sw"></span><span id="SW"></span>软件

将以下源文件复制到技术人员计算机上，而不是使用外部源，例如，网络共享或可移动驱动器。 这减少了中断生成过程从暂时的网络问题或断开 USB 设备的风险。

若要完成本指南，请从<https://www.microsoftoem.com>本节中获取推荐的下载。 

Windows ADK 的版本号，则 Windows 图像将部署，并必须匹配的语言和您要添加的功能。

此实验室假定 64 位体系结构，因此，如果您使用的 32 位版本，更改所有提及的 x64 的 x86。

### <a name="windows-10-version-1607-image-installwim"></a>第 10 Windows 版本 1607年图像 (install.wim)

|  |  |
|-----------|----------------------------------------------------|
| X21 08790 | Windows 家庭 10 版 1607年 32/64 位英语 OPK    |
| X21 08794 | Windows 家庭 SL 10 版 1607年 32/64 位英语 OPK |
| X21 08798 | Windows 专业 10 版 1607年 32/64 位英语 OPK     |

-   装载到驱动器中，ISO 文件，请注意驱动器号，例如，d。

-   复制 d:\\源\\install.wim 文件中，并将其保存到文件夹中的本地驱动器︰ **c:\\图像\\Win10\_x64\\**。

### <a name="windows-assessment-and-deployment-kit-adk-for-windows-10-version-1607"></a>Windows 评估和部署工具包 (ADK) Windows 10，1607年版本的

[Windows 10 为 Windows ADK、 版本 1607年](http://go.microsoft.com/fwlink/?LinkId=526803)或 X21 05999︰ 赢得 10 ADK

### <a name="customizations-windows-updates-languages-features-apps-and-microsoft-office"></a>自定义项︰ Windows 更新、 语言、 功能、 应用程序和 Microsoft Office

|  |  |
|-----------|---------------------------------------------------|
| X21 08801 | 赢取 10 1607年 32/64 MultiLang OPK LangPackAll/唇   |
| X21 08802 | 赢取 10 1607年 32/64 MultiLang OPK 特征即需即装    |
| X21 08808 | 赢取 10 1607年 32/64 MultiLang OPK 应用程序更新        |
| X21 19559 | 赢取 10 1607 OPK ZDP                               |
| X20 98485 | 办公移动 MultiLang v1.3 OPK                  |
| X21 05453 | 对于 OEM OPK 办公室 2016 v16.2 部署工具     |
| X21 05414 | Office 2016 v16.2 英语 OPK                     |
| X21 05508 | Office v16.2 德语 OPK                           |

我们还将讨论如何在本指南中添加的硬件驱动程序和其他 Windows 应用程序，实现这些硬件/软件制造商。

### <a name="product-keys"></a>产品密钥

从套件指南 Windows 10 默认制造键 OEM PDF 中，ISO 与 Windows 映像上获取默认值对于每个 Windows 版本的产品密钥。

获取分布与 Windows 10 图像匹配的产品密钥。

### <a name="sample-files-create-a-deployment-usb-drive"></a>示例文件︰ 创建部署 USB 驱动器

1.  USB 驱动器格式化 NTFS 文件格式，将它命名为 USB b。

    ![提取 USB](images/extract-usb.png) 

2.  从[USB B.zip](http://download.microsoft.com/download/5/8/4/5844EE21-4EF5-45B7-8D36-31619017B76A/USB-B.zip)，下载大部分实验室样本，并将文件解压缩到驱动器。

    添加到此[新版本的部署示例脚本](http://go.microsoft.com/fwlink/p/?LinkId=800657)。 

## <a name="span-idpreparespanspan-idpreparespanprepare-your-technician-pc"></a><span id="prepare"></span><span id="PREPARE"></span>准备您的技术人员计算机

下面介绍了如何设置您的 PC。

**将 Windows 映像复制到本地驱动器**

1.  装载您下载 Windows ISO 文件 (用鼠标右键单击该文件&gt;**装载**)，并注意到驱动器号，例如，d。

2.  文件资源管理器中创建一个新文件夹 (示例︰ **c:\\图像\\Win10\_x64**)，并将 Windows 映像复制 (d:\\源\\install.wim) 到文件夹的文件。 这将在以后帮助速度文件的创建过程。

**对于 Windows 10 安装 Windows ADK**

1.  如果您有早期版本的 Windows 评估和部署工具包 (ADK)，请将其卸载。

2.  下载[Windows ADK](https://developer.microsoft.com/en-us/windows/hardware/windows-assessment-deployment-kit#winADK)您正在安装的 Windows 版本相匹配的版本。 **运行**安装程序。

3.  单击**下一步** &gt; **下** &gt; **接受**以接受默认值并加入客户体验改善计划。

4.  选择以下工具︰

    -   **部署工具**

    -   **Windows 预安装环境 (Windows PE)**

    -   **用户状态迁移工具 (USMT)**

    对于这些实验室中，您不需要**Windows 性能 Toolkit**或**Windows 评估 Toolkit**。 您可以清除这些复选框。

5.  单击**安装**，然后单击**是**确认。 这可能需要几分钟的时间。

6.  完成安装后，单击**关闭**。

下一步︰[实验室 1︰ 安装 Windows PE](install-windows-pe-sxs.md)
