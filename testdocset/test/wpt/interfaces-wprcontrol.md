---
title: "接口"
description: "接口"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: d986953c-cadf-4c6e-a204-12a29e0b672e
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: b351c1a93d934aa5ee02e3badd928360523dde00
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="interfaces"></a>接口


本节介绍 WPRControl API 提供的接口。

## <a name="in-this-section"></a>在这一节


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>[IControlErrorInfo](icontrolerrorinfo.md)</p></td>
<td><p>提供控件管理器执行操作时发生，获取有关错误的信息的功能。</p></td>
</tr>
<tr class="even">
<td><p>[IControlManager](icontrolmanager.md)</p></td>
<td><p>表示 Windows 性能记录器 (WPR) 管理器，它控制着 ETW 会话。</p></td>
</tr>
<tr class="odd">
<td><p>[IControlProgressHandler](icontrolprogresshandler.md)</p></td>
<td><p>表示客户端处理程序库执行某项操作时接收更新。</p></td>
</tr>
<tr class="even">
<td><p>[IEnumControlWarningInfo](ienumcontrolwarninginfo.md)</p></td>
<td><p>提供用于枚举的[IControlErrorInfo](icontrolerrorinfo.md)接口的集合的标准 COM 枚举方法。</p></td>
</tr>
<tr class="odd">
<td><p>[IEnumProfile](ienumprofile.md)</p></td>
<td><p>提供用于枚举的[IProfile](iprofile.md)接口的集合的标准 COM 枚举方法。</p></td>
</tr>
<tr class="even">
<td><p>[IOnOffTransitionManager](ionofftransitionmanager.md)</p></td>
<td><p>使客户端存储的[IProfileCollection](iprofilecollection.md)注册表的启动跟踪配置文件。</p></td>
</tr>
<tr class="odd">
<td><p>[IParsingErrorInfo](iparsingerrorinfo.md)</p></td>
<td><p>提供用于获取有关 XML 验证失败的信息函数。</p></td>
</tr>
<tr class="even">
<td><p>[IProfile](iprofile.md)</p></td>
<td><p>表示客户端控件的单个配置文件。</p></td>
</tr>
<tr class="odd">
<td><p>[IProfileCollection](iprofilecollection.md)</p></td>
<td><p>表示作为一个单元运行库的配置文件的集合。</p></td>
</tr>
<tr class="even">
<td><p>[ITraceMergeProperties](itracemergeproperties.md)</p></td>
<td><p>启用客户端指定为合并使用 XML 的多个事件跟踪日志 (ETL) 文件的策略。</p></td>
</tr>
<tr class="odd">
<td><p>[ITraceMergeTextHandler](itracemergetexthandler.md)</p></td>
<td><p>获取文本和由用户添加其他元数据。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[WPRControl API 参考](wprcontrol-api-reference.md)

 

 







