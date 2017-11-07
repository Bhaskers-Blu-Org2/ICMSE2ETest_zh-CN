---
author: kpacquer
Description: "通过使用包，可以添加到您的设备制造的配置文件。"
ms.assetid: 9925eedf-a49e-4545-b071-72d10925f080
MSHAttr: PreferredLib:/library/windows/hardware
title: "创建自定义制造配置文件包"
ms.openlocfilehash: 06ae9d331da7e0c9a40ea95536f539cd4216a4f3
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="create-a-custom-manufacturing-profile-package"></a>创建自定义制造配置文件包


通过使用包，可以添加到您的设备制造的配置文件。 创建程序包的详细信息，请参阅[创建程序包](https://msdn.microsoft.com/library/dn756642)。 在某些情况下，您可能需要创建自定义配置文件。 例如，可能要微调 Microsoft 服务正在运行的性能或功能的原因或也许您想拥有多个制造配置文件。 当创建新的自定义配置文件，首先应通过复制提供的默认配置文件和自定义以满足您的需要。

例如，如果您想要创建的新自定义配置文件用于工厂测试是默认的配置文件的一个副本，但也将启动您的工厂测试服务，它可能会如下所示︰

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<Package xmlns="urn:Microsoft.WindowsPhone/PackageSchema.v8.00"
        Owner="Contoso"
        Component="MfgMode"
        SubComponent="ManufacturingModeServices"
        ReleaseType="Production"
        OwnerType="OEM">

    <Macros>
      <Macro Id="MfgMode" Value="$(hklm.control)\ManufacturingMode" />
      <Macro Id="CustomProfileServices" Value="$(MfgMode)\CustomProfile\Services" />
    </Macros>

    <Components>
        <OSComponent>
         <!-- Overrides copied from default profile -->
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\*">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000003" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\AccountProvSvc">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000002" />
            </RegKey>
          </RegKeys>              
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\adss">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000004" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\AudioSrv">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000002" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\BFE">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000002" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\BrokerInfrastructure">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000002" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\cellusermodeinterconnect">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000004" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\DcomLaunch">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000002" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\DHCP">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000002" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\Fusion">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000004" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\KeepWifiOnSvc">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000003" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\LaunchAppSvc">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000004" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\MPSSvc">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000002" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\NETACT">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000004" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\nsi">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000002" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\Power">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000002" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\ProfSvc">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000002" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\RpcEptMapper">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000002" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\RpcSs">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000002" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\SamSs">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000002" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\SecMgr">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000004" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\SirepSvc">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000004" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\SystemEventsBroker">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000002" />
            </RegKey>
          </RegKeys>
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\TestSirepSvc">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000002" />
            </RegKey>
          </RegKeys>
         <!-- Custom overrides for OEM services -->
          <RegKeys>
            <RegKey KeyName="$(CustomProfileServices)\OEMFactoryTestService">
              <RegValue Name="Start" Type="REG_DWORD" Value="00000002" />
            </RegKey>
          </RegKeys>
        </OSComponent>
    </Components>
</Package>
```

然后可以使用 pkggen.exe （随 Windows 驱动程序工具包） 来创建包︰

``` syntax
pkggen.exe example.pkg.xml /config:pkggen.cfg.xml
```

 

 





