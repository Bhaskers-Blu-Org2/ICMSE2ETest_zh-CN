---
author: kpacquer
Description: "您还可以只用于在设备处于制造模式的制造配置文件中指定 USBFN 的自定义设置。"
ms.assetid: 0b95ffc6-f3c4-4b22-a48f-513466c36eac
MSHAttr: PreferredLib:/library/windows/hardware
title: "创建自定义制造配置文件具有 USBFN 设置软件包"
ms.openlocfilehash: 3c06d6649d831f03db182e5f58e27420f47d38ff
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="create-a-custom-manufacturing-profile-package-with-usbfn-settings"></a>创建自定义制造配置文件具有 USBFN 设置软件包


您还可以只用于在设备处于制造模式的制造配置文件中指定 USBFN 的自定义设置。

该设备不是在制造模式下，USBFN 设置就仍然会读取从正常位置。 当设备处于制造模式，并提供了制造模式的设置时，设置是从不同的位置。 如果在制造活动配置文件中不提供了任何设置，则将从正常位置读取设置。 这允许您使用不同的设置，当设备处于制造模式，而不是它不是。

这里是一种制造配置文件指定 USBFN 设置的包︰

``` syntax
<?xml version='1.0' encoding='utf-8'?>
<Package
    xmlns="urn:Microsoft.WindowsPhone/PackageSchema.v8.00"
    Owner="Microsoft"
    Component="UsbFn"
    SubComponent="Settings"
    ReleaseType="Production"
    OwnerType="Microsoft"
    >
  <Macros>
    <Macro
        Id="MfgMode"
        Value="$(hklm.control)\ManufacturingMode"
        />
    <Macro
        Id="MfgModeProfile"
        Value="Default"
        />
    <Macro
        Id="MfgModeUsbFn"
        Value="$(MfgMode)\$(MfgModeProfile)\USBFN"
       />
  </Macros>
  <Components>
    <OSComponent>
      <RegKeys>
        <RegKey
            KeyName="$(MfgModeUsbFn)\Default"
            >
          <RegValue
              Name="bcdDevice"
              Type="REG_DWORD"
              Value="00000001"
              />
          <RegValue
              Name="bDeviceClass"
              Type="REG_DWORD"
              Value="00000000"
              />
          <RegValue
              Name="bDeviceProtocol"
              Type="REG_DWORD"
              Value="00000000"
              />
          <RegValue
              Name="bDeviceSubClass"
              Type="REG_DWORD"
              Value="00000000"
              />
          <RegValue
              Name="idProduct"
              Type="REG_DWORD"
              Value="0000F0CA"
              />
          <RegValue
              Name="idVendor"
              Type="REG_DWORD"
              Value="0000045E"
              />
          <RegValue
              Name="iManufacturer"
              Type="REG_DWORD"
              Value="00000001"
              />
          <RegValue
              Name="iProduct"
              Type="REG_DWORD"
              Value="00000002"
              />
          <RegValue
              Name="iSerialNumber"
              Type="REG_DWORD"
              Value="00000003"
              />
          <RegValue
              Name="ManufacturerString"
              Type="REG_SZ"
              Value="Microsoft"
              />
          <RegValue
              Name="ProductString"
              Type="REG_SZ"
              Value="Windows Phone 8.1"
              />
        </RegKey>
        <RegKey
            KeyName="$(MfgModeUsbFn)\Configurations\Default"
            >
          <RegValue
              Name="InterfaceList"
              Type="REG_MULTI_SZ"
              Value="IpOverUsb"
              />
          <RegValue
              Name="MSOSCompatIdDescriptor"
              Type="REG_BINARY"
              Value="28,00,00,00,00,01,04,00,01,00,00,00,00,00,00,00,00,01,4d,54,50,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00"
              />
        </RegKey>
        <RegKey
            KeyName="$(MfgModeUsbFn)\Interfaces\IpOverUsb"
            >
          <RegValue
              Name="InterfaceDescriptor"
              Type="REG_BINARY"
              Value="09,04,00,00,02,FF,FF,FF,00,07,05,81,02,00,02,00,07,05,02,02,00,02,00"
              />
          <RegValue
              Name="InterfaceGuid"
              Type="REG_SZ"
              Value="{30613563-7df3-4afb-80e0-e8c427c7e9bf}"
              />
          <RegValue
              Name="MSOSExtendedPropertyDescriptor"
              Type="REG_BINARY"
              Value="74,01,00,00,00,01,05,00,05,00,84,00,00,00,01,00,00,00,28,00,44,00,65,00,76,00,69,00,63,00,65,00,49,00,6E,00,74,00,65,00,72,00,66,00,61,00,63,00,65,00,47,00,55,00,49,00,44,00,00,00,4E,00,00,00,7B,00,32,00,36,00,66,00,65,00,64,00,63,00,34,00,65,00,2D,00,36,00,61,00,63,00,33,00,2D,00,34,00,32,00,34,00,31,00,2D,00,39,00,65,00,34,00,64,00,2D,00,65,00,33,00,64,00,34,00,62,00,32,00,63,00,35,00,63,00,35,00,33,00,34,00,7D,00,00,00,36,00,00,00,04,00,00,00,24,00,44,00,65,00,76,00,69,00,63,00,65,00,49,00,64,00,6C,00,65,00,45,00,6E,00,61,00,62,00,6C,00,65,00,64,00,00,00,04,00,00,00,01,00,00,00,34,00,00,00,04,00,00,00,22,00,44,00,65,00,66,00,61,00,75,00,6C,00,74,00,49,00,64,00,6C,00,65,00,53,00,74,00,61,00,74,00,65,00,00,00,04,00,00,00,01,00,00,00,38,00,00,00,04,00,00,00,26,00,44,00,65,00,66,00,61,00,75,00,6C,00,74,00,49,00,64,00,6C,00,65,00,54,00,69,00,6D,00,65,00,6F,00,75,00,74,00,00,00,04,00,00,00,10,27,00,00,44,00,00,00,04,00,00,00,32,00,55,00,73,00,65,00,72,00,53,00,65,00,74,00,44,00,65,00,76,00,69,00,63,00,65,00,49,00,64,00,6C,00,65,00,45,00,6E,00,61,00,62,00,6C,00,65,00,64,00,00,00,04,00,00,00,01,00,00,00"
              />
        </RegKey>
      </RegKeys>
    </OSComponent>
  </Components>
</Package>
```

然后可以使用 pkggen.exe （随 Windows 驱动程序工具包） 来创建包︰

``` syntax
pkggen.exe exampleUSBFN.pkg.xml /config:pkggen.cfg.xml
```

 

 





