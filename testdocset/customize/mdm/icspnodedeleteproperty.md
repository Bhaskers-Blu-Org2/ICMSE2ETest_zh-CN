---
title: ICSPNode DeleteProperty
description: ICSPNode DeleteProperty
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 7e21851f-d663-4558-b3e8-590d24b4f6c4
ms.openlocfilehash: 4c9d1c4f3d5dfb2d2660495b6e64108d55bdf2d8
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="icspnodedeleteproperty"></a>ICSPNode::DeleteProperty

此方法从配置服务提供程序节点中删除一个属性。

## <a name="syntax"></a>语法

``` syntax
HRESULT DeleteProperty([in] REFGUID guidProperty);
```

## <a name="parameters"></a>参数

<a href="" id="guidproperty"></a>*guidProperty*  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;若要删除该属性的 GUID。

## <a name="return-value"></a>返回值

S 的值\_确定指示成功找到了一个节点。 CFGMGR\_E\_PROPERTYNOTSUPPORTED 表示此节点不会管理或实现该属性本身，但委派到 ConfigManager2。 E\_NOTIMPL 表示此节点不支持此方法。

## <a name="remarks"></a>备注

外部事务 – 节点，如果实现此方法，则必须同时实现[ICSPNode::SetProperty](icspnodesetproperty.md)或回滚将失败。

## <a name="requirements"></a>要求

**标头︰**无

## <a name="related-topics"></a>相关的主题

[创建自定义配置服务提供程序](create-a-custom-configuration-service-provider.md)

 






