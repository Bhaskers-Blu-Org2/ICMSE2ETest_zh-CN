---
title: "ICSPNode 副本"
description: "ICSPNode 副本"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: cd5ce0bc-a08b-4f82-802d-c7ff8701b41f
ms.openlocfilehash: aa3dca9dbd9f50b6d701dbcf9cac46ac9005787f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="icspnodecopy"></a>ICSPNode::Copy

此方法在指定的路径中配置服务提供程序创建当前节点的副本。 如果存在目标节点，它应该被覆盖。

## <a name="syntax"></a>语法

``` syntax
HRESULT Copy([in] IConfigManager2URI* puriDestination,
             [in, out] ICSPNode** ppNewNode, 
             [in, out] DWORD* pgrfNodeOptions);
```

## <a name="parameters"></a>参数

<a href="" id="puridestination"></a>*puriDestination*  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;路径和新节点的位置，相对于配置服务提供程序的根节点的名称。

<a href="" id="ppnewnode"></a>*ppNewNode*  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;复制操作所创建的新节点。

<a href="" id="pgrfnodeoptions"></a>*pgrfNodeOptions*  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;在新节点上支持的功能。

<table style="margin-left:26px">
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>功能名称</th>
<th>一位的值 （以十六进制表示）</th>
<th>注释</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><code>CSPNODE_OPTION_NATIVESECURITY</code></p></td>
<td><p>0x01</p></td>
<td><p>本机的安全选项表示节点处理其自身安全检查，ConfigManager2 不需要管理此节点的安全性。</p></td>
</tr>
<tr class="even">
<td><p><code>CSPNODE_OPTION_INTERNALTRANSACTION</code></p></td>
<td><p>0x02</p></td>
<td><p>内部事务选项告诉 ConfigManager2 配置服务提供程序处理事务 （回滚和承诺） 的节点。 若要处理内部事务，该节点必须实现[ICSPNodeTransactioning](icspnodetransactioning.md)。</p></td>
</tr>
<tr class="odd">
<td><p><code>CSPNODE_OPTION_HANDLEALLPROPERTIES</code></p></td>
<td><p>0x04</p></td>
<td><p>未使用。</p></td>
</tr>
<tr class="even">
<td><p><code>CSPNODE_OPTION_SECRETDATA</code></p></td>
<td><p>0x08</p></td>
<td><p>未使用。</p></td>
</tr>
</tbody>
</table>

 
## <a name="return-value"></a>返回值

S 的值\_确定指示该节点已成功复制到新的位置。 CFGMGR\_E\_COMMANDNOTALLOWED 表示此节点不支持**复制**方法。

## <a name="remarks"></a>备注

对于外部事务 – 节点，如果实现此方法时，则[ICSPNode::Add](icspnodeadd.md)、 [ICSPNode::SetValue](icspnodesetvalue.md)、 [ICSPNode::Clear](icspnodeclear.md)和[ICSPNode::DeleteChild](icspnodedeletechild.md)必须同时实现或回滚将失败。

## <a name="requirements"></a>要求

**标头︰**无

## <a name="related-topics"></a>相关的主题

[创建自定义配置服务提供程序](create-a-custom-configuration-service-provider.md)






