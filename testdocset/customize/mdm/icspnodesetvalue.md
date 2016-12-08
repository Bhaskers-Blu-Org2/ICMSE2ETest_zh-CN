---
title: ICSPNode SetValue
description: ICSPNode SetValue
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: b218636d-fe8b-4a0f-b4e8-a621f65619d3
ms.openlocfilehash: fe88c00cf87aeba758bcdd48b90496d807ebd992
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="icspnodesetvalue"></a>ICSPNode::SetValue

此方法设置的值为配置服务提供程序节点。 它是错误试图设置内部节点的值。

## <a name="syntax"></a>语法

``` syntax
HRESULT SetValue([in] VARIANT varValue);
```

## <a name="parameters"></a>参数

<a href="" id="varvalue"></a>*varValue*  
<p style="margin-left: 25px">要设置的值。 若要清除叶节点的值，请将*varValue*类型设置为`VT_NULL`。</p>

## <a name="return-value"></a>返回值

S 的值\_确定指示成功地设置了值。 CFGMGR\_E\_COMMANDNOTALLOWED 表示此节点不支持**ICSP::SetValue**方法中，或者它是一个内部节点。

## <a name="remarks"></a>备注

对于外部事务 – 节点，必须不实现任何其他方法无法支持回滚功能。

## <a name="requirements"></a>要求

**标头︰**无

## <a name="related-topics"></a>相关的主题

[创建自定义配置服务提供程序](create-a-custom-configuration-service-provider.md)

 






