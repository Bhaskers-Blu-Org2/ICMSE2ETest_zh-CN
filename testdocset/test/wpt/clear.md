---
title: "最浅"
description: "最浅"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 7c37cc24-75c5-45e3-b35a-7d874574ce54
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 15f6430cb65e6b579085a6f40aa538be3ddb0275
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="clear"></a>最浅


从集合中移除所有配置文件。

## <a name="syntax"></a>语法


``` syntax
HRESULT Clear();
```

## <a name="parameters"></a>参数


无。

## <a name="return-value"></a>返回值


下表描述了可能的返回值。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>返回值</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>S_OK</p></td>
<td><p>函数成功从集合中移除所有配置文件。</p></td>
</tr>
<tr class="even">
<td><p>E_WPRC_FAILED_TO_CLEAR_PROFILE_COLLECTION</p></td>
<td><p>磁带库无法从集合中移除所有配置文件。 使用[传入](http://go.microsoft.com/fwlink/p/?linkid=217161 )来获取详细的错误信息。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[IProfileCollection](iprofilecollection.md)

 

 







