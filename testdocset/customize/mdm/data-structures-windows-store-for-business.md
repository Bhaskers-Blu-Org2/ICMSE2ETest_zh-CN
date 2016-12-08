---
title: "Windows 应用商店业务有关的数据结构"
MS-HAID:
- p\_phdevicemgmt.business\_store\_data\_structures
- p\_phDeviceMgmt.data\_structures\_windows\_store\_for\_business
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: ABE44EC8-CBE5-4775-BA8A-4564CB73531B
description: 
ms.openlocfilehash: 669c06f1bedafeb6f7b185a76fcc561b9d49e29d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="data-structures-for-windows-store-for-business"></a>Windows 应用商店业务有关的数据结构


下面是使用 Windows 应用商店业务 REST Api 的数据结构的列表︰

-   [AlternateIdentifier](#alternateidentifier)
-   [BulkSeatOperationResultSet](#bulkseatoperationresultset)
-   [FailedSeatRequest](#failedseatrequest)
-   [FrameworkPackageDetails](#frameworkpackagedetails)
-   [InventoryDistributionPolicy](#inventorydistributionpolicy)
-   [InventoryEntryDetails](#inventoryentrydetails)
-   [InventoryResultSet](#inventoryresultset)
-   [InventoryStatus](#inventorystatus)
-   [LicenseType](#licensetype)
-   [LocalizedProductDetail](#localizedproductdetail)
-   [OfflineLicense](#offlinelicense)
-   [PackageLocation](#packagelocation)
-   [ProductArchitectures](#productarchitectures)
-   [ProductDetails](#productdetails)
-   [ProductImage](#productimage)
-   [产品密钥](#productkey)
-   [ProductPackageDetails](#productpackagedetails)
-   [ProductPackageFormat](#productpackageformat)
-   [ProductPackageSet](#productpackageset)
-   [ProductPlatform](#productplatform)
-   [PublisherDetails](#publisherdetails)
-   [SeatAction](#seataction)
-   [SeatDetails](#seatdetails)
-   [SeatDetailsResultSet](#seatdetailsresultset)
-   [SeatState](#seatstate)
-   [SupportedProductPlatform](#supportedproductplatform)
-   [VersionInfo](#versioninfo)

## <a name="alternateidentifier"></a>AlternateIdentifier


指定备用标识符的属性。

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>名称</th>
<th>类型</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>类型</p></td>
<td><p>string</p></td>
<td><p>LegacyWindowStoreProductId，LegacyWindowsPhoneProductId，RedirectToThresholdProductId</p></td>
</tr>
<tr class="even">
<td><p>value</p></td>
<td><p>string</p></td>
<td></td>
</tr>
</tbody>
</table>

 

## <a name="bulkseatoperationresultset"></a>BulkSeatOperationResultSet


<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>名称</th>
<th>类型</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>seatDetails</p></td>
<td><p>[SeatDetails](#seatdetails)的集合</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>failedSeatOperations</p></td>
<td><p>[FailedSeatRequest](#failedseatrequest)的集合</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

 

## <a name="failedseatrequest"></a>FailedSeatRequest


<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>名称</th>
<th>类型</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>failureReason</p></td>
<td><p>string</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>产品密钥</p></td>
<td><p>[产品密钥](#productkey)</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>用户名</p></td>
<td><p>string</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

 

## <a name="frameworkpackagedetails"></a>FrameworkPackageDetails


<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>名称</th>
<th>类型</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>packageId</p></td>
<td><p>string</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>contentId</p></td>
<td><p>string</p></td>
<td><p>标识一个特定的应用程序</p></td>
</tr>
<tr class="odd">
<td><p>位置</p></td>
<td><p>[PackageLocation](#packagelocation)</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>packageFullName</p></td>
<td><p>string</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>packageIdentityName</p></td>
<td><p>string</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>体系结构</p></td>
<td><p>[ProductArchitectures](#productarchitectures)的集合</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>packageFormat</p></td>
<td><p>[ProductPackageFormat](#productpackageformat)</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>平台</p></td>
<td><p>[ProductPlatform](#productplatform)的集合</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>文件大小</p></td>
<td><p>整数-64</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>packageRank</p></td>
<td><p>整数 3232</p></td>
<td><p>可选</p></td>
</tr>
</tbody>
</table>

 

## <a name="inventorydistributionpolicy"></a>InventoryDistributionPolicy


<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>名称</th>
<th>类型</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>打开</p></td>
<td></td>
<td><p>打开的分布策略-许可证/座位可以是无限制分配/消耗</p></td>
</tr>
<tr class="even">
<td><p>限制</p></td>
<td></td>
<td><p>限制分发策略-许可证/座位必须根据可用计数分配/消耗</p></td>
</tr>
</tbody>
</table>

 

## <a name="inventoryentrydetails"></a>InventoryEntryDetails


<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>名称</th>
<th>类型</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>产品密钥</p></td>
<td><p>[产品密钥](#productkey)</p></td>
<td><p>在后续请求中用于获取其他内容，其中包括产品说明，脱机的许可证，并下载的 Url 标识符。</p></td>
</tr>
<tr class="even">
<td><p>seatCapacity</p></td>
<td><p>整数 64</p></td>
<td><p>已为应用程序购买的座位的总数</p></td>
</tr>
<tr class="odd">
<td><p>availableSeats</p></td>
<td><p>整数 64</p></td>
<td><p>剩余的应用程序的可用座位数。</p></td>
</tr>
<tr class="even">
<td><p>上次更改时间</p></td>
<td><p>dateTime</p></td>
<td><p>指定应用程序的上次修改的日期。 应用软件包的修改包括更新的产品详细信息、 应用程序的更新和更新的应用程序数量。</p></td>
</tr>
<tr class="odd">
<td><p>licenseType</p></td>
<td><p>[LicenseType](#licensetype)</p></td>
<td><p>指示的座位为给定的应用程序集是否支持在线或离线的授权。</p></td>
</tr>
<tr class="even">
<td><p>distributionPolicy</p></td>
<td><p>InventoryDistributionPolicy</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>status</p></td>
<td><p>InventoryStatus</p></td>
<td></td>
</tr>
</tbody>
</table>

 

## <a name="inventoryresultset"></a>InventoryResultSet


<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>名称</th>
<th>类型</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>continuationToken</p></td>
<td><p>string</p></td>
<td><p>continuationToken 只是下一个页面是否可用</p></td>
</tr>
<tr class="even">
<td><p>inventoryEntries</p></td>
<td><p>集合</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

 

## <a name="inventorystatus"></a>InventoryStatus


<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>名称</th>
<th>类型</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>活动</p></td>
<td><p></p></td>
<td><p>项是存在于组织的库存</p></td>
</tr>
<tr class="even">
<td><p>移除</p></td>
<td><p></p></td>
<td><p>从组织的库存已移除项</p></td>
</tr>
</tbody>
</table>

 

## <a name="licensetype"></a>LicenseType


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>名称</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>联机</p></td>
<td><p>在线的许可证的应用程序。</p></td>
</tr>
<tr class="even">
<td><p>脱机</p></td>
<td><p>脱机的许可证的应用程序。</p></td>
</tr>
</tbody>
</table>

 

## <a name="localizedproductdetail"></a>LocalizedProductDetail


指定属性的本地化产品。

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>名称</th>
<th>类型</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>language</p></td>
<td><p>string</p></td>
<td><p>语言或者如果指定的语言不是可用的备用语言。</p></td>
</tr>
<tr class="even">
<td><p>显示名称</p></td>
<td><p>string</p></td>
<td><p>应用程序的显示名称。</p></td>
</tr>
<tr class="odd">
<td><p>description</p></td>
<td><p>string</p></td>
<td><p>由开发人员提供应用程序说明可达 10000 个字符。</p></td>
</tr>
<tr class="even">
<td><p>图像</p></td>
<td><p>[ProductImage](#productimage)的集合</p></td>
<td><p>插图以及与应用程序关联的图标。</p></td>
</tr>
<tr class="odd">
<td><p>发布服务器</p></td>
<td><p>[PublisherDetails](#publisherdetails)</p></td>
<td><p>应用程序的发行者。</p></td>
</tr>
</tbody>
</table>

 

## <a name="offlinelicense"></a>OfflineLicense


<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>名称</th>
<th>类型</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>产品密钥</p></td>
<td><p>[产品密钥](#productkey)</p></td>
<td><p>标识一组与应用程序相关联的座位。</p></td>
</tr>
<tr class="even">
<td><p>licenseBlob</p></td>
<td><p>string</p></td>
<td><p>Base 64 编码，可以通过一个 CSP 安装的脱机许可证。</p></td>
</tr>
<tr class="odd">
<td><p>licenseInstanceId</p></td>
<td><p>string</p></td>
<td><p>许可证的版本。</p></td>
</tr>
<tr class="even">
<td><p>requestorId</p></td>
<td><p>string</p></td>
<td><p>请求许可证的组织。</p></td>
</tr>
<tr class="odd">
<td><p>contentId</p></td>
<td><p>string</p></td>
<td><p>标识应用程序所需的特定许可。</p></td>
</tr>
</tbody>
</table>

 

## <a name="productarchitectures"></a>ProductArchitectures


<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th>名称</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>neutral</p></td>
</tr>
<tr class="even">
<td><p>臂</p></td>
</tr>
<tr class="odd">
<td><p>x86</p></td>
</tr>
<tr class="even">
<td><p>x64</p></td>
</tr>
</tbody>
</table>

 

## <a name="packagecontentinfo"></a>PackageContentInfo


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>名称</th>
<th>类型</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>productPlatforms</p></td>
<td><p>[ProductPlatform](#productplatform)的集合</p></td>
</tr>
<tr class="even">
<td><p>packageFormat</p></td>
<td><p>string</p></td>
</tr>
</tbody>
</table>

 

## <a name="packagelocation"></a>PackageLocation


<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>名称</th>
<th>类型</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>url</p></td>
<td><p>URI</p></td>
<td><p>CDN 的包的位置。 URL 到期基于估计的时间要下载该程序包。</p></td>
</tr>
</tbody>
</table>

 

## <a name="productdetails"></a>ProductDetails


<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>名称</th>
<th>类型</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>产品密钥</p></td>
<td><p>[产品密钥](#productkey)</p></td>
<td><p>在后续请求中用于获取其他内容，其中包括产品说明，脱机的许可证，并下载的 Url 标识符。</p></td>
</tr>
<tr class="even">
<td><p>productType</p></td>
<td><p>string</p></td>
<td><p>产品的类型。</p></td>
</tr>
<tr class="odd">
<td><p>supportedLanguages</p></td>
<td><p>字符串的集合</p></td>
<td><p>为应用程序的本地化语言的集合。</p></td>
</tr>
<tr class="even">
<td><p>publisherId</p></td>
<td><p>string</p></td>
<td><p>发布服务器标识符。</p></td>
</tr>
<tr class="odd">
<td><p>类别</p></td>
<td><p>string</p></td>
<td><p>应用程序类别。</p></td>
</tr>
<tr class="even">
<td><p>alternateIds</p></td>
<td><p>[AlternateIdentifier](#alternateidentifier)的集合</p></td>
<td><p>标识符可以用来实例化该上联机的应用程序的安装。</p></td>
</tr>
<tr class="odd">
<td><p>packageFamilyName</p></td>
<td><p>string</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>supportedPlatforms</p></td>
<td><p>[ProductPlatform](#productplatform)的集合</p></td>
<td></td>
</tr>
</tbody>
</table>

 

## <a name="productkey"></a>产品密钥


指定产品密钥的属性。

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>名称</th>
<th>类型</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>产品 id</p></td>
<td><p>string</p></td>
<td><p>通过存储用于业务应用程序的产品标识符。</p></td>
</tr>
<tr class="even">
<td><p>skuId</p></td>
<td><p>string</p></td>
<td><p>指定应用程序的特定 SKU 的产品标识符。</p></td>
</tr>
</tbody>
</table>

 

## <a name="productimage"></a>ProductImage


指定的产品图像的属性。

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>名称</th>
<th>类型</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>位置</p></td>
<td><p>URI</p></td>
<td><p>下载图像的位置。</p></td>
</tr>
<tr class="even">
<td><p>目的</p></td>
<td><p>string</p></td>
<td><p>应用程序的屏幕抓图和图标</p></td>
</tr>
<tr class="odd">
<td><p>height</p></td>
<td><p>string</p></td>
<td><p>以像素为单位的图像的高度。</p></td>
</tr>
<tr class="even">
<td><p>width</p></td>
<td><p>string</p></td>
<td><p>以像素为单位的图像的宽度。</p></td>
</tr>
<tr class="odd">
<td><p>标题</p></td>
<td><p>string</p></td>
<td><p>无限</p></td>
</tr>
<tr class="even">
<td><p>背景</p></td>
<td><p>string</p></td>
<td><p>#RRGGBB 格式</p></td>
</tr>
<tr class="odd">
<td><p>foregroundColor</p></td>
<td><p>string</p></td>
<td><p>#RRGGBB 格式</p></td>
</tr>
<tr class="even">
<td><p>文件大小</p></td>
<td><p>long</p></td>
<td><p>文件的大小。</p></td>
</tr>
</tbody>
</table>

 

## <a name="publisherdetails"></a>PublisherDetails


指定发布服务器的详细信息的属性。

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>名称</th>
<th>类型</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>publisherName</p></td>
<td><p>string</p></td>
<td><p>发布服务器的名称。</p></td>
</tr>
<tr class="even">
<td><p>publisherWebsite</p></td>
<td><p>string</p></td>
<td><p>发布者的网站。</p></td>
</tr>
</tbody>
</table>

 

## <a name="productpackagedetails"></a>ProductPackageDetails


<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>名称</th>
<th>类型</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>frameworkDependencyPackages</p></td>
<td><p>[FrameworkPackageDetails](#frameworkpackagedetails)的集合</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>contentId</p></td>
<td><p>string</p></td>
<td><p>标识一个特定的应用程序。</p></td>
</tr>
<tr class="odd">
<td><p>packageId</p></td>
<td><p>string</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>位置</p></td>
<td><p>[PackageLocation](#packagelocation)</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>packageFullName</p></td>
<td><p>string</p></td>
<td><p>示例中 Microsoft.BingTranslator_1.1.10917.2059_x86__8wekyb3d8bbwe</p></td>
</tr>
<tr class="even">
<td><p>packageIdentityName</p></td>
<td><p>string</p></td>
<td><p>示例中 Microsoft.BingTranslator</p></td>
</tr>
<tr class="odd">
<td><p>体系结构</p></td>
<td><p>[ProductArchitectures](#productarchitectures)的集合</p></td>
<td><p>值 {x86，x 64，配置，中性}</p></td>
</tr>
<tr class="even">
<td><p>packageFormat</p></td>
<td><p>[ProductPackageFormat](#productpackageformat)</p></td>
<td><p>约，appxbundle xap</p></td>
</tr>
<tr class="odd">
<td><p>平台</p></td>
<td><p>[ProductPlatform](#productplatform)的集合</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>packageId</p></td>
<td><p>string</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>文件大小</p></td>
<td><p>整数 64</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>packageRank</p></td>
<td><p>整数 32</p></td>
<td><p>可选</p></td>
</tr>
</tbody>
</table>

 

## <a name="productpackageset"></a>ProductPackageSet


<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>名称</th>
<th>类型</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>packageSetId</p></td>
<td><p>string</p></td>
<td><p>应用程序包的特定组合标识符。</p></td>
</tr>
<tr class="even">
<td><p>productPackages</p></td>
<td><p>[ProductPackageDetails](#productpackagedetails)的集合</p></td>
<td><p>应用程序软件包的集合。</p></td>
</tr>
</tbody>
</table>

 

## <a name="productpackageformat"></a>ProductPackageFormat


<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th>名称</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>约</p></td>
</tr>
<tr class="even">
<td><p>appxBundle</p></td>
</tr>
<tr class="odd">
<td><p>xap</p></td>
</tr>
</tbody>
</table>

 

## <a name="productplatform"></a>ProductPlatform


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>名称</th>
<th>类型</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>platformName</p></td>
<td><p>string</p></td>
</tr>
<tr class="even">
<td><p>minVersion</p></td>
<td><p>[VersionInfo](#versioninfo)</p></td>
</tr>
<tr class="odd">
<td><p>maxTestedVersion</p></td>
<td><p>[VersionInfo](#versioninfo)</p></td>
</tr>
</tbody>
</table>

 

## <a name="seataction"></a>SeatAction


<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th>名称</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>将指定</p></td>
</tr>
<tr class="even">
<td><p>回收</p></td>
</tr>
</tbody>
</table>

 

## <a name="seatdetails"></a>SeatDetails


<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>名称</th>
<th>类型</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>分配给</p></td>
<td><p>string</p></td>
<td><p>格式 = UPN(user@domain)</p></td>
</tr>
<tr class="even">
<td><p>dateAssigned</p></td>
<td><p>日期时间</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>状态</p></td>
<td><p>[SeatState](#seatstate)</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>产品密钥</p></td>
<td><p>[产品密钥](#productkey)</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

 

## <a name="seatdetailsresultset"></a>SeatDetailsResultSet


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>名称</th>
<th>类型</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>座位</p></td>
<td><p>[SeatDetails](#seatdetails)的集合</p></td>
</tr>
<tr class="even">
<td><p>continuationToken</p></td>
<td><p>string</p></td>
</tr>
</tbody>
</table>

 

## <a name="seatstate"></a>SeatState


<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th>名称</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>活动</p></td>
</tr>
<tr class="even">
<td><p>被吊销</p></td>
</tr>
</tbody>
</table>

 

## <a name="supportedproductplatform"></a>SupportedProductPlatform


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>名称</th>
<th>类型</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>platformName</p></td>
<td><p>string</p></td>
</tr>
<tr class="even">
<td><p>minVersion</p></td>
<td><p>[VersionInfo](#versioninfo)</p></td>
</tr>
<tr class="odd">
<td><p>maxTestedVersion</p></td>
<td><p>[VersionInfo](#versioninfo)</p></td>
</tr>
<tr class="even">
<td><p>体系结构</p></td>
<td><p>ProductArchitectures 的集合</p></td>
</tr>
</tbody>
</table>

 

## <a name="versioninfo"></a>VersionInfo


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>名称</th>
<th>类型</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>主要</p></td>
<td><p>整数-23</p></td>
</tr>
<tr class="even">
<td><p>次要</p></td>
<td><p>整数-23</p></td>
</tr>
<tr class="odd">
<td><p>生成</p></td>
<td><p>整数-23</p></td>
</tr>
<tr class="even">
<td><p>修订</p></td>
<td><p>整数-23</p></td>
</tr>
</tbody>
</table>

 

 






