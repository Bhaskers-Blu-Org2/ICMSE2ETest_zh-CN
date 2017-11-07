---
Description: "这一节演示了如何添加一个虚构的驱动程序和 MCSF 自定义设置作为包的一部分。"
ms.assetid: 9d776681-9006-4dd5-b69e-fb195a888f7d
MSHAttr: PreferredLib:/library
author: CelesteDG
title: "创建移动包"
ms.openlocfilehash: c3856aad95d10845253e58b85ca6a100059c5419
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="create-mobile-packages"></a>创建移动包


在 Windows 10 手机，包构成所针对的 OS 的构建基块，它们可以包含所有文件、 库、 注册表设置、 可执行文件和在移动设备上的数据。 每个操作系统组件，从对系统文件，设备驱动程序必须包含在包中。

作为 OEM，如果您有特定于设备的驱动程序或自定义设置，您想要添加到操作系统中，您需要创建一个包。 这一节演示了如何添加一个虚构的驱动程序和 MCSF 自定义设置作为包的一部分。

移动包，其中包括指定其他组件和程序包合并，有关更多详细信息，请参阅[创建移动包](https://msdn.microsoft.com/library/dn756642)。

### <a name="span-idaddadrivercomponentspanspan-idaddadrivercomponentspanadd-a-driver-component"></a><span id="add_a_driver_component"></span><span id="ADD_A_DRIVER_COMPONENT"></span>添加驱动程序组件

若要了解有关驱动程序的详细信息并开始书写自己，请参阅[设备和驱动程序技术](https://msdn.microsoft.com/library/windows/hardware/ff557557)。

在本演练中，我们正在下载示例回响 KMDF 驱动程序，将其转换为通用的 Windows 驱动程序，然后使用 Visual Studio 创建软件包文件。

**添加驱动程序**

1.  下载回响通用驱动程序示例。

    1.  下载 master.zip 文件，并将其保存到本地硬盘︰ <https://github.com/microsoft/windows-driver-samples/archive/master.zip>。

    2.  提取的 master.zip 文件中的所有内容。 指定一个文件夹，如*c:\\DriverSamples*，或浏览到一个现有存储提取的文件。

    3.  文件将被解压缩后，将转到常规\\echo\\kmdf 保存回响驱动程序示例查找驱动程序解决方案提取的文件的文件夹内的子文件夹。 例如，如果您创建了*c:\\DriverSamples*文件夹在上一步中的，您可以找到驱动程序解决方案下的*c:\\DriverSamples\\常规\\echo\\kmdf*。

2.  将现有的回响驱动程序项目转换为通用的 Windows 驱动程序项目。

    1.  在 Visual Studio 2015，打开现有的 kmdfecho 驱动程序项目、 kmdfecho.sln。

    2.  在 Visual Studio 中的解决方案资源管理器的位置。 在解决方案资源管理器窗格中，右击**解决方案 kmdfecho （项目 3）** ，然后选择**配置管理器**。

    3.  在**配置管理器**窗口中，将设置为**Windows 10**的目标操作系统。

    4.  右键单击该驱动程序项目，然后选择**属性**。 在**配置管理器**下&gt;**驱动程序**，验证**目标平台**是否设置为**通用**。

        在**目标平台**中的其他选择包括**移动**。 如果您想要生成驱动程序只在 Windows 10 Mobile 上运行，您可能会选择此选项。

3.  从 Visual Studio 2015，使用 PkgGen 生成的包文件。

    1.  右键单击该驱动程序项目，然后选择**添加**-&gt;**新项**。

    2.  在**Visual C++** &gt; **的 Windows 驱动程序**，**包清单**中选择，然后单击**添加**。

        Visual Studio 将添加到驱动程序项目名为 Package.pkg.xml 的文件。 您可以右键单击文件并选择要验证的项类型被设置为**PkgGen**的**属性**。 在相同的属性页，可以设置**从生成中排除**为**是**如果您以后决定您想要生成此驱动程序项目，然后生成软件包文件。

    3.  单击**确定**。

    4.  右键单击该驱动程序项目并选择**属性**。 在**配置属性**打开**PackageGen**节点并将**版本**更改为您喜欢的任何值。 例如，您可以将版本设置为*1.0.0.0*。

    5.  设置包**所有者**、**组件**和**子组件**的值。

4.  右键单击该驱动程序项目并选择**属性**。 将测试证书设置为运行 installoemcerts.cmd 时安装 OEM 测试证书之一。

    例如，您可以使用 CN = Windows Phone OEM 根 2013 年 （仅测试）。

5.  保存您的工作，然后重新启动 Visual Studio 以管理员的身份。

6.  构建您的驱动程序。 Visual Studio 对所需的库链接并生成.cat 文件、 一个.inf 文件、 驱动程序二进制文件和一个.spkg 文件。

    一旦建立了驱动程序，您应该看到一个名为*项目名称*.spkg，其中包含.cab 和.spkg 的新文件夹。

    我们将使用您在本演练中创建的驱动程序.spkg 并将它与下一次的演练，以构建移动操作系统映像从.spkg 相结合。

若要了解有关如何运行 Visual Studio 之外的 PkgGen.exe，请参见下一节中添加自定义设置 请参阅[创建移动包](https://msdn.microsoft.com/library/dn756642)中的*运行 pkggen.exe 工具*部分。

### <a name="span-idaddanmcsfcustomizationsettingspanspan-idaddanmcsfcustomizationsettingspanadd-an-mcsf-customization-setting"></a><span id="add_an_mcsf_customization_setting"></span><span id="ADD_AN_MCSF_CUSTOMIZATION_SETTING"></span>添加了 MCSF 的自定义设置

在 Windows 10 手机，有这两种支持的自定义框架︰ 管理集中设置框架 (MCSF) 和 Windows 资源调配。 关于这些框架的详细信息，请参阅[移动设备的自定义项](https://msdn.microsoft.com/library/windows/hardware/mt481438)。 添加自定义的 OEM 自定义设置时，仅 MCSF 是可扩展和可用于 Oem 可以声明它们自己不同的移动操作系统设置简单和一致的方式类似于 Microsoft 自定义设置。

若要了解如何使用 MCSF 和封装 XML 架构声明并访问自定义 OEM 设置，请参阅[管理集中设置框架 (MCSF)](https://msdn.microsoft.com/library/windows/hardware/dn772150)。

在本演练中，我们正在扩展[配置快速操作](https://msdn.microsoft.com/library/windows/hardware/dn757416)自定义项使用 MCSF 架构创建公开各种插槽，以便它们可以轻松地配置以后而无需记住的注册表键和值的策略设置。 为此，我们添加中的策略设置声明。 pkg.xml 文件，然后生成该文件来创建一个包。

**若要添加自定义设置**

1.  相对应的 MCSF 策略设置写入以下注册表项︰

    ``` syntax
    $(HKLM.SOFTWARE)\Microsoft\Shell\OEM\QuickActions\Slot\X
    Type:  REG_SZ
    Possible values:  
       Microsoft.QuickAction.AllSettings
       Microsoft.QuickAction.Connect
       Microsoft.QuickAction.Note
       Microsoft.QuickAction.Flashlight
       Microsoft.QuickAction.RotationLock
       Microsoft.QuickAction.BatterySaver
       Microsoft.QuickAction.Bluetooth
       Microsoft.QuickAction.WiFi
       Microsoft.QuickAction.AirplaneMode
       Microsoft.QuickAction.Vpn
       Microsoft.QuickAction.Cellular
       Microsoft.QuickAction.MobileHotspot
       Microsoft.QuickAction.Camera
       Microsoft.QuickAction.Brightness
       Microsoft.QuickAction.QuietHours
       Microsoft.QuickAction.Location
    ```

    *X*中的注册表项应替换为正在配置的插槽编号 （从 1 开始）。 插槽是有序的从右到左。 而大屏幕的移动设备有 4 个插槽时最多的 5 大屏幕的移动设备上的插槽。

    下面的代码示例演示如何可以声明的快速动作的 MCSF 策略设置︰

    ``` syntax
        <SettingsGroup Path="Notifications/QuickActions">  
          <!-- Default Quick actions configuration -->  
          <Setting Name="QuickActionSlot1" Description="App to place in quick action slot 1.">  
            <RegistrySource Path="$(hklm.software)\Microsoft\Shell\OEM\QuickActions\Slot\1" Type="REG_SZ" Default="Microsoft.QuickAction.AllSettings" />  
            <Validate>
               <!-- Shows the available options for the quick action slot -->
               <Option Value="Microsoft.QuickAction.AllSettings" FriendlyName="All settings" />
               <Option Value="Microsoft.QuickAction.Connect" FriendlyName="Connect" />
               <Option Value="Microsoft.QuickAction.Note" FriendlyName="Note" />
               <Option Value="Microsoft.QuickAction.Flashlight" FriendlyName="Flashlight" />
               <Option Value="Microsoft.QuickAction.RotationLock" FriendlyName="Rotation lock" />
               <Option Value="Microsoft.QuickAction.BatterySaver" FriendlyName="Battery saver" />
               <Option Value="Microsoft.QuickAction.Bluetooth" FriendlyName="Bluetooth" />
               <Option Value="Microsoft.QuickAction.WiFi" FriendlyName="Wi-Fi" />
               <Option Value="Microsoft.QuickAction.AirplaneMode" FriendlyName="Airplane mode" />
               <Option Value="Microsoft.QuickAction.Vpn" FriendlyName="VPN" />
               <Option Value="Microsoft.QuickAction.Cellular" FriendlyName="Cellular" />
               <Option Value="Microsoft.QuickAction.MobileHotspot" FriendlyName="Mobile hotspot" />
               <Option Value="Microsoft.QuickAction.Camera" FriendlyName="Camera" />
               <Option Value="Microsoft.QuickAction.Brightness" FriendlyName="Brightness" />
               <Option Value="Microsoft.QuickAction.QuietHours" FriendlyName="Quiet hours" />
               <Option Value="Microsoft.QuickAction.Location" FriendlyName="Location" />
            </Validate>
          </Setting>  
          <Setting Name="QuickActionSlot2" Description="App to place in quick action slot 2.">  
            <RegistrySource Path="$(hklm.software)\Microsoft\Shell\OEM\QuickActions\Slot\2" Type="REG_SZ" Default="Microsoft.QuickAction.RotationLock" />  
            <Validate>
               <!-- Shows the available options for the quick action slot -->
               <Option Value="Microsoft.QuickAction.AllSettings" FriendlyName="All settings" />
               <Option Value="Microsoft.QuickAction.Connect" FriendlyName="Connect" />
               <Option Value="Microsoft.QuickAction.Note" FriendlyName="Note" />
               <Option Value="Microsoft.QuickAction.Flashlight" FriendlyName="Flashlight" />
               <Option Value="Microsoft.QuickAction.RotationLock" FriendlyName="Rotation lock" />
               <Option Value="Microsoft.QuickAction.BatterySaver" FriendlyName="Battery saver" />
               <Option Value="Microsoft.QuickAction.Bluetooth" FriendlyName="Bluetooth" />
               <Option Value="Microsoft.QuickAction.WiFi" FriendlyName="Wi-Fi" />
               <Option Value="Microsoft.QuickAction.AirplaneMode" FriendlyName="Airplane mode" />
               <Option Value="Microsoft.QuickAction.Vpn" FriendlyName="VPN" />
               <Option Value="Microsoft.QuickAction.Cellular" FriendlyName="Cellular" />
               <Option Value="Microsoft.QuickAction.MobileHotspot" FriendlyName="Mobile hotspot" />
               <Option Value="Microsoft.QuickAction.Camera" FriendlyName="Camera" />
               <Option Value="Microsoft.QuickAction.Brightness" FriendlyName="Brightness" />
               <Option Value="Microsoft.QuickAction.QuietHours" FriendlyName="Quiet hours" />
               <Option Value="Microsoft.QuickAction.Location" FriendlyName="Location" />
            </Validate>     
          </Setting> 
          <Setting Name="QuickActionSlot3" Description="App to place in quick action slot 3.">  
            <RegistrySource Path="$(hklm.software)\Microsoft\Shell\OEM\QuickActions\Slot\3" Type="REG_SZ" Default="Microsoft.QuickAction.Bluetooth" />  
            <Validate>
               <!-- Shows the available options for the quick action slot -->
               <Option Value="Microsoft.QuickAction.AllSettings" FriendlyName="All settings" />
               <Option Value="Microsoft.QuickAction.Connect" FriendlyName="Connect" />
               <Option Value="Microsoft.QuickAction.Note" FriendlyName="Note" />
               <Option Value="Microsoft.QuickAction.Flashlight" FriendlyName="Flashlight" />
               <Option Value="Microsoft.QuickAction.RotationLock" FriendlyName="Rotation lock" />
               <Option Value="Microsoft.QuickAction.BatterySaver" FriendlyName="Battery saver" />
               <Option Value="Microsoft.QuickAction.Bluetooth" FriendlyName="Bluetooth" />
               <Option Value="Microsoft.QuickAction.WiFi" FriendlyName="Wi-Fi" />
               <Option Value="Microsoft.QuickAction.AirplaneMode" FriendlyName="Airplane mode" />
               <Option Value="Microsoft.QuickAction.Vpn" FriendlyName="VPN" />
               <Option Value="Microsoft.QuickAction.Cellular" FriendlyName="Cellular" />
               <Option Value="Microsoft.QuickAction.MobileHotspot" FriendlyName="Mobile hotspot" />
               <Option Value="Microsoft.QuickAction.Camera" FriendlyName="Camera" />
               <Option Value="Microsoft.QuickAction.Brightness" FriendlyName="Brightness" />
               <Option Value="Microsoft.QuickAction.QuietHours" FriendlyName="Quiet hours" />
               <Option Value="Microsoft.QuickAction.Location" FriendlyName="Location" />
            </Validate>
          </Setting> 
          <Setting Name="QuickActionSlot4" Description="App to place in quick action slot 4.">  
            <RegistrySource Path="$(hklm.software)\Microsoft\Shell\OEM\QuickActions\Slot\4" Type="REG_SZ" Default="Microsoft.QuickAction.WiFi" />  
            <Validate>
               <!-- Shows the available options for the quick action slot -->
               <Option Value="Microsoft.QuickAction.AllSettings" FriendlyName="All settings" />
               <Option Value="Microsoft.QuickAction.Connect" FriendlyName="Connect" />
               <Option Value="Microsoft.QuickAction.Note" FriendlyName="Note" />
               <Option Value="Microsoft.QuickAction.Flashlight" FriendlyName="Flashlight" />
               <Option Value="Microsoft.QuickAction.RotationLock" FriendlyName="Rotation lock" />
               <Option Value="Microsoft.QuickAction.BatterySaver" FriendlyName="Battery saver" />
               <Option Value="Microsoft.QuickAction.Bluetooth" FriendlyName="Bluetooth" />
               <Option Value="Microsoft.QuickAction.WiFi" FriendlyName="Wi-Fi" />
               <Option Value="Microsoft.QuickAction.AirplaneMode" FriendlyName="Airplane mode" />
               <Option Value="Microsoft.QuickAction.Vpn" FriendlyName="VPN" />
               <Option Value="Microsoft.QuickAction.Cellular" FriendlyName="Cellular" />
               <Option Value="Microsoft.QuickAction.MobileHotspot" FriendlyName="Mobile hotspot" />
               <Option Value="Microsoft.QuickAction.Camera" FriendlyName="Camera" />
               <Option Value="Microsoft.QuickAction.Brightness" FriendlyName="Brightness" />
               <Option Value="Microsoft.QuickAction.QuietHours" FriendlyName="Quiet hours" />
               <Option Value="Microsoft.QuickAction.Location" FriendlyName="Location" />
            </Validate>
          </Setting> 
          <Setting Name="QuickActionSlot5" Description="App to place in quick action slot 5.">  
            <RegistrySource Path="$(hklm.software)\Microsoft\Shell\OEM\QuickActions\Slot\5" Type="REG_SZ" Default="Microsoft.QuickAction.Camera" />  
            <Validate>
               <!-- Shows the available options for the quick action slot -->
               <Option Value="Microsoft.QuickAction.AllSettings" FriendlyName="All settings" />
               <Option Value="Microsoft.QuickAction.Connect" FriendlyName="Connect" />
               <Option Value="Microsoft.QuickAction.Note" FriendlyName="Note" />
               <Option Value="Microsoft.QuickAction.Flashlight" FriendlyName="Flashlight" />
               <Option Value="Microsoft.QuickAction.RotationLock" FriendlyName="Rotation lock" />
               <Option Value="Microsoft.QuickAction.BatterySaver" FriendlyName="Battery saver" />
               <Option Value="Microsoft.QuickAction.Bluetooth" FriendlyName="Bluetooth" />
               <Option Value="Microsoft.QuickAction.WiFi" FriendlyName="Wi-Fi" />
               <Option Value="Microsoft.QuickAction.AirplaneMode" FriendlyName="Airplane mode" />
               <Option Value="Microsoft.QuickAction.Vpn" FriendlyName="VPN" />
               <Option Value="Microsoft.QuickAction.Cellular" FriendlyName="Cellular" />
               <Option Value="Microsoft.QuickAction.MobileHotspot" FriendlyName="Mobile hotspot" />
               <Option Value="Microsoft.QuickAction.Camera" FriendlyName="Camera" />
               <Option Value="Microsoft.QuickAction.Brightness" FriendlyName="Brightness" />
               <Option Value="Microsoft.QuickAction.QuietHours" FriendlyName="Quiet hours" />
               <Option Value="Microsoft.QuickAction.Location" FriendlyName="Location" />
            </Validate>
          </Setting> 
        </SettingsGroup>
    ```

2.  创建。 pkg.xml 文件并添加到上一步中的策略设置。 pkg.xml 文件。 下面的示例演示如何执行此操作。

    ```XML
    <?xml version="1.0" encoding="utf-8">
    <Package xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema"
      Owner=""
      Component=""
      SubComponent=""
      OwnerType="OEM"
      ReleaseType="">
       <Components>
        <SettingsGroup Path="Notifications/QuickActions">  
          <!-- Default Quick actions configuration -->  
          <Setting Name="QuickActionSlot1" Description="App to place in quick action slot 1.">  
            <RegistrySource Path="$(hklm.software)\Microsoft\Shell\OEM\QuickActions\Slot\1" Type="REG_SZ" Default="Microsoft.QuickAction.AllSettings" />  
            <Validate>
               <!-- Shows the available options for the quick action slot -->
               <Option Value="Microsoft.QuickAction.AllSettings" FriendlyName="All settings" />
               <Option Value="Microsoft.QuickAction.Connect" FriendlyName="Connect" />
               <Option Value="Microsoft.QuickAction.Note" FriendlyName="Note" />
               <Option Value="Microsoft.QuickAction.Flashlight" FriendlyName="Flashlight" />
               <Option Value="Microsoft.QuickAction.RotationLock" FriendlyName="Rotation lock" />
               <Option Value="Microsoft.QuickAction.BatterySaver" FriendlyName="Battery saver" />
               <Option Value="Microsoft.QuickAction.Bluetooth" FriendlyName="Bluetooth" />
               <Option Value="Microsoft.QuickAction.WiFi" FriendlyName="Wi-Fi" />
               <Option Value="Microsoft.QuickAction.AirplaneMode" FriendlyName="Airplane mode" />
               <Option Value="Microsoft.QuickAction.Vpn" FriendlyName="VPN" />
               <Option Value="Microsoft.QuickAction.Cellular" FriendlyName="Cellular" />
               <Option Value="Microsoft.QuickAction.MobileHotspot" FriendlyName="Mobile hotspot" />
               <Option Value="Microsoft.QuickAction.Camera" FriendlyName="Camera" />
               <Option Value="Microsoft.QuickAction.Brightness" FriendlyName="Brightness" />
               <Option Value="Microsoft.QuickAction.QuietHours" FriendlyName="Quiet hours" />
               <Option Value="Microsoft.QuickAction.Location" FriendlyName="Location" />
            </Validate>
          </Setting>  
          <Setting Name="QuickActionSlot2" Description="App to place in quick action slot 2.">  
            <RegistrySource Path="$(hklm.software)\Microsoft\Shell\OEM\QuickActions\Slot\2" Type="REG_SZ" Default="Microsoft.QuickAction.RotationLock" />  
            <Validate>
               <!-- Shows the available options for the quick action slot -->
               <Option Value="Microsoft.QuickAction.AllSettings" FriendlyName="All settings" />
               <Option Value="Microsoft.QuickAction.Connect" FriendlyName="Connect" />
               <Option Value="Microsoft.QuickAction.Note" FriendlyName="Note" />
               <Option Value="Microsoft.QuickAction.Flashlight" FriendlyName="Flashlight" />
               <Option Value="Microsoft.QuickAction.RotationLock" FriendlyName="Rotation lock" />
               <Option Value="Microsoft.QuickAction.BatterySaver" FriendlyName="Battery saver" />
               <Option Value="Microsoft.QuickAction.Bluetooth" FriendlyName="Bluetooth" />
               <Option Value="Microsoft.QuickAction.WiFi" FriendlyName="Wi-Fi" />
               <Option Value="Microsoft.QuickAction.AirplaneMode" FriendlyName="Airplane mode" />
               <Option Value="Microsoft.QuickAction.Vpn" FriendlyName="VPN" />
               <Option Value="Microsoft.QuickAction.Cellular" FriendlyName="Cellular" />
               <Option Value="Microsoft.QuickAction.MobileHotspot" FriendlyName="Mobile hotspot" />
               <Option Value="Microsoft.QuickAction.Camera" FriendlyName="Camera" />
               <Option Value="Microsoft.QuickAction.Brightness" FriendlyName="Brightness" />
               <Option Value="Microsoft.QuickAction.QuietHours" FriendlyName="Quiet hours" />
               <Option Value="Microsoft.QuickAction.Location" FriendlyName="Location" />
            </Validate>     
          </Setting> 
          <Setting Name="QuickActionSlot3" Description="App to place in quick action slot 3.">  
            <RegistrySource Path="$(hklm.software)\Microsoft\Shell\OEM\QuickActions\Slot\3" Type="REG_SZ" Default="Microsoft.QuickAction.Bluetooth" />  
            <Validate>
               <!-- Shows the available options for the quick action slot -->
               <Option Value="Microsoft.QuickAction.AllSettings" FriendlyName="All settings" />
               <Option Value="Microsoft.QuickAction.Connect" FriendlyName="Connect" />
               <Option Value="Microsoft.QuickAction.Note" FriendlyName="Note" />
               <Option Value="Microsoft.QuickAction.Flashlight" FriendlyName="Flashlight" />
               <Option Value="Microsoft.QuickAction.RotationLock" FriendlyName="Rotation lock" />
               <Option Value="Microsoft.QuickAction.BatterySaver" FriendlyName="Battery saver" />
               <Option Value="Microsoft.QuickAction.Bluetooth" FriendlyName="Bluetooth" />
               <Option Value="Microsoft.QuickAction.WiFi" FriendlyName="Wi-Fi" />
               <Option Value="Microsoft.QuickAction.AirplaneMode" FriendlyName="Airplane mode" />
               <Option Value="Microsoft.QuickAction.Vpn" FriendlyName="VPN" />
               <Option Value="Microsoft.QuickAction.Cellular" FriendlyName="Cellular" />
               <Option Value="Microsoft.QuickAction.MobileHotspot" FriendlyName="Mobile hotspot" />
               <Option Value="Microsoft.QuickAction.Camera" FriendlyName="Camera" />
               <Option Value="Microsoft.QuickAction.Brightness" FriendlyName="Brightness" />
               <Option Value="Microsoft.QuickAction.QuietHours" FriendlyName="Quiet hours" />
               <Option Value="Microsoft.QuickAction.Location" FriendlyName="Location" />
            </Validate>
          </Setting> 
          <Setting Name="QuickActionSlot4" Description="App to place in quick action slot 4.">  
            <RegistrySource Path="$(hklm.software)\Microsoft\Shell\OEM\QuickActions\Slot\4" Type="REG_SZ" Default="Microsoft.QuickAction.WiFi" />  
            <Validate>
               <!-- Shows the available options for the quick action slot -->
               <Option Value="Microsoft.QuickAction.AllSettings" FriendlyName="All settings" />
               <Option Value="Microsoft.QuickAction.Connect" FriendlyName="Connect" />
               <Option Value="Microsoft.QuickAction.Note" FriendlyName="Note" />
               <Option Value="Microsoft.QuickAction.Flashlight" FriendlyName="Flashlight" />
               <Option Value="Microsoft.QuickAction.RotationLock" FriendlyName="Rotation lock" />
               <Option Value="Microsoft.QuickAction.BatterySaver" FriendlyName="Battery saver" />
               <Option Value="Microsoft.QuickAction.Bluetooth" FriendlyName="Bluetooth" />
               <Option Value="Microsoft.QuickAction.WiFi" FriendlyName="Wi-Fi" />
               <Option Value="Microsoft.QuickAction.AirplaneMode" FriendlyName="Airplane mode" />
               <Option Value="Microsoft.QuickAction.Vpn" FriendlyName="VPN" />
               <Option Value="Microsoft.QuickAction.Cellular" FriendlyName="Cellular" />
               <Option Value="Microsoft.QuickAction.MobileHotspot" FriendlyName="Mobile hotspot" />
               <Option Value="Microsoft.QuickAction.Camera" FriendlyName="Camera" />
               <Option Value="Microsoft.QuickAction.Brightness" FriendlyName="Brightness" />
               <Option Value="Microsoft.QuickAction.QuietHours" FriendlyName="Quiet hours" />
               <Option Value="Microsoft.QuickAction.Location" FriendlyName="Location" />
            </Validate>
          </Setting> 
          <Setting Name="QuickActionSlot5" Description="App to place in quick action slot 5.">  
            <RegistrySource Path="$(hklm.software)\Microsoft\Shell\OEM\QuickActions\Slot\5" Type="REG_SZ" Default="Microsoft.QuickAction.Camera" />  
            <Validate>
               <!-- Shows the available options for the quick action slot -->
               <Option Value="Microsoft.QuickAction.AllSettings" FriendlyName="All settings" />
               <Option Value="Microsoft.QuickAction.Connect" FriendlyName="Connect" />
               <Option Value="Microsoft.QuickAction.Note" FriendlyName="Note" />
               <Option Value="Microsoft.QuickAction.Flashlight" FriendlyName="Flashlight" />
               <Option Value="Microsoft.QuickAction.RotationLock" FriendlyName="Rotation lock" />
               <Option Value="Microsoft.QuickAction.BatterySaver" FriendlyName="Battery saver" />
               <Option Value="Microsoft.QuickAction.Bluetooth" FriendlyName="Bluetooth" />
               <Option Value="Microsoft.QuickAction.WiFi" FriendlyName="Wi-Fi" />
               <Option Value="Microsoft.QuickAction.AirplaneMode" FriendlyName="Airplane mode" />
               <Option Value="Microsoft.QuickAction.Vpn" FriendlyName="VPN" />
               <Option Value="Microsoft.QuickAction.Cellular" FriendlyName="Cellular" />
               <Option Value="Microsoft.QuickAction.MobileHotspot" FriendlyName="Mobile hotspot" />
               <Option Value="Microsoft.QuickAction.Camera" FriendlyName="Camera" />
               <Option Value="Microsoft.QuickAction.Brightness" FriendlyName="Brightness" />
               <Option Value="Microsoft.QuickAction.QuietHours" FriendlyName="Quiet hours" />
               <Option Value="Microsoft.QuickAction.Location" FriendlyName="Location" />
            </Validate>
          </Setting> 
        </SettingsGroup>
       </Components>
    </Package>
    ```

3.  添加**所有者**、**组件**、**子组件**和**ReleaseType**元素的值。 例如︰

    -   **所有者**="Contoso"
    -   **组件**="Customization.Notifications"
    -   **子组件**="QuickActions"
    -   **ReleaseType**="Test"

    若要了解有关元素和属性的详细信息，请参阅[主元素和包的项目文件的属性](https://msdn.microsoft.com/library/dn756796)。

4.  命名并保存。 pkg.xml 文件作为"QuickActions.pkg.xml"。

5.  作为输入，生成一个程序包或.spkg 文件，使用"QuickActions.pkg.xml"。 有关详细信息，请参阅[创建移动包](https://msdn.microsoft.com/library/dn756642)在*运行 pkggen.exe 工具*。

    **若要生成使用 QuickActions.pkg.xml 软件包**

    1.  使用管理员权限打开命令行。

    2.  输入以下命令以生成从 QuickActions.pkg.xml 的软件包。

        **PkgGen QuickActions.pkg.xml /config:"%WPDKCONTENTROOT%\\工具\\bin\\i386\\pkggen.cfg.xml"**

        此命令将生成一个名为 Customization.Notifications.QuickActions.spkg 的包。 在下一节中，我们将使用此组件包，并将其添加到功能清单文件。

 

 



