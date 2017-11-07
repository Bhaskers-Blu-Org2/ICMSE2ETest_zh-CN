---
title: "获取本地化的产品详细信息"
description: "获取本地化产品详细信息操作检索 Windows 应用商店业务的产品的本地化信息。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: EF6AFCA9-8699-46C9-A3BB-CD2750C07901
ms.openlocfilehash: 0618f220c2381f1ed42be3da5cc0a5484bde23b8
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="get-localized-product-details"></a>获取本地化的产品详细信息

**获取本地化产品详细信息**操作 Windows 应用商店业务从中检索一种产品的本地化信息。

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
<td><p>https://bspmts.mp.microsoft.com/V1/Products/ {产品 Id} / {SkuId} /LocalizedDetails/ {语言中}</p></td>
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
<td><p>language</p></td>
<td><p>string</p></td>
<td><p>必需。 如 en ISO 格式语言-我们，en ca。</p></td>
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
<p>原因︰ 缺少参数或参数无效</p>
<p>详细信息︰ 字符串</p></td>
</tr>
<tr class="even">
<td><p>404</p></td>
<td><p>找不到</p></td>
<td></td>
<td><p>项目类型: 产品 Id skuId，语言</p></td>
</tr>
</tbody>
</table>

 

## <a name="response"></a>响应

该响应包含[LocalizedProductDetail](data-structures-windows-store-for-business.md#localizedproductdetail)。

 






