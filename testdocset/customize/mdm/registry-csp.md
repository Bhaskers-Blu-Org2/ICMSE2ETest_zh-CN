---
title: "注册表的 CSP"
description: "注册表的 CSP"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 2307e3fd-7b61-4f00-94e1-a639571f2c9d
ms.openlocfilehash: f28cd427bd5c747378a04301a63bdbb27e3811a4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="registry-csp"></a>注册表的 CSP


注册表配置服务提供程序用于更新注册表设置。 但是，如果配置服务提供程序所特有的需要更新的设置，使用特定的配置服务提供程序。

>  **请注意**  注册表 CSP 是只支持 Windows 10 移动用于 OEM 配置。 请不要将该 CSP 用于企业远程管理。
仅 Windows 10 移动式，此配置服务提供商要求使用 ID\_CAP\_CSP\_基础和 ID\_CAP\_CSP\_OEM 功能从网络配置应用程序进行访问。

 

对于注册表的 CSP，不能使用替换命令，除非该节点已存在。

注册表配置服务提供程序可对 OMA 客户机的资源调配和 OMA DM 协议进行管理。 当使用 OMA DM 添加注册表项，则还必须将子注册表值添加 XML 代码中。

OMA 客户端资源调配，适用如下说明︰

-   不允许查询注册表中的最高级别。 所有参数必须分别进行都查询。 注册表的基础数据存储区的类型。 一定要使用的**数据类型**属性*&lt;参数&gt;*标记。

-   本文档描述的默认特性。 可以添加额外的特征。

-   因为**注册表**配置服务提供程序使用反斜杠 (\)为必须转义键名，注册表项的名称出现的反斜杠之间的分隔符字符。 可以通过使用两个连续的反斜杠转义反斜杠 (\\\)。

默认安全角色映射到每个节点，除非子节点授予的特定权限。 子节点的安全角色是实现特定的并通过 Oem 和移动运营商可以更改。

## <a name="microsoft-custom-elements"></a>Microsoft 的自定义元素


下表显示了此配置服务提供程序支持 OMA 客户端资源调配的 Microsoft 自定义元素。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>元素</th>
<th>可用</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>参数查询</p></td>
<td><p>是</p></td>
</tr>
<tr class="even">
<td><p>noparm</p></td>
<td><p>是</p></td>
</tr>
<tr class="odd">
<td><p>nocharacteristic</p></td>
<td><p>是</p></td>
</tr>
<tr class="even">
<td><p>特征查询</p></td>
<td><p>是</p>
<p>递归查询︰ 是</p>
<p>顶级查询︰ 否</p></td>
</tr>
</tbody>
</table>

 

使用这些元素来生成标准资源调配 OMA 客户端配置 XML。 有关特定元素的信息，请参阅 MSPROV DTD 元素。

## <a name="supported-data-types"></a>支持的数据类型


下表显示了此配置服务提供程序支持的数据类型。

<table>
<colgroup>
<col width="15%" />
<col width="15%" />
<col width="70%" />
</colgroup>
<thead>
<tr class="header">
<th>XML 数据类型</th>
<th>本地注册表类型</th>
<th>XML 格式</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>integer</p></td>
<td><p>REG_DWORD</p></td>
<td><p>整数。 此参数的查询返回一个整数类型。</p></td>
</tr>
<tr class="even">
<td><p>布尔</p></td>
<td><p>REG_DWORD</p></td>
<td><p>1 或 0 的整数值。 此参数的查询返回一个整数类型。</p></td>
</tr>
<tr class="odd">
<td><p>float</p></td>
<td><p>REG_SZ</p></td>
<td><p>浮点型。 此参数的查询返回一个字符串类型。</p></td>
</tr>
<tr class="even">
<td><p>string</p></td>
<td><p>REG_SZ</p></td>
<td><p>字符串。 此参数的查询返回一个字符串类型。</p></td>
</tr>
<tr class="odd">
<td><p>multiplestring</p></td>
<td><p>REG_MULTI_SZ</p></td>
<td><p>由多个字符串分隔<strong>&amp;#xF000;</strong>和已结束，但两个<strong>&amp;#xF000;</strong> -此参数查询会返回名类型。</p></td>
</tr>
<tr class="even">
<td><p>二进制文件</p></td>
<td><p>REG_BINARY</p></td>
<td><p>Base64 编码。 此参数的查询返回的二进制类型。</p></td>
</tr>
<tr class="odd">
<td><p>时间</p></td>
<td><p>在 REG_BINARY FILETIME</p></td>
<td><p>时间格式符合 ISO8601 标准，使用可选的日期部分。 如果省略日期部分，则省略&quot;T&quot;分隔符。 此参数的查询返回的二进制类型。</p></td>
</tr>
<tr class="even">
<td><p>date</p></td>
<td><p>在 REG_BINARY FILETIME</p></td>
<td><p>日期格式符合 ISO8601 标准，使用可选的时间部分。 如果省略时间部分，则省略&quot;T&quot;分隔符。 此参数的查询返回的二进制类型。</p></td>
</tr>
</tbody>
</table>

 

不能访问当前路径下嵌套使用注册表配置服务提供程序的注册表项。 相反，该子项的值必须单独访问通过一个新的特征。

## <a name="related-topics"></a>相关的主题


[配置服务提供程序的引用](configuration-service-provider-reference.md)

 

 






