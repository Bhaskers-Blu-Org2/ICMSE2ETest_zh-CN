---
title: IControlProgressHandler
description: IControlProgressHandler
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 05c08784-fcfe-46f8-8209-51fd2b1367fe
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 77178c34a6f89d99649b8fa313e1e4f6b7bc4358
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="icontrolprogresshandler"></a>IControlProgressHandler


此接口是库执行某项操作时接收更新的客户端的处理程序。 然后，库执行同步回调到客户端，指示操作的进度。 根据用户的操作，客户端返回代码指示库可以继续操作，否则取消。 此过程使用户界面来显示用户**保存**如长时间操作的进度。 如果用户选择取消操作，UI 会返回相应的代码库。

## <a name="syntax"></a>语法


``` syntax
{
  [id(1), helpstring("OnBegin")] HRESULT OnBegin();
  [id(2), helpstring("OnUpdate")] HRESULT OnUpdate
    ([in] ULONG CurrentValuePercent);
  [id(3), helpstring("OnEnd")] HRESULT OnEnd
    ([in] HRESULT hrResult);
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
<td><p>[OnBegin](onbegin.md)</p></td>
<td><p>指示要开始操作的库。</p></td>
</tr>
<tr class="even">
<td><p>[OnUpdate](onupdate.md)</p></td>
<td><p>指示库继续操作的进度。</p></td>
</tr>
<tr class="odd">
<td><p>[OnEnd](onend.md)</p></td>
<td><p>在操作结束后返回的状态代码。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[接口](interfaces-wprcontrol.md)

 

 







