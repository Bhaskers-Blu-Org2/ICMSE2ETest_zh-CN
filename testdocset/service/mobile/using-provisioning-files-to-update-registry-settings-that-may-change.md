---
author: kpacquer
Description: "使用配置文件来更新可能会更改注册表设置"
ms.assetid: 77262c4c-69e2-456e-909b-27bd4e0d21f1
MSHAttr: PreferredLib:/library/windows/hardware
title: "使用配置文件来更新可能会更改注册表设置"
ms.openlocfilehash: a0034301bdf19713b700156fbc91e8547e9b0199
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="using-provisioning-files-to-update-registry-settings-that-may-change"></a>使用配置文件来更新可能会更改注册表设置


标准的程序包的更新不会应用到已更改的注册表数据 — — 例如，通过改变菜单的用户设置都会存储在注册表中。 若要更新此类别的注册表数据的值，设置 XML (provxml)，必须使用。 如果不使用 provxml 来更新该设备已在工厂中刷新后被更改的注册表数据，更新成功报告给用户，但在标准更新注册表更改将不会应用。

**重要**  
可以通过使用标准更新处理注册表更新将不会更改的条目。 不可避免地需要更新程序可能会更改注册表项时，仅使用 provxml 文件中更新。

 

## <a name="span-idavoidingtheneedspanspan-idavoidingtheneedspanspan-idavoidingtheneedspanregistry-update-strategies"></a><span id="AvoidingTheNeed"></span><span id="avoidingtheneed"></span><span id="AVOIDINGTHENEED"></span>注册表更新策略


若要避免需要更新现有的注册表数据，您的代码无法更新读取现有的注册表数据并将其迁移到新的密钥，以便保留任何现有的用户设置。 或者，例如当应用程序启动 （以确定使用哪个注册表值） 添加版本编号检查方法可能比较适当。 如果这些方法都不可能，可以用 provxml 来覆盖现有的注册表设置。

## <a name="span-idupdatingregistrysettingswithprovxmlspanspan-idupdatingregistrysettingswithprovxmlspanspan-idupdatingregistrysettingswithprovxmlspanupdating-registry-settings-with-provxml"></a><span id="Updating_registry_settings_with_provxml"></span><span id="updating_registry_settings_with_provxml"></span><span id="UPDATING_REGISTRY_SETTINGS_WITH_PROVXML"></span>用 provxml 更新注册表设置


大多数更新可以创建无需置备 XML (provxml)。 但也有某些情况下，provxml 使用可能要求。 如果用户设置或在应用此更新之前的任何时间在手机执行的代码可以修改的注册表值，标准软件包更新尊重这些更改并不会覆盖现有的注册表数据。 在此情况下，必须使用此处所述 provxml。

您可以使用 OMA CP 资源调配使用 provxml。

此示例 provxml 将设置一个注册表项的值。

``` syntax
<wap-provisioningdoc>
  <characteristic type="Registry">
    <characteristic type="HKLM\Software\ExampleRegistryKey>
      <parm name="ExampleSettingName" value="0" datatype="integer"/>
    </characteristic>
  </characteristic>
</wap-provisioningdoc>
```

Provxml 命名文件中使用下面的语法︰

``` syntax
mxipupdate_PackageName_n.provxml
```

对于*n*的第一个更新的值，请从 001 开始和递增的值对于每个后续更新。 所有 provxml 更新指定*n*的顺序都应用。

``` syntax
mxipupdate_updateExample_001.provxml
```

## <a name="span-idcreatingapackagefortheprovxmlspanspan-idcreatingapackagefortheprovxmlspanspan-idcreatingapackagefortheprovxmlspancreating-a-package-for-the-provxml"></a><span id="Creating_a_package_for_the_provxml"></span><span id="creating_a_package_for_the_provxml"></span><span id="CREATING_A_PACKAGE_FOR_THE_PROVXML"></span>Provxml 为创建包


创建的包文件中将这些文件放在正确的更新目录如下所示。 提供适当的所有者值。 有关更多信息，请参见[包项目文件的主元素和属性](https://msdn.microsoft.com/library/dn756796)。

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<Package xmlns="urn:Microsoft.WindowsPhone/PackageSchema.v8.00"
    Owner="Contoso"
    OwnerType="OEM"
    Platform="" 
    Component="Update"
    SubComponent="PROVXML"
    ReleaseType="Production"
>
  <Components>
    <OSComponent>
      <Files>
        <File Source="mxipupdate_updateExample_001.provxml" 
          DestinationDir="$(runtime.updateProvxmlOEM)" />
      </Files>
    </OSComponent>
  </Components>
</Package>
```

生成包，然后 OS 映像，可用于提交到 Microsoft 更新中包括的供应包。 有关详细信息，请参阅[创建程序包](https://msdn.microsoft.com/library/dn756642)和[提交更新](submit-an-update.md)。

## <a name="span-idresettingthephoneandprovxmlregistryupdatesspanspan-idresettingthephoneandprovxmlregistryupdatesspanspan-idresettingthephoneandprovxmlregistryupdatesspanresetting-the-phone-and-provxml-registry-updates"></a><span id="Resetting_the_phone_and_provxml_registry_updates"></span><span id="resetting_the_phone_and_provxml_registry_updates"></span><span id="RESETTING_THE_PHONE_AND_PROVXML_REGISTRY_UPDATES"></span>重置电话和 provxml 注册表更新


更新 provxml 文件进行处理后更新应用于该设备。 应用此更新后，在基本操作系统映像和当前的活动注册表中存储注册表更改。 这意味着，当重置设备时，已发送的更新中的注册表更改都存在，但对相关联的存储应用程序使用这些注册表设置的更新可能不会显示在设备上。 Oem 准备更新，它们必须确定可能的使用方案，如重置，请电话和测试那些以创建所需的用户体验。

## <a name="span-idtestingprovisioningfileinupdatesspanspan-idtestingprovisioningfileinupdatesspanspan-idtestingprovisioningfileinupdatesspantesting-provisioning-file-in-updates"></a><span id="Testing_provisioning_file_in_updates"></span><span id="testing_provisioning_file_in_updates"></span><span id="TESTING_PROVISIONING_FILE_IN_UPDATES"></span>更新的测试配置文件


两种方案必须进行测试，以验证更新配置文件︰

-   更新 — — 使用基本映像，应用此更新。 验证了应用 provxml 中的更改。

-   重置 — — 要更新电话后测试这一点，请使用**设置** &gt; **系统** &gt; **有关** &gt; **重置您的电话**。 验证已应用 provxml 的更新变化。

务必要验证此更新将工作正常，是否用户已更改的设置，更新目标。 此外，应遵循更新测试的标准指南。 有关详细信息，请参阅[测试更新](test-an-update.md)。

## <a name="span-idprovxmlupdateerrorhandlingspanspan-idprovxmlupdateerrorhandlingspanspan-idprovxmlupdateerrorhandlingspanprovxml-update-error-handling"></a><span id="Provxml_update_error_handling"></span><span id="provxml_update_error_handling"></span><span id="PROVXML_UPDATE_ERROR_HANDLING"></span>Provxml 更新错误处理


在更新期间，在最大努力的基础上处理 provxml 文件。 如果因为格式错误或权限问题而无法处理的 provxml 文件，则跳过该文件，并继续进行后续的 provxmls 的处理。 在开发中的 prvoxml，您可以检查存储在注册表的以下位置中的状态**HKLM\\软件\\Microsoft\\Windows\\CurrentVersion\\DataMigrationFramework\\ProvisioningStatus\\Microsoft**。 为处理时，每个 provxml 文件创建注册表项并处理文件从 HRESULT 存储为项的值。

 

 





