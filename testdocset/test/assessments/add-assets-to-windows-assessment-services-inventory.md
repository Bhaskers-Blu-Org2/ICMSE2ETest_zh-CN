---
title: "将资源添加到 Windows 评估服务清单"
description: "将资源添加到 Windows 评估服务清单"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: bddc94de-3531-4de9-a1bc-5ae359d1f6c6
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 759254f00694edb9949121925739d5ce17ec2820
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add-assets-to-windows-assessment-services-inventory"></a>将资源添加到 Windows 评估服务清单


本主题介绍如何将资产，例如计算机、 Windows 映像和无人参与的答案文件添加到 Windows 评估服务库存。 然后可以部署和评估各种计算机和 Windows 映像中库存中使用的评估工具。 驱动程序添加到 Windows 部署服务驱动程序存储区，以便他们可以被注入到 Windows 映像部署过程。

本主题︰

-   [将测试计算机添加到您的清单](#addcomps)

-   [将驱动程序添加到驱动程序存储区](#adddrivers-was)

-   [添加图像和无人参与的答案文件](#addimages-was)

## <a name="a-href-idaddcompsaadding-test-computers-to-your-inventory"></a><a href="" id="addcomps"></a>将测试计算机添加到您的清单


您可以添加裸露金属计算机 （没有正在运行的操作系统的计算机），并安装到 Windows 评估服务库存正在运行的操作系统的计算机。 然后可以使用评估工具来评估这些计算机。 当测试计算机运行的操作系统，则使用 Windows 评估服务脚本以将其添加到库存。 当测试计算机没有运行的操作系统，请使用 USB 闪存驱动器启动计算机并将其添加到库存。 有关如何将裸露金属的计算机添加到清单的详细信息，请参阅[部署和评估裸露的金属计算机的准备](prepare-to-deploy-and-assess-a-bare-metal-computer.md)。

**警告**  
您不应在同一时间多个 Windows 评估服务服务器清单中包括一台测试计算机。 当一台测试计算机出现在多个 Windows 评估服务服务器清单时，它使每台服务器上的 Windows 部署服务实例之间的竞争条件。 如果您必须测试计算机从一个库存移动到另一个，在 Windows 评估服务的客户端 (Windows ASC)，删除计算机资产从第一个 Windows 评估服务清单，并将其添加到新的 Windows 评估服务服务器上的清单。

 

**将正在运行的计算机添加到库存**

1.  在正在运行的测试计算机上登录到 Windows 评估服务服务器。 例如，在命令提示符处，键入︰

    ``` syntax
    Net use \\<servername>\relax /u:localadmin Pass.word
    ```

    **请注意**  
    此帐户和密码是在过程中设置的 Windows 评估服务安装和初始化。 这不是管理员帐户。

     

2.  在测试计算机上，删除 c:\\放松文件夹中，如果有的话。

3.  在提升的命令提示符下，运行 CompleteDeployment.cmd。 该命令的完整路径是\\ \\*&lt;服务器名称&gt;*\\放松\\脚本\\TestMachine\\ CompleteDeployment.cmd。

    在命令提示符窗口中将出现哪些脚本的作用的说明。

4.  按 enter 键继续。 添加到库存时，计算机将重新启动。

    **警告**  
    如果计算机名称包含下划线，它可能不是可以通过 DNS，符合 RFC 要求到达。 在这种情况下，该计算机将不会添加到库存。 全新安装体验 (OOBE) 允许将计算机名称以下划线，但 Windows 评估服务库存并没有。

     

5.  从**「 开始 」**菜单打开 Windows ASC。 在**入门**页面上，验证服务器清单中已添加了正确的计算机数。

## <a name="a-href-idadddrivers-wasaadding-drivers-to-the-driver-store"></a><a href="" id="adddrivers-was"></a>将驱动程序添加到驱动程序存储区


当正在运行的计算机添加到您的清单时，收集和存储位于系统驱动器 %%的 Windows 评估服务服务器上的全新驱动程序从计算机\\放松\\驱动程序\\%计算机名 %。 仅当要将计算机添加到正在运行的操作系统都有库存时，将发生这种情况。 它不会发生这种情况使用 Windows PE USB 驱动器添加到库存的裸露金属的计算机上。 在下面的过程中，将这些驱动程序添加到驱动程序存储区，以便它们可供在映像部署过程中的驱动程序注入 Windows 部署服务。

**警告**  
以下步骤仅适用于 Windows Server 2012。 如果您使用的 Windows Server 2008 R2，您必须注入驱动程序图像之前部署，因为在 Windows 部署服务的动态驱动程序设置在 Windows Server 2008 R2 上不支持。

 

**若要导入到驱动程序存储区中的驱动程序**

1.  单击**开始**，单击**管理工具**，然后单击**Windows 部署服务**。

2.  展开**服务器**节点，然后展开您的服务器名称。

3.  **驱动程序**中，用鼠标右键单击，然后单击**添加驱动程序包**。

4.  在添加驱动程序包向导中，单击**选择文件夹中的所有驱动程序包**，再单击**浏览**。

5.  浏览到 c:\\放松\\驱动程序文件夹，然后单击**确定**。

6.  在添加驱动程序包向导中，单击**下一步**。

7.  在**可用的驱动程序包**页面，单击**下一步**。

8.  在**摘要**页上，单击**下一步**。

9.  驱动程序复制到驱动程序存储区中，单击**下一步**。

10. 在**驱动程序组**页上，单击**选择一个现有的驱动程序组**，验证**DriverGroup1**被选中，然后单击**下一步**。

11. 单击**完成**。

## <a name="a-href-idaddimages-wasaadding-images-and-unattended-answer-files"></a><a href="" id="addimages-was"></a>添加图像和无人参与的答案文件


将其导入到清单数据库并将它们用于部署之前，您必须复制到映像共享 Windows 映像 (.wim) 文件。

**若要将图像添加到图像共享和库存**

1.  在 Windows 评估服务服务器上，将.wim 文件复制到 c:\\放松\\图像。

    **请注意**  
    图像路径不能包含空格。

     

2.  这些图像在 Windows 评估服务服务器映像共享，但它们还没有被导入到清单数据库。 若要将图像导入到清单数据库，使用以下方法之一︰

    -   **入门**页面上单击**现在导入图像**，并选择图像。 **导入**，请单击，然后单击**确定**。

    -   Windows ASC，在**服务器**菜单中单击**管理器库存**，单击**图像**选项卡，然后单击**添加**。

**将答案文件添加到共享位置**

1.  默认 Unattend.xml 应答文件为每个受支持的体系结构提供的系统驱动器 %%\\放松\\脚本\\模板。 您可以使用默认的应答文件，或可以复制的模板 Unattend.xml 和 Windows 系统映像管理器中修改它。 有关如何修改答案文件的详细信息，请参阅[Windows 系统映像管理器 (Windows SIM) 技术参考](http://go.microsoft.com/fwlink/?LinkId=214570)。

2.  Unattend.xml 答案文件复制到系统驱动器 %%\\放松\\unattendfiles。 如果您提供特定图像的单独的无人参与的应答文件，提供一个唯一名称为每个新答案文件之前将其复制到系统驱动器 %%\\放松\\unattendfiles。

3.  当您将图像添加到项目中，Windows ASC 时，指定您想要使用该映像的答案文件的路径。

    **重要**  
    当部署到 OEM 激活 3.0 (OA 3.0) 的系统映像，使用与图像关联的产品密钥 unattend.xml 自定义答案文件。

     

**若要将答案文件与映像相关联**

1.  在**服务器**菜单上单击**库存管理**。

2.  在**资产清单**窗口中，单击**图像**选项卡，然后使用筛选器文本框中添加筛选条件，以便您可以找到您正在寻找的图像。

3.  用鼠标右键单击列标题，然后单击**无人参与的路径**显示为一列此字段。

4.  使用垂直滚动条查找**无人参与路径**列。 默认情况下，此字段为空。 双击字段中，输入您想要使用所选的图像，例如系统驱动器 %%的应答文件的 UNC 路径\\放松\\unattendfiles\\*&lt;我\_答案\_文件&gt;*.xml。

## <a name="related-topics"></a>相关的主题


[Windows 评估服务常见方案](windows-assessment-services-how-to-topics--wastechref.md)

 

 







