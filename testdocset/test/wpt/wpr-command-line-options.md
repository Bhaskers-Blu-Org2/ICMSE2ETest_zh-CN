---
title: "WPR 命令行选项"
description: "WPR 命令行选项"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 3c69c8df-6ce3-49a0-b17f-e2b60016b72a
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: a7f90d462ad753a23e1d69b2ce847eaf0fd1cb56
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wpr-command-line-options"></a>WPR 命令行选项


Windows 性能记录器 (WPR) 提供了一个简单的命令行界面。 记录配置文件中嵌入 WPR 的全部复杂性。

WPR 要求 Windows 7 或更高版本的操作系统。

**语法︰**

**wpr**{**-profiles** \[*&lt;path&gt;* \[ …\] \]  |  **-启动***&lt;参数&gt;* | **-停止***&lt;参数&gt;* | **-取消** | **-状态***&lt;参数&gt;* | **-日志***&lt;参数&gt;* | **-purgecache** | **-帮助***&lt;参数&gt;* | **-profiledetails** | **-disablepagingexecutive**}

以下各节描述了命令行选项︰

-   [配置文件](#profiles)

-   [启动](#start)

-   [停止](#stop)

-   [取消](#cancel)

-   [状态](#status)

-   [Profiledetails](#prodet)

-   [提供程序](#prodet)

-   [Disablepagingexecutive](#disablepagingexec)

-   [日志](#log)

-   [Purgecache](#purge)

-   [备注](#rem)

**请注意**  
如果另一个应用程序记录 （如 Xperf 或使用 NT 内核记录器，如 logman 或 PerfTrace 的应用程序） 的同时，可以从命令行启动 WPR，WPR 未能开始录制，并返回以下错误︰

`The event collector was already running.`

在这种情况下，您必须取消其他记录之前，您可以通过使用 WPR 启动一个新录制。

 

## <a name="profiles"></a>配置文件


使用此选项可以列出录制使用 WPR 配置文件。

**语法︰**

**wpr****-配置文件**\[*&lt;path&gt;*\]

下表描述了可用的参数，可以适用于此选项。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>参数</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>&lt;路径&gt;</em></p></td>
<td><p>若要查看内置的配置文件，请省略参数。</p>
<p>若要列出配置文件定义文件中定义的配置文件，请指定的路径和该文件的名称。</p>
<p>示例：</p>
<p><code>wpr -profiles</code></p>
<p><code>wpr -profiles “c:\Users\User1\Documents\WPR Files\Custom Profiles\CustomProfile1.wprp”</code></p></td>
</tr>
</tbody>
</table>

 

## <a name="start"></a>Start


使用此选项可以通过使用一个或多个配置文件开始录制。

**语法︰**

**wpr-启动***&lt;配置文件&gt;*\] ** \[-启动** &lt; *profilen* &gt; \] \[ **-filemode** \] \[ **-recordtempto** &lt;*临时文件夹路径*&gt;\]\[**-onoffscenario** &lt;*打开 / 过渡类型*&gt; \] \[ **-onoffresultspath** &lt;*跟踪文件保存到的路径*&gt;\]\[**-onoffproblemdescription** &lt;*方案的说明*&gt; \] \[ **-numiterations** &lt;*打开 / 跟踪的迭代次数*&gt;\]

下表描述了可用的参数，可以适用于此选项。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>参数</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>&lt;配置文件&gt;</em>或<em> &lt;profilen&gt;</em></p></td>
<td><p>指定内置的配置文件或用户定义的配置文件的路径。</p>
<p>您可以在单个命令行上指定最多 64 个配置文件。 以下列方式指定每个配置文件︰</p>
<pre class="syntax" space="preserve"><code>&lt;profile&gt; :=&lt;profile_name&gt;[.{light|verbose}] </code></pre></td>
</tr>
<tr class="even">
<td><p><em>&lt;profile_name&gt;</em></p></td>
<td><p>每个配置文件可以定义光或详细的版本中，或两个版本。 如果未指定任何选项，则除非该配置文件中包含仅简版使用详细的版本。 正确的语法，请参阅前面的代码示例为<em>&lt;配置文件&gt;</em>或<em>&lt;profilen&gt;</em>。</p></td>
</tr>
<tr class="odd">
<td><p><em>-filemode</em></p></td>
<td><p>指定在文件模式下完成录制。 （默认的模式是内存）。</p>
<p>通过使用此选项，数据记录到另一个未绑定文件，可以增长的大小，直到填满磁盘。</p></td>
</tr>
<tr class="even">
<td><p><em>-onoffresultspath</em></p></td>
<td><p>跟踪文件保存到的路径。</p></td>
</tr>
<tr class="odd">
<td><p><em>-onoffproblemdescription</em></p></td>
<td><p>方案的说明。</p></td>
</tr>
<tr class="even">
<td><p><em>-onoffscenario</em></p></td>
<td><p>指定打开/关闭过渡的一种类型。 它们是︰ 引导、 FastStartup、 关机、 RebootCycle、 待机或休眠。</p></td>
</tr>
<tr class="odd">
<td><p><em>-numiterations</em></p></td>
<td><p>设置用于<em>打开 /</em>录制的迭代次数。 默认情况下，默认使用内置或自定义的配置文件中的设置。</p></td>
</tr>
</tbody>
</table>

 

## <a name="stop"></a>停止


使用此选项来停止当前录制，并将其保存到由参数指定的文件。

**语法︰**

**wpr****-停止***&lt;file&gt;**&lt;问题描述*&gt;

下表描述了可用的参数，可以适用于此选项。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>参数</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>&lt;文件&gt;</em></p></td>
<td><p>指定事件跟踪日志 (ETL) 文件 WPR 将录制保存。 此参数是必需的。</p></td>
</tr>
<tr class="even">
<td><p><em>&lt;问题说明&gt;</em></p></td>
<td><p>指定的问题说明。 虽然此参数是可选的我们推荐您使用它。</p></td>
</tr>
</tbody>
</table>

 

## <a name="cancel"></a>Cancel


使用此选项将取消当前的录制而不保存记录的数据。 如果没有实例当前处于活动状态，则返回错误。

**语法︰**

**wpr****-取消**

此选项不采用任何参数。

## <a name="status"></a>。


使用此选项可显示有关当前 WPR 录制的状态信息。

**语法︰**

**wpr****-状态**\[*配置文件*\] \[*收集器* \[*的详细信息*\]\]

如果没有录制当前处于活动状态，则显示一条消息 WPR 没有录音。 如果录制当前处于活动状态，并且没有使用参数，将显示以下状态信息︰

`WPR recording is in progress...`

`Time since start        : 00:04:27`

`Dropped event           : 0`

`Logging mode            : Memory`

如果您提供参数与**– 状态**选项，以及特定于该选项的数据显示上面列出的信息。 下表描述了可用的参数，可以适用于此选项。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>参数</th>
<th>说明和示例输出</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>配置文件</em></p></td>
<td><p>此参数列表中当前 WPR 正在使用每个配置文件记录。</p>
<p><strong>示例：</strong></p>
<p><code>Recording system activity using the following set of profiles:</code></p>
<p><code>Profile                 : CPU.Verbose.Memory</code></p></td>
</tr>
<tr class="even">
<td><p><em>收集器</em></p></td>
<td><p>列出收集器的信息。 如果缓冲区已丢失，则列出这些缓冲区。</p>
<p><strong>示例：</strong></p>
<pre class="syntax" space="preserve"><code>Actively recording collectors:

Collector Name          : NT Kernel Logger
Buffer Size (KB)        : 1024
Events Lost             : 0
System Keywords
        CSwitch
        ProcessThread
        SampledProfile
System Stacks
        CSwitch
        SampledProfile

Collector Name          : WPR_initiated_WPR Event Collector
Buffer Size (KB)        : 1024
Events Lost             : 0
Providers
        Microsoft-Windows-Shell-Core: 0x1000000000000: 0x04
        Microsoft-Windows-Win32k: 0x1000000402000: 0xff : Stack
CaptureState Providers on Save
        Microsoft-Windows-Win32k: 0x80000: 0xff</code></pre></td>
</tr>
<tr class="odd">
<td><p><em></em>详细信息</p></td>
<td><p>列出了有关每个收集器的其他信息。</p></td>
</tr>
</tbody>
</table>

 

## <a name="a-href-idprodetaprofiledetails"></a><a href="" id="prodet"></a>Profiledetails


使用此选项可以显示详细的信息的配置文件或配置文件集。 若要指定多个配置文件，请使用以下语法在`profile` *n*指的是每个配置文件的名称。

**语法︰**

`wpr -profiledetails profile1+profile2..+profilen [-filemode] -onoffscenario <OnOff Transition Type>`

## <a name="providers"></a>提供程序


使用此选项可以显示有关提供程序的详细的信息。 提供程序，请参阅公开事件到 Windows 性能记录器 (WPR) 跟踪 Windows 事件 (ETW) 组件。 若要显示有关提供程序的信息，请使用下面的语法在`providers`* * 指的是所有安装已知且已注册的提供程序。

**语法︰**

`wpr -providers`

## <a name="a-href-iddisablepagingexecadisablepagingexecutive"></a><a href="" id="disablepagingexec"></a>Disablepagingexecutive


使用此选项可以指定是否可以驱动程序和内核模式系统代码进行分页到磁盘。 将此选项设置为*on* ，则会阻止分页。
此选项在注册表中设置[DisablePagingExecutive](https://technet.microsoft.com/en-us/library/cc959492.aspx)的值。

**语法︰**

`wpr -disablepagingexecutive <on/off>`

**请注意**  
要正确地捕获事件堆栈上运行 Windows 7 的 64 位系统，应将*disablepagingexecutive*设置为*上*，并且必须重新启动系统，然后启动性能记录。 对于运行 Windows 7 的 32 位系统和运行 Windows 8 或更高版本的所有系统，您可以操作性能录制而不将*disablepagingexecutive*设置为*On*。

 

## <a name="log"></a>Log


使用此选项添加并配置调试日志记录到事件日志。

**语法︰**

**wpr****-日志**{*已启用*|*禁用*|*删除*}

下表描述了可用的参数，可以适用于此选项。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>参数</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>enabled</em></p></td>
<td><p>启用调试日志记录到事件日志。</p></td>
</tr>
<tr class="even">
<td><p><em>禁用</em></p></td>
<td><p>禁用调试日志记录到事件日志。</p></td>
</tr>
<tr class="odd">
<td><p><em>删除</em></p></td>
<td><p>卸载 WPR 调试记录系统中的提供程序清单。</p></td>
</tr>
</tbody>
</table>

 

## <a name="a-href-idpurgeapurgecache"></a><a href="" id="purge"></a>Purgecache


使用此选项可以清除托管的符号缓存。

**语法︰**

**wpr****-purgecache**

此选项不采用任何参数。

## <a name="help"></a>帮助


使用此选项可以在命令提示符窗口中显示联机帮助。

**wpr****-帮助**\[{*日志*|*配置文件*|*profiledetails*\\*disablepagingexecutive*\\*启动*|*状态*|*停止*}\]

下表描述了可用的参数，可以适用于此选项。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>参数</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>取消</em></p></td>
<td><p>介绍了<code>–cancel</code>的命令行参数。 有关详细信息，请参阅[取消](#cancel)。</p></td>
</tr>
<tr class="even">
<td><p><em>disablepagingexecutive</em></p></td>
<td><p>描述<em>– disablepagingexecutive</em>命令行参数。 有关详细信息，请参阅[Disablepagingexecutive](#disablepagingexec)。</p></td>
</tr>
<tr class="odd">
<td><p><em>日志</em></p></td>
<td><p>介绍了<code>-log</code>的命令行参数。 有关详细信息，请参阅[日志](#log)。</p></td>
</tr>
<tr class="even">
<td><p><em>profiledetails</em></p></td>
<td><p>描述<em>– profiledetails</em>命令行参数。 有关详细信息，请参阅[Profiledetails](#prodet)。</p></td>
</tr>
<tr class="odd">
<td><p><em>配置文件</em></p></td>
<td><p>介绍了<code>-profiles</code>的命令行参数。 有关详细信息，请参阅[配置文件](#profiles)。</p></td>
</tr>
<tr class="even">
<td><p><em>提供程序</em></p></td>
<td><p>介绍了<code>-providers</code>的命令行参数。 有关详细信息，请参阅[提供程序](#providers)。</p></td>
</tr>
<tr class="odd">
<td><p><em>purgecache</em></p></td>
<td><p>介绍了<code>–purgecache</code>的命令行参数。 有关详细信息，请参阅[Purgecache](#purge)。</p></td>
</tr>
<tr class="even">
<td><p><em>start</em></p></td>
<td><p>提供了说明<code>-start</code>命令行参数。 有关详细信息，请参阅[启动](#start)。</p></td>
</tr>
<tr class="odd">
<td><p><em>status</em></p></td>
<td><p>提供了说明<code>-status</code>命令行参数。 有关详细信息，请参阅[状态](#status)。</p></td>
</tr>
<tr class="even">
<td><p><em>停止</em></p></td>
<td><p>介绍了<code>-stop</code>的命令行参数。 有关详细信息，请参阅[停止](#stop)</p></td>
</tr>
</tbody>
</table>

 

## <a name="a-href-idremaremarks"></a><a href="" id="rem"></a>备注


WPR 保存托管应用程序在系统上运行时捕获的跟踪每次 WPR 保存托管的符号旁边的跟踪文件。 此功能使托管应用程序的性能分析。

生成托管的符号是资源-和时间-耗时的操作。 WPR 自动创建托管的符号缓存来加快生成托管符号。 当 WPR 需要托管的符号时，它首先检查此缓存，并使用所有可用和适当的符号，而不是重新生成它们。

管理默认符号缓存位置为 c:\\ProgramData\\WindowsPerformanceRecorder\\NGenPdbs\_高速缓存。

## <a name="related-topics"></a>相关的主题


[WPR 引用](wpr-reference.md)

 

 







