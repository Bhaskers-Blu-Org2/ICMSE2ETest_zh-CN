---
title: IProfileCollection
description: IProfileCollection
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 74833b03-86f0-4909-b497-f409365d4ea7
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: d947dc73b6b5a11e9220e536664a280080aa4bfa
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="iprofilecollection"></a>IProfileCollection


表示作为一个单元运行库的配置文件的集合。 该接口提供使客户端能够向集合中添加一个配置文件，将给已经在集合中，其中一个配置文件进行比较的功能从集合中移除一个或所有配置文件。

## <a name="syntax"></a>语法


``` syntax
{
    [id(1), helpstring("Add")] HRESULT Add([in] IProfile* pProfile, [in] VARIANT_BOOL fMerge);
    [id(2), helpstring("Remove")] HRESULT Remove([in] IProfile* pProfile);
    [id(3), helpstring("Clear")] HRESULT Clear();
    [id(4), helpstring("IsEqual")] HRESULT IsEqual([in] IProfileCollection* pProfileCollection);    [id(5), helpstring("LoadIntoXML")] HRESULT LoadIntoXML([out] BSTR* pbstrResults);
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
<th>函数</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[添加](add.md)</p></td>
<td><p>向集合中添加一个配置文件。</p></td>
</tr>
<tr class="even">
<td><p>[删除](remove.md)</p></td>
<td><p>从集合中移除一个配置文件。</p></td>
</tr>
<tr class="odd">
<td><p>[清除](clear.md)</p></td>
<td><p>清除集合中的所有配置文件。</p></td>
</tr>
<tr class="even">
<td><p>[IsEqual](isequal-iprofilecollection.md)</p></td>
<td><p>比较两个<strong>IProfileCollection</strong>对象以查看它们是否具有匹配的配置文件属性。</p></td>
</tr>
<tr class="odd">
<td><p>[LoadIntoXML](loadintoxml.md)</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[接口](interfaces-wprcontrol.md)

 

 







