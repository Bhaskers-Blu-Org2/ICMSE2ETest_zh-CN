---
author: Justinha
Description: "在 Windows 安装期间添加到 Windows 的设备驱动程序"
ms.assetid: adb22778-06a2-493a-81de-3a1306a0b208
MSHAttr: PreferredLib:/library/windows/hardware
title: "在 Windows 安装期间添加到 Windows 的设备驱动程序"
ms.openlocfilehash: 22d78edfc2a2c180044a89d3fc5420460657dc2b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add-device-drivers-to-windows-during-windows-setup"></a>在 Windows 安装期间添加到 Windows 的设备驱动程序


某些硬件设计上安装 Windows®，您可能需要将设备驱动程序添加到 Windows 安装程序。 通过使用应答文件中指定的驱动程序文件的路径，可以为 Windows 安装程序添加驱动程序。 为此在新安装中，您将 Microsoft 的 Windows PnpCustomizationWinPE 组件添加在[windowsPE](windowspe.md)配置阶段、 添加驱动程序路径中，然后指定答案文件。

此外可以修改现有的映像，添加和删除驱动程序。 您可以为服务脱机映像中几种方法。 例如，您可以将 Microsoft 的 Windows PnpCustomizationsNonWinPE 组件添加在[offlineServicing](offlineservicing.md)配置阶段、 添加或删除驱动程序的路径，然后指定应答文件的名称。 有关如何通过使用应答文件，并且还到添加的驱动程序并删除现有的映像的驱动程序的其他方法来修改脱机 Windows 映像的驱动程序的详细信息，请参阅[添加和删除的脱机 Windows 映像的驱动程序](add-and-remove-drivers-to-an-offline-windows-image.md)。

## <a name="span-idbkmk1spanspan-idbkmk1span-add-drivers-to-new-installations-windowspe"></a><span id="bkmk_1"></span><span id="BKMK_1"></span>将驱动程序添加到新的安装 (windowsPE)


为新的安装，您可以在[windowsPE](windowspe.md)配置阶段添加驱动程序。

此方法初始化 Windows 预安装环境 (Windows PE)，并处理从答案文件中，Windows PE 设置，如下所示︰

1.  存储在 RAM 驱动程序的 Windows PE 驱动程序的 Windows 阶段. Windows 加载 Windows PE 为访问本地磁盘和网络所需要的启动关键驱动程序。 当您右键单击**DevicePaths** ，然后选择**插入到 Windows PE 的新 PathAndCredentials**时，Windows PE 处理其他应答文件指定的 Windows PE 的自定义。

2.  在 Windows 安装过程中应用 Windows 映像。 引导关键驱动程序显示 Windows 映像之前安装程序安装该映像。 其他驱动程序添加到 Windows PE 驱动程序存储区将出现在 Windows 映像的驱动程序存储区中。 当 Windows 安装程序处理的[offlineServicing](offlineservicing.md)传递时，Windows 安装程序还将驱动程序路径指定的任何驱动程序添加到 Windows 映像的驱动程序存储区。

**在 windowsPE 传递期间添加设备驱动程序**

1.  使用 Windows 系统映像管理器 (Windows SIM) 来创建一个应答文件，其中包含您想要安装的设备驱动程序的路径。

2.  **Microsoft 的 Windows PnpCustomizationsWinPE**组件添加到答案文件中[windowsPE](windowspe.md)配置阶段。

3.  **Microsoft 的 Windows PnpCustomizationsWinPE**在展开节点应答文件。 **DevicePaths**，用鼠标右键单击，然后选择**插入新 PathAndCredentials**。

    新的**PathAndCredentials**列表项出现。

4.  您访问的每个位置，添加一个单独的**PathAndCredentials**列表项。

    您可以通过添加多个**PathAndCredentials**列表项包含多个设备驱动程序路径。 如果添加多个列表项，则必须增加`Key`的每个路径的值。 例如，如果您将添加两个单独的驱动程序路径，第一条路径使用`Key`的值`1`，并使用第二个路径`Key`的值`2`。

5.  将答案文件中，保存，然后关闭 Windows sim 卡。 答案文件必须类似于以下示例︰

    ``` syntax
    <?xml version="1.0" encoding="utf-8" ?> 
    <unattend xmlns="urn:schemas-microsoft-com:unattend">
       <settings pass="windowsPE">
          <component name="Microsoft-Windows-PnpCustomizationsWinPE" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
             <DriverPaths>
                <PathAndCredentials wcm:keyValue="1" wcm:action="add">
                   <Credentials>
                      <Domain>Fabrikam</Domain> 
                      <Password>MyPassword</Password> 
                      <Username>MyUserName</Username> 
                   </Credentials>
                   <Path>\\server\share\drivers</Path> 
                </PathAndCredentials>
             </DriverPaths>
          </component>
       </settings>
    </unattend>
    ```

6.  引导至 Windows PE。

7.  在命令提示符下，运行 Windows 安装程序。 指定应答文件的名称。 例如︰

    ``` syntax
    Setup /unattend:C:\unattend.xml
    ```

    Windows 安装程序会添加设备驱动程序在\\\\服务器\\共享\\在安装过程中系统的驱动程序路径。

有关驱动程序的详细信息，请参阅[设备驱动程序和部署概述](device-drivers-and-deployment-overview.md)和[添加驱动程序在线在审核模式下](add-a-driver-online-in-audit-mode.md)。 有关 Windows 组件的详细信息，请参阅[无人参与的 Windows 安装程序参考](http://go.microsoft.com/fwlink/?LinkId=206281)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Windows 安装程序技术参考](windows-setup-technical-reference.md)

[从 DVD 启动](boot-from-a-dvd.md)

[部署自定义映像](deploy-a-custom-image.md)

[引导到审核模式或 OOBE 的窗口](boot-windows-to-audit-mode-or-oobe.md)

[使用 Windows 安装程序配置集](use-a-configuration-set-with-windows-setup.md)

[向 Windows 安装程序中添加自定义脚本](add-a-custom-script-to-windows-setup.md)

 

 






