---
title: OnBegin
description: OnBegin
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 125d9c1c-bc34-4642-ae9c-ddd0f62745cb
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 9e0eda73f9536214c87cada6f39e8bf3017564b9
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="onbegin"></a>OnBegin


指示库继续操作的进度。

## <a name="syntax"></a>语法


``` syntax
HRESULT OnBegin();
```

## <a name="parameters"></a>参数


无。

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
<td><p>客户端已请求取消操作。 例如，如果用户单击<strong>取消</strong>时，客户端将返回此代码。</p></td>
</tr>
</tbody>
</table>

 

## <a name="remarks"></a>备注


此方法用于在回调跟踪中的各种操作，如启动或停止跟踪。 只是在行动开始之前调用。

## <a name="related-topics"></a>相关的主题


[IControlProgressHandler](icontrolprogresshandler.md)

 

 







