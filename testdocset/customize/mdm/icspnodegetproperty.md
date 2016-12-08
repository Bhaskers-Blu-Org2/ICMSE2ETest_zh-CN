---
title: "ICSPNode 替代"
description: "ICSPNode 替代"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: a2bdc158-72e0-4cdb-97ce-f5cf1a44b7db
ms.openlocfilehash: 8aa482ef59fd86e09c9147909079b2b575af8ad9
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="icspnodegetproperty"></a>ICSPNode::GetProperty

从配置服务提供程序节点，此方法返回的属性值。

## <a name="syntax"></a>语法

``` syntax
HRESULT GetProperty([in] REFGUID guidProperty, 
                    [in,out] VARIANT* pvarValue);
```

## <a name="parameters"></a>参数

<a href="" id="guidproperty"></a>*guidProperty*  
<p style="margin-left: 25px">指定要返回的属性的 GUID。</p>

<a href="" id="pvarvalue"></a>*pvarValue*  
<p style="margin-left: 25px">要返回的值。</p>

## <a name="return-value"></a>返回值

S 的值\_确定指示成功返回的值。 CFGMGR\_E\_COMMANDNOTSUPPORTED 表示该节点不实现该属性本身，但委托到 ConfigManager2 属性的管理。

## <a name="remarks"></a>备注

每个节点必须处理 CFGMGR\_属性\_数据类型属性。

对于外部事务 – 节点，没有其他的方法所需的成功回滚。

## <a name="requirements"></a>要求

**标头︰**无

## <a name="related-topics"></a>相关的主题

[创建自定义配置服务提供程序](create-a-custom-configuration-service-provider.md)

 






