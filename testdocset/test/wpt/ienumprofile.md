---
title: IEnumProfile
description: IEnumProfile
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: a7f512d4-13dd-44be-881b-2b705deb973a
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: aa7de8478e29e62c373eee31d066fbdac72cfe54
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="ienumprofile"></a>IEnumProfile


提供用于枚举的[IProfile](iprofile.md)接口的集合的标准 COM 枚举方法。

## <a name="syntax"></a>语法


``` syntax
{
  [id(1), helpstring("Next")] HRESULT Next
    ([in] ULONG celt,
    [out, size_is(celt), length_is(*pCeltFetched)] IProfile** prgVar,
    [out] ULONG* pCeltFetched);
  [id(2), helpstring("Skip")] HRESULT Skip
    ([in] ULONG celt);
  [id(3), helpstring("Reset")] HRESULT Reset();
  [id(4), helpstring("Clone")] HRESULT Clone
    ([out] IEnumProfile** ppEnum);
};
```

## <a name="functions"></a>函数


下表描述了此接口提供的功能。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>方法</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[下一步](next-ienumprofile.md)</p></td>
<td><p>返回一个数组，其中包含指定的数量的元素。</p></td>
</tr>
<tr class="even">
<td><p>[跳过](skip-ienumprofile.md)</p></td>
<td><p>指示要跳过元素的数。</p></td>
</tr>
<tr class="odd">
<td><p>[重置](reset-ienumprofile.md)</p></td>
<td><p>重置枚举。</p></td>
</tr>
<tr class="even">
<td><p>[克隆](clone-ienumprofile.md)</p></td>
<td><p>创建克隆枚举器。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[接口](interfaces-wprcontrol.md)

 

 







