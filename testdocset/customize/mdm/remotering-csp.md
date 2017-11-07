---
title: "RemoteRing 的 CSP"
description: "RemoteRing 的 CSP"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 70015243-c07f-46cb-a0f9-4b4ad13a5609
ms.openlocfilehash: 19c74a4f6706970a224a12399fe0e504e87e5bb4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="remotering-csp"></a>RemoteRing 的 CSP


RemoteRing 配置服务提供程序可用于远程触发发声听见铃无论在设备设置该卷的设备。

下面的关系图以树格式显示 RemoteRing 配置服务提供程序。

![资源调配\-csp\-remotering](images/provisioning-csp-remotering.png)

<a href="" id="ring"></a>**环**  
必需。 该节点接受环设备的请求。

受支持的操作被执行。

## <a name="examples"></a>示例


下面的示例演示如何启动一个远程设备上的环。

``` syntax
<Exec>
  <CmdID>5</CmdID> 
    <Item> 
    <Target> 
      <LocURI>./Vendor/MSFT/RemoteRing/Ring </LocURI> 
    </Target> 
    </Item> 
</Exec>
```

 

 






