---
title: ICSPNode GetChildNodeNames
description: ICSPNode GetChildNodeNames
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: dc057f2b-282b-49ac-91c4-bb83bd3ca4dc
ms.openlocfilehash: 13c3711bdd27b56c41305b73f6e70a6680083587
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="icspnodegetchildnodenames"></a>ICSPNode::GetChildNodeNames

此方法返回配置服务提供程序节点的子节点的列表。

## <a name="syntax"></a>语法

``` syntax
HRESULT GetChildNodeNames([out] ULONG* pulCount,
                          [out,size_is(,*pulCount)] BSTR** pbstrNodeNames);
```

## <a name="parameters"></a>参数

<a href="" id="pulcount"></a>*pulCount*
<p style="margin-left: 25px">要返回的子节点数。</p>

<a href="" id="pbstrnodenames"></a>*pbstrNodeNames*
<p style="margin-left: 25px">子节点名称的数组。 返回的数组必须分配与`CoTaskMemAlloc`。 数组中的每个元素都必须是有效的非空`BSTR`、 分配由`SysAllocString`或`SysAllocStringLen`。 返回的名称必须不以任何方式，包括规范化原因的 URI 编码，编码。</p>

## <a name="return-value"></a>返回值

S 的值\_确定指示成功找到了一个节点。 CFGMGR\_E\_COMMANDNOTALLOWED 表示，这称为叶节点 （没有子将返回） 上。

## <a name="remarks"></a>备注

对于外部事务 – 节点，没有其他的方法所需的成功回滚。

## <a name="requirements"></a>要求

**标头︰**无

## <a name="related-topics"></a>相关的主题

[创建自定义配置服务提供程序](create-a-custom-configuration-service-provider.md)

 






