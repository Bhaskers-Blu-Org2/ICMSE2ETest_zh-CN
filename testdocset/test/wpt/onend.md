---
title: OnEnd
description: OnEnd
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 3daba834-c555-40d4-8afa-ed0a1f6aaedf
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 44660b5d8adc97bcf98a905e19400e284172c6d7
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="onend"></a>OnEnd


在操作结束后返回的状态代码。

## <a name="syntax"></a>语法


``` syntax
HRESULT OnEnd(HRESULT hrResult);
```

## <a name="parameters"></a>参数


<a href="" id="hrresult--in-"></a>*hrResult*\[in\]  
操作完成后的状态代码。

## <a name="return-value"></a>返回值


下表描述了可能的返回值。 WPR 忽略失败值。

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
<td><p>函数成功返回状态。</p></td>
</tr>
</tbody>
</table>

 

## <a name="remarks"></a>备注


媒体库不会检查该函数的返回值。

在停止或保存跟踪时，此回调也会返回在跟踪过程中丢失的事件数。

## <a name="related-topics"></a>相关的主题


[IControlProgressHandler](icontrolprogresshandler.md)

 

 







