---
title: "本地视频播放"
description: "本地视频播放"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: eaf18658-4d3a-472f-a88d-ce13ec04701b
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 1a31ce50dfcd0e64800d9424723a57ce0ddcd6ae
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="local-video-playback"></a>本地视频播放


作为电池运行下作业的一部分，本地视频播放评估全屏显示本地视频播放期间测量的计算机电池的使用率。

当播放全屏显示本地视频、 设备和提供能源的一小部分的视频播放现在使用不必要的软件，允许更大的电池寿命。

有关结果和这一评估所产生的问题的详细信息，请参阅[本地视频播放评估的结果](results-for-the-local-video-playback-assessment.md)。

## <a name="a-href-idbeforeyoubeginabefore-you-begin"></a><a href="" id="beforeyoubegin"></a>开始之前


Windows 8.1 中的第一次运行帮助提示可以对评估结果产生负面影响。 若要禁用这些，从提升的命令提示符下，运行下面的命令并重新启动计算机︰`reg.exe add "HKLM\Software\Policies\Microsoft\Windows\EdgeUI" /v DisableHelpSticker /t REG_DWORD /d "1" /f`

当运行 Windows 8.1 此评估，确保评估预期的电池寿命时，**收集分析跟踪**设置处于未选中状态。 当选中时，此选项会产生不正确的估计。

仅当您需要调查其他与能源有关的问题的其他信息，请启用分析跟踪集合。

如果已从 Windows 8 升级到 Windows 8.1 的 PC 上运行本地视频播放时，将提示您选择用于播放 MP4 文件的默认程序。 这只会影响 PC 已升级，并通过全新 Windows 8.1 安装不会影响个人电脑。 若要运行评估，选择默认视频播放器时提示您。 或者，您可以更改使用控制面板中打开 MP4 文件的默认程序。

1.  从**搜索超级按钮**，键入**更改文件类型与文件扩展名相关联**。

2.  打开**控制面板**。

3.  选择.mp4 扩展名，然后单击**更改程序**。

4.  选择要用于播放 MP4 文件的默认程序。

### <a name="requirements"></a>要求

-   计算机必须具有默认的媒体播放器设置能够播放 MP4 编码的内容。

-   计算机必须能够播放 1080p 视频。

-   必须在直流 （电池） 电源运行计算机。 能源效率作业设计为仅在移动设备上运行。 如果未检测到电池时，将收到错误信息。

### <a name="recommendations"></a>建议

在开始之前，要创建最现实的方案尽可能降低风险的结果中生成警告的计算机上配置设置。 下列准则被建议的设置。 他们并不需要的作业运行，但如果计算机配置不正确，结果可能会受到不良影响。

-   请确保您的计算机在飞机模式下运行。

-   退出所有不必要运行应用程序。

-   将屏幕亮度设置为至少 75%（200 尼特）。

-   安装并启用防病毒软件。 如果防病毒软件不是启用并运行，结果可能无法反映实际情况。

    在控制面板中，打开**操作中心**，选择**安全**，检查**病毒防护****在**。 如果没有，则选择**更改操作中心设置**，然后选择**病毒防护**复选框。

-   请确保电源策略被设置为**平衡**。 默认情况下，任何其他电源策略生成一条警告，可能会影响结果。

    在控制面板中，打开**电源选项**中，，然后选择**平衡**。

-   请确保该计算机已配置，以便当计算机从一个屏幕保护程序，不需要密码。

-   请确保所有设备驱动程序都安装正确。 如果您的计算机已丢失或不正确的驱动程序，结果可能会有显著变化。 [驱动程序验证](driver-verification.md)评估可用于标识您要评估的计算机上的驱动程序问题。

-   为获得最佳效果，建议作为一揽子作业运行该作业。 有关如何创建和运行一个已打包的作业信息，请参阅[打包作业和运行它在另一台计算机上](package-a-job-and-run-it-on-another-computer.md)。

### <a name="system-requirements"></a>系统要求

您可以在以下操作系统上运行此评估︰

-   Windows 8.1

-   Windows RT 8.1

-   Windows 10

支持的体系结构包括基于 x86 和基于 x64 的基于 ARM 的系统。

您可以下列方式中的任一 Windows RT 8.1 系统上运行此评估︰

-   打包在 Windows 评估控制台中，该评估作业并运行在 Windows RT 8.1。 有关此选项的详细信息，请参阅[打包作业和运行它在另一台计算机上](package-a-job-and-run-it-on-another-computer.md)。

-   使用 Windows 评估服务。 有关详细信息，请参阅[Windows 评估服务](windows-assessment-services-technical-reference.md)。

 

 






