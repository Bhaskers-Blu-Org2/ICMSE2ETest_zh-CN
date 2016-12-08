---
title: "ICSPNode 移动"
description: "ICSPNode 移动"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: efb359c3-5c86-4975-bf6f-a1c33922442a
ms.openlocfilehash: 247f8e876dbfd347c197ba8c9f3a980f0213eb38
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="icspnodemove"></a>ICSPNode::Move

此方法将节点移到配置服务提供程序中的新位置。 如果目标节点已经存在，它应该被覆盖。

## <a name="syntax"></a>语法

``` syntax
HRESULT Move([in] IConfigManager2URI* puriDestination);
```

## <a name="parameters"></a>参数

<a href="" id="puridestination"></a>*puriDestination*  
<p style="margin-left: 25px">路径和名称的节点的新位置，相对于配置服务提供程序的根节点。</p>

## <a name="return-value"></a>返回值

S 的值\_确定指示该节点已成功移动。 CFGMGR\_E\_COMMANDNOTALLOWED 表示此节点不支持**ICSP::Move**方法。

## <a name="remarks"></a>备注

对于外部事务 – 节点，如果实现此方法时，则[ICSPNode::Add](icspnodeadd.md)和[ICSPNode::SetValue](icspnodesetvalue.md)必须同时实现或回滚将失败。

## <a name="requirements"></a>要求

**标头︰**无

## <a name="related-topics"></a>相关的主题

[创建自定义配置服务提供程序](create-a-custom-configuration-service-provider.md)

 






