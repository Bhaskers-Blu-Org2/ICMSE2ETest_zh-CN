---
author: kpacquer
Description: "如果您想要测试制造模式，您可以通过使用 ffutool.exe 或使用 BCD 设置启用它。"
ms.assetid: a5506896-0692-4256-a307-075da141ad44
MSHAttr: PreferredLib:/library/windows/hardware
title: "启用或禁用制造模式"
ms.openlocfilehash: 174e0af1d93a728e7789f2c2a11e1c52aa552e23
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="enable-or-disable-manufacturing-mode"></a>启用或禁用制造模式


如果您想要测试制造模式，您可以通过使用 ffutool.exe 或使用 BCD 设置启用它。

**请注意** 支持制造模式对运输设备的推荐的方式是固件支持引导模式管理 （uefi） 协议。 这个协议的详细信息，请参阅[启动模式管理 （uefi） 协议](boot-mode-management-uefi-protocol.md)。

 

## <a name="span-idenableordisablemanufacturingmodewithffutoolexespanspan-idenableordisablemanufacturingmodewithffutoolexespanenable-or-disable-manufacturing-mode-with-ffutoolexe"></a><span id="enable_or_disable_manufacturing_mode_with_ffutool.exe"></span><span id="ENABLE_OR_DISABLE_MANUFACTURING_MODE_WITH_FFUTOOL.EXE"></span>启用或禁用 ffutool.exe 与制造模式


如果设备支持的启动模式 （uefi） 协议，您可以启用或禁用与 ffutool.exe 的制造模式，通过使用**setBootMode**参数。 语法如下所示︰

``` syntax
ffutool.exe -setBootMode <boot mode> <profile name>
```

-   一个整数，对应的启动模式*启动模式*— 记录在[EFI\_启动\_模式\_信息枚举](efi-boot-mode-info-enumeration.md)。
-   *配置文件名称*--能够制造配置文件的名称。 当启动模式设置为 1，并且在启动模式设置为 0 时被忽略，这是必需的。

下面的示例使制造模式，并使用一个称为 CustomProfile 的生产配置文件︰

``` syntax
ffutool.exe -setBootMode 1 CustomProfile
```

下面的示例禁用制造模式，允许操作系统可以正常启动︰

``` syntax
ffutool.exe -setBootMode 0
```

## <a name="span-idenablemanufacturingmodewithabcdsettingspanspan-idenablemanufacturingmodewithabcdsettingspanspan-idenablemanufacturingmodewithabcdsettingspanenable-manufacturing-mode-with-a-bcd-setting"></a><span id="Enable_Manufacturing_Mode_with_a_BCD_setting"></span><span id="enable_manufacturing_mode_with_a_bcd_setting"></span><span id="ENABLE_MANUFACTURING_MODE_WITH_A_BCD_SETTING"></span>用 BCD 设置启用制造模式


MfgMode BCD 设置可用于测试使用自定义的制造模板的制造模式。 MfgMode 是一个字符串值，设置为您制造的自定义配置文件的名称。

例如，您可以启动设备在制造模式下使用默认制造配置文件的设备上运行以下命令︰

``` syntax
bcdedit.exe /set {default} mfgmode "default"
```

或者，您可以启动设备在制造模式下使用自定义制造配置文件命名，CustomProfile，通过执行以下︰

``` syntax
bcdedit.exe /set {default} mfgmode "CustomProfile"
```

您还可以在脱机设备已接通电源并在 USB 大容量存储模式下启用它。 例如︰

``` syntax
bcdedit.exe /store "D:\EFIESP\efi\Microsoft\Boot\BCD" /set {default} mfgmode "default"
```

**请注意** 如果您使用较旧版本的 bcdedit.exe，您可能需要**自定义︰ 22000140**而不是**mfgmode**用作 BCD 设置名称。

 

## <a name="span-idcreateamanufacturingmodebcdpackagespanspan-idcreateamanufacturingmodebcdpackagespanspan-idcreateamanufacturingmodebcdpackagespancreate-a-manufacturing-mode-bcd-package"></a><span id="Create_a_Manufacturing_Mode_BCD_package"></span><span id="create_a_manufacturing_mode_bcd_package"></span><span id="CREATE_A_MANUFACTURING_MODE_BCD_PACKAGE"></span>创建制造模式 BCD 包


您可以创建创建 MfgMode BCD 条目并将其设置为您自定义制造的配置文件的包。 若要执行此操作，必须首先创建引用 BCD 条目的 XML 文件︰

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<BootConfigurationDatabase xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/phone/2011/10/BootConfiguration">
  <Objects>

    <!-- Global Settings Group -->
    <Object SaveKeyToRegistry="false">
      <FriendlyName>Windows Loader</FriendlyName>
      <Elements>

        <Element>
          <DataType>
            <WellKnownType>Manufacturing Mode</WellKnownType>
          </DataType>
          <ValueType>
            <StringValue>Default</StringValue>
          </ValueType>
        </Element>

      </Elements>
    </Object>

  </Objects>
</BootConfigurationDatabase>
```

创建后，您可以在包 XML 文件引用︰

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<Package xmlns="urn:Microsoft.WindowsPhone/PackageSchema.v8.00"
        Owner="Contoso"
        Component="MfgMode"
        SubComponent="ManufacturingModeBcd"
        ReleaseType="Production"
        Partition="EFIESP"
        OwnerType="OEM">

    <Components>
        <BCDStore Source=".\exampleBcd.bcd.xml"/>
    </Components>
</Package>
```

**请注意** 没有定义这些 BCD 条目需要应用于 EFIESP 分区的分区特性。 这应更新为 BCD 存储设备所在的分区。 如果这是不同于分区主操作系统驻留的位置，从相同的包无法进行其他操作，例如将文件和注册表项添加到主操作系统分区。

 

若要创建程序包，可以使用 pkggen.exe （随 Windows 驱动程序工具包）︰

``` syntax
pkggen.exe exampleBcd.pkg.xml /config:pkggen.cfg.xml
```

 

 





