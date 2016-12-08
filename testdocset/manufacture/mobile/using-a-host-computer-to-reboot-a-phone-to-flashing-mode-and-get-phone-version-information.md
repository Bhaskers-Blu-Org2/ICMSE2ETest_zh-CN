---
author: kpacquer
Description: "使用一台主机重新启动设备，对闪烁模式并获得版本信息"
ms.assetid: 19499cb0-b45d-4971-9934-778f17a87e52
MSHAttr: PreferredLib:/library/windows/hardware
title: "使用一台主机重新启动设备，对闪烁模式并获得版本信息"
ms.openlocfilehash: fdaf844d037f01842137db1276f5aa95bbb0e374
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="using-a-host-pc-to-reboot-a-device-to-flashing-mode-and-get-version-information"></a>使用一台主机重新启动设备，对闪烁模式并获得版本信息


当 Windows 10 移动设备连接到一台主机通过 USB 数据线时，您可以在宿主 PC 运行的应用程序中执行以下任务。 这些任务是非常有用的某些制造或客户服务。

-   到闪烁模式下重新启动设备。

-   从设备中检索版本信息。

宿主应用程序使用 Windows 便携设备 API 来完成这些任务。

## <a name="span-idunderstandingthewindowsportabledevicesapispanspan-idunderstandingthewindowsportabledevicesapispanspan-idunderstandingthewindowsportabledevicesapispanunderstanding-the-windows-portable-devices-api"></a><span id="Understanding_the_Windows_Portable_Devices_API"></span><span id="understanding_the_windows_portable_devices_api"></span><span id="UNDERSTANDING_THE_WINDOWS_PORTABLE_DEVICES_API"></span>了解 Windows 便携设备 API


Windows 便携设备 (WPD) API 是基于 COM 的 API，使计算机与附加设备进行通讯。 要了解更多有关此 API，请参阅以下资源︰

-   [Windows 便携设备](http://msdn.microsoft.com/library/windows/desktop/dd388998.aspx)︰ 本节的 MSDN library 提供体系结构指南和参考文档，Windows 便携设备 api。

-   [便携设备 COM API 示例](http://code.msdn.microsoft.com/windowsdesktop/Portable-Devices-COM-API-fd4a5f7d)︰ 此示例演示如何使用 Windows 便携设备 API 来执行各种任务，包括在枚举连接的设备，在阅读内容上已连接的设备的属性和 MTP 命令发送到设备。

-   [便携设备服务 COM API 示例](http://code.msdn.microsoft.com/windowsdesktop/Portable-Devices-COM-API-b1e2db21)︰ 此示例演示如何使用 Windows 便携设备 API 来执行各种操作设备服务，包括枚举服务和服务内容。

## <a name="span-iddiscoveringwindows10mobiledevicesthatareconnectedtothehostcomputerspanspan-iddiscoveringwindows10mobiledevicesthatareconnectedtothehostcomputerspanspan-iddiscoveringwindows10mobiledevicesthatareconnectedtothehostcomputerspandiscovering-windows-10-mobile-devices-that-are-connected-to-the-host-computer"></a><span id="Discovering_Windows_10_Mobile_devices_that_are_connected_to_the_host_computer"></span><span id="discovering_windows_10_mobile_devices_that_are_connected_to_the_host_computer"></span><span id="DISCOVERING_WINDOWS_10_MOBILE_DEVICES_THAT_ARE_CONNECTED_TO_THE_HOST_COMPUTER"></span>发现连接到宿主计算机的 Windows 10 移动设备


主机应用程序可以重启到闪烁模式下的设备或从设备中检索版本信息之前，主机应用程序必须发现与计算机连接的所有设备。

1.  创建一个[IPortableDeviceManager](http://msdn.microsoft.com/library/windows/desktop/dd388688.aspx)对象，并使用[IPortableDeviceManager::GetDevices](http://msdn.microsoft.com/library/windows/desktop/dd388693.aspx)函数来获取连接的所有设备的设备 Id 的集合。

2.  设备 Id，以确定 Windows 10 移动对于哪些连接的设备的集合进行枚举的每个设备 ID 创建一个[IPortableDevice](http://msdn.microsoft.com/library/windows/desktop/dd319361.aspx)对象，然后使用[IPortableDevice::Content](http://msdn.microsoft.com/library/windows/desktop/dd375688.aspx)和[IPortableDeviceContent::Properties](http://msdn.microsoft.com/library/windows/desktop/dd388540.aspx)函数来检索 WPD\_设备\_模型\_唯一\_的设备 ID 设备属性。 如果该设备是 10 Windows Mobile 设备，WPD 值\_设备\_模型\_唯一\_ID 属性是具有以下值的 GUID。

    ``` syntax
    0x59f12ea9, 0x53ce, 0x452d, 0x97, 0x11, 0xca, 0x4e, 0xea, 0xf1, 0x80, 0x89
    ```

### <a name="span-idexamplesandadditionalresourcesspanspan-idexamplesandadditionalresourcesspanspan-idexamplesandadditionalresourcesspanexamples-and-additional-resources"></a><span id="Examples_and_additional_resources"></span><span id="examples_and_additional_resources"></span><span id="EXAMPLES_AND_ADDITIONAL_RESOURCES"></span>示例和其他资源

下面的代码示例在[便携式设备 COM API 示例](http://code.msdn.microsoft.com/windowsdesktop/Portable-Devices-COM-API-fd4a5f7d)演示以下相关的任务︰

-   创建一个[IPortableDeviceManager](http://msdn.microsoft.com/library/windows/desktop/dd388688.aspx)对象︰ 请参阅`ChooseDevice`DeviceEnumeration.cpp 中的函数。

-   获取该设备的所有连接的设备 Id︰ 请参阅`EnumerateAllDevices`DeviceEnumeration.cpp 中的函数。

-   检索设备属性︰ 请参阅`ReadContentProperties`ContentProperties.cpp 中的函数。

关于设备枚举和检索设备属性的详细信息，请参阅下列文章︰

-   [枚举的设备](http://msdn.microsoft.com/library/windows/desktop/dd319331.aspx)

-   [设备属性](http://msdn.microsoft.com/library/windows/desktop/dd319322.aspx)

-   [检索属性的单个对象](http://msdn.microsoft.com/library/windows/desktop/dd375726.aspx)

## <a name="span-idrebootingawindows10mobiledeviceintoflashingmodespanspan-idrebootingawindows10mobiledeviceintoflashingmodespanspan-idrebootingawindows10mobiledeviceintoflashingmodespanrebooting-a-windows-10-mobile-device-into-flashing-mode"></a><span id="Rebooting_a_Windows_10_Mobile_device_into_flashing_mode"></span><span id="rebooting_a_windows_10_mobile_device_into_flashing_mode"></span><span id="REBOOTING_A_WINDOWS_10_MOBILE_DEVICE_INTO_FLASHING_MODE"></span>重新启动 Windows 10 移动设备，到闪烁模式


表示 Windows 10 移动设备的[IPortableDevice](http://msdn.microsoft.com/library/windows/desktop/dd319361.aspx)对象后，可以发送 MTP 命令重新启动到闪烁模式的电话。

1.  创建一个[IPortableDeviceValues](http://msdn.microsoft.com/library/windows/desktop/dd319461.aspx)对象并将其配置为设置 MTP 命令参数︰

    1.  调用[IPortableDeviceValues::SetGuidValue](http://msdn.microsoft.com/library/windows/desktop/dd375671.aspx)。 传递 WPD\_属性\_通用\_命令\_类别的*key*参数和传递 WPD\_命令\_MTP\_分机\_执行\_命令\_不\_数据\_PHASE.fmtid*值*参数。

    2.  调用[IPortableDeviceValues::SetUnsignedIntegerValue](http://msdn.microsoft.com/library/windows/desktop/dd375681.aspx)。 传递 WPD\_属性\_通用\_命令\_ *key*参数和传递 WPD ID\_命令\_MTP\_分机\_执行\_命令\_不\_数据\_PHASE.pid*值*参数。

    3.  再次调用[IPortableDeviceValues::SetUnsignedIntegerValue](http://msdn.microsoft.com/library/windows/desktop/dd375681.aspx) 。 通过 WPD\_属性\_MTP\_分机\_操作\_ *key*参数和*值*参数传递值**0x9401**代码。 此值表示将手机重新启动到闪烁模式的 MTP 命令。

    4.  创建一个[**IPortableDevicePropVariantCollection**](https://msdn.microsoft.com/library/windows/hardware/ff597589)对象。

    5.  调用[**IPortableDeviceValues::SetIPortableDevicePropVariantCollectionValue**](https://msdn.microsoft.com/library/windows/hardware/ff597632)。 通过 WPD\_属性\_MTP\_分机\_操作\_ *pValue*参数对象的*键*参数和传递[**IPortableDevicePropVariantCollection**](https://msdn.microsoft.com/library/windows/hardware/ff597589)参数。

2.  调用[IPortableDevice::SendCommand](http://msdn.microsoft.com/library/windows/desktop/dd375691.aspx)来发送 MTP 命令。 传递给*pParameters*的参数初始化的[IPortableDeviceValues](http://msdn.microsoft.com/library/windows/desktop/dd319461.aspx)对象。 此操作所发送的 MTP 命令重新电话引导进入闪烁模式。

### <a name="span-idexamplesandadditionalresourcesspanspan-idexamplesandadditionalresourcesspanspan-idexamplesandadditionalresourcesspanexamples-and-additional-resources"></a><span id="Examples_and_additional_resources"></span><span id="examples_and_additional_resources"></span><span id="EXAMPLES_AND_ADDITIONAL_RESOURCES"></span>示例和其他资源

下面的代码示例演示如何设置 MTP 命令参数，并发送 MTP 命令︰

-   [发出 GetNumObjects 命令](http://msdn.microsoft.com/library/windows/desktop/ff384842.aspx)︰ 在 MSDN 库中的此主题演示如何发送标准的 GetNumObjects MTP 命令。

-   `SendhintsCommand` ContentEnumeration.cpp 在[便携式设备 COM API 示例](http://code.msdn.microsoft.com/windowsdesktop/Portable-Devices-COM-API-fd4a5f7d)中的函数。

有关发送 MTP 命令使用 Windows 便携设备 API 的详细信息，请参阅[支持 MTP 扩展](http://msdn.microsoft.com/library/windows/desktop/ff384848.aspx)。

## <a name="span-idretrievingversioninformationfromawindows10mobiledevicespanspan-idretrievingversioninformationfromawindows10mobiledevicespanspan-idretrievingversioninformationfromawindows10mobiledevicespanretrieving-version-information-from-a-windows-10-mobile-device"></a><span id="Retrieving_version_information_from_a_Windows_10_Mobile_device"></span><span id="retrieving_version_information_from_a_windows_10_mobile_device"></span><span id="RETRIEVING_VERSION_INFORMATION_FROM_A_WINDOWS_10_MOBILE_DEVICE"></span>从 Windows 10 移动设备中检索版本信息


确定连接到主机计算机的 Windows 10 移动设备的设备 ID 后，您可以使用名为 MtpDuDeviceService 的 Windows 10 特定于移动设备服务从设备中检索版本信息。

**请注意**  
如果使用 PIN 保护设备，如果在输入 PIN 和设备处于解锁状态才可用 MtpDuDeviceService。

 

### <a name="span-idopenthemtpdudeviceservicespanspan-idopenthemtpdudeviceservicespanspan-idopenthemtpdudeviceservicespanopen-the-mtpdudeviceservice"></a><span id="Open_the_MtpDuDeviceService"></span><span id="open_the_mtpdudeviceservice"></span><span id="OPEN_THE_MTPDUDEVICESERVICE"></span>打开 MtpDuDeviceService

首先，枚举设备服务要打开的 MtpDuDeviceService 的一个[IPortableDeviceService](http://msdn.microsoft.com/library/windows/desktop/dd319445.aspx)对象。

1.  获取设备支持的所有设备服务的 Id 的数组。 要做到这一点，现有[IPortableDeviceServiceManager](http://msdn.microsoft.com/library/windows/desktop/dd319402.aspx) [IPortableDeviceManager](http://msdn.microsoft.com/library/windows/desktop/dd388688.aspx)对象强制转换并调用[IPortableDeviceServiceManager::GetDeviceServices](http://msdn.microsoft.com/library/windows/desktop/dd319408.aspx)方法。 将 10 Windows Mobile 设备的设备 ID 传递给*pszPnPDeviceID*的参数和值[GUID\_DEVINTERFACE\_WPD\_服务](http://msdn.microsoft.com/library/windows/desktop/dd319319.aspx)到*guidServiceCategory*参数。 在*pServices*参数中返回的服务 Id 数组。

2.  循环访问的服务 Id 数组，每个服务 id 执行以下任务︰

    1.  创建一个[IPortableDeviceService](http://msdn.microsoft.com/library/windows/desktop/dd319445.aspx)对象并调用[IPortableDeviceService::Open](http://msdn.microsoft.com/library/windows/desktop/dd319453.aspx)函数，以打开服务。 将当前的服务 ID 传递给*pszPnPServiceID*的参数。

    2.  通过调用[IPortableDeviceService::GetServiceObjectID](http://msdn.microsoft.com/library/windows/desktop/dd319449.aspx)函数获取服务对象 ID。 您需要的服务对象 ID 来访问该服务的属性。

    3.  使用[IPortableDeviceService::Content](http://msdn.microsoft.com/library/windows/desktop/dd319445.aspx)和[IPortableDeviceContent::Properties](http://msdn.microsoft.com/library/windows/desktop/dd388540.aspx)函数来检索服务 （ [IPortableDeviceProperties](http://msdn.microsoft.com/library/windows/desktop/dd388696.aspx)对象） 的属性的集合。

    4.  创建一个[IPortableDeviceKeyCollection](http://msdn.microsoft.com/library/windows/desktop/dd388548.aspx)对象并添加 WPD 定义 WPD\_对象\_到此集合的名称属性键。 此属性关键字指示要检索的服务显示名称。

    5.  调用[IPortableDeviceProperties::GetValues](http://msdn.microsoft.com/library/windows/desktop/dd388714.aspx)函数来检索包含属性值的[IPortableDeviceValues](http://msdn.microsoft.com/library/windows/desktop/dd319461.aspx)对象。 将服务对象 ID 传递给*pszObjectID*的参数和*pKeys*参数初始化的[IPortableDeviceKeyCollection](http://msdn.microsoft.com/library/windows/desktop/dd388548.aspx)对象。

    6.  调用[IPortableDeviceValues::GetStringValue](http://msdn.microsoft.com/library/windows/desktop/dd375661.aspx)函数，并传递 WPD 定义 WPD\_对象\_ *key*参数名称属性键。

    7.  [IPortableDeviceValues::GetStringValue](http://msdn.microsoft.com/library/windows/desktop/dd375661.aspx)函数返回的字符串**MtpDuDeviceService**，如果您发现需要从手机中检索版本信息的服务对象。 退出该循环，并前进到下一节。

        如果服务名称不是**MtpDuDeviceService**，调用[IPortableDeviceService::Close](http://msdn.microsoft.com/library/windows/desktop/dd319441.aspx)函数，循环到下一个服务 ID 返回[IPortableDeviceServiceManager::GetDeviceServices](http://msdn.microsoft.com/library/windows/desktop/dd319408.aspx)，并返回到步骤 2。

### <a name="span-idretrieveversioninformationfromthedevicespanspan-idretrieveversioninformationfromthedevicespanspan-idretrieveversioninformationfromthedevicespanretrieve-version-information-from-the-device"></a><span id="Retrieve_version_information_from_the_device"></span><span id="retrieve_version_information_from_the_device"></span><span id="RETRIEVE_VERSION_INFORMATION_FROM_THE_DEVICE"></span>从设备中检索版本信息

MtpDuDeviceService 为打开一个[IPortableDeviceService](http://msdn.microsoft.com/library/windows/desktop/dd319445.aspx)对象后，您可以使用此对象来从设备中检索版本信息

1.  使用[IPortableDeviceService::Content](http://msdn.microsoft.com/library/windows/desktop/dd319445.aspx)和[IPortableDeviceContent::Properties](http://msdn.microsoft.com/library/windows/desktop/dd388540.aspx)函数来检索服务 （ [IPortableDeviceProperties](http://msdn.microsoft.com/library/windows/desktop/dd388696.aspx)对象） 的属性的集合。

2.  创建一个[IPortableDeviceKeyCollection](http://msdn.microsoft.com/library/windows/desktop/dd388548.aspx)对象，并将[PROPERTYKEY](http://msdn.microsoft.com/library/windows/desktop/bb773381.aspx)值添加到此集合，它指定要从设备中检索版本的数据。 [PROPERTYKEY](http://msdn.microsoft.com/library/windows/desktop/bb773381.aspx)值必须具有以下结构︰

    -   *Fmtid*字段必须具有下面的 GUID 值︰

        ``` syntax
        0x9BFC64C1, 0x19C9, 0x4F3D, 0xA1, 0x4D,  0xC8,  0xDB,  0xE0,  0x47,  0x5D,  0x13
        ```

    -   *Pid*字段必须具有下表中所示的值之一

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left">要检索的设备数据</th>
    <th align="left">pid 值</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><p>在设备上的图像生成字符串</p></td>
    <td align="left"><p>使用以下的 pid 值返回的数据构造生成字符串︰</p>
    <ul>
    <li><p>4 （从生成内部 Microsoft 分支操作系统的名称）</p></li>
    <li><p>6 （Windows 内部版本号）</p></li>
    <li><p>7 （Windows 10 移动内部版本号）</p></li>
    <li><p>8 （生成的时间戳）</p></li>
    </ul>
    <p>生成字符串的示例为 WPMAIN.9600.12186.20130906 1624。</p></td>
    </tr>
    <tr class="even">
    <td align="left"><p>操作系统版本</p></td>
    <td align="left"><p>12</p></td>
    </tr>
    <tr class="odd">
    <td align="left"><p>OEM 设备名称</p></td>
    <td align="left"><p>15</p></td>
    </tr>
    <tr class="even">
    <td align="left"><p>固件版本</p></td>
    <td align="left"><p>16</p></td>
    </tr>
    <tr class="odd">
    <td align="left"><p>SoC 版本</p></td>
    <td align="left"><p>17</p></td>
    </tr>
    <tr class="even">
    <td align="left"><p>无线软件版本</p></td>
    <td align="left"><p>18</p></td>
    </tr>
    <tr class="odd">
    <td align="left"><p>无线电的硬件版本</p></td>
    <td align="left"><p>19</p></td>
    </tr>
    <tr class="even">
    <td align="left"><p>引导加载程序版本</p></td>
    <td align="left"><p>20</p></td>
    </tr>
    <tr class="odd">
    <td align="left"><p>（从 SMBIOS) 平台 ID。</p></td>
    <td align="left"><p>29</p></td>
    </tr>
    </tbody>
    </table>

     

3.  调用[IPortableDeviceProperties::GetValues](http://msdn.microsoft.com/library/windows/desktop/dd388714.aspx)函数来检索包含请求的版本信息的[IPortableDeviceValues](http://msdn.microsoft.com/library/windows/desktop/dd319461.aspx)对象。 将服务对象 ID 传递给*pszObjectID*的参数和*pKeys*参数初始化的[IPortableDeviceKeyCollection](http://msdn.microsoft.com/library/windows/desktop/dd388548.aspx)对象。

4.  调用[IPortableDeviceValues::GetStringValue](http://msdn.microsoft.com/library/windows/desktop/dd375661.aspx)函数。 *Key*参数，通过先前使用的[PROPERTYKEY](http://msdn.microsoft.com/library/windows/desktop/bb773381.aspx)值相同。 此函数在*pValue*参数中返回所请求的版本信息。

### <a name="span-idexamplesandadditionalresourcesspanspan-idexamplesandadditionalresourcesspanspan-idexamplesandadditionalresourcesspanexamples-and-additional-resources"></a><span id="Examples_and_additional_resources"></span><span id="examples_and_additional_resources"></span><span id="EXAMPLES_AND_ADDITIONAL_RESOURCES"></span>示例和其他资源

下面的代码示例在[便携式设备服务 COM API 示例](http://code.msdn.microsoft.com/windowsdesktop/Portable-Devices-COM-API-b1e2db21)演示以下相关的任务︰

-   枚举设备服务︰ 请参阅`EnumerateContactsServices`ServiceEnumeration.cpp 中的函数。

-   正在读取服务属性︰ 请参阅`ReadContentProperties`ContentProperties.cpp 中的函数。

有关如何使用设备服务的详细信息，请参阅[打开服务](http://msdn.microsoft.com/library/windows/desktop/dd375706.aspx)、[访问服务对象属性](http://msdn.microsoft.com/library/windows/desktop/dd743198.aspx)和[检索对象属性](http://msdn.microsoft.com/library/windows/desktop/dd375722.aspx)。

 

 





