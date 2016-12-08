---
title: "回收从用户的座位"
description: "从用户操作的回收座位返回 Windows 应用商店业务用户使用回收的点。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: E2C3C899-D0AD-469A-A319-31A420472A4C
ms.openlocfilehash: a087b900bd75fdb8c4679c7c9550c92f54845b02
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="reclaim-seat-from-user"></a>回收从用户的座位

**回收座位从用户**操作返回 Windows 应用商店业务用户使用回收的点。

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
<td><p>https://bspmts.mp.microsoft.com/V1/Inventory/ {产品 Id} / {skuId} /Seats/ {用户名}</p></td>
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
</tbody>
</table>

 
## <a name="response"></a>响应

### <a name="response-body"></a>响应正文

响应正文中包含[SeatDetails](data-structures-windows-store-for-business.md#seatdetails)。

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th>错误代码</th>
<th>说明</th>
<th>重试</th>
<th>数据字段</th>
<th>详细信息</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>400</p></td>
<td><p>无效的参数</p></td>
<td><p>否</p></td>
<td><p>参数名称</p>
<p>原因︰ 无效参数</p>
<p>详细信息︰ 字符串</p></td>
<td><p>无效的产品 Id、 skuId 或用户名可以包含</p></td>
</tr>
<tr class="even">
<td><p>404</p></td>
<td><p>找不到</p></td>
<td></td>
<td><p>项目类型︰ 库存，用户，座位</p>
<p>值︰ 产品 Id/SkuId，用户名，产品 Id/SkuId/用户名</p></td>
<td><p>项类型︰ 库存，用户，座位</p>
<p>值︰ 产品 Id/SkuId，用户名，产品 Id/SkuId/用户名</p></td>
</tr>
<tr class="odd">
<td><p>409</p></td>
<td><p>Conflict</p></td>
<td></td>
<td><p>原因︰ 未联机</p></td>
<td></td>
</tr>
</tbody>
</table>

 

 





