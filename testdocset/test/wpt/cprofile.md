---
title: CProfile
description: CProfile
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 046b4559-0408-4766-8bb5-d50a695138b9
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: b275d536918f15bfdadb4e380744a9a096f5dbc2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="cprofile"></a>CProfile


表示**配置文件**中的一个对象，包含要配置跟踪 Windows 事件 (ETW) 会话和提供程序的数据。 此类实现的[IProfile](iprofile.md)和[IParsingErrorInfo](iparsingerrorinfo.md)接口。 客户端实例化每个配置文件，则需要运行一个新实例。 在客户端加载配置文件时，该实例验证架构。 如果验证失败，该实例存储错误的信息，并返回一个错误代码。 如果出现错误，客户端接收到**IParsingErrorInfo**的接口指针，然后检索错误信息。

## <a name="syntax"></a>语法


``` syntax
{
  [default] interface IProfile;
  interface IParsingErrorInfo;
};
```

## <a name="related-topics"></a>相关的主题


[类](classes.md)

 

 







