---
title: ITraceMergeProperties
description: ITraceMergeProperties
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 6afd2bab-ef90-4182-9757-45d62b4be952
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: f6faf49fea713d867e30cb962c729a757c4c7d79
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="itracemergeproperties"></a>ITraceMergeProperties


使客户端可以指定应合并了多个事件跟踪日志 (ETL) 文件，使用 XML。 它提供了从文件或从字符串加载属性，以 XML 格式的功能。

## <a name="syntax"></a>语法


``` syntax
{
  [id(1), helpstring("LoadFromFile")] HRESULT LoadFromFile([in] BSTR bstrTraceMergeName, [in] BSTR bstrFileName);
  [id(2), helpstring("LoadFromString")] HRESULT LoadFromString([in] BSTR bstrTraceMerge);
  [id(3), helpstring("IsEqual")] HRESULT IsEqual([in] ITraceMergeProperties* pTraceMergeProperties);
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
<td><p>[IsEqual](isequal-itracemergeproperties.md)</p></td>
<td><p>从指定文件加载属性。</p></td>
</tr>
<tr class="even">
<td><p>[LoadFromString](loadfromstring-itracemergeproperties.md)</p></td>
<td><p>从指定的字符串加载属性。</p></td>
</tr>
<tr class="odd">
<td><p>[IsEqual](isequal-itracemergeproperties.md)</p></td>
<td><p>比较两个<strong>ITraceMergeProperties</strong>对象。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[接口](interfaces-wprcontrol.md)

 

 







