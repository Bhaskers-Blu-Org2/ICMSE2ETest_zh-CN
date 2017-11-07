---
title: ICSPNodeTransactioning
description: ICSPNodeTransactioning
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 24dc518a-4a8d-41fe-9bc6-217bbbdf6a3f
ms.openlocfilehash: 65e0d6cbb324039364f0208c66565fdb3fdc41b9
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="icspnodetransactioning"></a>ICSPNodeTransactioning

这是可选的界面，使配置服务提供程序定义为单个节点自身事务方案 （内部事务）。 事务支持的功能在节点上回滚上一操作。 多数节点使用外部事务，会自动处理，并不需要实现此接口。 有关内部和外部事务的详细信息，包括如何处理`RollbackAction`的功能，请参阅"确定节点操作"[设计一个自定义配置服务提供程序](design-a-custom-windows-csp.md)。

``` syntax
interface ICSPNodeTransactioning : IUnknown
{
    HRESULT PersistRollbackAddState([in] IConfigManager2URI* puriChild, 
                                    [in] CFG_DATATYPE DataType, 
                                    [in] VARIANT varValue, 
                                    [in] ISequentialStream* pRollbackStream, 
                                    [in] ISequentialStream* pUninstallStream);
    HRESULT PersistRollbackCopyState([in] IConfigManager2URI* puriDestination, 
                                     [in] ISequentialStream* pRollbackStream, 
                                     [in] ISequentialStream* pUninstallStream);
    HRESULT PersistRollbackDeleteChildState([in] IConfigManager2URI* puriChild, 
                                            [in] ISequentialStream* pRollbackStream, 
                                            [in] ISequentialStream* pUninstallStream);
    HRESULT PersistRollbackClearState([in] ISequentialStream* pRollbackStream, 
                                      [in] ISequentialStream* pUninstallStream);
    HRESULT PersistRollbackExecuteState([in] VARIANT varUserData, 
                                        [in] ISequentialStream* pRollbackStream, 
                                        [in] ISequentialStream* pUninstallStream);
    HRESULT PersistRollbackMoveState([in] IConfigManager2URI* puriDestination, 
                                     [in] ISequentialStream* pRollbackStream, 
                                     [in] ISequentialStream* pUninstallStream);
    HRESULT PersistRollbackSetValueState([in] VARIANT varValue, 
                                         [in] ISequentialStream* pRollbackStream, 
                                         [in] ISequentialStream* pUninstallStream);
    HRESULT PersistRollbackSetPropertyState([in] REFGUID guidProperty, 
                                            [in] VARIANT varValue, 
                                            [in] ISequentialStream* pRollbackStream, 
                                            [in] ISequentialStream* pUninstallStream); 
    HRESULT PersistRollbackDeletePropertyState([in] REFGUID guidProperty, 
                                               [in] ISequentialStream* pRollbackStream, 
                                               [in] ISequentialStream* pUninstallStream);
    HRESULT RollbackAdd([in] ISequentialStream* pUndoStream, 
                        [in] BOOL fRecoveryRollback);
    HRESULT RollbackCopy([in] ISequentialStream* pUndoStream, 
                         [in] BOOL fRecoveryRollback);
    HRESULT RollbackDeleteChild([in] ISequentialStream* pUndoStream, 
                                [in] BOOL fRecoveryRollback);
    HRESULT RollbackClear([in] ISequentialStream* pUndoStream, 
                          [in] BOOL fRecoveryRollback);
    HRESULT RollbackExecute([in] ISequentialStream* pUndoStream, 
                            [in] BOOL fRecoveryRollback);
    HRESULT RollbackMove([in] ISequentialStream* pUndoStream, 
                         [in] BOOL fRecoveryRollback);
    HRESULT RollbackSetValue([in] ISequentialStream* pUndoStream, 
                             [in] BOOL fRecoveryRollback);
    HRESULT RollbackSetProperty([in] ISequentialStream* pUndoStream, 
                                [in] BOOL fRecoveryRollback);
    HRESULT RollbackDeleteProperty([in] ISequentialStream* pUndoStream, 
                                   [in] BOOL fRecoveryRollback);

    HRESULT Commit();
};
```

## <a name="related-topics"></a>相关的主题

[创建自定义配置服务提供程序](create-a-custom-configuration-service-provider.md)

 





