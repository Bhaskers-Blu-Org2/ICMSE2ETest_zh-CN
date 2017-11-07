---
title: ICSPNode DeleteChild
description: ICSPNode DeleteChild
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 8cf3663d-a4cf-4d11-b03a-f1d096ad7f9c
ms.openlocfilehash: 20b4c2719c35638256aa2ba69259e5ed6bdca338
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="icspnodedeletechild"></a>ICSPNode::DeleteChild

从配置服务提供程序节点中删除指定的子节点。 [ICSPNode::Clear](icspnodeclear.md)必须始终是第一次在要删除的子节点上。

## <a name="syntax"></a>语法

``` syntax
HRESULT DeleteChild([in] IConfigManager2URI* puriChildToDelete);
```

## <a name="parameters"></a>参数

<a href="" id="purichildtodelete"></a>*puriChildToDelete*  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;要删除的子节点的名称。

## <a name="return-values"></a>返回值

| 返回值                 | 说明                                      |
|------------------------------|--------------------------------------------------|
| CFGMGR\_E\_NODENOTFOUND      | 子节点不存在                    |
| CFGMGR\_E\_COMMANDNOTALLOWED | 要删除的子节点是只读节点 |
| S\_确定                        | 成功。                                         |

 
S 的值\_确定指示一个节点已成功删除。 CFGMGR\_E\_NODENOTFOUND 表示子节点不存在。 CFGMGR\_E\_COMMANDNOTALLOWED 表示此节点不支持**ICSP::DeleteChild**方法中，或被删除的子节点是只读节点。

## <a name="remarks"></a>备注

外部事务 – 节点，如果实现此方法，则必须同时实现[ICSPNode::Add](icspnodeadd.md)或回滚将失败。

## <a name="requirements"></a>要求

**标头︰**无

## <a name="related-topics"></a>相关的主题

[创建自定义配置服务提供程序](create-a-custom-configuration-service-provider.md)

 






