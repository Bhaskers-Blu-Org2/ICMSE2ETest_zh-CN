---
title: ICSPNode GetValue
description: ICSPNode GetValue
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: c684036d-98be-4659-8ce8-f72436a39b90
ms.openlocfilehash: 487b04617e234564354ea470536b79dd98e540e6
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="icspnodegetvalue"></a>ICSPNode::GetValue

此方法获取的节点的值和数据类型。 内部 （非叶） 的节点可能没有值。

## <a name="syntax"></a>语法

``` syntax
HRESULT GetValue([in,out] VARIANT* pvarValue);
```

## <a name="parameters"></a>参数

<a href="" id="pvarvalue"></a>*pvarValue*  
<p style="margin-left: 25px">要返回的数据值。 包含密码值的节点返回 16 星号 ('\*') 的此方法。 尚未设置其值的叶节点返回一个 variant 类型，其类型为`VT_NULL`。
</p>

## <a name="return-value"></a>返回值

S 的值\_确定指示成功找到了一个节点。 CFGMGR\_E\_COMMANDNOTALLOWED 表示此节点不支持**ICSP::GetValue**的方法，或这是一个内节点。

## <a name="remarks"></a>备注

对于外部事务 – 节点，此节点不需要实现的成功回滚任何其他方法。

## <a name="requirements"></a>要求

**标头︰**无

## <a name="related-topics"></a>相关的主题

[创建自定义配置服务提供程序](create-a-custom-configuration-service-provider.md)

 






