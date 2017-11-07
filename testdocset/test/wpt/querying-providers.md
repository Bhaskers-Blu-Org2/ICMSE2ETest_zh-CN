---
title: "查询提供程序"
description: "查询提供程序"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: abe58e3b-4050-4d42-ad71-a0c702492f8d
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 37b1a0b475fe745ecbf08e6963db2d5c0ad80777
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="querying-providers"></a>查询提供程序


显示跟踪和提供程序查询选项。

``` syntax
xperf {-providers [options] | -loggers | -boottrace | -profint | -profiles | -profileswithdetails | -profilesessions | -profileproviders | -profileloggers}
```

## <a name="parameters"></a>参数


<a href="" id="-providers-options----"></a>**-提供商***\[选项...\]*  
查询所有安装已知且已注册提供程序，以及所有已知的内核标志和组。 有关详细信息，请参阅[提供程序](providers-wpa.md)。

<a href="" id="-loggers"></a>**-记录器**  
查询所有活动的日志记录会话。

<a href="" id="-boottrace"></a>**-boottrace**  
查询启动跟踪配置。

<a href="" id="-profint"></a>**-profint**  
查询的当前配置文件的时间间隔。

<a href="" id="-profiles-profilefilename---profilename-"></a>**-配置文件***{ProfileFileName |ProfileName}*  
查询*ProfileFileName*或*ProfileName*中定义的配置文件名称。 如果未不指定任何参数，则查询的内置配置文件的名称。

<a href="" id="-profileswithdetails-profilefilename---profilename-"></a>**-profileswithdetails***{ProfileFileName |ProfileName}*  
查询配置文件名称中定义的*ProfileFileName*或*ProfileName*中的详细的属性。 如果未不指定任何参数，则查询的内置配置文件的名称。

<a href="" id="-profilesessions-profilefilename---sessionname-"></a>**-profilesessions***{ProfileFileName |会话名}*  
查询配置会话名称定义在*ProfileFileName*或*会话名*。 如果未不指定任何参数，则查询内置的配置文件中的会话的名称。

<a href="" id="-profileproviders-profilefilename---providername-"></a>**-profileproviders***{ProfileFileName |提供程序名称}*  
查询*ProfileFileName*或*提供程序名称*中定义的配置文件提供程序名称。 如果未不指定任何参数，则查询的内置配置文件提供程序的名称。

<a href="" id="-profileloggersprofilename"></a>**-profileloggers***ProfileName*  
查询在*ProfileName*中指定的日志记录会话。

## <a name="related-topics"></a>相关的主题


[Xperf 选项](xperf-options.md)

 

 







