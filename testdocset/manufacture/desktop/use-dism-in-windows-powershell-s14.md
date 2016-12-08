---
author: Justinha
Description: "使用 DISM 中 Windows PowerShell"
ms.assetid: c258fead-059f-4a03-b6af-24cdc7451ca3
MSHAttr: PreferredLib:/library/windows/hardware
title: "使用 DISM 中 Windows PowerShell"
ms.openlocfilehash: 076b603410d23827606747c645dee141056588c1
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="use-dism-in-windows-powershell"></a>使用 DISM 中 Windows PowerShell


部署映像服务和管理 (DISM) cmdlet 可以用于执行相同的功能作为 DISM.exe 命令行工具。 在许多情况下，DISM cmdlet 名称直接对应 Dism.exe 选项，可使用相同的参数。 由于还没有在 DISM cmdlet 名称并不直接对应 Dism.exe 选项的情况下，此处提供了将 Dism.exe 命令映射到 DISM cmdlet 的表︰

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Dism.exe 命令</th>
<th align="left">DISM cmdlet</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Dism.exe /Add-Capability</p></td>
<td align="left"><p>添加 WindowsCapability</p></td>
</tr>
<tr class="even">
<td align="left"><p>Dism.exe /Append-Image</p></td>
<td align="left"><p>添加 WindowsImage</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Dism.exe /Apply-Image</p></td>
<td align="left"><p>展开 WindowsImage</p></td>
</tr>
<tr class="even">
<td align="left"><p>Dism.exe /Capture-Image</p></td>
<td align="left"><p>新 WindowsImage</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Dism.exe /Cleanup-MountPoints</p></td>
<td align="left"><p>清除-WindowsCorruptMountPoint</p></td>
</tr>
<tr class="even">
<td align="left"><p>Dism.exe /Commit-Image</p></td>
<td align="left"><p>保存-WindowsImage</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Dism.exe /Export-Image</p></td>
<td align="left"><p>导出 WindowsImage</p></td>
</tr>
<tr class="even">
<td align="left"><p>Dism.exe /Get-Capabilities</p></td>
<td align="left"><p>获得 WindowsCapability</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Dism.exe /Get-ImageInfo</p></td>
<td align="left"><p>获得 WindowsImage</p></td>
</tr>
<tr class="even">
<td align="left"><p>Dism.exe /Get-MountedImageInfo</p></td>
<td align="left"><p>获取 WindowsImage 的安装</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Dism.exe /Get-WimBootEntry</p></td>
<td align="left"><p>获得 WIMBootEntry</p></td>
</tr>
<tr class="even">
<td align="left"><p>Dism.exe /List-Image</p></td>
<td align="left"><p>获得 WindowsImageContent</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Dism.exe /Mount-Image</p></td>
<td align="left"><p>装入 WindowsImage</p></td>
</tr>
<tr class="even">
<td align="left"><p>Dism.exe /Split-Image</p></td>
<td align="left"><p>拆分 WindowsImage</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Dism.exe /Remove-Capability</p></td>
<td align="left"><p>删除 WindowsCapability</p></td>
</tr>
<tr class="even">
<td align="left"><p>Dism.exe /Remove-Image</p></td>
<td align="left"><p>删除 WindowsImage</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Dism.exe /Remount-Image</p></td>
<td align="left"><p>装入 WindowsImage-重新安装</p></td>
</tr>
<tr class="even">
<td align="left"><p>Dism.exe /Unmount-Image</p></td>
<td align="left"><p>卸除 WindowsImage</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Dism.exe /Update-WimBootEntry</p></td>
<td align="left"><p>更新 WIMBootEntry</p></td>
</tr>
<tr class="even">
<td align="left"><p>Dism.exe /Image:&lt;...&gt; / 添加驱动程序</p></td>
<td align="left"><p>添加 WindowsDriver</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Dism.exe /Image:&lt;...&gt; /Add-Package</p></td>
<td align="left"><p>添加 WindowsPackage</p></td>
</tr>
<tr class="even">
<td align="left"><p>Dism.exe /Image:&lt;...&gt; /Add-ProvisionedAppxPackage</p></td>
<td align="left"><p>添加 AppxProvisionedPackage</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Dism.exe /Image:&lt;...&gt; /Apply-Unattend</p></td>
<td align="left"><p>应用 WindowsUnattend</p></td>
</tr>
<tr class="even">
<td align="left"><p>Dism.exe /Image:&lt;...&gt; /Cleanup-Image /CheckHealth</p></td>
<td align="left"><p>修复-WindowsImage CheckHealth</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Dism.exe /Image:&lt;...&gt; /Cleanup-Image /ScanHealth</p></td>
<td align="left"><p>修复-WindowsImage ScanHealth</p></td>
</tr>
<tr class="even">
<td align="left"><p>Dism.exe /Image:&lt;...&gt; /Cleanup-Image /RestoreHealth</p></td>
<td align="left"><p>修复-WindowsImage RestoreHealth</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Dism.exe /Image:&lt;...&gt; /Disable-Feature</p></td>
<td align="left"><p>禁用-WindowsOptionalFeature</p></td>
</tr>
<tr class="even">
<td align="left"><p>Dism.exe /Image:&lt;...&gt; /Enable-Feature</p></td>
<td align="left"><p>启用 WindowsOptionalFeature</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Dism.exe /Image:&lt;...&gt; /Export-Driver</p></td>
<td align="left"><p>导出 WindowsDriver</p></td>
</tr>
<tr class="even">
<td align="left"><p>Dism.exe /Image:&lt;...&gt; /Get-CurrentEdition</p></td>
<td align="left"><p>获取 WindowsEdition 的当前</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Dism.exe /Image:&lt;...&gt; /Get-Driverinfo</p></td>
<td align="left"><p>获取 WindowsDriver 的驱动程序</p></td>
</tr>
<tr class="even">
<td align="left"><p>Dism.exe /Image:&lt;...&gt; /Get-Drivers</p></td>
<td align="left"><p>获得 WindowsDriver</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Dism.exe /Image:&lt;...&gt; /Get-Featureinfo</p></td>
<td align="left"><p>获得 WindowsOptionalFeature 功能名</p></td>
</tr>
<tr class="even">
<td align="left"><p>Dism.exe /Image:&lt;...&gt; /Get-Features</p></td>
<td align="left"><p>获得 WindowsOptionalFeature</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Dism.exe /Image:&lt;...&gt; /Get-Packageinfo</p></td>
<td align="left"><p>获得 WindowsPackage PackagePath |软件包的名称</p></td>
</tr>
<tr class="even">
<td align="left"><p>Dism.exe /Image:&lt;...&gt; /Get-Packages</p></td>
<td align="left"><p>获得 WindowsPackage</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Dism.exe /Image:&lt;...&gt; /Get-ProvisionedAppxPackages</p></td>
<td align="left"><p>获得 AppxProvisionedPackage</p></td>
</tr>
<tr class="even">
<td align="left"><p>Dism.exe /Image:&lt;...&gt; /Get-TargetEditions</p></td>
<td align="left"><p>获取 WindowsEdition 的目标</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Dism.exe /Image:&lt;...&gt; /Optimize-Image</p></td>
<td align="left"><p>优化 WindowsImage</p></td>
</tr>
<tr class="even">
<td align="left"><p>Dism.exe /Image:&lt;...&gt; /Remove-Driver</p></td>
<td align="left"><p>删除 WindowsDriver</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Dism.exe /Image:&lt;...&gt; /Remove-Package</p></td>
<td align="left"><p>删除 WindowsPackage</p></td>
</tr>
<tr class="even">
<td align="left"><p>Dism.exe /Image:&lt;...&gt; /Remove-ProvisionedAppxPackage</p></td>
<td align="left"><p>删除 AppxProvisionedPackage</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Dism.exe /Image:&lt;...&gt; /Set-Edition</p></td>
<td align="left"><p>一组 WindowsEdition</p></td>
</tr>
<tr class="even">
<td align="left"><p>Dism.exe /Image:&lt;...&gt; /Set-ProductKey</p></td>
<td align="left"><p>一组 WindowsProductKey</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Dism.exe /Image:&lt;...&gt; /Set-ProvisionedAppxDataFile</p></td>
<td align="left"><p>一组 AppXProvisionedDataFile</p></td>
</tr>
</tbody>
</table>

 

**安装 Windows 评估和部署工具包 （可选）**

-   DISM PowerShell 模块包含在 Windows 10 和 Windows 服务器 2016年技术预览。 其他受支持的操作系统，您可以安装的 Windows 评估和部署工具包 (ADK)，它包括 DISM PowerShell 模块。

**安装 Windows PowerShell 5.0**

-   对于 Windows 10 和 Windows 服务器 2016年技术预览，Windows Powershell 5.0 包含在安装中。 其他支持旧版 Windows 和 Windows 服务器，您必须安装 Windows 管理框架 5.0。 您可以从下载并安装[Windows 管理框架 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) Microsoft 下载中心。

**若要准备 DISM PowerShell 环境**

1.  打开具有管理员权限，请在**启动**屏幕上，PowerShell 键入**PowerShell**，用鼠标右键单击**Windows PowerShell**应用程序图块，然后在应用程序栏中，单击**以管理员身份运行**。

2.  DISM PowerShell 模块中导入。

    DISM PowerShell 模块包含在 Windows 10 和 Windows 服务器 2016年技术预览，并不需要导入。

    其他受支持的操作系统，可以使用包含在 Windows ADK DISM PowerShell 模块。 默认情况下，使用 Windows ADK 在 DISM 文件夹中安装模块*&lt;x86 或 amd64&gt;*\\DISM\\路径下︰ c:\\程序文件 (x86)\\窗口工具包\\10.0\\评估和部署工具包\\部署工具\\窗口 10 中。 若要导入此模块，在命令提示符下，键入︰

    ``` syntax
    import-module <path to DISM folder>
    ```

    例如，在 64 位计算机类型上使用 Windows ADK 的 Windows 10 版本︰

    ``` syntax
    import-module "C:\Program Files (x86)\Windows Kits\10.0\Assessment and Deployment Kit\Deployment Tools\amd64\DISM"
    ```

    **请注意**  
    **导入模块**模块导入到当前会话。 要导入的所有会话的模块，添加到 PowerShell 配置文件**导入模块**的命令。 有关配置文件的详细信息，请键入`get-help about_profiles`。

     

3.  设置`%path%`环境变量到 DISM 在 ADK Windows 安装文件夹的位置。 在命令提示符下，键入︰

    ``` syntax
    $env:path = <path to DISM folder>
    ```

    更改环境变量 PowerShell 中的时，更改将影响只对当前会话。 要永久性更改存储在注册表中更改环境变量，使用控制面板中的系统。 有关详细信息，请参阅[添加或更改环境变量的值](http://go.microsoft.com/fwlink/?LinkId=223710)。

**若要获取有关 DISM PowerShell cmdlet 的帮助**

-   若要获取的语法使用的 cmdlet，请在命令提示符处，键入︰

    ``` syntax
    get-help <cmdlet name>
    ```

    例如，键入︰

    ``` syntax
    get-help get-WindowsImage
    ```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[DISM 的部署 windows 映像服务和管理技术参考](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md)

[DISM 支持的平台](dism-supported-platforms.md)

 

 






