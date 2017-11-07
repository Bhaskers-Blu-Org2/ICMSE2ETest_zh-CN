---
title: Device.Network.WLAN
Description: "要求。"
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 7859ae0ed6526bba95d7a832518dd1aae9943a4a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="devicenetworkwlan"></a>Device.Network.WLAN

 - [Device.Network.WLAN](#device.network.wlan)
 - [Device.Network.WLAN.SupportConnectionToAP](#device.network.wlan.supportconnectiontoap)
 - [Device.Network.WLAN.SupportWakeFromLowPower](#device.network.wlan.supportwakefromlowpower)
 - [Device.Network.WLAN.SupportMACAddressRandomization](#device.network.wlan.supportmacaddressrandomization)
 - [Device.Network.WLAN.SupportHotspot2Dot0](#device.network.wlan.supporthotspot2dot0)
 - [Device.Network.WLAN.SupportDot11W](#device.network.wlan.supportdot11w )
 - [Device.Network.WLAN.SupportFIPS](#device.network.wlan.supportfips)
 - [Device.Network.WLAN.SupportWiFiDirect](#device.network.wlan.supportwifidirect)
 - [Device.Network.WLAN.SupportWiFiDirectServices](#device.network.wlan.supportwifidirectservices )
 - [Device.Network.WLAN.SupportWirelessDocking](#device.network.wlan.supportwirelessdocking)
 - [Device.Network.WLAN.SupportHostedNetwork](#device.network.wlan.supporthostednetwork)

<a name="device.network.wlan"></a>
## <a name="devicenetworkwlan"></a>Device.Network.WLAN

*10 WLAN Windows 驱动程序可以实现以下驱动程序模型之一︰*

 - WDI 驱动程序模型引入 Windows 10 （支持 Windows 10 的新功能）

*OR*

 - 本机 Wi-fi 驱动程序模型 （不支持 Windows 10 的新功能）

<a name="device.network.wlan.supportconnectiontoap"></a>
## <a name="devicenetworkwlansupportconnectiontoap"></a>Device.Network.WLAN.SupportConnectionToAP

### <a name="devicenetworkwlansupportconnectiontoapconnectiontoap-mandatory"></a>Device.Network.WLAN.SupportConnectionToAP.ConnectionToAP （必需）

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
</td></tr></table>

**说明**

设备必须报告支持带内每个各自的类别信息。 此外，设备必须符合以下要求。

**最小化 CPU 利用率**

Wi-fi 设备应符合以下要求的最小化 CPU 利用率。

-   在 EXTSTA 模式下并处于 D0 状态，WLAN 设备必须不中断操作系统 1 个以上时，每个数据包 （非 D0 合并只包。 如果 WLAN 设备支持 D0 数据包合并，WLAN 设备应符合 D0 数据包合并规范为 D0 合并的数据包）。 请注意是否 WLAN 设备正在使用 SDIO 总线接口，中断生成的每个数据包的 SDIO 主控制器免除此要求。  非数据数据包相关的中断，如果需要不能超过每秒 3 中断平均在 2 分钟内测量时。  此外，作为一种最佳做法，在活动状态下 （当数据流量），非数据数据包相关的中断应发出的有效的数据包相关中断 1 毫秒内。

-   处于 D0 状态时，所有 （如果有的话） 微型端口特定的定期维护计时器，必须指定一个可用"timer 合并"API，使用最小值 2 的第二个句点和 1 秒的容差。  连接中的任何更改时，将长时间运行的连接状态测试这一要求。  在 D3 状态必须取消所有此类计时器。  请注意，此要求不适用于如 IEEE 802.11 规范中定义的计时器关联的计时器，漫游计时器等如连接计时器。  

-   单个的 DPC （延迟过程调用） 持续时间不能超过 2 毫秒。 累计的 DPC 持续时间应在任何 10 毫秒窗口之上的小于 4 毫秒。

在低功耗状态，如果设备不支持，无线唤醒 WLAN 设备必须中断 CPU。 如果该设备是能够无线唤醒，WLAN 设备必须中断由 NDIS 无线 LAN 上的唤醒触发器上除 CPU。 必须取消所有不相关的唤醒触发器的中断。

**支持多个设备实例**

插可以支持某个设备的多个实例。 设备的多个实例可以存在，并且在同一个实例的同一系统中起作用。 对于网络通信设备，必须足以允许通信设备会自动添加到系统的多个网络的插 Id 和资源支持。 这一要求意味着必须设置和读取通过提供设备所在的总线标准接口设备的所有资源。 对于 PCI 设备，此接口是 PCI 配置空间。 此外，必须在注册表中存储设备参数设置。

**符合以下规格︰ NDIS 6.50，WDF/KMDF**

只有网络驱动程序接口规范 (NDIS) 6.50 或 Windows 驱动程序的基础 (WDF) 调用，则必须进行网络设备驱动程序。 不允许有任何的内核模式组件的调用。

**关联的计时要求**

WPA2 PSK 在网络上，WLAN 设备必须完成内**除了**关联。  它指当操作系统发出一个 OID 的事件之间的时间"OID\_WDI\_任务\_连接"和微型端口发送"NDIS\_状态\_WDI\_指示\_关联\_结果"对操作系统的指示。 

**漫游计时要求**

设备*不*支持快速漫游 (这意味着 STA 不支持发送/接收操作框架和 utilitizes 802.11r 快速 BSS 过渡。 此外，AP 端 802.11 k 邻居报告和 802.11r AP 中未启用）︰ 漫游操作必须在**100 毫秒**内完成。 这一次测量启动时操作系统发出 OID\_WDI\_任务\_连接或 OID\_WDI\_任务\_漫游命令并结束时 NDIS\_状态\_WDI\_指示\_关联\_OS，AssociationStatus 设置为 WDI 通过收到结果通知\_ASSOC\_状态\_成功。

设备*是否*支持快速漫游 (这意味着 STA 支持发送/接收操作框架，并利用 802.11r 快速 BSS 过渡。 此外，在接入点启用 AP 端 802.11 k 邻居报告和 802.11r）︰ 漫游操作必须在**50 毫秒**内完成。 这一次测量启动时操作系统发出 OID\_WDI\_任务\_连接或 OID\_WDI\_任务\_漫游命令并结束时 NDIS\_状态\_WDI\_指示\_关联\_OS，AssociationStatus 设置为 WDI 通过收到结果通知\_ASSOC\_状态\_成功。

**设备初始化计时要求**

WLAN 设备必须满足以下要求在启动时，继续从休眠、 和设备启用/禁用操作。

设备必须在 1 秒钟内完成 OpenAdapterHandler 例程。 当 NDIS 调用 OpenAdapterHandler 函数作为系统的即插即用操作和 OpenAdapterCompleteHandler 的一部分之间测量时间 (NDIS\_状态\_成功) 返回。 在 OpenAdapterHandler 中，驱动程序必须已完成其所有设备初始化。

**无线电的状态更改计时要求**

WLAN 设备必须能够在 2 秒内无线电设备状态更改。 此持续时间将长之间请求被发送通过 OID\_WDI\_任务\_设置\_无线电\_状态和微型端口时指示 NDIS\_状态\_WDI\_指示\_无线电\_状态后。

**扫描首选的通道设置**

首选通道集︰ 扫描可用的网络或漫游来查找候选访问点时的微型端口驱动程序时支持并允许按规章域，必须喜欢以下渠道︰

-   2.4 g h z 通道︰ 1 到 14

-   5 GHz U NII 低声道︰ 36、 40、 44、 48

-   5 GHz U NII 中间通道︰ 52、 56、 60,64

-   5 GHz U NII 全球渠道︰ 100、 104、 108、 112、 116、 120、 124、 128、 132、 136、 140

-   5 GHz U NII 上部通道︰ 149、 153、 157、 161,165

驱动程序必须报告这些支持和任何其他渠道它支持通过提供 WDI ChannelList\_带\_信息的 OID\_WDI\_获得\_适配器\_功能。

**扫描操作要求**

WLAN 设备必须开始扫描时收到"OID\_WDI\_任务\_"从 OS 和回用相对值答复"扫描 NDIS\_状态\_WDI\_指示\_扫描\_完成"操作系统一旦完成扫描。 如果扫描活动，预计微型端口发送到网络通道，以满足扫描目标探测活动的通配符。 在被动扫描，微型端口不需要发送到网络渠道的任何探测器。

此优先顺序，应按扫描︰

1.  NLO 提示通道

2.  首选的通道

3.  任何剩余的频道

将从时间戳测量下面列出的计时，当该设备收到 OID"OID\_WDI\_任务\_扫描"从 OS 时各自的指示提供给微型端口通过操作系统的时间戳。

-   如果可用网络列表中卸载提示，该设备应利用网络列表中卸载提示优化扫描行为，并返回"NDIS\_状态\_WDI\_指示\_NLO\_发现"指示以下计时中找到匹配的配置文件时︰

    <!-- -->

    -   扫描的网络活动扫描允许的位置-20 毫秒/通道

    -   扫描的网络只能被动扫描允许的位置-120ms年/通道

    <!-- -->

-   如果使用网络列表中卸载提示找到任何匹配项，WLAN 设备下一步应扫描上面列表中的首选的通道。  为扫描首选的频道列表中的通道，WLAN 设备应该不会超过 3.5 秒 （时间包括主动和被动的频道扫描）。 应从 OS 上的下一步的 BSS 列表查询返回周围 BSS 条目的新创建的列表。

-   如果未在上面 2 的情况下找到匹配项，WLAN 设备下一步应扫描任何剩余的频道。 WLAN 设备应该不会超过 4 秒的整个扫描操作。 

**在从休眠/屏幕关闭时扫描行为**

当从休眠/屏幕关闭恢复，预计 WLAN 设备重新连接到它进入睡眠状态，如果可用之前已连接到同一个接入点。 WLAN 设备必须满足以下计时检测其存在︰

-   重新连接到一个通道处于活动状态扫描允许-50 毫秒

-   重新连接到一个通道是只能被动扫描允许-120ms

如果找不到上次连接的网络，WLAN 设备必须扫描网络下面列出的优先级顺序。

-   NLO 提示通道

-   首选的通道

-   任何剩余的频道

前面已定义，在常规扫描部分 WLAN 设备必须遵循的时间约束。  设备报告为处于 D0 状态时，将时间戳从开始测量的排练时间 (OID\_WDI\_设置\_电源\_状态完成) 时各自的指示提供给微型端口通过操作系统的时间戳。

**扫描非广播网络**

WLAN 设备必须能够扫描和报告存在的非广播 （即隐藏） 网络。

**支持协调扫描 （如果实现） （仅 WDI 驱动程序）**

VOIP 运营需要能够确定网络资源的优先级，同时仍然允许移动性维护数据质量。 这种无线堆栈中，我们引入了媒体流式处理模式的概念。 此功能专门调出扫描含义的键 / 在媒体流式处理模式时的行为。 请到 WDI 规范的详细信息，参阅。

**支持原始操作框架 （如果实现） （仅 WDI 驱动程序）**

原始操作框架所需的传输 ANQP 查询/响应帧、 802.11 k 邻居报告/请求帧和 802.11v BSS 过渡管理报告/请求帧。 该设备必须报告它在 WDI 支持原始操作框架\_获得\_适配器\_功能。 请到 WDI 规范实现的详细信息，参阅。 802.11 k 邻居报告和 802.11vBSS 过渡管理框架将用于改进操作系统中的漫游性能。 通过利用 802.11 k 邻居报告和 802.11v BSS 过渡管理框架、 OS 有进一步的了解其周围的环境，并允许漫游性能改进，因而导致较少的难题，为最终用户在语音/视频通话时。

**802.11r 支持快速 BSS 转换 （如果实现） （仅 WDI 驱动程序）**

802.11r 快速 BSS 转换允许密钥交换速度，从而提高了漫游性能。 驱动程序必须支持快速 BSS 关联的新的关联类型和关联/密钥交换过程中对操作系统发出适当指示。 请从详细信息参阅 WDI 规范。

**低滞后时间**

WLAN 设备应该能够支持低延迟的应用程序方案，可如 Wi-Fi 显示/Lync/Skype。 为此，WLAN 设备必须支持以下︰

-   应在所有端口包括虚拟的端口 – ExtSTA，支持 WMM Wi-Fi 直接角色端口 （组所有者） 和 Wi-Fi 直接角色端口 （客户端）。

-   WMM 应支持 Wi-Fi 直接角色端口 （组所有者） 上，Wi-Fi 直接角色端口 （客户端） 即使通过 ExSTA 端口连接的 AP 不支持 WMM。

-   NIC 应能够同时支持跨两个端口 (ExtSTA & 一个 Wi-fi 直接角色端口) 的优先顺序。

-   设备应该能够确定优先级基于 802.11e 通信访问类别 (AC) 标记。

-   当网卡进行虚拟化具有并发单通道中时，它应该能够跨不同的虚拟端口基于 WMM 和媒体流指示优先传输通信。

-   当网卡进行虚拟化具有并发跨多个通道时，它应该能够跨不同的虚拟端口基于 WMM 和媒体流指示优先传输通信，接收通信跨并发渠道提供服务。

WMM 优先顺序时用交流\_VI 或 AC\_VO （语音/视频），WLAN 设备必须满足以下延迟和数据包丢失。

<html>
    <table>
        <thead>
            <tr class="header">
                <th></th>
                <th>ExSTA</th>
                <th>Wi-Fi 直接角色端口</th>
                <th>最大值。 一种方法反应时间为 AC_VI/AC_VO 通信 UDP</th>
                <th>AC_VI/AC_VO 通信的数据包丢失</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <td>只有 ExSTA</td>
                <td>AC_VI/AC_VO</td>
                <td>NA</td>
                <td>30ms</td>
                <td>0.5%，不是更该 3 consequetive 数据包</td>
            </tr>
            <tr class="even">
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
            <tr class="odd">
                <td>ExSTA + Wi-fi 直接在单通道并发</td>
                <td>AC_VI/AC_VO</td>
                <td></td>
                <td>30ms</td>
                <td>0.5%，不是更该 3 consequetive 数据包</td>
            </tr>
            <tr class="even">
                <td></td>
                <td></td>
                <td>AC_VI/AC_VO</td>
                <td>30ms</td>
                <td>0.5%，不是更该 3 consequetive 数据包</td>
            </tr>
            <tr class="odd">
                <td></td>
                <td>AC_VI/AC_VO</td>
                <td>AC_VI/AC_VO</td>
                <td>30ms</td>
                <td>0.5%，不是更该 3 consequetive 数据包</td>
            </tr>
            <tr class="even">
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
            <tr class="odd">
                <td>ExSTA + Wi-fi 直接在多通道并发</td>
                <td>AC_VI/AC_VO</td>
                <td></td>
                <td>40 毫秒</td>
                <td>0.5%，不是更该 3 consequetive 数据包</td>
            </tr>
            <tr class="even">
                <td></td>
                <td></td>
                <td>AC_VI/AC_VO</td>
                <td>40 毫秒</td>
                <td>0.5%，不是更该 3 consequetive 数据包</td>
            </tr>
            <tr class="odd">
                <td></td>
                <td>AC_VI/AC_VO</td>
                <td>AC_VI/AC_VO</td>
                <td>50 毫秒</td>
                <td>0.5%，不是更该 3 consequetive 数据包</td>
            </tr>
        </tbody>
    </table>
</html>

**最小的吞吐量性能**

**与并发操作的吞吐量︰**802.11 设备不能有超过 20%的聚合吞吐量下降时的数据流划分 3 个端口 （带分隔符和不多 Channel/波段操作的情况下） 即 – ExtSTA、 Wi-Fi 直接角色端口 （转） 和 Wi-Fi 直接角色端口 （客户端） 与聚合吞吐量相比，当只有一个 Wi-fi 端口连接。

**吞吐量︰**

这吞吐量的需求分别是适用于所有类型的端口 （ExtSTA、 Wi-Fi 直接角色端口 （转） 和 Wi-Fi 直接角色端口 （客户端））。

设备必须能够通过 TCP 连接特定的 Phy 类型、 流和通道宽度的数字组合支持下的吞吐量数字。 吞吐量被指在应用程序层使用内置于 Windows 硬件认证工具包 NTTTCP 性能测量工具。

-   如果 WLAN 设备支持 802.11ac Phy 类型 （请注意，802.11ac Phy 类型的支持是可选的 WLAN 设备。 802.11ac 还将 802.11 n 测试设备操作)

    -   802.11ac 将上仅 5 Ghz 频段测试组合。

    -   同时发送和接收端吞吐量将进行测试。 设备应满足相同的吞吐量号 （如下所示） 在传输和接收端的特定组合。

将测试通过网卡的最大支持空间流。 例如，如果 NIC 支持 3 空间流，将测试组合与空间流 3。

<html>
    <table>
        <thead>
            <tr class="header">
                <th><em>信道宽度</em></th>
                <th colspan="2"><em>20 Mhz</em></th>
                <th colspan="2"><em>40 Mhz</em></th>
                <th colspan="2"><em>80 Mhz</em></th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <th># 空间流 </th>
                <td>最大 Phy 率 （100%)</td>
                <td>Windows 认证所需的吞吐量</td>
                <td>最大 Phy 率 （100%)</td>
                <td>Windows 认证所需的吞吐量</td>
                <td>最大 Phy 率 （100%)</td>
                <td>Windows 认证所需的吞吐量</td>
            </tr>
            <tr class="even">
                <th>1 流</th>
                <td>86</td>
                <td>18</td>
                <td>200</td>
                <td>42</td>
                <td>433</td>
                <td>90</td>
            </tr>
            <tr class="odd">
                <th>2 流</th>
                <td>173</td>
                <td>38</td>
                <td>400</td>
                <td>88</td>
                <td>866</td>
                <td>191</td>
            </tr>
            <tr class="even">
                <th>3 流或更高版本\*</th>
                <td>258</td>
                <td>47</td>
                <td>600</td>
                <td>110</td>
                <td>1300</td>
                <td>237</td>
            </tr>
        </tbody>
    </table>
    <p><em>\*所有的速度是以 mbps 为单位。</em></p>
    <p><em>\*不需要的 SDIO 和 USB 2.0 总线类型设备的组合。2 个以上流支持这些设备必须能够获得 2 数据流中列出的值。请注意，未排除 USB 3.0 设备。</em></p>
    <ul>
        <li>
            <p>802.11 n WLAN 设备</p>
            <ul>
                <li><p>802.11 n 组合将 2.4 g h z 和 5ghz 区段通过测试，如果这两个区段在设备上受支持。</p></li>
                <li><p>同时发送和接收端吞吐量将进行测试。 设备应满足相同的吞吐量号 （如下所示） 在传输和接收端的特定组合。</p></li>
                <li><p>将测试最大的支持空间流通过 NIC。 例如，如果 NIC 支持 3 空间流，将测试组合与空间流 3。</p></li>
            </ul>
        </li>
    </ul>
    <table>
        <thead>
            <tr class="header">
                <th>信道宽度</th>
                <th colspan="2">20 Mhz</th>
                <th colspan="2">40 Mhz</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <th># 空间流</th>
                <td>最大 Phy 率 （100%)</td>
                <td>Windows 认证所需的吞吐量</td>
                <td>最大 Phy 率 （100%)</td>
                <td>Windows 认证所需的吞吐量</td>
            </tr>
            <tr class="even">
                <th>1 流</th>
                <td>72</td>
                <td>15</td>
                <td>150</td>
                <td>31</td>
            </tr>
            <tr class="odd">
                <th>2 流</th>
                <td>144</td>
                <td>32</td>
                <td>300</td>
                <td>66</td>
            </tr>
            <tr class="even">
                <th>3 流或更高版本\*</th>
                <td>216</td>
                <td>40</td>
                <td>450</td>
                <td>82</td>
            </tr>
        </tbody>
    </table>
    <p><em>\*所有的速度是以 mbps 为单位。</em></p>
    <p><em>\*不需要的 SDIO 总线类型设备的组合。SDIO 2 个以上流支持的设备必须能够获得 2 数据流中列出的值。</em></p>
</html>

**Wi-Fi 电源-保存模式**

Wi-fi 驱动程序时需要执行检测和协商的适当 Wi-Fi 电源保存模式 (PSM) 设备和 Wi-Fi 接入点之间并将其报告为 AutoPowerSaveMode 中 WDI\_站\_属性。  如果驱动程序报告它支持 PSM 检测，WLAN 服务将委托 PSM 决策到驱动程序，默认情况下。

如果驱动程序所支持的自动 PSM 功能 Wi-fi 服务将不再设置广播的管理筛选器从微型端口接收信号，并将改为设置一个 OID 在驱动程序中启用自动 PSM。  在自动的 PSM，驱动程序应始终协商 PSM 模式，当它检测到该接入点支持和管理设备和 Wi-Fi 接入点，以确保最佳的连接，同时使用最少的电源之间的 PSM 使用。

**连接丢失**

所有的 WLAN 设备必须检测和内 20 信号间隔指示连接的 AP （无信标） 的损失。

**允许信息元素添加到关联框架 （请求/响应）**

所有 802.11 设备必须允许信息元素添加到关联的帧，请求和响应。 这包括添加当前指定的信息元素，如 Wi-fi 保护设置，以及其他供应商扩展信息元素。

**支持 32 个多路广播地址的筛选**

WLAN 硬件在每个端口上都必须支持至少 32 个多路广播的地址。 STA 和 Wi-Fi-直接端口需要支持分别筛选 32 个多路广播的地址。

**支持单独信标和探测信息元素**

所有 802.11 设备必须分别表明 Wi-Fi 保护设置导致浏览器接收信号帧和探测响应帧中。 如果设备已从特定 BSSID 接收信号帧和探测响应帧，它必须提供两个 IE，其中一个实例是最最近收到来自信标的 WPS IE 和一个实例处于最最近收到来自探测器响应的 WPS IE。

**传输所有边界上的数据包**

在奇数字节、 字、 双字或其他边界缓冲区中开始是否指缓冲区对齐方式。 设备必须能够传输的数据包与任何数据包片段在奇数字节边界上开始。 为了提高性能，必须到双字边界上的相邻缓冲区收到数据包。

**TCP 校验和卸载 （如果实现） （仅 WDI 驱动程序）**

TCP/IP 协议旨在提供可靠的数据传输机制。 这就要求对于 TCP 堆栈来实现不同的保护机制来检测和修复这种错误。 这样一种机制是使用"校验和"为了确保可靠性的概念。 我们在 Windows 中执行校验和计算在 OS 中，请求的数据包的重试次数和管理在主机中的数据包。 WLAN 设备必须报告它支持减轻，并能减轻操作系统规定的方式。 设备必须能够检测出是否卸载导致的性能问题，并能够禁用卸载。 跨站连接和 Wi-Fi 直接使用方案不应处理减轻。

**连接类型**

所有的 WLAN 设备必须能够使用下列的 Wi-Fi 连接类型进行连接。 所有的 WLAN 设备声明只支持这些 WDI 通过\_算法\_对报告在 OID\_WDI\_获得\_适配器\_功能

在基础结构模式所需的支持身份验证和密码︰

| Authnetication  | 密码     |
|-----------------|------------|
| 打开            | 无       |
| 打开            | WEP 的 40 位  |
| 打开            | WEP-104 位 |
| 打开            | WEP        |
| WPA-企业  | TKIP       |
| WPA-企业  | CCMP       |
| WPA-个人    | TKIP       |
| WPA-个人    | CCMP       |
| WPA2-企业 | TKIP       |
| WPA2-企业 | CCMP       |
| WPA2-个人   | TKIP       |
| WPA2-个人   | CCMP       |

\[仅本机 Wi-fi 驱动程序\]（如果实现） 身份验证和加密所需支持点对点 (IBSS) 模式中︰

| Authnetication | 密码     |
|----------------|------------|
| 打开           | 无       |
| 打开           | WEP 的 40 位  |
| 打开           | WEP-104 位 |
| 打开           | WEP        |
| WPA2-个人  | CCMP       |

**支持休眠和恢复**

如果设备支持休眠和恢复时，该设备应不淡出总线作为其初始 （启动时） 固件下载过程或进入休眠状态时。

**支持无线电管理 （无线电开/关）**

设备必须支持从 OS WDI 通过无线电管理请求\_任务\_设置\_无线电\_状态命令。 请到 WDI 规范的详细信息，参阅。

**支持 Wi-Fi 保护设置 (WPS)**

设备必须支持 Wi-Fi 保护设置。 操作系统将发出 WDI\_设置\_P2P\_WPS\_启用命令指示到 LE，WPS 设置时。 请到 WDI 规范的详细信息，参阅。

**支持数据包筛选器 （如果实现）**

数据包筛选器允许 OS，以筛选不同类型的时收到的数据包。 操作系统将使用 WDI\_TLV\_数据包\_筛选器\_参数 TLV 以指示哪种类型的数据包筛选。 请到 WDI 规范的详细信息，参阅。

**获取 WFA 认证 （如果实现）**

强烈建议设备获取以下 WFA 认证︰

-   802.11 n
-   WMM
-   WPA2Protected 管理框架 (PMF)

**实施 802.11 a （如果实现）**

设备必须报告 802.11 a PHY 类型 4 (WDI\_PHY\_类型\_OFDM) 中 WDI\_PHY\_信息结构由 OID\_WDI\_获得\_适配器\_功能。

**实施 802.11 b （必需）**

设备必须报告 802.11 b PHY 类型 2 (WDI\_PHY\_类型\_HRDSS) 在 WDI\_PHY\_信息结构由 OID\_WDI\_获得\_适配器\_功能。

**实施 802.11 g （如果实现）**

设备必须报告 802.11 g PHY 类型 5 (WDI\_PHY\_类型\_ERP) 中 WDI\_PHY\_信息结构由 OID\_WDI\_获得\_适配器\_功能。

**实施 802.11 n （如果实现）**

为获得最佳的 WLAN 性能的建议。

设备必须报告 802.11 n PHY 类型 7 (WDI\_PHY\_类型\_HT) 中 WDI\_PHY\_信息结构由 OID\_WDI\_获得\_适配器\_功能。

**实现 802.11ac （如果实现）**

设备必须报告 802.11ac PHY 类型 8 (WDI\_PHY\_类型\_VHT) 在 WDI\_PHY\_信息结构由 OID\_WDI\_获得\_适配器\_功能。

**支持挂起检测和恢复 （如果实现） （仅 WDI 驱动程序）**

已经知道 Wi-fi 设备固件挂起和/或获取处于停滞状态。 一旦发生这种情况，下边驱动程序会导致 9F 或者崩溃 （蓝屏） 或 Wi-fi 子系统进入一种状态，这就需要重新启动系统才能重新正常工作的设备。 在任一情况下，用户在其连接面对负面体验和中断及其一般的系统使用。 WDI 的一个有机组成部分，为我们设计了一种机制来检测当固件进入这些状态和无缝恢复设备。 这将确保该用户将看到通过确保 Wi-fi 设备堆栈中恢复并继续到网络的连接，无需重新启动系统的最低程度的服务中断。 设备必须报告支持挂起检测和恢复 WDI\_获得\_适配器\_功能。 请到 WDI 规范实现的详细信息，参阅。

需求 — 硬件 / 固件

ACPI 系统固件︰ 系统将提供 PDLR 的 ACPI 方法 at 总线或在设备级别的设备。

系统硬件︰ 系统，可实现 PDLR （完整设备级别重置）。 所有系统都必须都支持 PDLR。

系统︰ 系统将指示支持 PDLR 的支持。

设备︰ 下边驱动程序将能够收集 25 ms，250 Kb 大小的转储

系统︰ 系统必须完成重置在 10 秒钟之内。

<a name="device.network.wlan.supportwakefromlowpower"></a>
## <a name="devicenetworkwlansupportwakefromlowpower"></a>Device.Network.WLAN.SupportWakeFromLowPower

### <a name="devicenetworkwlansupportwakefromlowpowerwakefromlowpower-if-implemented"></a>Device.Network.WLAN.SupportWakeFromLowPower.WakeFromLowPower （如果实现）

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
</td></tr></table>

在 WLAN 上实现唤醒

**说明︰**

实现 WoWLAN （无线 LAN 上的唤醒） 的 WLAN 设备必须支持与 WoWLAN 功能相关的所有功能。 不会进行认证被视为实现如下功能的子集。 WLAN 设备应执行以下操作︰

-   必须指明特定唤醒支持的无线 LAN (响应 WoWLAN) 功能。

-   必须支持至少 22 WoWLAN 位图唤醒模式的 128 字节。

-   必须能够执行 GTK (WPA/WPA2) 和 IGTK 刷新在 Dx 状态 (WPA2)。

-   必须支持在 GTK 和 IGTK 握手错误的唤醒。

-   必须支持唤醒时 802.1 x EAP 请求/标识数据包接收。

-   必须支持唤醒时四次握手请求接收到。

-   必须与当前的 AP 丢失的关联上支持唤醒。

-   当网络匹配 NLO （列表中卸载功能的网络） 提示必须支持唤醒。

-   必须支持唤醒数据包指示。 NIC 应缓存在硬件上导致唤醒数据包，当操作系统准备接收向上传递。

-   必须支持为确保链接本地网络发现的 ARP 和 NS 减轻。 WLAN 设备应该能够对 ARP 和 NS 请求作出响应而不会中断 CPU 时设备处于低功耗 (D3) 状态。 设备必须支持至少一个 ARP 卸载和至少 2 NS 减轻 （与目标 IPv6 地址最多配置 2 每个 NS 卸载）。

卸载功能的网络列表

**说明︰**

WLAN 设备应支持 10 BSSID 卸载配置文件。 标记的 Wi-Fi 配置文件自动连接将被下放到设备操作系统。  设备应使用列表中卸载功能的网络作为一个提示，以优化扫描行为并返回"NDIS\_状态\_WDI\_指示\_NLO\_发现"指示找到匹配的配置文件时。

<a name="device.network.wlan.supportmacaddressrandomization"></a>
## <a name="devicenetworkwlansupportmacaddressrandomization"></a>Device.Network.WLAN.SupportMACAddressRandomization

### <a name="devicenetworkwlansupportmacaddressrandomizationmacaddressrandomization-if-implemented-wdi-drivers-only"></a>Device.Network.WLAN.SupportMACAddressRandomization.MACAddressRandomization （如果实现） **（仅 WDI 驱动程序）**

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
</td></tr></table>

**说明**

Wi-Fi MAC 地址目前用于跟踪用户，因为它们在公共空间，从热点的热点，甚至在百货公司或商场内移动。 随机化的 MAC 地址，通过 Windows 手机用户无法跟踪未经他们的同意。 若要支持此功能，设备必须报告给操作系统它支持 MAC 地址随机化 WDI 通过\_获得\_适配器\_功能。 请到 WDI 规范功能实现的详细信息，参阅。

<a name="device.network.wlan.supporthotspot2dot0"></a>
## <a name="devicenetworkwlansupporthotspot2dot0"></a>Device.Network.WLAN.SupportHotspot2Dot0

### <a name="devicenetworkwlansupporthotspot2dot0hotspot2dot0-if-implemented-wdi-drivers-only"></a>（如果执行） 的 Device.Network.WLAN.SupportHotspot2Dot0.Hotspot2Dot0 **（仅 WDI 驱动程序）**

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
</td></tr></table>

**说明**

设备必须报告它在 WDI 支持 ActionFrameSupport\_TLV\_接口\_功能和 optinally 报告它在 WDI 支持 ConnectToSSIDsBelongingToHESSID\_站\_属性。 请到 WDI 规范实现的详细信息，参阅。

<a name="device.network.wlan.supportdot11w "></a>
## <a name="devicenetworkwlansupportdot11w"></a>Device.Network.WLAN.SupportDot11W 

### <a name="devicenetworkwlansupportdot11wdot11w-if-implemented"></a>Device.Network.WLAN.SupportDot11W.Dot11W （如果实现）

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
</td></tr></table>

**说明**

设备必须报告对 802.11w 的支持 WDI 中受保护的管理框架\_站\_属性。 IEEE 802.11w 是 IEEE 802.11 系列标准，以提高安全性的管理框架的补充。 请到 WDI 规范实现的详细信息，参阅。

<a name="device.network.wlan.supportfips"></a>
## <a name="devicenetworkwlansupportfips"></a>Device.Network.WLAN.SupportFIPS

### <a name="devicenetworkwlansupportfipsfips-if-implemented"></a>Device.Network.WLAN.SupportFIPS.FIPS （如果实现）

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
</td></tr></table>

**说明**

报告支持在 WDI FIPS\_站\_属性。 请到 WDI 规范实现的详细信息，参阅。 FIPS （联邦信息处理标准） 是美国政府内的通信和计算机系统的使用要求。

您的 WLAN 设备必须支持以下的两种方法之一 FIPS 支持︰

1.  基于硬件的解决方案︰ 您可以选择以直接通过您的硬件设备支持 FIPS。 可以做到通过声明 DOT11\_EXTSTA\_属性\_安全模式\_（对于 NWIFI 驱动程序） 的认证并 WDI\_站\_– 主机 FIPS 模式实现特性 （对于 WDI 驱动程序） 驱动程序中。 如果你声明的 FIPS 基于硬件支持您的设备制造商负责确保符合 FIPS 标准。 Windows 不能和不会在此模式下测试符合 FIPS 标准。

2.  基于软件的解决方案︰ Windows 实现符合 FIPS 标准的软件解决方案。 可以做到通过声明 DOT11\_EXTSTA\_属性\_安全模式\_OID\_支持，并实现 OID\_DOT11\_安全\_模式\_启用或 OID\_DOT11\_安全\_模式\_HT\_驱动程序中启用。

<a name="device.network.wlan.supportwifidirect"></a>
## <a name="devicenetworkwlansupportwifidirect"></a>Device.Network.WLAN.SupportWiFiDirect

### <a name="devicenetworkwlansupportwifidirectwifidirect-if-implemented"></a>Device.Network.WLAN.SupportWiFiDirect.WiFiDirect （如果实现）

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
</td></tr></table>

#### <a name="support-wi-fi-direct-base-functionality"></a>支持 Wi-Fi 直接基本功能

**说明**

如果实现，支持 Wi-fi 直接通过 Wi-fi 驱动程序启用 Miracast，公共 Api，可用于 Wi-fi 直接允许配对到和电脑、 接受和设备连接到其他 Wi-fi 直接转到与客户端角色。 这包括支持并发操作通过 Wi-fi 直接及站。

**详细信息**  

设备必须报告中推出 WIFI 的相关功能\_获得\_适配器\_WDI 规范的能力

-   WIFI\_虚拟化\_属性
-   WIFI\_P2P\_属性
-   WIFI\_带\_信息
-   WIFI\_PHY\_信息

如果支持此要求，则再设备必须能够执行以下操作在 WDI 规范中定义的

-   扫描的 Wi-Fi 直接设备和转到

-   可检测到为 Wi-fi 直接设备和转到

-   Wi-Fi 直接设备和转到与配对

-   接受传入配对从 Wi-Fi 直接设备和转到

-   连接到 Wi-fi 直接客户端或转到

-   接受传入的连接从 Wi-Fi 直接客户端或转到

-   对可扩展导致浏览器在期间配对和 （重新） 关联的支持

-   支持 Wi-Fi 直接连接而不考虑角色提供的链接质量和吞吐率

-   在转到或客户端角色通过 WIFI 支持操作系统通道的指示\_指示\_链接\_状态\_更改

#### <a name="support-background-discovery"></a>支持后台发现

**说明**

如果实现，支持 Wi-fi 直接设备的背景发现，这样的应用程序，使用 Wi-Fi 直接 API 来减轻发现能够更丰富的情况下通过允许应用程序，而无须定期扫描为它们找到的设备时获得通知。 对此功能的支持还可以更好的资源利用率。  

**详细信息**  

设备必须报告中推出 WIFI 的相关功能\_获得\_适配器\_WDI 规范的能力

-   WIFI\_虚拟化\_属性
-   WIFI\_P2P\_属性 

如果设备支持这一要求，它必须能够扫描 Wi-fi 直接设备和进入所有支持定期在 D0 状态。

#### <a name="support-ecsa"></a>支持 eCSA

**说明**

如果实现，支持根据 802.11 技术指标，在 Wi-fi 直接客户和 Wi-Fi 直接转增强通道开关发布 (eCSA)。 这将允许通过 NIC 移动转或响应 eCSA 请求连接到转到更好的性能。


**详细信息**

设备必须报告中推出 WIFI 的相关功能\_获得\_适配器\_WDI 规范的能力

-   WIFI\_接口\_属性 


如果支持此要求，则所有 Wi-Fi 直接端口必须都支持 eCSA。 如果设备处于转模式然后必须能够检测到远程设备 （连接到） 是否支持 eCSA 和 eCSA 用于移动到单通道配置它。 如果该设备是在客户端模式下，则响应 eCSA 请求从远程设备 （连接到）。 该设备必须报告操作系统通道更改为客户端和通过 WIFI 转到\_指示\_P2P\_组\_操作系统\_通道指示。

操作系统不会控制该设备的 eCSA 行为，这是设备特定的实现。

#### <a name="support-concurrency"></a>支持并发

**说明**

如果实现，支持的方案，例如 Miracast 或 Wi-fi 直接和 Wi-Fi 直接服务以及与 Internet 的连接进行操作。 如果没有为此支持，才能够连接到一个终端设备-示例不能连接到 Miracast 同时也连接到 Internet。


**详细信息**

设备必须报告中推出 WIFI 的相关功能\_获得\_适配器\_WDI 规范的能力

-   WIFI\_虚拟化\_属性
-   WIFI\_P2P\_属性


如果支持此要求，则设备必须能够同时在以下配置中不仅包括 Wi-Fi 直设备端口支持至少 2 Wi-Fi 直接角色端口︰

-   上一个 Wi-fi 直接端口组所有者 （转） 和客户端上其他 Wi-fi 直接并行端口

-   客户端上每个 Wi-fi 直接端口上同时

-   设备可以与基础结构连接，可以在不同频道同时支持跨不同区段 (2.4/5 GHz) 与 2 个并发通道。


2 通道和 2 端口并发的预期支持矩阵的示例

-   如果 WLAN 设备支持 802.11ac，然后︰

| &nbsp;       | **ExTSTA 端口** |     &nbsp;    |     &nbsp;     | **Wi-Fi 直接角色端口 1** |     &nbsp;    |    &nbsp;      | **Wi-Fi 直接角色端口 2** |    &nbsp;     |    &nbsp;      |
|-------------|-----------------|---------|----------|------------------------------|---------|----------|------------------------------|---------|----------|
| **案例\#** | 802.11 n         | 802.11 n | 802.11ac | 802.11 n                      | 802.11 n | 802.11ac | 802.11 n                      | 802.11 n | 802.11ac |
| ** **       | 2.4 g h z         | 5 Ghz   | 5 GHz    | 2.4 g h z                      | 5 Ghz   | 5 GHz    | 2.4 g h z                      | 5 Ghz   | 5 GHz    |
| **1**       | STA             | X       | X        | 转到                           | X       | X        | X                            | X       | X        |
| **2**       | STA             | X       | X        | 客户端                       | X       | X        | X                            | X       | X        |
| **4**       | STA             | X       | X        | X                            | 客户端  | X        | X                            | X       | X        |
| **6**       | STA             | X       | X        | X                            | X       | 客户端   | X                            | X       | X        |
| **7**       | STA             | X       | X        | 转到                           | X       | X        | 客户端                       | X       | X        |
| **8**       | STA             | X       | X        | 客户端                       | X       | X        | 客户端                       | X       | X        |
| **9**       | STA             | X       | X        | 转到                           | X       | X        | X                            | 客户端  | X        |
| **10**      | STA             | X       | X        | 客户端                       | X       | X        | X                            | 客户端  | X        |
| **11**      | STA             | X       | X        | 转到                           | X       | X        | X                            | X       | 客户端   |
| **12**      | STA             | X       | X        | 客户端                       | X       | X        | X                            | X       | 客户端   |
| **14**      | STA             | X       | X        | X                            | 客户端  | X        | X                            | 客户端  | X        |
| **16**      | STA             | X       | X        | X                            | 客户端  | X        | X                            | X       | 客户端   |
| **18**      | STA             | X       | X        | X                            | X       | 客户端   | X                            | X       | 客户端   |
| **19**      | X               | STA     | X        | 转到                           | X       | X        | X                            | X       | X        |
| **20**      | X               | STA     | X        | 客户端                       | X       | X        | X                            | X       | X        |
| **21**      | X               | STA     | X        | X                            | 转到      | X        | X                            | X       | X        |
| **22**      | X               | STA     | X        | X                            | 客户端  | X        | X                            | X       | X        |
| **23**      | X               | STA     | X        | X                            | X       | 转到       | X                            | X       | X        |
| **24**      | X               | STA     | X        | X                            | X       | 客户端   | X                            | X       | X        |
| **25**      | X               | STA     | X        | 转到                           | X       | X        | 客户端                       | X       | X        |
| **26**      | X               | STA     | X        | 客户端                       | X       | X        | 客户端                       | X       | X        |
| **27**      | X               | STA     | X        | 转到                           | X       | X        | X                            | 客户端  | X        |
| **28**      | X               | STA     | X        | 客户端                       | X       | X        | X                            | 客户端  | X        |
| **29**      | X               | STA     | X        | 转到                           | X       | X        | X                            | X       | 客户端   |
| **30**      | X               | STA     | X        | 客户端                       | X       | X        | X                            | X       | 客户端   |
| **31**      | X               | STA     | X        | X                            | 转到      | X        | X                            | 客户端  | X        |
| **32**      | X               | STA     | X        | X                            | 客户端  | X        | X                            | 客户端  | X        |
| **33**      | X               | STA     | X        | X                            | 转到      | X        | X                            | X       | 客户端   |
| **34**      | X               | STA     | X        | X                            | 客户端  | X        | X                            | X       | 客户端   |
| **35**      | X               | STA     | X        | X                            | X       | 转到       | X                            | X       | 客户端   |
| **36**      | X               | STA     | X        | X                            | X       | 客户端   | X                            | X       | 客户端   |
| **37**      | X               | X       | STA      | 转到                           | X       | X        | X                            | X       | X        |
| **38**      | X               | X       | STA      | 客户端                       | X       | X        | X                            | X       | X        |
| **39**      | X               | X       | STA      | X                            | 转到      | X        | X                            | X       | X        |
| **40**      | X               | X       | STA      | X                            | 客户端  | X        | X                            | X       | X        |
| **41**      | X               | X       | STA      | X                            | X       | 转到       | X                            | X       | X        |
| **42**      | X               | X       | STA      | X                            | X       | 客户端   | X                            | X       | X        |
| **43**      | X               | X       | STA      | 转到                           | X       | X        | 客户端                       | X       | X        |
| **44**      | X               | X       | STA      | 客户端                       | X       | X        | 客户端                       | X       | X        |
| **45**      | X               | X       | STA      | 转到                           | X       | X        | X                            | 客户端  | X        |
| **46**      | X               | X       | STA      | 客户端                       | X       | X        | X                            | 客户端  | X        |
| **47**      | X               | X       | STA      | 转到                           | X       | X        | X                            | X       | 客户端   |
| **48**      | X               | X       | STA      | 客户端                       | X       | X        | X                            | X       | 客户端   |
| **49**      | X               | X       | STA      | X                            | 转到      | X        | X                            | 客户端  | X        |
| **50**      | X               | X       | STA      | X                            | 客户端  | X        | X                            | 客户端  | X        |
| **51**      | X               | X       | STA      | X                            | 转到      | X        | X                            | X       | 客户端   |
| **52**      | X               | X       | STA      | X                            | 客户端  | X        | X                            | X       | 客户端   |
| **53**      | X               | X       | STA      | X                            | X       | 转到       | X                            | X       | 客户端   |
| **54**      | X               | X       | STA      | X                            | X       | 客户端   | X                            | X       | 客户端   |
| **55**      | X               | X       | X        | 转到                           | X       | X        | 客户端                       | X       | X        |
| **56**      | X               | X       | X        | 客户端                       | X       | X        | 客户端                       | X       | X        |
| **57**      | X               | X       | X        | 转到                           | X       | X        | X                            | 客户端  | X        |
| **58**      | X               | X       | X        | 客户端                       | X       | X        | X                            | 客户端  | X        |
| **59**      | X               | X       | X        | 转到                           | X       | X        | X                            | X       | 客户端   |
| **60**      | X               | X       | X        | 客户端                       | X       | X        | X                            | X       | 客户端   |
| **62**      | X               | X       | X        | X                            | 客户端  | X        | X                            | 客户端  | X        |
| **63**      | X               | X       | X        | X                            | 转到      | X        | X                            | X       | 客户端   |
| **64**      | X               | X       | X        | X                            | 客户端  | X        | X                            | X       | 客户端   |
| **66**      | X               | X       | X        | X                            | X       | 客户端   | X                            | X       | 客户端   |


-   如果 WLAN 设备不支持 802.11ac:

| **案例\#** | **红外线端口** |   &nbsp;    | **消防局端口 1** |    &nbsp;    | **消防局端口 2** |   &nbsp;     |
|-------------|----------------|-------|----------------|--------|----------------|--------|
| ** **       | 2.4 g h z        | 5 Ghz | 2.4 g h z        | 5 Ghz  | 2.4 g h z        | 5 Ghz  |
| **1**       | STA            | X     | 转到             | X      | X              | X      |
| **2**       | STA            | X     | 客户端         | X      | X              | X      |
| **4**       | STA            | X     | X              | 客户端 | X              | X      |
| **5**       | STA            | X     | 转到             | X      | 客户端         | X      |
| **6**       | STA            | X     | 客户端         | X      | 客户端         | X      |
| **7**       | STA            | X     | 转到             | X      | X              | 客户端 |
| **8**       | STA            | X     | 客户端         | X      | X              | 客户端 |
| **10**      | STA            | X     | X              | 客户端 | X              | 客户端 |
| **11**      | X              | STA   | 转到             | X      | X              | X      |
| **12**      | X              | STA   | 客户端         | X      | X              | X      |
| **13**      | X              | STA   | X              | 转到     | X              | X      |
| **14**      | X              | STA   | X              | 客户端 | X              | X      |
| **15**      | X              | STA   | 转到             | X      | 客户端         | X      |
| **16**      | X              | STA   | 客户端         | X      | 客户端         | X      |
| **17**      | X              | STA   | 转到             | X      | X              | 客户端 |
| **18**      | X              | STA   | 客户端         | X      | X              | 客户端 |
| **19**      | X              | STA   | X              | 转到     | X              | 客户端 |
| **20**      | X              | STA   | X              | 客户端 | X              | 客户端 |
| **21**      | X              | X     | 转到             | X      | 客户端         | X      |
| **22**      | X              | X     | 客户端         | X      | 客户端         | X      |
| **23**      | X              | X     | 转到             | X      | X              | 客户端 |
| **24**      | X              | X     | 客户端         | X      | X              | 客户端 |
| **26**      | X              | X     | X              | 客户端 | X              | 客户端 |

 

#### <a name="support-internet-sharing"></a>支持 Internet 共享

**说明**

如果实现，支持 Tethering 通过虚拟化包括 tethering 和工作站连接的并发操作支持自定义 SSID 和 WPA2 授权/加密的 Wi-Fi 端口。  

建议支持 tethering 至少 3 客户端设备。

设备必须报告中推出 WIFI 的相关功能\_获得\_适配器\_WDI 规范的能力

-   WIFI\_虚拟化\_属性
-   WIFI\_P2P\_属性
-   WIFI\_带\_信息
-   WIFI\_PHY\_信息

在消防局角色端口支持 WMM 高级的级别

**说明**

此要求捕获通过 Wi-fi 驱动程序所需的工作量。 这包括通过 Miracast、 站和 Bluetooth 的并发操作的支持。

**详细信息**

连接质量和 Wi-Fi 直接性能与 Miracast 方案至关重要。 设备评估服务将为您的设备提供结果，下面是合理质量 Miracast 连接的指导。  

应在所有端口包括虚拟的端口 – ExtSTA，支持 WMM Wi-Fi 直接角色端口 （组所有者） 和 Wi-Fi 直接角色端口 （客户端）。

-   NIC 应能够同时支持跨两个端口 (ExtSTA & 一个 Wi-fi 直接角色端口) 的优先顺序。

-   设置优先级基于 802.11e 通信访问类别 (AC) 标记。

-   当网卡进行虚拟化具有并发单通道中时，它必须能够确定传输通信跨基于 WMM 和媒体流指示不同的虚拟端口的优先级。

-   当网卡进行虚拟化具有并发跨多个通道时，它必须能够跨不同的虚拟端口基于 WMM 和媒体流指示优先传输通信，接收通信跨并发渠道提供服务。

WMM 优先顺序时用交流\_VI 或 AC\_VO （语音/视频），WLAN 设备应满足以下延迟和数据包丢失。

| ** **                                                  | **ExSTA**     | **Wi-Fi 直接角色端口** | **最大值。一种方法反应时间交流的 UDP\_VI/AC\_VO 通信** | **交流的数据包丢失\_VI/AC\_VO 通信** |
|--------------------------------------------------------|---------------|-----------------------------|-----------------------------------------------------------|-------------------------------------------|
| **只有 ExSTA**                                         | AC\_VI/AC\_VO | NA                          | 30ms                                                      | 0.5%，不超过 3 个连续的数据包 |
| ** **                                                  |               |                             |                                                           |                                           |
| **ExSTA + Wi-fi 直接在单通道并发** | AC\_VI/AC\_VO | &nbsp;                      | 30ms                                                      | 0.5%，不超过 3 个连续的数据包 |
| **&nbsp;**                                             | &nbsp;        | AC\_VI/AC\_VO               | 30ms                                                      | 0.5%，不超过 3 个连续的数据包 |
| **&nbsp;**                                             | AC\_VI/AC\_VO | AC\_VI/AC\_VO               | 30ms                                                      | 0.5%，不超过 3 个连续的数据包 |
| ** **                                                  |               |                             |                                                           |                                           |
| **ExSTA + Wi-fi 直接在多通道并发**  | AC\_VI/AC\_VO | &nbsp;                      | 40 毫秒                                                      | 0.5%，不超过 3 个连续的数据包 |
| **&nbsp;**                                             | &nbsp;        | AC\_VI/AC\_VO               | 40 毫秒                                                      | 0.5%，不超过 3 个连续的数据包 |
| **&nbsp;**                                             | AC\_VI/AC\_VO | AC\_VI/AC\_VO               | 50 毫秒                                                      | 0.5%，不超过 3 个连续的数据包 |

<a name="device.network.wlan.supportwifidirectservices "></a>
## <a name="devicenetworkwlansupportwifidirectservices"></a>Device.Network.WLAN.SupportWiFiDirectServices 

### <a name="devicenetworkwlansupportwifidirectwifidirectservices-if-implementedwdi-drivers-only"></a>Device.Network.WLAN.SupportWiFiDirect.WiFiDirectServices （如果实现）**（仅 WDI 驱动程序）**

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
</td></tr></table>

**说明**

如果实现**，**支持 Wi-Fi 直接通过 Wi-fi 驱动程序启用 Wi-fi 直接服务订阅和发布 Wi-Fi 直接服务。 Windows SDK 提供 Api 的使用 Wi-Fi 的直接服务，使应用程序开发人员可以构建对等应用程序，例如︰ 多人游戏、 文件共享或与设备同步 

**详细信息**  

设备必须报告按照 WDI 规范了以下功能︰

-   行动框架支持的 WDI\_接口\_属性

-   服务发现中 WDI 支持\_P2P\_属性

WDI 中支持的 P2P 服务名称发现\_P2P\_ATTRIBUTESMax P2P 服务名称公布字节中支持 WDI\_P2P\_ATTRIBUTESOptional 支持建议为下面列出的功能︰

-   后台发现 P2P 设备和服务 WDI\_P2P\_属性 （强烈推荐）

-   WDI 被动可用性侦听状态\_P2P\_属性 （强烈推荐）

-   WDI 支持 P2P 服务信息发现\_P2P\_属性

-   最大的 P2P 服务信息广告字节支持 WDI\_P2P\_属性

如果支持这一要求，则设备必须能够 WDI 规范中定义，请执行以下操作︰

-   对 Wi-Fi 直接支持

-   支持发送请求和响应的操作框架

-   查询 AQNP 的支持

-   用于指示接收操作框架支持

<a name="device.network.wlan.supportwirelessdocking"></a>
## <a name="devicenetworkwlansupportwirelessdocking"></a>Device.Network.WLAN.SupportWirelessDocking

### <a name="devicenetworkwlansupportwirelessdocking-if-implemented-wdi-drivers-only"></a>Device.Network.WLAN.SupportWirelessDocking （如果实现） **（仅 WDI 驱动程序）**

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
</td></tr></table>
**说明︰**

通过 802.11ac 或 802.11ad 的无线坞站解决方案必须使用 Wi-fi 驱动程序接口 (WDI) 驱动程序，它提供坞站和装饰发现 / 连接通过本机对等和 Wi-Fi 直接服务协议。 请 Wi-fi 驱动程序接口 (WDI) 规范 1.0.20 或更高版本的功能实现的详细信息，参阅

如果在使用 802.11ad 时，必须申报下列新的 PHY 类型︰

**实现 802.11ad （如果实现）**

设备必须报告 802.11ad PHY 类型 9 (WDI\_PHY\_类型\_DMG) 在 WDI\_PHY\_信息结构由 OID\_WDI\_获得\_适配器\_功能。

<a name="device.network.wlan.supporthostednetwork"></a>
## <a name="devicenetworkwlansupporthostednetwork"></a>Device.Network.WLAN.SupportHostedNetwork

### <a name="devicenetworkwlansupporthostednetworkhostednetwork-if-implemented-native-wi-fi-drivers-only"></a>Device.Network.WLAN.SupportHostedNetwork.HostedNetwork （如果实现） **（仅本机 Wi-fi 驱动程序）**

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
</td></tr></table>
**说明︰**

使用此功能，Windows 计算机可以使用单个物理无线适配器作为硬件接入点 (AP)，而在同一时间作为一种软件允许其他无线功能的设备的接入点连接到该客户端连接。

