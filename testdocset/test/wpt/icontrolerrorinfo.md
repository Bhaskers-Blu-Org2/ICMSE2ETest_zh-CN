---
title: IControlErrorInfo
description: IControlErrorInfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 47dd2be1-9217-4045-b530-c8b022c3c794
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 4e993102972e02eeaab429a2e5599f8e2d5c7511
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="icontrolerrorinfo"></a>IControlErrorInfo


提供控件管理器执行操作时发生，获取有关错误的信息的功能。 该错误指示发生错误的对象的类型︰ 收集器或提供程序的配置文件。 可以嵌套此接口以提供错误的信息的层次结构。 接口是从 COM[传入](http://go.microsoft.com/fwlink/p/?linkid=217161)接口，它提供了访问的上下文的详细的错误消息的函数。

## <a name="syntax"></a>语法


``` syntax
{
  typedef enum
  {
    ObjectType_Unknown,
    ObjectType_Profile,
    ObjectType_Collector,
    ObjectType_Provider
  } CObjectType;
  [id(1), helpstring("GetObjectType")] HRESULT GetObjectType
    ([out, retval] CObjectType* pObjectType);
  [id(2), helpstring("GetHResult")] HRESULT GetHResult
    ([out, retval] HRESULT* pHResult);
  [id(3), helpstring("GetInnerErrorInfo")] HRESULT GetInnerErrorInfo
    ([out, retval] IUnknown** ppVal);
};
```

## <a name="functions"></a>函数


下表描述了此接口的函数。

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
<td><p>[GetObjectType](getobjecttype.md)</p></td>
<td><p>返回产生错误的类型。</p></td>
</tr>
<tr class="even">
<td><p>[GetHResult](gethresult.md)</p></td>
<td><p>返回一个 HRESULT 值，该值指示的错误代码。</p></td>
</tr>
<tr class="odd">
<td><p>[GetInnerErrorInfo](getinnererrorinfo.md)</p></td>
<td><p>返回有关错误的其他信息。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[接口](interfaces-wprcontrol.md)

 

 







