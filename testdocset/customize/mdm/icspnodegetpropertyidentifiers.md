---
title: ICSPNode GetPropertyIdentifiers
description: ICSPNode GetPropertyIdentifiers
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 8a052cd3-d74c-40c4-845f-f804b920deb4
ms.openlocfilehash: ff89818afc775b7911cd29266c34d5e83dfd62e9
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="icspnodegetpropertyidentifiers"></a>ICSPNode::GetPropertyIdentifiers

此方法返回该节点所支持的非标准属性的列表。 返回的数组必须分配与`CoTaskMemAlloc`。

## <a name="syntax"></a>语法

``` syntax
HRESULT GetPropertyIdentifiers([out] ULONG* pulCount,
                               [out,size_is(,*pulCount)] GUID** pguidProperties);
```

## <a name="parameters"></a>参数

<a href="" id="pulcount"></a>*pulCount*  
<p style="margin-left: 25px">非标准属性返回的数目。</p>

<a href="" id="pguidproperties"></a>*pguidProperties*  
<p style="margin-left: 25px">属性 Guid 返回的数组。 此数组必须分配与`CoTaskMemAlloc`。</p>

## <a name="return-value"></a>返回值

S 的值\_确定指示属性已成功返回。 E\_NOTIMPL 表示该节点不支持此方法。

## <a name="remarks"></a>备注

对于外部事务 – 节点，没有其他的方法所需的成功回滚。

## <a name="requirements"></a>要求

**标头︰**无

## <a name="related-topics"></a>相关的主题

[创建自定义配置服务提供程序](create-a-custom-configuration-service-provider.md)

 





