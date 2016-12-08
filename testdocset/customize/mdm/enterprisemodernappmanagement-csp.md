---
title: "EnterpriseModernAppManagement 的 CSP"
description: "EnterpriseModernAppManagement 的 CSP"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 9DD0741A-A229-41A0-A85A-93E185207C42
ms.openlocfilehash: 581196a453472b3db564beb2da2c8cb36508644e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="enterprisemodernappmanagement-csp"></a>EnterpriseModernAppManagement 的 CSP


资源调配和报告的现代企业应用程序使用 EnterpriseModernAppManagement 配置服务提供程序 (CSP)。 有关如何使用该 CSP 对报告应用程序清单、 安装和删除应用程序的用户的详细信息，资源调配设备、 应用程序和管理应用程序的许可证，请参见[企业应用程序管理](enterprise-app-management.md)。

> **请注意** Windows 全息仅支持每用户配置的 EnterpriseModernAppManagement csp。

 

下面的图像以树格式显示 EnterpriseModernAppManagement 配置服务提供程序。

![enterprisemodernappmanagement 的 csp 图](images/provisioning-csp-enterprisemodernappmanagement.png)![enterprisemodernappmanagement 的 csp 图](images/provisioning-csp-enterprisemodernappmanagement2.png)

<a href="" id="device-or-user-context"></a>**设备或用户上下文**  
对于用户的上下文中，使用**./User/Vendor/MSFT**路径和设备上下文中，使用**./Device/Vendor/MSFT**路径。

> **请注意** Windows 全息和 Windows 10 移动只支持每用户配置的 EnterpriseModernAppManagement CSP。

 

<a href="" id="appmanagement"></a>**AppManagement**  
必需。 用于库存和应用程序管理 （安装后）。

<a href="" id="appmanagement-updatescan"></a>**AppManagement/UpdateScan**  
必需。 用来启动 Windows 更新扫描。

受支持的操作被执行。

<a href="" id="appmanagement-lastscanerror"></a>**AppManagement/LastScanError**  
必需。 报告由更新扫描返回的最后一个错误代码。

受支持的操作是获得。

<a href="" id="appmanagement-appinventoryquery"></a>**AppManagement/AppInventoryQuery**  
添加 Windows 10 1511年版本中。 必需。 指定的查询的应用程序清单。

查询参数︰

-   输出-指定用于在 AppInventoryResults 操作返回的信息的参数。 多个值必须是单独的 |。 有效值包括︰
    -   PackagesName-返回的*PackageFamilyName*和*PackageFullName*的应用程序。 如果未进行指定的默认值。
    -   PackageDetails-返回包的所有库存属性。 这包括从 PackageNames 参数的所有信息，但不会验证 RequiresReinstall。
    -   RequiredReinstall-验证库存查询，以确定他们是否要求重新安装应用程序的应用程序状态。 此属性可能会影响系统性能，具体取决于安装的应用程序数目。 需要重新安装更新资源包或应用程序处于篡改状态时发生。
-   源-指定对齐到现有库存节点的应用程序分类。 可以使用特定的筛选器，或者如果不指定任何筛选器的所有源将会都返回。 如果未不指定任何值，则返回所有分类。 有效值包括︰
    -   AppStore 的此分类是用于收购从 Windows 应用商店的应用程序。 这些是从 Windows 应用商店或企业应用程序从 Windows 应用商店业务直接安装的应用程序。
    -   nonStore-此分类是用于不收购从 Windows 应用商店的应用程序。
    -   系统的应用程序是操作系统的一部分。 您不能卸载这些应用程序。 此分类是只读的只可以清点。
-   PackageTypeFilter-指定一个或多个类型的程序包，您可以使用查询的用户或设备。 必须用分隔多个值 |。 有效值包括︰

    -   主窗口-返回主已安装的软件包。
    -   捆绑在一起-返回已安装的软件包的软件包。
    -   框架-返回框架安装的程序包。
    -   资源-返回安装的资源包。 资源是语言、 小数位数或 DirectX 资源。 它们是观音菩萨的部分。
    -   XAP-返回 XAP 包类型。
    -   All-返回的所有包类型。

    如果未不指定任何值，将返回主、 捆绑、 框架和 XAP 的组合。

-   PackageFamilyName-指定某个特定的包的名称。 如果指定此参数，则返回包系列名称，如果包中包含此值。

    如果不指定此值，则返回所有软件包。

-   发布服务器上的指定特定包的发布服务器。 如果指定此参数，它返回发布服务器，如果在发布服务器字段中的值存在。

    如果不指定此值，则返回所有出版商。

受支持的操作是获得和替换。

下面的示例设置软件包名称的库存查询并检查适用于所有主包的 nonStore 应用程序重新安装的状态。

``` syntax
<Replace>
   <CmdID>10</CmdID>
   <Item>
      <Target>
         <LocURI>./User/Vendor/MSFT/EnterpriseModernAppManagement/AppManagement/AppInventoryQuery</LocURI>
      </Target>
      <Meta><Format xmlns="syncml:metinf">xml</Format></Meta>
      <Data><Inventory Output="PackageNames|RequiresReinstall" Source="nonStore" PackageTypeFilter="Main" /></Data>
   </Item>
</Replace>
```

<a href="" id="appmanagement-appinventoryresults"></a>**AppManagement/AppInventoryResults**  
添加 Windows 10 1511年版本中。 必需。 返回 AppInventoryQuery 操作之后创建的应用程序清单的结果。

受支持的操作是获得。

这里是 AppInventoryResults 操作的一个示例。

``` syntax
<Get>
   <CmdID>11</CmdID>
   <Item>
      <Target>
         <LocURI>./User/Vendor/MSFT/EnterpriseModernAppManagement/AppManagement/AppInventoryResults</LocURI>
      </Target>
   </Item>
</Get>
```

<a href="" id="appmanagement-nonstore"></a>**AppManagement/nonStore**  
用来管理企业应用程序或开发人员的应用程序从 Windows 应用商店不收购。

受支持的操作是获得。

<a href="" id="appmanagement-system"></a>**AppManagement/系统**  
将报告作为操作系统的一部分安装的应用程序。

受支持的操作是获得。

<a href="" id="appmanagement-appstore"></a>**AppManagement/AppStore**  
必需。 用于管理从 Windows 应用商店应用程序。

支持的操作包括获取和删除。

<a href="" id="----packagefamilyname"></a>**.../ ***_PackageFamilyName_**  
可选项。 该应用程序的包姓 (PFN)。 没有一个用于每个设备上 PFN 报告库存时。 这些项目植根在他们签名的来源。

支持的操作包括获取和删除。

> **请注意** XAP 文件使用代替 PackageFamilyName 的产品 ID。 下面是一个示例的 XAP 产品 ID （包括括号），{12345678-9012-3456-7890-123456789012}。

 

下面是一个用于卸载应用程序的示例︰

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.2">
  <SyncBody>
        <!-- Uninstall app -->
        <delete>
           <CmdID>2</CmdID>
              <Item>
                 <Target>
                    <LocURI>./User/Vendor/MSFT/EnterpriseModernAppManagement/AppManagement/AppStore/%7b12345678-9012-3456-7890-123456789012%7D</LocURI>
                 </Target>
              </Item>
        </delete>
     <Final/>
  </SyncBody>
</SyncML>
```

<a href="" id="----packagefamilyname-packagefullname"></a>**.../*PackageFamilyName*/****_PackageFullName_**  
可选项。 安装程序包的完整名称。

支持的操作包括获取和删除。

> **请注意** XAP 文件使用代替 PackageFullName 的产品 ID。 下面是一个示例的 XAP 产品 ID （包括括号），{12345678-9012-3456-7890-123456789012}。

 

<a href="" id="----packagefamilyname-packagefullname-name"></a>**.../*PackageFamilyName*/*PackageFullName*/Name**  
必需。 该应用程序的名称。 值类型是字符串。

受支持的操作是获得。

<a href="" id="----packagefamilyname-packagefullname-version"></a>**.../*PackageFamilyName*/*PackageFullName*/Version**  
必需。 该应用程序的版本。 值类型是字符串。

受支持的操作是获得。

<a href="" id="----packagefamilyname-packagefullname-publisher"></a>**.../*PackageFamilyName*/*PackageFullName*/Publisher**  
必需。 应用程序的发布服务器名称。 值类型是字符串。

受支持的操作是获得。

<a href="" id="----packagefamilyname-packagefullname-architecture"></a>**.../*PackageFamilyName*/*PackageFullName*/Architecture**  
必需。 已安装的软件包体系结构。 值类型是字符串。

> **请注意** 对 XAP 文件不适用。

 

受支持的操作是获得。

<a href="" id="----packagefamilyname-packagefullname-installlocation"></a>**.../*PackageFamilyName*/*PackageFullName*/InstallLocation**  
必需。 在设备上安装应用程序的位置。 值类型是字符串。

> **请注意** 对 XAP 文件不适用。

 

受支持的操作是获得。

<a href="" id="----packagefamilyname-packagefullname-isframework"></a>**.../*PackageFamilyName*/*PackageFullName*/IsFramework**  
必需。 无论应用程序是 framework 程序包。 值类型是 int。 如果应用程序框架包和其他所有情况下为 0 （零），则值为 1。

> **请注意** 对 XAP 文件不适用。

 

受支持的操作是获得。

<a href="" id="----packagefamilyname-packagefullname-isbundle"></a>**.../*PackageFamilyName*/*PackageFullName*/IsBundle**  
必需。 如果包是应用程序捆绑包和其他所有情况下为 0 （零），则值为 1。 值类型是 int。

受支持的操作是获得。

<a href="" id="----packagefamilyname-packagefullname-installdate"></a>**.../*PackageFamilyName*/*PackageFullName*/InstallDate**  
必需。 该应用程序的安装日期。 值类型是字符串。

受支持的操作是获得。

<a href="" id="----packagefamilyname-packagefullname-resourceid"></a>**.../*PackageFamilyName*/*PackageFullName*/ResourceID**  
必需。 应用程序的资源 ID。 这是主应用程序中，对于 ~ 捆绑包，并包含资源信息的资源包。 值类型是字符串。

> **请注意** 对 XAP 文件不适用。

 

受支持的操作是获得。

<a href="" id="----packagefamilyname-packagefullname-packagestatus"></a>**.../*PackageFamilyName*/*PackageFullName*/PackageStatus**  
必需。 提供软件包的状态的信息。 值类型是 int。 有效值包括︰

-   (0)-确定包是否可用。
-   LicenseIssue (1)-包的是许可证无效。
-   修改 (2)-未知来源的修改数据包有效负载。
-   篡改 (4) 的数据包有效负载被故意破坏。
-   已禁用 (8) 的包不是可供使用。 仍然可以处理。

> **请注意** 对 XAP 文件不适用。

 

受支持的操作是获得。

<a href="" id="----packagefamilyname-packagefullname-requiresreinstall"></a>**.../*PackageFamilyName*/*PackageFullName*/RequiresReinstall**  
必需。 指定程序包状态是否已更改并需要重新安装该应用程序。 新的应用程序资源是必需的例如当设备具有语言首选项或新 DPI 变化可发生该错误。 它也可能发生的包已损坏。 如果值为 1，则执行重新安装该应用程序。 值类型是 int。

> **请注意** 对 XAP 文件不适用。

 

受支持的操作是获得。

<a href="" id="----packagefamilyname-packagefullname-users"></a>**.../*PackageFamilyName*/*PackageFullName*/Users**  
必需。 应用程序的已注册的用户。 如果查询是在设备级别时，它会返回设备的所有已注册的用户。 如果查询的用户上下文时，它将只返回当前用户。 值类型是字符串。

受支持的操作是获得。

<a href="" id="----packagefamilyname-packagefullname-isprovisioned"></a>**.../*PackageFamilyName*/*PackageFullName*/IsProvisioned**  
必需。 值为 0 或 1，该值指示是否在设备上配置应用程序。 值类型是 int。

受支持的操作是获得。

<a href="" id="----packagefamilyname-donotupdate"></a>* *.../*PackageFamilyName*/DoNotUpdate**  
必需。 指定您是否要阻止通过自动更新更新特定的应用程序。

支持的操作是添加 Get，删除和替换。

<a href="" id="----packagefamilyname-appsettingpolicy---only-for---user-vendor-msft-"></a>* *.../*PackageFamilyName*/AppSettingPolicy** （仅适用于./User/Vendor/MSFT)  
添加 Windows 10 1511年版本中。 设置值的所有托管应用程序的内部节点。 在用户上下文中才支持此节点。

<a href="" id="----packagefamilyname-appsettingpolicy-settingvalue---only-for---user-vendor-msft-"></a>**.../*PackageFamilyName*/AppSettingPolicy / ***_SettingValue_ * * （仅适用于./User/Vendor/MSFT) 添加 Windows 10 1511年版本中。*SettingValue*和数据表示键/值对来配置应用程序。 节点表示的项的名称和数据表示的值。

此设置仅适用于支持该功能的应用程序，而且只支持在用户上下文中。

值类型是字符串。 支持的操作是添加 Get，替换和删除。

下面的示例为服务器设置的值

``` syntax
<!— Configure app settings -->
<Add>
   <CmdID>0</CmdID>
   <Item>
      <Target>
         <LocURI>./User/Vendor/MSFT/EnterpriseModernAppManagement/AppManagement/AppStore/PackageFamilyName/AppSettingPolicy/Server</LocURI>
      </Target>
      <Meta>
         <Format xmlns="syncml:metinf">chr</Format>
      </Meta>
      <Data>server1.contoso.com</Data>
   </Item>
</Add>
```

下面的示例获取特定的应用程序的所有托管的应用程序设置。

``` syntax
<!—Get app settings -->
<Get>
   <CmdID>0</CmdID>
   <Item>
      <Target>
         <LocURI>./User/Vendor/MSFT/EnterpriseModernAppManagement/AppManagement/AppStore/PackageFamilyName/AppSettingPolicy?list=StructData</LocURI>
      </Target>
   </Item>
</Get>
```

<a href="" id="appinstallation"></a>**AppInstallation**  
所需的节点。 用来执行应用程序的安装。

<a href="" id="appinstallation-packagefamilyname"></a>**AppInstallation / ***_PackageFamilyName_**  
可选的节点。 该应用程序的包姓 (PFN)。 没有一个用于每个设备上 PFN 报告库存时。 这些项目植根在他们签名的来源。

支持的操作包括获取和添加。

> **请注意** XAP 文件使用代替 PackageFamilyName 的产品 ID。 下面是一个示例的 XAP 产品 ID （包括括号），{12345678-9012-3456-7890-123456789012}。

 

<a href="" id="appinstallation-packagefamilyname-storeinstall"></a>* *AppInstallation /*PackageFamilyName*/StoreInstall**  
必需。 命令来执行 Windows 应用商店应用程序和许可证的安装。

受支持的操作被执行。

<a href="" id="appinstallation-packagefamilyname-hostedinstall"></a>* *AppInstallation /*PackageFamilyName*/HostedInstall**  
必需。 从托管位置 （可以是本地驱动器、 UNC 或 https 数据源） 执行应用程序软件包的安装命令。

受支持的操作被执行。

<a href="" id="appinstallation-packagefamilyname-lasterror"></a>* *AppInstallation /*PackageFamilyName*/LastError**  
必需。 与应用程序安装的最后一个错误。

受支持的操作是获得。

> **请注意** 此元素不存在该应用程序安装后。

 

<a href="" id="appinstallation-packagefamilyname-lasterrordescription"></a>* *AppInstallation /*PackageFamilyName*/LastErrorDescription**  
必需。 与应用程序安装的最后一个错误的说明。

受支持的操作是获得。

> **请注意** 此元素不存在该应用程序安装后。

 

<a href="" id="appinstallation-packagefamilyname-status"></a>* *AppInstallation /*PackageFamilyName*/Status**  
必需。 应用程序安装的状态。 返回下列值︰

-   不\_已安装 (0)-该节点已添加，但是执行尚未完成。
-   安装 (1)-已开始执行，但尚未完成部署。 如果无论成功完成部署，更新此值。
-   失败 (2)-安装失败。 错误的详细信息可在 LastError 和 LastErrorDescription 下找到。
-   (3)-已安装成功安装后此节点已被清除，但是万一清理操作未完成，这种状态可能会短暂显示。

受支持的操作是获得。

> **请注意** 此元素不存在该应用程序安装后。

 

<a href="" id="appinstallation-packagefamilyname-progessstatus"></a>* *AppInstallation /*PackageFamilyName*/ProgessStatus**  
必需。 一个整数，指示应用程序安装的进度。 对于 https 位置，这表明的下载进度。 ProgressStatus 可用于设置并不是只对基于用户的安装。 在资源调配时，的值始终为 0 （零）。

受支持的操作是获得。

> **请注意** 此元素不存在该应用程序安装后。

 

<a href="" id="applicenses"></a>**AppLicenses**  
所需的节点。 用于管理应用程序方案的许可证。

<a href="" id="applicenses-storelicenses"></a>**AppLicenses/StoreLicenses**  
所需的节点。 用于管理存储应用程序的许可证。

<a href="" id="applicenses-storelicenses-licenseid"></a>**AppLicenses/StoreLicenses / ***_LicenseID_**  
可选的节点。 存储的许可证 ID 安装应用程序。 许可证 ID 通常是应用程序的 PFN。

支持的操作是 Get，添加和删除。

<a href="" id="applicenses-storelicenses-licenseid-licensecategory"></a>* *AppLicenses/StoreLicenses/*LicenseID*/LicenseCategory**  
添加 Windows 10 1511年版本中。 必需。 许可证，用于分类各种许可证源的类别。 有效值︰

-   未知的未知的许可证类别
-   通过零售渠道，通常是从 Windows 应用商店销售许可证的零售-
-   企业-通过企业销售渠道，通常是从业务的存储销售许可证
-   OEM 的许可证颁发给 OEM
-   开发人员的开发人员许可，通常安装在应用程序开发或侧加载 scernarios。

受支持的操作是获得。

<a href="" id="applicenses-storelicenses-licenseid-licenseusage"></a>* *AppLicenses/StoreLicenses/*LicenseID*/LicenseUsage**  
添加 Windows 10 1511年版本中。 必需。 表示允许的使用的许可证。 有效值︰

-   未知-用法是未知
-   联机-许可证才有效供联机使用。 这是应用程序的并发需求，如应用程序在多台计算机上使用，但只能使用一个在任何给定的时间上。
-   脱机-许可证的有效期以供脱机使用。 您不需要连接到 internet 才能使用此许可证。
-   企业根-

受支持的操作是获得。

<a href="" id="applicenses-storelicenses-licenseid-requesterid"></a>* *AppLicenses/StoreLicenses/*LicenseID*/RequesterID**  
添加 Windows 10 1511年版本中。 必需。 请求许可证，获得许可证的客户端等实体的标识符。 例如，对于特定的企业客户端的存储业务颁发的所有许可证都有同一个 RequesterID。

受支持的操作是获得。

<a href="" id="applicenses-storelicenses-licenseid-addlicense"></a>* *AppLicenses/StoreLicenses/*LicenseID*/AddLicense**  
必需。 要添加许可证的命令。

受支持的操作被执行。

<a href="" id="applicenses-storelicenses-licenseid-getlicensefromstore"></a>* *AppLicenses/StoreLicenses/*LicenseID*/GetLicenseFromStore**  
添加 Windows 10 1511年版本中。 必需。 要从存储区获取许可证命令。

受支持的操作被执行。

## <a name="examples"></a>示例


有关如何使用到该 CSP 进行报告的应用程序清单、 安装和删除用户的应用程序的示例，调配设备、 应用程序和管理应用程序的许可证，请参阅[企业应用程序管理](enterprise-app-management.md)。

查询一个特定的应用程序子类别，如 nonStore 应用程序的设备。

``` syntax
<Get>
  <CmdID>1</CmdID>
  <Item>
    <Target>
      <LocURI>./Device/Vendor/MSFT/EnterpriseModernAppManagement/AppManagement/nonStore</LocURI>
    </Target>
  </Item>
</Get>
```

结果︰ 列出的应用程序，如&lt;数据&gt;App1/App2/App3&lt;/数据&gt;。

对于特定的应用程序对其属性的后续查询。

``` syntax
  
<Get>
   <CmdID>1</CmdID>
   <Item>
     <Target>
       <LocURI>./Device/Vendor/MSFT/EnterpriseModernAppManagement/AppManagement/nonStore/App1?list=StructData</LocURI>
     </Target>
   </Item>
</Get>
<Get>
  <CmdID>2</CmdID>
  <Item>
    <Target>
      <LocURI>./Device/Vendor/MSFT/EnterpriseModernAppManagement/AppManagement/nonStore/App2?list=StructData</LocURI>
    </Target>
  </Item>
</Get>
```

## <a name="related-topics"></a>相关的主题


[配置服务提供程序的引用](configuration-service-provider-reference.md)

 

 






