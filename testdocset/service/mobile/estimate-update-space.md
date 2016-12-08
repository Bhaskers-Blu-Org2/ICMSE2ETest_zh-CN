---
author: kpacquer
Description: "估计更新空间"
ms.assetid: dfd2eed9-3202-4a08-87d1-d1f4f132b7c5
MSHAttr: PreferredLib:/library/windows/hardware
title: "估计更新空间"
ms.openlocfilehash: f272e3d69b8a3adb9bbd15ec4a359bfcb59db302
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="estimate-update-space"></a>估计更新空间


要下载并应用更新设备上所需的内存量可能千差万别。 评估要求的原则考虑事项是更新和下载、 准备，并安装所需的处理工作区的类型。

**重要**  
由于压缩、 目标的包和更新的特定二进制内容等因素，估计过程是不精确的。 Oem 必须单独测试以确定所需的确切大小的更新。

 

## <a name="span-idfactorsthataffectupdatespacerequirementsspanspan-idfactorsthataffectupdatespacerequirementsspanspan-idfactorsthataffectupdatespacerequirementsspanfactors-that-affect-update-space-requirements"></a><span id="Factors_that_affect_update_space_requirements"></span><span id="factors_that_affect_update_space_requirements"></span><span id="FACTORS_THAT_AFFECT_UPDATE_SPACE_REQUIREMENTS"></span>影响因素更新空间要求


在更新过程中，每个都有自己的空间考虑有三个阶段︰ 下载、 处理和完成。

### <a name="span-idcompressionfordownloadingspanspan-idcompressionfordownloadingspanspan-idcompressionfordownloadingspancompression-for-downloading"></a><span id="Compression_for_downloading"></span><span id="compression_for_downloading"></span><span id="COMPRESSION_FOR_DOWNLOADING"></span>下载的压缩

更新被压缩为传送到设备。 作为过渡过程的更新，更新被解压。 可以为变量度压缩二进制可执行文件、 文本文件和站点地图数据。 正因为如此，可以不同的压缩量。

### <a name="span-idupdateprocessingspanspan-idupdateprocessingspanspan-idupdateprocessingspanupdate-processing"></a><span id="Update_processing"></span><span id="update_processing"></span><span id="UPDATE_PROCESSING"></span>更新处理

当更新已准备好安装时，它们将在验证过程中解压缩。 额外的空间是临时和有效性所必需的。 在最后一个阶段的更新，当设备引导至操作系统的更新，更新应用和临时工作区返回到操作系统、 更新完成后。

所有更新的处理都需要设置的空间量。 工作区位于主操作系统分区。 在更新过程中不使用 SD 卡和用户数据存储区。 工作区的大小大约是 50 MB。

### <a name="span-idupdatedstatespanspan-idupdatedstatespanspan-idupdatedstatespanupdated-state"></a><span id="Updated_state"></span><span id="updated_state"></span><span id="UPDATED_STATE"></span>更新后的状态

根据更新的内容，它所消耗的图像的最终大小而异。 如果更新会覆盖现有的文件包，有可能减少或增加可用的空间量可用设备上。 例如，如果更新将新文件添加到操作系统中，最终大小会反映新的文件的大小。

## <a name="span-idestimatingsizerequirementsspanspan-idestimatingsizerequirementsspanspan-idestimatingsizerequirementsspanestimating-size-requirements"></a><span id="Estimating_size_requirements"></span><span id="estimating_size_requirements"></span><span id="ESTIMATING_SIZE_REQUIREMENTS"></span>估计大小要求


差别更新包含只更新程序包所需的差异。 Nondifferential 的更新都是价内税和独立。 若要将某个差异更新应用到包中，中间包创建差异，然后适用于。 这意味着相当小的差异更新可以将大量的额外空间带到舞台并应用如果目标的包很大。 大多数的 Microsoft 操作系统更新差异和增量针对特定的操作系统版本。

### <a name="span-iddifferentialupdatesspanspan-iddifferentialupdatesspanspan-iddifferentialupdatesspandifferential-updates"></a><span id="Differential_updates"></span><span id="differential_updates"></span><span id="DIFFERENTIAL_UPDATES"></span>差别更新

要估计所需的某个差异更新，必须确定作为更新目标的包的大小的空间。

*(以 MB 为单位目标的包\*1.5) + 工作空间 = 以 mb 为单位所需的估计更新空间。*

例如，如果目标包的大小为 4 MB，计算将如下︰

*(4 \* 1.5) + 50 MB = 62 MB。*

请注意，在估计中不使用包含差异更新的包的大小。

### <a name="span-idnondifferentialupdatesspanspan-idnondifferentialupdatesspanspan-idnondifferentialupdatesspannondifferential-updates"></a><span id="Nondifferential_updates"></span><span id="nondifferential_updates"></span><span id="NONDIFFERENTIAL_UPDATES"></span>Nondifferential 更新

要估计典型的 nondifferential OEM 更新所需的空间，请使用此公式︰

*(以 MB 为单位更新\*1.5) + 以 mb 为单位的工作空间 = 以 mb 为单位所需的估计更新空间。*

### <a name="span-idsvpartitionupdatesspanspan-idsvpartitionupdatesspanspan-idsvpartitionupdatesspansv-partition-updates"></a><span id="SV_partition_updates"></span><span id="sv_partition_updates"></span><span id="SV_PARTITION_UPDATES"></span>SV 分区更新

有关信息的 SV 分区更新的大小估计与硅片供应商。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[更新](index.md)

 

 






