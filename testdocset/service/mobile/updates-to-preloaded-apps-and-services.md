---
author: kpacquer
Description: "对预加载应用程序和服务"
ms.assetid: d3e08bae-f997-4593-9c6d-552fdd7a3d11
MSHAttr: PreferredLib:/library/windows/hardware
title: "对预加载应用程序和服务"
ms.openlocfilehash: ba4bc7d278f23ef2e83affedba7dea9b5756db6c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="updates-to-preloaded-apps-and-services"></a>对预加载应用程序和服务


合作伙伴应用程序可以包括在映像和期间第一次启动安装到用户存储区。

预加载应用程序的更新被分别传递从操作系统更新，并且必须由用户启动。 因此，必须用预加载应用程序来管理与主操作系统和 OEM BSP 更新兼容性。 此外，用户可以启动备份和还原序列或重置该设备，其中之一可能会更改预加载应用程序的当前版本。 必须开发一种战略来测试并解决了所有可能的方案。

应用程序预加载的*系统设置*，Oem 可以公开硬件组件的自定义设置。 有其他重要更新系统设置应用程序的注意事项。 有关更多信息，请参阅[系统设置应用程序和更新](system-settings-apps-and-updates.md)。

## <a name="span-idsummaryofpreloadedappscenariosspanspan-idsummaryofpreloadedappscenariosspanspan-idsummaryofpreloadedappscenariosspansummary-of-preloaded-app-scenarios"></a><span id="Summary_of_preloaded_app_scenarios"></span><span id="summary_of_preloaded_app_scenarios"></span><span id="SUMMARY_OF_PRELOADED_APP_SCENARIOS"></span>概述了预加载应用程序方案


下表总结了预加载应用程序方案。

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">OTA 更新</th>
<th align="left">用户启动存储更新</th>
<th align="left">备份和恢复</th>
<th align="left">Reset</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>预加载应用程序更新无法创建 oem;当前已安装的应用程序不更新，只存储的一个。</p></td>
<td align="left"><p>活动的应用程序进行更新;存储的应用程序保持不变。</p></td>
<td align="left"><p>重新安装存储的设备上的应用程序。 如果尚未更新存储的版本，用户将需要从存储库中下载更新的版本。</p></td>
<td align="left"><p>重新安装存储的设备上的应用程序。 如果尚未更新存储的版本，用户将需要从存储库中下载更新的版本。</p></td>
</tr>
</tbody>
</table>

 

这些示例方案演示，并且在不会捕获所有可能的客户使用方案或更新版本的可能的组合。 Oem 必须确定可能的使用方案和测试那些准备更新时。

## <a name="span-idmanagingupdatestopreloadedappsspanspan-idmanagingupdatestopreloadedappsspanspan-idmanagingupdatestopreloadedappsspanmanaging-updates-to-preloaded-apps"></a><span id="Managing_updates_to_preloaded_apps"></span><span id="managing_updates_to_preloaded_apps"></span><span id="MANAGING_UPDATES_TO_PRELOADED_APPS"></span>管理更新预加载应用程序


预加载应用程序使用的存储区传递机制的更新。 当用户运行应用商店应用程序时，会显示未完成的更新;这些更新包括预加载应用程序的可用更新。 存储更新总是升级到最新版本的应用程序从任何以前的版本。

## <a name="span-idpreloadedappotaupdatesspanspan-idpreloadedappotaupdatesspanspan-idpreloadedappotaupdatesspanpreloaded-app-ota-updates"></a><span id="Preloaded_app_OTA_updates"></span><span id="preloaded_app_ota_updates"></span><span id="PRELOADED_APP_OTA_UPDATES"></span>OTA 预加载应用程序的更新


若要允许的预加载应用程序中，如果重置设备安装最新版本，可以预加载应用程序准备无线 (OTA) 软件包更新。 此 OTA 更新不会更新设备; 上的应用程序的当前有效版本它只更新如果重置设备，则使用存储的版本。 这意味着可以在设备上预先加载的应用程序的两个不同的版本

例如，如果设备附带已预加载应用程序预加载的版本 1.0 更新 OTA，和用户下载版本 1.1 的预加载应用程序从存储区，存储和当前版本都存在于设备上，如下图中所示。

![oem\-预加载\-应用程序](images/oem-preloaded-app.png)

## <a name="span-idbackupandrestorescenariosspanspan-idbackupandrestorescenariosspanspan-idbackupandrestorescenariosspanbackup-and-restore-scenarios"></a><span id="Backup_and_restore_scenarios"></span><span id="backup_and_restore_scenarios"></span><span id="BACKUP_AND_RESTORE_SCENARIOS"></span>备份和还原方案


预加载应用程序则不会还原从云;相反，预加载应用程序将重新安装在设备上使用的存储的版本。 如果已更新预加载应用程序的存储的版本 OTA，更新后的版本在安装时被还原的设备。 如果用户重置设备和还原，并且尚未更新存储的版本，用户将需要检查的预加载应用程序的更新的存储。

这种现象是不同于未预先加载到设备的存储应用程序。 当备份电话后时，安装的应用程序的列表存储为备份的一部分。 还原后设备，从云中，使用手机备份时创建的应用程序列表安装最新版本的应用程序。 有关此功能的详细信息，请参阅[备份我的资料](http://go.microsoft.com/fwlink/p/?LinkId=331631)。

## <a name="span-idresetscenariosspanspan-idresetscenariosspanspan-idresetscenariosspanreset-scenarios"></a><span id="Reset_scenarios"></span><span id="reset_scenarios"></span><span id="RESET_SCENARIOS"></span>重置方案


重置设备，预加载应用程序返回到存储设备; 上一个应用程序软件包的版本这可能是设备提供的版本。 电话已收到任何操作系统更新重置之后还有设备上的活动。 这意味着原预加载应用程序可能需要采用与较新版本的操作系统和 BSP 的较新版本运行。 这些依赖关系和相互作用应该被视为准备预加载应用程序的更新。 操作系统重置行为有关的详细信息，请参阅[重置设备](../../manufacture/mobile/resetting-a-phone-during-manufacturing.md)。

## <a name="span-idupdatestonativeservicesandserviceagentsspanspan-idupdatestonativeservicesandserviceagentsspanspan-idupdatestonativeservicesandserviceagentsspanupdates-to-native-services-and-service-agents"></a><span id="Updates_to_native_services_and_service_agents"></span><span id="updates_to_native_services_and_service_agents"></span><span id="UPDATES_TO_NATIVE_SERVICES_AND_SERVICE_AGENTS"></span>对本机服务和服务代理的更新


Oem 可以使用本机服务和服务代理中应对连续运行代码的情况下操作系统。 因为本机服务和服务代理使用两种不同的方法包括在操作系统中，创建和管理不同的更新。

### <a name="span-idnativeservicesspanspan-idnativeservicesspanspan-idnativeservicesspannative-services"></a><span id="Native_services"></span><span id="native_services"></span><span id="NATIVE_SERVICES"></span>本机服务

本机服务通过将相关的代码添加到图像中包含的包包含在操作系统中。 它们像任何其他程序包在操作系统更新。

### <a name="span-idserviceagentsspanspan-idserviceagentsspanspan-idserviceagentsspanservice-agents"></a><span id="Service_agents"></span><span id="service_agents"></span><span id="SERVICE_AGENTS"></span>服务代理

一个预加载的应用程序中包含多个服务代理。 如同所有预加载应用程序，使用该存储区传递更新。 每个服务代理应用程序可以有多个运行中的服务代理。 如果任一服务代理需要更新，包含服务代理的应用程序需要更新。 一般情况下，服务代理行为类似于预加载应用程序更新、 重置和还原方案中的。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题

[更新](index.md)

[系统设置应用程序和更新](system-settings-apps-and-updates.md)

 

 


