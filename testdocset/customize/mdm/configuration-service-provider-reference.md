---
title: "配置服务提供程序的引用"
description: "配置服务提供程序 (CSP) 是一个接口，用于读取、 设置、 修改或删除设备上的配置设置。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 71823658-951f-4163-9c40-c4d4adceaaec
ms.openlocfilehash: 04bea68be2c71dd928d378f71ada01affdb1a9cd
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="configuration-service-provider-reference"></a>配置服务提供程序的引用


配置服务提供程序 (CSP) 是一个接口，用于读取、 设置、 修改或删除设备上的配置设置。 这些设置映射到注册表项或文件。 某些配置服务提供程序支持 WAP 格式、 一些支持 SyncML 和一些支持这两种。 SyncML 是只使用的过 – – 空气的开放手机联盟设备管理 (OMA DM)，而 WAP 可以是使用的通过 – – 空气 OMA 客户端资源调配，或者它可以作为包含在电话映像在引导过程中安装的.provxml 文件。

有关映射到这些 Csp 的桥 WMI 提供程序类的信息，请参阅[每台 MDM 桥 WMI 提供程序](https://msdn.microsoft.com/library/windows/hardware/dn905224)。 新的 Csp 添加 Windows 10 中的列表，请参阅[Windows 10 1511 版本中添加新的 Csp](#newcsps)。 查看[列表中的 Csp 支持 Windows 全息](#hololens)和[Csp 中 Microsoft Surface 集线器支持的列表](#surfacehubcspsupport)的其他信息。

下表显示了配置服务提供程序支持 Windows 10。  

> **重要** 水平定位表，表上单击然后使用键盘上的向左、 右滚动键或在表的底部使用滚动条。

<table>
<colgroup>
<col width="12%" />
<col width="12%" />
<col width="12%" />
<col width="12%" />
<col width="12%" />
<col width="12%" />
<col width="12%" />
<col width="12%" />
</colgroup>
<thead>
<tr class="header">
<th>配置服务提供程序</th>
<th>在 Windows 中 10 专业支持</th>
<th>在 Windows 10 企业支持</th>
<th>支持 Windows 10 教育</th>
<th>支持 Windows 10 家</th>
<th>支持 Windows 10 移动</th>
<th>在 Windows 10 移动企业支持</th>
<th>支持 Windows 10 IoT 核心 （IoT 核心）</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>[动态同步 CSP](activesync-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[AllJoynManagement 的 CSP](alljoynmanagement-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
</tr>
<tr class="odd">
<td>[应用 CSP](application-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
</tr>
<tr class="even">
<td>[AppLocker CSP](applocker-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[AssignedAccess 的 CSP](assignedaccess-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[引导的 CSP](bootstrap-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[BrowserFavorite 的 CSP](browserfavorite-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[CellularSettings 的 CSP](cellularsettings-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[CertificateStore 的 CSP](certificatestore-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
</tr>
<tr class="even">
<td>[ClientCertificateInstall 的 CSP](clientcertificateinstall-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
</tr>
<tr class="odd">
<td>[CM_CellularEntries 的 CSP](cm-cellularentries-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[CM_ProxyEntries 的 CSP](cm-proxyentries-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[CMPolicy 的 CSP](cmpolicy-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[CMPolicyEnterprise 的 CSP](cmpolicyenterprise-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" />*</td>
<td><img src="images/checkmark.png" alt="check mark" />*</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[CustomDeviceUI 的 CSP](customdeviceui-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
</tr>
<tr class="even">
<td>[Defender CSP](defender-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[DevDetail 的 CSP](devdetail-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
</tr>
<tr class="even">
<td>[DeviceInstanceService 的 CSP](deviceinstanceservice-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[DeviceLock 的 CSP](devicelock-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[DeviceManageability 的 CSP](devicemanageability-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[DeviceStatus 的 CSP](devicestatus-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[DevInfo 的 CSP](devinfo-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
</tr>
<tr class="odd">
<td>[DiagnosticLog 的 CSP](diagnosticlog-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
</tr>
<tr class="even">
<td>[DMAcc 的 CSP](dmacc-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
</tr>
<tr class="odd">
<td>[DMClient 的 CSP](dmclient-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
</tr>
<tr class="even">
<td>[电子邮件 2 CSP](email2-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[EnterpriseAPN 的 CSP](enterpriseapn-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" />只有版本 1507</td>
<td><img src="images/checkmark.png" alt="check mark" />只有版本 1507</td>
<td><img src="images/checkmark.png" alt="check mark" />只有版本 1507</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[EnterpriseAppManagement 的 CSP](enterpriseappmanagement-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[EnterpriseAssignedAccess 的 CSP](enterpriseassignedaccess-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[EnterpriseDataProtection 的 CSP](enterprisedataprotection-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[EnterpriseDesktopAppManagement 的 CSP](enterprisedesktopappmanagement-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[EnterpriseExt 的 CSP](enterpriseext-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[EnterpriseExtFileSystem 的 CSP](enterpriseextfilessystem-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[EnterpriseModernAppManagement 的 CSP](enterprisemodernappmanagement-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
</tr>
<tr class="odd">
<td>[文件系统 CSP](filesystem-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" />
<p>（仅提供）</p></td>
<td><img src="images/checkmark.png" alt="check mark" />
<p>（仅提供）</p></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[HealthAttestation 的 CSP](healthattestation-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[CSP 热点](hotspot-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[映射的 CSP](maps-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[NAP CSP](nap-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[NAPDEF 的 CSP](napdef-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[NodeCache 的 CSP](nodecache-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[PassportForWork 的 CSP](passportforwork-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[CSP 的策略](policy-configuration-service-provider.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
</tr>
<tr class="even">
<td>[PolicyManager 的 CSP](policymanager-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[资源调配 CSP](provisioning-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" />
<p>（仅提供）</p></td>
<td><img src="images/checkmark.png" alt="check mark" />
<p>（仅提供）</p></td>
<td><img src="images/checkmark.png" alt="check mark" />
<p>（仅提供）</p></td>
<td><img src="images/checkmark.png" alt="check mark" />
<p>（仅提供）</p></td>
<td><img src="images/checkmark.png" alt="check mark" />
<p>（仅提供）</p></td>
<td><img src="images/checkmark.png" alt="check mark" />
<p>（仅提供）</p></td>
<td><img src="images/checkmark.png" alt="check mark" />
<p>（仅提供）</p></td>
</tr>
<tr class="even">
<td>[代理服务器 CSP](proxy-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[PXLOGICAL 的 CSP](pxlogical-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[重新启动 CSP](reboot-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[注册表的 CSP](registry-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[RemoteFind 的 CSP](remotefind-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[RemoteLock](remotelock-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[RemoteRing 的 CSP](remotering-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[RemoteWipe 的 CSP](remotewipe-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[报告 CSP](reporting-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[RootCATrustedCertificates 的 CSP](rootcacertificates-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
</tr>
<tr class="even">
<td>[SecureAssessment 的 CSP](secureassessment-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" />*</td>
<td><img src="images/checkmark.png" alt="check mark" />*</td>
<td><img src="images/checkmark.png" alt="check mark" />*</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[SecurityPolicy 的 CSP](securitypolicy-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[SharedPC 的 CSP](sharedpc-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" />*</td>
<td><img src="images/checkmark.png" alt="check mark" />*</td>
<td><img src="images/checkmark.png" alt="check mark" />*</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[存储 CSP](storage-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[SUPL CSP](supl-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[SurfaceHub](surfacehub-csp.md)</td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>[UnifiedWriteFilter 的 CSP](unifiedwritefilter-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[更新的 CSP](update-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
</tr>
<tr class="even">
<td>[VPN 的 CSP](vpn-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[VPNv2 的 CSP](vpnv2-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
</tr>
<tr class="even">
<td>[W4 应用 CSP](w4-application-csp.md)</td>
<td></td>
<td></td>
<td></td>
<td></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[w7 应用 CSP](w7-application-csp.md)</td>
<td></td>
<td></td>
<td></td>
<td></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[Wi-Fi CSP](wifi-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
</tr>
<tr class="odd">
<td>[Win32AppInventory 的 CSP](win32appinventory-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" />*</td>
<td><img src="images/checkmark.png" alt="check mark" />*</td>
<td><img src="images/checkmark.png" alt="check mark" />*</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[WindowsAdvancedThreatProtection 的 CSP](windowsadvancedthreatprotection-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" />*</td>
<td><img src="images/checkmark.png" alt="check mark" />*</td>
<td><img src="images/checkmark.png" alt="check mark" />*</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="odd">
<td>[WindowsLicensing 的 CSP](windowslicensing-csp.md)</td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
<tr class="even">
<td>[WindowsSecurityAuditing 的 CSP](windowssecurityauditing-csp.md)</td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/checkmark.png" alt="check mark" /></td>
<td><img src="images/crossmark.png" alt="cross mark" /></td>
</tr>
</tbody>
</table>

 

## <a name="a-href-idhololensacsps-supported-in-windows-holographic"></a><a href="" id="hololens"></a>Csp 支持 Windows 全息


下面的列表显示的配置中全息 Windows 版本支持的服务提供商。

| 配置服务提供程序                                                                        | 全息 Windows 版      | Windows 全息企业版 |
|-------------------------------------------------------------------------------------------------------|-------------------------------------|-------------------------------------------|
| [应用 csp](application-csp.md)                                     | ![复选标记](images/checkmark.png) | ![复选标记](images/checkmark.png)       |
| [applocker csp](applocker-csp.md)                                         | ![叉号](images/crossmark.png) | ![复选标记](images/checkmark.png)       |
| [certificatestore 的 csp](certificatestore-csp.md)                           | ![复选标记](images/checkmark.png) | ![复选标记](images/checkmark.png)       |
| [clientcertificateinstall 的 csp](clientcertificateinstall-csp.md)           | ![叉号](images/crossmark.png) | ![复选标记](images/checkmark.png)       |
| [devdetail 的 csp](devdetail-csp.md)                                         | ![复选标记](images/checkmark.png) | ![复选标记](images/checkmark.png)       |
| [devicestatus 的 csp](devicestatus-csp.md)                                                              | ![叉号](images/crossmark.png) | ![复选标记](images/checkmark.png)       |
| [devinfo 的 csp](devinfo-csp.md)                                             | ![复选标记](images/checkmark.png) | ![复选标记](images/checkmark.png)       |
| [diagnosticlog 的 csp](diagnosticlog-csp.md)                                 | ![叉号](images/crossmark.png) | ![复选标记](images/checkmark.png)       |
| [dmacc 的 csp](dmacc-csp.md)                                                 | ![复选标记](images/checkmark.png) | ![复选标记](images/checkmark.png)       |
| [dmclient 的 csp](dmclient-csp.md)                                           | ![复选标记](images/checkmark.png) | ![复选标记](images/checkmark.png)       |
| [enterprisemodernappmanagement 的 csp](enterprisemodernappmanagement-csp.md) | ![叉号](images/crossmark.png) | ![复选标记](images/checkmark.png)       |
| [nodecache 的 csp](nodecache-csp.md)                                         | ![复选标记](images/checkmark.png) | ![复选标记](images/checkmark.png)       |
| [策略的 csp](policy-configuration-service-provider.md)                                               | ![叉号](images/crossmark.png) | ![复选标记](images/checkmark.png)       |
| [rootcatrustedcertificates 的 csp](rootcacertificates-csp.md)                | ![叉号](images/crossmark.png) | ![复选标记](images/checkmark.png)       |
| [更新的 csp](update-csp.md)                                               | ![叉号](images/crossmark.png) | ![复选标记](images/checkmark.png)       |
| [vpnv2 的 csp](vpnv2-csp.md)                                                 | ![叉号](images/crossmark.png) | ![复选标记](images/checkmark.png)       |
| [wi-fi csp](wifi-csp.md)                                                  | ![叉号](images/crossmark.png) | ![复选标记](images/checkmark.png)       |
| [windowslicensing 的 csp](windowslicensing-csp.md)                           | ![复选标记](images/checkmark.png) | ![复选标记](images/checkmark.png)       |


## <a name="a-href-idnewcspsanew-csps-added-in-windows-10-version-1511"></a><a href="" id="newcsps"></a>Windows 10 1511年版本中添加新的 Csp

-   [AllJoynManagement 的 CSP](alljoynmanagement-csp.md)
-   [映射的 CSP](maps-csp.md)
-   [报告 CSP](reporting-csp.md)
-   [SurfaceHub 的 CSP](surfacehub-csp.md)
-   [WindowsSecurityAuditing 的 CSP](windowssecurityauditing-csp.md)

## <a name="a-href-idsurfacehubcspsupportacsps-supported-in-microsoft-surface-hub"></a><a href="" id="surfacehubcspsupport"></a>Csp 支持 Microsoft Surface 集线器

-   [应用 CSP](application-csp.md)
-   [CertificateStore 的 CSP](certificatestore-csp.md)
-   [ClientCertificateInstall 的 CSP](clientcertificateinstall-csp.md)
-   [Defender CSP](defender-csp.md)
-   [DevDetail 的 CSP](devdetail-csp.md)
-   [DeviceManageability 的 CSP](devicemanageability-csp.md)
-   [DeviceStatus 的 CSP](devicestatus-csp.md)
-   [DevInfo 的 CSP](devinfo-csp.md)
-   [DiagnosticLog 的 CSP](diagnosticlog-csp.md)
-   [DMAcc 的 CSP](dmacc-csp.md)
-   [DMClient 的 CSP](dmclient-csp.md)
-   [EnterpriseModernAppManagement 的 CSP](enterprisemodernappmanagement-csp.md)
-   [HealthAttestation 的 CSP](healthattestation-csp.md)
-   [NodeCache 的 CSP](nodecache-csp.md)
-   [PassportForWork 的 CSP](passportforwork-csp.md)
-   [CSP 的策略](policy-configuration-service-provider.md)
-   [重新启动 CSP](reboot-csp.md)
-   [RemoteWipe 的 CSP](remotewipe-csp.md)
-   [报告 CSP](reporting-csp.md)
-   [RootCATrustedCertificates 的 CSP](rootcacertificates-csp.md)
-   [SurfaceHub 的 CSP](surfacehub-csp.md)
-   [WindowsAdvancedThreatProtection 的 CSP](windowsadvancedthreatprotection-csp.md)




