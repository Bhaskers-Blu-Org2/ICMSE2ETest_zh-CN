---
title: "可选功能，用于建立移动图像"
description: "它们包括在 OEMInput XML 文件中的功能元素，可以向图像添加可选功能。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 8147e170-f21f-4ed3-8130-4d498368ff92
ms.openlocfilehash: e5ba14b60503190ca2db0657f3f2c9c54829a0c1
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="optional-features-for-building-mobile-images"></a>可选功能，用于建立移动图像


它们包括在 OEMInput XML 文件中的**功能**元素，可以向图像添加可选功能。 添加功能将添加到映像的功能关联的文件包。 某些功能只使用某些类型的图像。 有关使用可选功能的详细信息，请参阅[构建映像使用 ImgGen.cmd](building-a-phone-image-using-imggencmd.md)。

应通过提交操作系统测试更新更新请求使用接收客户端和验证成功的操作系统更新。

## <a name="conditional-features"></a>条件的功能


如果设备满足功能下, 表中列出的安装条件，则除非该功能的安装时，设备的更新路径将失败。 例如，如果更新丰富的通信套件平台支持 Windows 10 移动，并且您从该功能的设备，否则将能够使用它，然后整个更新程序包 （和所有后续更新） 将无法安装。 若要获取更新，您又需要提供图像包含的功能给客户，并让它们重新刷新设备。

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>功能名称和 ID</th>
<th>更新路径</th>
<th>条件</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>丰富的通信套件平台支持 (RCS_FEATURE_PACK)</td>
<td>Windows 10 为 Windows 8.1</td>
<td><p>如果安装 PhoneManufacturer = 诺基亚</p>
<p>如果安装，更新</p></td>
</tr>
<tr class="even">
<td>附近的数字块和筛选器 （MS_COMMSENHANCEMENT * 应用程序）</td>
<td>Windows 10 为 Windows 8.1</td>
<td><p>如果安装 MS_COMMSENHANCEMENTCHINA HKEY_LOCAL_MACHINE\system\Platform\DeviceTargetingInfo\phoneromlanguage = 0804年。 如果已经安装了此，更新。</p>
<p>如果安装 MS_COMMSENHANCEMENTGLOBAL HKEY_LOCAL_MACHINE\system\Platform\DeviceTargetingInfo\phoneromlanguage &lt; &gt; 0804年。 如果已经安装了此，更新。</p></td>
</tr>
</tbody>
</table>

 

## <a name="retail-features-defined-by-microsoft"></a>由 Microsoft 零售功能


下表描述可以在 OEMInput 文件中为零售设备的**功能**元素中使用 oem Microsoft 定义的功能。

指任何其他零售功能用于特定的移动运营商的移动运营手册。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>功能 </th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>OPTIMIZED_BOOT</p></td>
<td><p>修改操作系统启动过程以启动某些系统进程和服务之前启动的所有设备驱动程序的行为。 启用此功能可能会减少启动时间，但在引导行为，在某些情况下可能会发生衰退。</p></td>
</tr>
<tr class="even">
<td><p>STANDARD_FEATURE_1</p></td>
<td><p>此功能包括标准必须包括在所有图像的功能。</p></td>
</tr>
<tr class="odd">
<td><p>NETLOG_RETAIL</p></td>
<td><p>这项功能将添加网络捕获日志记录，以帮助诊断网络连接问题。 该功能用于通过字段 Medic 收集网络诊断信息。</p></td>
</tr>
<tr class="even">
<td><p>导航栏</p></td>
<td><p>此功能增加了一项电话设置，使用户能够配置软件按钮的颜色。</p></td>
</tr>
<tr class="odd">
<td><p>FACEBOOK</p></td>
<td><p>此功能包括在映像中的 Facebook。</p></td>
</tr>
<tr class="even">
<td><p>SKYPE</p></td>
<td><p>此功能包括 Skype Windows Phone Silverlight 应用程序映像中。</p></td>
</tr>
<tr class="odd">
<td><p>BINGAPPS</p></td>
<td><p>此功能增加了 Bing 新闻、 财务、 体育和天气。</p></td>
</tr>
<tr class="even">
<td><p>BINGFOOD</p></td>
<td><p>此功能增加了 Bing 食品&amp;饮用。</p></td>
</tr>
<tr class="odd">
<td><p>BINGHEALTH</p></td>
<td><p>此功能增加了 Bing 健康&amp;的适用性。</p></td>
</tr>
<tr class="even">
<td><p>BINGTRAVEL</p></td>
<td><p>此功能增加了 Bing 旅行。</p></td>
</tr>
<tr class="odd">
<td><p>WIFI_FEATURE_PACK</p></td>
<td><p>此功能从操作系统中删除所有与移动电话相关的功能，仅供不会连接到蜂窝网络的设备。 它将删除所有移动电话相关的拼贴、 图标和设置的用户界面。 包括此功能可减少内存使用量，改善了用户体验，通过不显示非功能性手机设置和图标。</p></td>
</tr>
<tr class="even">
<td><p>RELEASE_PRODUCTION</p></td>
<td><p>中已弃用，不能再使用。</p></td>
</tr>
<tr class="odd">
<td><p>COMMSENHANCEMENTGLOBAL</p></td>
<td><p>功能包括消息并调用筛选图像中的应用程序。</p></td>
</tr>
<tr class="even">
<td><p>COMMSENHANCEMENTCHINA</p></td>
<td><p>功能包括消息&amp;调用筛选、 调用位置和类别图像中的应用程序。 它是中国大陆仅使用。</p></td>
</tr>
<tr class="odd">
<td><p>4GBFEATURESONDATA</p></td>
<td><p>具有 4 GB 的存储设备上的数据分区上存储调配的包。</p></td>
</tr>
<tr class="even">
<td><p>8GBFEATURESONDATA</p></td>
<td><p>在具有 8 GB 的存储设备，调配的包存储在数据分区。</p>
<div class="alert">
<strong>请注意</strong> 我们强烈建议您同时使用 8GBFEATURESONSYSTEM，当您指定此功能。
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td><p>8GBFEATURESONSYSTEM</p></td>
<td><p>在具有 8 GB 的存储设备，调配的包存储在操作系统分区。</p></td>
</tr>
<tr class="even">
<td><p>16GBFEATURESONDATA</p></td>
<td><p>16 gb 的存储设备上的数据分区上存储调配的包。</p>
<div class="alert">
<strong>请注意</strong> 我们强烈建议您同时使用 16GBFEATURESONSYSTEM，当您指定此功能。
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td><p>16GBFEATURESONSYSTEM</p></td>
<td><p>16 gb 的存储设备上的资源调配的包存储在操作系统分区。</p></td>
</tr>
<tr class="even">
<td><p>SPATIALSOUND_FILTERDATA</p></td>
<td><p>包含所有数据文件和启用移动设备上的空间的音频功能所需的注册表项。 空间的音频用于使声音好像来自一个特定的方向，而且使音频声音像它存在自然内特定类型的房间。</p></td>
</tr>
<tr class="odd">
<td><p>TAIWAN_ENABLEMENT</p></td>
<td><p>从映像中删除引用台湾。</p></td>
</tr>
<tr class="even">
<td><p>MYANMAR_ZAWGYI_ENABLEMENT</p></td>
<td><p>启用要使用在缅甸的 Zawgyi 编码此图像。 添加此功能时，您还应该添加 Zawgyi 键盘。</p></td>
</tr>
<tr class="odd">
<td><p>SOCProdTest_HSTI</p></td>
<td><p>此功能安装正确的驱动程序为安全水位线检查并对于 Windows 10 移动是必需的。 如果未安装此软件包，您将看到<strong>不为零售</strong>水印。</p>
<div class="alert">
<strong>重要</strong> 此功能必须包括在您的操作系统映像。 如果不包含此功能，则该设备可能不会启动。
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td><p>ATTWIFI</p></td>
<td><p>此功能安装第三方插件允许使用 AT 设备&amp;T SIM 会自动连接到 AT&amp;T 的热点。</p></td>
</tr>
<tr class="odd">
<td><p>DISABLE_ABNORMAL_RESET</p></td>
<td><p>此功能禁用异常重置并不到 Watson 报告。</p></td>
</tr>
<tr class="even">
<td><p>停靠</p></td>
<td><p>此功能使 Windows 10 移动的统一体。</p></td>
</tr>
<tr class="odd">
<td><p>RESET_PROTECTION</p></td>
<td><p>此功能可重新设置保护零售映像上。 当第一次启动设备时，编写相应的安全 （uefi） 变量。</p></td>
</tr>
<tr class="even">
<td><p>PERF_TRACING_TOOLS</p></td>
<td><p>包含用于进行性能分析，如停止和合并 ETL 跟踪工具的工具。</p></td>
</tr>
<tr class="odd">
<td><p>ENABLE_BOOT_PERF_BASIC_TRACING</p></td>
<td><p>启用启动性能跟踪事件生成。</p></td>
</tr>
<tr class="even">
<td><p>ENABLE_BOOT_PERF_CPU_PROFILING_TRACING</p></td>
<td><p>启用配置文件事件的 CPU。 除了启用了 ENABLE_BOOT_PERF_BASIC_TRACING 的启动性能跟踪事件。</p></td>
</tr>
<tr class="odd">
<td><p>MESSAGINGGLOBAL</p></td>
<td><p>此功能将安装包括 Skype 集成消息传递包。 它必须用于除内部认证在中国所提交的任何设备。</p></td>
</tr>
<tr class="even">
<td><p>MESSAGINGLITE</p></td>
<td><p>此功能将安装 Skype 集成无消息包。 它必须用于任何电话或其他设备在中国 （不包括香港特别行政区和澳门特别行政区） 的内部认证提交。</p></td>
</tr>
<tr class="odd">
<td><p>SPATIALSOUND_FILTERDATA</p></td>
<td><p>此功能将安装<a href="https://dev.windows.com/holographic/spatial_sound">声音的空间</a>。</p></td>
</tr>
</tbody>
</table>

 

**零售启动顺序设置**

接下来的两个设置控制手机启动。 只有一个可以选择。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>BOOTSEQUENCE_RETAIL</p></td>
<td><p>此功能使标准零售引导顺序。</p></td>
</tr>
</tbody>
</table>

 

**Microsoft 内部零售功能**

以下组件是保留 Microsoft 仅供内部使用，但在此记录的完整性。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>SELFHOST</p></td>
<td><p>这项功能添加组件以独占方式用于在 Microsoft 的自托管方案。</p></td>
</tr>
<tr class="even">
<td><p>FieldMedicCustomProfiles</p></td>
<td><p>此功能增加了额外的跟踪配置文件使用字段 Medic。</p></td>
</tr>
<tr class="odd">
<td><p>RESET_PROTECTION_INTERNAL</p></td>
<td><p>此功能启用重置保护测试图像上。 当第一次启动设备时，编写相应的安全 （uefi） 变量。</p></td>
</tr>
</tbody>
</table>

 

**零售演示体验功能**

零售演示体验 FOD 包含脱机零售演示内容，是极好的零售演示体验的关键。 此脱机内容包含 Windows 和 Office 与任何 OEM 或零售商的零售演示内容一起显示的内容。 添加此零售演示体验 FOD 的是必需的和必要的参与使其 Windows 10 设备上零售演示体验任何 Oem。

-   MS\_RETAILDEMOCONTENT\_AR SA
-   MS\_RETAILDEMOCONTENT\_BG-BG
-   MS\_RETAILDEMOCONTENT\_CS CZ
-   MS\_RETAILDEMOCONTENT\_DA-DK
-   MS\_RETAILDEMOCONTENT\_DE DE
-   MS\_RETAILDEMOCONTENT\_EL-GR
-   MS\_RETAILDEMOCONTENT\_EN GB
-   MS\_RETAILDEMOCONTENT\_EN-美国
-   MS\_RETAILDEMOCONTENT\_ES-ES
-   MS\_RETAILDEMOCONTENT\_ES-MX
-   MS\_RETAILDEMOCONTENT\_ET EE
-   MS\_RETAILDEMOCONTENT\_FI FI
-   MS\_RETAILDEMOCONTENT\_FR-CA
-   MS\_RETAILDEMOCONTENT\_FR-FR
-   MS\_RETAILDEMOCONTENT\_HE-IL
-   MS\_RETAILDEMOCONTENT\_HR-HR
-   MS\_RETAILDEMOCONTENT\_HU HU
-   MS\_RETAILDEMOCONTENT\_ID ID
-   MS\_RETAILDEMOCONTENT\_IT-IT
-   MS\_RETAILDEMOCONTENT\_JA-JP
-   MS\_RETAILDEMOCONTENT\_KO-KR
-   MS\_RETAILDEMOCONTENT\_LT 浅色
-   MS\_RETAILDEMOCONTENT\_LV LV
-   MS\_RETAILDEMOCONTENT\_NB-无
-   MS\_RETAILDEMOCONTENT\_中性
-   MS\_RETAILDEMOCONTENT\_NL NL
-   MS\_RETAILDEMOCONTENT\_PL PL
-   MS\_RETAILDEMOCONTENT\_PT-BR
-   MS\_RETAILDEMOCONTENT\_磅磅
-   MS\_RETAILDEMOCONTENT\_RO RO
-   MS\_RETAILDEMOCONTENT\_RU-RU
-   MS\_RETAILDEMOCONTENT\_SK-SK
-   MS\_RETAILDEMOCONTENT\_SL SI
-   MS\_RETAILDEMOCONTENT\_SR-LATN RS
-   MS\_RETAILDEMOCONTENT\_SV SE
-   MS\_RETAILDEMOCONTENT\_TH-TH
-   MS\_RETAILDEMOCONTENT\_异
-   MS\_RETAILDEMOCONTENT\_UK-UA
-   MS\_RETAILDEMOCONTENT\_VI-VN
-   MS\_RETAILDEMOCONTENT\_ZH-CN
-   MS\_RETAILDEMOCONTENT\_ZH 香港
-   MS\_RETAILDEMOCONTENT\_ZH-TW

## <a name="test-features-defined-by-microsoft"></a>定义由 Microsoft 的测试功能


下表描述可以在 OEMInput 文件中的**功能**元素中使用 oem 的 Microsoft 定义测试功能。 这些功能在 MSOptionalFeatures.xml，附带 %WPDKCONTENTROOT%下 MobileOS\\FMFiles。

### <a name="boot-option-features"></a>引导选项功能

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>功能 </th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>BOOTSEQUENCE_TEST</p></td>
<td><p>此功能包括引导至操作系统完全测试图像中的 BCD 启动顺序配置。 此功能还包括预启动故障转储应用程序和启动前崩溃转储条目。</p>
<div class="alert">
<strong>请注意</strong>  
<p>以下功能是互相排斥;仅有一种可以在 OEMInput 文件中引用︰ BOOTSEQUENCE_TEST、 MMOSLOADER_TEST。</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td><p>MMOSLOADER_TEST</p></td>
<td><p>此功能包括 BCD 启动顺序配置为支持转用中测试映像 MMO。 此功能还包括预启动故障转储应用程序和启动前崩溃转储条目。 MMO 有关的详细信息，请参阅<a href="mmos-image-definition.md">MMO 图像定义</a>。</p>
<div class="alert">
<strong>请注意</strong>  
<p>以下功能是互相排斥;仅有一种可以在 OEMInput 文件中引用︰ BOOTSEQUENCE_TEST、 MMOSLOADER_TEST。</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td><p>MOBILECOREBOOTSH</p></td>
<td><p>使 bootsh 服务 (bootshscv)，以便可以使用 startup.bsc 功能，如 telnet 和 ftp。</p></td>
</tr>
<tr class="even">
<td><p>MOBILECORE_TEST</p></td>
<td><p>将在本文档的后面的版本中提供此功能的信息。</p></td>
</tr>
<tr class="odd">
<td><p>生产</p></td>
<td><p>包含用来为生产生成主操作系统、 UEFI 和更新的操作系统中支持基本的操作系统功能的核心操作系统文件。 此功能用于生产映像类型。</p></td>
</tr>
<tr class="even">
<td><p>PRODUCTION_CORE</p></td>
<td><p>此功能将生产启动和主操作系统二进制文件添加到图像中。 PRODUCTION_CORE 自动包括以下功能︰</p>
<ul>
<li><p>CODEINTEGRITY_PROD</p></li>
</ul>
<p>因为这些功能已经包括在内，他们不应手动包含在 PRODUCTION_CORE 中生成。</p></td>
</tr>
<tr class="odd">
<td><p>DISABLE_FFU_PLAT_ID_CHECK</p></td>
<td><p>禁用设备平台验证闪烁 Microsoft 应用程序中。 关于闪烁在平台检查的详细信息，请参阅<a href="use-the-flashing-tools-provided-by-microsoft.md">的使用由 Microsoft 提供的闪烁的工具</a>。</p>
<div class="alert">
<strong>重要</strong>  
<p>必须禁用零售图像中闪烁的设备平台验证。</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td><p>RESET_PROTECTION_INTERNAL</p></td>
<td><p>此功能使设备上重新设置保护。 当第一次启动设备时，编写相应的安全 （uefi） 变量。</p></td>
</tr>
</tbody>
</table>

 

### <a name="boot-option-feature-constraints"></a>引导选项功能约束

您可以指定生成配置功能约束，以避免不合逻辑或不适当的。

某些设置是互相排斥的只有一种设置应指定一次。 例如，请考虑功能，发布\_生产和发行\_测试。 这些功能是互相排斥的。 这意味着，如果发行\_测试集，版本\_不能设置生产。 有关详细信息请参阅有关如何在 XML 中指定约束条件的信息，[功能分组和约束](feature-groupings-and-constraints.md)。

当&lt;ReleaseType&gt;生产&lt;/ReleaseType&gt; OEMInput 文件，发布到此映射中设置\_生产。 当&lt;ReleaseType&gt;测试&lt;/ReleaseType&gt; OEMInput 文件，发布到此映射中设置\_测试。 发行类别有关的详细信息，请参阅[OEMInput 文件的内容](oeminput-file-contents.md)。

发行版的版本约束\_生产可以归纳为以下几点。

-   任何一个发行版\_生产或 CODEINTEGRITY\_可以选择生产。 这是因为自动启用生产代码完整性时释放\_生产处于选中状态，因此不能手动启用。

可以使用这些功能的约束以防止不正确的生成选项配置。 这些功能约束指定生产\_核心是互斥发行版\_生产和测试而不是互相排斥与健康、 生产或 SELFHOST。

下表提供生成选项的摘要，并指示该选项是否特有的任何其他选项。

<table style="width:100%;">
<colgroup>
<col width="14%" />
<col width="14%" />
<col width="14%" />
<col width="14%" />
<col width="14%" />
<col width="14%" />
<col width="14%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>RELEASE_PRODUCTION</th>
<th>测试</th>
<th>健康状况</th>
<th>生产</th>
<th>SELFHOST</th>
<th>PRODUCTION_CORE</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>RELEASE_PRODUCTION</p></td>
<td><p>NA</p></td>
<td><p>是</p></td>
<td><p>是</p></td>
<td><p>是</p></td>
<td><p>是</p></td>
<td><p>是</p></td>
</tr>
<tr class="even">
<td><p>测试</p></td>
<td><p>是</p></td>
<td><p>NA</p></td>
<td><p>是</p></td>
<td><p>是</p></td>
<td><p>是</p></td>
<td><p>是</p></td>
</tr>
<tr class="odd">
<td><p>健康状况</p></td>
<td><p>是</p></td>
<td><p>是</p></td>
<td><p>NA</p></td>
<td><p>是</p></td>
<td><p>是</p></td>
<td><p>否</p></td>
</tr>
<tr class="even">
<td><p>生产</p></td>
<td><p>是</p></td>
<td><p>是</p></td>
<td><p>是</p></td>
<td><p>NA</p></td>
<td><p>是</p></td>
<td><p>否</p></td>
</tr>
<tr class="odd">
<td><p>SELFHOST</p></td>
<td><p>是</p></td>
<td><p>是</p></td>
<td><p>是</p></td>
<td><p>是</p></td>
<td><p>NA</p></td>
<td><p>否</p></td>
</tr>
<tr class="even">
<td><p>PRODUCTION_CORE</p></td>
<td><p>是</p></td>
<td><p>是</p></td>
<td><p>否</p></td>
<td><p>否</p></td>
<td><p>否</p></td>
<td><p>NA</p></td>
</tr>
</tbody>
</table>

 

### <a name="other-boot-related-features"></a>其他启动相关的功能

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>功能 </th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>STARTUPOVERRIDES</p></td>
<td><p>此功能将启动 FTP 服务 (ftpd.exe) 和 Telnet 服务 (telnetd.exe) 在启动时自动。</p></td>
</tr>
<tr class="even">
<td><p>LABIMAGE</p></td>
<td><p>此功能会导致设备在设备启动时，自动输入 FFU 下载模式。 有关详细信息，请参阅<a href="use-the-flashing-tools-provided-by-microsoft.md">的使用由 Microsoft 提供的闪烁的工具</a>。</p></td>
</tr>
<tr class="odd">
<td><p>BOOTKEYACTIONS_RETAIL</p></td>
<td><p>此功能启用了一套零售设备中使用的按钮操作。</p></td>
</tr>
<tr class="even">
<td><p>SKIPOOBE</p></td>
<td><p>此功能禁用初始安装过程向导。 此功能支持测试、 健康和生产的图像类型。 零售的图像必须不使用此功能。</p></td>
</tr>
</tbody>
</table>

 

### <a name="security-related-features"></a>与安全相关的功能

有两个代码签名模式 10 Windows Mobile 设备、 零售和测试上。 与零售，所有代码必须都是有符号若都要能够在设备上运行的生产。 对于测试签名，必须使用测试证书签名的所有代码。 有关代码签名的详细信息，请参见[代码签名](https://msdn.microsoft.com/library/windows/hardware/dn756634)。

在生成系统中自动管理签名模式两种代码。 不再使用以前的 DISABLETESTSIGNING 和 ENABLETESTSIGNING 功能设置。 而测试的代码签名会自动启用以下生成类型中︰

-   测试

-   健康状况

-   生产

-   SELFHOST

无法启用版本中的测试的代码签名\_生产生成用于零售设备的类型

下表总结了安全相关的功能。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>功能 </th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CODEINTEGRITY_PROD</p></td>
<td><p>此功能包括用于生产映像上的签名验证的代码的完整性二进制文件。 代码完整性验证二进制文件的完整性，因为它们是由操作系统加载到内存。 当选中 PRODUCTION_CORE 时，此功能将自动包括在内。 由于这个原因，CODEINTEGRITY_PROD 不应手动添加 PRODUCTION_CORE 当选。</p></td>
</tr>
<tr class="even">
<td><p>CODEINTEGRITY_TEST</p></td>
<td><p>此功能包括用于测试图像上的签名验证的代码的完整性二进制文件。 代码完整性验证二进制文件的完整性，因为它们是由操作系统加载到内存。</p></td>
</tr>
<tr class="odd">
<td><p>GWPCERTTESTPROV</p></td>
<td><p>此功能规定，图像中的一组测试的正版 Windows Phone 证书 (GWPC) 证书。</p></td>
</tr>
</tbody>
</table>

 

### <a name="test-related-features"></a>测试相关的功能

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>功能 </th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>测试</p></td>
<td><p>此功能增加了很多测试驱动程序、 应用程序和其他组件，用于在不同的条件中测试操作系统。</p></td>
</tr>
<tr class="even">
<td><p>TESTINFRASTRUCTURE</p></td>
<td><p>此功能将下列组件添加到图像︰</p>
<ul>
<li><p>MinTE.exe 以及其他支持组件的最小测试线束环境测试编写和执行框架 (TAEF) 的测试。</p></li>
<li><p>Verifier.cmd 脚本，它用于配置驱动程序验证程序。</p></li>
<li><p>Tux.exe 和其他组件与本机代码 Tux 测试工具。</p></li>
<li><p>TuxNet.exe 和其他组件与托管代码 TuxNet 测试工具。</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>健康状况</p></td>
<td><p>此功能添加用于运行测试功能和性能与相关的组件。</p></td>
</tr>
<tr class="even">
<td><p>DRIVERS_WDTFINFRA</p></td>
<td><p>将在本文档的后面的版本中提供此功能的信息。</p></td>
</tr>
<tr class="odd">
<td><p>DRIVERS_WDTFPOWER</p></td>
<td><p>将在本文档的后面的版本中提供此功能的信息。</p></td>
</tr>
<tr class="even">
<td><p>DRIVERS_WDTFPLGINS</p></td>
<td><p>将在本文档的后面的版本中提供此功能的信息。</p></td>
</tr>
<tr class="odd">
<td><p>DRIVERS_WDTFDRVCOV</p></td>
<td><p>将在本文档的后面的版本中提供此功能的信息。</p></td>
</tr>
<tr class="even">
<td><p>DRIVERS_WDTFIOSPY</p></td>
<td><p>将在本文档的后面的版本中提供此功能的信息。</p></td>
</tr>
</tbody>
</table>

 

### <a name="debug-related-features"></a>调试相关的功能

使用以下设置指定用于调试的传输。 以前的 DEBUGGERON 功能已被否决。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>功能 </th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p></p></td>
<td><p><strong>调试传输设置</strong></p></td>
</tr>
<tr class="even">
<td><p>KDNETUSB_ON</p></td>
<td><p>包括所有内核调试器传输并使 KDNET 可以通过 USB。</p>
<p>此功能的默认调试传输设置的 IP 地址为&quot;1.2.3.4&quot;，端口地址&quot;50000&quot;，并且调试器项的&quot;4.3.2.1&quot;。 若要使用默认 IP 地址为 1.2.3.4，运行 VirtEth.exe <em>/autodebug</em>标志。 若要建立内核调试器连接到电话时，使用下面的命令。</p>
<p>Windbg-k net︰ 端口 = 50000，键 = 4.3.2.1</p></td>
</tr>
<tr class="odd">
<td><p>KDUSB_ON</p></td>
<td><p>包括所有内核调试器传输，使 KDUSB。</p>
<p></p>
<p>此功能的默认调试传输目标名称是 WOATARGET。 若要建立内核调试器连接到电话时，使用下面的命令。</p>
<p>Windbg-k usb:targetname = WOATARGET</p>
<div class="alert">
<strong>请注意</strong>  
<p>如果您需要在图像中启用 USB 相比 MTP 或 IP，不要包括 KDUSB_ON 或 KDNETUSB_ON。 在图像中启用了内核调试器和调试运输用来连接到该设备，如果内核调试器已独占使用 USB 端口并防止 MTP 和 IP 通过 USB 工作。</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td><p>KDSERIAL_ON</p></td>
<td><p>包括所有内核调试器传输和下面的设置启用 KDSERIAL︰ 为 115200 波特、 8 位、 无奇偶校验。</p></td>
</tr>
<tr class="odd">
<td><p>KD</p></td>
<td><p>在图像中，包括所有的内核调试器传输但不启用内核调试器。</p></td>
</tr>
<tr class="even">
<td><p>KD_TEST</p></td>
<td><p>在图像中，包括所有的内核调试器传输但不启用内核调试器。</p></td>
</tr>
<tr class="odd">
<td><p>KDNETUSB_TEST_ON</p></td>
<td><p>包括所有内核调试器传输并使 KDNET 可以通过 USB 中测试映像。 此选项必须只使用与测试映像。</p></td>
</tr>
</tbody>
</table>

 

**其他调试设置**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>功能 </th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p></p></td>
<td><p>设置功能的以下三种功能的 Dumpsize 必须只用于测试和运行状况图像类型。 这些功能必须不能用于零售的图像。 可以一次选择一个 dumpsize 设置。</p></td>
</tr>
<tr class="even">
<td><p>DUMPSIZE512MB</p></td>
<td><p>指定一个预分配的崩溃转储文件大小为 592 MB。 这适用于具有 512 MB 内存的电话。</p></td>
</tr>
<tr class="odd">
<td><p>DUMPSIZE1G</p></td>
<td><p>指定一个预分配的崩溃转储文件大小为 1104 MB。 这适用于具有 1024 MB 内存的电话。</p></td>
</tr>
<tr class="even">
<td><p>DUMPSIZE2G</p></td>
<td><p>指定一个预分配的崩溃转储文件大小为 2128 MB。 这适用于具有 2048 MB 内存的电话。</p></td>
</tr>
<tr class="odd">
<td><p>DUMPSIZE4G</p></td>
<td><p>指定的预分配的崩溃转储文件大小为 4 GB。 这适用于具有 4096 MB 内存的电话。</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>转储数据存储位置-接下来的两个设置控件，如果崩溃转储的数据存储在 eMMC 上或者崩溃转储的数据存储在 SD 卡上。 这些设置中的只有一个可以一次选择。 只有必须与测试、 运行状况和 Selfhost 的图像类型使用这两种功能。 这些功能必须不能用于零售的图像。</p></td>
</tr>
<tr class="odd">
<td><p>DEDICATEDDUMPONEMMC</p></td>
<td><p>指定 c:\crashdump\dedicateddump.sys DedicatedDumpFile 的位置。</p></td>
</tr>
<tr class="even">
<td><p>DEDICATEDDUMPONSD</p></td>
<td><p>DEDICATEDDUMPONSD – 指定为 d:\dedicateddump.sys 的 DedicatedDumpFile 位置</p>
<p>使用 DEDICATEDDUMPONSD 时，如果用户删除该 SD 卡或卡没有引导设备时，将禁用故障转储。 要重新启用故障转储︰</p>
<ol>
<li><p>设置此注册表项<code>HKLM\System\CurrentControlSet\Control\CrashControl\CrashDumpEnabled</code>的值 <code>HKLM\System\CurrentControlSet\Control\CrashControl\ExpectedCrashDumpEnabled</code></p></li>
<li><p>重新启动手机。</p></li>
</ol></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>测试磁盘空闲能耗行为-接下来的两个设置确定如果存储设备 (内部和 SD 卡) 进入低功耗状态后变得空闲。 他们必须不能用于零售的图像。</p>
<p></p></td>
</tr>
<tr class="even">
<td><p>TEST_ENABLE_DISK_IDLE</p></td>
<td><p>此功能将允许存储设备 (内部和 SD 卡) 进入低功耗状态，不久之后他们进入空闲状态。 此设置可能会阻止 crashdumps MSM8960 处理器的设备上的集合。 如果需要从 MSM8960 设备收集到 crashdumps，使用 TEST_DISABLE_DISK_IDLE 功能。</p></td>
</tr>
<tr class="odd">
<td><p>TEST_DISABLE_DISK_IDLE</p></td>
<td><p>此功能将防止存储设备 (内部和 SD 卡) 从进入低功耗状态之后他们进入空闲状态。 如果需要从 MSM8960 设备收集到 crashdumps，则应使用此设置。</p></td>
</tr>
<tr class="even">
<td><p>DRVRF_SIPLAT</p></td>
<td><p>设置 OEM 和 SoC 驱动程序驱动程序验证程序参数。 此功能将 VerifyDriverLevel 设置为 002209BB 和 VerifierOptions 到 00000009 的值。 使用 VerifyDrivers 项中排除 Windows 驱动程序由 Microsoft 提供的。 以下调试命令可用于在您的环境中列出的驱动程序进行验证。</p>
<pre class="syntax" space="preserve"><code>!verifier 1    </code></pre></td>
</tr>
<tr class="odd">
<td><p>DBGCHKDISABLE</p></td>
<td><p>此功能禁用调试器连接检查和调试程序连接状态将被忽略。</p>
<p>对调试器行为的影响是不同的具体取决于正在使用的 SoC。</p>
<ul>
<li><p>对于 QC8x26 和 QC8974 的设备，包括 DBGCHKDISABLE，以确保将生成脱机转储，即使该设备连接到调试器。 否则为将不会创建脱机转储 （错误检查代码 0x14C 转储），但仍将创建原始转储。</p></li>
<li><p>对于 8960 设备，包括 DBGCHKDISABLE，以确保将生成脱机转储，即使该设备连接到调试器。 否则，将不创建脱机转储 （即错误检查代码 0x14C 转储）。</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>MSVCRT_DEBUG</p></td>
<td><p>此功能增加了对图像中包括 msvcp120d.dll 和 msvcr120d.dll 的显式链接调试 c 运行时库支持。 详细信息，请参阅本主题在 MSDN 上︰ <a href="http://msdn.microsoft.com/library/abx4dbyh.aspx">CRT 库功能</a>。</p></td>
</tr>
<tr class="odd">
<td><p>MWDBGSRV</p></td>
<td><p>此功能增加用户模式调试服务器的支持。</p></td>
</tr>
<tr class="even">
<td><p>NOLIVEDUMPS</p></td>
<td><p>禁用内核出现非致命错误报告。  这些报告包含操作系统和驱动程序开发人员的调试信息。</p></td>
</tr>
<tr class="odd">
<td><p>TELEMETRYONSDCARD</p></td>
<td><p>此功能允许调试日志和 SD 卡上的文件临时存储。  此功能只是适合于测试/自助主机图像且仅在具有不超过 8 GB 的可用空间的主存储设备上。</p></td>
</tr>
</tbody>
</table>

 

### <a name="non-production-features"></a>非生产功能

以下是一些可以用于开发和测试支持的功能。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>功能 </th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>POWERTRACINGTOOL</p></td>
<td><p>此功能增加了 PowerTracingTool.exe，用于收集与电源有关 ETW 日志，到图像。</p></td>
</tr>
<tr class="even">
<td><p>TASKSCHEDULERTOOL</p></td>
<td><p>此功能增加了 TaskSchTestUtil.exe，用于执行任务的日程排定相关的操作，对图像。</p></td>
</tr>
<tr class="odd">
<td><p>DISABLEPREBOOTCRASHDUMP</p></td>
<td><p>这项功能将添加的注册表设置，禁用脱机崩溃转储。</p></td>
</tr>
<tr class="even">
<td><p>ALWAYSKEEPMEMORYDUMP</p></td>
<td><p>这项功能添加注册表设置，用于告知设备保持内核转储文件。</p></td>
</tr>
<tr class="odd">
<td><p>AUTOREBOOT</p></td>
<td><p>此功能增加了故障转储完成后立即重新启动该设备的注册表设置。</p></td>
</tr>
<tr class="even">
<td><p>DISABLEDEBUGCHECKSCREEN</p></td>
<td><p>这项功能将添加注册表设置禁止显示错误检查屏幕。</p></td>
</tr>
</tbody>
</table>

 

### <a name="other-features"></a>其他功能

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>功能 </th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>FAKEVIBRA</p></td>
<td><p>这项功能将添加测试硬件通知驱动程序用于控制振动的反馈机制。</p></td>
</tr>
<tr class="even">
<td><p>IMGFAKELED</p></td>
<td><p>此功能将添加到图像控制 Led 测试硬件通知驱动程序。</p></td>
</tr>
<tr class="odd">
<td><p>LOCATIONFRAMEWORKAPP</p></td>
<td><p>这项功能将添加位置框架 LFApp、 测试和调试应用程序。</p></td>
</tr>
<tr class="even">
<td><p>PSEUDOLOCALES</p></td>
<td><p>此功能允许使用伪区域设置本地化测试。 有关详细信息，请参阅 MSDN 上的<a href="http://msdn.microsoft.com/library/windows/desktop/dd374118.aspx">使用仿真的区域设置进行本地化测试</a>。</p></td>
</tr>
<tr class="odd">
<td><p>GRAPHICSSOFTWAREDRIVERS</p></td>
<td><p>此功能增加了 BasicDisplay 和变形的图形驱动程序。 早期的设备提出的 SoC 供应商通常使用此功能。</p></td>
</tr>
</tbody>
</table>

 

## <a name="microsoft-internal-features"></a>Microsoft 的内部功能


以下组件是保留 Microsoft 仅供内部使用，但在此记录的完整性。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>功能 </th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>SELFHOST</p></td>
<td><p>这项功能添加组件以独占方式用于在 Microsoft 的自托管方案。</p></td>
</tr>
<tr class="even">
<td><p>IMGUPD_POWERTOYS</p></td>
<td><p>此功能包括与更新设备上的程序包相关的几个实用程序应用程序。</p></td>
</tr>
<tr class="odd">
<td><p>INSTRUMENT_FOR_COVERAGE</p></td>
<td><p>将在本文档的后面的版本中提供此功能的信息。</p></td>
</tr>
<tr class="even">
<td><p>IMGFAKEMODEM</p></td>
<td><p>将在本文档的后面的版本中提供此功能的信息。</p></td>
</tr>
<tr class="odd">
<td><p>USE_WMC</p></td>
<td><p>此功能用于 Microsoft 测试。</p></td>
</tr>
<tr class="even">
<td><p>CORTANADBG_TEST_PROTECTED</p></td>
<td><p>此功能仅用于 Microsoft 非常。</p></td>
</tr>
<tr class="odd">
<td><p>有限</p></td>
<td><p>此功能仅用于 Microsoft 非常。</p></td>
</tr>
<tr class="even">
<td><p>TEST_PROTECTED</p></td>
<td><p>此功能仅用于 Microsoft 非常。</p></td>
</tr>
<tr class="odd">
<td><p>SELFHOST_PROTECTED</p></td>
<td><p>此功能仅用于 Microsoft 非常。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[构建和闪烁的图像](building-and-flashing-images.md)

 

 

[发送有关此主题的意见的评论](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_phFlashing\p_phFlashing%5D:%20Optional%20features%20for%20building%20mobile%20images%20%20RELEASE:%20%2810/4/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "发送有关此主题的意见的评论")





