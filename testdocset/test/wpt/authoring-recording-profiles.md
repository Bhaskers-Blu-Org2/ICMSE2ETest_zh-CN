---
title: "编写配置文件记录"
description: "编写配置文件记录"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 1eea16bd-f96d-4d17-a857-f93c0d0717b7
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 048db3b52b5dca730dff0d06c74412a77b503a53
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="authoring-recording-profiles"></a>编写配置文件记录


您可以创建 Windows 性能记录器 (WPR) 录制为具有.wprp 扩展名的 XML 文件中的配置文件。 记录配置文件包含所有必要信息，可以记录特定方案的性能。 此数据包括有关跟踪 Windows 事件 (ETW) 会话、 提供商和关键字的信息。 每个.wprp 文件包含至少一个配置文件定义，它整合了一组特定的 ETW 会话和提供程序。 配置文件定义还包括会话和提供程序属性开始和控制性能记录。

WPR 配置文件支持以下 ETW 功能︰

-   顺序文件和内存循环日志记录模式。

-   缓存和缓冲区大小，为每个会话的用户指定数量。

-   ETW 系统记录器与 NT 内核记录器的会话。 此合并包含指定关键字、 堆栈和内存池标记的能力。

-   指定提供程序名称或 GUID、 关键字、 堆栈、 详细程度和非分页内存的事件会话。

-   捕获捕获过程中的状态的状态提供程序启动或保存操作只。

.Wprp 文件必须包含按特定顺序列出的特定定义。 下面的主题介绍如何创作该订单中的定义。

## <a name="authoring-wprp-files-in-visual-studio"></a>在 Visual Studio 中的创作.wprp 文件


您可以使用 Visual Studio 通过 WPR 架构文件，WPRControlProfiles.xsd，WPT 安装文件夹中提供的创作录制配置文件︰

1.  在 Visual Studio 中打开.wprp 文件。

2.  在主菜单中，选择**XML**，然后选择**架构...**

3.  在**XML 架构**出现的对话框中，选择**添加...**

4.  选择 WPRControlProfiles.xsd 架构。 默认情况下，此文件为 WPT 安装目录中︰

    -   `C:\Program Files (x86)\Windows Kits\8.1\Windows Performance Toolkit`

一旦选择了架构，您可以使用上下文相关 IntelliSense 来创作.wprp 文件。

## <a name="in-this-section"></a>在这一节


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>[1.收集器定义](1-collector-definitions.md)</p></td>
<td><p>如何定义配置文件的收集器。</p></td>
</tr>
<tr class="even">
<td><p>[2.系统和事件提供程序定义](2-system-and-event-provider-definitions.md)</p></td>
<td><p>如何定义配置文件提供程序。</p></td>
</tr>
<tr class="odd">
<td><p>[3.配置文件定义](3-profile-definitions.md)</p></td>
<td><p>如何定义配置文件。</p></td>
</tr>
<tr class="even">
<td><p>[严格的供应商](strict-providers.md)</p></td>
<td><p>如何使用<strong>严格</strong>属性。</p></td>
</tr>
<tr class="odd">
<td><p>[继承](inheritance.md)</p></td>
<td><p>描述继承创作录制的配置文件中。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[配置文件记录](recording-profiles.md)

[创作自定义录制配置文件](author-a-custom-recording-profile.md)

[添加或删除自定义录制配置文件](add-or-remove-a-custom-recording-profile.md)

 

 







