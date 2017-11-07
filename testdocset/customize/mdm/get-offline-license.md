---
title: "获取脱机许可证"
description: "获取脱机许可操作从 Windows 应用商店业务检索脱机许可证信息的产品。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 08DAD813-CF4D-42D6-A783-994A03AEE051
ms.openlocfilehash: 80773fece46c5ccfc8219e8aaa3c5d70d8bce6a5
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="get-offline-license"></a>获取脱机许可证

**获取许可证脱机**操作从 Windows 应用商店业务检索脱机许可证信息的产品。

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
<td><p>https://bspmts.mp.microsoft.com/V1/Products/ {产品 Id} / {skuId} /OfflineLicense/ {contentId}</p></td>
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
<td><p>必需。 标识特定产品已获得。</p></td>
</tr>
<tr class="even">
<td><p>skuId</p></td>
<td><p>string</p></td>
<td><p>必需。 SKU 标识符中。</p></td>
</tr>
<tr class="odd">
<td><p>contentId</p></td>
<td><p>string</p></td>
<td><p>必需。 标识一个特定的应用程序。</p></td>
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
<td></td>
</tr>
<tr class="odd">
<td><p>409</p></td>
<td><p>Conflict</p></td>
<td></td>
<td><p>原因︰ 不归其所有，没有离线</p></td>
</tr>
</tbody>
</table>


## <a name="response"></a>响应

### <a name="response-body"></a>响应正文

该响应包含[OfflineLicense](data-structures-windows-store-for-business.md#offlinelicense)。

 






