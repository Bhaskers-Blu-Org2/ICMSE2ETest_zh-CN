---
author: kpacquer
Description: "可能希望服务通常会被禁用，但在设备处于制造模式时自动运行的情况。"
ms.assetid: 5504bade-5342-4006-9631-7321acd983ac
MSHAttr: PreferredLib:/library/windows/hardware
title: "定义仅在制造模式下运行的服务"
ms.openlocfilehash: 314009721cdcbe0f78c1612c276ed7b1849e87d3
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="define-a-service-that-only-runs-in-manufacturing-mode"></a>定义仅在制造模式下运行的服务


可能希望服务通常会被禁用，但在设备处于制造模式时自动运行的情况。 例如，工厂测试套件将可能在此配置中运行。 将服务的启动类型设置为禁用，然后添加制造配置文件重写，使您的服务自动启动时使用相应的制造模式配置文件。

这里是制造配置文件示例︰

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<Package xmlns="urn:Microsoft.WindowsPhone/PackageSchema.v8.00"
        Owner="Contoso"
        Component="MfgMode"
        SubComponent="FactoryTest"
        ReleaseType="Production"
        OwnerType="OEM">

    <Macros>
      <Macro Id="MfgMode" Value="$(hklm.control)\ManufacturingMode" />
      <Macro Id="CustomProfileServices" Value="$(MfgMode)\CustomProfile\Services" />
    </Macros>

    <Components>
      <!-- Definition for the service -->
      <Service
        Name="FactoryService"
        Start="Disabled"
        Type="Win32OwnProcess"
        ErrorControl="Ignore"
        DisplayName="OEMFactoryTestService"
        Description="A Sample OEM Factory Test Service">

        <Executable Source="$(BINARY_ROOT)\bin\factory\oem_factory_test_service.exe" />

        <!-- Failure actions should reset once per day, for security reasons -->
        <FailureActions ResetPeriod="86400">
          <Action Type="RestartService" Delay="1000"/>
          <Action Type="RestartService" Delay="1000"/>
          <Action Type="RestartService" Delay="1000"/>
          <!-- if it fails to start three times, services should just stop -->
          <Action Type="None" Delay="0"/>
        </FailureActions>

        <RequiredCapabilities>
          <!-- Needed to access and create RPC endpoints -->
          <RequiredCapability CapId="ID_CAP_INTEROPSERVICES" />
        </RequiredCapabilities>

      </Service>

      <OSComponent>
        <!-- Set the factory test service to auto-start when the device is in Manufacturing Mode -->
        <RegKeys>
          <RegKey KeyName="$(CustomProfileServices)\OEMFactoryTestService">
            <RegValue Name="Start" Type="REG_DWORD" Value="00000002" />
          </RegKey>
        </RegKeys>
      </OSComponent>

    </Components>
</Package>
```

 

 





