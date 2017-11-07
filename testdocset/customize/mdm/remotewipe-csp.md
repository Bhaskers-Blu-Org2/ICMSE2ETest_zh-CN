---
title: "RemoteWipe 的 CSP"
description: "RemoteWipe 的 CSP"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 6e89bd37-7680-4940-8a67-11ed062ffb70
ms.openlocfilehash: dd01f00604b70b54455e6e2b05809cdd9b595d38
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="remotewipe-csp"></a>RemoteWipe 的 CSP


移动运营商 DM 服务器或企业管理服务器可以使用 RemoteWipe 配置服务提供程序来远程擦除设备。 RemoteWipe 配置服务提供程序可以使内存和难以恢复如果远程擦除设备后被丢失或被盗的硬盘中存储的数据。

下图显示了 RemoteWipe 配置服务提供程序管理对象以树格式由 OMA DM 和 OMA 客户端资源调配使用。 企业 IT 专业人员可以通过使用 Exchange Server 更新这些设置。

![remotewipe csp （dm，cp）](images/provisioning-csp-remotewipe-dmandcp.png)

<a href="" id="dowipe"></a>**doWipe**  
指定应执行远程擦除的设备。 返回状态代码表示设备是否接受 Exec 命令。

当用于 OMA 客户端资源调配，伪"1"的值应包括此元素。

受支持的操作被执行。

<a href="" id="dowipepersistprovisioneddata"></a>**doWipePersistProvisionedData**  
指定设置数据应备份到一个永久的位置，则应执行远程擦除的设备。

受支持的操作被执行。

当用于 OMA 客户端资源调配，伪"1"的值应包括此元素。

将还原已备份的信息并将其应用于该设备时它会继续。 返回状态代码显示设备是否接受 Exec 命令。

## <a name="the-remote-wipe-process"></a>远程擦除过程


远程擦除命令发送到设备作为 XML 配置文件。 由于 OMA DM 和 WAP，将使用 RemoteWipe 配置服务提供程序，客户端和服务器之间传递的 XML 配置文件的身份验证处理资源调配。

在 Windows 10 手机，远程擦除命令来实现设备上使用**ResetPhone**函数。 在桌面上，远程擦除触发**删除所有**选项**重置此 PC**功能。

> **请注意** 在桌面上，远程擦除有效地执行出厂重置和擦除完成后，电脑将不会保留该命令有关的任何信息。 来自设备的实际状态或该命令的结果的任何响应可能是不一致而且不可靠，因为 MDM 信息已被删除。

 

## <a name="related-topics"></a>相关的主题


[配置服务提供程序的引用](configuration-service-provider-reference.md)

 

 






