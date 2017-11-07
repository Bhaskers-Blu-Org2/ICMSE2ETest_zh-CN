---
title: "检索零售 ETW 日志"
description: "检索零售 ETW 日志"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: a32d9f2b-1a4a-4d69-aae0-c5e80472a708
ms.openlocfilehash: 6afe072297e0ef5e9d3ec7888c722666b980abd4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="retrieve-retail-etw-logs"></a>检索零售 ETW 日志


您可以通过查看零售日志诊断各种问题。 [捕获窗口 10 移动上的事件跟踪日志](capture-event-trace-logs-on-windows-phone.md)以获取有关处理和查看零售日志的详细信息，请参阅。

## <a name="retrieving-logs-from-a-retail-device"></a>从零售设备检索日志


您需要在大容量存储模式，从工程或零售解锁设备检索日志引导设备。 在大容量存储模式下启动时，宿主 PC 可以为存储设备检测到设备。 若要执行此操作的步骤取决于硅供应商设置。

这是如何从零售设备检索现有 ETW 日志︰

1.  将设备解锁。

2.  在大容量存储模式下启动的设备上按特定的键序列。 通常这是在开机时按住只照相机按钮，或照相机和向下按钮，音量。

3.  大约 5 秒钟后，屏幕将保持空白，然后您将看到新的存储驱动器在 Windows 资源管理器中。 查找 EFIESP 文件夹所在的驱动器。

4.  在 Windows 资源管理器中，从以下两个目录中复制的文件。

    ``` syntax
    <mass storage drive letter>:\Data\SystemData\Telemetry
    <mass storage drive letter>:\Data\SystemData\ETW
    ```

    具体取决于手机上的活动量，记录的 ETL 系统转储在 cab 文件中，和其他日志将在此目录中。

5.  从设备复制日志后，关闭 Windows 资源管理器中，然后再弹出该设备。

## <a name="related-topics"></a>相关的主题


[软件跟踪](index.md)

 

 







