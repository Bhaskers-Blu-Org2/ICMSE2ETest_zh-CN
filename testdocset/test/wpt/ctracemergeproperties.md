---
title: CTraceMergeProperties
description: CTraceMergeProperties
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: d7991df7-574a-4b48-9e2c-a76bb5da1cd3
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 5a4bd87e49dcd19aa08efc7e7ae108c57717210c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="ctracemergeproperties"></a>CTraceMergeProperties


表示库合并以前已启动使用配置文件的跟踪 Windows 事件 (ETW) 会话的事件跟踪日志 (ETL) 文件时，将应用的策略。 它实现了[ITraceMergeProperties](itracemergeproperties.md)和[IParsingErrorInfo](iparsingerrorinfo.md)接口。 客户端实例化它需要合并的 ETL 文件应用每个合并属性的新实例。 当在客户端加载 XML 合并属性时，实例验证的架构。 如果验证失败，该实例存储错误的信息，并返回一个错误代码。 如果出现错误，客户端获取到**IParsingErrorInfo**的接口指针，并检索错误的信息。

## <a name="syntax"></a>语法


``` syntax
{
  [default] interface ITraceMergeProperties;
  interface IParsingErrorInfo;
};
```

## <a name="related-topics"></a>相关的主题


[类](classes.md)

 

 







