---
title: OnUpdate
description: OnUpdate
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 0dff0606-a8f9-4698-a086-1f8ad7e6b695
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 5af3c38ce663c9984888ededbf601c56096ac471
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="onupdate"></a>OnUpdate


指示库，以继续操作。

## <a name="syntax"></a>语法


``` syntax
HRESULT OnUpdate
  ([in] ULONG CurrentValuePercent)
;
```

## <a name="parameters"></a>参数


<a href="" id="currentvaluepercent"></a>*CurrentValuePercent*  
\[在\]指示已完成操作的百分比。

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
<td><p>表示成功。 该操作将继续。</p></td>
</tr>
<tr class="even">
<td><p>其中包含 E_ABORT</p></td>
<td><p>客户端已请求库取消该操作。 例如，如果用户单击<strong>取消</strong>，该客户端返回此代码库。</p></td>
</tr>
</tbody>
</table>

 

## <a name="remarks"></a>备注


当执行某些更新时，经常在操作过程中调用此函数。 例如，当启动跟踪时，调用每个提供程序启用后时停止和合并跟踪缓冲区的一定百分比合并后。

## <a name="related-topics"></a>相关的主题


[IControlProgressHandler](icontrolprogresshandler.md)

 

 







