---
title: LoadIntoXML
description: LoadIntoXML
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: aa5556fa-d58a-450d-b217-93986c383239
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: b76fc68e9155814a19fbe56797b07b373ef66fd9
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="loadintoxml"></a>LoadIntoXML


获得[IProfileCollection](iprofilecollection.md)对象中的所有配置文件的 XML 格式。

## <a name="syntax"></a>语法


``` syntax
[id(5), helpstring("LoadIntoXML")] HRESULT LoadIntoXML([out] BSTR* pbstrResults);
```

## <a name="parameters"></a>参数


<a href="" id="pbstrresults--out-"></a>*pbstrResults*\[出\]  
结果字符串的指针。

## <a name="return-value"></a>返回值


## <a name="remarks"></a>注解


此函数将输出一个合并的配置文件已添加到配置文件集合的所有配置文件。

## <a name="related-topics"></a>相关的主题


[IProfileCollection](iprofilecollection.md)

 

 







