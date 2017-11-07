---
author: kpacquer
Description: "更新要求"
ms.assetid: 3f2c96f5-cc52-44a2-b61d-279b649995fc
MSHAttr: PreferredLib:/library/windows/hardware
title: "更新要求"
ms.openlocfilehash: 2b62f3b9adb69bda3e6707c18b594a490fb014d4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="update-requirements"></a>更新要求


本部分包含将在零售设备安装的任何更新的要求。

## <a name="span-idgeneralupdaterequirementsspanspan-idgeneralupdaterequirementsspanspan-idgeneralupdaterequirementsspangeneral-update-requirements"></a><span id="General_update_requirements"></span><span id="general_update_requirements"></span><span id="GENERAL_UPDATE_REQUIREMENTS"></span>一般更新要求


OEM 更新软件包必须符合以下要求。

-   必须通过使用存储区更新预加载应用程序。

-   更新目标信息必须设置在图像和移动操作员 ID 和设备 ID 必须提交的每个更新请求与 OEM 合作伙伴。 有关创建更新请求时设置的移动操作员 ID 和设备 ID 的详细信息，请参阅[新建 RequestForUpdate cmdlet](new-requestforupdate-cmdlet.md)。

-   获取所有包，Oem 必须设置必需的属性值。 有关详细信息，请参阅[包项目文件的主元素和属性](https://msdn.microsoft.com/library/dn756796)中的"包属性"一节。

## <a name="span-idwindowsstandardpackageconfigurationwspccompliancespanspan-idwindowsstandardpackageconfigurationwspccompliancespanspan-idwindowsstandardpackageconfigurationwspccompliancespanwindows-standard-package-configuration-wspc-compliance"></a><span id="Windows_Standard_Package_Configuration__WSPC__compliance"></span><span id="windows_standard_package_configuration__wspc__compliance"></span><span id="WINDOWS_STANDARD_PACKAGE_CONFIGURATION__WSPC__COMPLIANCE"></span>Windows 标准软件包配置 (WSPC) 的法规遵从性


零售包必须符合[Windows 标准包装配置 (WSPC) 零售图像的要求](https://msdn.microsoft.com/library/dn756781)。

当您提交的固件更新时，映像验证执行两次︰

-   当您不使用-NonWspcCompliant 参数运行[初始化 FirmwareSubmission cmdlet](initialize-firmwaresubmission-cmdlet.md)时，接收客户端验证提交。 如果图像验证失败，图像提交初始化失败。

-   提交更改后，Microsoft 更新系统执行映像验证第二次之前处理它的代码签名。 如果映像验证此检查中失败，提交不能继续进行处理的代码签名。

## <a name="span-idfirmwareversioningrequirementsspanspan-idfirmwareversioningrequirementsspanspan-idfirmwareversioningrequirementsspanfirmware-versioning-requirements"></a><span id="Firmware_versioning_requirements"></span><span id="firmware_versioning_requirements"></span><span id="FIRMWARE_VERSIONING_REQUIREMENTS"></span>固件版本控制要求


**版本化方案**

创建版本控制方案，其中包括由四部分构成的版本号。

新的包数大于旧包装编号时，仅更新包。 包编号必须使用分层方案从左到右，这样该版本 2.0.0.0 大于版本 1.9.9.9。

我们建议使用硅片供应商 (SV) 版本号，跟 OEM 版本编号。 示例︰ *SV-Major.SV-Minor.OEM-Major.OEM-次要*。 为一致起见，请考虑使用内部版本环境变量，如日期时创建的版本化方案。

每个新的更新，创建一个新的版本号。 提交更新时，请提供旧的和新的版本数。 例如︰

1.  0001.0001.0001.20140801-&gt; 0001.0040.0055.20140808

2.  0001.0040.0055.20140808-&gt; 0001.0040.0077.20140815

3.  0001.0040.0077.20140815-&gt; 0002.0000.0077.20140822

（对于包并不增加版本） 更新生成或更新生成进程的完全故障期间无法满足这一要求导致或者被忽略的包。

**若要避免版本控制错误︰**

-   跟踪的单独的电子表格中的版本号。

-   不发送两个版本具有相同的上一版本编号相同的包-每个更新必须链接在一起到以前的版本。 设备更新发布服务有权拒绝为新的更新的源版本不包括上一次更新的目标版本的更新 (RFUs) 的请求。

**版本控制的常见问题解答**

*如果不更改我的版本号和包所做的更改的内容会怎么样？*

包将被视为是与现有版本相同，并且它将不下载和安装用户更新其设备

*在我所有的货物应使用相同的版本号？*

有些版本可能不同如果他们准确地指示将使用以前的包版本。 您应该与用于，例如版本编号均递增方式和中四部分版本数字代表什么每个元素的版本化方案保持一致。

*所有驱动程序的版本应匹配的每个更新软件包的版本吗？*

它建议让司机的包版本号码会遵循类似的版本化方案，尽最大可能，但它不是一个要求所有版本的所有软件包都必须完全相同。 任何更新的包必须具有更高的版本号。

## <a name="span-idupdatepartitionrequirementsspanspan-idupdatepartitionrequirementsspanspan-idupdatepartitionrequirementsspanupdate-partition-requirements"></a><span id="Update_partition_requirements"></span><span id="update_partition_requirements"></span><span id="UPDATE_PARTITION_REQUIREMENTS"></span>更新分区要求


**警告**  
到设备安装更新时，将保留所有用户数据和设置。 您需要确保该用户设置将被保留当更新设备。

 

主操作系统进行更新的大部分。 可能需要更新其他分区的设备。 本节提供了分区可以更新有关的信息。

对于有关 SV 分区的信息，请与 SoC 供应商联系。

**重要**  
在设备上不支持分区布局的更改。  如果提交两个分区包依赖于新的分区布局，未定义的结果应用到设备时可能会发生

 

可以更新下列分区︰

-   EFIESP-启动管理器、 启动配置数据库 （uefi） 的应用程序

-   （UEFI)

-   SBL1，SBL2，SBL3-安全引导加载程序

-   RPM

-   TZ

-   PLAT — ACPI 表

-   WINSECAPP

-   主操作系统

Oem 必须更新以下分区。

-   DPP

-   数据，用户数据分区

-   SD 卡

-   更新操作系统

## <a name="span-idacpitableversioningduringbspupdatesspanspan-idacpitableversioningduringbspupdatesspanspan-idacpitableversioningduringbspupdatesspanacpi-table-versioning-during-bsp-updates"></a><span id="ACPI_table_versioning_during_BSP_updates"></span><span id="acpi_table_versioning_during_bsp_updates"></span><span id="ACPI_TABLE_VERSIONING_DURING_BSP_UPDATES"></span>BSP 更新期间的 ACPI 表版本控制


每次您更改 ACPI 表中 BSP 更新，应该增加**DefinitionBlock**对象的表中的**OEMRevision**字段。 做这有助于确保操作系统将使用最新的 ACPI 配置数据。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[新 RequestForMicrosoftUpdate cmdlet](new-requestformicrosoftupdate-cmdlet.md)

[新 RequestForUpdate cmdlet](new-requestforupdate-cmdlet.md)

 

 






