---
title: "大容量分配和回收来自用户的座位"
description: "大容量分配和回收操作返回回收或分配座位在 Windows 应用商店业务用户的座位。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 99E2F37D-1FF3-4511-8969-19571656780A
ms.openlocfilehash: edfe6d2d8a2475789fedae09fb751943bc266833
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="bulk-assign-and-reclaim-seats-from-users"></a>大容量分配和回收来自用户的座位

**大容量分配和回收来自用户的座位**操作返回回收或分配座位在 Windows 应用商店的业务。

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
<td><p>发布</p></td>
<td><p>https:<span></span>//bspmts.mp.microsoft.com/V1/Inventory/{productId}/{skuId}/Seats</p></td>
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
<td><p>用户名</p></td>
<td><p>string</p></td>
<td><p>要求范围内 (UPN)。 目标用户帐户的用户名。</p></td>
</tr>
<tr class="even">
<td><p>seatAction</p></td>
<td><p>[SeatAction](data-structures-windows-store-for-business.md#seataction)</p></td>
<td></td>
</tr>
</tbody>
</table>

 
## <a name="response"></a>响应

### <a name="response-body"></a>响应正文

响应正文中包含[BulkSeatOperationResultSet](data-structures-windows-store-for-business.md#bulkseatoperationresultset)。

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
<td><p>404</p></td>
<td><p>找不到</p></td>
<td></td>
<td><p>项目类型︰ 库存</p>
<p>值︰ 产品 Id/SkuId</p></td>
</tr>
</tbody>
</table>

 

 





