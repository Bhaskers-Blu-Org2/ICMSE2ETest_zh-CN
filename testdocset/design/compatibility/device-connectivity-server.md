---
title: Device.Connectivity.Server
Description: "要求。"
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: f12460d25dba7b316e6327d425d1f8246df472e5
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.Connectivity.Server

 - [Device.Connectivity.Server](#device.connectivity.server)
-->

<a name="device.connectivity.server"></a>
##Device.Connectivity.Server

### <a name="deviceconnectivityserverserveroutofbandmanageability"></a>Device.Connectivity.Server.ServerOutOfBandManageability

*服务器的底板管理控制器 (BMC) 设备必须支持带外管理功能。*

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

BMC 设备必须支持服务器硬件的带外管理功能，使用 IPMI 2.0 通过 LAN 和/或串行接口，以及带内通过 KCS 系统通道通过 IPMI 驱动程序。

它不是必要 BMC 实现完整的 IPMI 2.0 规范，功能的子集，则需要进行带外管理。 BMC 必须支持下列功能︰

1.  系统的启动源是通过 BMC 配置的。

    1.  BMC 必须支持在服务器系统上执行以下操作。 使用设置系统启动选项命令来实现此功能。

        1.  可以将服务器配置为从 PXE 服务器启动下一步会重置的时间

        2.  可以将服务器配置为从硬盘启动下一步会重置的时间

        3.  可以将服务器配置为始终从 PXE 服务器启动

        4.  可以将服务器配置为始终从硬磁盘引导

2.  系统的 BMC 固件和 BIOS 版本信息公开通过 BMC。

    1.  BMC 必须公开以下组件的版本信息︰

        1.  BIOS （通过获得系统信息参数命令）。

        2.  （通过获取设备标识命令） 的 BMC 管理固件。

3.  OOB 管理 LAN 配置可以通过 BMC 更新。

    1.  这一要求是只适用于公开通过 IPMI/局域网通道 BMC 的系统。 通过带内通道通过 IPMI 驱动程序执行管理操作。 BMC 必须公开自己通过获得 LAN 配置参数命令的 LAN 配置有关的下列信息︰

        1.  指示符，指示 BMC 配置了静态 IP 地址还是一个是由 DHCP 分配

        2.  IP 地址

        3.  子网掩码

        4.  默认网关

    2.  BMC 必须支持通过设置 LAN 配置参数命令执行以下操作︰

        1.  可以用一个静态 IP 地址、 子网掩码和默认网关 IP 地址配置 BMC

        2.  可以将 BMC 配置为从 DHCP 服务器获取其 IP 地址

4.  可以通过 BMC 管理系统的电源状态。

    1.  BMC 必须公开以下服务器系统信息︰

        1.  （通过获取机箱状态命令） 的服务器的当前电源状态

    2.  BMC 必须支持在服务器系统中通过机箱控制命令执行以下操作︰

        1.  可以关闭服务器的电源

        2.  可以打开服务器电源

        3.  可以重置服务器的电源

5.  BMC 防止不受信任的访问到服务器系统。

    1.  使用 IPMI 的身份验证机制带来大量与不安全配置 BMC 中可利用的漏洞。 为了缓解其中一些漏洞，是经过认证的 Bmc 上存在以下配置︰

        1.  BMC 局域网通道使用 RAKP 上不允许远程访问的任何身份验证算法。

        2.  BMC 不能有默认配置匿名用户帐户。 如果此帐户存在，它必须被禁用。

6.  通过 BMC 公开系统的基本库存。

    1.  BMC 必须公开以下服务器系统信息︰

        1.  （读取 FRU 数据命令） 的服务器硬件的制造商联系

        2.  模型的服务器硬件 （读取 FRU 数据命令）

        3.  服务器 SMBIOS GUID （获取系统 GUID 命令）

            1.  路上的 GUID 的预期的格式符合 SMBIOS 2.8 规范 (DSP0134) 中描述的格式。 GUID 00112233-4455-6677-8899-AABBCCDDEEFF 为 33 22 11 00 55 44 77 66 88 99 的传输，即获取系统 GUID 命令的 AA BB 抄送 DD EE FF。

        4.  服务器 （读取 FRU 数据命令） 的资产标签

        5.  服务器 （读取 FRU 数据命令） 的序列号

        6.  （获取 SEL Time 命令） 的服务器的系统事件日志时间

        7.  系统事件日志容量信息 （获取 SEL 信息命令）

7.  BMC 允许远程凭据管理。

    1.  BMC 必须支持通过设定用户密码命令被更改的管理员密码。 执行此操作，使用 IPMI 驱动程序通过带内通道。

8.  可以通过 BMC 管理系统事件日志 (SEL)

    1.  SEL 条目可读 （获取 sel 日志项命令）

    2.  可以清除 SEL （清除 SEL 命令）

下面是 IPMI 命令来管理 BMC 设备正在使用的列表︰

-   打开会话

-   RAKP 消息

-   设置会话权限级别

-   获取会话信息

-   关闭会话

-   获取设备 Id

-   获取系统的 GUID

-   获取系统信息参数

-   读取 FRU 数据

-   机箱控制

-   获取机箱状态

-   获取通道信息

-   获得 LAN 配置参数

-   设置 LAN 配置参数

-   热重置

-   获取 SEL 条目

-   获取 SEL 信息

-   SEL 准备金

-   清除 SEL

-   获取 SEL 时间

-   获取系统启动选项

-   设置系统启动选项

-   获取用户名称

-   设置用户密码

**强制执行**

这是一项"如果实现"可选设备的要求。 这是自称带外管理使用领域事实上的标准 IPMI 的服务器的必备设备要求。 这一要求实际上成为 Windows 服务器 2016年的版本。

