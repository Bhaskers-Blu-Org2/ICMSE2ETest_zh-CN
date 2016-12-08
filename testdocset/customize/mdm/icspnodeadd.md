---
title: "添加 ICSPNode"
description: "添加 ICSPNode"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 5f03d350-c82b-4747-975f-385fd8b5b3a8
ms.openlocfilehash: ce7ed552315358a78d8b1ac111d8870b05092a4a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="icspnodeadd"></a>ICSPNode::Add

此方法将直接子节点添加到配置服务提供程序节点，并将指针返回到新的节点。

## <a name="syntax"></a>语法

``` syntax
HRESULT Add([in] IConfigManager2URI* pChildName,
            [in] CFG_DATATYPE DataType,
            [in] VARIANT varValue, 
            [in, out] ICSPNode** ppNewNode, 
            [in, out] DWORD* pgrfNodeOptions);
```

## <a name="parameters"></a>参数

<a href="" id="pchildname"></a>*pChildName*  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;要添加的子节点的名称。

<a href="" id="datatype"></a>*数据类型*  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;要添加的子节点的数据类型。 受支持的类型包括︰
-   CFG\_数据类型\_节点

-   CFG\_数据类型\_为空

-   CFG\_数据类型\_二进制

-   CFG\_数据类型\_整数

-   CFG\_数据类型\_字符串

-   CFG\_数据类型\_多个\_字符串

<a href="" id="varvalue"></a>*varValue*  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;要添加的子节点的值。

<a href="" id="ppnewnode"></a>*ppNewNode*  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;要返回的新子节点。

<a href="" id="pgrfnodeoptions"></a>*pgrfNodeOptions*  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;在新的子节点上支持的功能。
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
<td style="vertical-align:top"><p><code>CSPNODE_OPTION_NATIVESECURITY</code></p></td>
<td style="vertical-align:top"><p>0x01</p></td>
<td style="vertical-align:top"><p>本机的安全选项表示节点处理其自身安全检查，ConfigManager2 不需要管理此节点的安全性。</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p><code>CSPNODE_OPTION_INTERNALTRANSACTION</code></p></td>
<td style="vertical-align:top"><p>0x02</p></td>
<td style="vertical-align:top"><p>内部事务选项告诉 ConfigManager2 配置服务提供程序处理事务 （回滚和承诺） 的节点。 若要处理内部事务，该节点必须实现[ICSPNodeTransactioning](icspnodetransactioning.md)。</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p><code>CSPNODE_OPTION_HANDLEALLPROPERTIES</code></p></td>
<td style="vertical-align:top"><p>0x04</p></td>
<td style="vertical-align:top"><p>未使用。</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p><code>CSPNODE_OPTION_SECRETDATA</code></p></td>
<td style="vertical-align:top"><p>0x08</p></td>
<td style="vertical-align:top"><p>未使用。</p></td>
</tr>
</tbody>
</table>

 
## <a name="return-value"></a>返回值

此方法返回 ICSPNode 和子节点上支持的功能选项。 该方法返回空值，如果调用时出错，若要获取错误值。

S 的值\_确定指示成功找到了一个节点。 CMN\_E\_已\_存在表示子节点具有相同的名称已经存在。 CFGMGR\_E\_COMMANDNOTALLOWED 表示此节点不支持**Add**方法。

## <a name="remarks"></a>备注

对于外部事务 – 节点，如果实现此方法时，则[ICSPNode::Clear](icspnodeclear.md)和[ICSPNode::DeleteChild](icspnodedeletechild.md)必须同时实现或回滚将失败。

## <a name="requirements"></a>要求

**标头︰**无

## <a name="related-topics"></a>相关的主题

[创建自定义配置服务提供程序](create-a-custom-configuration-service-provider.md)

 






