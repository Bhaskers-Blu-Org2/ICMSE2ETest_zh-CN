---
title: "编写自定义配置服务提供程序的示例"
description: "编写自定义配置服务提供程序的示例"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: ccda4d62-7ce1-483b-912f-25d50c974270
ms.openlocfilehash: 6b7b0cd2eed047ece5e7312aa0e2e354308495cc
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="samples-for-writing-a-custom-configuration-service-provider"></a>编写自定义配置服务提供程序的示例

下面的示例演示如何检索双 sim 卡手机集成电路卡标识符 (ICCID) 和国际移动用户标识 (IMSI)。

## <a name="retrieving-iccid-and-imsi-for-a-dual-sim-phone"></a>检索 ICCID 和双 sim 卡手机的 IMSI

下面的示例使用[IConfigServiceProvider2::ConfigManagerNotification](iconfigserviceprovider2configmanagernotification.md)方法实现。 第一次检索 IConfigSession2 对象中，并使用 IConfigSession2::GetSessionVariable 方法然后查询 ICCID。 若要检索 IMSI，替换 L"IMSI"L"ICCID"。

``` syntax
case CFGMGR_NOTIFICATION_SETSESSIONOBJ:
    if (NULL != lpParam)
    {
        m_pSession = reinterpret_cast<IConfigSession2*>(lpParam);
        m_pSession->AddRef();
    }

    bstrContext = SysAllocString(L"ICCID");
    if (NULL == bstrContext)
    {
    hr = E_OUTOFMEMORY;
    goto Error;
    }

    hr = m_pSession->GetSessionVariable(bstrContext, &varValue);
    if (FAILED(hr))
    {
        goto Error;
    }
    break;
```

 





