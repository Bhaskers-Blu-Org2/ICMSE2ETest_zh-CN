---
author: Justinha
Description: "BCDEdit 是用于管理引导配置数据 (BCD) 的命令行工具。"
ms.assetid: cf7d52f0-13fb-416d-9ec5-9e4eff4fd774
MSHAttr: PreferredLib:/library/windows/hardware
title: "BCDEdit 命令行选项"
ms.openlocfilehash: 0179c5d2aa91b43f359071be2987206ac31036e4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="span-idbcdeditcommand-lineoptionsspanbcdedit-command-line-options"></a><span id="bcdedit_command-line_options"></span>BCDEdit 命令行选项


BCDEdit 是用于管理引导配置数据 (BCD) 的命令行工具。

BCD 文件提供了用于描述引导应用程序和引导应用程序设置的存储区。

BCDEdit 可用于多种用途，包括创建新的存储、 修改现有存储区中添加引导菜单选项等。

您需要具有管理特权才能使用 BCDEdit 修改 BCD。 启动命令提示符 （管理员），或者使用 Windows PE。

正常关机并重新启动有必要确保任何修改的 BCDEdit 设置被刷新到磁盘。

BCDEdit 包含在 %WINDIR%\\System32 文件夹。

BCDEdit 仅限于标准的数据类型，主要用于执行对 BCD 常见的单个更改。 相关的资源︰

-   一些常用的 BCD 操作，例如恢复分区或设置新 PC 的系统分区，可能会更轻松地使用[BCDboot](bcdboot-command-line-options-techref-di.md)来完成。
-   对于复杂的操作或使用了非标准的数据类型，请考虑使用 BCD Windows 管理规范 (WMI) 应用程序编程接口 (API) 来创建更强大而灵活的自定义工具。

## <a name="span-idbcdeditcommand-lineoptionsspanspan-idbcdeditcommand-lineoptionsspanspan-idbcdeditcommand-lineoptionsspanbcdedit-command-line-options"></a><span id="BCDEdit_Command-Line_Options"></span><span id="bcdedit_command-line_options"></span><span id="BCDEDIT_COMMAND-LINE_OPTIONS"></span>BCDEdit 命令行选项


下面的命令行选项都可用于 BCDEdit.exe。

**BCDEdit /Command***\[Argument1\] \[Argument2\] ...*

### <a name="span-idhelpspanspan-idhelpspanspan-idhelpspanhelp"></a><span id="Help"></span><span id="help"></span><span id="HELP"></span>帮助

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">选项</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">/? [命令]</td>
<td align="left"><p>显示 BCDEdit 命令的列表。</p>
<p>若要显示有关特定命令的详细的帮助，请运行<strong>bcdedit /？</strong><em>命令</em>，其中<em>命令</em>是正在寻求更多的信息有关的命令的名称。</p>
<pre class="syntax" space="preserve"><code>bcdedit /? createstore</code></pre></td>
</tr>
</tbody>
</table>

 

### <a name="span-idoperatingonastorespanspan-idoperatingonastorespanspan-idoperatingonastorespanoperating-on-a-store"></a><span id="Operating_on_a_store"></span><span id="operating_on_a_store"></span><span id="OPERATING_ON_A_STORE"></span>在存储上运行

| 选项       | 说明                                                                                                                                                                                                                                                             |
|--------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /createstore | 创建新的空引导配置数据存储。 创建存储区不是一个系统存储区。                                                                                                                                                                             |
| /export      | 导出系统的内容存储到一个文件中。 可以以后使用此文件来还原系统存储的状态。 此命令是仅适用于系统存储区。                                                                                            |
| /import      | 通过使用 /export 选项以前生成的备份数据文件恢复系统存储的状态。 导入操作之前，该命令将删除任何系统存储区中的现有条目。 此命令是仅适用于系统存储区。      |
| /store       | 此选项可以与大多数 BCDedit 命令，用于指定要使用的存储区。 如果不指定此选项，则 BCDEdit 作用于系统存储区。 单独运行 bcdedit /store 命令等同于运行 bcdedit /enum 活动的命令。 |
| /sysstore    | 设置系统存储设备。 这只会影响基于 EFI 的系统。 它不能持续在重新引导后，并在系统存储设备不明确的情况下才使用。                                                                                            |

 

### <a name="span-idoperatingonentriesinastorespanspan-idoperatingonentriesinastorespanspan-idoperatingonentriesinastorespanoperating-on-entries-in-a-store"></a><span id="Operating_on_entries_in_a_store"></span><span id="operating_on_entries_in_a_store"></span><span id="OPERATING_ON_ENTRIES_IN_A_STORE"></span>操作存储区中的项

| 选项  | 说明                                                                                                                                                                                                                                                                                       |
|---------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /copy   | 使在同一个系统存储中指定的启动项目的副本。                                                                                                                                                                                                                                  |
| 创建 / | 引导配置数据存储区中创建一个新项。 如果已知标识符指定，然后 /application / 继承，并且不能指定 /device 选项。 如果标识符未指定或未有已知，/application，/ 继承，或必须指定 /device 选项。 |
| /delete | 从指定的项中删除的元素。                                                                                                                                                                                                                                                        |
| /mirror | 在存储中创建的条目的镜像。                                                                                                                                                                                                                                                           |

 

### <a name="span-idchangingentryoptionsspanspan-idchangingentryoptionsspanspan-idchangingentryoptionsspanchanging-entry-options"></a><span id="Changing_entry_options"></span><span id="changing_entry_options"></span><span id="CHANGING_ENTRY_OPTIONS"></span>更改输入选项

| 选项       | 说明                                    |
|--------------|------------------------------------------------|
| /deletevalue | 从启动项中删除指定的元素。 |
| 设定 /         | 设置项的选项值。                    |

例如，此命令将使系统能够信任 Windows 内幕预览生成默认情况下不信任的证书进行签名︰

``` syntax
Bcdedit /set {bootmgr} flightsigning on
Bcdedit /set flightsigning on
```
运行命令后重新启动。 若要关闭 flightsigning:

``` syntax
Bcdedit /set {bootmgr} flightsigning off
Bcdedit /set flightsigning off
``` 

### <a name="span-idcontrollingoutputspanspan-idcontrollingoutputspanspan-idcontrollingoutputspancontrolling-output"></a><span id="Controlling_output"></span><span id="controlling_output"></span><span id="CONTROLLING_OUTPUT"></span>控制输出

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">选项</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">/enum</td>
<td align="left">列出了存储区中的项。 /Enum 选项是默认值为 BCEdit，因此运行不带任何选项的 bcdedit 命令等同于运行 bcdedit /enum 活动的命令。</td>
</tr>
<tr class="even">
<td align="left">/v</td>
<td align="left">详细模式。 通常情况下，由他们友好的速记形式表示任何已知条目的标识符。 指定的命令行选项 /v 完全显示所有标识符。
<p>单独运行 bcdedit /v 命令等同于运行 bcdedit /enum 活动 /v 命令。</p></td>
</tr>
</tbody>
</table>

 

### <a name="span-idcontrollingthebootmanagerspanspan-idcontrollingthebootmanagerspanspan-idcontrollingthebootmanagerspancontrolling-the-boot-manager"></a><span id="Controlling_the_boot_manager"></span><span id="controlling_the_boot_manager"></span><span id="CONTROLLING_THE_BOOT_MANAGER"></span>控制启动管理器

| 选项             | 说明                                                                                                                                                                                                                                          |
|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /bootsequence      | 指定要用于下一次启动一次性的显示顺序。 此命令类似于 /displayorder 选项，只是下次计算机启动的时，将只使用它。 然后，计算机将恢复到原来的显示顺序。 |
| /default           | 指定的超时时间到期时，将选择启动管理器的默认项。                                                                                                                                                                  |
| /displayorder      | 指定在向用户显示启动选项时使用的启动管理器的显示顺序。                                                                                                                                                       |
| /timeout           | 指定等待时间，以秒为单位之前启动管理器选择默认项。                                                                                                                                                           |
| /toolsdisplayorder | 指定启动管理器显示工具菜单时使用的显示顺序。                                                                                                                                                              |

 

### <a name="span-idemergencymanagementservicesoptionsspanspan-idemergencymanagementservicesoptionsspanspan-idemergencymanagementservicesoptionsspanemergency-management-services-options"></a><span id="Emergency_Management_Services_options"></span><span id="emergency_management_services_options"></span><span id="EMERGENCY_MANAGEMENT_SERVICES_OPTIONS"></span>紧急管理服务选项

| 选项       | 说明                                                                                                               |
|--------------|---------------------------------------------------------------------------------------------------------------------------|
| /bootems     | 启用或禁用指定项紧急管理服务 (EMS)。                                          |
| /ems         | 启用或禁用指定的操作系统启动项的 EMS。                                                    |
| /emssettings | 设置计算机的全局 EMS 设置。 /emssettings 不会启用或禁用的任何特定启动项目的 EMS。 |

 

### <a name="span-iddebuggingspanspan-iddebuggingspanspan-iddebuggingspandebugging"></a><span id="Debugging"></span><span id="debugging"></span><span id="DEBUGGING"></span>调试

| 选项              | 说明                                                                                                                                                                                                                                                               |
|---------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /bootdebug          | 启用或禁用指定的启动项目的启动调试器。 虽然此命令适用于任何启动项目，就只适合启动应用程序。                                                                                                             |
| /dbgsettings        | 指定或显示系统的全局调试器设置。 此命令不会启用或禁用内核调试程序;为此目的使用 /debug 选项。 若要设置单个全局调试器设置，使用 bcdedit /setdbgsettings type 值命令。 |
| /debug              | 启用或禁用内核调试程序，以便指定的启动项目。                                                                                                                                                                                                       |
| /hypervisorsettings | 设置虚拟机监控程序参数。                                                                                                                                                                                                                                           |

 

若要解决新的安装，请通过修改引导配置文件 (BCD) 启用调试模式。 例如，使用下面的语法来启用内核或启动调试。

``` syntax
bcdedit /set <id> debug on
```

-或者-

``` syntax
bcdedit /set <id> bootdebug on
```

其中&lt;id&gt;是用来加载操作系统的加载程序对象的 GUID。 如果操作系统已启动管理器菜单上的默认选项，则可以使用"默认值"。

BCDEdit 的示例，请参见[在 Windows Vista 中的引导配置数据](http://go.microsoft.com/fwlink/?LinkId=69448)。

### <a name="span-idremoteeventloggingspanspan-idremoteeventloggingspanspan-idremoteeventloggingspanremote-event-logging"></a><span id="Remote_event_logging"></span><span id="remote_event_logging"></span><span id="REMOTE_EVENT_LOGGING"></span>远程事件日志记录

| 选项         | 说明                                                             |
|----------------|-------------------------------------------------------------------------|
| /eventsettings | 设置全局的远程事件日志参数。                        |
| /event         | 启用或禁用某个操作系统项的远程事件日志记录。 |

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[BCDboot](bcdboot-command-line-options-techref-di.md)

[UEFI 的 BCD 系统存储设置](bcd-system-store-settings-for-uefi.md)

[引导环境的 BCDEdit 命令](https://msdn.microsoft.com/library/windows/hardware/dn653986)

[4gb 调整︰ BCDEdit，Boot.ini](https://msdn.microsoft.com/library/windows/desktop/bb613473.aspx)

[在 Windows Vista 中的引导配置数据](http://go.microsoft.com/fwlink/?LinkId=69448)

 

 




