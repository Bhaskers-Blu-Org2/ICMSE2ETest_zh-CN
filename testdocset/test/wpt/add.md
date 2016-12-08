---
title: Add
description: Add
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 85e46ed9-12d7-45b8-8e5a-ffbd9193e668
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 80dd6e869ece0e9b7f42c796af92c385479f321e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add"></a>Add


向集合中添加一个配置文件。

## <a name="syntax"></a>语法


``` syntax
HRESULT Add
  ([in] IProfile* pProfile,
  [in] VARIANT_BOOL fMerge)
;
```

## <a name="parameters"></a>参数


<a href="" id="pprofile"></a>*pProfile*  
\[在\]到**IProfile**对象添加到集合的指针。

<a href="" id="fmerge"></a>*fMerge*  
\[在\]布尔值，该值指示是否要合并*pProfile*其中一个集合中具有相同的名称。 如果可变配置文件是在集合中，并且此参数设置为 TRUE，则将合并配置文件。 否则，该方法将返回一个错误。 如果集合不包含具有相同名称的配置文件，该方法将忽略此参数，并向集合添加配置文件。

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
<td><p>函数成功添加到集合的配置文件。</p></td>
</tr>
<tr class="even">
<td><p>E_INVALIDARG</p></td>
<td><p>一个或多个参数是无效的。 使用[传入](http://go.microsoft.com/fwlink/p/?linkid=217161)来获取详细的错误信息。</p></td>
</tr>
<tr class="odd">
<td><p>E_WPRC_FAILED_TO_ADD_PROFILE</p></td>
<td><p>磁带库无法向集合中添加一个配置文件。 使用<strong>传入</strong>来获取详细的错误信息。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[IProfileCollection](iprofilecollection.md)

 

 







