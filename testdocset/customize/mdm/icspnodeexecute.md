---
title: "ICSPNode 执行"
description: "ICSPNode 执行"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 5916e7b7-256d-49fd-82b6-db0547a215ec
ms.openlocfilehash: d8a21a2cc6ac824a6d1cb0c714b8cb40320fb507
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="icspnodeexecute"></a>ICSPNode::Execute

此方法通过指定的用户数据中传递和返回结果内部事务配置服务提供程序节点上运行任务。 **执行**和是否甚至支持的确切含义取决于节点的目的。 例如，**执行**上一个节点，表示一个文件调用可能应**ShellExecute**文件，通常在一个注册表节点上调用**执行**没有意义，而。

## <a name="syntax"></a>语法

``` syntax
HRESULT Execute([in] VARIANT varUserData);
```

## <a name="parameters"></a>参数

<a href="" id="varuserdata"></a>*varUserData*  
&nbsp;&nbsp;&nbsp;&nbsp;要传递到执行的数据。

## <a name="return-value"></a>返回值

S 的值\_确定指示操作已成功执行的节点上。 E\_NOTIMPL 未实现此方法应返回。

## <a name="remarks"></a>备注

外部事务 – 节点不支持此方法。

## <a name="requirements"></a>要求

**标头︰**无

## <a name="related-topics"></a>相关的主题

[创建自定义配置服务提供程序](create-a-custom-configuration-service-provider.md)

 




