---
title: Device.Imaging.Scanner
Description: "要求。"
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 3555fdac0870f223e9a73cf044c7cffd24b4e334
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="deviceimagingscanner"></a>Device.Imaging.Scanner

 - [Device.Imaging.Scanner.Base](#device.imaging.scanner.base)
 - [Device.Imaging.Scanner.WSD](#device.imaging.scanner.wsd)

<a name="device.imaging.scanner.base"></a>
## <a name="deviceimagingscannerbase"></a>Device.Imaging.Scanner.Base

### <a name="deviceimagingscannerbasedatatransfer"></a>Device.Imaging.Scanner.Base.dataTransfer

*WIA 驱动程序必须支持特定数据传输的实现。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

Windows 图像采集 (WIA) 驱动程序必须执行以下操作︰

-   在下载过程中使用只有**编写**、**搜寻**，以及**SetSizeIStream**方法。

-   在上载过程中使用只**读取**、**查找**和**StatIStream**方法。

-   在对**IWiaMiniDrvTransferCallback::SendMessage**的调用过程中发送有效的**lPercentComplete**值&lt;元素&gt;。  **lPercentComplete**必须是介于 0 和 100 非独占。

-   在对 IWiaMiniDrvTransferCallback::SendMessage 的调用期间发送正确的 ulTransferredBytes 值。

-   将新数据追加到流的末尾， **IWiaMiniDrvTransferCallback::GetNextStream**&lt;元素&gt;接收如果流不为空。

-   成功时返回的值从**Wia MiniDrv::drvAcquireItemData**方法驱动程序调用我**WiaMiniDrv::drvAcquireItemData**在所有支持的格式中使用正确的参数。

-   其**IWiaMiniDrv::drvAcquireItemData**方法返回或调用**IWiaMiniDrvTransferCallback::GetNextStream**之前释放其对应用程序的**IStream**对象的引用。

-   发送一个流在下载过程中包含多页文件，通过使用所有支持 TYMED\_多页\_文件格式。

-   发送一个流，为通过使用所有下载期间的每一项支持的 TYMED\_文件格式。

-   返回 S\_IWiaMiniDrv::drvAcquireItemData IWiaMiniDrvTransferCallback::SendMessage 返回如果从假 S\_FALSE。

-   继续在多项下载过程传输任何后续项目， **IWiaMiniDrvTransferCallback::GetNextStream**返回 WIA 后\_状态\_跳过\_项。

-   返回 S\_ **IWiaMiniDrv::drvAcquireItemData** **IWiaMiniDrvTransferCallback::GetNextStream**返回 WIA 后单项和多项下载期间从确定\_状态\_跳过\_项目的任何项目。

-   **IWiaMiniDrvTransferCallback::GetNextStream**返回 S 后中止转移所有物料的\_FALSE。

-   返回从**IWiaMiniDrv::drvAcquireItemData**调用已取消在传输期间更少的时间比在过程中已完成转移。

-   如果 IWiaMiniDrvTransferCallback::GetNextStream 出现故障，请从 IWiaMiniDrv::drvAcquireItemData 返回失败代码。

-   如果**IWiaMiniDrvTransferCallback::GetNextStream**返回空流指针，请从**IWiaMiniDrv::drvAcquireItemData**返回标准 COM 错误代码。

-   如果 IWiaMiniDrvTransferCallback::SendMessage 出现故障，请从 IWiaMiniDrv::drvAcquireItemData 返回失败代码。

-   在安装了相同的设备以及相同设备将同时转移项目时，成功将物料转移。

-   如果**IStream**方法失败，请从**IWiaMiniDrv::drvAcquireItemData**返回失败代码。

-   寻找到正确的流位置后驱动程序开始传输或调用**IWiaMiniDrvTransferCallback::GetNextStream**或**IWiaMiniDrvTransferCallback::SendMessage**。

-   如果 WIA 服务传输期间终止，然后再重新启动，并请求新的传输，正常工作。

-   忽略对**drvNotifyPnPEvent**的调用&lt;元素&gt;包含 WIA\_事件\_取消\_IO 没有发生转移，如果没有崩溃或挂起。

-   成功地将邮件传送后有效 WIA\_国际音标\_TYMED 属性值写入使用有符号或无符号的变量类型。

WIA 驱动程序必须执行以下操作︰

-   在应用程序的传输回调返回 S 调用应用程序的**IStream**对象以外的**IUnknown::Release**方法\_假，WIA\_状态\_跳过\_项或有一个错误。

-   在多项传输过程调用应用程序的**IStream**对象而不是驱动程序的**IWiaMiniDrv::drvAcquireItemData**方法返回后的**IUnknown::Release**方法或调用**IWiaMiniDrvTransferCallback::GetNextStream**的方法。

-   通过使用 WIA 调用**IWiaMiniDrvTransferCallback::SendMessage** \_传输\_消息\_结束\_的\_流和 WIA\_传输\_消息\_结束\_的\_传输消息。

-   IWiaMiniDrvTransferCallback::SendMessage 返回 S 后再调用 IWiaMiniDrvTransferCallback::SendMessage 或 IWiaMiniDrvTransferCallback::GetNextStream\_虚假或错误。

-   系统崩溃或挂起，如果设备使用无效或为空流请求上载。

 

### <a name="deviceimagingscannerbasewia20"></a>Device.Imaging.Scanner.Base.wia20

*扫描仪和扫描功能的多功能打印机必须实现根据 Windows 驱动程序工具包准则的 WIA 2.0 驱动程序体系结构。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

扫描仪和扫描功能的多功能打印机必须在 Windows 驱动程序工具包实现根据准则的 WIA 2.0 驱动程序体系结构。
扫描仪支持基于流的图像传输。 基于流的传输，WIA 应用程序提供使用，然后驱动程序流读取或写入到流。 文件流、 内存流或任何其他类型的流，该流可能会。 该流是透明的驱动程序。 使用流与图像处理筛选器还提供方便的集成。 这有助于防止出现 （内存或文件） 的目标类型的复杂性。
扫描仪必须正确实施的 Windows WIA 扫描仪项体系结构平板、 ADF，和胶片扫描仪和扫描程序具有存储。 Windows 驱动程序工具包参考文档和工具概述了 WIA 扫描仪项体系结构。 设备制造商必须实现 WIA 支持 Windows 驱动程序工具包中所述。

*设计备注*

WIA 2.0 使新的基于流的传输模型，包括图像处理筛选器、 分段过滤器和错误处理某些扩展。 WIA 2.0 的更多信息，请参阅"简介 WIA 2.0"at <http://www.microsoft.com/whdc/device/stillimage/WIA20-intro.mspx> *和"*最新信息在 WIA 2.0" 处<http://msdn.microsoft.com/en-us/library/ms630379.aspx>*.*

### <a name="deviceimagingscannerbasewiaproperties"></a>Device.Imaging.Scanner.Base.WIAProperties

*扫描仪必须实现对所有必需的 WIA 属性和属性值的支持。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

Windows 驱动程序工具包 (WDK) 参考文档和工具对于 WIA 概述属性和属性值。 扫描仪必须实现 WIA WDK 中所述。

<a name="device.imaging.scanner.wsd"></a>
## <a name="deviceimagingscannerwsd"></a>Device.Imaging.Scanner.WSD

### <a name="deviceimagingscannerwsdwsscan"></a>Device.Imaging.Scanner.WSD.WSScan

*具有网络连接的扫描仪必须实现 WS 扫描协议。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
</td></tr></table>

**说明**

此要求适用于扫描仪或具有扫描功能，连接到网络，并且设备上有物理扫描按钮的多功能打印机。 这些扫描仪或多功能打印机必须实现以下 WS 扫描协议要求 WS 扫描规范 1.0 版中所述︰

-   所有的事件和操作的规范定义，该设备必须正确实现。

<!-- -->

-   该设备必须支持**ScanAvailableEvent** ，以便用户可以启动从扫描仪扫描，然后推给扫描的应用程序的文档。

<!-- -->

-   该设备必须支持 WS 扫描公开的所有设备功能的 Microsoft WSD 扫描类驱动程序。

-   如果设备具有 ADF 和印版扫描，设备必须支持通过 WS 扫描的那些介质。

有关详细信息，请参阅"实现 Web 服务上的设备的打印和扫描" <http://www.microsoft.com/whdc/connect/rally/wsdspecs.mspx>*.*

