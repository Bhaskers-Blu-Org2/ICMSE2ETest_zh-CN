---
title: "更新的 CSP"
description: "更新的 CSP"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: F1627B57-0749-47F6-A066-677FDD3D7359
ms.openlocfilehash: 7f8c05848846e3f2f9f2b69b86593b5cb48ba66a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="update-csp"></a>更新的 CSP


更新配置服务提供程序使 IT 管理员可以管理和控制的推出新的更新。

下面的关系图以树格式显示更新配置服务提供程序。

![更新的 csp 图](images/provisioning-csp-update.png)

<a href="" id="update"></a>**更新**  
根节点。

受支持的操作是获得。

<a href="" id="approvedupdates"></a>**ApprovedUpdates**  
更新审批和代表最终用户的最终用户许可协议接受的节点。

> **请注意**当设置了 RequireUpdateApproval 策略时，MDM 使用 ApprovedUpdates 列表传递批准的 Guid。 这些 Guid 应该是 InstallableUpdates 列表的一个子集。

MDM 必须首先出示到 EULA IT 并让他们接受它，才能批准更新。 如果不这样做是法律或合同义务的违反。 Eula 可获取的更新元数据，并有他们自己的协议 id。 很可能的多个更新程序共享同一个最终用户许可协议。 它只是用来审核一次每个最终用户许可协议 ID，不是每个更新的 EULA。

更新审批列表使 IT 部门能够批准单独更新和更新分类。 通过更新分类的自动审批使 IT 部门能够自动批准 （亦即，在设备上的病毒和间谍软件定义更新） 特征码更新和安全更新 （即，特定于产品的更新与安全相关的漏洞）。 更新的审批列表不支持卸载更新通过吊销批准已安装的更新。 更新已批准基于 UpdateID，和 UpdateID 只需一次审批。 更新 UpdateID 和 RevisionNumber 是 UpdateIdentity 类型的一部分。 UpdateID 可关联到几个 UpdateIdentity Guid，由于 RevisionNumber 设置的更改。 MDM 服务必须同步基于最新的 RevisionNumber，以获得最新的元数据更新 UpdateID 的 UpdateIdentity。 但是，更新批准基于 UpdateID。

> **请注意** Windows 10 版本，客户端可能需要添加更多的更新后重新启动计算机。

 

支持的操作包括获取和添加。

<a href="" id="approvedupdates-approved-update-guid"></a>**ApprovedUpdates / ***_批准更新 Guid_**  
指定该更新的 GUID。

要自动批准的更新的类，您可以指定[更新类别](http://go.microsoft.com/fwlink/p/?LinkId=526723)Guid。 我们强烈建议始终指定 DefinitionsUpdates 分类 (E0789628-CE08-4437-BE74-2495B842F43B)，其用于反恶意软件签名。 那里定期的发布 （每天多次）。 一些公司可能还要自动批准的安全更新，让他们迅速部署。

支持的操作包括获取和添加。

示例 syncml:

```
<LocURI>./Vendor/MSFT/Update/ApprovedUpdates/%7ba317dafe-baf4-453f-b232-a7075efae36e%7d</LocURI>
```

<a href="" id="approvedupdates-approved-update-guid-approvedtime"></a>* *ApprovedUpdates /*批准更新 Guid*/ApprovedTime**  
指定的时间获取批准更新。

支持的操作包括获取和添加。

<a href="" id="failedupdates"></a>**FailedUpdates**  
指定的已批准的更新程序无法安装到设备上。

受支持的操作是获得。

<a href="" id="failedupdates-failed-update-guid"></a>**FailedUpdates / ***_失败更新 Guid_**  
更新表示无法下载或安装更新 UpdateIdentity GUID 标识符字段。

受支持的操作是获得。

<a href="" id="failedupdates-failed-update-guid-hresult"></a>* *FailedUpdates /*失败更新 Guid*/HResult**  
更新失败，错误代码。

受支持的操作是获得。

<a href="" id="failedupdates-failed-update-guid-status"></a>* *FailedUpdates /*失败更新 Guid*/Status**  
指定失败的更新状态 （例如，下载，安装）。

受支持的操作是获得。

<a href="" id="installedupdates"></a>**InstalledUpdates**  
在设备安装这些更新。

受支持的操作是获得。

<a href="" id="installedupdates-installed-update-guid"></a>**InstalledUpdates / ***_安装更新的 Guid_**  
表示设备上安装的更新的 UpdateIDs。

受支持的操作是获得。

<a href="" id="installableupdates"></a>**InstallableUpdates**  
所适用的并且尚未安装在设备上的更新。 这包括未获得批准的更新。

受支持的操作是获得。

<a href="" id="installableupdates-installable-update-guid"></a>**InstallableUpdates / ***_的 Guid 可安装的更新_**  
表示适用和设备上未安装的更新的更新标识符。

受支持的操作是获得。

<a href="" id="installableupdates-installable-update-guid-type"></a>* *InstallableUpdates /*的 Guid 可安装更新*/Type**  
UpdateClassification 的更新值。 有效值包括︰

-   0-无
-   1-安全性
-   2 = 临界

受支持的操作是获得。

<a href="" id="installableupdates-installable-update-guid-revisionnumber"></a>* *InstallableUpdates /*的 Guid 可安装更新*/RevisionNumber**  
必须传入的服务器到服务器的同步更新获取元数据的更新修订号。

受支持的操作是获得。

<a href="" id="pendingrebootupdates"></a>**PendingRebootUpdates**  
需要重新启动才能完成更新会话更新。

受支持的操作是获得。

<a href="" id="pendingrebootupdates-pending-reboot-update-guid"></a>**PendingRebootUpdates / ***_挂起的重新启动更新 Guid_**  
更新挂起的重新启动状态的标识符。

受支持的操作是获得。

<a href="" id="pendingrebootupdates-pending-reboot-update-guid-installedtime"></a>* *PendingRebootUpdates /*挂起的重新启动更新 Guid*/InstalledTime**  
安装了此更新的时间。

受支持的操作是获得。

<a href="" id="lastsuccessfulscantime"></a>**LastSuccessfulScanTime**  
上次成功的扫描时间。

受支持的操作是获得。

<a href="" id="deferupgrade"></a>**DeferUpgrade**  
推迟到下一个期间的升级。

受支持的操作是获得。

## <a name="related-topics"></a>相关的主题


[配置服务提供程序的引用](configuration-service-provider-reference.md)

 

 






