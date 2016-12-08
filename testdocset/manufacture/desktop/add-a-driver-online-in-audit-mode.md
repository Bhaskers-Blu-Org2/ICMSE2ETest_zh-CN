---
author: Justinha
Description: "在审核模式下添加驱动程序"
ms.assetid: 3b7e2d24-4bd4-4ca3-8e6f-2bd771ebab3b
MSHAttr: PreferredLib:/library/windows/hardware
title: "在审核模式下添加驱动程序"
ms.openlocfilehash: 90b76852f2a72c84958d469745df29911773c9ac
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add-a-driver-online-in-audit-mode"></a>在审核模式下添加驱动程序


可以使用答案文件自动安装设备驱动程序在审核模式下启动计算机时。

## <a name="span-idbkmk2spanspan-idbkmk2spanadding-a-device-driver"></a><span id="bkmk_2"></span><span id="BKMK_2"></span>添加设备驱动程序


[AuditSystem](auditsystem.md)配置传递过程无人参与的安装设置 Windows 在系统上下文中，在审核模式下的计算机在用户登录之前运行时。 在审核模式下启动计算机的情况下，才会**auditSystem**配置阶段运行。 在**auditSystem**配置阶段添加设备驱动程序， [Microsoft 的 Windows PnpCustomizationsNonWinPE](https://msdn.microsoft.com/library/windows/hardware/dn923009)组件添加到答案文件中的**auditSystem**配置阶段中，并指定每个设备驱动程序的路径。 运行安装程序后，请在审核模式下启动 Windows。 **/ 审核**选项以配置计算机，以便启动下一次启动在审核模式下，可以运行**Sysprep**命令。 或者，在答案文件中，您可以配置 Microsoft Windows 部署\\重新封装\\`Mode`设置为**审核**。 有关详细信息，请参阅[无人参与的 Windows 安装程序参考](https://msdn.microsoft.com/library/windows/hardware/dn923277)。

### <a name="span-idtoaddadevicedriverduringtheauditsystemconfigurationpassspanspan-idtoaddadevicedriverduringtheauditsystemconfigurationpassspanspan-idtoaddadevicedriverduringtheauditsystemconfigurationpassspanto-add-a-device-driver-during-the-auditsystem-configuration-pass"></a><span id="To_add_a_device_driver_during_the_auditSystem_configuration_pass"></span><span id="to_add_a_device_driver_during_the_auditsystem_configuration_pass"></span><span id="TO_ADD_A_DEVICE_DRIVER_DURING_THE_AUDITSYSTEM_CONFIGURATION_PASS"></span>在 auditSystem 配置阶段添加设备驱动程序

1.  找到您想要安装在审核模式下的设备驱动程序的.inf 文件。

2.  技术人员计算机上打开 Windows 系统映像管理器 （Windows sim 卡）。 单击**开始**，键入**Windows 系统映像管理器**，然后选择**Windows 系统映像管理器**。

3.  打开答案文件，然后展开**组件**节点以显示可用的设置。

4.  Microsoft 的 Windows PnpCustomizationsNonWinPE 组件添加到答案文件中的**auditSystem**配置阶段。

5.  **Microsoft 的 Windows PnpCustomizationsNonWinPE**在展开节点应答文件。 **DevicePaths**，用鼠标右键单击，然后单击**插入新 PathAndCredentials**。

    新的**PathAndCredentials**列表项出现。

6.  您访问的每个位置，添加一个单独的**PathAndCredentials**列表项。

7.  Microsoft 的 Windows PnpCustomizationsNonWinPE 组件中指定的路径的设备驱动程序和用于访问该文件，如果文件位于网络共享的凭据。

    **请注意**  
    您可以通过添加多个**PathAndCredentials**列表项包含多个设备驱动程序路径。 如果添加多个列表项，则必须增加值为`Key`的每个路径。 例如，如果您将添加两个单独的驱动程序路径，第一条路径使用`Key`值为**1**，并且第二个路径会使用`Key`的值为**2**。

     

8.  保存答案文件并关闭 Windows sim 卡。 答案文件必须类似于以下示例︰

    ``` syntax
    <?xml version="1.0" encoding="utf-8" ?> 
    <unattend xmlns="urn:schemas-microsoft-com:unattend">
       <settings pass="auditSystem">
          <component name="Microsoft-Windows-PnpCustomizationsNonWinPE" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
             <DriverPaths>
                <PathAndCredentials wcm:keyValue="1" wcm:action="add">
                   <Credentials>
                      <Domain>Fabrikam</Domain> 
                      <Password>MyPassword</Password> 
                      <Username>MyUserName</Username> 
                   </Credentials>
                   <Path>\\networkshare\share\drivers</Path> 
                </PathAndCredentials>
             </DriverPaths>
          </component>
       </settings>
    </unattend>
    ```

9.  Windows 预安装环境 (Windows PE) 在启动、 运行 Windows 安装程序并指定应答文件的名称。 例如︰

    ``` syntax
    Setup /unattend:C:\unattend.xml
    ```

    指定的答案文件会缓存到系统中，以便计算机审核模式下运行时，应用答案文件中的设置。

    安装程序尚未完成。

10. **使用/审核**选项配置计算机，在审核模式下启动下一次启动运行**Sysprep**命令。 例如︰

    ``` syntax
    Sysprep /audit /reboot
    ```

    在审核模式下重新启动 Windows，添加您在应答文件中指定的设备驱动程序。

您可以使用 PNPUtil 工具来添加、 删除和枚举驱动程序上运行的操作系统。 有关如何使用 PNPUtil 来添加或删除插驱动程序的详细信息，请参阅[安装即插即用设备](http://go.microsoft.com/fwlink/?LinkId=139151)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[设备驱动程序和部署概述](device-drivers-and-deployment-overview.md)

[在 Windows 安装期间添加到 Windows 的设备驱动程序](add-device-drivers-to-windows-during-windows-setup.md)

[DISM 驱动程序服务命令行选项](dism-driver-servicing-command-line-options-s14.md)

[添加和移除脱机 Windows 映像的驱动程序](add-and-remove-drivers-to-an-offline-windows-image.md)

[审核模式概述](audit-mode-overview.md)

[引导到审核模式或 OOBE 的窗口](boot-windows-to-audit-mode-or-oobe.md)

 

 






