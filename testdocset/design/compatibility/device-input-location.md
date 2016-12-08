---
title: Device.Input.Location
Description: "Windows 10 位置驱动程序可以实现与传统传感器类扩展驱动程序集成在一起或者 GNSS 驱动程序或 Windows 10 中引入 GNSS GNSS DDI 相结合的驱动程序。"
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: e2e798929b6d558188451d2dc975aee2b0232cec
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.Input.Location

 - [Device.Input.Location](#device.input.location)
-->

<a name="device.input.location"></a>
##Device.Input.Location

*Windows 10 位置驱动程序可以实现以下驱动程序模型之一。*

-   与传统的传感器类扩展驱动程序集成的 GNSS 驱动程序

*OR*

-   在 Windows 10 中引入集成与 GNSS DDI 的 GNSS 驱动程序

### <a name="deviceinputlocationactivetracking-if-implemented"></a>Device.Input.Location.ActiveTracking （如果实现）

*活动跟踪 breadcrumbing*

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

此项要求允许 GNSS 芯片可积极跟踪基于 breadcrumbing 技术的用户所在的位置。 操作系统将减轻对硬件的 breadcrumbing 和接收用户位置时所需。 此功能允许操作系统更精细的方式收集用户的位置的历史记录。

### <a name="deviceinputlocationassistedgnss-if-implemented"></a>Device.Input.Location.AssistedGNSS （如果实现）

*仅当您硬件给定类型的辅助 GNSS 的使用位置堆栈相关。*

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

协助向 GNSS 接收器用于启用接收方获得位置速度更快，以启用购置甚至在情况下的信号非常微弱，并且这样做在较低功率。 与粗糙的职位提供 GNSS 设备位置平台支持，大致时间，而且它还可以作为 GNSS 设备所支持的专有 ephemeris 格式的代理服务器。

### <a name="deviceinputlocationbase"></a>Device.Input.Location.Base

*定位设备必须支持以下基本功能。*

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

定位设备必须能够接收位置的请求和响应提供一个位置或错误的平台与正确交互。 必须支持交换的功能，以及配置命令，取决于哪种功能驱动程序界面中存在并且是强制性的。 需要确保它们位置会话和位置会话参数的类型确定的时间间隔报告位置数据位置的所有设备。 该应用程序所需的准确性，并应考虑其他会话参数以尽可能高效地提供位置数据。

支持两种驱动程序模型，因为我们有每个要求的特定要求和测试。

***与传统的传感器类扩展驱动程序集成的 GNSS 驱动程序***

GNSS 设备必须支持以下基本要求︰

<html><!--edit: improve layout and tagging of these lists, tables, and blockquotes-->
    <ul>
        <li><p><strong>数据字段支持的位置报告</strong></p></li>
    </ul>
    <blockquote>
        <p>-位置 API 公开通过标准的内置报告的位置数据。 这些报告填充位置传感器的位置 API 自动管理的。</p>
        <p>位置传感器设备的报告其类别为 SENSOR_CATEGORY_LOCATION，（尽管设备驱动程序接口 ISensorDriver::OnGetSupportedSensorObjects 和 IsensorDriver::OnGetProperties()) 必须支持一种内置的报告，以便位置 API 可以管理传感器并汇报其数据。 每个内置报告具有一组预期的数据字段 (尽管设备驱动程序接口 IsensorDriver::OnGetSupportedDataFields() 和 IsensorDriver::OnGetDataFields()) 查找位置 API。</p>
        <p>-所有内置报告要求 SENSOR_DATA_TYPE_TIMESTAMP 将提供除指定的字段。 此字段报告在 UTC 中收集数据的时间。</p>
        <p>-位置 API 支持内置报表︰ LatLongReport，这就需要在纬度/经度 （纬度/经度） 和错误的响应度量值。  对 LatLongReport 的支持是必需的所有位置传感器。</p>
        <p>若要支持 LatLongReport，以下字段是必需的︰</p>
    </blockquote>
    <table>
        <thead>
            <tr class="header">
                <th>数据字段</th>
                <th>数据类型</th>
                <th>详细信息</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <td>SENSOR_DATA_TYPE_LATITUDE_DEGREES</td>
                <td>VT_R8</td>
                <td>显示中度，必须在 [-90、 + 90] 范围内的当前的纬度</td>
            </tr>
            <tr class="even">
                <td>SENSOR_DATA_TYPE_LONGITUDE_DEGREES</td>
                <td>VT_R8</td>
                <td>显示中度，必须在 [-180、 180] 范围内的当前的经度</td>
            </tr>
            <tr class="odd">
                <td>SENSOR_DATA_TYPE_ERROR_RADIUS_METERS</td>
                <td>VT_R8</td>
                <td>实际的纬度和经度必须在报告 （纬度，经度） 周围绘制一个圆，该半径 （以米为单位）。 启用位置 API 来确定优先级的传感器;它应动态更新，并必须为非零值，正数。</td>
            </tr>
        </tbody>
    </table>
    <p>作为 LatLongReport 的一部分，以下字段是可选的但必须申报时可用︰</p>
    <table>
        <thead>
            <tr class="header">
                <th>可选的数据字段</th>
                <th>数据类型</th>
                <th>详细信息</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <td>SENSOR_DATA_TYPE_ALTITUDE_ELLIPSOID_METERS</td>
                <td>VT_R8</td>
                <td>海拔高度 （以米为单位） WGS84 椭圆体方面</td>
            </tr>
            <tr class="even">
                <td>SENSOR_DATA_TYPE_ALTITUDE_ELLIPSOID_ERROR_METERS</td>
                <td>VT_R8</td>
                <td>这一错误当前海拔测量 （以米为单位）</td>
            </tr>
        </tbody>
    </table>
    <blockquote>
        <p>
            <br />
重要提示︰ 位置 API 支持一组额外的数据 （对应于字段 NMEA 数据字段）。 有关详细信息，请参阅 WDK 的设备和驱动程序技术部分中的传感器主题。
        </p>
    </blockquote>
    <p> </p>
    <blockquote>
        <p>下面的要求确保驱动程序引发事件位置报告，以正确的方式。 如果不遵循正确的行为，则位置 API 将阻止传感器，和客户端应用程序将无法接收数据。</p>
    </blockquote>
    <ul>
        <li>
            <p>
                <strong>传感器的数据报告的生成</strong></p>
                <p>该设备必须能够生成有效的 ISensorDataReports 一系列有关的一个或两个两个的位置报告类型。 每个生成的报表必须至少包含报表类型的最小值的数据字段。<br />
传感器和位置平台将依赖于设备驱动程序已实现传感器的设备驱动程序接口，通过该平台提供的数据。 在大多数情况下将使用传感器和位置平台验证设备。
            </p>
        </li>
        <li>
            <p>
                <strong>有关可设置的属性的说明</strong></p>
                <p>作为筛选和电源管理标准，以下可设置的属性必须使用设备驱动程序中。 这两个属性必须跟踪每个客户端。
            </p>
        </li>
    </ul>
    <blockquote>
        <p>这些属性为需要实现可设置为︰</p>
    </blockquote>
    <table>
        <thead>
            <tr class="header">
                <th>属性</th>
                <th>数据类型</th>
                <th>详细信息</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <td>SENSOR_PROPERTY_CURRENT_REPORT_INTERVAL</td>
                <td>VT_UI4</td>
                <td>设置客户端想要接收来自传感器的数据报告中的最小的频率 （以毫秒为单位）。</td>
            </tr>
            <tr class="even">
                <td>
SENSOR_PROPERTY_LOCATION_DESIRED_ACCURACY<br />
                </td>
                <td>VT_UI4</td>
                <td>
设置提示如何准确驱动程序应努力。<br />
DESIRED_ACCURACY_DEFAULT︰ 传感器应优化电源和其他成本因素。 将枚举位置 api GNS 传感器，除非是从其他提供程序在系统上不可用的位置数据或数据的准确性是小于 500 米。<br />
DESIRED_ACCURACY_HIGH︰ 传感器都会提供可能的最高精确度报告。 位置 API 将始终连接到所有位置传感器 （包括 GNSS） 以获得可能的最准确的位置。
                </td>
            </tr>
        </tbody>
    </table>
    <p><em><strong>GNSS 的驱动程序与 GNSS DDI 集成 Windows 10 中引入了</strong></em></p>
    <p>GNSS 设备必须支持以下基本要求︰</p>
    <table>
        <thead>
            <tr class="header">
                <th><strong>平台和驱动程序功能交换</strong></th>
                <td>
                    <p>检查平台 (GNSS_SEND_PLATFORM_CAPABILITY) 和关于它们各自的功能的驱动程序 (GNSS_GET_DEVICE_CAPABILITY) 之间的交换。 预期结果是，驱动程序正确发送到平台的设备功能，考虑到定位平台将相应地调整其行为。</p>
                    <p>距离跟踪和 geofencing 等功能时可以将它们转移到 GNSS 设备应仅将声明，这将是当它们不需要应用程序处理器进行跟踪。</p>
                </td>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <td><strong>驱动程序命令检查</strong></td>
                <td>检查基本的驱动程序命令所需的产品和测试支持。 一样，ClearAgnssData。</td>
            </tr>
            <tr class="even">
                <td><strong>检查基本的单个快照</strong></td>
                <td>开始一个快照会话，直到收到最后修复运行。 预计最终修复被交付在 2 分钟内。 在这种情况下可能会提供协助的数据。 在协助数据的情况下最终修复有望在 10 秒内传送。</td>
            </tr>
            <tr class="odd">
                <td><strong>完全独立基本单个拍摄的检查</strong></td>
                <td>确保在冷状态，并不具有访问权限的任何类型，AGNSS 的驱动程序仍可以实现单个快照请求的最终解决方法。 预计最终修复被交付在 2 分钟内。</td>
            </tr>
            <tr class="even">
                <td><strong>单个快照多个相邻会话检查</strong></td>
                <td>检查，一百个单个快照会话可以运行一个接一个未出现任何问题。 期望每一个快照会话到达最终修复没有问题。</td>
            </tr>
        </tbody>
    </table>
</html>


### <a name="deviceinputlocationgeofencing-if-implemented"></a>Device.Input.Location.Geofencing （如果实现）

*如果硬件支持 Geofencing 和 Windows 10 中引入 GNSS DDI 集成 GNSS 驱动程序仅支持这一要求。*

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

此项要求允许 GPS 来定义地理边界或虚拟的障碍。 当设备进入或离开 geofence，它允许移动设备到触发器操作或通知管理员。 可行的用途包括零售商店所有者创建零售商店周围 geofence 并将优惠券发送给他/她在移动设备上应用零售商店应用程序与客户的能力。

如果实施，设备必须能够支持以下要求。

| **基本的 Geofence**    | GeoFence 可以成功地添加和删除。 必须检查一致性。                                                                                                                     |
|------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Geofence 跟踪 1**   | 添加 Geofence 周围未知状态与您当前的位置并验证输入事件。                                                                                                          |
| **Geofence 轨道 2**   | 添加输入状态与 Geofence，以便您当前的位置是 Geofence 的外侧。 确认退出事件。                                                                              |
| **Geofence 轨道 3**   | 添加 Geofence 周围输入状态与您当前的位置并验证会触发任何事件                                                                                            |
| **Geofence 跟踪 4**   | 添加 EXITED 状态与 Geofence，以便您当前的位置是 Geofence 的外侧。 验证会触发任何事件。                                                                    |
| **Geofence 轨道 5**   | 作为退出仅添加未知状态与您当前的位置周围 Geofence 和警报类型并验证不接收的任何事件                                                                 |
| **Geofence 轨道 6**   | 这样您当前的位置位于外 Geofence 和设置警报类型到输入和验证接收的事件不只是添加 Geofence （带有输入状态）                           |
| **可靠性**        | 获取硬件支持的 geofences 的最大数量。 围绕当前的位置，与此最大数目的 Geofences 未知状态，期望该入口/出口事件数设置。 |
| **Geofence 清除**    | 添加多个 Geofences，然后同时将其清除。 必须检查一致性。                                                                                                             |
| **Geofence 负** | 添加错误 （零半径） 参数与 Geofence。                                                                                                                                               |
| **Geofence 边界** | 添加 Geofence 很小的半径 （5 米）。                                                                                                                                                     |

### <a name="deviceinputlocationsupl-if-implemented"></a>Device.Input.Location.SUPL （如果实现）

*这一要求是只适用于与 GNSS DDI 引入 Windows 10 中集成了 GNSS 驱动程序。*

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

安全用户平面位置 (SUPL) 客户端必须由 IHV 支持移动运营需求来实现。 驱动程序接口提供了配置 SUPL 客户端上，对于移动运营中获得的信息的机制。 向移动操作员相关位置平台所支持的唯一 SUPL 配置是，只有一个 SUPL 配置支持一次。

本节中的测试可确保 SUPL 客户端能够接收从位置平台 SUPL 配置命令。 HLK 验证 GNSS 驱动程序和用户通知接收的 NI （网络启动） 位置请求时支持位置平台之间的集成中有任何测试。 这种验证将需要在完成使用专用的系统并验证 SUPL OMA 一致性的测试套件。

### <a name="deviceinputlocationv2pul-if-implemented"></a>Device.Input.Location.V2PUL （如果实现）

*这一要求是只适用于与 GNSS DDI 引入 Windows 10 中集成了 GNSS 驱动程序。*

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

V2 用户平面位置 (V2UPL) 要求仅适用于设备使用 CDMA 蜂窝移动通信连接，并根据需要由移动运营商。
