---
title: IParsingErrorInfo
description: IParsingErrorInfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: bdec574b-3863-499f-8bf3-fe89d4400d29
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: ef44c7c6ed88e1495975d278e150b6d5f8829acc
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="iparsingerrorinfo"></a>IParsingErrorInfo


提供标识位置的 XML 文件验证失败的函数。 接口是从 COM[传入](http://go.microsoft.com/fwlink/p/?linkid=217161)接口，它提供了访问的上下文的详细的错误消息的函数。

## <a name="syntax"></a>语法


``` syntax
{
  [id(1), helpstring("GetColumnNumber")] HRESULT GetColumnNumber
    ([out, retval] ULONG* pColumnNumber);
  [id(2), helpstring("GetLineNumber")] HRESULT GetLineNumber
    ([out, retval] ULONG* pLineNumber);
  [id(3), helpstring("GetElementType")] HRESULT GetElementType
    ([out, retval] BSTR* pbstrElementType);
  [id(4), helpstring("GetElementId")] HRESULT GetElementId
    ([out, retval] BSTR* pbstrElementId);
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
<td><p>[GetColumnNumber](getcolumnnumber.md)</p></td>
<td><p>返回验证错误的列号。</p></td>
</tr>
<tr class="even">
<td><p>[GetLineNumber](getlinenumber.md)</p></td>
<td><p>返回验证错误的行号。</p></td>
</tr>
<tr class="odd">
<td><p>[GetElementType](getelementtype.md)</p></td>
<td><p>返回验证错误发生处的元素类型。</p></td>
</tr>
<tr class="even">
<td><p>[GetElementId](getelementid.md)</p></td>
<td><p>返回验证错误发生处的元素标识符。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[接口](interfaces-wprcontrol.md)

 

 







