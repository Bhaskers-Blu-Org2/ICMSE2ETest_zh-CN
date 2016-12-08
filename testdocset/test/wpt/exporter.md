---
title: "导出程序"
description: "导出程序"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 3b6b8ff1-b1c6-4117-a44a-010629b6b981
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: a75dc624a3c325e11d157cb57aeb7e338d198007
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="exporter"></a>导出程序


WPA 导出程序是一个命令行工具自动的分析方案为提供 WPA 功能。 通过批处理 WPA 导出程序命令组合在一起时，您可以更大规模地比通过用户界面上执行跟踪分析。

WPA 导出程序可用于从单个跟踪和配置文件，可以选择过滤到一个特定的时间范围，为.csv （逗号分隔值） 文件导出表。 可以通过以下任一定义这些时间范围︰

-   数字时间戳值

-   已命名的标记

-   [感兴趣的区域](regions-of-interest.md)

如果不指定时间范围内，从整个跟踪持续时间数据导出。

当前不能从[比较分析视图](comparative-analysis-views.md)导出表。

## <a name="syntax"></a>语法


若要使用 WPA 出口商，必须提供现有的跟踪文件和配置文件。

`wpaexporter.exe [-i] traceFile.etl -profile profile.wpaProfile [-delimiter <char>] [-prefix <prefix>] [-outputfolder <folder>] [-range <start> <end>] [-marks <M1> <M2>] [-regionsxml <manifest> ...] [-region <region_name>] [-symbols] [-tti] [-h | /?]`

## <a name="parameters"></a>参数


<a href="" id="--i--tracefile-etl"></a>*\[-i\] traceFile.etl*  
包含要导出的数据的跟踪文件。 `–i`标志是可选的。

<a href="" id="-profile"></a>*-配置文件*  
包含要导出的表的 WPA 配置文件 (.wpaProfile)。

<a href="" id="-delimiter"></a>*分隔符*  
（可选）要用作 CSV 中值之间的分隔符的字符。 默认的分隔符是逗号。

<a href="" id="-prefix"></a>*-前缀*  
（可选）若要为每个输出文件名的前面添加一个字符串。

<a href="" id="-outputfolder"></a>*-outputfolder*  
（可选）将表导出到的目标文件夹。

<a href="" id="-range"></a>*-区域*  
（可选）时间跨度，从&lt;启动&gt;到&lt;结束&gt;、 要导出。 默认单位是毫微秒，但您也可以指定秒 (s) 毫秒 (ms) 或微秒 （美国）。

**示例︰**`1s`， `100ms`，`500us`

<a href="" id="-marks"></a>*-标记*  
（可选）要导出的范围所指定的两个命名标记。

<a href="" id="-regionsxml"></a>*-regionsxml*  
（可选）一个或多个清单文件包含感兴趣的区域。 您可以指定此标志，而不`–region`标志要导出整个**区域感兴趣的**表。

**示例︰**`-regionsxml regionsxml1.xml regionsxml2.xml`

<a href="" id="-region"></a>*-区域*  
（可选）在跟踪中特定区域的名称。 使用此标志只对该区域的持续时间中导出数据。 如果您使用此标志，则还必须指定至少一个利息清单文件的区域。

<a href="" id="-symbols"></a>*符号*  
（可选）包含此标记以启用符号加载。

<a href="" id="-tti"></a>*-tti*  
（可选）处理跟踪甚至存在时间 inversions。

## <a name="remarks"></a>备注


输出文件的名称将自动生成基于表和预设的名称。 用户可以有选择地指定前缀 (`-prefix`) 和目录 (`-outputfolder`)。

## <a name="related-topics"></a>相关的主题


[WPA 功能](wpa-features.md)

[查看配置文件](view-profiles.md)

 

 







