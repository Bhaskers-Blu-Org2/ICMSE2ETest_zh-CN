---
title: CControlManager
description: CControlManager
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 1952f739-e610-4bc3-938f-8ffad3875aec
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: d434adb9481268b5aa57e208c2f2de33914bf1b4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="ccontrolmanager"></a>CControlManager


表示控件管理器运行配置文件集合。 类实现的[IControlManager](icontrolmanager.md)、 [IOnOffTransitionManager](ionofftransitionmanager.md)、 [IControlErrorInfo](icontrolerrorinfo.md)和[IEnumControlWarningInfo](ienumcontrolwarninginfo.md)接口。 若要运行配置文件，客户端实例化类的实例。 库维护的单一、 静态实例管理器。 如果客户端尝试实例化多次，则库返回原始实例和增加引用计数。

## <a name="syntax"></a>语法


``` syntax
{
  [default] interface IControlManager;
  interface IOnOffTransitionManager;
  interface IControlErrorInfo;
  interface IEnumControlWarningInfo;
};
```

## <a name="related-topics"></a>相关的主题


[类](classes.md)

 

 







