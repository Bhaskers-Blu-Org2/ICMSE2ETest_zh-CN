---
title: "获取产品包"
description: "获取产品包操作检索有关特定应用程序在 Windows 应用商店业务有关的信息。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 4314C65E-6DDC-405C-A591-D66F799A341F
ms.openlocfilehash: 2ddc282b8aa3c6445f40c2325c9914d0e8be6096
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="get-product-package"></a>获取产品包

**获取产品包**操作检索有关特定应用程序在 Windows 应用商店业务有关的信息。

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
<td><p>https://bspmts.mp.microsoft.com/V1/Products/ {产品 Id} / {skuId} /Packages/ {packageId}</p></td>
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
<td><p>packageId</p></td>
<td><p>string</p></td>
<td><p>必需。</p></td>
</tr>
</tbody>
</table>
   

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
<td><p>可以为产品 Id、 skuId 或 packageId</p></td>
</tr>
<tr class="even">
<td><p>404</p></td>
<td><p>找不到</p></td>
<td></td>
<td></td>
<td><p>项目类型︰ 产品/SKU</p></td>
</tr>
<tr class="odd">
<td><p>409</p></td>
<td><p>Conflict</p></td>
<td></td>
<td><p>原因︰ 不负责</p></td>
<td></td>
</tr>
</tbody>
</table>


## <a name="response"></a>响应

### <a name="response-body"></a>响应正文

响应正文中包含[ProductPackageDetails](data-structures-windows-store-for-business.md#productpackagedetails)。

 






