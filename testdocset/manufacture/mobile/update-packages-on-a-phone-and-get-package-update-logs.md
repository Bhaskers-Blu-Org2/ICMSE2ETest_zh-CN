---
title: "更新设备上的程序包并获取包更新日志"
description: "更新设备上的程序包并获取包更新日志"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: d0594281-56f4-4676-9d00-19b6910ab50f
ms.openlocfilehash: 858ca01b53daa83b54379c320ca957cc93f2630f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="update-packages-on-a-device-and-get-package-update-logs"></a>更新设备上的程序包并获取包更新日志


Windows 驱动程序工具包 (WDK) 包括用于更新程序包 (IUTool.exe) 的设备和设备 (GetDULogs.exe) 中获取包更新日志的工具的工具。 这些工具可以在下，%WPDKCONTENTROOT%\\工具\\bin\\i386。

## <a name="using-iutoolexe-to-update-packages-on-a-device"></a>使用 IUTool.exe 来更新设备上的程序包


IUTool.exe 是一个命令行工具，可用来更新现有的设备上的包或向设备中添加一个新包。 必须以管理员身份打开命令行窗口中使用 IUTool.exe。 IUTool.exe 的命令行语法是以下。

``` syntax
IUTool -p <path to packages>
```

下表介绍的 IUTool.exe 命令行参数。

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
<td><p><strong>-p</strong><em>的包的路径</em></p></td>
<td><p>指定一个或多个软件包更新设备上，或要添加到该设备。 该<em>程序包的路径</em>参数可以具有以下格式︰</p>
<ul>
<li><p>要更新或添加一个软件包，请在开发计算机上指定包的完整路径。</p></li>
<li><p>要更新或添加多个程序包，请在开发计算机上指定包的分号分隔列表。 例如︰</p>
<pre class="syntax" space="preserve"><code>IUTool -p C:\ContosoPackages\Contoso.Device.SampleDriver.spkg;C:\ContosoPackages\Contoso.Device.SampleApplication.spkg</code></pre></li>
<li><p>若要更新或添加的包的整个目录，指定目录的路径。 例如︰</p>
<pre class="syntax" space="preserve"><code>IUTool -p C:\ContosoPackages</code></pre></li>
</ul>
<p></p></td>
</tr>
</tbody>
</table>

 

### <a name="package-versioning"></a>软件包版本

如果设备上已存在指定的程序包，该程序包的新版本必须在设备上当前已经包比更高的版本或更新将失败。 若要指定软件包的版本，使用 PkgGen.exe 的**/version**命令行参数，生成包时。 有关详细信息，请参阅[为包生成器命令行参数](https://msdn.microsoft.com/library/windows/hardware/dn756636)。

## <a name="using-getdulogsexe-to-get-package-update-logs-from-a-device"></a>使用 GetDULogs.exe 从设备获取包更新日志


GetDULogs.exe 是一个命令行工具，可用于从设备获取包更新日志。 必须以管理员身份打开命令行窗口中使用 GetDULogs.exe。 GetDULogs.exe 的命令行语法是以下。

``` syntax
GetDULogs -o <output file path>
```

下表介绍的 GetDULogs.exe 命令行参数。

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
<td><p><strong>-o</strong><em>输出文件路径</em></p></td>
<td><p>要写入日志信息的开发计算机上的文件的完整路径。</p></td>
</tr>
</tbody>
</table>

 

 

 

[发送有关此主题的意见的评论](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_phFlashing\p_phFlashing%5D:%20Update%20packages%20on%20a%20device%20and%20get%20package%20update%20logs%20%20RELEASE:%20%2810/4/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "发送有关此主题的意见的评论")




