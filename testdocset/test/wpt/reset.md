---
title: Reset
description: Reset
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: ef800c09-aeda-4e16-a12b-9938faccf5ff
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 7727f9fbfd7eea5f75d80b87279f9a18e03d30cd
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="reset"></a>Reset


将枚举数重置回开头。

## <a name="syntax"></a>语法


``` syntax
HRESULT Reset();
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
<td><p>此功能已成功重置枚举。</p></td>
</tr>
<tr class="even">
<td><p>S_FALSE</p></td>
<td><p>指示故障。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[IEnumControlWarningInfo](ienumcontrolwarninginfo.md)

 

 







