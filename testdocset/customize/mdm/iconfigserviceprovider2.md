---
title: IConfigServiceProvider2
description: IConfigServiceProvider2
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 8deec0fb-59a6-4d08-8ddb-6d0d3d868a10
ms.openlocfilehash: 93fdb533d5fa92f8ae3c31ae280a0f9179e00127
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="iconfigserviceprovider2"></a>IConfigServiceProvider2


Oem 需要，以实现此接口配置服务提供商每一次。 ConfigManager2 客户端使用此接口来实例化配置服务提供商，以常规状态信息传递给配置服务提供程序，并经常访问或创建节点。

下表显示了 Oem 必须实现此接口所定义的方法。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>方法</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[IConfigServiceProvider2::ConfigManagerNotification](iconfigserviceprovider2configmanagernotification.md)</p></td>
<td><p>允许将通知发送到配置服务提供程序的事件，如加载或卸载配置服务提供程序时，执行回滚时，和在节点上调用操作时的 ConfigManager2。</p></td>
</tr>
<tr class="even">
<td><p>[IConfigServiceProvider2::GetNode](iconfigserviceprovider2getnode.md)</p></td>
<td><p>基于路径相对于根节点的配置服务提供程序返回一个节点。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题

[创建自定义配置服务提供程序](create-a-custom-configuration-service-provider.md)

 






