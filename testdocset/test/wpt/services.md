---
title: "服务"
description: "服务"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 139a09db-6c62-449a-9369-2219cc99e823
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: a768599f24288300a234a8d8d7246e712a8e7312
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="services"></a>服务


此操作将生成一个文本文件，其中概述了与服务相关的度量标准。

``` syntax
-a services [-range T1 T2] [-poiThreshold_ContainerInit <t>] [-poiThreshold_ImageLoad <t>] [-poiThreshold_ServiceInit <t>]
```

## <a name="parameters"></a>参数


<a href="" id="-ranget1-t2"></a>**-范围***T1 T2*  
显示数据之间时间*T1*和*T2*，同时以微秒为单位。

<a href="" id="-poithreshold-containerinit-t-"></a>**-poiThreshold\_ContainerInit***&lt;t&gt; *  
标志以微秒为单位的利益点大于*t*，任何容器初始化时间。

<a href="" id="-poithreshold-imageload-t-"></a>**-poiThreshold\_ImageLoad***&lt;t&gt; *  
标志的任何映像加载时间超过*t*，单位为微秒，感兴趣的点。

<a href="" id="-poithreshold-serviceinit-t-"></a>**-poiThreshold\_ServiceInit***&lt;t&gt; *  
标志以微秒为单位的利益点大于*t*，任何服务初始化时间。

## <a name="remarks"></a>备注


默认设置是标记为旅游点标识的任何服务。 以毫秒为单位，将显示所有的时间。

## <a name="related-topics"></a>相关的主题


[Xperf 操作](xperf-actions.md)

 

 







