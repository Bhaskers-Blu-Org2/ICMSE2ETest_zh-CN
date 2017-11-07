---
author: kpacquer
Description: "当您启动到制造模式时，可以跳过 OOBE，预安装应用程序来运行制造测试。"
ms.assetid: e448479f-6831-40b5-bb19-7ad4c22cdf6a
MSHAttr: PreferredLib:/library/windows/hardware
title: "创建完整的操作系统制造配置文件"
ms.openlocfilehash: cf3a19a55b85557c8da0742e2eeca6e74427d22e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="create-a-full-operating-system-manufacturing-profile"></a>创建完整的操作系统制造配置文件


当您启动到制造模式时，可以跳过 OOBE，预安装应用程序来运行制造测试。 跳过 OOBE 可以加速生产的时候。

若要对此进行设置，您可以添加应与制造配置文件一起安装的应用程序。 关于制造配置文件的详细信息，请参阅[制造模式](manufacturing-mode.md)。

## <a name="span-idaddappstoacustommanufacturingprofilespanspan-idaddappstoacustommanufacturingprofilespanspan-idaddappstoacustommanufacturingprofilespanadd-apps-to-a-custom-manufacturing-profile"></a><span id="Add_apps_to_a_custom_manufacturing_profile"></span><span id="add_apps_to_a_custom_manufacturing_profile"></span><span id="ADD_APPS_TO_A_CUSTOM_MANUFACTURING_PROFILE"></span>自定义制造配置文件中添加应用程序


在制造模式下的配置文件，您必须创建新的注册表项列表应该与制造配置文件一起安装的应用程序︰

``` syntax
HKEY_LOCAL_MACHINE\System\ControlSet001\Control\ManufacturingMode\<Profile Name>\Apps\OobeInstall
```

在 OOBEInstall 注册表项，您必须创建注册表项 (使用 REG\_DWORD 类型) 的每个应用程序。 该注册表项的名称必须与应用程序软件包的文件名匹配。

例如，要添加制造配置文件设置的应用程序，您添加一个名为**systemsettings**的注册表项。

以下是在制造配置文件中添加应用程序时需要考虑的一些事项︰

-   生产配置文件不得禁用任何 Windows 服务。
-   该注册表项的值被保留。 使用仅的注册表项名称。
-   应用程序可以是第一或第二方的应用程序，但应用程序软件包必须是图像的一部分。
-   \*通配符可用于应用程序的名称。
-   如果要将普通 OOBE 体验 （与安装的所有应用程序），创建一个注册表项的名称**\***。

### <a name="span-idfindthenameoftheappspanspan-idfindthenameoftheappspanspan-idfindthenameoftheappspanfind-the-name-of-the-app"></a><span id="Find_the_name_of_the_app"></span><span id="find_the_name_of_the_app"></span><span id="FIND_THE_NAME_OF_THE_APP"></span>查找应用程序的名称

该注册表项的名称必须与应用程序软件包的文件名匹配。 您可以通过运行下面的命令在该设备的驱动器的根都在设备的应用程序的列表︰

``` syntax
dir /S MPAP_*.provxml
```

此命令返回文件，类似于以下的列表︰

``` syntax
MPAP_systemsettings_001.provxml
```

之后文件名的一部分**MPAP\_**和**\_0xx.provxml**是您应使用的注册表项名称。

## <a name="span-idaddtheregistrykeystoyourcustommanufacturingprofilepackagespanspan-idaddtheregistrykeystoyourcustommanufacturingprofilepackagespanspan-idaddtheregistrykeystoyourcustommanufacturingprofilepackagespanadd-the-registry-keys-to-your-custom-manufacturing-profile-package"></a><span id="Add_the_registry_keys_to_your_custom_manufacturing_profile_package"></span><span id="add_the_registry_keys_to_your_custom_manufacturing_profile_package"></span><span id="ADD_THE_REGISTRY_KEYS_TO_YOUR_CUSTOM_MANUFACTURING_PROFILE_PACKAGE"></span>将注册表项添加到您的自定义制造配置文件包


添加注册表键到您的自定义制造配置文件打包起来就像使用任何其他包。 关于打包的详细信息，请参阅[创建电话包](https://msdn.microsoft.com/library/dn756642)。

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<Package xmlns="urn:Microsoft.WindowsPhone/PackageSchema.v8.00"
        Owner="Contoso"
        Component="MfgMode"
        SubComponent="Manufacturing.FactoryTestSample"
        ReleaseType="Production"
        OwnerType="OEM">

    <Macros>
      <Macro Id="MfgMode" Value="$(hklm.control)\ManufacturingMode" />
      <Macro Id="CustomProfile" Value="$(MfgMode)\CustomProfile" />
    </Macros>

    <Components>
        <OSComponent>
          <RegKeys>
            <RegKey KeyName="$(CustomProfile)\"/>
            <RegKey KeyName="$(CustomProfile)\Services"/>
            <RegKey KeyName="$(CustomProfile)\Apps"/>
            <RegKey KeyName="$(CustomProfile)\Apps\OobeInstall">
                <RegValue Name="FactoryTestOEMSample" Value="0" Type="REG_DWORD"/>
                <RegValue Name="systemsettings" Value="0" Type="REG_DWORD"/>
             </RegKey>
          </RegKeys>
        </OSComponent>
    </Components>
</Package>
```

 

 





