---
author: kpacquer
Description: "支持 Api 的生产测试环境"
ms.assetid: a51f7722-ccca-4571-9f07-3ff512a0ddaa
MSHAttr: PreferredLib:/library/windows/hardware
title: "支持 Api 的生产测试环境"
ms.openlocfilehash: e8ec1abf9e4a027ef4f83a476ea16b292942caf6
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="manufacturing-test-environment-supported-apis"></a>支持 Api 的生产测试环境


生产测试环境 (MTE) 仅用于制造支持 Api 和设计的技术。 本部分介绍在 MTE 支持特定库。

## <a name="span-idmmoslibspanspan-idmmoslibspanmmoslib"></a><span id="mmos.lib"></span><span id="MMOS.LIB"></span>MMO。Lib


MMO。Lib 提供 Windows 8 mincore.lib 镜像接口。 Mincore.lib 有关的一般信息，请参阅[Windows API 集](http://msdn.microsoft.com/library/windows/desktop/Hh802935.aspx)。

安装 %WPDKCONTENTROOT%作为由 Windows 驱动程序工具包 (WDK) MMO 库 (.lib) 文件中定义本机 Api 用于 MTE 主用户模式\\Lib\\文件夹。

## <a name="span-idsupportedapisspanspan-idsupportedapisspanspan-idsupportedapisspansupported-apis"></a><span id="Supported_APIs"></span><span id="supported_apis"></span><span id="SUPPORTED_APIS"></span>受支持的 Api


以下各部分提供的 MMO Api 允许进行测试的功能的预览。 MMO 的附加信息支持的 Api 将在本文档的后面的版本中提供。 API 标题的子文件夹和 Windows SDK 头位于"%programfiles(x86)%\\窗口工具包\\10\\包括\\"文件夹。 MMO 的用户模式应用程序中，可以使用这些 Api。 有关创建和运行 MMO 应用程序的详细信息，请参见[开发 MMO 测试应用程序](develop-mmos-test-applications.md)的主题。

### <a name="span-idmicrophoneaudioandaudioroutingspanspan-idmicrophoneaudioandaudioroutingspanspan-idmicrophoneaudioandaudioroutingspanmicrophone-audio-and-audio-routing"></a><span id="Microphone__audio_and_audio_routing"></span><span id="microphone__audio_and_audio_routing"></span><span id="MICROPHONE__AUDIO_AND_AUDIO_ROUTING"></span>麦克风，录音和音频路由

音频和音频路由 Api 允许测试应用程序以测试录音和音频路由功能。 某些情况下该测试可以测试应用程序在每个不同的音频终结点上播放频率。 可以使用音频 Api 测试麦克风。 下面的头文件包含音频和音频路由 Api。

-   Mmo\\audiotunerapi.h

-   Mmo\\audiotunerdef.h

-   Mmo\\audiotunerprop.h

-   Km\\ksmedia\_phone.h

-   Um\\initguid.h

-   Um\\avrt.h (Windows SDK)

-   ctime.h (Windows SDK)

-   Um\\audioclient.h (Windows SDK)

-   Um\\mmdeviceapi.h (Windows SDK)

-   Um\\functiondiscoverykeys.h (Windows SDK)

### <a name="span-iddisplayspanspan-iddisplayspanspan-iddisplayspandisplay"></a><span id="Display"></span><span id="display"></span><span id="DISPLAY"></span>显示

Direct3D 可用于显示信息。 常规信息，请参阅 MSDN 从此[Direct3D 11 图形](http://msdn.microsoft.com/library/windows/desktop/ff476080.aspx)。 下面的头文件包含 D3D Api。

-   Um\\D3DWrapper.h

-   Um\\D3D11.h (Windows SDK)

### <a name="span-idcameraspanspan-idcameraspanspan-idcameraspancamera"></a><span id="Camera"></span><span id="camera"></span><span id="CAMERA"></span>照相机

媒体基础 CaptureEngine Api 可用于使用照相机。 有关如何使用媒体基础的常规信息，请参阅 MSDN 上的[媒体基础编程参考](http://msdn.microsoft.com/library/windows/desktop/ms704847.aspx)。 IMFCaptureEngine 接口的信息，请参阅本 MSDN 主题， [IMFCaptureEngine 接口](http://msdn.microsoft.com/library/windows/desktop/hh447846.aspx)。 下面的头文件包含可用于相机测试的接口。

-   Um\\mfapi.h

-   Um\\mfobjects.h

-   Um\\mfidl.h

-   Um\\mfreadwrite.h

-   Um\\mfcaptureengine.h

-   Um\\wincodec.h

### <a name="span-idsensorsspanspan-idsensorsspanspan-idsensorsspansensors"></a><span id="Sensors"></span><span id="sensors"></span><span id="SENSORS"></span>传感器

有关传感器和测试 MMO 中使用的 Api 的详细信息，请参阅传感器主题。

### <a name="span-idledspanspan-idledspanled"></a><span id="LED"></span><span id="led"></span>指示灯

LED Api 允许测试应用程序通过调用 Ioctl 不同，导致打开、 关闭、 或闪烁的指示灯通知测试通知 LED。 下面的头文件包含 LED Api。

-   Mmo\\hwn.h

### <a name="span-idsdcardspanspan-idsdcardspanspan-idsdcardspansd-card"></a><span id="SD_Card"></span><span id="sd_card"></span><span id="SD_CARD"></span>SD 卡

SD 卡的 Api 允许测试应用程序通过调用不同的 Ioctl 的测试用例，如读取和写入到的卡片测试 SD 卡驱动程序。 下面的头文件包含该 SD 卡的 Api。

-   Um\\sffdisk.h

### <a name="span-idtouchspanspan-idtouchspanspan-idtouchspantouch"></a><span id="Touch"></span><span id="touch"></span><span id="TOUCH"></span>触摸

有关测试触摸控制器的详细信息，请参阅[Access 中 MMO 的触摸界面](access-the-touch-interface-in-mmos.md)主题。 下面的头文件包含触控 Api。

-   Um\\InputDriverRawSamples.h

-   Um\\WinPhoneInput.h

### <a name="span-idvibratorspanspan-idvibratorspanspan-idvibratorspanvibrator"></a><span id="Vibrator"></span><span id="vibrator"></span><span id="VIBRATOR"></span>Vibrator

Vibrator Api 允许测试应用程序通过调用 Ioctl 不同测试设备上的 vibrator。 Ioctl 允许以各种速度和周期的 vibrator 驱动程序在设备上测试应用程序。 下面的头文件包含 vibrator 的 Api。

-   Mmo\\hwn.h

### <a name="span-idhardwarebuttonsspanspan-idhardwarebuttonsspanspan-idhardwarebuttonsspanhardware-buttons"></a><span id="Hardware_buttons"></span><span id="hardware_buttons"></span><span id="HARDWARE_BUTTONS"></span>硬件按钮

有关硬件按钮的详细信息，请参阅硬件按钮主题。 下面的头文件包含硬件按钮的 Api。

-   UM\\ntddkbd.h

### <a name="span-idfmradiospanspan-idfmradiospanspan-idfmradiospanfm-radio"></a><span id="FM_radio"></span><span id="fm_radio"></span><span id="FM_RADIO"></span>调频广播

调频广播的 Api 允许测试通过调用 Ioctl FM 调频收音机调谐器在手机上的测试应用程序。 Ioctl 允许应用程序来测试各种方案，如频率调节，或寻求。 下面的头文件包含调频广播的 Api。

-   Mmo\\audiotunerapi.h

-   Mmo\\audiotunerprop.h

### <a name="span-idwi-fispanspan-idwi-fispanspan-idwi-fispanwi-fi"></a><span id="Wi-Fi"></span><span id="wi-fi"></span><span id="WI-FI"></span>Wi-Fi

有关 Wi-Fi 测试 API，请参阅[Wi-Fi 制造 API](wi-fi-manufacturing-api.md)主题。 下面的头文件包含 Wi-fi Api。

-   Um\\wifimte.h

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[调用 SetScreenOff 输入备用连接](calling-setscreenoff-to-enter-connected-standby.md)

 

 






