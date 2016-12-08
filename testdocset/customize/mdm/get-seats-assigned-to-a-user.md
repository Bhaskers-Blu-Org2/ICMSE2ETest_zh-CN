---
title: "获取分配给用户的座位"
description: "获得席位分配给一个用户操作检索分配座位在 Windows 应用商店业务的有关信息。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: CB963E44-8C7C-46F9-A979-89BBB376172B
ms.openlocfilehash: 509b6b1dda68464ff1b5d4c17ae96e1a5ada1b3e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="get-seats-assigned-to-a-user"></a>获取分配给用户的座位

**获得席位分配给用户**操作检索分配座位在 Windows 应用商店业务的有关信息。

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
<td><p>https:<span></span>/ / bspmts.mp.microsoft.com/V1/Users/{username}/Seats?continuationToken={ContinuationToken}&amp;maxResults = {MaxResults}</p></td>
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
<td><p>用户名</p></td>
<td><p>string</p></td>
<td><p>要求范围内 (UPN)。 目标用户帐户的用户名。</p></td>
</tr>
<tr class="even">
<td><p>continuationToken</p></td>
<td><p>string</p></td>
<td><p>可选项。</p></td>
</tr>
<tr class="odd">
<td><p>maxResults</p></td>
<td><p>inteter-32</p></td>
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
<p>原因︰ 无效参数</p>
<p>详细信息︰ 字符串</p></td>
</tr>
<tr class="even">
<td><p>404</p></td>
<td><p>找不到</p></td>
<td></td>
<td><p>项目类型︰ 用户</p>
<p>值︰ 用户名</p></td>
</tr>
</tbody>
</table>

 

 





