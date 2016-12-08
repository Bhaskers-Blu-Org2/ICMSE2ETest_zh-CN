---
title: ICSPValidate
description: ICSPValidate
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: b0993f2d-6269-412f-a329-af25fff34ca2
ms.openlocfilehash: f9f03e0f95f9479201c8321663f88cd803fddd69
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="icspvalidate"></a>ICSPValidate

此接口是可选的。 它由 ConfigManager2 因为它批命令事务开始之前调用。 这使得配置服务提供程序执行的特定操作之前验证节点。 它通常只用于配置服务提供程序，需要公开用户界面。

``` syntax
interface ICSPValidate : IUnknown
{
    HRESULT ValidateAdd([in] IConfigNodeState* pNodeState,
                        [in] IConfigManager2URI* puriChild, 
                        [in] CFG_DATATYPE DataType,
                        [in] VARIANT varValue);
    HRESULT ValidateCopy([in] IConfigNodeState* pNodeState, 
                         [in] IConfigManager2URI* puriDestination);
    HRESULT ValidateDeleteChild([in] IConfigNodeState* pNodeState, 
                                [in] IConfigManager2URI* puriChild);
    HRESULT ValidateClear([in] IConfigNodeState* pNodeState);
    HRESULT ValidateExecute([in] IConfigNodeState* pNodeState, 
                            [in] VARIANT varUserData);
    HRESULT ValidateMove([in] IConfigNodeState* pNodeState, 
                         [in] IConfigManager2URI* puriDestination);
    HRESULT ValidateSetValue([in] IConfigNodeState* pNodeState, 
                             [in] VARIANT varValue);
    HRESULT ValidateSetProperty([in] IConfigNodeState* pNodeState, 
                                [in] REFGUID guidProperty, 
                                [in] VARIANT varValue);
    HRESULT ValidateDeleteProperty([in] IConfigNodeState* pNodeState, 
                                   [in] REFGUID guidProperty);
```

## <a name="related-topics"></a>相关的主题

[创建自定义配置服务提供程序](create-a-custom-configuration-service-provider.md)

 






