---
title: "创建自定义配置服务提供程序"
description: "创建自定义配置服务提供程序"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 0cb37f03-5bf2-4451-8276-23f4a1dee33f
ms.openlocfilehash: eb2d7a0ec76b770246f5d3263e528f326c9187c3
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="create-a-custom-configuration-service-provider"></a>创建自定义配置服务提供程序

移动设备 Oem 可以创建自定义配置服务提供程序来管理他们的设备。 配置服务提供程序包含用于创建、 编辑和删除节点和节点自身的接口。 每个节点包含一个注册表值数据，也可以选择支持 get，设置，以及删除操作。

若要设计一个自定义配置服务提供商，OEM 必须执行以下步骤︰

1.  建立节点的语义
2.  配置服务提供商的子树的形状
3.  选择一种事务方案的每个节点
4.  确定节点操作

有关详细信息，请参见[设计一个自定义配置服务提供程序](design-a-custom-windows-csp.md)。

若要编写自定义配置服务提供商，OEM 必须实现以下接口︰

-   [IConfigServiceProvider2](iconfigserviceprovider2.md)（每一次配置服务提供程序）

-   [ICSPNode](icspnode.md)（每个节点一个）

-   [ICSPNodeTransactioning](icspnodetransactioning.md)（可选，只有内部事务节点）

-   [ICSPValidate](icspvalidate.md)（可选，只有 ui）

此代码必须编译到单个.dll 文件，并可以通过使用"添加内容到包"中[创建包](https://msdn.microsoft.com/en-us/library/windows/hardware/dn756642)中的说明添加到包。 在编写此代码时，Oem 可以在以下位置存储注册表设置和文件。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>文件位置</strong></p></td>
<td><p>%DataDrive%\SharedData\OEM\CSP\</p></td>
</tr>
<tr class="even">
<td><p><strong>注册表位置</strong></p></td>
<td><p>$ (HKLM。软件） \OEM\CSP\</p></td>
</tr>
</tbody>
</table>


有关如何执行常见任务，如添加节点，替换节点的值的示例查询节点的值或枚举节点的子节点，请参阅[编写自定义配置服务提供程序的示例](samples-for-writing-a-custom-configuration-service-provider.md)。

要注册为 COM 对象的配置服务提供程序，必须将下面的注册表设置添加到包。 此步骤是必需的。 在下面的示例中，将*uniqueCSPguid*替换为此目的生成新的、 唯一 CLSID。 包含配置服务提供程序的代码的.dll 文件的名称替换*dll 名称*。

``` syntax
<RegKeys>
    <RegKey KeyName="$(HKCR.CLASSES)\CLSID\{uniqueCSPguid}\InprocServer32">
        <RegValue Name="@" Type="REG_SZ" Value="dllName.dll" />
    </RegKey>
</RegKeys>
```

要注册 ConfigManager2 配置服务提供程序，必须到包添加下面的注册表设置。 此步骤是必需的。 在以下示例中，配置服务提供程序 （根节点的名称） 的名称替换*dll 名称*。 如前面的示例中所示相同的*uniqueCSPguid*值替换*uniqueCSPguid* 。

``` syntax
<RegKeys>
   <RegKey KeyName="$(HKLM.SOFTWARE)\Microsoft\Provisioning\CSPs\.\Vendor\OEM\{Name}">
       <RegValue Name="@" Value="{uniqueCSPguid}" Type="REG_SZ"/>
   </RegKey>
</RegKeys>
```

从 WAP XML 进行配置服务提供程序可访问，您必须注册它 WAP 数据处理单元通过在您的程序包设置下面的注册表项。 配置服务提供程序的名称替换*名称*。 将 GUID 值完全写入此处。

``` syntax
<RegKeys>
   <RegKey KeyName="$(HKLM.SOFTWARE)\Classes\Name">
       <RegValue Name="WAPNodeProcessor" Value="{FB11047A-4051-4d1d-9DCA-C80C5DF98D70}" 
          Type="REG_SZ"/>
   </RegKey>
</RegKeys>
```

 






