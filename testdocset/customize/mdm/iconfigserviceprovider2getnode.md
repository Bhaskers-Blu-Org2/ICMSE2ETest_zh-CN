---
title: IConfigServiceProvider2 GetNode
description: IConfigServiceProvider2 GetNode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 4dc10a59-f6a2-45c0-927c-d594afc9bb91
ms.openlocfilehash: 87f4d1aaf000229f7fb3196925ad611a1afd8a78
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="iconfigserviceprovider2getnode"></a>IConfigServiceProvider2::GetNode


基于传递路径的配置服务提供程序，此方法返回一个节点。 返回的节点为根节点的后代。

## <a name="syntax"></a>语法


``` syntax
HRESULT GetNode([in] IConfigManager2URI* pURI, 
                [out] ICSPNode** ppNode,
                [in, out] DWORD* pgrfNodeOptions);
```

## <a name="parameters"></a>参数

<a href="" id="puri"></a>*pUri*
<ul style="list-style-type:none">
<li>
相对于根节点的子节点的 URI。 例如，若要访问"./Vendor/Contoso/SampleCSP/ContainerA/UserName"节点，ConfigManager2 调用配置服务提供商`GetNode`方法，并传入 IConfigManager2URI 实例表示的 URI"ContainerA/SampleCSP/用户名"。
</li>
</ul>
<br>
<a href="" id="ppnode"></a>*ppNode*
<ul style="list-style-type:none">
<li>
如果查询成功，这将返回*pUri*位置处的 ICSPNode 实例配置服务提供商的树中。
</li>
</ul>
<br>
<a href="" id="pgrfnodeoptions"></a>*pgrfNodeOptions*
<ul style="list-style-type:none">
<li>
节点支持以下功能。

<table>
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
</li>
</ul>
<br>

## <a name="return-value"></a>返回值

此方法返回 ICSPNode。 如果该函数返回 null，调用时出错，若要获取错误值。

S 的值\_确定指示成功找到了一个节点。 CFGMGR\_E\_NODENOTFOUND 表示该节点不存在。 请注意，这可能是正常的如可选的节点的情况。

## <a name="requirements"></a>要求

**标头︰**无

 






