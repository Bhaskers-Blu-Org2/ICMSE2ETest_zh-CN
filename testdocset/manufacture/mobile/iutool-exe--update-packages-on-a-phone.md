---
title: "在设备上的 IUTool.exe 更新程序包"
description: "Windows 驱动程序工具包 (WDK) 包含一个工具，用于更新设备上，或向设备中添加新包的包。 (IUTool.exe)。 此工具可在 WPDKCONTENTROOT\\\\工具\\\\bin\\\\i386。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 29B7436A-1F6E-41AF-BBBD-5FBB59669B77
ms.openlocfilehash: b5f315a51776c440ab4dd8d54a50207560116f63
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="iutoolexe-update-packages-on-a-device"></a>IUTool.exe︰ 更新设备上的程序包


Windows 驱动程序工具包 (WDK) 包含一个工具，用于更新设备上，或向设备中添加新包的包。 (IUTool.exe)。 此工具可在下，%WPDKCONTENTROOT%\\工具\\bin\\i386。

## <a name="using-iutoolexe-to-update-packages-on-a-device"></a>使用 IUTool.exe 来更新设备上的程序包


必须以管理员身份打开命令行窗口中使用 IUTool.exe。 IUTool.exe 的命令行语法是以下。

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
<td><p><em>-p 包路径</em></p></td>
<td><p>指定一个或多个软件包更新设备上，或要添加到该设备。 软件包参数的路径可具有以下格式︰</p>
<ul>
<li>要更新或添加一个软件包，请在开发计算机上指定包的完整路径。</li>
<li><p>要更新或添加多个程序包，请在开发计算机上指定包的分号分隔列表。 例如︰</p>
<pre class="syntax" space="preserve"><code>IUTool -p C:\ContosoPackages\Contoso.Device.SampleDriver.spkg;C:\ContosoPackages\Contoso.Device.SampleApplication.spkg</code></pre></li>
<li><p>若要更新或添加的包的整个目录，指定目录的路径。 例如︰</p>
<pre class="syntax" space="preserve"><code>IUTool -p C:\ContosoPackages</code></pre></li>
</ul></td>
</tr>
</tbody>
</table>

 

### <a name="package-versioning"></a>软件包版本

如果设备上已存在指定的程序包，该程序包的新版本必须在设备上当前已经包比更高的版本或更新将失败。 若要指定软件包的版本，使用 PkgGen.exe 的 /version 命令行参数，生成包时。 有关详细信息，请参阅[为包生成器命令行参数](https://msdn.microsoft.com/library/windows/hardware/dn756636)。

### <a name="using-getdulogsexe-to-get-package-update-logs-from-a-device"></a>使用 GetDULogs.exe 从设备获取包更新日志

使用 GetDULogs.exe 从设备获取包更新日志。

``` syntax
GetDULogs -o <output file path>
```

有关详细信息，请参阅[GetDULogs︰ 获取包更新日志](update-packages-on-a-phone-and-get-package-update-logs.md)。

 

 

[发送有关此主题的意见的评论](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_phFlashing\p_phFlashing%5D:%20IUTool.exe:%20Update%20packages%20on%20a%20device%20%20RELEASE:%20%2810/4/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "发送有关此主题的意见的评论")




