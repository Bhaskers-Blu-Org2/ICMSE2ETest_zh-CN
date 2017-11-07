---
title: "获取清单"
description: "从企业来确定新的或更新的应用程序是否有可用的 Windows 应用商店，获取库存操作检索信息。"
MS-HAID:
- p\_phdevicemgmt.get\_seatblock
- p\_phDeviceMgmt.get\_inventory
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: C5485722-FC49-4358-A097-74169B204E74
ms.openlocfilehash: b6624774acef1280b500991d7b1cfc79081d99f8
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="get-inventory"></a>获取清单

从企业来确定新的或更新的应用程序是否有可用的 Windows 应用商店，**获取库存**操作检索信息。

## <a name="request"></a>请求

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>方法</th>
<th>请求的 URI</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>获取</p></td>
<td><p>{ContinuationToken} https://bspmts.mp.microsoft.com/V1/Inventory?continuationToken=&amp;modifiedSince = {ModifiedSince}&amp;licenseTypes = {LicenseType}&amp;maxResults = {MaxResults}</p></td>
</tr>
</tbody>
</table>


 

### <a name="uri-parameters"></a>URI 参数

可以请求 URI 中指定以下参数。

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>参数</th>
<th>类型</th>
<th>默认值</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>continuationToken</p></td>
<td><p>string</p></td>
<td><p>Null</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>modifiedSince</p></td>
<td><p>日期时间</p></td>
<td><p>Null</p></td>
<td><p>可选项。 用于确定自特定日期以来的更改。</p></td>
</tr>
<tr class="odd">
<td><p>licenseTypes</p></td>
<td><p>[LicenseType](data-structures-windows-store-for-business.md#licensetype)的集合</p></td>
<td><p>{在线、 离线}</p></td>
<td><p>可选项。 许可证类型的集合</p></td>
</tr>
<tr class="even">
<td><p>maxResults</p></td>
<td><p>整数 32</p></td>
<td><p>25</p></td>
<td><p>可选项。 指定应用程序在单个查询中返回的最大数目。</p></td>
</tr>
</tbody>
</table>




下面是一些示例。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>查询类型</th>
<th>示例查询</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>在线和离线</p></td>
<td><p>https:<span></span>//bspmts.mp.microsoft.com/V1/Inventory?licenseTypes=online&amp;licenseTypes 脱机 =&amp;maxResults = 25</p></td>
</tr>
<tr class="even">
<td><p>仅联机</p></td>
<td><p>https:<span></span>//bspmts.mp.microsoft.com/V1/Inventory?licenseTypes=online&amp;maxResults = 25</p></td>
</tr>
<tr class="odd">
<td><p>仅脱机时</p></td>
<td><p>https:<span></span>//bspmts.mp.microsoft.com/V1/Inventory?licenseTypes=offline&amp;maxResults = 25</p></td>
</tr>
<tr class="even">
<td><p>许可证类型和时间筛选器</p></td>
<td><p>https:<span></span>//bspmts.mp.microsoft.com/V1/Inventory?modifiedSince=2015-07-13T14%3a02%3a25.6863382-07%3a00&amp;licenseTypes 在线 =&amp;licenseTypes 脱机 =&amp;maxResults = 25</p></td>
</tr>
</tbody>
</table>




<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>错误代码</th>
<th>说明</th>
<th>重试</th>
<th>数据字段</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>400</p></td>
<td><p>无效的参数</p></td>
<td><p>否</p></td>
<td><p>参数名称</p>
<p>无效的修改日期、 许可证、 或 continuationToken</p>
<p>详细信息︰ 字符串</p></td>
</tr>
</tbody>
</table>




## <a name="response"></a>响应

### <a name="response-body"></a>响应正文

该响应包含[InventoryResultSet](data-structures-windows-store-for-business.md#inventoryresultset)。

 






