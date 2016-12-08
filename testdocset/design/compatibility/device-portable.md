---
title: Device.Portable
Description: "要求。"
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 16e3a06e4ea69ee4f8e1b402484bd34a872e903e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="deviceportable"></a>Device.Portable

 - [Device.Portable.Core](#device.portable.core)
 - [Device.Portable.DigitalCamera](#device.portable.digitalcamera)
 - [Device.Portable.DigitalVideoCamera](#device.portable.digitalvideocamera)
 - [Device.Portable.MediaPlayer](#device.portable.mediaplayer)
 - [Device.Portable.MobilePhone](#device.portable.mobilephone)

<a name="device.portable.core"></a>
## <a name="deviceportablecore"></a>Device.Portable.Core

*核心*

### <a name="deviceportablecoreaudiocodec"></a>Device.Portable.Core.AudioCodec

*如果便携式设备可以捕获音频内容，它必须做到使用在 Windows 本身支持的格式。*

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

如果便携设备可以捕获音频内容，它必须在 Windows 本身理解的格式操作。

下表表示列表框中格式 Windows 将呈现这不是受支持的格式在 Windows 中详尽。 支持格式的完整列表，请访问︰ <http://go.microsoft.com/fwlink/?LinkID=242995&clcid=0x409>。

**注意**，对于不需要支持所有给定的比特率和采样率下表中的给定格式，但是需要支持的格式，行提供的范围内。

<html>
    <p><strong>MP4 音频内容</strong></p>
    <table>
        <thead>
            <tr class="header">
                <th></th>
                <th>设置</th>
                <th>要求</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <td rowspan="4">AAC</td>
                <td>编解码器</td>
                <td>
AAC 标准，AAC 配置文件级别 2 最小 (0x29)<br />
与兼容 (0x29、 0x2A，0x2B，0x2C，0x2E，0x2F，0x30，0x31，0x32，0x33)                </td>
            </tr>
            <tr class="even">
                <td>CBR 的比特率</td>
                <td>96、 128、 160，192 kbps 速率进行传输</td>
            </tr>
            <tr class="odd">
                <td>采样速率</td>
                <td>44.1 或 48 kHz</td>
            </tr>
            <tr class="even">
                <td>频道</td>
                <td>2</td>
            </tr>
        </tbody>
    </table>
    <p>
        <br />
        <strong>MP3 音频内容</strong>
    </p>
    <table>
        <thead>
            <tr class="header">
                <th></th>
                <th>设置</th>
                <th>要求</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <td rowspan="4">MP3</td>
                <td>编解码器</td>
                <td>Version1 Layer3</td>
            </tr>
            <tr class="even">
                <td>CBR 文件的比特率</td>
                <td>从 32 到 320 千比特每秒 (Kbps)</td>
            </tr>
            <tr class="odd">
                <td>采样速率</td>
                <td>16、 22.05、 24、 32、 44.1，48 khz</td>
            </tr>
            <tr class="even">
                <td>频道</td>
                <td>2</td>
            </tr>
        </tbody>
    </table>
    <p>
        <br />
        <strong>WMA 音频内容</strong>
    </p>
    <table>
        <thead>
            <tr class="header">
                <th></th>
                <th>设置</th>
                <th>要求</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <td rowspan="6">WMA 标准</td>
                <td>编解码器</td>
                <td>WMA9 或更高版本</td>
            </tr>
            <tr class="even">
                <td>CBR 文件的比特率</td>
                <td>从 32 到 256 千比特每秒 (Kbps)</td>
            </tr>
            <tr class="odd">
                <td>VBR 文件的平均比特率</td>
                <td>从 48 到 160 kbps 的通信量</td>
            </tr>
            <tr class="even">
                <td>最大峰值的 VBR 文件的比特率</td>
                <td>256 kbps 速率进行传输</td>
            </tr>
            <tr class="odd">
                <td>采样速率</td>
                <td>44.1 或 48 khz</td>
            </tr>
            <tr class="even">
                <td>频道</td>
                <td>2</td>
            </tr>
        </tbody>
    </table>
</html>
 

### <a name="deviceportablecorecustomdeviceservices"></a>Device.Portable.Core.CustomDeviceServices

*实现自定义的 MTP 服务的便携式设备必须满足 MTP 设备服务扩展规范中定义的要求。*

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

MTP 设备服务扩展到媒体传输协议 (MTP) 有助于 MTP 发起方，在这种情况下 Windows、 查找和访问特定类型的内容存储设备上。  已定义扩展机制处理设备所定义的特定内容类型的应用程序提供更大的灵活性。 这些机制可提供更大的可扩展性，比当前定义的媒体传输协议规范，修订版本 1.0 的现有数据的代码机制。

便携设备是否支持自定义设备服务，实现必须具有有效的*ServiceInfo*数据集、 一个有效的*ServiceCapabilities*数据集，以及一个有效的*ServicePropertiesDesc*数据集，因为 MTP 设备服务扩展规范中定义。 规范中定义的所有必需的属性必须支持自定义的服务中。

下表是一份实施 MTP 服务时必需的操作︰

| 操作              | MTP Datacode | 说明                                                                                                                                                                               |
|------------------------|--------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| GetServiceIDs          | 0x9301       | 该操作返回一个数组的 ServiceIDs。                                                                                                                                            |
| GetServiceInfo         | 0x9302       | 此操作将返回 ServiceInfo 数据集的服务。                                                                                                                             |
| GetServiceCapabilities | 0x9303       | 通过使用 GetServiceCapabilities 操作报告所有对象格式和方法的格式信息。                                                                                |
| GetServicePropDesc     | 0x9304       | 此操作将返回 theServicePropertyDesc 数据集的服务。                                                                                                                      |
| GetServicePropList     | 0x9305       | 此操作是类似于 GetObjectPropList 中的 MTP 规范版本 1.0。 GetServicePropList 服务中读取属性。                                                |
| SetServicePropList     | 0x9306       | 此操作通过使用 ServicePropList 数据集设置 ServiceProperty。 它使写入属性值的服务。                                                       |
| UpdateObjectPropList   | 0x9307       | 此操作将设置将更新与新的二进制对象的特定对象的属性列表。 此操作可用于替换现有对象的二进制数据。 |
| DeleteObjectPropList   | 0x9308       | 此操作将删除在 DeleteObjectPropList 数据集从指定的对象或对象中指定的属性。                                                        |
| DeleteServicePropList  | 0x9309       | 此操作将删除在 DeleteServicePropList 数据集从指定的服务中指定的属性。                                                                 |

 
如果可以使用 MTP 规范中定义的功能来实现的情况下不使用实现的操作设备的属性、 定义中的 MTP 1.0 规范 （或更高版本），则设备必须定义这些设备服务的方案，并且必须支持这些服务根据 MTP 设备服务扩展规范中定义的要求等。 例如，可以定义介质交换服务来管理媒体同步之间发起方和响应程序替换标准 MTP 1.0 行为所支持的功能。

Device Stage 中公开自定义设备服务，必须创作自定义任务并将其定义为设备舞台创作过程的一部分。 这被介绍 Microsoft 设备经验开发工具包。

*设计备注*

-   请参阅 MTP 设备服务扩展指标网址*http://msdn.microsoft.com/en-us/windows/hardware/gg463541.aspx*。

-   请参阅 Microsoft 设备经验开发工具包网址*http://msdn.microsoft.com/en-us/windows/hardware/gg463154.aspx*。

### <a name="deviceportablecoredeviceservices"></a>Device.Portable.Core.DeviceServices

*MTP 服务定义支持的便携设备必须实现这些服务根据 MTP 设备服务为 Windows 规范中定义的要求。*

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

MTP 设备服务体系结构使 Windows 查找并使用各种服务和设备上的内容类型。 通过创建 WPD API 和 MTP 协议的扩展，Windows 可以找到、 使用，并与有用的内容和设备上的服务进行交互。

支持个人信息管理 (PIM) 服务︰

-   联系服务
-   服务日历
-   说明服务
-   服务任务

其他支持的服务︰

-   状态服务
-   提示服务
-   设备元数据服务
-   铃声服务
-   SMS 服务

如果设备支持一个或多个 PIM 服务，它还必须支持的两个同步服务才能实际同步数据。 Windows 支持下面的框中︰

-   枚举同步
-   同步定位点

它最多是制造商选择的服务最适合于该设备。

供应商选择支持自定义 Device Stage 元数据包，应确保，适当的任务设备属性暴露或正确的包中。

对于服务可由服务意识到启动器，以下服务相关的设备还必须支持的操作︰

| 操作              | MTP Datacode | 说明                                                                                                                                                                               |
|------------------------|--------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| GetServiceIDs          | 0x9301       | 该操作返回一个数组的 ServiceIDs。                                                                                                                                            |
| GetServiceInfo         | 0x9302       | 此操作将返回 ServiceInfo 数据集的服务。                                                                                                                             |
| GetServiceCapabilities | 0x9303       | 通过使用 GetServiceCapabilities 操作报告所有对象格式和方法的格式信息。                                                                                |
| GetServicePropDesc     | 0x9304       | 此操作将返回 theServicePropertyDesc 数据集的服务。                                                                                                                      |
| GetServicePropList     | 0x9305       | 此操作是类似于 GetObjectPropList 中的 MTP 规范版本 1.0。 GetServicePropList 服务中读取属性。                                                |
| SetServicePropList     | 0x9306       | 此操作通过使用 ServicePropList 数据集设置 ServiceProperty。 它使写入属性值的服务。                                                       |
| UpdateObjectPropList   | 0x9307       | 此操作将设置将更新与新的二进制对象的特定对象的属性列表。 此操作可用于替换现有对象的二进制数据。 |
| DeleteObjectPropList   | 0x9308       | 此操作将删除在 DeleteObjectPropList 数据集从指定的对象或对象中指定的属性。                                                        |
| DeleteServicePropList  | 0x9309       | 此操作将删除在 DeleteServicePropList 数据集从指定的服务中指定的属性。                                                                 |

 

*设计备注*

-   有关定义的 MTP 服务的信息，请参阅 MTP 设备服务为 Windows 规范网址<http://msdn.microsoft.com/en-us/windows/hardware/gg463544>*.*

-   有关服务操作和一般服务的详细信息，请参阅 MTP 设备服务扩展规范网址<http://msdn.microsoft.com/en-us/windows/hardware/gg463545>。

-   请参见元数据架构和网址<http://msdn.microsoft.com/en-us/windows/hardware/gg463153>*.*的软件包格式规范

### <a name="deviceportablecoremediasync"></a>Device.Portable.Core.MediaSync

*支持媒体内容的便携设备必须满足基本的互操作性要求，成功地在 Windows 上传输与 MTP 意识到媒体播放器应用程序的内容。*

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

基于 MTP 设备必须能够传输数据传入和传出的基于 Windows 应用程序支持 MTP 使用电脑。

**注意**，如果设备代替核心 MTP 媒体处理功能与自定义的 MTP 服务，然后使用 Windows Media Player 的互操作性将无法按预期运行。 实现自定义服务的设备必须有与核心 MTP 操作以支持媒体传输的功能性奇偶校验和与 WPD 基于应用程序的同步。

与 Windows Media Player 交互时，必须满足以下要求︰

**支持从设备到计算机的数字媒体传输**该设备必须支持数字媒体传输到计算机的应用程序启用此类转移，如便携式设备外壳 Namespace 扩展和 Windows Media Player。

**支持数字媒体传输到设备的计算机**该设备必须支持支持的媒体格式计算机传输到设备通过 Windows Media Player。 该设备必须支持从计算机到通过 Windows® Namespace 扩展设备传输所有文件格式。

**支持元数据更新-**设备必须支持 MTP 元数据的更新后的原始轨道已复制到该设备。 使用 Windows Media Player 执行元数据更新。

**支持取消的传输和同步的**该设备必须支持的传输和同步取消中间任务而不会崩溃或挂起的设备。

**能正确识别的文件类型-**该设备必须不依赖于要查找的文件类型的文件的文件扩展名。 该设备可以使用 MTP 对象格式，也可以分析该文件的内容以确定文件类型。

**提供设备对象元数据的**如果一台主机发送唱片集、 艺术家或标题为空值，该设备必须显示有意义的文字来代替空的元数据并允许用户在用户界面的设备相关联的字段上的搜索时查找内容。 例如，设备可能使用未知艺术家艺术家收到艺术家元数据为空值时。 如果设备支持显示流派元数据，然后如果主机发送流派为空值，该设备必须显示有意义的文字来代替空的元数据并允许用户在用户界面的设备相关联的字段上的搜索时查找内容。

**播放列表传送-**该设备必须支持传输的由使用 Windows Media Player 的用户手动创建的播放列表。 手动播放列表传输时使用 Windows Media Player，播放列表，播放列表的内容的引用必须位于该设备上。

要从 Windows Media Player 中接收播放列表，设备必须支持的对象引用。 如果受支持的对象引用，它们必须对所有媒体文件格式支持。 对对象的引用的支持表示支持下面的命令︰

-   GetObjectReferences (0x9810)
-   SetObjectReferences (0x9811)

该设备还必须支持 AbstractAudioVideoPlaylist (0xBA05) 格式。 播放列表是包含在播放列表中的所有对象作为一个 0 字节的对象句柄的引用列表都发送。

### <a name="deviceportablecoremodelid"></a>Device.Portable.Core.ModelID

*便携设备可能支持可选的 ModelID 属性来唯一标识逻辑设备功能的多功能设备上。*

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

插支持一个名为 DEVPKEY 的 DevNode 属性\_设备\_ModelId。 此参数用于存储将存储在该设备上的特定于类的设备或特定制造商的方式中的某些设备的 ModelID 值。

ModelID 跨越上通过在 Windows 7 中称为聚合逻辑设备中的一个"塑料片"表示该显示对象的内部结构的多功能设备的逻辑设备功能。  ModelID 可以为特定或通用制造商选择。 例如，ModelID 可能两种产品模型，单个模型或甚至是个别设备的颜色不同。 为支持 ModelID，必须支持必需的属性的设备属性代码 0xD302。

*设计备注*

-   请参阅随 Windows 便携设备启用工具包，网址<http://msdn.microsoft.com/en-us/windows/hardware/gg463545>MTP 设备服务扩展指标。

### <a name="deviceportablecoremtp"></a>Device.Portable.Core.MTP

*便携设备必须支持一组核心的 MTP 操作和设备属性中的媒体传输协议修订版本 1.0 或以后版本，以及设备的属性和对象的特定设备类型的格式定义。*

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

媒体传输协议 (MTP) 是图片传输协议 (ISO 15740) 的扩展。  这两个规范包括可选的命令或操作，但其中一些所需的证书。 还有一组核心操作和必须满足的每个设备类别的与 Windows 兼容的设备属性。 MTP 的实现详细信息在媒体传输协议规范，修订版本 1.0 或更高版本中定义，并将用于作为参照所有的便携设备的证书作为 Windows 硬件认证计划的一部分。

 
**支持 MTP 驱动程序**便携设备必须使用 Windows 附带的收件箱 MTP 驱动程序。 这意味着他们必须安装并立即使用，而无需安装其他驱动程序或软件。

**默认情况下支持 MTP**便携设备必须随附 MTP 启用为默认的连接模式。 设备可以支持大容量存储类 (MSC) 除了 MTP。

-   该设备不能有持久的用户可以访问设置来启用或禁用 MTP 或 MSC 模式。

-   （内部的和外部的） 的设备上的所有存储卷都必须可以访问使用 MTP 协议。

一个设备可以允许用户引导至设备恢复方案的 MSC 模式的安全模式。 在用户断开连接连接在安全模式下的设备后，设备必须恢复正常操作。

**设备信息数据集**该设备必须支持 MTP DeviceInfo 数据集。 下表说明了必须实现特定于字段的要求︰

| 数据集字段               | 要求 | 注释                                                                                                                                                                                                                                               |
|-----------------------------|-------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 标准版            | R           | 这标识这个设备可支持在百分之几秒的 PTP 版本。 对于 MTP 设备，这不应包含值 100 （代表 1.00）。                                                                                                       |
| MTP 供应商扩展 ID     | R           | 这此设备的标识使用中的 MTP 供应商扩展版本。                                                                                                                                                                             |
| MTP 版本                 | R           | 它标识该设备支持的 MTP 标准的版本。 MTP 设备实现 MTP 1.0，这不应包含的值 （表示 1.00） 100。 对于实现 MTP 2.0 的 MTP 设备，这不应包含 200。 |
| MTP 扩展              | I           | 此字符串用于标识应用于 MTP 任何扩展集。                                                                                                                                                                                  |
| 功能的模式             | R           | 模式允许设备来表达不同具有不同的功能状态。 如果设备支持只有一种模式，则此字段应包含值 0x00000000。 MTP 规范的详细信息，请参阅。                                                  |
| 支持的操作        | R           | 此字段标识 datacode 通过此设备支持当前的功能模式中的所有操作。                                                                                                                                          |
| 支持事件            | I           | 此字段标识 datacode 通过该设备可以在当前功能模式中生成的所有事件。                                                                                                                                          |
| 支持的设备属性 | R           | 此字段标识 datacode 通过此设备支持在当前正常工作模式下的所有设备属性。                                                                                                                                   |
| 捕获的格式             | I           | 此字段由 datacode （即，没有内容放置在设备上） 此设备可以独立生成每种格式对象格式代码的标识。                                                                    |
| 播放格式            | I           | 此字段由 datacode，此设备可以理解，如果放置在设备上分析每一种格式对象格式代码的标识。<br/><br/>如果该设备可以携带未经确认的二进制对象如果不了解这些，它应指明这通过在其播放格式中包括未定义对象 (0x3000) 的代码。 |
| 制造商                | R           | MTP 规范标识为一个可选的字符串;它是必需的硬件认证。 此字段包含可读的字符串，用于标识该设备的制造商。                                                    |
| 模型                       | R           | MTP 规范标识为一个可选的字符串;它是必需的硬件认证。 此字段包含可读的字符串，用于标识该设备的模型。                                                           |
| 设备版本              | R           | MTP 规范标识为一个可选的字符串;它是必需的硬件认证。 此字段包含可读的字符串，用于标识该设备的软件或固件版本。                                    |
| 序列号               | R           | 序列号必须是唯一的而所有设备共享相同的模型和设备版本字段。                                                                                                                                                 |

其中：<br/>
R = 所需<br/>
I = 如果实现 （可选）<br/>
不适用不适用 =

**支持控制请求**控制请求启用 MTP 启动器向 MTP 响应方发送带的请求。 该设备必须支持下列请求。

-   获取状态
-   取消请求
-   重置设备请求

**必需的操作**这种核心设置的 MTP 操作和设备属性必须满足每个可移植设备与 Windows 兼容的。  媒体传输协议规范，修订版本 1.0 或更高版本中定义了每个操作和设备属性的实现详细信息。 突出显示的操作表示 MTP 操作所需的所有的便携设备的核心集。

|          &nbsp;         | 属性代码 | 移动电话 | 媒体播放机 | 数字照相机 | 数字摄像机 | 其他 （基础货币） |
|-------------------------|---------------|--------------|--------------|----------------|----------------------|--------------|
| GetDeviceInfo           | 0x1001        | R            | R            | R              | R                    | R            |
| OpenSession             | 0x1002        | R            | R            | R              | R                    | R            |
| CloseSession            | 0x1003        | R            | R            | R              | R                    | R            |
| GetStorageIDs           | 0x1004        | R            | R            | R              | R                    | R            |
| GetStorageInfo          | 0x1005        | R            | R            | R              | R                    | R            |
| GetNumObjects           | 0x1006        | R            | R            | R              | R                    | R            |
| GetObjectHandles        | 0x1007        | R            | R            | R              | R                    | R            |
| GetObjectInfo           | 0x1008        | R            | R            | R              | R                    | R            |
| GetObject               | 0x1009        | R            | R            | R              | R                    | R            |
| GetDevicePropDesc       | 0x1014        | R            | R            | R              | R                    | R            |
| GetDevicePropValue      | 0x1015        | R            | R            | R              | R                    | R            |
| DeleteObject            | 0x100B        | R            | R            | I              | I                    | I            |
| SetDevicePropValue      | 0x100A        | R            | R            | I              | I                    | I            |
| SendObjectInfo          | 0x100C        | R            | R            | I              | I                    | I            |
| SendObject              | 0x100D        | R            | R            | I              | I                    | I            |
| GetPartialObject        | 0x101B        | R            | R            | I              | I                    | I            |
| GetObjectPropsSupported | 0x9801        | R            | R            | I              | I                    | I            |
| GetObjectPropDesc       | 0x9802        | R            | R            | I              | I                    | I            |
| GetObjectPropValue      | 0x9803        | R            | R            | I              | I                    | I            |
| SetObjectPropValue      | 0x9804        | R            | R            | I              | I                    | I            |
| GetObjectReferences     | 0x9810        | R            | R            | I              | I                    | I            |
| SetObjectReferences     | 0x9811        | R            | R            | I              | I                    | I            |

**操作**在 MTP 规范中，修订版本 1.0 或更高版本定义的 MTP 操作的完整列表，请参阅。

极力推荐采用下列操作，尽管不需要这么做︰

-   FormatStore (0x100F)
-   GetObjectPropList (0x9805)
-   SetObjectPropList (0x9806)
-   GetInterDependentPropDesc (0x9807)
-   SendObjectPropList (0x9808)-此命令，您的设备还必须支持的目标，这将使 MTP 启动器以指示该对象的父句柄的规范。

**所需的事件**对所有对象必须支持以下事件︰

-   ObjectAdded (0x4002)
-   ObjectRemoved (0x4003)

如果设备支持可移动媒体，它还必须支持以下事件。

-   StoreAdded (0x4004)
-   StoreRemoved (0x4005)

**操作响应**所有的操作必须返回相应的响应。 如果遇到错误，则错误响应代码还定义，并且必须提供的设备。 有关详细信息，请参阅 MTP 技术指标的"响应"一节。

**所需的设备属性**

|        &nbsp;           | 属性代码 | 移动电话 | 媒体播放机 | 数字照相机 | 数字摄像机 | 其他 （基础货币） |
|-------------------------|---------------|--------------|--------------|----------------|----------------------|--------------|
| 电池级别           | 0x5001        | I            | I            | I              | I                    | I            |
| 同步伙伴 | 0xD401        | I            | I            | I              | I                    | I            |
| 设备友好名称    | 0xD402        | R            | R            | I              | I                    | I            |
| 设备图标             | 0xD405        | I            | I            | I              | I                    | I            |

**设备属性**中 MTP 技术指标，修订版本 1.0 或更高版本的已定义设备属性的完整列表，请参阅。

设备图标不是必需的但强烈推荐。 可使用设备的高分辨率图像并在 Windows 用户界面中公开。

**对象的格式**

下表表示的便携设备的*所需*对象格式的列表。 每个对象格式也有必须支持每个对象类型对象属性的列表。 突出显示的对象格式对于所有 MTP 设备是必需的并被认为是为 Windows 核心 MTP 要求。

 

|           &nbsp;                | 属性代码 | 移动电话    | 媒体播放机    | 数字照相机  | 数字摄像机 | 其他 （基础货币）    |
|---------------------------------|---------------|-----------------|-----------------|-----------------|----------------------|-----------------|
| 未定义                       | 0x3000        | I               | I               | I               | I                    | I               |
| 关联                     | 0x3001        | R               | R               | R               | R                    | R               |
| 抽象的音频唱片集            | 0xBA03        | I<sup>(2)</sup> | I<sup>(2)</sup> | N/A             | N/A                  | I<sup>(2)</sup> |
| 抽象的音频和视频播放列表 | 0xBA05        | I               | I               | N/A             | N/A                  | I               |
| WAV                             | 0x3008        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I               |
| MP3                             | 0x3009        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I               |
| AVI                             | 0x300A        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | R<sup>(1)</sup>      | I               |
| MPEG                            | 0x300B        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | R<sup>(1)</sup>      | I               |
| ASF                             | 0x300C        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | R<sup>(1)</sup>      | I               |
| EXIF/JPEG                       | 0x3801        | I               | I               | R<sup>(1)</sup> | I                    | I               |
| TIFF/EP                         | 0x3802        | I               | I               | R<sup>(1)</sup> | I                    | I               |
| BMP                             | 0x3804        | I               | I               | R<sup>(1)</sup> | I                    | I               |
| JPEG XR                         | 0xB804        | I               | I               | R<sup>(1)</sup> | I                    | I               |
| WMA                             | 0xB901        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I               |
| AAC                             | 0xB903        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I               |
| WMV                             | 0xB981        | I               | I               | I               | R<sup>(1)</sup>      | I               |
| MP4 容器                   | 0xB982        | I               | I               | I               | R<sup>(1)</sup>      | I               |
| 3GP 容器                   | 0xB984        | I               | I               | I               | R<sup>(1)</sup>      | I               |
| 3G 2                             | 0xB985        | I               | I               | I               | R<sup>(1)</sup>      | I               |
| AVCHD                           | 0xB986        | I               | I               | I               | R<sup>(1)</sup>      | I               |

（1） 可移植能够播放音频和/或视频的设备必须支持至少其中一种格式。 此表不表示受支持格式; 数据格式的完整列表它表示常用格式列表中。
**设置对象的格式**在 MTP 规范中，修订版本 1.0 或更高版本定义设备属性的完整列表，请参阅。

（2） 支持下列对象属性是必需的 AbstractAudioAlbum 对象︰

-   流派 (0xDC8C)
-   唱片集艺术家 (0xDC9B)
-   WMPMetadataRoundTrip (0x9201)

支持的 AbstractAudioAlbum 格式和图像格式的设备可能会选择支持唱片集画面。 唱片集画面通过将剪贴画添加到相册的 RepresentativeSampleData 属性附加到一个 AbstractAudioAlbum 对象。

如果便携式设备支持唱片集画面，设备必须支持下列对象属性︰

-   PurchaseFlag (0xd901)，在便携式设备 MTP 扩展 Windows 媒体 DRM 10 对象属性
-   RepresentativeSampleFormat (0xdc81)
-   RepresentativeSampleSize (0xdc82)
-   RepresentativeSampleHeight (0xdc83)
-   RepresentativeSampleWidth (0xdc84)
-   RepresentativeSampleData (0xdc86)
-   用户等级 (0xdc8a)
-   WMPMetadataRoundTrip (0x9201)

*设计备注*

-   "对于数字仍摄影设备，图片传输协议 (PTP)"1.0 版的 PIMA15740: 2000年图片传输协议规范。
     
-   *Http://go.microsoft.com/fwlink/?LinkId=243145*提供了媒体传输协议规范，修订版本 1.0。
     
-   其他的实现详细信息可以找到 Windows 7 便携式设备启用工具包中 MTP，该版本可在<http://go.microsoft.com/fwlink/?LinkId=243146>。

### <a name="deviceportablecoremtpfunctionality"></a>Device.Portable.Core.MTPFunctionality

*支持 MTP 设备必须满足必需的一般功能要求，以确保在 Windows 中的预期的行为。*

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

便携设备必须按照下面定义的要求的行为。 该设备必须︰

 
**Persist 所有传输的内容的**该设备必须报告接收它不保留的内容。

**按要求-响应**便携设备必须响应时接收由一台主机发出的 MTP *GetDeviceStatus*控制请求。

**支持意外的设备断开连接的**意外断开连接不会导致停止响应 （挂起或崩溃） 或重新启动该设备。

### <a name="deviceportablecoremtpmultisession"></a>Device.Portable.Core.MTPMultiSession

*启用 MTP 多会话功能的便携设备必须支持会话操作所需的对象。*

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

为了正确地支持 MTP 多会话功能和工作如期与多会话识别启动器，设备必须支持以下会话操作︰

-   CreateSession
-   GetSessionResponderInfo

RestrictSession 操作是可选的。 此操作在 Windows 支持并为响应程序 RestrictSession 数据集内定义的限制。

这些操作都需要除了基本会话操作的 MTP 1.0 规范; 中定义的操作这些操作包括 OpenSession、 CloseSession、 TransactionID、 会话 Id 等。没有需要的最小值或最大设备必须支持多会话的会话数。

*设计备注*

实现详细信息，请参阅媒体传输协议规范修订 2.0 版，网址*http://go.microsoft.com/fwlink/?LinkId=243142。*

### <a name="deviceportablecoremtpobjectproperties"></a>Device.Portable.Core.MTPObjectProperties

*MTP 设备必须支持对象属性为每个可耗用的媒体格式。*

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

必须由设备提供报告每种格式支持以下设备功能。 如果支持 MP4 容器，则设备功能需要在此项中包含正确的属性。 根据此信息，Windows 可以预测正确编码转换个人资料和编码转换文件的设备，可以再播放设备上。

下表总结了所需 (R)，并建议如果实现 (I) / 可选对象属性支持所有对象的格式。 有关完整列表，请参阅对象格式摘要表中 MTP 技术指标，这不是详尽列出所有可用的对象属性。

| 对象属性                     | MTP Datacode | 。              | 说明                                                                                                                                                                              |
|-------------------------------------|--------------|---------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 存储 ID                          | 0xDC01       | R                   | 该对象存储在存储区域。                                                                                                                                           |
| 对象格式                       | 0xDC02       | R                   | 该对象的数据格式。                                                                                                                                                          |
| 保护状态                   | 0xDC03       | R                   | 对象的保护状态。                                                                                                                                                     |
| 对象大小                         | 0xDC04       | R                   | 组件的对象，以字节为单位的大小。                                                                                                                                  |
| 对象文件名称                    | 0xDC07       | R                   | 该对象的文件的名称。                                                                                                                                                             |
| 创建日期                        | 0xDC08       | I**<sup>(1)</sup>** | 此属性包含的日期和时间创建该对象时。                                                                                                                    |
| 修改日期                       | 0xDC09       | I**<sup>(1)</sup>** | 日期和时间对象最后一次更改过。                                                                                                                                      |
| 父对象                       | 0xDC0B       | R                   | 对象的父对象。                                                                                                                                                         |
| 持久的唯一对象标识符 | 0xDC41       | R                   | 对象的持久的唯一对象标识符。                                                                                                                                   |
| 名称                                | 0xDC44       | R                   | 对象的名称。                                                                                                                                                                  |
| 非易耗品                      | 0xDC4F       | R                   | 指示对象是否已传送到便携媒体播放器仅存储并因此，是不能由该便携设备的 （例如，播放）。 |

其中：<br/>
R = 所需<br/>
I = 如果实现 （可选）<br/>
不适用不适用 =

（1） 强烈建议，以使应用程序能够区分哪些对象已被以前导入或同步支持创建日期和修改日期。 这一点对于照片购置方案尤其重要。

 
下表总结了所需，如果实现 （可选） 对象属性支持图像、 音频和视频对象。 这不是无所不包的受支持的对象的所有属性。 有关完整列表，请参阅 MTP 规范中对象属性摘要表。

| 对象属性              | MTP Datacode | Image | 音频               | 视频 |
|------------------------------|--------------|-------|---------------------|-------|
| 艺术家                       | 0xDC46       | N/A   | R                   | I     |
| 说明                  | 0xDC48       | N/A   | I                   | I     |
| 代表样本格式 | 0xDC81       | I     | I                   | I     |
| 代表样本大小   | 0xDC82       | I     | I                   | I     |
| 代表样本高度 | 0xDC83       | I     | I                   | I     |
| 代表样本宽度  | 0xDC84       | I     | I                   | I     |
| 代表示例数据   | 0xDC86       | I     | I                   | I     |
| 宽度                        | 0xDC87       | R     | N/A                 | R     |
| 高度                       | 0xDC88       | R     | N/A                 | R     |
| 持续时间                     | 0xDC89       | N/A   | I                   | I     |
| 用户分级                  | 0xDC8a       | N/A   | I                   | I     |
| 跟踪                        | 0xDC8b       | N/A   | R                   | I     |
| 流派                        | 0xDC8c       | N/A   | I                   | I     |
| 使用计数                    | 0xDC91       | N/A   | I                   | I     |
| 家长分级              | 0xDC94       | N/A   | I                   | I     |
| 原始发行日期        | 0xDC99       | N/A   | I                   | I     |
| 专辑名称                   | 0xDC9A       | N/A   | R                   | N/A   |
| 唱片集艺术家                 | 0xDC9B       | N/A   | R**<sup>(2)</sup>** | N/A   |
| 比特率类型                 | 0xDE92       | N/A   | I                   | I     |
| 采样速率                  | 0xDE93       | N/A   | R                   | R     |
| 通道数           | 0xDE94       | N/A   | R                   | R     |
| 扫描类型                     | 0xDE97       | N/A   | I                   | R     |
| 波形音频编解码器             | 0xDE99       | N/A   | R                   | R     |
| 音频比特率                | 0xDE9A       | N/A   | R                   | R     |
| FourCC 视频编解码器           | 0xDE9B       | N/A   | N/A                 | R     |
| 视频比特率                | 0xDE9C       | N/A   | N/A                 | R     |
| 每秒千位帧  | 0xDE9D       | N/A   | N/A                 | R     |
| 关键帧的距离           | 0xDE9E       | N/A   | N/A                 | I     |
| 加密配置文件             | 0xDEA1       | N/A   | I                   | R     |

（2） 注意唱片集艺术家 (0xDC9B) 才需要整个唱片集，则单独的音频文件仅支持艺术家 (0xDC46) 的需要。

此外，如果设备支持如果实现 （可选） 的对象属性，该设备必须这样做符合 MTP 规范和准则。 测试用于验证如果设备支持的可选功能。

*设计备注*

有关实施的详细信息，请参阅媒体传输协议规范修订版本 1.0，附录 B- *http://go.microsoft.com/fwlink/?LinkId=243143*在可用的对象属性。

### <a name="deviceportablecoremtpstreams"></a>Device.Portable.Core.MTPStreams

*实施 MTP 流的便携设备必须支持流操作所需的对象。*

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

为了正确地支持 MTP 流功能，设备必须支持以下操作︰

| 操作         | 。 | 说明                                                                           |
|-------------------|--------|---------------------------------------------------------------------------------------|
| OpenObjectStream  | R      | 此操作打开某个对象以流的形式。                                           |
| ReadObjectStream  | R      | 此操作从以前打开的对象流中读取的部分数据。      |
| WriteObjectStream | R      | 此操作打开以前的对象流中写入数据的部分。     |
| SeekObjectStream  | R      | 此操作寻求前进的读取或写入流中的下一个数据块。 |
| CloseObjectStream | R      | 此操作将关闭先前打开的对象流并释放已分配  |

其中：<br/>
R = 所需<br/>
I = 如果实现 （可选）<br/>
不适用不适用 =

*设计备注*

-   实现详细信息请参阅媒体传输协议规范修订版本 2.0，网址<http://go.microsoft.com/fwlink/?LinkId=243144>。

### <a name="deviceportablecoretransportbluetooth"></a>Device.Portable.Core.TransportBluetooth

*如果便携式设备利用了 Bluetooth 传输，则设备应支持该传输和相关的测试的最新版本所需的规范︰ Bluetooth （规范版本 2.1 或更高版本）。*

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

使用 Bluetooth 的便携式设备必须使用下列规范︰

-   Bluetooth 核心规范版本 2.1 + EDR （与最新的错误） 或更高版本\[ <https://www.bluetooth.org/Technical/Specifications/adopted.htm>\]
-   通过从 Microsoft Bluetooth 配置文件规范的 MTP \[ *http://msdn.microsoft.com/en-us/windows/hardware/gg463543*\]

*设计备注*

-   必须根据需求定义的 Bluetooth 设备实现连接。

-   Bluetooth 功能的便携设备必须能够与**窗口的 Bluetooth 类驱动程序**（在标准 MTP 对话通过 USB 和 TCP/IP 类似 Bluetooth） 进行通信。 

-   Bluetooth 功能的便携设备必须支持 Bluetooth V2.1 + EDR，以确保 Windows 可以为优化配对体验中利用**安全简单配对 (SSR)** 。

-   Bluetooth 功能的便携设备必须利用 L2CAP 传输 MTP 响应程序服务定义记录所需参数"**GetFormatCapabilities**"来减少格式枚举性能问题。

### <a name="deviceportablecoretransportip"></a>Device.Portable.Core.TransportIP

*如果便携式设备利用了 IP 传输，则设备应支持该传输和相关的测试的最新版本所需的规范︰ IP （以及 MTP 网络关联扩展名规范和相关的 UPnP 规范）。*

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

支持通过 IP 的 MTP Windows 便携设备必须遵守的相机和成像产品关联 (CIPA) PTP 通过互联网协议 (PTP/IP) 规范 （CIPA-005/2005 年），扩展的 PTP 规范使用 TCP/IP 进行 PTP 操作通过无线网络。

 
MTP/IP 设备必须支持以下三种技术，以确保与 PC 兼容︰

1. **UPnP 基本设备**

    MTP/IP 设备必须支持通用即插即用 (Upnp™") 的基本设备以及简单服务发现协议 (SSDP) 发现。 请参阅详细信息的 MTP 网络关联扩展名定义。

2. **通过 IP 的图片传输协议**

    MTP/IP 设备必须遵守的相机和成像产品关联 (CIPA) PTP 通过互联网协议 (PTP/IP) 规范 （CIPA-005/2005 年），扩展的 PTP 规范使用 TCP/IP 进行 PTP 操作通过无线网络。

3. **MTP 网络关联扩展名**

    MTP/IP 设备必须遵守 MTP 技术指标的 Wi-Fi 提供扩展和 MTP 技术指标的 MTP 网络关联扩展。

通过 MTP DeviceInfo 数据集，作为对 MTP GetDeviceInfo 操作的响应返回的 MTPVendorExtensionDesc 字段中包含以下字符串指示此 MTP 扩展的支持。

| 数据集字段          | 数据类型                   |
|------------------------|----------------------------|
| MTPVendorExtensionDesc | "microsoft.com/WPDNA: 1.0" |

 
通过此扩展定义设备属性为零或名义身份验证支持的设备支持网络关联配置。 安全的身份验证不受此扩展;如果需要，可以通过自定义的 MTP 服务实现安全的身份验证。 请参阅详细信息的 MTP 网络关联扩展名定义。

**网络提供的建议**

MTP Wi-Fi 提供扩展 Windows 立即连接将体系结构扩展到 MTP 设备。 此扩展定义新 MTP 对象格式为 WFC （无线配置文件） 的对象。 WFC 对象包含将允许响应方加入无线网络的网络设置。 支持的 WCN 架构一个启动器能够 WFC 对象传输到设备。 WFC 的每个对象表示一个无线网络的设置。 随着时间的推移，响应方可能会收到多个 WFC 对象。 每个对象将被命名为根据网络的 SSID。

在 DeviceInfo 数据集的 MTPVendorExtensionDesc 字段中必须包含下面的数据类型。

| 数据集字段          | 数据类型                    |
|------------------------|-----------------------------|
| MTPVendorExtensionDesc | "microsoft.com/WPDWCN: 1.0" |

 
**通过 IP 的提高性能的建议**为了减轻格式枚举性能问题，MTP/IP 设备应该还支持**GetFormatCapabilities**操作，因为 MTP 设备服务扩展规范中定义。 此操作可提高查询与经典 MTP 存储 （这些格式显示在 DeviceInfo 数据集） 的格式上的受支持的对象属性的设备的性能。 GetFormatCapabilities 是一种批量操作，重复的 GetObjectPropsSupported、 GetObjectPropDesc 和 GetInterdependentPropDesc 的功能。 响应程序应该实现此操作，因为对设备的多个调用替换单一、 效率更高的调用。

*设计备注*

-   请参阅 PTP/IP 规范 （CIPA-005/2005 年）"图片通过 TCP/IP 网络传输协议"。

-   在<http://msdn.microsoft.com/en-us/windows/hardware/gg463545>，MTP 设备服务扩展规范。

-   就可以在<http://msdn.microsoft.com/en-us/windows/hardware/gg463543>MTP 网络关联、 MTP Windows 立即连接，和 MTP Wi-Fi 提供扩展名的文档。

### <a name="deviceportablecoretransportipdlna"></a>Device.Portable.Core.TransportIPDLNA

*作为 DMR 或 DMS 便携设备符合定义的网络媒体设备的需求。*

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

便携设备可以实现一个或多个 DLNA 的设备类别，如︰

-   数字媒体呈现器 (DMR)
-   数字媒体服务器 (DMS)

该设备必须满足的 Windows 硬件认证程序要求的网络媒体设备部分中提出的每一类设备定义的要求。 DLNA 的 MTP 独立管理。

*设计备注*

-   请参阅网络媒体设备节要求的详细信息。 可以在[http://www.dlna.org](http://www.dlna.org/)找到 DLNA 认证的信息。

### <a name="deviceportablecoretransportusb"></a>Device.Portable.Core.TransportUSB

*如果便携式设备利用 USB 传输，则设备应支持该传输和相关的测试的最新版本所需的规范︰ USB （规范 2.0 版或更高版本）。*

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

使用 USB 的便携式设备必须使用以下命令︰

-   USB 核心规范 （与最新的错误） 的 2.0 版或更高版本\[ <http://www.usb.org/developers/docs>\]

-   （使用最新的错误） 的 USB MTP DWG 规范 1.0 或更高版本\[ <http://www.usb.org/developers/devclass_docs>\]

*设计备注*

-   Usb 端口连接的设备都必须支持高速和最快速度。 超级速度是可选的。

-   根据在适当的连接类型部分中要求必须实现连接。

-   没有特定的 Windows 硬件认证要求，在便携式设备上使用的 USB 连接器的类型。

### <a name="deviceportablecorevideocodec"></a>Device.Portable.Core.VideoCodec

*如果便携式设备已捕获的视频内容的能力，它必须做到使用在 Windows 本身支持的格式。*

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

如果便携式设备可以捕获的视频内容，它必须在 Windows 可以以本机方式而无需使用其他编码解码器安装对解码的格式将这样做。

下表表示列表框中格式 Windows 将呈现这不是彻底的受支持的格式。 支持格式的完整列表，请访问︰ <http://go.microsoft.com/fwlink/?LinkID=242995&clcid=0x409>。

**注意**，对于不需要支持所有给定的比特率和采样率下表中的给定格式，但是需要支持的格式，行提供的范围内。

<html>
    <p><strong>MP4 容器内容</strong></p>
    <table>
        <thead>
            <tr class="header">
                <th>&nbsp;</th>
                <th>设置</th>
                <th>要求</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <th rowspan="4">AAC</th>
                <td>编解码器</td>
                <td>
AAC 标准，最小的 AAC 配置文件级别 2 (0x29)<br />
兼容的 0x29，0x2A，0x2B，0x2C，0x2E，0x2F，0x30，0x31，0x32，0x33                </td>
            </tr>
            <tr class="even">
                <td>CBR 的比特率</td>
                <td>96、 128、 160，192 kbps 速率进行传输</td>
            </tr>
            <tr class="odd">
                <td>采样速率</td>
                <td>44.1 或 48 kHz</td>
            </tr>
            <tr class="even">
                <td>频道</td>
                <td>2</td>
            </tr>
            <tr class="odd">
                <th rowspan="5">H.264</th>
                <td>编解码器</td>
                <td>H.264 标准</td>
            </tr>
            <tr class="even">
                <td>编解码器配置文件</td>
                <td>比较基准 3 级</td>
            </tr>
            <tr class="odd">
                <td>分辨率，像素长宽比</td>
                <td>任何 （只要报告）</td>
            </tr>
            <tr class="even">
                <td>帧速率</td>
                <td>任何 （只要报告）</td>
            </tr>
            <tr class="odd">
                <td>平均比特率</td>
                <td>任何 （只要报告）</td>
            </tr>
        </tbody>
    </table>
    <p>
        <br />
        <strong>移动 WMV 视频内容</strong>
    </p>
    <table>
        <thead>
            <tr class="header">
                <th>&nbsp;</th>
                <th>设置</th>
                <th>要求</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <th rowspan="5">WMA 标准</th>
                <td>编解码器</td>
                <td>WMA9 或更高版本</td>
            </tr>
            <tr class="even">
                <td>平均比特率</td>
                <td>从 48 到 96 千比特每秒 (Kbps)</td>
            </tr>
            <tr class="odd">
                <td>最大峰值比特率</td>
                <td>192 kbps 速率进行传输</td>
            </tr>
            <tr class="even">
                <td>采样速率</td>
                <td>44.1 或 48 kHz</td>
            </tr>
            <tr class="odd">
                <td>频道</td>
                <td>2</td>
            </tr>
            <tr class="even">
                <th rowspan="9">WMV</th>
                <td>编解码器</td>
                <td>VC-1</td>
            </tr>
            <tr class="odd">
                <td>编解码器配置文件</td>
                <td>简单</td>
            </tr>
            <tr class="even">
                <td>分辨率，像素长宽比</td>
                <td>
下列选项之一︰                    <ul>
                        <li>176Ã — 144 个像素，1:1</li>
                        <li>220Ã — 176 像素，1:1</li>
                    </ul>
                </td>
            </tr>
            <tr class="odd">
                <td>帧速率</td>
                <td>15 个或 24 帧 / 秒</td>
            </tr>
            <tr class="even">
                <td>平均比特率</td>
                <td>从 96 至 384 kbps 速率进行传输</td>
            </tr>
            <tr class="odd">
                <td>最大峰值比特率</td>
                <td>768 kbps 速率进行传输</td>
            </tr>
            <tr class="even">
                <td>最大缓冲区</td>
                <td>3 秒</td>
            </tr>
            <tr class="odd">
                <td>关键帧的最大距离</td>
                <td>15 秒</td>
            </tr>
            <tr class="even">
                <td>颜色深度</td>
                <td>每像素 16 位</td>
            </tr>
        </tbody>
    </table>
    <p>
        <br />
        <strong>便携式 WMV 视频内容</strong>
    </p>
    <table>
        <thead>
            <tr class="header">
                <th>&nbsp;</th>
                <th>设置</th>
                <th>要求</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <th rowspan="5">WMA 标准</th>
                <td>编解码器</td>
                <td>WMA9 或更高版本</td>
            </tr>
            <tr class="even">
                <td>平均比特率</td>
                <td>从 48 到 128 Kbps</td>
            </tr>
            <tr class="odd">
                <td>最大峰值比特率</td>
                <td>256 kbps 速率进行传输</td>
            </tr>
            <tr class="even">
                <td>采样速率</td>
                <td>44.1 或 48 kHz</td>
            </tr>
            <tr class="odd">
                <td>频道</td>
                <td>2</td>
            </tr>
            <tr class="even">
                <th rowspan="9">WMV</th>
                <td>编解码器</td>
                <td>VC-1</td>
            </tr>
            <tr class="odd">
                <td>编解码器配置文件</td>
                <td>简单</td>
            </tr>
            <tr class="even">
                <td>分辨率，像素长宽比</td>
                <td>
下列选项之一︰                    <ul>
                        <li>320 Ã-240 像素，1:1</li>
                        <li>480 Ã — 270 像素，1:1</li>
                    </ul>
                </td>
            </tr>
            <tr class="odd">
                <td>帧速率</td>
                <td>24、 25 或 29.97 帧 / 秒</td>
            </tr>
            <tr class="even">
                <td>平均比特率</td>
                <td>从 850 Kbps 到 384</td>
            </tr>
            <tr class="odd">
                <td>最大峰值比特率</td>
                <td>1700 kbps 速率进行传输</td>
            </tr>
            <tr class="even">
                <td>最大缓冲区</td>
                <td>3 秒</td>
            </tr>
            <tr class="odd">
                <td>关键帧的最大距离</td>
                <td>15 秒</td>
            </tr>
            <tr class="even">
                <td>颜色深度</td>
                <td>每像素 16 位</td>
            </tr>
        </tbody>
    </table>
    <p>
        <br />
        <strong>标准的 WMV 视频内容</strong>
    </p>
    <table>
        <thead>
            <tr class="header">
                <th>&nbsp;</th>
                <th>设置</th>
                <th>要求</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <th rowspan="5">WMA 标准</th>
                <td>编解码器</td>
                <td>WMA9 或更高版本</td>
            </tr>
            <tr class="even">
                <td>平均比特率</td>
                <td>从 192 Kbps 到 64</td>
            </tr>
            <tr class="odd">
                <td>最大峰值比特率</td>
                <td>360 kbps 速率进行传输</td>
            </tr>
            <tr class="even">
                <td>采样速率</td>
                <td>44.1 或 48 kHz</td>
            </tr>
            <tr class="odd">
                <td>频道</td>
                <td>2</td>
            </tr>
            <tr class="even">
                <th rowspan="9">WMV</th>
                <td>编解码器</td>
                <td>VC-1</td>
            </tr>
            <tr class="odd">
                <td>编解码器配置文件</td>
                <td>主</td>
            </tr>
            <tr class="even">
                <td>分辨率，像素长宽比</td>
                <td>
下列选项之一︰                    <ul>
                        <li>640 Ã-480 像素，1:1</li>
                        <li>720 Ã — 480 像素，10:11</li>
                        <li>720 Ã — 480 像素、 40:33</li>
                    </ul>
                </td>
            </tr>
            <tr class="odd">
                <td>帧速率</td>
                <td>24、 25 或 29.97 帧 / 秒</td>
            </tr>
            <tr class="even">
                <td>平均比特率</td>
                <td>从 1000 到 3000 kbps 速率进行传输</td>
            </tr>
            <tr class="odd">
                <td>最大峰值比特率</td>
                <td>6000 kbps 速率进行传输</td>
            </tr>
            <tr class="even">
                <td>最大缓冲区</td>
                <td>2 秒</td>
            </tr>
            <tr class="odd">
                <td>关键帧的最大距离</td>
                <td>15 秒</td>
            </tr>
            <tr class="even">
                <td>颜色深度</td>
                <td>16 或 24 位 / 像素</td>
            </tr>
        </tbody>
    </table>
    <p>
        <br />
        <strong>高清晰度 WMV 视频内容</strong>
    </p>
    <table>
        <thead>
            <tr class="header">
                <th>&nbsp;</th>
                <th>设置</th>
                <th>最低要求</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <th rowspan="5">WMA 标准</th>
                <td>编解码器</td>
                <td>WMA9 或更高版本</td>
            </tr>
            <tr class="even">
                <td>平均比特率</td>
                <td>从 192 Kbps 到 64</td>
            </tr>
            <tr class="odd">
                <td>最大峰值比特率</td>
                <td>360 kbps 速率进行传输</td>
            </tr>
            <tr class="even">
                <td>采样速率</td>
                <td>44.1 或 48 kHz</td>
            </tr>
            <tr class="odd">
                <td>频道</td>
                <td>2</td>
            </tr>
            <tr class="even">
                <th rowspan="5">WMA 专业</th>
                <td>编解码器</td>
                <td>WMA9 或更高版本</td>
            </tr>
            <tr class="odd">
                <td>平均比特率</td>
                <td>从 320 到 1500 kbps 速率进行传输</td>
            </tr>
            <tr class="even">
                <td>最大峰值比特率</td>
                <td>2500 kbps 速率进行传输</td>
            </tr>
            <tr class="odd">
                <td>采样速率</td>
                <td>44.1、 48 或 96 kHz</td>
            </tr>
            <tr class="even">
                <td>频道</td>
                <td>最多 8 个</td>
            </tr>
            <tr class="odd">
                <th rowspan="9">WMV</th>
                <td>编解码器</td>
                <td>VC-1</td>
            </tr>
            <tr class="even">
                <td>编解码器配置文件</td>
                <td>高级</td>
            </tr>
            <tr class="odd">
                <td>分辨率，像素长宽比</td>
                <td>Ã 1280年-720 像素，1:1</td>
            </tr>
            <tr class="even">
                <td>帧速率</td>
                <td>24、 25 或 29.97 帧 / 秒</td>
            </tr>
            <tr class="odd">
                <td>平均比特率</td>
                <td>从 8000 到 10000 kbps 速率进行传输</td>
            </tr>
            <tr class="even">
                <td>最大峰值比特率</td>
                <td>20000 kbps 速率进行传输</td>
            </tr>
            <tr class="odd">
                <td>最大缓冲区</td>
                <td>2 秒</td>
            </tr>
            <tr class="even">
                <td>关键帧的最大距离</td>
                <td>15 秒</td>
            </tr>
            <tr class="odd">
                <td>颜色深度</td>
                <td>每像素 24 位</td>
            </tr>
        </tbody>
    </table>
</html>


<a name="device.portable.digitalcamera"></a>
## <a name="deviceportabledigitalcamera"></a>Device.Portable.DigitalCamera

*DigitalCamera*

### <a name="deviceportabledigitalcameramtp"></a>Device.Portable.DigitalCamera.MTP

*数字照相机必须支持 MTP 操作和属性定义在媒体传输协议修订版本 1.0 或更高版本，以及每种设备类型的特定对象格式。*

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

媒体传输协议 (MTP) 是图片传输协议 (ISO 15740) 的扩展。  这两个规范包括可选的命令或操作，但其中一些所需的证书。 还有一组核心操作和必须满足的每个设备类别的与 Windows 兼容的设备属性。 MTP 的实现详细信息在媒体传输协议规范，修订版本 1.0 或更高版本中定义，并将用于作为参照所有的便携设备的证书作为 Windows 硬件认证计划的一部分。

**所需的操作**

这种核心设置的 MTP 操作和设备属性必须满足每个可移植设备与 Windows 兼容的。  媒体传输协议规范，修订版本 1.0 或更高版本中定义了每个操作和设备属性的实现详细信息。

|        &nbsp;           | 属性代码 | 移动电话 | 媒体播放机 | 数字照相机 | 数字摄像机 | 其他 （基础货币） |
|-------------------------|---------------|--------------|--------------|----------------|----------------------|--------------|
| GetDeviceInfo           | 0x1001        | R            | R            | R              | R                    | R            |
| OpenSession             | 0x1002        | R            | R            | R              | R                    | R            |
| CloseSession            | 0x1003        | R            | R            | R              | R                    | R            |
| GetStorageIDs           | 0x1004        | R            | R            | R              | R                    | R            |
| GetStorageInfo          | 0x1005        | R            | R            | R              | R                    | R            |
| GetNumObjects           | 0x1006        | R            | R            | R              | R                    | R            |
| GetObjectHandles        | 0x1007        | R            | R            | R              | R                    | R            |
| GetObjectInfo           | 0x1008        | R            | R            | R              | R                    | R            |
| GetObject               | 0x1009        | R            | R            | R              | R                    | R            |
| GetDevicePropDesc       | 0x1014        | R            | R            | R              | R                    | R            |
| GetDevicePropValue      | 0x1015        | R            | R            | R              | R                    | R            |
| DeleteObject            | 0x100B        | R            | R            | I              | I                    | I            |
| SetDevicePropValue      | 0x100A        | R            | R            | I              | I                    | I            |
| SendObjectInfo          | 0x100C        | R            | R            | I              | I                    | I            |
| SendObject              | 0x100D        | R            | R            | I              | I                    | I            |
| GetPartialObject        | 0x101B        | R            | R            | I              | I                    | I            |
| GetObjectPropsSupported | 0x9801        | R            | R            | I              | I                    | I            |
| GetObjectPropDesc       | 0x9802        | R            | R            | I              | I                    | I            |
| GetObjectPropValue      | 0x9803        | R            | R            | I              | I                    | I            |
| SetObjectPropValue      | 0x9804        | R            | R            | I              | I                    | I            |
| GetObjectReferences     | 0x9810        | R            | R            | I              | I                    | I            |
| SetObjectReferences     | 0x9811        | R            | R            | I              | I                    | I            |

 
其中：<br/>
R = 所需<br/>
I = 如果实现 （可选）<br/>
不适用不适用 =<br/>

**操作**在 MTP 规范中，修订版本 1.0 或更高版本定义的 MTP 操作的完整列表，请参阅。

极力推荐采用下列操作，尽管不需要这么做︰

-   FormatStore (0x100F)
-   GetObjectPropList (0x9805)
-   SetObjectPropList (0x9806)
-   GetInterDependentPropDesc (0x9807)
-   SendObjectPropList (0x9808)-此命令，您的设备还必须支持的目标，这将使 MTP 启动器以指示该对象的父句柄的规范。

**所需的事件**

对所有对象必须支持以下事件︰

-   ObjectAdded (0x4002)
-   ObjectRemoved (0x4003)

如果设备支持可移动媒体，它还必须支持以下事件。

-   StoreAdded (0x4004)
-   StoreRemoved (0x4005)

**操作响应**

所有的操作必须返回相应的响应。 如果遇到错误，则错误响应代码还定义，并且必须提供的设备。 有关详细信息，请参阅 MTP 技术指标的"响应"一节。

**所需的设备属性**

|     &nbsp;              | 属性代码 | 移动电话 | 媒体播放机 | 数字照相机 | 数字摄像机 | 其他 （基础货币） |
|-------------------------|---------------|--------------|--------------|----------------|----------------------|--------------|
| 电池级别           | 0x5001        | I            | I            | I              | I                    | I            |
| 同步伙伴 | 0xD401        | I            | I            | I              | I                    | I            |
| 设备友好名称    | 0xD402        | R            | R            | I              | I                    | I            |
| 设备图标             | 0xD405        | I            | I            | I              | I                    | I            |

**设备属性**中 MTP 技术指标，修订版本 1.0 或更高版本的已定义设备属性的完整列表，请参阅。
设备图标不是必需的但强烈推荐。 可使用设备的高分辨率图像并在 Windows 用户界面中公开。

**对象的格式**

下表表示的便携设备的*所需*对象格式的列表。
每个对象格式也有必须支持每个对象类型对象属性的列表。

|          &nbsp;                 | 属性代码 | 移动电话    | 媒体播放机    | 数字照相机  | 数字摄像机 | 其他 （基础货币） |
|---------------------------------|---------------|-----------------|-----------------|-----------------|----------------------|--------------|
| 未定义                       | 0x3000        | I               | I               | I               | I                    | I            |
| 关联                     | 0x3001        | R               | R               | R               | R                    | R            |
| 抽象的音频唱片集            | 0xBA03        | I               | I               | N/A             | N/A                  | I            |
| 抽象的音频和视频播放列表 | 0xBA05        | I               | I               | N/A             | N/A                  | I            |
| WAV                             | 0x3008        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I            |
| MP3                             | 0x3009        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I            |
| AVI                             | 0x300A        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | R<sup>(1)</sup>      | I            |
| MPEG                            | 0x300B        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | R<sup>(1)</sup>      | I            |
| ASF                             | 0x300C        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | R<sup>(1)</sup>      | I            |
| EXIF/JPEG                       | 0x3801        | I               | I               | R<sup>(1)</sup> | I                    | I            |
| TIFF/EP                         | 0x3802        | I               | I               | R<sup>(1)</sup> | I                    | I            |
| BMP                             | 0x3804        | I               | I               | R<sup>(1)</sup> | I                    | I            |
| JPEG XR                         | 0xB804        | I               | I               | R<sup>(1)</sup> | I                    | I            |
| WMA                             | 0xB901        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I            |
| AAC                             | 0xB903        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I            |
| WMV                             | 0xB981        | I               | I               | I               | R<sup>(1)</sup>      | I            |
| MP4 容器                   | 0xB982        | I               | I               | I               | R<sup>(1)</sup>      | I            |
| 3GP 容器                   | 0xB984        | I               | I               | I               | R<sup>(1)</sup>      | I            |
| 3G 2                             | 0xB985        | I               | I               | I               | R<sup>(1)</sup>      | I            |
| AVCHD                           | 0xB986        | I               | I               | I               | R<sup>(1)</sup>      | I            |

（1） 可移植能够播放音频和/或视频的设备必须支持至少其中一种格式。 此表不表示受支持格式; 数据格式的完整列表它表示常用格式列表中。

**设置对象的格式**在 MTP 规范中，修订版本 1.0 或更高版本定义设备属性的完整列表，请参阅。

*设计备注*

-   "对于数字仍摄影设备，图片传输协议 (PTP)"1.0 版的 PIMA15740: 2000年图片传输协议规范。

-   *Http://go.microsoft.com/fwlink/?LinkId=243145*提供了媒体传输协议规范，修订版本 1.0。

-   其他的实现详细信息可以找到 Windows 7 便携式设备启用工具包中 MTP，该版本可在<http://go.microsoft.com/fwlink/?LinkId=243146>。

<a name="device.portable.digitalvideocamera"></a>
## <a name="deviceportabledigitalvideocamera"></a>Device.Portable.DigitalVideoCamera

*DigitalVideoCamera*

### <a name="deviceportabledigitalvideocameramtp"></a>Device.Portable.DigitalVideoCamera.MTP

*数字摄像机必须支持 MTP 操作和属性定义在媒体传输协议修订版本 1.0 或更高版本，以及每种设备类型的特定对象格式。*

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

媒体传输协议 (MTP) 是图片传输协议 (ISO 15740) 的扩展。  这两个规范包括可选的命令或操作，但其中一些所需的证书。 还有一组核心操作和必须满足的每个设备类别的与 Windows 兼容的设备属性。 MTP 的实现详细信息在媒体传输协议规范，修订版本 1.0 或更高版本中定义，并将用于作为参照所有的便携设备的证书作为 Windows 硬件认证计划的一部分。

**所需的操作**

这种核心设置的 MTP 操作和设备属性必须满足每个可移植设备与 Windows 兼容的。  媒体传输协议规范，修订版本 1.0 或更高版本中定义了每个操作和设备属性的实现详细信息。

|       &nbsp;            | 属性代码 | 移动电话 | 媒体播放机 | 数字照相机 | 数字摄像机 | 其他 （基础货币） |
|-------------------------|---------------|--------------|--------------|----------------|----------------------|--------------|
| GetDeviceInfo           | 0x1001        | R            | R            | R              | R                    | R            |
| OpenSession             | 0x1002        | R            | R            | R              | R                    | R            |
| CloseSession            | 0x1003        | R            | R            | R              | R                    | R            |
| GetStorageIDs           | 0x1004        | R            | R            | R              | R                    | R            |
| GetStorageInfo          | 0x1005        | R            | R            | R              | R                    | R            |
| GetNumObjects           | 0x1006        | R            | R            | R              | R                    | R            |
| GetObjectHandles        | 0x1007        | R            | R            | R              | R                    | R            |
| GetObjectInfo           | 0x1008        | R            | R            | R              | R                    | R            |
| GetObject               | 0x1009        | R            | R            | R              | R                    | R            |
| GetDevicePropDesc       | 0x1014        | R            | R            | R              | R                    | R            |
| GetDevicePropValue      | 0x1015        | R            | R            | R              | R                    | R            |
| DeleteObject            | 0x100B        | R            | R            | I              | I                    | I            |
| SetDevicePropValue      | 0x100A        | R            | R            | I              | I                    | I            |
| SendObjectInfo          | 0x100C        | R            | R            | I              | I                    | I            |
| SendObject              | 0x100D        | R            | R            | I              | I                    | I            |
| GetPartialObject        | 0x101B        | R            | R            | I              | I                    | I            |
| GetObjectPropsSupported | 0x9801        | R            | R            | I              | I                    | I            |
| GetObjectPropDesc       | 0x9802        | R            | R            | I              | I                    | I            |
| GetObjectPropValue      | 0x9803        | R            | R            | I              | I                    | I            |
| SetObjectPropValue      | 0x9804        | R            | R            | I              | I                    | I            |
| GetObjectReferences     | 0x9810        | R            | R            | I              | I                    | I            |
| SetObjectReferences     | 0x9811        | R            | R            | I              | I                    | I            |

 
其中︰ < /br/ > R = 必需 < /br/ > 我如果实现 （可选） < /br/ > n/A = = 不适用

**操作**在 MTP 规范中，修订版本 1.0 或更高版本定义的 MTP 操作的完整列表，请参阅。
极力推荐采用下列操作，尽管不需要这么做︰

-   FormatStore (0x100F)
-   GetObjectPropList (0x9805)
-   SetObjectPropList (0x9806)
-   GetInterDependentPropDesc (0x9807)
-   SendObjectPropList (0x9808)-此命令，您的设备还必须支持的目标，这将使 MTP 启动器以指示该对象的父句柄的规范。

**所需的事件**

对所有对象必须支持以下事件︰

-   ObjectAdded (0x4002)
-   ObjectRemoved (0x4003)

如果设备支持可移动媒体，它还必须支持以下事件。

-   StoreAdded (0x4004)
-   StoreRemoved (0x4005)

**操作响应**

所有的操作必须返回相应的响应。 如果遇到错误，则错误响应代码还定义，并且必须提供的设备。 有关详细信息，请参阅 MTP 技术指标的"响应"一节。

**所需的设备属性**

|        &nbsp;           | 属性代码 | 移动电话 | 媒体播放机 | 数字照相机 | 数字摄像机 | 其他 （基础货币） |
|-------------------------|---------------|--------------|--------------|----------------|----------------------|--------------|
| 电池级别           | 0x5001        | I            | I            | I              | I                    | I            |
| 同步伙伴 | 0xD401        | I            | I            | I              | I                    | I            |
| 设备友好名称    | 0xD402        | R            | R            | I              | I                    | I            |
| 设备图标             | 0xD405        | I            | I            | I              | I                    | I            |

**设备属性**中 MTP 技术指标，修订版本 1.0 或更高版本的已定义设备属性的完整列表，请参阅。
设备图标不是必需的但强烈推荐。 可使用设备的高分辨率图像并在 Windows 用户界面中公开。

**对象的格式**

下表表示的便携设备的*所需*对象格式的列表。
每个对象格式也有必须支持每个对象类型对象属性的列表。

|            &nbsp;               | 属性代码 | 移动电话    | 媒体播放机    | 数字照相机  | 数字摄像机 | 其他 （基础货币） |
|---------------------------------|---------------|-----------------|-----------------|-----------------|----------------------|--------------|
| 未定义                       | 0x3000        | I               | I               | I               | I                    | I            |
| 关联                     | 0x3001        | R               | R               | R               | R                    | R            |
| 抽象的音频唱片集            | 0xBA03        | I               | I               | N/A             | N/A                  | I            |
| 抽象的音频和视频播放列表 | 0xBA05        | I               | I               | N/A             | N/A                  | I            |
| WAV                             | 0x3008        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I            |
| MP3                             | 0x3009        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I            |
| AVI                             | 0x300A        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | R<sup>(1)</sup>      | I            |
| MPEG                            | 0x300B        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | R<sup>(1)</sup>      | I            |
| ASF                             | 0x300C        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | R<sup>(1)</sup>      | I            |
| EXIF/JPEG                       | 0x3801        | I               | I               | R<sup>(1)</sup> | I                    | I            |
| TIFF/EP                         | 0x3802        | I               | I               | R<sup>(1)</sup> | I                    | I            |
| BMP                             | 0x3804        | I               | I               | R<sup>(1)</sup> | I                    | I            |
| JPEG XR                         | 0xB804        | I               | I               | R<sup>(1)</sup> | I                    | I            |
| WMA                             | 0xB901        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I            |
| AAC                             | 0xB903        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I            |
| WMV                             | 0xB981        | I               | I               | I               | R<sup>(1)</sup>      | I            |
| MP4 容器                   | 0xB982        | I               | I               | I               | R<sup>(1)</sup>      | I            |
| 3GP 容器                   | 0xB984        | I               | I               | I               | R<sup>(1)</sup>      | I            |
| 3G 2                             | 0xB985        | I               | I               | I               | R<sup>(1)</sup>      | I            |
| AVCHD                           | 0xB986        | I               | I               | I               | R<sup>(1)</sup>      | I            |

（1） 可移植能够播放音频和/或视频的设备必须支持至少其中一种格式。 此表不表示受支持格式; 数据格式的完整列表它表示常用格式列表中。
**设置对象的格式**在 MTP 规范中，修订版本 1.0 或更高版本定义设备属性的完整列表，请参阅。

*设计备注*

-   "对于数字仍摄影设备，图片传输协议 (PTP)"1.0 版的 PIMA15740: 2000年图片传输协议规范。

-   *Http://go.microsoft.com/fwlink/?LinkId=243145*提供了媒体传输协议规范，修订版本 1.0。

-   其他的实现详细信息可以找到 Windows 7 便携式设备启用工具包中 MTP，该版本可在<http://go.microsoft.com/fwlink/?LinkId=243146>。

<a name="device.portable.mediaplayer"></a>
## <a name="deviceportablemediaplayer"></a>Device.Portable.MediaPlayer

*MediaPlayer*

### <a name="deviceportablemediaplayermtp"></a>Device.Portable.MediaPlayer.MTP

*MTP 操作和属性定义在媒体传输协议修订版本 1.0 或更高版本，以及每种设备类型的特定对象格式，必须支持的媒体播放器。*

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

媒体传输协议 (MTP) 是图片传输协议 (ISO 15740) 的扩展。  这两个规范包括可选的命令或操作，但其中一些所需的证书。 还有一组核心操作和必须满足的每个设备类别的与 Windows 兼容的设备属性。 MTP 的实现详细信息在媒体传输协议规范，修订版本 1.0 或更高版本中定义，并将用于作为参照所有的便携设备的证书作为 Windows 硬件认证计划的一部分。

**所需的操作**

这种核心设置的 MTP 操作和设备属性必须满足每个可移植设备与 Windows 兼容的。  媒体传输协议规范，修订版本 1.0 或更高版本中定义了每个操作和设备属性的实现详细信息。

|       &nbsp;            | 属性代码 | 移动电话 | 媒体播放机 | 数字照相机 | 数字摄像机 | 其他 （基础货币） |
|-------------------------|---------------|--------------|--------------|----------------|----------------------|--------------|
| GetDeviceInfo           | 0x1001        | R            | R            | R              | R                    | R            |
| OpenSession             | 0x1002        | R            | R            | R              | R                    | R            |
| CloseSession            | 0x1003        | R            | R            | R              | R                    | R            |
| GetStorageIDs           | 0x1004        | R            | R            | R              | R                    | R            |
| GetStorageInfo          | 0x1005        | R            | R            | R              | R                    | R            |
| GetNumObjects           | 0x1006        | R            | R            | R              | R                    | R            |
| GetObjectHandles        | 0x1007        | R            | R            | R              | R                    | R            |
| GetObjectInfo           | 0x1008        | R            | R            | R              | R                    | R            |
| GetObject               | 0x1009        | R            | R            | R              | R                    | R            |
| GetDevicePropDesc       | 0x1014        | R            | R            | R              | R                    | R            |
| GetDevicePropValue      | 0x1015        | R            | R            | R              | R                    | R            |
| DeleteObject            | 0x100B        | R            | R            | I              | I                    | I            |
| SetDevicePropValue      | 0x100A        | R            | R            | I              | I                    | I            |
| SendObjectInfo          | 0x100C        | R            | R            | I              | I                    | I            |
| SendObject              | 0x100D        | R            | R            | I              | I                    | I            |
| GetPartialObject        | 0x101B        | R            | R            | I              | I                    | I            |
| GetObjectPropsSupported | 0x9801        | R            | R            | I              | I                    | I            |
| GetObjectPropDesc       | 0x9802        | R            | R            | I              | I                    | I            |
| GetObjectPropValue      | 0x9803        | R            | R            | I              | I                    | I            |
| SetObjectPropValue      | 0x9804        | R            | R            | I              | I                    | I            |
| GetObjectReferences     | 0x9810        | R            | R            | I              | I                    | I            |
| SetObjectReferences     | 0x9811        | R            | R            | I              | I                    | I            |

 
其中：<br/>
R = 所需<br/>
I = 如果实现 （可选）<br/>
不适用不适用 =

**操作**在 MTP 规范中，修订版本 1.0 或更高版本定义的 MTP 操作的完整列表，请参阅。
极力推荐采用下列操作，尽管不需要这么做︰

-   FormatStore (0x100F)
-   GetObjectPropList (0x9805)
-   SetObjectPropList (0x9806)
-   GetInterDependentPropDesc (0x9807)
-   SendObjectPropList (0x9808)-此命令，您的设备还必须支持的目标，这将使 MTP 启动器以指示该对象的父句柄的规范。

**所需的事件**

对所有对象必须支持以下事件︰

-   ObjectAdded (0x4002)
-   ObjectRemoved (0x4003)

如果设备支持可移动媒体，它还必须支持以下事件。

-   StoreAdded (0x4004)
-   StoreRemoved (0x4005)

**操作响应**

所有的操作必须返回相应的响应。 如果遇到错误，则错误响应代码还定义，并且必须提供的设备。 有关详细信息，请参阅 MTP 技术指标的"响应"一节。

**所需的设备属性**

|         &nbsp;          | 属性代码 | 移动电话 | 媒体播放机 | 数字照相机 | 数字摄像机 | 其他 （基础货币） |
|-------------------------|---------------|--------------|--------------|----------------|----------------------|--------------|
| 电池级别           | 0x5001        | I            | I            | I              | I                    | I            |
| 同步伙伴 | 0xD401        | I            | I            | I              | I                    | I            |
| 设备友好名称    | 0xD402        | R            | R            | I              | I                    | I            |
| 设备图标             | 0xD405        | I            | I            | I              | I                    | I            |

**设备属性**中 MTP 技术指标，修订版本 1.0 或更高版本定义设备属性的完整列表，请参阅。
设备图标不是必需的但强烈推荐。 可使用设备的高分辨率图像并在 Windows 用户界面中公开。

**对象的格式**

下表表示的便携设备的*所需*对象格式的列表。
每个对象格式也有必须支持每个对象类型对象属性的列表。

|        &nbsp;                   | 属性代码 | 移动电话    | 媒体播放机    | 数字照相机  | 数字摄像机 | 其他 （基础货币）    |
|---------------------------------|---------------|-----------------|-----------------|-----------------|----------------------|-----------------|
| 未定义                       | 0x3000        | I               | I               | I               | I                    | I               |
| 关联                     | 0x3001        | R               | R               | R               | R                    | R               |
| 抽象的音频唱片集            | 0xBA03        | I<sup>(2)</sup> | I<sup>(2)</sup> | N/A             | N/A                  | I<sup>(2)</sup> |
| 抽象的音频和视频播放列表 | 0xBA05        | I               | I               | N/A             | N/A                  | I               |
| WAV                             | 0x3008        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I               |
| MP3                             | 0x3009        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I               |
| AVI                             | 0x300A        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | R<sup>(1)</sup>      | I               |
| MPEG                            | 0x300B        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | R<sup>(1)</sup>      | I               |
| ASF                             | 0x300C        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | R<sup>(1)</sup>      | I               |
| EXIF/JPEG                       | 0x3801        | I               | I               | R<sup>(1)</sup> | I                    | I               |
| TIFF/EP                         | 0x3802        | I               | I               | R<sup>(1)</sup> | I                    | I               |
| BMP                             | 0x3804        | I               | I               | R<sup>(1)</sup> | I                    | I               |
| JPEG XR                         | 0xB804        | I               | I               | R<sup>(1)</sup> | I                    | I               |
| WMA                             | 0xB901        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I               |
| AAC                             | 0xB903        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I               |
| WMV                             | 0xB981        | I               | I               | I               | R<sup>(1)</sup>      | I               |
| MP4 容器                   | 0xB982        | I               | I               | I               | R<sup>(1)</sup>      | I               |
| 3GP 容器                   | 0xB984        | I               | I               | I               | R<sup>(1)</sup>      | I               |
| 3G 2                             | 0xB985        | I               | I               | I               | R<sup>(1)</sup>      | I               |
| AVCHD                           | 0xB986        | I               | I               | I               | R<sup>(1)</sup>      | I               |

（1） 可移植能够播放音频和/或视频的设备必须支持至少其中一种格式。 此表不表示受支持格式; 数据格式的完整列表它表示常用格式列表中。
**设置对象的格式**在 MTP 规范中，修订版本 1.0 或更高版本定义设备属性的完整列表，请参阅。
（2） 支持下列对象属性是必需的 AbstractAudioAlbum 对象︰

-   流派 (0xDC8C)
-   唱片集艺术家 (0xDC9B)
-   WMPMetadataRoundTrip (0x9201)

支持的 AbstractAudioAlbum 格式和图像格式的设备可能会选择支持唱片集画面。 唱片集画面通过将剪贴画添加到相册的 RepresentativeSampleData 属性附加到一个 AbstractAudioAlbum 对象。
如果便携式设备支持唱片集画面，设备必须支持下列对象属性︰

-   PurchaseFlag (0xd901)，在便携式设备 MTP 扩展 Windows 媒体 DRM 10 对象属性
-   RepresentativeSampleFormat (0xdc81)
-   RepresentativeSampleSize (0xdc82)
-   RepresentativeSampleHeight (0xdc83)
-   RepresentativeSampleWidth (0xdc84)
-   RepresentativeSampleData (0xdc86)
-   用户等级 (0xdc8a)
-   WMPMetadataRoundTrip (0x9201)

*设计备注*

-   "对于数字仍摄影设备，图片传输协议 (PTP)"1.0 版的 PIMA15740: 2000年图片传输协议规范。

-   *Http://go.microsoft.com/fwlink/?LinkId=243145*提供了媒体传输协议规范，修订版本 1.0。

-   其他的实现详细信息可以找到 Windows 7 便携式设备启用工具包中 MTP，该版本可在<http://go.microsoft.com/fwlink/?LinkId=243146>。

<a name="device.portable.mobilephone"></a>
## <a name="deviceportablemobilephone"></a>Device.Portable.MobilePhone

*MobilePhone*

### <a name="deviceportablemobilephonemtp"></a>Device.Portable.MobilePhone.MTP

*手机必须支持 MTP 操作和属性定义在媒体传输协议修订版本 1.0 或更高版本，以及每种设备类型的特定对象格式。*

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

媒体传输协议 (MTP) 是图片传输协议 (ISO 15740) 的扩展。  这两个规范包括可选的命令或操作，但其中一些所需的证书。 还有一组核心操作和必须满足的每个设备类别的与 Windows 兼容的设备属性。 MTP 的实现详细信息在媒体传输协议规范，修订版本 1.0 或更高版本中定义，并将用于作为参照所有的便携设备的证书作为 Windows 硬件认证计划的一部分。

**所需的操作**

这种核心设置的 MTP 操作和设备属性必须满足每个可移植设备与 Windows 兼容的。  媒体传输协议规范，修订版本 1.0 或更高版本中定义了每个操作和设备属性的实现详细信息。

|       &nbsp;            | 属性代码 | 移动电话 | 媒体播放机 | 数字照相机 | 数字摄像机 | 其他 （基础货币） |
|-------------------------|---------------|--------------|--------------|----------------|----------------------|--------------|
| GetDeviceInfo           | 0x1001        | R            | R            | R              | R                    | R            |
| OpenSession             | 0x1002        | R            | R            | R              | R                    | R            |
| CloseSession            | 0x1003        | R            | R            | R              | R                    | R            |
| GetStorageIDs           | 0x1004        | R            | R            | R              | R                    | R            |
| GetStorageInfo          | 0x1005        | R            | R            | R              | R                    | R            |
| GetNumObjects           | 0x1006        | R            | R            | R              | R                    | R            |
| GetObjectHandles        | 0x1007        | R            | R            | R              | R                    | R            |
| GetObjectInfo           | 0x1008        | R            | R            | R              | R                    | R            |
| GetObject               | 0x1009        | R            | R            | R              | R                    | R            |
| GetDevicePropDesc       | 0x1014        | R            | R            | R              | R                    | R            |
| GetDevicePropValue      | 0x1015        | R            | R            | R              | R                    | R            |
| DeleteObject            | 0x100B        | R            | R            | I              | I                    | I            |
| SetDevicePropValue      | 0x100A        | R            | R            | I              | I                    | I            |
| SendObjectInfo          | 0x100C        | R            | R            | I              | I                    | I            |
| SendObject              | 0x100D        | R            | R            | I              | I                    | I            |
| GetPartialObject        | 0x101B        | R            | R            | I              | I                    | I            |
| GetObjectPropsSupported | 0x9801        | R            | R            | I              | I                    | I            |
| GetObjectPropDesc       | 0x9802        | R            | R            | I              | I                    | I            |
| GetObjectPropValue      | 0x9803        | R            | R            | I              | I                    | I            |
| SetObjectPropValue      | 0x9804        | R            | R            | I              | I                    | I            |
| GetObjectReferences     | 0x9810        | R            | R            | I              | I                    | I            |
| SetObjectReferences     | 0x9811        | R            | R            | I              | I                    | I            |

位置︰ R = 所需<br/>
I = 如果实现 （可选）<br/>
不适用不适用 =

**操作**在 MTP 规范中，修订版本 1.0 或更高版本定义的 MTP 操作的完整列表，请参阅。

极力推荐采用下列操作，尽管不需要这么做︰

-   FormatStore (0x100F)
-   GetObjectPropList (0x9805)
-   SetObjectPropList (0x9806)
-   GetInterDependentPropDesc (0x9807)
-   SendObjectPropList (0x9808)-此命令，您的设备还必须支持的目标，这将使 MTP 启动器以指示该对象的父句柄的规范。

**所需的事件**

对所有对象必须支持以下事件︰

-   ObjectAdded (0x4002)
-   ObjectRemoved (0x4003)

如果设备支持可移动媒体，它还必须支持以下事件。

-   StoreAdded (0x4004)
-   StoreRemoved (0x4005)

**操作响应**

所有的操作必须返回相应的响应。 如果遇到错误，则错误响应代码还定义，并且必须提供的设备。 有关详细信息，请参阅 MTP 技术指标的"响应"一节。

**所需的设备属性**

|        &nbsp;           | 属性代码 | 移动电话 | 媒体播放机 | 数字照相机 | 数字摄像机 | 其他 （基础货币） |
|-------------------------|---------------|--------------|--------------|----------------|----------------------|--------------|
| 电池级别           | 0x5001        | I            | I            | I              | I                    | I            |
| 同步伙伴 | 0xD401        | I            | I            | I              | I                    | I            |
| 设备友好名称    | 0xD402        | R            | R            | I              | I                    | I            |
| 设备图标             | 0xD405        | I            | I            | I              | I                    | I            |

**设备属性**中 MTP 技术指标，修订版本 1.0 或更高版本的已定义设备属性的完整列表，请参阅。

设备图标不是必需的但强烈推荐。 可使用设备的高分辨率图像并在 Windows 用户界面中公开。

**对象的格式**

下表表示的便携设备的*所需*对象格式的列表。
每个对象格式也有必须支持每个对象类型对象属性的列表。

|              &nbsp;             | 属性代码 | 移动电话    | 媒体播放机    | 数字照相机  | 数字摄像机 | 其他 （基础货币）    |
|---------------------------------|---------------|-----------------|-----------------|-----------------|----------------------|-----------------|
| 未定义                       | 0x3000        | I               | I               | I               | I                    | I               |
| 抽象的音频唱片集            | 0xBA03        | I<sup>(2)</sup> | I<sup>(2)</sup> | N/A             | N/A                  | I<sup>(2)</sup> |
| 抽象的音频和视频播放列表 | 0xBA05        | I               | I               | N/A             | N/A                  | I               |
| WAV                             | 0x3008        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I               |
| MP3                             | 0x3009        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I               |
| AVI                             | 0x300A        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | R<sup>(1)</sup>      | I               |
| MPEG                            | 0x300B        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | R<sup>(1)</sup>      | I               |
| ASF                             | 0x300C        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | R<sup>(1)</sup>      | I               |
| EXIF/JPEG                       | 0x3801        | I               | I               | R<sup>(1)</sup> | I                    | I               |
| TIFF/EP                         | 0x3802        | I               | I               | R<sup>(1)</sup> | I                    | I               |
| BMP                             | 0x3804        | I               | I               | R<sup>(1)</sup> | I                    | I               |
| JPEG XR                         | 0xB804        | I               | I               | R<sup>(1)</sup> | I                    | I               |
| WMA                             | 0xB901        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I               |
| AAC                             | 0xB903        | R<sup>(1)</sup> | R<sup>(1)</sup> | I               | I                    | I               |
| WMV                             | 0xB981        | I               | I               | I               | R<sup>(1)</sup>      | I               |
| MP4 容器                   | 0xB982        | I               | I               | I               | R<sup>(1)</sup>      | I               |
| 3GP 容器                   | 0xB984        | I               | I               | I               | R<sup>(1)</sup>      | I               |
| 3G 2                             | 0xB985        | I               | I               | I               | R<sup>(1)</sup>      | I               |
| AVCHD                           | 0xB986        | I               | I               | I               | R<sup>(1)</sup>      | I               |

（1） 可移植能够播放音频和/或视频的设备必须支持至少其中一种格式。 此表不表示受支持格式; 数据格式的完整列表它表示常用格式列表中。

**设置对象的格式**在 MTP 规范中，修订版本 1.0 或更高版本定义设备属性的完整列表，请参阅。

（2） 支持下列对象属性是必需的 AbstractAudioAlbum 对象︰

-   流派 (0xDC8C)
-   唱片集艺术家 (0xDC9B)
-   WMPMetadataRoundTrip (0x9201)

支持的 AbstractAudioAlbum 格式和图像格式的设备可能会选择支持唱片集画面。 唱片集画面通过将剪贴画添加到相册的 RepresentativeSampleData 属性附加到一个 AbstractAudioAlbum 对象。
如果便携式设备支持唱片集画面，设备必须支持下列对象属性︰

-   PurchaseFlag (0xd901)，在便携式设备 MTP 扩展 Windows 媒体 DRM 10 对象属性
-   RepresentativeSampleFormat (0xdc81)
-   RepresentativeSampleSize (0xdc82)
-   RepresentativeSampleHeight (0xdc83)
-   RepresentativeSampleWidth (0xdc84)
-   RepresentativeSampleData (0xdc86)
-   用户等级 (0xdc8a)
-   WMPMetadataRoundTrip (0x9201)

*设计备注*

-   "对于数字仍摄影设备，图片传输协议 (PTP)"1.0 版的 PIMA15740: 2000年图片传输协议规范。

-   *Http://go.microsoft.com/fwlink/?LinkId=243145*提供了媒体传输协议规范，修订版本 1.0。

-   其他的实现详细信息可以找到 Windows 7 便携式设备启用工具包中 MTP，该版本可在<http://go.microsoft.com/fwlink/?LinkId=243146>。

