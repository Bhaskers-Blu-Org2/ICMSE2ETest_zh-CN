---
title: "10 Windows Mobile 上查找 ETW 提供程序"
description: "这里我们给出如何在 Windows 10 移动设备上查找 ETW 提供程序的示例。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 918791F9-B627-4AA6-A6FC-39A0B376834B
ms.openlocfilehash: acc881246fca4566b4dee95a586de66f5ec371c4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="find-etw-providers-on-windows-10-mobile"></a>10 Windows Mobile 上查找 ETW 提供程序


这里我们给出如何在 Windows 10 移动设备上查找 ETW 提供程序的示例。 此步骤可仅为工程师。

## <a name="field-medic-appx"></a>字段 Medic Appx


找到与 MobileOS 软件包 FieldMedic.appx。

将 FieldMedic.appx 的名称更改为 FieldMedic.zip。

打开 FieldMedic.zip，然后再打开的 ProfileXMLs 文件夹。

在 ProfileXMLs 文件夹中，打开任何配置文件 XML 文件，以查看属于配置文件的 ETW 提供程序的 Guid。 例如，打开 FieldMedic Performance.xml。

``` syntax
<EventProvider Name="A6BF0DEB-3659-40ad-9F81-E25AF62CE3C7" …/>
<EventProvider Name="331C3B3A-2005-44C2-AC5E-77220C37D6B4" …/>
<EventProvider Name="0F67E49F-FE51-4E9F-B490-6F2948CC6027" …/>
<EventProvider Name="C514638F-7723-485B-BCFC-96565D735D4A" …/>
<EventProvider Name="5412704E-B2E1-4624-8FFD-55777B8F7373" …/>
<EventProvider Name="59819D0A-ADAF-46B2-8D7C-990BC39C7C15" …/>
<EventProvider Name="5C103042-7E75-4629-A748-BDFA67607FAC" …/>
```

## <a name="manifest-files-in-the-windows-driver-kit"></a>Windows 驱动程序工具包中的清单文件


Windows 驱动程序工具包中找到清单文件夹。

例如︰ C\\程序文件 (x86)\\窗口工具包\\10\\清单

在清单文件夹中，打开要查看 ETW 提供程序名称和 GUID 的任何清单 (.mc) 文件。 例如，打开 microsoft 的 windowsphone-mtp.mc。

``` syntax
<provider name="Microsoft-WindowsPhone-Mtp"
          guid="{13D97131-EE68-43F4-A1D0-9E762D2A4729}"
```

## <a name="xperf"></a>XPerf


建立在计算机和设备之间的 TShell 连接。

在计算机上，在 TShell，输入以下命令︰

``` syntax
exec-device xperf –providers I
```

输出内容类似于这样︰

``` syntax
…
0063715b-eeda-4007-9429-ad526f62696e             : Microsoft-Windows-Services
00a083e0-1eda-4c82-9a16-e62b1bbc0659             : Microsoft-WindowsPhone-WboExt
02292a7f-12e0-4de6-8fb0-cb93cc1126d3             : Microsoft-WindowsPhone-MMResourceRegistrar
048970b2-e55c-4d10-bbc8-2ee964b745a4             : Microsoft-WindowsMobile-SyncMLDPU-Provider
04a490d4-84c6-4920-9c22-51c80825ff2c             : Microsoft-WindowsPhone-Comms-PhoneUtil
…
```

## <a name="reg-device"></a>注册设备


在 TShell，输入以下命令︰

``` syntax
reg-device query HKLM\Software\Microsoft\Windows\CurrentVersion\WINEVT\Publishers /s > publishers.txt
```

输出内容类似于这样︰

``` syntax
HKEY_LOCAL_MACHINE\...\Publishers\{0063715B-EEDA-4007-9429-AD526F62696E}
    (Default)    REG_SZ    Microsoft-Windows-Services
    Enabled    REG_DWORD    0x1
    MessageFileName    REG_SZ    C:\windows\System32\services.exe
    ResourceFileName    REG_SZ    C:\windows\System32\services.exe

HKEY_LOCAL_MACHINE\...\Publishers\{00A083E0-1EDA-4c82-9A16-E62B1BBC0659}
    (Default)    REG_SZ    Microsoft-WindowsPhone-WboExt
    Enabled    REG_DWORD    0x1
    MessageFileName    REG_SZ    C:\windows\System32\WboExt.dll
    ResourceFileName    REG_SZ    C:\windows\System32\WboExt.dll
…
```

## <a name="tracelog"></a>Tracelog


在 TShell，输入以下命令︰

对于生产的图像，您可能感兴趣的 WinPhoneCritical 和 WinPhoneCircular 的会话。

``` syntax
 Copy imageCopy code  
exec-device tracelog –q WinPhoneCritical -lp
exec-device tracelog –q WinPhoneCircular -lp
```

输出内容类似于这样︰

``` syntax
Logger Name:            WinPhoneCritical
…
Log Mode:               AddToTriageDump  Buffering-only
…
Log Filename:

Enabled Providers:
## Guid                                  Level  Flags

531ab09a-fd58-4d14-bace-bdd7f8e910eb      2  0xffffffffffffffff
ebfe7216-281a-4601-875f-17d1cabed9e0      2  0x00000007
08dde8cc-029f-4e95-9d84-259ccf3a6808      2  0x00000007
…
21f1f21b-c2f6-47d0-bafc-5b75a86f5343      2  0x00000001
Total of 154 providers
```

 

 






