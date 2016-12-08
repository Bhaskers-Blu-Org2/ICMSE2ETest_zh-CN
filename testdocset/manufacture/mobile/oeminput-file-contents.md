---
title: "OEMInput 文件的内容"
description: "OEMInput.xml 文件包含用于定义移动图像的必选和可选元素。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 945961d7-382e-4d66-9e00-bc01d3fbfa86
ms.openlocfilehash: 333ebba504c6dfe05b9962277cf0c257dffea82d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="oeminput-file-contents"></a>OEMInput 文件的内容


OEMInput.xml 文件包含用于定义移动图像的必选和可选元素。 操作系统使用此文件来确定应用程序的处理器、 生成类型、 用户界面语言，默认区域格式、 分辨率和其他属性以在将生成的图像中包含。

本主题提供了有关该文件的 XML 架构的完整列表。

## <a name="required-elements-in-the-oeminput-file"></a>在 OEMInput 文件中的必需的元素


下表介绍了在 OEMInput 文件中的必需的元素。

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
<td><p><strong>OEMInput</strong></p></td>
<td><p>OEMInput 文件的根元素。</p></td>
</tr>
<tr class="even">
<td><p><strong>说明</strong></p></td>
<td><p>一个字符串，描述图像。 Oem 应该添加特定于设备的图像描述生成的。</p></td>
</tr>
<tr class="odd">
<td><p><strong>SOC</strong></p></td>
<td><p>一个字符串，标识该设备使用 SoC。 当前支持以下值︰</p>
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>应用程序处理器</th>
<th>支持的 SOC 值</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>QC8974</strong></p></td>
<td><ul>
<li><p><strong>QC8974</strong>︰ 创建图像没有崩溃转储分区。 此值用于生产图像。</p></li>
<li><p><strong>QC8974_Test</strong>︰ 创建图像与崩溃转储分区的大小超过 2 GB。 生成具有 4 GB 以上的存储设备的测试图像时，请使用此值。</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>QC8x26</strong></p></td>
<td><ul>
<li><p><strong>QC8x26</strong>︰ 没有任何崩溃转储分区创建图像。 此值用于生产图像。</p></li>
<li><p><strong>QC8x26_Test</strong>︰ 使用 eMMC 上的两个专用的崩溃转储分区创建图像。 合并两个分区的大小是大小在手机上的 RAM 内存总量的 3.5 倍。 若要创建支持完全转储以及脱机转储至少 8gb 的 eMMC 设备测试图像，使用此值，包括 DEDICATEDUMPONEMMC 功能。</p></li>
<li><p><strong>QC8x26_UseSD_Test</strong>︰ 创建一个图像，而无需专用的分区以供具有少于 8GB eMMC 设备上存储故障转储。 若要创建完全、 内核或离线的故障转储，SD 卡必须存在，并且必须指定 DEDICATEDUMPONSD 功能将转储转到 SD 卡。 推荐的脱机转储 SD 卡大小为 16 或 32 GB。 有关指定调试功能的详细信息，请参阅<a href="optional-features-for-building-images.md">构建映像的可选功能</a>。</p></li>
</ul>
<p>若要生成少于 8GB eMMC 的设备支持完全转储和脱机转储的 QC8x26 测试图像，使用 QC8x26_UseSD_Test。 包括 DEDICATEDUMPONSD 功能将转储转到 SD 卡。 推荐的脱机转储 SD 卡大小为 16 或 32 GB。</p>
<p>若要生成至少 8GB eMMC 的设备支持完全转储和脱机转储的 QC8x26 测试图像，使用<strong>QC8x26_Test</strong> ，包括 DEDICATEDUMPONEMMC 功能。</p>
<p>若要生成在完全转储和脱机转储未启用 QC8x26 零售或生产图像，使用<strong>QC8x26</strong>。</p></td>
</tr>
<tr class="odd">
<td><p><strong>QC8960</strong></p></td>
<td><ul>
<li><p><strong>QC8960</strong>︰ 创建图像没有崩溃转储分区。 此值用于生产图像。</p></li>
<li><p><strong>QC8960_Test</strong>︰ 创建图像与崩溃转储分区的大小超过 2 GB。 生成的电话超过 4 GB 的存储与测试图像时，请使用此值。</p></li>
<li><p><strong>QC8960_Test_4gb</strong>︰ 约 600 mb 的大小，大小不足以存储单个崩溃转储具有 512 MB 内存的设备的故障转储分区创建图像。 生成只有 4 GB 的存储与电话有关的测试图像时，请使用此值。</p></li>
</ul>
<div class="alert">
<strong>重要</strong>  
<p>8960 SOC 选项必须仅用于使用为 Windows 10 移动创建的更新的图像。 有关详细信息，请参阅<a href="../../service/mobile/index.md">更新</a>。</p>
</div>
<div>
 
</div></td>
</tr>
</tbody>
</table>
<p> </p></td>
</tr>
<tr class="even">
<td><p><strong>设备</strong></p></td>
<td><p>一个字符串，标识设备模型图像正在生成的。 使用此设置来包含标有相应的<strong>设备</strong>特性的<strong>DeviceSpecificPackages</strong>和功能清单文件中的<strong>OEMDevicePlatformPackages</strong>元素的包。</p></td>
</tr>
<tr class="odd">
<td><p><strong>ReleaseType</strong></p></td>
<td><p>一个字符串，指示图像的版本类型。 使用此设置来包含标有相应的<strong>ReleaseType</strong>属性值的功能清单文件中的<strong>ReleasePackages</strong>元素的包。 支持以下值︰</p>
<ul>
<li><p><strong>生产</strong>︰ 此值表明映像中的所有程序包都是生产签名，并将图像只包括生产包 （即，其中 XML 包中的<strong>ReleaseType</strong>属性设置为<strong>生产</strong>的程序包）。 此外，Microsoft 拥有的所有软件包必须使用由 Microsoft 颁发的证书进行都签名。 生成最终的零售映像时，才应使用此值。</p></li>
<li><p><strong>测试</strong>︰ 此值表明图像可以包含测试签名的包以及生产签署的程序包，并将图像混合的生产和测试包 （即，其中 XML 包中的<strong>ReleaseType</strong>属性设置为<strong>测试</strong>或<strong>生产</strong>的程序包）。 此值用于生产、 测试、 运行状况和制造图像。 有关不同的图像类型的详细信息，请参阅<a href="building-a-phone-image-using-imggencmd.md">构建使用 ImgGen.cmd 电话映像</a>。</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>BuildType</strong></p></td>
<td><p>一个字符串，指定是否在创建映像时使用已检验的版本或免费包。 若要生成已检验的版本与调试代码，指定<strong>选项</strong>。 若要生成可用生成无需调试代码，指定<strong>帧</strong>。</p></td>
</tr>
<tr class="odd">
<td><p><strong>SupportedLanguages</strong></p></td>
<td><p>包含在生成的图像中指定的语言支持以下子元素︰</p>
<ul>
<li><p><strong>UserInterface</strong>︰ 一个字符串，包含语言编码在图像中包含的显示语言。 如果列出了多个语言代码，他们必须每个包含在其自己<code>&lt;language&gt;</code>块。</p></li>
<li><p><strong>键盘</strong>︰ 一个字符串，包含该语言的键盘语言在图像中包含的代码 （即，修正和建议支持中的文本的语言）。 如果列出了多个语言代码，他们必须每个包含在其自己<code>&lt;language&gt;</code>块。</p></li>
<li><p><strong>语音</strong>︰ 一个字符串，包含语言语音语言，在图像中包含的代码。 如果列出了多个语言代码，他们必须每个包含在其自己<code>&lt;language&gt;</code>块。</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>BootUILanguage</strong></p></td>
<td><p>一个字符串，指定默认值的语言代码显示在图像中包含的语言。</p></td>
</tr>
<tr class="odd">
<td><p><strong>BootLocale</strong></p></td>
<td><p>一个字符串，指定图像的默认区域格式的语言代码。</p></td>
</tr>
<tr class="even">
<td><p><strong>解决方法</strong></p></td>
<td><p>包含一个<strong>解析</strong>元素。 该<strong>解析</strong>元素包含一个字符串，表示支持由图像的显示分辨率。 支持以下值︰ <strong>480 x 800</strong>、 <strong>540 x 960</strong>、 <strong>720 x 1280</strong>， <strong>768 x 1280</strong>和<strong>1080 x 1920</strong>。 生成将包括相应的解决方法包中指定的分辨率的图像。</p>
<p>注意只能使用某些应用程序处理器支持的一些解决方法。</p></td>
</tr>
</tbody>
</table>

 

## <a name="optional-elements-in-the-oeminput-file"></a>在 OEMInput 文件中的可选元素


下表描述了 Oem 可以在 OEMInput 文件中包含的可选元素。

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
<td><p><strong>SV</strong></p></td>
<td><p>一个字符串，标识该设备使用 SoC 的制造商。 使用此设置来包含标记的功能清单文件中对应的<strong>SVPackages</strong>元素的包。</p></td>
</tr>
<tr class="even">
<td><p><strong>Product</strong></p></td>
<td><p>一个字符串，指定要生成哪些操作系统变量。 指定<strong>制造操作系统</strong>生成 MMO (Microsoft 制造 OS) 映像，其中包含 OS 程序包所需的 MMO 的最小集的值。 若要生成一个完整的操作系统映像，忽略此元素。</p>
<p>有关构建 MMO 映像的详细信息，请参阅<a href="mmos-image-definition.md">MMO 图像定义</a>。</p></td>
</tr>
<tr class="odd">
<td><p><strong>FormatDPP</strong></p></td>
<td><p>一个字符串，指示是否包含资源调配分区 (DPP) 在图像中的空的格式化的设备。 指定值<strong>，则返回 true</strong>以生成包含空的格式化的 DPP 的映像。 指定值<strong>false</strong>或省略此元素可防止 DPP 覆盖。</p></td>
</tr>
<tr class="even">
<td><p><strong>ExcludePrereleaseFeatures</strong></p></td>
<td><p>从生成中排除 string 类型的值，该值指示是否功能被认为是预发布。 指定值<strong>，则返回 true</strong>以生成图像不包括预发行功能，指定<strong>false</strong>以便将它们包含。 与 ExcludePrereleaseFeatures 设置为<strong>true</strong>，则创建的生成可能会被称为&quot;有限&quot;生成。 如果 OEMInput 文件中不包含此项，将在图像中包括的预发行功能。</p>
<p>当此选项设置为<strong>true</strong>可能还会有一些替换功能图像中出现。 如果没有配置替换功能，然后他们将不会显示生成中。</p></td>
</tr>
<tr class="odd">
<td><p><strong>功能</strong></p></td>
<td><p>包含一个或多个指定的可选功能时生成图像引用名称的子元素。 每个功能对应于将在图像中包含的一个或多个软件包。 要使用的功能，功能必须定义出<strong>AdditionalFMs</strong>元素的功能清单中。 有关功能和功能清单的详细信息，请参阅<a href="building-a-phone-image-using-imggencmd.md">生成使用 ImgGen.cmd 电话图像</a>和<a href="feature-manifest-file-contents.md">功能清单文件的内容</a>。</p>
<p><strong>功能</strong>元素包含一个或多个下列的子元素︰</p>
<ul>
<li><p><strong>Microsoft</strong>包含一个或多个<strong>功能</strong>元素，用于指定在图像中包含的可选 Microsoft 功能的名称。 有关 Microsoft 功能的详细信息，请参阅<a href="optional-features-for-building-images.md">构建映像的可选功能</a>。</p></li>
<li><p><strong>OEM</strong>包含一个或多个<strong>功能</strong>元素，用于指定在图像中包含的可选 OEM 功能的名称。 有关添加 OEM 功能的详细信息，请参阅<a href="feature-manifest-file-contents.md">功能清单文件的内容</a>。</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>AdditionalFMs</strong></p></td>
<td><p>包含一个或多个<strong>AdditionalFM</strong>元素。 <strong>AdditionalFM</strong>中的每个元素包含一个字符串值，指定在构建映像时引用的功能清单文件的完整路径。</p>
<p>功能清单定义一组程序包将自动包括在某些类型的图像，并且它们还定义功能可以在映像中包括其他程序包的<strong>功能</strong>元素引用的名称。 功能清单文件的更多信息，请参见<a href="feature-manifest-file-contents.md">清单文件内容的功能</a>。</p></td>
</tr>
<tr class="odd">
<td><p><strong>PackageFiles</strong></p></td>
<td><p>包含一组的<strong>PackageFile</strong>元素，用于指定在图像中包含的其他程序包。</p>
<div class="alert">
<strong>重要</strong>  
<p><strong>PackageFiles</strong>元素只能在预零售的图像，如测试和运行状况的图像。 仅可用于在您需要快速向预零售映像中添加特殊包的方案中使用。 在零售图像中，必须使用下列出的<strong>功能</strong>元素或引用<strong>AdditionalFMs</strong>元素下的功能清单中列出的功能引用所有包。 有关功能和功能清单的详细信息，请参阅<a href="building-a-phone-image-using-imggencmd.md">生成使用 ImgGen.cmd 电话图像</a>和<a href="feature-manifest-file-contents.md">功能清单文件的内容</a>。</p>
</div>
<div>
 
</div>
<p><strong>PackageFile</strong>中的每个元素都包含一个文本值，指定的路径和名称的单个产品包。 如果没有其他程序包添加到映像，则必须从该文件省略<strong>PackageFiles</strong>元素。 包可以在开发计算机上的任何位置。 环境变量可以用每个包中的<strong>PackageFile</strong>元素的路径。</p>
<p></p></td>
</tr>
</tbody>
</table>

 

## <a name="xml-schema-for-the-oeminput-file"></a>OEMInput 文件的 XML 架构


OEMInput 文件是根据下面的 XML 架构验证。 可以使用此架构来验证您所创建的 OEMInput XML 文件。 若要在 Visual Studio 中执行此操作，首先保存此 XSD 扩展名的文件中。 在 Visual Studio 中选择**XML** &gt; **架构**，然后选择您创建的文件。 将突出显示在您的 XML 架构中的任何偏差。 将鼠标悬停在突出显示的项目以查看其他信息。

``` syntax
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema targetNamespace="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate" 
      elementFormDefault="qualified" 
      xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate" 
      xmlns:mstns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate" 
      xmlns:xs="http://www.w3.org/2001/XMLSchema">  
   <xs:element name="OEMInput">  
      <xs:complexType>  
         <xs:all>  
            <xs:element name="Product" type="xs:string" minOccurs="0" maxOccurs="1"/>  
            <xs:element name="Description" type="xs:string" minOccurs="0" maxOccurs="1" />  
            <xs:element name="SV" type="xs:string" minOccurs="0" maxOccurs="1"/>  
            <xs:element name="SOC" type="xs:string" minOccurs="1" maxOccurs="1"/>  
            <xs:element name="Device" type="xs:string" minOccurs="1" maxOccurs="1"/>  
  
            <xs:element name="ReleaseType" minOccurs="1" maxOccurs="1">  
               <xs:simpleType>  
                  <xs:restriction base="xs:string">  
                     <xs:enumeration value="Test"/>  
                     <xs:enumeration value="Production"/>  
                  </xs:restriction>  
               </xs:simpleType>  
            </xs:element>  
              
            <xs:element name="BuildType" minOccurs="1" maxOccurs="1">  
               <xs:simpleType>  
                  <xs:restriction base="xs:string">  
                     <xs:enumeration value="fre"/>  
                     <xs:enumeration value="chk"/>  
                     <xs:enumeration value="%BUILDTYPE%"/> 
                  </xs:restriction>  
               </xs:simpleType>  
            </xs:element>  
  
            <xs:element name="FormatDPP" minOccurs="0" maxOccurs="1">  
               <xs:simpleType>  
                  <xs:restriction base="xs:string">  
                     <xs:enumeration value="true"/>  
                     <xs:enumeration value="false"/>  
                  </xs:restriction>  
               </xs:simpleType>  
            </xs:element>  
  
            <xs:element name="ExcludePrereleaseFeatures" minOccurs="0" maxOccurs="1">  
               <xs:simpleType>  
                  <xs:restriction base="xs:string">  
                     <xs:enumeration value="true"/>  
                     <xs:enumeration value="false"/>  
                  </xs:restriction>  
               </xs:simpleType>  
            </xs:element>  
  
            <xs:element name="OEMDevicePlatform" type="xs:string" minOccurs="0" maxOccurs="1"/>  
              
            <xs:element name="SupportedLanguages" minOccurs="1" maxOccurs="1">  
               <xs:complexType>  
                  <xs:all>  
                     <xs:element name="UserInterface" minOccurs="1" maxOccurs="1">  
                        <xs:complexType>  
                        <xs:sequence>  
                           <xs:element name="Language" type="xs:string" 
                              minOccurs="1" maxOccurs="unbounded" />  
                        </xs:sequence>  
                     </xs:complexType>  
                     </xs:element>  
                     <xs:element name="Keyboard" minOccurs="0" maxOccurs="1">  
                        <xs:complexType>  
                           <xs:sequence>  
                              <xs:element name="Language" type="xs:string" 
                                 minOccurs="1" maxOccurs="unbounded"/>  
                           </xs:sequence>  
                        </xs:complexType>  
                     </xs:element>  
                     <xs:element name="Speech" minOccurs="0" maxOccurs="1">  
                        <xs:complexType>  
                           <xs:sequence>  
                              <xs:element name="Language" type="xs:string" 
                                 minOccurs="1" maxOccurs="unbounded"/>  
                           </xs:sequence>  
                        </xs:complexType>  
                     </xs:element>  
                  </xs:all>  
               </xs:complexType>  
            </xs:element>  

            <xs:element name="BootUILanguage" type="xs:string" minOccurs="1" maxOccurs="1"/>  
              
            <xs:element name="BootLocale" type="xs:string" minOccurs="1" maxOccurs="1"/>  
              
            <xs:element name="Resolutions" minOccurs="0" maxOccurs="1">  
               <xs:complexType>  
                  <xs:sequence>  
                     <xs:element name="Resolution" type="xs:string" minOccurs="1" 
                        maxOccurs="unbounded"/>  
                  </xs:sequence>  
               </xs:complexType>  
            </xs:element>  
  
            <xs:element name="Features" minOccurs="0" maxOccurs="1">  
               <xs:complexType>  
                  <xs:sequence>  
                     <xs:element name="Microsoft" minOccurs="0" maxOccurs="1">  
                        <xs:complexType>  
                           <xs:sequence>  
                              <xs:element name="Feature" type="xs:string" 
                                 minOccurs="1" maxOccurs="unbounded"/>  
                           </xs:sequence>  
                        </xs:complexType>  
                     </xs:element>  
                     <xs:element name="OEM" minOccurs="0" maxOccurs="1">  
                        <xs:complexType>  
                           <xs:sequence>  
                              <xs:element name="Feature" type="xs:string" 
                                 minOccurs="1" maxOccurs="unbounded"/>  
                           </xs:sequence>  
                        </xs:complexType>  
                     </xs:element>  
                  </xs:sequence>  
               </xs:complexType>  
            </xs:element>  
  
            <xs:element name="AdditionalFMs" minOccurs="0" maxOccurs="1">  
               <xs:complexType>  
                  <xs:sequence>  
                     <xs:element name="AdditionalFM" type="xs:string" 
                        minOccurs="1" maxOccurs="unbounded"/>  
                  </xs:sequence>  
               </xs:complexType>  
            </xs:element>  
            <!-This element is only for use with Windows 8 Phone device update images -->       
            <xs:element name="UserStoreMapData" minOccurs="0" maxOccurs="1">  
               <xs:complexType>  
                  <xs:attribute name="SourceDir" type="xs:string" />  
                  <xs:attribute name="UserStoreDir" type="xs:string" />  
               </xs:complexType>  
            </xs:element>  
  
            <xs:element name="PackageFiles" minOccurs="0" maxOccurs="1">  
               <xs:complexType>  
                  <xs:sequence>  
                     <xs:element name="PackageFile" type="xs:string" 
                        minOccurs="1" maxOccurs="unbounded"/>  
                  </xs:sequence>  
               </xs:complexType>  
            </xs:element>  
         </xs:all>  
      </xs:complexType>  
   </xs:element>  
</xs:schema>
```

## <a name="related-topics"></a>相关的主题


[构建使用 ImgGen.cmd 的图像](building-a-phone-image-using-imggencmd.md)

 

 

[发送有关此主题的意见的评论](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_phFlashing\p_phFlashing%5D:%20OEMInput%20file%20contents%20%20RELEASE:%20%2810/4/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "发送有关此主题的意见的评论")





