---
title: ITraceMergeTextHandler
description: ITraceMergeTextHandler
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 0827802d-a62a-4420-8bb9-83f8af650669
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: e3a2dc5baef5e80ba378fe83d776fbea50159a1b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="itracemergetexthandler"></a>ITraceMergeTextHandler


获取文本和由用户添加其他元数据。

## <a name="syntax"></a>语法


``` syntax
{
    [propget, id(1), helpstring("Count")] HRESULT Count([out, retval] ULONG* cText);
    [id(2), helpstring("GetText")] HRESULT GetText([in] ULONG iText, [out] BSTR* pbstrText);
    [id(3), helpstring("WaitForText")] HRESULT WaitForText([in] ULONG Milliseconds);
    [id(4), helpstring("GetFileName")] HRESULT GetFileName([out] BSTR* pbstrFileName);
    [id(5), helpstring("GetNGenPdbsPath")] HRESULT GetNGenPdbsPath([out] VARIANT_BOOL* pfEnable, [out] BSTR* pbstrNGenPdbsCachePath, [out] BSTR* pbstrNGenPdbsTargetPath);
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
<td><p><strong>propget</strong></p></td>
<td><p>返回指定属性的值。</p></td>
</tr>
<tr class="even">
<td><p>[GetText](gettext.md)</p></td>
<td><p>获取从指定的文件的字符串。</p></td>
</tr>
<tr class="odd">
<td><p>[WaitForText](waitfortext.md)</p></td>
<td><p>等待，直到用户添加适当的文本字符串和调用。</p></td>
</tr>
<tr class="even">
<td><p>[GetFileName](getfilename.md)</p></td>
<td><p>获取文件的名称。</p></td>
</tr>
<tr class="odd">
<td><p>[GetNGenPdbsPath](getngenpdbspath.md)</p></td>
<td><p>获取 NGEN Pdb 的路径。</p></td>
</tr>
</tbody>
</table>

 

## <a name="properties"></a>属性


下表描述此接口提供的属性。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>属性</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>计数</strong></p></td>
<td><p>指示用户添加文本项的数目。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[接口](interfaces-wprcontrol.md)

 

 







