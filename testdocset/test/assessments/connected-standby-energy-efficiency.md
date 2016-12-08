---
title: "连接的备用能源效率"
description: "连接的备用能源效率"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 9a23aaaa-922c-410d-a27d-ffd5eb67b546
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 22a5e57c77ada31e7a0172118ef6e0c96c1cf0e4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="connected-standby-energy-efficiency"></a>连接的备用能源效率


作为**电池寿命期间连接待机**作业的一部分，**连接备用能源效率**评估在备用连接时测量的软件和设备系统的电池寿命的影响。 评估还能测量转换传入和传出连接待机状态所花费的时间。

本主题︰

-   [工作负载](#bkmk-photoworkloads)

-   [设置](#settings)

有关结果和这一评估所产生的问题的详细信息，请参阅[连接备用能源效率评估的结果](results-for-the-connected-standby-energy-efficiency-assessment.md)。

## <a name="a-href-idbeforeyoubeginabefore-you-begin"></a><a href="" id="beforeyoubegin"></a>开始之前


Windows 8.1 中的第一次运行帮助提示可以对评估结果产生负面影响。 若要禁用这些，从提升的命令提示符下，运行下面的命令并重新启动计算机︰`reg.exe add "HKLM\Software\Policies\Microsoft\Windows\EdgeUI" /v DisableHelpSticker /t REG_DWORD /d "1" /f`

当运行 Windows 8.1 此评估，确保评估预期的电池寿命时，**收集分析跟踪**设置处于未选中状态。 当选中时，此选项会产生不正确的估计。

仅当您需要调查其他与能源有关的问题的其他信息，请启用分析跟踪集合。

### <a name="requirements"></a>要求

-   系统必须支持连接待机状态。 要确认支持这种睡眠状态，打开一个命令提示符窗口，并运行以下命令︰

    **powercfg /a**

    如果您的系统支持连接待机，**待机 （已连接）**将在列表中可用的休眠状态。

-   确保直流 （电池） 电源运行系统。 能源效率作业设计为仅在移动设备上运行。 如果未检测到电池时，将收到错误信息。

**重要**  
若要在 Windows RT 或 Windows RT 8.1 设备上运行连接备用能源效率评估，必须执行以下操作︰

1.  运行 WAC 计算机中插入 USB 存储设备。 存储设备应有至少 60 MB 的可用空间。

2.  在 WAC，打包评估，并选择 USB 存储设备为目标。 有关详细信息，请参阅[打包作业和运行它在另一台计算机上](package-a-job-and-run-it-on-another-computer.md)。

3.  将 USB 存储设备转移到正在运行 Windows RT 或 Windows RT 8.1 的设备。

4.  将 USB 存储设备中的内容复制到正在运行 Windows RT 或 Windows RT 8.1 的设备上的目标。

5.  在设备上运行 Windows RT 或 Windows RT 8.1，用管理员权限打开命令提示符。

6.  导航到评估程序包的位置。

7.  定位到 Assessment1\\臂目录。

8.  运行 InstallKitsPolicy.cmd。 这将重新启动该设备。

9.  之后重新启动时，向后定位到根的评估包的位置，并运行 RunJob.cmd。

要删除策略，请执行以下操作︰

1.  导航到评估程序包的位置。

2.  定位到 Assessment1\\臂目录。

3.  运行 DeleteKitsPolicy.cmd。 这将重新启动该设备。

 

### <a name="recommendations"></a>建议

在开始之前，以减少在结果中生成警告和电源使用产生负面影响的风险的笔记本电脑上配置设置。 下列准则被建议的设置。 他们并不需要的作业运行，但如果计算机没有正确配置，可能会影响结果。

-   请确保已启用无线功能和计算机已连接到网络。 否则，结果可能无法反映实际情况。

    在控制面板中打开**管理无线网络**。 如果未启用无线功能，将其打开，并连接到无线网络。

    **请注意**  
    如果无线连接已打开，但没有连接到网络，则结果仍受影响。

     

-   安装并启用防病毒软件。 如果防病毒软件不是启用并运行，结果可能无法反映实际情况。

    在控制面板中，打开**操作中心**，选择**安全**，检查**病毒防护****在**。 如果没有，则选择**更改操作中心设置**，然后选择**病毒防护**复选框。

-   请确保电源策略被设置为**平衡**。 默认情况下，任何其他电源策略生成一条警告，可能会影响结果。

    在控制面板中，打开**电源选项**中，，然后选择**平衡**。

-   请确保该计算机已配置，以便当计算机从一个屏幕保护程序，不需要密码。

-   请确保所有设备驱动程序都安装正确。 如果您的计算机已丢失或不正确的驱动程序，结果可能会有显著变化。 [驱动程序验证](driver-verification.md)评估可用于标识您要评估的计算机上的驱动程序问题。

-   为获得最佳效果，建议作为一揽子作业运行该作业。 有关如何创建和运行一个已打包的作业信息，请参阅[打包作业和运行它在另一台计算机上](package-a-job-and-run-it-on-another-computer.md)。

### <a name="system-requirements"></a>系统要求

您可以在以下操作系统上运行此评估︰

-   Windows 8

-   Windows 8.1

-   Windows RT

-   Windows RT 8.1

-   Windows 10

支持的体系结构包括基于 x86 和基于 x64 的基于 ARM 的系统。

## <a name="a-href-idbkmk-photoworkloadsaworkloads"></a><a href="" id="bkmk-photoworkloads"></a>工作负载


工作负荷是一组预定义的、 可重复的方式模拟用户活动的自动化任务。 工作负载运行相互独立。 您可以选择这些工作负荷评估过程中运行的任意组合。 此评估测量持续时间和吞吐量的使用，每个工作负载和存储在结果文件中的指标。

下表描述了可用于此评估的工作负荷。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>工作负荷</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>诊断模式</p></td>
<td><p>使用重量级跟踪，生成附加的跟踪、 测量数据和用于帮助诊断能源效率问题的问题。 如果<strong>生成的诊断信息</strong>选项在<strong>能源效率设置</strong>下，第一次迭代运行诊断模式中。</p></td>
</tr>
<tr class="even">
<td><p>负载模式</p></td>
<td><p>使用轻量的跟踪。 负载模式不会产生任何指标或问题。 如果<strong>能源效率设置</strong>下启用<strong>生成的诊断信息</strong>选项，则第一次迭代在诊断模式下，运行的同时剩余迭代运行工作负载模式。 否则，所有迭代都运行工作负载模式。</p></td>
</tr>
</tbody>
</table>

 

## <a name="settings"></a>Settings


Microsoft 定义建议的设置，以便跨多个计算机配置或一段时间，在同一台计算机上，您可以比较结果。 当您查看结果时，请运行的信息包括指示评估是否使用推荐的设置的元数据。 如果需要，您可以更改这些设置。

下表描述了连接备用能源效率评估设置。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>设置</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>使用建议的设置</p></td>
<td><p>指定评估是否使用推荐的设置。 默认情况下，选中此复选框。 若要更改此评估服务的设置，必须首先清除此复选框。</p></td>
</tr>
<tr class="even">
<td><p>分钟</p></td>
<td><p>指定的每个迭代，时间在几分钟内，计算机将花费在连接待机状态。</p></td>
</tr>
<tr class="odd">
<td><p>禁用静音时间</p></td>
<td><p>指定是否在评估过程中禁用静音时间功能。 默认情况下，不会禁用静音时间功能。</p></td>
</tr>
</tbody>
</table>

 

 

 






