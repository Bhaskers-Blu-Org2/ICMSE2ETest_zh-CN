---
author: kpacquer
Description: "重置设备解决了大量关键方案︰ 用户可能想要重置的设备来将它转移到另一个所有者。"
ms.assetid: 2db677f1-edf6-421d-8482-770ee5f16140
MSHAttr: PreferredLib:/library/windows/hardware
title: "重置移动设备"
ms.openlocfilehash: ada132c1d114158c59f856d4380a97a6126883ff
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="resetting-a-mobile-device"></a>重置移动设备


重置设备解决了大量关键的方案︰

-   用户可能需要重置的设备来将它转移到另一个所有者。
-   设备已丢失或被盗以及所有者想要远程重新启动设备
-   该设备属于一个单位，并组织想要远程重新启动设备。 例如，当雇员离开公司。
-   该设备出现故障，用户想要将设备重置。
-   OEM 出厂测试已完成，并且想要重置该设备 （还可以选择保留预加载的站点地图数据）。

**重要**  
重置设备时，它不返回其原始出厂状态。 例如，添加或更新过程中修改的任何包保持。 要返回到原始出厂状态的设备，必须使用原始出厂映像闪烁。

 

## <a name="span-idwaystoresetamobiledevicespanspan-idwaystoresetamobiledevicespanspan-idwaystoresetamobiledevicespanways-to-reset-a-mobile-device"></a><span id="Ways_to_reset_a_mobile_device"></span><span id="ways_to_reset_a_mobile_device"></span><span id="WAYS_TO_RESET_A_MOBILE_DEVICE"></span>如何重置移动设备


下面的重新设置选项可供不同类型的用户。

### <a name="span-idendusersspanspan-idendusersspanspan-idendusersspanend-users"></a><span id="End_users"></span><span id="end_users"></span><span id="END_USERS"></span>最终用户

最终用户可以通过下列选项来调用重置︰

-   如果可以访问设置，点击**设置** &gt; **系统** &gt; **有关** &gt; **重置您的电话**。

    **请注意**  
    如果设备没有响应，用户应首先尝试重新启动它。在本主题的后面部分，请参阅[重新启动操作系统](#restarting)。

     

-   如果无法访问设置，请执行以下步骤︰

    1.  请关闭该设备。

    2.  按住按钮增大音量直到感叹号出现在屏幕上打开该设备。

    3.  按此顺序按下四个按钮︰ 调高音量、 调低音量、 电源、 调低音量。

-   在 WindowsPhone.com 网站上使用擦除功能远程设备重置。 有关详细信息，请参阅[查找丢失的电话](http://www.windowsphone.com/how-to/wp8/basics/find-a-lost-phone)。

### <a name="span-idpartnersspanspan-idpartnersspanspan-idpartnersspanpartners"></a><span id="Partners"></span><span id="partners"></span><span id="PARTNERS"></span>合作伙伴

除了选项列在前面的部分中，合作伙伴如 Oem 和移动运营商具有以下附加选项来调用重置︰

-   可以通过调用 ResetPhone 或 ResetPhoneEx 函数来制造方案期间以编程方式调用重置。

-   在非零售映像 （即，在 OEMInput 文件中的**ReleaseType**元素设置为**测试**的图像），可以通过开发人员引导菜单调用重置。

**请注意** 最终用户工厂重置过程不适用于在工厂车间使用。 我们建议重置以编程方式在工厂或翻新设置电话。 它是快于重置电话，通过**设置** &gt;**系统**&gt; **有关** &gt; **重置您的电话**。

 

您可以验证所有数据已成功都删除通过使用 GetResetLogs.exe。 日志文件将显示重置设备之后没有删除任何文件。

### <a name="span-identerprisesspanspan-identerprisesspanspan-identerprisesspanenterprises"></a><span id="Enterprises"></span><span id="enterprises"></span><span id="ENTERPRISES"></span>企业

在企业方案中使用设备管理软件来管理移动设备，其中可以远程调用重置通过以下选项︰

-   可以通过使用 Exchange ActiveSync RemoteWipe 策略设置调用重置。 更多的信息，请参阅[Windows Phone Exchange ActiveSync 概述](http://go.microsoft.com/fwlink/?LinkId=270085)白皮书已发布上的 Microsoft 下载中心。

-   可以通过使用 OMA DM 调用重置。 有关详细信息，请参阅[RemoteWipe CSP](http://go.microsoft.com/fwlink/p/?LinkId=708418)。

## <a name="span-idoperationsperformedbyphoneresetspanspan-idoperationsperformedbyphoneresetspanspan-idoperationsperformedbyphoneresetspanoperations-performed-by-phone-reset"></a><span id="Operations_performed_by_phone_reset"></span><span id="operations_performed_by_phone_reset"></span><span id="OPERATIONS_PERFORMED_BY_PHONE_RESET"></span>通过电话重新设置执行操作


重置将执行以下操作︰

-   它使用 chkdsk 工具来扫描主操作系统的损坏问题，它会尝试自动修复问题，如果发现任何。 由重置操作使用 ResetPhoneEx 函数**重置\_保留\_用户\_商店\_数据**标志，该操作也会扫描用户数据分区。

-   执行快速格式化用户数据分区。 （如映射数据） 的用户数据分区上的所有预先填充的数据将被删除并将需要重新加载。

-   它将删除所有用户安装应用商店应用程序。 用户可以使用备份和还原功能恢复的已安装应用程序。

-   它从操作系统分区中移除包不所描述的任何文件。 程序包中描述的更新，因为更新将显示重置后。

-   它通过使用期间第一次启动，它在向其中添加注册表更改已收到更新包中的所有已保存的存储的副本重新创建注册表。

-   如果设备加密启用重置操作之前，它会永久删除活动设备加密密钥。 但是，设备加密将继续启用后重置操作使用不同的加密密钥。

-   如果该设备有 SD 卡，在某些情况下，该 SD 卡也重新格式化。 有关更多详细信息，请参见本主题后面的[重新格式化 SD 卡](#sdcard)。

在重置保留下列项目︰

-   更新包被发送到该设备并由用户安装。

-   已发送更新的注册表更改。

-   DPP 分区，例如校准数据中的所有数据。

-   如上文所述，主操作系统和用户数据分区的内容将被重置。 任何其他操作系统分区中存储 does 保持不变。

-   静态的冷启动置备 XML。

-   如果使用 ResetPhoneEx 函数来启动重置操作，某些用户存储中的数据可以有选择地保留通过指定**重置\_保留\_用户\_存储\_数据**在*dwFlags*参数中。 目前，唯一保留的用户存储数据是预加载的站点地图数据。

### <a name="span-idsdcardspanspan-idsdcardspanreformatting-the-sd-card"></a><span id="sdcard"></span><span id="SDCARD"></span>重新格式化 SD 卡

如果设备包括 SD 卡，可以在下面的重置方案中重新格式化 SD 卡︰

-   用户启动的系统设置，在重置操作，用户选择的选项重新格式化 SD 卡和重置设备。

-   用户启动的 WindowsPhone.com 网站从远程重置操作。 在这种情况下，重置操作自动重新格式化 SD 卡中;没有保持 SD 卡内容的选项。

-   重置将启动操作远程受控设备上通过使用 Exchange ActiveSync 或使用 OMA DM 和 RemoteWipe 配置服务提供程序。 在这种情况下，重置操作自动重新格式化 SD 卡中;没有保持 SD 卡内容的选项。 有关详细信息，请参阅[RemoteWipe CSP](http://go.microsoft.com/fwlink/p/?LinkId=708418)。

-   通过以下方式使用 ResetPhone 或 ResetPhoneEx 函数的合作伙伴应用程序以编程方式启动重置操作︰

    -   ResetPhone︰**真**向传递*bWipeStorageCard*参数。

    -   ResetPhoneEx︰ 传递**重置\_擦拭\_SD**到*dwFlags*参数。

在每种情况下，操作系统尝试执行快速格式化 SD 卡。 如果重新格式化 SD 卡的尝试不成功，该操作才继续重置过程的其余部分。

## <a name="span-idomaprovisioningandresettingthedevicespanspan-idomaprovisioningandresettingthedevicespanspan-idomaprovisioningandresettingthedevicespanoma-provisioning-and-resetting-the-device"></a><span id="OMA_provisioning_and_resetting_the_device"></span><span id="oma_provisioning_and_resetting_the_device"></span><span id="OMA_PROVISIONING_AND_RESETTING_THE_DEVICE"></span>OMA 资源调配和重置设备


重置设备时，将保留 OMA 客户端资源调配和 OMA 设备管理 (DM) 存储在调制解调器的设置。 重置设备时，不会保留更改进行自动配置的注册表设置。 有关详细信息，请参阅[RemoteWipe CSP](http://go.microsoft.com/fwlink/p/?LinkId=708418)。

## <a name="span-idpersistingprovisionedcontentfromtheworkplacespanspan-idpersistingprovisionedcontentfromtheworkplacespanspan-idpersistingprovisionedcontentfromtheworkplacespanpersisting-provisioned-content-from-the-workplace"></a><span id="Persisting_provisioned_content_from_the_workplace"></span><span id="persisting_provisioned_content_from_the_workplace"></span><span id="PERSISTING_PROVISIONED_CONTENT_FROM_THE_WORKPLACE"></span>保持工作场所的提供的内容


如果该设备已应用与资源调配包或组织使用 EnterpriseExtFileSystem 配置服务提供程序提供的内容推送到永久的位置，提供的内容可随重置使用以下方式︰

-   用户启动的系统设置，在重置操作，用户选择的选项来保持工作场所的提供的内容。
-   重置将启动操作远程受控设备上使用的 OMA DM 和 RemoteWipe 配置服务提供程序 （doWipePersistProvisionedData 节点）。

关于 RemoteWipe 配置服务提供程序和 EnterpriseExtFileSystem 配置服务提供程序的详细信息，请参阅[RemoteWipe CSP](http://go.microsoft.com/fwlink/p/?LinkId=708418)。

## <a name="span-idrestartingspanspan-idrestartingspanspan-idrestartingspanrestarting-the-os"></a><span id="Restarting"></span><span id="restarting"></span><span id="RESTARTING"></span>重新启动操作系统


如果该设备不响应正常关机过程或单独的电源按钮，该设备可以被迫使用的按钮组合重新启动。 此过程不重置该设备;相反，它提供了另一种方法来重新启动响应的设备。

要重新启动该设备，请按住音量按钮和电源按钮 10 秒钟。

 

 





