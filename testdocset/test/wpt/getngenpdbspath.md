---
title: GetNGenPdbsPath
description: GetNGenPdbsPath
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: b3abddcc-b83f-4cfc-9e9a-64ec96465b21
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 86ff5e32c29a925bfb74f1fcba64ce8f2257e612
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="getngenpdbspath"></a>GetNGenPdbsPath


返回的路径缓存和目标 NGEN PDB 文件托管代码。

## <a name="syntax"></a>语法


``` syntax
HRESULT GetNGenPdbsPath
  ([out] VARIANT_BOOL* pfEnable,
  [out] BSTR* pbstrNGenPdbsCachePath,
  [out] BSTR* pbstrNGenPdbsTargetPath)
;
```

## <a name="parameters"></a>参数


<a href="" id="pfenable"></a>*pfEnable*  
\[出\]boolean 类型的值，该值指示是否启用 NGEN Pdb。

<a href="" id="pbstrngenpdbscachepath"></a>*pbstrNGenPdbsCachePath*  
\[出\]向源路径的指针。

<a href="" id="pbstrngenpdbstargetpath"></a>*pbstrNGenPdbsTargetPath*  
\[出\]一个指针，指向的目标路径。

## <a name="return-value"></a>返回值


下表描述了可能的返回值。 失败返回值是特定于实现的。

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
<td><p>表示成功。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[ITraceMergeTextHandler](itracemergetexthandler.md)

 

 







