---
title: "错误代码"
description: "错误代码"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 08f519ec-ef59-4bbd-9155-dcbb9b803fca
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 340d244c1417cad977a60dc33e470e18a16cb63b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="error-codes"></a>错误代码


下表描述了 WPRControl 错误代码。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>错误代码</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>E_WPRC_DUPLICATE_INSTANCE_RUNNING</p></td>
<td><p>库检测到库的另一个实例已在运行。</p></td>
</tr>
<tr class="even">
<td><p>E_WPRC_FAILED_TO_ADD_PROFILE</p></td>
<td><p>磁带库无法向集合中添加一个配置文件。</p></td>
</tr>
<tr class="odd">
<td><p>E_WPRC_FAILED_TO_CANCEL_PROFILE</p></td>
<td><p>磁带库未通过取消配置文件集合中的一个配置文件。</p></td>
</tr>
<tr class="even">
<td><p>E_WPRC_FAILED_TO_CLEAR_PROFILE_COLLECTION</p></td>
<td><p>磁带库无法从集合中移除所有配置文件。</p></td>
</tr>
<tr class="odd">
<td><p>E_WPRC_FAILED_TO_DISABLE_DEBUG_LOGGING</p></td>
<td><p>磁带库未通过禁用调试日志记录。</p></td>
</tr>
<tr class="even">
<td><p>E_WPRC_FAILED_TO_DISABLE_PROFILES_FOR_BOOT_TRACING</p></td>
<td><p>磁带库无法删除的配置文件，以便它们在启动过程中无法启动。</p></td>
</tr>
<tr class="odd">
<td><p>E_WPRC_FAILED_TO_ENABLE_DEBUG_LOGGING</p></td>
<td><p>磁带库未启用调试日志记录。</p></td>
</tr>
<tr class="even">
<td><p>E_WPRC_FAILED_TO_ENABLE_PROFILES_FOR_BOOT_TRACING</p></td>
<td><p>磁带库无法保存的配置文件在启动过程中启动。</p></td>
</tr>
<tr class="odd">
<td><p>E_WPRC_FAILED_TO_QUERY_BUILTIN_PROFILES</p></td>
<td><p>磁带库未通过查询内置的配置文件。</p></td>
</tr>
<tr class="even">
<td><p>E_WPRC_FAILED_TO_QUERY_PROFILES</p></td>
<td><p>磁带库无法查询会话和中的所有配置文件提供程序的属性。</p></td>
</tr>
<tr class="odd">
<td><p>E_WPRC_FAILED_TO_REMOVE_PROFILE</p></td>
<td><p>磁带库未通过从集合中删除配置文件。</p></td>
</tr>
<tr class="even">
<td><p>E_WPRC_FAILED_TO_SAVE_PROFILE</p></td>
<td><p>磁带库无法保存配置文件的配置文件集合中。</p></td>
</tr>
<tr class="odd">
<td><p>E_WPRC_FAILED_TO_START_PROFILE</p></td>
<td><p>磁带库未通过启动配置文件集合中的一个配置文件。</p></td>
</tr>
<tr class="even">
<td><p>E_WPRC_FAILED_TO_STOP_PROFILE</p></td>
<td><p>磁带库未通过停止配置文件集合中的一个配置文件。</p></td>
</tr>
<tr class="odd">
<td><p>E_WPRC_FAILED_TO_UPDATE_PROFILE</p></td>
<td><p>磁带库未通过更新配置文件的配置文件集合中。</p></td>
</tr>
<tr class="even">
<td><p>E_WPRC_FAILED_TO_VALIDATE_PROFILE</p></td>
<td><p>磁带库未通过验证的配置文件。</p></td>
</tr>
<tr class="odd">
<td><p>E_WPRC_FAILED_TO_VALIDATE_TRACEMERGE_PROPERTIES</p></td>
<td><p>磁带库未通过验证跟踪合并属性。</p></td>
</tr>
<tr class="even">
<td><p>E_WPRC_INVALID_PROFILES_RUNTIME_STATE</p></td>
<td><p>在系统上运行的配置文件是不同于那些用于开始录制。</p></td>
</tr>
<tr class="odd">
<td><p>E_WPRC_TRACE_MERGE_LOST_EVENTS</p></td>
<td><p>事件跟踪 Windows (ETW) 会话丢失事件，并合并来自会话的事件跟踪日志 (ETL) 文件可能会创建一个不完整的 ETL 文件。</p></td>
</tr>
<tr class="even">
<td><p>E_WPRC_WOW64_NOT_SUPPORTED</p></td>
<td><p>配置库不支持 Windows 32 位的 Windows 64 位。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[WPRControl API 参考](wprcontrol-api-reference.md)

 

 







