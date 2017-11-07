---
title: "ICSPNode 清除"
description: "ICSPNode 清除"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: b414498b-110a-472d-95c0-2d5b38cd78a6
ms.openlocfilehash: e23b2e078c131a070238f862ac426ce80e76cafd
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="icspnodeclear"></a>ICSPNode::Clear

此方法将删除的内容和配置服务提供程序在当前节点的子节点。 之前在父节点上调用[ICSPNode::DeleteChild](icspnodedeletechild.md) ，始终是在子节点上调用此方法。


## <a name="syntax"></a>语法

``` syntax
HRESULT Clear();
```


## <a name="return-value"></a>返回值

S 的值\_确定指示该节点已被成功清除。 CFGMGR\_E\_COMMANDNOTALLOWED 表示此节点不支持**清除**方法。


## <a name="remarks"></a>备注

对于外部事务 – 节点，如果实现此方法时，则[ICSPNode::SetValue](icspnodesetvalue.md)和[ICSPNode::SetProperty](icspnodesetproperty.md)必须同时实现或回滚将失败。

在调用之前**清除**在目标节点上，ConfigManager2 尝试收集的当前状态的节点;父节点不需要保留其子节点的状态，如果这些外部事务。

## <a name="requirements"></a>要求

**标头︰**无


## <a name="related-topics"></a>相关的主题

[创建自定义配置服务提供程序](create-a-custom-configuration-service-provider.md)

 





