---
title: IEnumControlWarningInfo
description: IEnumControlWarningInfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 49078217-91ef-444e-9d08-88f87d1b0280
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: b8c9082e82bb5f5aba51ad38933df559c9a930cc
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="ienumcontrolwarninginfo"></a>IEnumControlWarningInfo


提供用于枚举的[IControlErrorInfo](icontrolerrorinfo.md)接口的集合的标准 COM 枚举方法。 当库执行操作，例如启动或更新时，它可能不会启用某些提供程序，例如那些不受支持的系统上。 在这种情况下，库创建**IControlErrorInfo**对象的每个包含描述提供程序被启用的上下文错误详细的信息的列表。 客户端可以查询此接口从[IControlManager](icontrolmanager.md)来确定是否列出了任何错误。

## <a name="syntax"></a>语法


``` syntax
{
  [id(1), helpstring("Next")] HRESULT Next
    ([in] ULONG celt,
    [out, size_is(celt), length_is(*pCeltFetched)] IControlErrorInfo** prgVar,
    [out] ULONG* pCeltFetched);
  [id(2), helpstring("Skip")] HRESULT Skip
    ([in] ULONG celt);
  [id(3), helpstring("Reset")] HRESULT Reset();
  [id(4), helpstring("Clone")] HRESULT Clone
    ([out] IEnumControlWarningInfo** ppEnum);
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
<td><p>[下一步](next.md)</p></td>
<td><p>返回一个数组，其中包含指定的数量的元素。</p></td>
</tr>
<tr class="even">
<td><p>[跳过](skip.md)</p></td>
<td><p>指示要跳过元素的数。</p></td>
</tr>
<tr class="odd">
<td><p>[重置](reset.md)</p></td>
<td><p>重置枚举。</p></td>
</tr>
<tr class="even">
<td><p>[克隆](clone.md)</p></td>
<td><p>创建克隆枚举器。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[接口](interfaces-wprcontrol.md)

 

 







