---
title: "设置设备平台信息"
description: "了解如何构建图像，可以刷新到移动设备，在图像最终零售设备包括合作伙伴名称、 版本号和设备名称，例如附加的设备平台信息的先决条件。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 3bf177d9-fd4a-4221-958b-ed98e5bd4e70
ms.openlocfilehash: 2261e7ef0bd9c0a929a9b4fc83f39e680db4be4f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="set-device-platform-information"></a>设置设备平台信息


若要准备构建映像，Oem 必须执行以下任务来指定目标的设备平台所需的信息︰

-   在设备上 SMBIOS 系统信息结构中设置多个设备平台值。

-   生成*设备平台*软件包。

闪烁由 Microsoft 提供的工具集工程前闪烁图像比较 SMBIOS 系统信息结构中的值与设备平台软件包中的相应值。 这一检查可以帮助确保图像可以刷新为特定的设备中，只有当它构建相应的设备平台。 建议 Oem 制造环境的创建闪烁工具相同的验证。 有关详细信息，请参阅本主题中的[验证前闪烁到设备的图像的设备平台信息](#validating)。

**请注意**  
本主题介绍构建图像，可以刷新设备为先决条件的。 Oem 必须设置附加的设备平台信息在图像最终零售设备包括合作伙伴名称、 版本号和设备名称。

 

## <a name="a-href-idsetting-smbios-system-information-values-asetting-smbios-system-information-values"></a><a href="" id="setting-smbios-system-information-values-"></a>设置 SMBIOS 系统信息值


在每个设备平台上，Oem 必须确保设置 SMBIOS 系统信息结构中的以下值︰

-   PhoneManufacturer

-   系列

-   产品名称

-   版本

这些值可以设置为默认值由 SoC 的供应商;Oem 必须将这些与他们的设备平台的值替换。 Oem 可能还需要设置其他 SMBIOS 值所指定的 SoC 供应商。 有关如何设置或读取这些值的详细信息，请参阅 SoC 供应商提供的文档。

有关预期的大小和数据类型，这些值的详细信息，请参阅[系统管理 BIOS (SMBIOS) 参考技术指标](http://go.microsoft.com/fwlink/?LinkId=267529)(PDF) 中的部分 7.2。

**重要**  
PhoneManufacturer 设置必须包含由 Microsoft 对应于 OEM 指定的代码。 此设置用于设备更新、 用于连接到存储-在-一-存储在 Windows 应用商店，以及 Watson 报告。 该值必须是有效的 OEM id。 若要获取适用于您有效 OEM 标识，请联系您的 Microsoft 代表联系。

 

## <a name="creating-the-device-platform-package"></a>创建设备平台软件包


设备平台包中包含一个文件︰ XML 文件命名为**OEMDevicePlatform.xml** ，其中包括为其生成图像的设备平台的特定信息。 每个图像必须包含设备平台软件包。 Oem 必须在 FM 文件包括在映像中使用 OEMDevicePlatformPackages 元素来指定设备平台包。

若要创建设备平台软件包，请首先创建 OEMDevicePlatform.xml 文件，其中包含所需的架构格式的设备平台信息。 然后，创建一个包，其中包含该 XML 文件。

### <a name="creating-the-xml-file"></a>创建 XML 文件

OEMDevicePlatform.xml 文件中包含一个**OEMDevicePlatform**元素具有以下子元素。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>元素</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>MinSectorCount</strong></p></td>
<td><p>此值指定应在存储设备的小扇区。 成像工具使用此值来确保内容适合在设备上。 实际的扇区计数可能不超过此最小值。 扇区大小为 512 字节，由 Microsoft 提供的设备布局包中定义。</p></td>
</tr>
<tr class="even">
<td><p><strong>DevicePlatformID</strong></p></td>
<td><p>这是从 SMBIOS 系统信息结构连接在一起，由句点 （.） 分隔每个值的值组成的下列字符串之一︰</p>
<ul>
<li><p><em>PhoneManufacturer</em>。<em>家族</em>。<em>产品名称</em></p></li>
<li><p><em>PhoneManufacturer</em>。<em>家族</em>。<em>产品名称</em>。<em>版本</em></p></li>
</ul>
<p>Oem 可以选择在此字符串中包含的<em>版本</em>值。</p>
<p>在 Microsoft 中闪烁应用程序启用设备平台验证时，此字符串中指定的值将与 SMBIOS 系统信息结构中的相应值进行比较。 有关详细信息，请参阅[的使用由 Microsoft 提供的闪烁的工具](use-the-flashing-tools-provided-by-microsoft.md)。</p>
<p>设备平台 XML 文件可以仅包含<strong>DevicePlatformID</strong>或<strong>DevicePlatformIDs</strong>元素，但不是能同时。</p></td>
</tr>
<tr class="odd">
<td><p><strong>DevicePlatformIDs</strong></p></td>
<td><p>Oem 可以使用下面的 XML 语法，其中每个字符串具有相同的格式为<strong>DevicePlatformID</strong>元素所述平台 Id 设置多个设备。</p>
<pre class="syntax" space="preserve"><code>&lt;DevicePlatformIDs&gt;
   &lt;ID&gt;Contoso.ContosoPhoneFamily.Z101._012&lt;/ID&gt;
   &lt;ID&gt;Contoso.ContosoPhoneFamily.Z101._013&lt;/ID&gt;
   &lt;ID&gt;Contoso.ContosoPhoneFamily.Z102&lt;/ID&gt;
&lt;/DevicePlatformIDs&gt;</code></pre>
<p>如果任何 Id 匹配指定 PhoneManufacturer.Family.Product 或 PhoneManufacturer.Family.Product.Version，设备平台验证将会成功。</p>
<p>设备平台 XML 文件可以仅包含<strong>DevicePlatformID</strong>或<strong>DevicePlatformIDs</strong>元素，但不是能同时。</p></td>
</tr>
<tr class="even">
<td><p><strong>AdditionalMainOSFreeSectorsRequest</strong></p></td>
<td><p>可选项。 此值指定要添加到保留用以未来更新使用操作系统的存储池的扇区数。 不能保证使用<strong>AdditionalMainOSFreeSectorsRequest</strong>元素所指定的扇区将始终可供 OEM 特定更新;扇区改为添加到单个保留来自 Microsoft 和 Oem 的所有更新的存储池。</p></td>
</tr>
<tr class="odd">
<td><p><strong>MainOSRTCDataReservedSectors</strong></p></td>
<td><p>可选项。 此值指定要添加到池中的存储在备份和还原操作期间由运行时配置数据保留用于操作系统的扇区数。 可以保留最多 100 MB。</p>
<p>下面的示例演示如何保留 50 MB。</p>
<pre class="syntax" space="preserve"><code>&lt;MainOSRTCDataReservedSectors&gt;102400&lt;/MainOSRTCDataReservedSectors&gt;</code></pre></td>
</tr>
<tr class="even">
<td><p><strong>CompressedPartitions</strong></p></td>
<td><p>可选项。 使用此元素启用移动图像中的 CompactOS。</p>
<p>此元素包含一个或多个指定要压缩的分区的子<strong>名称</strong>元素。 目前，唯一受支持的分区是主操作系统分区中，并在此元素下唯一受支持的值是<strong>MainOS</strong>，如下面的示例中所示。</p>
<pre class="syntax" space="preserve"><code>&lt;CompressedPartitions&gt;
  &lt;Name&gt;MainOS&lt;/Name&gt;
&lt;/CompressedPartitions&gt;</code></pre>
<div class="alert">
<strong>重要</strong> 在其中创建该图像的主机都必须运行 Windows 10。 您还可以在运行 Windows 8.1 的主机计算机上创建图像或安装 Windows Server 2012 R2 与[KB3066427](https://support.microsoft.com/kb/3066427) 。
</div>
<div>
 
</div></td>
</tr>
</tbody>
</table>

 

下面的示例演示一个 OEMDevicePlatform.xml 文件。

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<OEMDevicePlatform xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
   xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
   xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate">
   <MinSectorCount>20971520</MinSectorCount>
   <DevicePlatformID>Contoso.ContosoFamily.ContosoDevice.v1</DevicePlatformID>
   <AdditionalMainOSFreeSectorsRequest>204800</AdditionalMainOSFreeSectorsRequest>
</OEMDevicePlatform>
```

### <a name="creating-the-package"></a>创建程序包

若要创建一个包，其中包含的 OEMDevicePlatform.xml 文件，请按照[创建包](creating-mobile-packages.md)中的指导。 下面的示例演示设备平台 XML 文件指定一个单一的设备平台 id。

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<Package xmlns="urn:Microsoft.WindowsPhone/PackageSchema.v8.00"
   Owner="OEMName" OwnerType="OEM" Component="OEMDevicePlatform" 
   ReleaseType="Production" Platform="DeviceName">
   <Components>
      <OSComponent>
         <Files>
            <File Source="OEMDevicePlatform.xml" DestinationDir="$(runtime.windows)\ImageUpdate" 
                  Name="OEMDevicePlatform.xml"/>
         </Files>
      </OSComponent>
   </Components>
</Package>
```

请注意有关此示例的以下详细信息︰

-   请确保"*OEMName*"和"*设备名称*"条目替换为适当的值。

-   `$(runtime.windows)` **DestinationDir**属性全局定义的宏在路径中的字符串。 **DestinationDir**路径必须以全局定义宏目录开始。 有关**DestinationDir**属性的详细信息，请参阅[指定文件和包项目文件中的注册表项](https://msdn.microsoft.com/windows/hardware/dn789219)。 有关宏的详细信息，请参阅[主元素和包的项目文件的属性](https://msdn.microsoft.com/library/windows/hardware/dn756796)。

**在映像中包括的设备平台软件包**

创建设备平台包后，必须指定使用的功能清单文件中的 OEMDevicePlatformPackages 元素。 有关详细信息，请参阅[功能清单文件的内容](feature-manifest-file-contents.md)。

## <a name="a-href-idvalidatingavalidating-the-device-platform-information-before-flashing-an-image-to-a-device"></a><a href="" id="validating"></a>验证前闪烁到设备的图像的设备平台信息


为了帮助确保图像将要刷新为设备为该设备实际设计，闪烁的工具集，由 Oem 应该检查*制造商*、*家族*和*产品名称*SMBIOS 系统信息结构值在设备上的并*制造商*对这些值进行比较。*家族*。*产品名称*的设备平台包中的**DevicePlatformID**字符串的一部分。 闪烁的工具应该这些值匹配时才继续闪烁的过程。 闪烁的工具也可以验证，也匹配的*版本*值，但这不是必需。 有关详细信息，请参阅[开发自定义 OEM 闪烁工具](developing-custom-oem-flashing-tools.md)。

默认情况下，设备端 UEFI 闪烁由 Microsoft 提供的应用程序验证中 SMBIOS 的设备平台信息匹配图像中的设备平台信息。 有关详细信息，请参阅[的使用由 Microsoft 提供的闪烁的工具](use-the-flashing-tools-provided-by-microsoft.md)。

需要将电话迁移到一套新的设备平台值时，Microsoft 建议以下过程︰

-   生成包含新 SMBIOS 值但仍引用旧设备平台软件包中的**DevicePlatformID**字符串的转换图像。

-   刷新此图像的移动电话。 此过程将覆盖新 SMBIOS 面额的电话 SMBIOS 值。

-   在图像定义中，更新设备平台软件包以匹配新的 SMBIOS 值中的**DevicePlatformID**字符串。 这使得图像的移动电话将刷新。

## <a name="related-topics"></a>相关的主题


[开发自定义 OEM 闪烁工具](developing-custom-oem-flashing-tools.md)

[使用由 Microsoft 提供的闪烁工具](use-the-flashing-tools-provided-by-microsoft.md)

 

 

[发送有关此主题的意见的评论](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_phFlashing\p_phFlashing%5D:%20Set%20device%20platform%20information%20%20RELEASE:%20%2810/4/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "发送有关此主题的意见的评论")





