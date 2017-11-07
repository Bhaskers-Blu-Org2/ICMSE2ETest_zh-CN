---
title: "删除"
description: "删除"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 41897744-5d47-4fec-8f9d-490e98e17e14
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 62bebb62c6cefeeb7f4f158801cde256f7941d32
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="remove"></a>删除


从集合中移除一个[IProfile](iprofile.md)对象。

## <a name="syntax"></a>语法


``` syntax
HRESULT Remove
  ([in] IProfile* pProfile)
;
```

## <a name="parameters"></a>参数


<a href="" id="pprofile"></a>*pProfile*  
\[在\]要从集合中移除的**IProfile**对象的指针。

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
<td><p>函数成功从集合中移除该配置文件。</p></td>
</tr>
<tr class="even">
<td><p>E_INVALIDARG</p></td>
<td><p>参数无效。 使用[传入](http://go.microsoft.com/fwlink/p/?linkid=217161)来获取详细的错误信息。</p></td>
</tr>
<tr class="odd">
<td><p>E_WPRC_FAILED_TO_REMOVE_PROFILE</p></td>
<td><p>磁带库无法从集合中移除该配置文件。 使用<strong>传入</strong>来获取详细的错误信息。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[IProfileCollection](iprofilecollection.md)

 

 







