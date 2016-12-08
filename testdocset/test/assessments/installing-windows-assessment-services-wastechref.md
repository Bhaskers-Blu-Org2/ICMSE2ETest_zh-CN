---
title: "安装 Windows 评估服务"
description: "安装 Windows 评估服务"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: fbd2036a-8d3e-43ac-b8c9-3c499e7e8322
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 48fe05e94dca89961e0fc40f3d009332c289b1dd
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="installing-windows-assessment-services"></a>安装 Windows 评估服务


Windows 评估服务和 Windows 评估服务的客户端 (Windows ASC) 是 Windows 评估和部署工具包 (Windows ADK) 中可用。 您可以安装或下载 Windows ADK 和选择要安装的功能。

您必须在服务器计算机上，它还会在服务器上安装 Windows ASC 安装 Windows 评估服务。 您可以在客户端计算机上安装 Windows ASC 是独立版本，并使用它来连接到 Windows 评估服务。

Windows 评估服务服务器通过使用 Windows 部署服务支持预启动执行环境 PXE 基于映像部署。 Windows 评估服务服务器还维护库存数据库、 作业共享、 结果共享和各种用于自动化的脚本。 您可以使用 Windows ASC 来管理资产的库存中，设置和安排项目和作业，监视进度并查看结果。

本主题︰

-   [系统要求](#sysreq-was)

-   [安装 Windows 评估服务](#installwas)

-   [安装 Windows 评估服务客户端](#installwasc)

-   [备份窗口评估服务库存数据库](#installwasc-backupinventory)

-   [下一步行动](#installwasc-nextsteps)

## <a name="a-href-idsysreq-wasasystem-requirements"></a><a href="" id="sysreq-was"></a>系统要求


**服务器计算机**

若要安装 Windows 的评估服务，您的服务器必须满足以下要求︰

-   Windows Server 2012 或 Windows 服务器 2008 R2 企业、 标准版或数据中心版。 服务器核心、 Windows 服务器基本套件或域控制器的服务器上不支持 Windows 评估服务。

    默认情况下，Windows ASC 安装与 Windows 评估服务。 您必须安装在 Windows Server 2008 R2 上运行 Windows ASC 的远程管理 3.0。

    当您在 Windows Server 2012 服务器上安装了 Windows 评估服务时，Windows 部署服务 (WDS) 配置如下︰

    -   启用 Microsoft Windows 部署服务，Microsoft-Windows-Deployment-Services-Transport-Server，和 Microsoft-Windows-Deployment-Services-Deployment-Server。

    -   Windows 评估服务被列为通过网络客户端引导服务提供商的列表中的第一个提供程序。

    -   如果未初始化 WDS，Windows 评估服务对其进行初始化，并将 REMINST 文件夹设置 %系统驱动器 %\\REMINST。

    -   使用 Windows 评估服务安装的启动.wim 文件被添加到 WDS 映像库存。

    当您在 Windows Server 2008 R2 服务器上安装了 Windows 评估服务时，Windows 部署服务 (WDS) 配置如下︰

    -   启用 Microsoft Windows 部署服务和 Microsoft-Windows-Deployment-Services-Transport-Server。

    -   在系统驱动器 %%创建 REMINST 共享\\REMINST，该文件夹共享的并且权限被设置为 Windows ASC 用户 (localadmin)。

    -   启动文件从 Windows 评估服务安装目录.../ 放松/脚本、 复制到 REMINST 共享。

    -   WDS 组件，Wdstftp，配置。

    -   Windows 评估服务被列为通过网络客户端引导服务提供商的列表中的第一个提供程序。

    -   利用 Windows 评估服务已安装的启动.wim 文件被添加到 WDS 映像库存。

    -   WDS 服务器将重新启动。

    **请注意**  
    当您在服务器上安装了 Windows 的评估服务时，Windows 部署服务启用这些优点和限制︰

    -   Windows 部署服务配置为自动执行基于 PXE 的计算机发现和映像部署。 在部署时测试计算机的图像，您必须使用已使用 sysprep 工具通用化的 Windows 映像 (.wim) 文件。

    -   在 Windows Server 2012 Windows 评估服务使用 Windows 部署服务动态驱动程序资源调配 (DDP) 映像部署过程中，插入匹配插驱动程序。 Windows 评估服务不支持 Windows Server 2008 R2 DDP。 在两种服务器操作系统，您可以使用 DISM.exe.wim 映像脱机部署之前注入驱动程序。

    -   如果该服务器是域成员，则必须设置 Internet 协议安全 (IPsec) 排除策略使用 Windows 部署服务将映像部署和测试计算机上运行的评估。

    -   如果测试计算机上已经有支持正在运行的操作系统，或如果它是图像已部署外部 Windows 评估服务，您可以跳过 Windows 部署服务映像部署。

    -   支持 Internet 协议版本 4 (IPv4)。

     

-   Microsoft.NET Framework 3.5 和.NET Framework 4

    **请注意**  
    对于 Windows Server 2008 R2，默认情况下安装.NET Framework 3.5 和评估 Toolkit 安装.NET Framework 4。

     

    对于 Windows Server 2012，默认情况下安装.NET Framework 4 和安装 Windows 评估服务之前，您必须启用.NET Framework 3.5。 若要启用.NET Framework 3.5，在服务器上，在命令提示符下，键入以下命令︰

    ``` syntax
    DISM /Online /Enable-Feature /FeatureName:NetFx3 /All
    ```

-   网络︰ 1 千兆字节 (GB) 的网络适配器

-   硬盘空间︰ 50 GB 的内存，每台测试计算机。

-   内存︰ 8GB 最小，对于支持 100 多个测试计算机的服务器的 16 GB。

**技术人员计算机**

默认情况下，在安装 Windows 评估服务的服务器上安装了 Windows ASC。 此外可以在客户端计算机上安装它。 要安装 Windows ASC，您的计算机必须运行下列操作系统之一︰

-   使用远程管理 3.0 安装 Windows Server 2008 R2

-   Windows Server 2012

-   Windows 8

-   Windows 10

**测试计算机**

测试计算机必须满足下列要求︰

-   支持 USB 启动

-   网络 (PXE) 启动支持

-   网络适配器驱动程序

**网络基础结构**

至少，您的网络设施应满足下列要求︰

-   所有计算机都必须位于同一子网。 否则，Windows 评估服务服务器和 Windows 部署服务的 IP 地址应为使用 Windows 评估服务进行部署的所有测试计算机开关的 IP 帮助程序地址列表中。

-   动态主机配置协议 (DHCP) 服务器必须是可用来分配 IP 地址来测试计算机的同一网络上。

**安全说明︰**

出于安全目的，执行以下某项限制访问 Windows 评估服务服务器︰

-   通过使用组策略，如果计算机位于域中，或如果在工作组中的管理员阻止端口 8000 相同子集外部用户。

-   编辑服务器定义的范围中的防火墙规则︰

    -   一个特定的子网

    -   一个特定的 IP 范围

    -   预定义的计算机集

    -   特定的用户或特定计算机

## <a name="a-href-idinstallwasainstalling-windows-assessment-services"></a><a href="" id="installwas"></a>安装 Windows 评估服务


**重要**  
您可以升级到较新版本的 Windows 评估服务。 升级时，将保留在服务器上的评估结果。 项目、 作业和作业信息将不会被保留。

 

1.  在服务器计算机上，双击**ADKSetup.exe**。

2.  单击**下载**以下载 Windows ADK。 或者，如果在安装过程中，服务器可以保持与 Internet 的连接，单击**安装**。

3.  接受 Microsoft 软件许可条款。

4.  选择以下功能︰

    -   部署工具

    -   Windows 预安装环境

    -   Windows 评估服务

    -   Windows 性能 Toolkit

5.  单击**安装**。

**请注意**  
Microsoft SQL Server 2012年速成版的一个实例是与 Windows 评估服务一起安装的。 SQL Server 实例的名称是 ADK。 如果已命名 ADK 的 SQL Server 实例存在，应该删除，或将其重命名，然后再安装 Windows 评估服务。 如果不这样做，则使用现有的实例。

默认情况下，Windows ASC 会同时安装和 Windows 评估服务在服务器上。

 

## <a name="a-href-idinstallwascainstalling-windows-assessment-services---client"></a><a href="" id="installwasc"></a>安装客户端的 Windows 评估服务-


默认情况下，Windows ASC 安装在服务器上，当您安装 Windows 评估服务。 但是，您也会安装它的客户端 （或技术） 的计算机上。

1.  在技术人员的计算机上，双击**ADKSetup.exe**。

2.  单击**下载**以下载 Windows ADK。 或者，如果计算机在安装过程中可以保持与 Internet 的连接，单击**安装**。

3.  **部署工具**、 **Windows 评估服务客户端**，以及**Windows 性能 Toolkit**，选择，然后单击**安装**。

## <a name="a-href-idinstallwasc-backupinventoryabacking-up-the-windows-assessment-services-inventory-database"></a><a href="" id="installwasc-backupinventory"></a>备份窗口评估服务库存数据库


如果要升级的服务器操作系统，在安装 Windows 的评估服务，您必须重新启动 Windows 评估服务库存数据库和相关的任何自定义的脚本。 尽管不是必需的如果您要卸载并重新安装 Windows 的评估服务，我们也建议备份数据库和自定义脚本。

**要备份 Windows 评估服务清单数据库**

1.  安装 Microsoft SQL Server 管理 Studio 速成版 (ENU\\x86\\SQLManagementStudio\_x86\_ENU.exe)，从[Microsoft 下载中心获取](http://go.microsoft.com/fwlink/?LinkId=251597)。

2.  使用**net stop wassvc**停止 Windows 评估服务。

3.  打开 SQL Server 管理 Studio 2012 和分离 Windows 评估服务数据库。 有关如何分离的数据库，SQL Server 管理 Studio 2012 的详细信息，请参阅[MSDN︰ 分离数据库](http://go.microsoft.com/fwlink/?LinkId=251595)。

4.  复制的数据库 （.mdb 文件） 和事务日志从系统驱动器 %%\\ProgramData\\Windows 评估服务\\数据库，到安全的备份位置。

    **请注意**  
    如果您有自定义的.../relax/scripts 文件夹中的脚本，还将它们复制到一个安全的备份位置。

     

5.  卸载 Windows 评估服务，升级服务器操作系统，然后重新安装 Windows 评估服务。

6.  初始化 Windows 评估服务服务器，请打开 Windows ASC，然后连接到服务器。

7.  使用**net stop wassvc**停止 Windows 评估服务。

8.  打开 SQL Server 管理 Studio 2012 和分离时初始化 Windows 评估服务服务器创建新的 Windows 评估服务数据库。

9.  新数据库删除 %系统驱动器 %\\ProgramData\\Windows 评估服务\\数据库。

10. 将旧的数据库从备份位置复制到系统驱动器 %%\\ProgramData\\Windows 评估服务\\数据库。

11. 打开 SQL Server 管理 Studio 2012 并附加窗口评估服务数据库。 有关如何将附加的数据库，SQL Server 管理 Studio 2012 的详细信息，请参阅[MSDN︰ 附加数据库](http://go.microsoft.com/fwlink/?LinkId=251596)。

12. 将您的自定义的脚本放回中的.../relax/scripts 目录。

13. **净启动 wassvc**用于启动 Windows 评估服务。

## <a name="a-href-idinstallwasc-nextstepsanext-steps"></a><a href="" id="installwasc-nextsteps"></a>下一步行动


安装 Windows 评估服务和 Windows ASC 后, 初始化服务器和配置 Windows 评估服务和 Windows ASC 计算机之间的通信。 您可以配置多个 Windows ASC 计算机的 Windows 评估服务服务器进行通信。 有关详细信息，请参阅[Windows 评估服务安装和配置](windows-assessment-services-setup-and-configuration-wastechref.md)。

## <a name="related-topics"></a>相关的主题


[Windows 评估服务](windows-assessment-services-technical-reference.md)

 

 







