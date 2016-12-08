---
title: "使用由 Microsoft 提供的闪烁工具"
description: "使用由 Microsoft 提供的闪烁工具"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: deb8960a-18b0-447d-ba6d-5611def266c0
ms.openlocfilehash: 9ab519b802b4a35907605a97fcd573f2fb588b58
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="use-the-flashing-tools-provided-by-microsoft"></a>使用由 Microsoft 提供的闪烁工具


Microsoft 提供的闪烁图像设备设置的工具。 该工具组包括 ffutool.exe，在开发计算机运行一个命令行工具和 ffuloader.efi，闪烁应用程序设备端 （uefi)。 本主题介绍如何设置您的设备和开发计算机以使用该工具设置，并提供了使用说明。

**重要**  
-   在第 10 Windows 版本 1607，通过评估和部署工具包 (ADK) 安装了 ffutool.exe。 在早期版本的 Windows 10，ffutool.exe 被安装的 Windows 驱动程序工具包 (WDK)、 企业 WDK (EWDK) 或 Windows 硬件实验室工具包 (HLK)。

-   设备端 UEFI 闪烁应用程序从 Microsoft 自动纳入所有图像。 此应用程序必须包含所有零售设备中。

-   对于在制造闪烁图像设备，Oem 可以生产自己闪烁的工具通过[开发自定义 OEM 闪烁工具](developing-custom-oem-flashing-tools.md)中提供的信息，或使用 ffutool.exe。 如果您使用 ffutool 闪存映像，则可能是低于其他闪烁的工具。

 

## <a name="a-href-idinitialdevicesidesetupainitial-device-side-setup"></a><a href="" id="initialdevicesidesetup"></a>设备端的初始设置


若要准备一台设备与 Windows 10 移动图像闪烁，请执行以下步骤︰

1.  SoC 供应商提供的工具可用于获取到需要刷新任何设备 （uefi）。 设备必须是可引导至少到闪烁的 UEFI 工作。

    通常情况下，这被执行 eMMC 软件下载程序。 此 UEFI 应包括在设备图像相同 （uefi）。

2.  可引导 UEFI 的位置后，必须添加到设备并启动运行闪烁的应用程序 (ffuloader.efi) 和支持简单的 I/O 驱动程序 (efisimpleio.dll)。 若要执行此操作，请设备连接到开发计算机时运行应用 ffubinaries.bat 脚本。 所有这些文件提供的套件在 %programfiles(x86)%\\窗口工具包\\10\\工具\\bin\\i386。

    应用 ffubinaries.bat 脚本将 ffuloader.efi 和 efisimpleio.dll 复制到设备上的 ESP 目录的根，并将启动配置数据库设置为立即启动输入闪烁模式。 该脚本需要使用 bcdedit.exe 的路径中。

**请注意**  
这些步骤只需要一次执行的每个设备。 完成以上步骤后，您将能够闪存设备不同的图像

 

## <a name="a-href-idhostsidesetupahost-side-setup"></a><a href="" id="hostsidesetup"></a>主机端安装


在主机端上的闪烁被通过使用与 WinUSB，Microsoft 通用 USB 设备驱动程序建立连接。 默认情况下，在 Windows 8 及更高版本包含必要的驱动程序。

在 Windows 7 中，可以从 Windows Update 安装必要的驱动程序。 要配置 Windows 7 计算机来安装必要的驱动程序︰

1.  单击开始。

2.  **设备安装设置**的类型。

3.  选择**是，这样做会自动 （推荐）**。

4.  单击**保存更改**。

## <a name="a-href-idflashingprocedureaflashing-procedure"></a><a href="" id="flashingprocedure"></a>闪烁的过程


设备端和主机端安装完毕后，请执行以下步骤以闪存设备︰

1.  连接到主机时，该设备引导至 FFU 下载模式。 有几种方法可以在启动过程中强制进入 FFU 下载模式的设备︰

    -   通过指定**LABIMAGE**可选功能，生成测试图像时，图像中包括 Microsoft.BCD.Lab.spkg 软件包。 当测试图像中包含此包时，设备将在它启动时，自动进入 FFU 下载模式。 有关生成图像的详细信息，请参阅[构建使用 ImgGen.cmd 电话映像](building-a-phone-image-using-imggencmd.md)。

    -   若要手动强制到 FFU 下载模式的设备，请按下并松开电源按钮可启动设备，然后立即按下并保持向上按钮卷。 仅在初始 FFU 已经刷新到设备后，此选项才可用。

2.  Ffutool.exe 从命令行运行以闪烁图像。 此程序在 %programfiles(x86)%\\窗口工具包\\10\\工具\\bin\\i386。 以下是用法示例。

    ``` syntax
    ffutool -flash <FFU file>
    ```

    下表介绍了用于 ffutool.exe 的命令行参数。

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
    <td><p><strong>-闪存</strong><em>FFU 文件</em></p></td>
    <td><p>指定刷新为设备的 FFU 文件的路径。</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>-跳过</strong></p></td>
    <td><p>对于包含自动引导至 FFU 下载模式<strong>LABIMAGE</strong>可选功能的设备，此参数将引导至主操作系统 （跳过 FFU 下载模式）。</p></td>
    </tr>
    </tbody>
    </table>

     

通过使用 ffutool.exe，可以一次闪烁多个设备。 若要执行此操作，请确保所有设备都连接前运行 ffutool.exe。 此外，我们建议使用所以闪烁一台设备出现问题不会影响所有设备包含每个端口的专用的根集线器的 USB 卡。

**请注意**  
闪烁速度会降低添加设备。

 

## <a name="a-href-idvalidatingplatformidavalidations-performed-by-the-microsoft-flashing-tool"></a><a href="" id="validatingplatformid"></a>由 Microsoft 闪烁工具执行的验证


在闪烁的图像之前, 设备端 UEFI 闪烁应用程序由 Microsoft 提供的图像上执行下面的验证︰

-   应用程序将验证映像签名与平台键 (PK) 证书和 Microsoft Windows Phone 生产 PCA 2012 证书 （用于零售图像） 或 Microsoft 测试根颁发机构证书 （用于非零售图像）。

-   应用程序将验证每个块的图像对签名的编录文件的哈希表中的数据的哈希。

-   应用程序将验证图像支持当前的设备平台。 若要执行此验证，应用程序将 SMBIOS 系统信息结构中，设备平台软件包中的相应值的多个值进行比较。 这些检查帮助确保图像可以刷新为特定的设备中，只有当它构建相应的设备平台。 关于这些检查的详细信息如下。

### <a name="device-platform-validation-checks"></a>设备平台验证检查

若要验证图像支持前闪烁当前的设备平台，应用程序可以执行以下任务︰

1.  它从图像中刷新的设备平台包中检索**DevicePlatformID**字符串。 有关此字符串的详细信息，请参阅[设置设备平台信息](set-device-platform-information.md)。

2.  如果该字符串有*制造商*的格式。*家族*。*产品名称*。*版本*和平台验证在设备上相应的*制造商*、*家族*、*产品名称*和*版本*SMBIOS 值成功字符串匹配和闪烁的操作中的所有四个值将继续进行。

3.  如果该字符串有*制造商*的格式。*家族*。*产品名称*和相应的*制造商*、*家族*和*产品名称*SMBIOS 值在设备上，平台验证成功的匹配字符串和闪烁的操作中的所有三个值将继续进行。

4.  否则为平台验证将失败，并且图像不刷新为设备。

在非零售图像中，Oem 可以通过添加禁用禁用闪烁的设备平台验证\_FFU\_PLAT\_ID\_OEMInput 文件用于生成图像的检查功能。

**重要**  
必须禁用零售图像中闪烁的设备平台验证。

 

## <a name="ffu-tool-error-codes"></a>FFU 工具错误代码


使用 FFU 工具时闪到您的设备图像，您可能会遇到错误，如下所示。

``` syntax
Error: Failed to flash with device error { 0x18, 0x0, 0x0, 0x2, 0xa, 0x5 }
```

第一个十六进制数是故障的指示闪烁类型的事件代码。 下表提供了 FFU 工具闪烁错误的说明。

**常见的错误**

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
<td><p>0xC</p></td>
<td><p>在图像应用到磁盘时，读取失败返回所有当前数据描述符中指定的块。</p>
<p>此错误通常会导致损坏的图像。 图像通常需要重建。 有关详细信息，请参阅[构建使用 ImgGen.cmd 电话映像](building-a-phone-image-using-imggencmd.md)。</p></td>
</tr>
<tr class="even">
<td><p>0x18</p></td>
<td><p>在初始化哈希检查，编录签名检查失败。</p>
<p>发生此错误时，它通常与对签名的图像。 有关详细信息，请参阅[注册全闪存更新 (FFU) 图像](sign-a-full-flash-update--ffu--image.md)。</p></td>
</tr>
<tr class="odd">
<td><p>0x1C</p></td>
<td><p>无效磁盘位置引用一个或多个写入说明符。</p>
<p>此错误通常指示图像立志为与存储空间超过当前电话实际上有一部电话。 找到正确的图像，或者更新可以通过减少 MinSectorCount 在 OEMDevicePlatform.xml 中指定的图像。 有关详细信息，请参阅[设置设备平台信息](set-device-platform-information.md)。</p></td>
</tr>
</tbody>
</table>

 

**其他错误**

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
<td><p>0x8</p></td>
<td><p>无效的二进制清单标头时准备闪存设备读取。</p></td>
</tr>
<tr class="even">
<td><p>0x9</p></td>
<td><p>应用程序无法分配足够的内存来复制磁盘写入描述符表。</p></td>
</tr>
<tr class="odd">
<td><p>0xB</p></td>
<td><p>然后再写入数据，闪烁的应用程序无法读取所有磁盘写入说明符。</p></td>
</tr>
<tr class="even">
<td><p>0xD</p></td>
<td><p>在图像应用到磁盘时，块写操作失败。</p></td>
</tr>
<tr class="odd">
<td><p>0xE</p></td>
<td><p>闪烁的应用程序读取的数据包包含有效的校验和。</p></td>
</tr>
<tr class="even">
<td><p>0xF</p></td>
<td><p>在准备图像闪烁，闪烁的应用程序时无法读取完整安全标头。</p></td>
</tr>
<tr class="odd">
<td><p>0x10</p></td>
<td><p>同时准备闪烁图像，闪烁的应用程序中读取无效安全标头。</p></td>
</tr>
<tr class="even">
<td><p>0x11</p></td>
<td><p>同时准备闪烁图像，闪烁的应用程序无法读取预期的安全标头之后的空白量。</p></td>
</tr>
<tr class="odd">
<td><p>0x12</p></td>
<td><p>同时准备闪烁图像，闪烁的应用程序中读取无效映像标头。</p></td>
</tr>
<tr class="even">
<td><p>0x13</p></td>
<td><p>同时准备闪烁图像，闪烁的应用程序无法读取填充图像标题后的预期的数额。</p></td>
</tr>
<tr class="odd">
<td><p>0x14</p></td>
<td><p>当准备将映像应用到磁盘时，块 flasher 无法缓冲区足够安全地闪烁的流中的字节数。</p></td>
</tr>
<tr class="even">
<td><p>0x15</p></td>
<td><p>同时应用到磁盘映像，块 flasher 意外到达流的末尾。 这表明未正确生成了映像。</p></td>
</tr>
<tr class="odd">
<td><p>0x16</p></td>
<td><p>在图像中指定平台 ID 与要刷新的设备 ID 不匹配。</p></td>
</tr>
<tr class="even">
<td><p>0x17</p></td>
<td><p>读取图像数据，而哈希检查失败。</p></td>
</tr>
<tr class="odd">
<td><p>0x1A</p></td>
<td><p>无法获取 UEFI 固件消除同步事件的句柄。</p></td>
</tr>
<tr class="even">
<td><p>0x1B</p></td>
<td><p>未能查询平台 ID 检查设置的 BCD。</p></td>
</tr>
<tr class="odd">
<td><p>0x1D</p></td>
<td><p>图像没有启用重置保护或使用了不支持重置保护图像。</p></td>
</tr>
<tr class="even">
<td><p>0x20</p></td>
<td><p>不能将图像刷新可移动媒体上。</p></td>
</tr>
<tr class="odd">
<td><p>0x21</p></td>
<td><p>不能使用优化闪烁的方法。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[构建和闪烁的图像](building-and-flashing-images.md)

 

 

[发送有关此主题的意见的评论](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_phFlashing\p_phFlashing%5D:%20Use%20the%20flashing%20tools%20provided%20by%20Microsoft%20%20RELEASE:%20%2810/4/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "发送有关此主题的意见的评论")





