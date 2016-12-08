---
title: "获得席位"
description: "获取使用点操作检索活动座位在 Windows 应用商店业务有关的信息。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 32945788-47AC-4259-B616-F359D48F4F2F
ms.openlocfilehash: 6eb0c2d40da3a1f1fd277a91e6c696a07cef3259
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="get-seats"></a>获得席位

**获得席位**操作检索活动座位在 Windows 应用商店业务有关的信息。

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
<td><p>https://bspmts.mp.microsoft.com/V1/Inventory/ {产品 Id} / {skuId} / Seats?continuationToken = {ContinuationToken}&amp;maxResults = {MaxResults}</p></td>
</tr>
</tbody>
</table>

 
### <a name="uri-parameters"></a>URI 参数

可以请求 URI 中指定以下参数。

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>参数</th>
<th>类型</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>产品 id</p></td>
<td><p>string</p></td>
<td><p>必需。 通过存储用于业务应用程序的产品标识符。</p></td>
</tr>
<tr class="even">
<td><p>skuId</p></td>
<td><p>string</p></td>
<td><p>必需。 指定应用程序的特定 SKU 的产品标识符。</p></td>
</tr>
<tr class="odd">
<td><p>continuationToken</p></td>
<td><p>string</p></td>
<td><p>可选项。</p></td>
</tr>
<tr class="even">
<td><p>maxResults</p></td>
<td><p>int32</p></td>
<td><p>可选项。 默认值 = 25，最大值 = 100</p></td>
</tr>
</tbody>
</table>

 
## <a name="response"></a>响应

### <a name="response-body"></a>响应正文

响应正文中包含[SeatDetailsResultSet](data-structures-windows-store-for-business.md#seatdetailsresultset)。

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
<p>原因︰ 缺少参数或参数无效</p>
<p>详细信息︰ 字符串</p></td>
</tr>
<tr class="even">
<td><p>404</p></td>
<td><p>找不到</p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>409</p></td>
<td><p>Conflict</p></td>
<td></td>
<td><p>原因︰ 未联机</p></td>
</tr>
</tbody>
</table>

 

 





