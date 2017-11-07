---
title: ICSPNode
description: ICSPNode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 023466e6-a8ab-48ad-8548-291409686ac2
ms.openlocfilehash: 017c74b93528f5efa5e29b9f5d48ccb04d38cca2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="icspnode"></a>ICSPNode

此接口完成大部分配置服务提供程序中的工作。 配置服务提供程序树中的每个节点都表示此接口的不同实现。 ConfigManager2 客户端的操作通常被转换为 ICSPNode 的实例的调用。

这样，如果他们失败，在方法结束该节点的状态与状态匹配之前调用该方法时，必须实现这些方法。

一些节点将不能执行某些操作，并且可以返回 CFGMGR\_E\_COMMANDNOTALLOWED 的那些方法。 对于每个方法所实现的外部事务 – 节点，相反的方法必须还实现，通过[设计一个自定义配置服务提供程序](design-a-custom-windows-csp.md)中的"确定节点操作"的定义。

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
<td><p>[ICSPNode::Add](icspnodeadd.md)</p></td>
<td><p>添加到配置服务提供程序节点的直接子并返回一个指向新的子节点。</p></td>
</tr>
<tr class="even">
<td><p>[ICSPNode::Clear](icspnodeclear.md)</p></td>
<td><p>删除的内容和当前配置服务提供程序节点的子级。 在[ICSPNode::DeleteChild](icspnodedeletechild.md)之前调用。</p></td>
</tr>
<tr class="odd">
<td><p>[ICSPNode::Copy](icspnodecopy.md)</p></td>
<td><p>在中配置服务提供程序指定的路径创建当前节点的副本。 如果存在目标节点，它应该被覆盖。</p></td>
</tr>
<tr class="even">
<td><p>[ICSPNode::DeleteChild](icspnodedeletechild.md)</p></td>
<td><p>从配置服务提供程序节点中删除指定的子节点。</p></td>
</tr>
<tr class="odd">
<td><p>[ICSPNode::DeleteProperty](icspnodedeleteproperty.md)</p></td>
<td><p>从配置服务提供程序节点中删除一个属性。</p></td>
</tr>
<tr class="even">
<td><p>[ICSPNode::Execute](icspnodeexecute.md)</p></td>
<td><p>通过在指定的用户数据传递和返回结果内部事务配置服务提供程序节点上运行任务。</p></td>
</tr>
<tr class="odd">
<td><p>[ICSPNode::GetChildNodeNames](icspnodegetchildnodenames.md)</p></td>
<td><p>返回配置服务提供程序节点的子级的列表。</p></td>
</tr>
<tr class="even">
<td><p>[ICSPNode::GetProperty](icspnodegetproperty.md)</p></td>
<td><p>从配置服务提供程序节点返回的属性值。</p></td>
</tr>
<tr class="odd">
<td><p>[ICSPNode::GetPropertyIdentifiers](icspnodegetpropertyidentifiers.md)</p></td>
<td><p>返回的节点支持的非标准属性的列表。 返回的数组必须分配与<code>CoTaskMemAlloc</code>。</p></td>
</tr>
<tr class="even">
<td><p>[ICSPNode::GetValue](icspnodegetvalue.md)</p></td>
<td><p>获取节点的值和数据类型。 内部 （非叶） 的节点可能没有值。</p></td>
</tr>
<tr class="odd">
<td><p>[ICSPNode::Move](icspnodemove.md)</p></td>
<td><p>将此节点移动到配置服务提供程序中的新位置。 如果目标节点已经存在，它应该被覆盖。</p></td>
</tr>
<tr class="even">
<td><p>[ICSPNode::SetProperty](icspnodesetproperty.md)</p></td>
<td><p>设置用于配置服务提供程序节点的属性值。</p></td>
</tr>
<tr class="odd">
<td><p>[ICSPNode::SetValue](icspnodesetvalue.md)</p></td>
<td><p>设置配置服务提供程序节点的值。 它是错误试图设置内部节点的值。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题

[创建自定义配置服务提供程序](create-a-custom-configuration-service-provider.md)

 






