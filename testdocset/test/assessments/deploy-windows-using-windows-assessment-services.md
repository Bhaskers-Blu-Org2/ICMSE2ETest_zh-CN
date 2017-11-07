---
title: "部署 Windows 使用 Windows 评估服务"
description: "部署 Windows 使用 Windows 评估服务"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: e86b9140-36dc-4802-b672-ffe94f1eed6a
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: f507b2c69910cd201fda42f431a47118d2cb9bd6
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="deploy-windows-using-windows-assessment-services"></a>部署 Windows 使用 Windows 评估服务


有三种方法可以设置上作业和相关资产。 您可以设置一个作业来执行以下︰

-   评估已有支持，运行操作系统的计算机。

-   受支持的操作系统部署到计算机，通过使用 Windows 评估服务，并评估该计算机。

-   使用其他部署工具或方法来将受支持的操作系统部署到计算机，然后评估计算机。

本主题介绍三个这些部署选项。

**若要将资源添加到作业和部署映像**

1.  在 Windows ASC，创建或打开一个作业。

2.  在**作业设置**单击**概述**，并确认**应用图像**复选框已选中。

3.  如果您想要插入匹配插在映像部署期间将存储资源调配的动态驱动程序的驱动程序的驱动程序，请选择**动态驱动程序设置**。

4.  在**作业设置****资源**，请单击，然后单击**添加**以选择您希望运行该作业的计算机。

5.  在**选择评估资产**窗口中，选择您想要评估，单击**下一步**，然后单击**完成**的计算机。

6.  在 Windows 下**评估资产**ASC 的右侧显示的计算机。 选择一台计算机**更改图像**选择想要应用到该计算机的图像和，然后单击**确定**。

    **请注意**  
    计算机和图像的体系结构必须匹配，不同之处在于，您可以选择基于 x86 映像部署到基于 x64 的计算机。

     

**若要将资源添加到作业，并使用自定义部署**

1.  在 Windows ASC，创建或打开一个作业。

2.  在**作业设置**单击**概述**，并确认**应用图像**复选框已选中。

3.  清除**动态驱动程序设置**复选框。

4.  在**作业设置****资源**，请单击，然后单击**添加**以选择您希望运行该作业的计算机。

5.  在**选择评估资产**窗口中，选择要评估的计算机，然后单击**下一步**。

6.  单击**&lt;使用预先部署映像&gt;**，然后单击**完成**。

    **请注意**  
    当使用安排作业**&lt;使用预先部署映像&gt;**，部署 Windows 并运行后才启动该作业**\\ \\%wasserver%\\放松\\脚本\\testmachine\\completedeployment.cmd 自动**在提升的命令提示符。

     

**若要将资源添加到作业，而不部署映像**

1.  在 Windows ASC，创建或打开一个作业。

2.  在**作业设置**单击**概述**，，然后清除**应用图像**复选框。

3.  在**作业设置****资源**，请单击，然后单击**添加**以选择您希望运行该作业的计算机。

4.  在**选择评估资产**窗口中，选择要评估的计算机，然后单击**完成**。

## <a name="related-topics"></a>相关的主题


[Windows 评估服务常见方案](windows-assessment-services-how-to-topics--wastechref.md)

 

 







