---
title: ICSPNode SetProperty
description: ICSPNode SetProperty
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: e235c38f-ea04-4cd8-adec-3c6c0ce7172d
ms.openlocfilehash: b980dbd11c2ebe46afaab516b5f14ba8ab10a6be
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="icspnodesetproperty"></a>ICSPNode::SetProperty

此方法设置为配置服务提供程序节点的属性值。

## <a name="syntax"></a>语法

``` syntax
HRESULT SetProperty([in] REFGUID guidProperty, 
                    [in] VARIANT varValue);
```

## <a name="parameters"></a>参数

<a href="" id="guidproperty"></a>*guidProperty*  
<p style="margin-left: 25px">该属性的 GUID。</p>

<a href="" id="varvalue"></a>*varValue*  
<p style="margin-left: 25px">要返回的值。</p>

## <a name="return-value"></a>返回值

S 的值\_确定指示成功找到了一个节点。 CFGMGR\_E\_COMMANDNOTSUPPORTED 表示此节点委派到 ConfigManager2 属性的管理。

## <a name="remarks"></a>备注

每个节点必须正确处理 CFGMGR\_属性\_数据类型属性。

对于外部事务 – 节点，没有其他的方法所需的成功回滚。

## <a name="requirements"></a>要求

**标头︰**无

## <a name="related-topics"></a>相关的主题

[创建自定义配置服务提供程序](create-a-custom-configuration-service-provider.md)

 






