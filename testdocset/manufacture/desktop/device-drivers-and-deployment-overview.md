---
author: Justinha
Description: "设备驱动程序"
ms.assetid: daa94074-a23d-4788-8e32-0e27c0a62d88
MSHAttr: PreferredLib:/library/windows/hardware
title: "设备驱动程序"
ms.openlocfilehash: cb54f07ab351a1b8bf9fd9af43cf2852a26ef1e2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="device-drivers"></a>设备驱动程序


可以将设备驱动程序添加到 Windows 映像之前、 期间或之后部署映像。 在规划时如何将驱动程序添加到 Windows 部署，就一定要了解如何将驱动程序文件夹添加到图像上时，驱动程序分级如何影响部署中，以及驱动程序的数字签名要求。

本主题︰

-   [添加驱动程序](#addingdrivers)

-   [管理驱动程序文件夹](#drivermgmt)

-   [了解驱动程序分级](#driverranking)

-   [了解数字签名要求](#signaturereqs)

-   [其他资源](#resources)

## <a name="span-idaddingdriversspanspan-idaddingdriversspanspan-idaddingdriversspanadding-drivers"></a><span id="AddingDrivers"></span><span id="addingdrivers"></span><span id="ADDINGDRIVERS"></span>添加驱动程序


可以将设备驱动程序添加到 Windows 映像︰

-   [对脱机 Windows 映像进行部署之前](#offline)

-   [在自动部署过程](#automated)

-   [在正在运行的操作系统上部署](#online)

有关详细信息，请参阅[了解处理策略](understanding-servicing-strategies.md)。

### <a name="span-idofflinespanspan-idofflinespanadd-drivers-before-deployment-on-an-offline-windows-image-by-using-dism"></a><span id="offline"></span><span id="OFFLINE"></span>通过使用 DISM 脱机 Windows 映像上添加驱动程序才能部署

当您修改完全脱机 Windows 映像而不启动操作系统时，即开始脱机服务。 您可以添加、 删除和枚举上脱机 Windows 映像的驱动程序通过使用 DISM 命令行工具。 DISM 安装 windows 并还分发 Windows 评估和部署工具包 (Windows ADK) 中。 有关 DISM 的详细信息，请参阅[DISM 的部署映像服务和管理技术参考的窗口](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md)。

将驱动程序添加到脱机映像时，它已转移，或将图像中反映出来︰

-   **引导关键驱动程序**将反映出来。 换句话说，这些文件将复制到根据.inf 文件中指定的图像。 PC 在初始启动，包括关键设备数据库 (CDDB) 和注册表更新过程中完成安装任务。

-   转移**的不是启动关键驱动程序**。 换句话说，它们会添加到驱动程序存储区。 Windows 启动后，即插即用将检测该设备并从驱动程序存储区中安装匹配的驱动程序。

您可以使用 DISM 命令添加或删除驱动程序的安装，或应用 Windows 或 Windows 预安装环境 (Windows PE) 映像。

**请注意**  
您不能使用 DISM 删除收件箱驱动程序 （默认情况下在 Windows 安装的驱动程序）。 可以使用它来删除第三方或现成的驱动程序。

 

此外可以使用 DISM 命令应用到已装载或应用 Windows 映像无人参与的答案文件。

有关详细信息，请参阅[添加和删除脱机 Windows 映像的驱动程序](add-and-remove-drivers-to-an-offline-windows-image.md)。

如果您正在使用 DISM，可以只.inf 驱动程序添加到脱机 Windows 映像。 以.cab 文件提供了显示专为 Windows 徽标的驱动程序。 如果您的安装使用 DISM 安装.inf 文件之前，必须展开.cab 文件。 您必须安装的驱动程序打包为.exe 文件或其他文件上运行的 Windows 操作系统的类型。 若要运行.exe 或 Windows 安装程序 (.msi) 驱动程序包，可以将自定义命令添加到答案文件以安装驱动程序包。 有关详细信息，请参阅[添加到答案文件中自定义命令](https://msdn.microsoft.com/library/windows/hardware/dn915058)。

### <a name="span-idautomatedspanspan-idautomatedspanadd-drivers-during-an-automated-deployment-by-using-windows-setup-and-an-answer-file"></a><span id="automated"></span><span id="AUTOMATED"></span>在自动部署过程中添加的驱动程序，使用 Windows 安装程序和答案文件

无人参与的答案文件可用于向图像中添加驱动程序，当您使用 Windows 安装程序以进行部署。 在此答案文件中，可以指定网络共享上的设备驱动程序的路径 （或本地路径）。 通过添加 Microsoft 的 Windows PnpCustomizationWinPE 或 Microsoft 的 Windows PnpCustomizationNonWinPE 组件实现此目的，并指定配置传递想要安装它们。 当您运行 Windows 安装程序并指定应答文件的名称，转移出的全新驱动程序 （添加到图像上的驱动程序存储区），以及反映启动关键驱动程序 （添加到映像，以便在计算机启动时将使用它们）。 安装将使用应答文件。 通过在**windowsPE**或**offlineServicing**配置阶段期间添加设备驱动程序，可以现成的设备驱动程序添加到 Windows 映像之前在计算机重新启动。 您可以使用此方法将引导所必需设备驱动程序添加到 Windows 映像。 有关详细信息，请参阅[添加设备驱动程序与 Windows 安装过程中 Windows](add-device-drivers-to-windows-during-windows-setup.md)。 有关 Windows 安装程序是如何工作的详细信息，请参阅[Windows 安装程序技术参考](windows-setup-technical-reference.md)。

如果您想要添加到 Windows PE 启动关键驱动程序，使用**windowsPE**配置阶段引导 Windows PE 映像之前反映了驱动程序。 添加在**windowsPE**配置过程的启动关键驱动程序将传递，并将它们添加在**offlineServicing**配置阶段之间的区别是，在**windowsPE**配置阶段，使用 Windows PE 为反映启动关键驱动程序。 在**offlineServicing**配置阶段，驱动程序将转移到存储在 Windows 映像中的驱动程序。

通过使用 Windows 安装程序添加设备驱动程序的方法包括︰

-   使用应答文件**offlineServicing**配置阶段的设置期间添加驱动程序。

-   使用应答文件在**windowsPE**配置阶段的设置过程中添加的驱动程序。

-   For Windows Server®，将驱动程序放置在 $ $WinPEDriver 目录在**windowsPE**配置阶段的设置过程中自动安装。 $WinPEDriver$ 目录扫描所有驱动器号为 C 或更高的值。 在安装过程中，驱动器必须能够访问到硬盘。 请确保该驱动器不需要存储驱动程序加载才可以访问它。

有关这些和其他配置阶段的详细信息，请参阅[Windows 安装程序配置阶段](windows-setup-configuration-passes.md)。

当您使用 Windows 服务器中部署 Windows 部署服务时，可以将设备驱动程序添加到您的服务器并将其配置为基于网络的安装的一部分部署到客户端。 您配置此功能通过在服务器上，创建驱动程序组，添加程序包，然后添加筛选器定义哪些客户端将安装这些驱动程序。 基于客户端的硬件 （例如，制造商或 BIOS 供应商） 和安装期间选择的 Windows 映像的版本，您可以配置要安装的驱动程序。 此外可以配置客户端是安装驱动程序组或匹配客户机上安装的硬件的驱动程序中的所有软件包。 有关如何实现此功能的详细信息，请参阅 Windows 部署服务文档。

### <a name="span-idonlinespanspan-idonlinespanadd-drivers-after-deployment-on-a-running-operating-system-by-using-pnputil-or-an-answer-file"></a><span id="online"></span><span id="ONLINE"></span>使用 PnPUtil 或应答文件上运行的操作系统部署后添加驱动程序

可以使用 PnPUtil 工具来添加或删除驱动程序上运行的操作系统。 或者，可以使用答案文件自动安装驱动程序，在审核模式下启动计算机时。 这些方法可能会有所帮助，如果您想要保持一个简单的 Windows 映像，然后添加所需的特定硬件配置的驱动程序。 有关如何使用审核模式，请参阅[启动到审核模式或 OOBE 的 Windows](boot-windows-to-audit-mode-or-oobe.md)的详细信息。

将设备驱动程序添加到正在运行的操作系统的方法包括︰

-   使用 PnPUtil 添加或删除即插即用的驱动程序。 有关详细信息，请参阅[使用 PnPUtil 命令行来安装即插即用设备](http://go.microsoft.com/fwlink/?LinkId=139151)。

-   使用答案文件自动安装即插即用驱动程序时在审核模式下启动计算机。 有关详细信息，请参阅[添加驱动程序在线在审核模式下](add-a-driver-online-in-audit-mode.md)。

## <a name="span-iddrivermgmtspanspan-iddrivermgmtspanspan-iddrivermgmtspanmanaging-driver-folders"></a><span id="DriverMgmt"></span><span id="drivermgmt"></span><span id="DRIVERMGMT"></span>管理驱动程序文件夹


如果您要添加多个驱动程序，则应创建单独为每个驱动程序或驱动程序类别的文件夹。 这可以确保当您添加具有相同文件名的驱动程序没有任何冲突。 在操作系统上安装驱动程序后，将其重命名为 Oem\*.inf 以确保在操作系统中唯一的文件名。 例如，命名为 MyDriver1.inf 和 MyDriver2.inf 的暂存驱动程序被重命名为 Oem0.inf 和 Oem1.inf 他们正在安装后。

答案文件中指定的设备驱动程序路径时，指定的目录和子目录中的所有.inf 驱动程序都添加到 Windows 映像，%systemroot%\system32\driverstore\filerepository 的驱动程序存储区中。 例如，如果您希望在 c︰ 驱动器的驱动程序的所有\\MyDrivers\\网络、 c:\\MyDrivers\\视频和 c:\\MyDrivers\\在 Windows 映像中可用的音频目录指定的设备驱动程序路径，c:\\MyDrivers，在应答文件中的。 如果您没有使用答案文件，则可以使用 DISM 中**/recurse**命令。 有关**/recurse**命令的详细信息，请参阅[DISM 驱动程序服务命令行选项](dism-driver-servicing-command-line-options-s14.md)。 此命令将确保，每个子目录中的所有驱动程序将被添加到 Windows 映像中的驱动程序存储区。

如果指定的目录和子目录中的所有驱动程序添加到映像中，应当小心管理答案文件或 DISM 命令和这些目录。 尽全力解决问题，有关增加不必要的驱动程序包通过图像的大小。

如果不是实际管理驱动程序共享以便只有必需的驱动程序添加到映像，可以使用该驱动程序包安装程序 (DPInst) 工具添加联机不启动关键驱动程序。 有选择地，DPInst 安装存在硬件时才或更好的匹配的设备驱动程序包是否不启动关键驱动程序。

## <a name="span-iddriverrankingspanspan-iddriverrankingspanspan-iddriverrankingspanunderstanding-driver-ranking"></a><span id="DriverRanking"></span><span id="driverranking"></span><span id="DRIVERRANKING"></span>了解驱动程序分级


当驱动程序成功导入到驱动程序存储区，但，系统在线、 即插即用后找到一个高级驱动程序，安装该驱动程序，而是发生部署驱动程序的最常见的问题之一。

Windows 即插即用管理器按重要性的顺序排列这些驱动程序的包属性︰

1.  签名

2.  即插即用 ID 匹配

3.  驱动程序日期

4.  驱动程序版本

例如，如果设备具有更好的 PnP ID 匹配项，但没有签名，签名的驱动程序兼容 ID 匹配的优先。 旧的驱动程序可以 outrank 更新的驱动程序，如果旧的驱动程序具有更好的 PnP ID 匹配项或签名。

有关驱动程序分级的详细信息，请参阅[如何 Windows 通道驱动程序](http://go.microsoft.com/fwlink/?LinkId=91227)。

## <a name="span-idsignaturereqsspanspan-idsignaturereqsspanspan-idsignaturereqsspanunderstanding-digital-signature-requirements"></a><span id="SignatureReqs"></span><span id="signaturereqs"></span><span id="SIGNATUREREQS"></span>了解数字签名要求


有签名的设备驱动程序是 Windows 中的主要安全功能。 在基于 x64 的计算机安装的驱动程序必须具有数字签名。 虽然它不是必需的但我们建议确保驱动程序之前安装基于 x86 的计算机上签名。

所有的启动关键驱动程序必须包含嵌入的签名。 数字签名不需要插 (PnP) 驱动程序。 但正在运行的操作系统上安装未签名的 PnP 驱动程序后，管理员凭据也是必需的并且您不能在 64 位操作系统上安装这些驱动程序。

有两种方法可以进行签名的驱动程序︰

-   内核模式和启动关键驱动程序进行数字签名通过一种称为嵌入式签名方法。 通过使用嵌入式的签名，驱动程序包中的每个二进制文件进行签名。 嵌入式的签名可以改善引导加载性能。 对于不是即插即用的驱动程序，以便它们不是丢失的操作系统升级期间应嵌入签名。

-   数字签名的 PnP 驱动程序包含已进行数字签名的编录 (.cat) 文件。 编录文件包含用于安装驱动程序的.inf 文件中的所有文件的哈希值。 签名的编录文件是已正确安装大多数即插即用驱动程序所必需的所有。

这些源可以对驱动程序进行签名︰

-   Windows 硬件质量实验室 (WHQL)，它将确保您的驱动程序限定为 Windows 硬件认证计划。 WHQL 创建签名的驱动程序目录。 对于引导所必需的驱动程序，则应添加嵌入式的签名，而不是依赖于目录。 引导关键驱动程序映像文件中的嵌入式的签名通过消除需要找到相应的编录文件，当操作系统加载程序将验证驱动程序签名时优化操作系统的启动性能。

-   证书颁发机构 (CA)，通过使用软件发布证书 (SPC)。 对于引导所必需的和基于 x64 的内核驱动程序，Microsoft 提供了可用于交叉签名驱动程序的其他证书。 不是启动关键驱动程序不必是由 Microsoft 跨签名或嵌入。 如果您需要亲自签名驱动程序的灵活性，可以使用 Windows 内核模式代码签名过程。 在基于 x64 的系统内核模块的数字签名的信息，请参阅[64 位驱动程序准则](http://go.microsoft.com/fwlink/?LinkId=529487)。

进行测试，您还可以使用测试证书。

如果从供应商收到未签名的驱动程序进行测试，您可以使用测试签名来验证该驱动程序并测试安装。 测试签名是数字签名通过使用私有密钥和信任仅在测试环境的范围中的相应代码签名证书的应用程序的行为。

以下是生成此类测试签名证书的主要方式︰

-   开发人员可以生成自己的自签名的证书。

-   CA 可以颁发的证书。

无论哪种方式，测试签名证书必须清楚地标识为仅适用于测试。 例如中的证书使用者名称，可以包含"test"，可以将包含在证书中附加法律免责声明。 必须为签名只公开 beta 版发布和公共软件和内部业务线软件的最终版本保留生产由商业 Ca 颁发的证书。

有关详细信息，请参阅[设备驱动程序签名和转移的要求](http://go.microsoft.com/fwlink/?LinkId=210665)。

当您要添加到 Windows 的测试签名的驱动程序包时，请考虑以下几点︰

-   您必须在运行的操作系统上安装测试证书。 无法脱机安装它们。

-   受信任的根证书颁发机构证书存储中，必须插入测试证书颁发的 CA 证书。

    **请注意**  
    如果测试证书是自签名 — — 例如，通过使用证书创建工具 (MakeCert) — — 必须将测试证书插入受信任根证书颁发机构证书存储区中。

     

-   在受信任的发行者证书存储中，必须插入用于对驱动程序包进行签名的测试证书。

-   您必须添加测试证书 （与 Windows 映像启动实例） 联机之前您可以使用部署映像服务和管理 (DISM) 命令行工具添加测试签名的驱动程序离线。

-   DISM 验证 WHQL 认证仅用于引导所必需的驱动程序。 但是，DISM 命令行选项可覆盖此行为。 有关详细信息，请参阅[DISM 驱动程序服务命令行选项](dism-driver-servicing-command-line-options-s14.md)。

-   要安装和验证测试签名的驱动程序在 64 位操作系统上，请设置 Windows 启动配置要在目标计算机上使用 BCDedit 工具测试模式。 测试模式验证已签名的驱动程序图像，但证书路径验证不需要配置为受信任的根颁发机构颁发。 即插即用驱动程序安装和分级逻辑正确处理驱动程序，必须在操作系统映像的受信任的证书存储区存储测试证书。 在开发过程中测试模式的信息，请参阅[64 位驱动程序准则](http://go.microsoft.com/fwlink/?LinkId=62690)。

**警告︰**  
如果在基于 x64 的计算机上安装一个未签名或无效的引导所必需设备驱动程序，则计算机将不会启动。 未签名或无效的引导所必需设备驱动程序会导致出现 Stop 错误。 从关键设备数据库 (CDDB) 或其反映的图像中的位置，您应该删除该驱动程序。 如果要执行升级，确保该未签名的驱动程序和它们相关联的应用程序、 服务，或移除设备或使用已签名的驱动程序更新。

如果您不使用 BCDedit，启用测试模式，并且您有安装测试签名的驱动程序，您的计算机将无法启动。 如果您使用 DISM 删除驱动程序，可能不会删除反射的驱动程序包的所有实例。 因此，我们建议您不要部署具有测试签名的驱动程序安装的图像。

 

## <a name="span-idresourcesspanspan-idresourcesspanspan-idresourcesspanadditional-resources"></a><span id="Resources"></span><span id="resources"></span><span id="RESOURCES"></span>其他资源


这些网站提供了有关设备驱动程序要求的详细信息︰

-   有关即插即用驱动程序部署的详细信息，请参阅[签名即插即用设备安装的要求](http://go.microsoft.com/fwlink/?LinkId=89602)。

-   有关数字签名以及开发驱动程序的详细信息，请参阅[Windows 硬件开发人员中心](http://go.microsoft.com/fwlink/?LinkId=139175)网站上的相关网页。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[将设备驱动程序路径添加到答案文件](https://msdn.microsoft.com/library/windows/hardware/dn915062)

[在审核模式下添加驱动程序](add-a-driver-online-in-audit-mode.md)

[DISM 驱动程序服务命令行选项](dism-driver-servicing-command-line-options-s14.md)

[添加和移除脱机 Windows 映像的驱动程序](add-and-remove-drivers-to-an-offline-windows-image.md)

[在 Windows 安装期间添加到 Windows 的设备驱动程序](add-device-drivers-to-windows-during-windows-setup.md)

[在捕获 Windows 映像时维护驱动程序配置](maintain-driver-configurations-when-capturing-a-windows-image.md)

[BCDboot 命令行选项](bcdboot-command-line-options-techref-di.md)

[部署疑难解答和日志文件](deployment-troubleshooting-and-log-files.md)

 

 






