---
title: "使用 OMA DM 可在 Windows 设备管理服务器要求"
description: "使用 OMA DM 可在 Windows 设备管理服务器要求"
MS-HAID:
- p\_phDeviceMgmt.server\_requirements\_for\_oma\_dm
- p\_phDeviceMgmt.server\_requirements\_windows\_mdm
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 5b90b631-62a6-4949-b53a-01275fd304b2
ms.openlocfilehash: ef4e13f94de994a4f19352df6ff84598f4a034ff
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="server-requirements-for-using-oma-dm-to-manage-windows-devices"></a>使用 OMA DM 可在 Windows 设备管理服务器要求

下面的列表显示了使用 OMA DM 来管理 Windows 设备的常规服务器要求︰

-   OMA DM 服务器必须支持的 OMA DM v1.1.2 或更高版本的协议。

-   安全套接字层 (SSL) 必须在 OMA DM 服务器上，并且它必须提供服务器基于证书的身份验证、 数据完整性检查和数据加密。 如果证书不颁发商业证书颁发机构的根证书就是预装在设备中，您必须配置企业根证书在该设备的根存储区中。

-   若要在应用程序级别的客户端的身份验证，您必须使用基本或 MD5 客户端身份验证。

-   必须在每个 DM 会话更新服务器 MD5 nonce。 DM 客户端新的服务器目前下一个会话向服务器发送状态元素上每个 DM 会话中。

-   服务计算哈希值时，应使用的 MD5 二进制 nonce 发送到 XML 编码的 B64 格式，但八进制形式的二进制数据。

    有关更多基本的信息或 MD5 客户端身份验证、 MD5 哈希值和 MD5 现时请参阅 OMA 设备管理安全规范 (OMA TS DM\_安全 V1\_2\_1 20080617 A)，可从[OMA 网站](http://go.microsoft.com/fwlink/p/?LinkId=526900)。

-   该服务器必须支持 HTTPS。

 





