---
title: "CellularSettings 的 CSP"
description: "CellularSettings 的 CSP"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: ce8b6f16-37ca-4aaf-98b0-306d12e326df
ms.openlocfilehash: 6e049d70a9540916dac3689ccf423e1e00e6757f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="cellularsettings-csp"></a>CellularSettings 的 CSP


CellularSettings 配置服务提供程序用于在移动设备上配置手机设置。

下图显示树状格式由开放手机联盟客户端资源调配 (OMA CP) CellularSettings 配置服务提供程序。 OMA DM 协议不支持此配置服务提供商。

![资源调配\-csp\-cellularsettings](images/provisioning-csp-cellularsettings.png)

<a href="" id="dataroam"></a>**DataRoam**  
可选项。 整数。 指定默认漫游值。 有效值包括︰

<table>
<colgroup>
<col width="20%" />
<col width="80%" />
</colgroup>
<thead>
<tr class="header">
<th>值</th>
<th>设置</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>0</p></td>
<td><p>不漫游</p></td>
</tr>
<tr class="even">
<td><p>1</p></td>
<td><p>不漫游 （或国内漫游，如果适用的话）</p></td>
</tr>
<tr class="odd">
<td><p>2</p></td>
<td><p>漫游</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[配置服务提供程序的引用](configuration-service-provider-reference.md)

 

 






