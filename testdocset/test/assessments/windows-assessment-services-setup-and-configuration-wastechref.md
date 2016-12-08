---
title: "Windows 评估服务安装和配置"
description: "Windows 评估服务安装和配置"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: f624a482-23c6-4f84-b16b-9431e7259ba8
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 817bdc80c5930c34d935e6196633c9ad10c8a1f1
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-assessment-services-setup-and-configuration"></a>Windows 评估服务安装和配置


在您开始使用评估工具之前，必须先初始化 Windows 评估服务。 多台 Windows ASC 计算机可以与同一 Windows 评估服务服务器进行通信。 额外的配置步骤包括准备可引导 Windows PE USB 驱动器有正在运行的操作系统安装的测试计算机上收集库存。 对于正在运行的操作系统安装的计算机，提供了 CompleteDeployment 脚本来添加这些计算机的库存。 您还必须添加驱动程序和图像到您的库存。 本主题中的过程将引导您完成此过程。

本主题︰

-   [正在初始化 Windows 评估服务](#configwas)

-   [配置符号](#bkmk-wasc-symbols)

-   [向 Boot.wim 添加网络适配器驱动程序](#bkmk-wac-nicdrivers)

-   [为测试计算机库存准备 Windows PE USB 驱动器](#prepwinpe)

-   [将测试计算机添加到您的清单](#addcomps)

-   [将驱动程序添加到驱动程序存储区](#adddrivers-was)

-   [添加图像和无人参与的答案文件](#addimages-was)

## <a name="a-href-idconfigwasainitializing-windows-assessment-services"></a><a href="" id="configwas"></a>正在初始化 Windows 评估服务


若要初始化 Windows 评估服务必须从服务器运行 Windows ASC。

**重要**  
必须在服务器上打开端口 8000，以便 Windows ASC 和测试计算机可以进行通信。 Windows 评估服务初始化添加防火墙规则来打开端口 8000。 如果它被阻止的组策略设置，将不会打开该端口。

 

1.  单击**开始**，然后键入**Windows 评估服务的客户端**，若要查找并打开该应用程序。

2.  在文本框中，键入安装 Windows 评估服务的服务器的名称，然后单击**确定**。

    第一次初始化服务器可能需要大约 15 到 30 分钟。 已成功初始化服务器时，将出现一条消息。

**警告**  
Windows 评估服务服务器在配置期间，Windows 部署服务 (WDS) 配置为列表窗口评估服务为客户端引导服务提供商的列表中第一个提供程序在网络上。 要有效应答所有客户端的第一个提供程序拒绝的请求与列表中的所有其他提供程序。 我们不建议您在生产服务器上安装 Windows 评估服务。

 

## <a name="a-href-idbkmk-wasc-symbolsaconfiguring-symbols"></a><a href="" id="bkmk-wasc-symbols"></a>配置符号


一些评估需要访问符号。 如果没有可用的符号，评估结果可能不正确或不完整。 互联网连接和访问 Microsoft 公共符号服务器满足该依赖项。 在其他情况下，在与 Internet 的连接不可用，像实验室环境，您可以在部署期间，使用无人参与的答案文件中配置符号访问或手动配置。

**通过使用无人参与的答案文件中配置符号环境变量**

1.  到了第三方组件的符号复制**%系统驱动器 %\\放松\\符号\\%处理器\_体系结构 %\\ ** Windows 评估服务服务器上。

2.  如果测试计算机不能访问 Internet 而无法访问 Microsoft 公共符号服务器，测试计算机连接到 Internet，按照[http://support.microsoft.com/kb/311503](http://go.microsoft.com/fwlink/p/?linkid=235360)中的说明下载匹配的 Windows 组件元件。 然后，将测试计算机移回原来的网络，并将复制到下载的符号**%系统驱动器 %\\放松\\符号\\%处理器\_体系结构 %\\ ** Windows 评估服务服务器上。

3.  在下更改部署映像无人参与的答案文件模板**c:\\放松\\脚本\\tempate**，通过添加以下`<FirstLogonCommands>`部分。 到最后一个命令序列的同步更新的订单编号。

    ``` syntax
    <SynchronousCommand>
    ```

    ``` syntax
       <Order>8</Order>
    ```

    ``` syntax
       <CommandLine>setx _NT_SYMBOL_PATH SRV*%systemdrive%\relax\symbols\%PROCESSOR_ARCHITECTURE%;%systemdrive%\relax\symbols\%PROCESSOR_ARCHITECTURE% /M</CommandLine>
    ```

    ``` syntax
       <Description>"Setting _NT_SYMBOL_PATH"</Description>
    ```

    ``` syntax
    </SynchronousCommand>
    ```

4.  清点或将映像部署到测试计算机，然后在文件中配置的符号路径︰ \\ \\&lt;服务器&gt;\\放松\\脚本\\testmachine\\setenvironment.cmd。

5.  部署 Windows 和清点您的测试计算机后，您必须设置正确的符号路径&lt;系统驱动器&gt;:\\放松\\setenvironment.cmd。

测试计算机 Windows 评估服务将映像部署到测试计算机后，将拥有\_NT\_符号\_PATH 环境变量。

有关如何设置符号路径，并将符号下载的详细信息，请参阅[MSDN︰ 符号支持](http://go.microsoft.com/fwlink/?LinkId=235359)。

**若要手动配置符号环境变量**

1.  打开文件资源管理器中，右键单击**计算机**，然后单击**属性**。

2.  在**属性**窗口中，单击**高级系统设置**。

3.  在**系统属性**窗口上的**高级**选项卡上，单击**环境变量**。

4.  在**系统变量**，请单击**新建**符号将环境变量设置通过使用以下方法之一︰

    -   **使用公共符号服务器 （需要 Internet 连接）**

        将计算机连接到 Internet，以便它可以访问 Microsoft 符号服务器，，然后配置\_NT\_符号\_在 http://msdl.microsoft.com/downloads/symbols 中使用 Microsoft 符号服务器的路径环境变量。

    -   **使用网络连接符号路径 （需要通过本地网络连接）**

        将计算机连接到本地，然后配置\_NT\_符号\_PATH 环境变量，使用内联网符号路径。

    -   **使用本地符号路径**

        将符号下载到 Windows 评估服务服务器计算机上，并指向该位置设置测试计算机\_NT\_符号\_要像在服务器上，使用这些符号的路径的路径环境变量**\\ \\WASServer\\放松\\符号**。

有关如何设置符号路径，并将符号下载的详细信息，请参阅[MSDN︰ 符号支持](http://go.microsoft.com/fwlink/?LinkId=235359)。

## <a name="a-href-idbkmk-wac-nicdriversaadding-network-adapter-drivers-to-bootwim"></a><a href="" id="bkmk-wac-nicdrivers"></a>向 Boot.wim 添加网络适配器驱动程序


将网络适配器 (NIC) 驱动程序添加到 Windows 部署服务使用的 Windows PE 映像。 仅当测试计算机需要现成的网卡驱动程序，以便在库存或在部署 Windows 映像后具有网络连接时，此步骤是必需的。 在 Windows PE 启动裸露金属计算机 （一台计算机没有安装操作系统） 时需要的 NIC 驱动程序。

**若要向 boot.wim 添加网卡驱动程序**

1.  在服务器上，为网卡驱动程序创建一个文件夹并将它们复制到该文件夹。 例如，如果您的驱动程序存储在共享位置中，您可以使用如下所示的命令︰

    ``` syntax
    robocopy \\Server\share\drivers  C:\Drivers\amd64NIC /MIR
    ```

2.  单击**开始**，单击**管理工具**，然后单击**Windows 部署服务**。

3.  展开**服务器**节点，然后展开您的服务器名称。

4.  **驱动程序**中，用鼠标右键单击，然后单击**添加驱动程序包**。

5.  在添加驱动程序包向导中，单击**选择文件夹中的所有驱动程序包**，再单击**浏览**。

6.  浏览到包含现成的 NIC 驱动程序的文件夹，然后单击**确定**。

7.  在添加驱动程序包向导中，单击**下一步**。

8.  在**可用的驱动程序包**页面，单击**下一步**。

9.  在**摘要**页上，单击**下一步**。

10. 驱动程序复制到驱动程序存储区中，单击**下一步**。

11. 在**驱动程序组**页上，单击**选择一个现有的驱动程序组**，验证**DriverGroup1**被选中，然后单击**下一步**。

12. 单击**完成**。

13. 在**服务器**节点中，单击**启动映像**，用鼠标右键单击想要插入该驱动程序，引导映像，然后单击**将驱动程序包添加到映像**。

14. 在**向启动映像添加驱动程序包**向导中的**开始之前**页上，单击**下一步**。

15. **选择驱动程序包**在页上，单击**包类**，然后单击**编辑**。

16. 删除所有内容除**净**，，然后单击**确定**。

17. 在**向启动映像添加驱动程序包**向导中，单击**搜索程序包**，请单击**下一步**，然后单击**下一步**再次。

18. 添加驱动程序时，单击**完成**。

启动映像现在有现成的网卡驱动程序。 对于每个 Windows 部署服务 boot.wim 体系结构重复这些步骤。

## <a name="a-href-idprepwinpeapreparing-the-windows-pe-usb-drive-for-test-computer-inventory"></a><a href="" id="prepwinpe"></a>为测试计算机库存准备 Windows PE USB 驱动器


要清点裸露金属计算机 （未安装操作系统的计算机），您必须创建可引导的 USB 驱动器启动计算机并将其添加到库存。 关于如何准备的可引导 Windows PE USB 驱动器的详细信息，请参阅[演练︰ 向 CD、 USB 闪存驱动器或 USB 硬盘安装 Windows PE](http://go.microsoft.com/fwlink/p/?linkid=219488)。 本演练通过使用默认的 Windows PE 映像 (WinPE.wim) 而自定义创建可引导介质。 库存的使用可引导的 USB 驱动器之前，必须将 RelaxWinPE.wim 文件到 USB 驱动器上的源文件夹。

**重要**  
列出清单测试基于 x86 的计算机，您必须使用基于 x86 的 Windows PE 映像。 要在基于 AMD64 的测试计算机的库存，必须使用基于 AMD64 的 Windows PE 映像。 此过程使用基于 x86 的图像。 如果您的测试计算机 x86 和基于 AMD64，创建每个体系结构使用 USB 驱动器。

 

**使用 Windows AS WinPE.wim 文件来替换 boot.wim 文件**

1.  在技术人员计算机上创建 Windows PE 构建环境的位置，键入以下命令︰

    ``` syntax
    xcopy %SystemDrive%\REMINST\Boot\x86\Images\RelaxWinPE.wim c:\winpe_x86\media\sources\boot.wim
    ```

    ``` syntax
    xcopy %SystemDrive%\REMINST\Boot\x64\Images\RelaxWinPE.wim c:\winpe_x64\media\sources\boot.wim
    ```

2.  重复上面的步骤来创建每个体系结构所需的测试计算机的 USB 驱动器。

    **重要**  
    列出清单测试基于 x86 的计算机，您必须使用基于 x86 的 Windows PE 映像。 要在基于 AMD64 的测试计算机的库存，必须使用基于 AMD64 的 Windows PE 映像。

     

现在，准备好的可引导 Windows PE USB 驱动器和网卡驱动程序均已到位，可以向服务器中添加清单并将其包含在您的项目和作业。

## <a name="a-href-idaddcompsaadding-test-computers-to-your-inventory"></a><a href="" id="addcomps"></a>将测试计算机添加到您的清单


您可以添加裸机计算机 （不包含正在运行的操作系统的计算机），也有到 Windows 评估服务正在运行的操作系统的计算机库存，以便可以使用评估工具来评估这些计算机。 当测试计算机没有运行的操作系统时，使用 USB 驱动器启动计算机并将它添加到 Windows 评估服务清单。 当测试计算机运行的操作系统，则使用 Windows 评估服务脚本以将其添加到 Windows 评估服务库存。

**警告**  
您不应在同一时间多个 Windows 评估服务服务器清单中包括一台测试计算机。 当一台测试计算机出现在多个 Windows 评估服务服务器清单时，它使每台服务器上的 Windows 部署服务实例之间的竞争条件。 如果您必须测试计算机从一个库存移动到另一个，在 Windows 评估服务的客户端 (Windows ASC)，删除计算机资产从第一个 Windows 评估服务清单，并将其添加到新的 Windows 评估服务服务器上的清单。

 

**若要添加裸机计算机清单**

1.  测试计算机中插入 usb 闪存盘。

2.  打开计算机，然后打开计算机 （如 esc 键） 引导设备选择菜单按键。

3.  选择为引导设备的 USB 驱动器。

    当计算机重新启动时，请提供以下信息︰

    -   计算机名。 计算机名称必须包含只能包含字母数字字符和短划线。 如果计算机名称包含下划线符号或其他扩展的字符，则计算机可能无法通过域名系统 (DNS) 中发现。 计算机名称必须是 15 个字符或更少。

    -   计算机的位置。 计算机位置必须为 78 个字符或更少。

    -   是否要执行驱动程序清理。 此操作将复制到 Windows 评估服务驱动程序存储区的计算机上找到驱动程序。

4.  在测试计算机中删除 USB 驱动器。 计算机将重新启动。

    **请注意**  
    如果您使用 Windows 评估服务部署映像，建议在 BIOS 中设置引导顺序，以便预启动执行环境 (PXE) 的启动顺序中的第一个。 这种方法，您不必手动按引导顺序键盘快捷方式和选择网络启动作业开始之前。

     

5.  从**「 开始 」**菜单打开 Windows ASC。 在**入门**页面上，验证服务器清单中已添加了正确的计算机数。

**若要添加正在运行的计算机的库存**

1.  在正在运行的测试计算机上登录到 Windows 评估服务服务器。 例如，在命令提示符下，键入︰

    ``` syntax
    Net use \\<servername>\relax /u:localadmin Pass.word
    ```

    **请注意**  
    此帐户和密码是在过程中设置的 Windows 评估服务安装和初始化。 这不是管理员帐户。

     

2.  在测试计算机上，删除 c:\\放松文件夹中，如果有的话。

3.  从提升的命令提示符下，运行 CompleteDeployment.cmd。 该命令的完整路径是\\ \\&lt;服务器名称&gt;\\放松\\脚本\\TestMachine\\CompleteDeployment.cmd。

    在命令提示符窗口中将出现哪些脚本的作用的说明。

4.  按 enter 键继续。 添加到库存时，计算机将重新启动。

    **警告**  
    如果计算机名称包含下划线，它可能不是可以通过 DNS，符合 RFC 要求到达。 在这种情况下，该计算机将不会添加到库存。 全新安装体验 (OOBE) 允许将计算机名称以下划线，但 Windows 评估服务库存并没有。

     

5.  从**「 开始 」**菜单打开 Windows ASC。 在**入门**页面上，验证服务器清单中已添加了正确的计算机数。

## <a name="a-href-idadddrivers-wasaadding-drivers-to-the-driver-store"></a><a href="" id="adddrivers-was"></a>将驱动程序添加到驱动程序存储区


当正在运行的计算机添加到您的清单时，收集和存储位于系统驱动器 %%的 Windows 评估服务服务器上的全新驱动程序从计算机\\放松\\驱动程序\\%计算机名 %。 仅当要将计算机添加到已运行的操作系统的 inventoty 时，将发生这种情况。 它不会发生这种情况使用 Windows PE USB 驱动器添加到库存的裸露金属的计算机上。 在下面的过程中，将这些驱动程序添加到驱动程序存储区，以便它们可供在映像部署过程中的驱动程序注入 Windows 部署服务。

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

    -   在**入门**页面上，单击**导入映像现在**选择的图像，单击**导入**，，然后单击**确定**。

    -   Windows ASC，在**服务器**菜单中单击**管理器库存**，单击**图像**选项卡，然后单击**添加**。

**将答案文件添加到共享位置**

1.  默认 Unattend.xml 应答文件为每个受支持的体系结构提供的系统驱动器 %%\\放松\\脚本\\模板。 您可以使用默认的应答文件，或可以复制的模板 Unattend.xml 和 Windows 系统映像管理器中修改它。 有关如何修改答案文件的详细信息，请参阅[Windows 系统映像管理器 (Windows SIM) 技术参考](http://go.microsoft.com/fwlink/?LinkId=214570)。

2.  Unattend.xml 答案文件复制到系统驱动器 %%\\放松\\unattendfiles。 如果您提供特定图像的单独的无人参与的应答文件，提供一个唯一名称为每个新答案文件之前将其复制到系统驱动器 %%\\放松\\unattendfiles。

3.  将图像添加到 Windows ASC 中的项目后，您可以指定您想要使用该映像的答案文件的路径。 在**服务器**菜单上单击**库存管理**。 在**图像**选项卡上更改**无人参与的路径**。

## <a name="related-topics"></a>相关的主题


[Windows 评估服务](windows-assessment-services-technical-reference.md)

[安装 Windows 评估服务](installing-windows-assessment-services-wastechref.md)

 

 







