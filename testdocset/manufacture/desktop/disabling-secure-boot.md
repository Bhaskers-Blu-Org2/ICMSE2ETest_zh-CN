---
author: Justinha
Description: "禁用安全启动"
ms.assetid: 2b98718d-13ce-4a5d-bd89-d276a0dc493d
MSHAttr: PreferredLib:/library/windows/hardware
title: "禁用安全启动"
ms.openlocfilehash: bd984c1e34181abaa16a37f3a678289379002077
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="disabling-secure-boot"></a>禁用安全启动


您可能需要禁用安全启动运行某些 PC 图形卡、 硬件或操作系统，如 Linux 或以前版本的 Windows。

安全启动有助于确保您的 PC 启动使用受信任的制造商的固件。

对于大多数 Pc，可以通过 PC 的固件 (BIOS) 菜单禁用安全启动。 对于徽标认证 Windows RT 8.1 和 Windows RT Pc，安全引导是需要进行配置，以便它不能被禁用。

**警告**  
-   禁用安全启动和安装的其他软件和硬件之后, 它可能很难不将计算机还原到出厂状态中重新激活安全启动。

-   更改 BIOS 设置时要小心。 BIOS 菜单为高级用户设计，它有可能更改阻止计算机正确启动的设置。 一定要严格按照制造商的说明进行操作。

 

**若要禁用安全启动︰**

1.  禁用安全引导之前, 应考虑是否有必要。 有时，您的制造商可以为您的 PC 更新信任的硬件、 驱动程序和操作系统的列表。 要检查更新，请转到 Windows 更新或查看制造商的网站。

2.  打开 PC 的 BIOS 菜单。 通常可以通过在启动过程中，如 F1、 F2、 f12 键或 esc 键按下一个键来访问该菜单。

    或者，在 Windows 中，按住 Shift 键的同时选择**重新启动**。 转到**解决&gt;高级选项︰ UEFI 固件设置**。

3.  找到**安全启动**设置，并且如果可能，请将其设置为**禁用**。 此选项通常是以**安全**选项卡、**启动**选项卡或**身份验证**选项卡。

4.  保存更改并退出。 计算机将重新启动。

5.  安装图形卡、 硬件或安全启动与不兼容的操作系统。

    在某些情况下，您可能需要更改其他设置，例如启用兼容性支持模块 (CSM) 以支持旧的 BIOS 操作系统的固件中。 若要使用 CSM，您可能还需要重新格式化硬盘使用主启动记录 (MBR) 的格式，然后再重新安装 Windows。 有关详细信息，请参阅[Windows 安装︰ 安装使用 MBR 或 GPT 分区样式](windows-setup-installing-using-the-mbr-or-gpt-partition-style.md)。

6.  如果您使用的 Windows 8.1，您可能会提醒您未正确配置安全启动桌面上看到水印。 获取此[更新，以删除安全启动桌面上的水印](http://go.microsoft.com/fwlink/p/?linkid=329932)。

**要重新启用安全启动︰**

1.  卸载任何图形卡、 硬件或安全启动与不兼容的操作系统。

2.  打开 PC 的 BIOS 菜单。 通常可以通过在启动过程中，如 F1、 F2、 f12 键或 esc 键按下一个键来访问该菜单。

    或从 Windows︰ 转到**设置超级按钮&gt;更改 PC 设置&gt;更新和恢复&gt;恢复&gt;高级启动︰ 立即重新启动**。 当计算机重新启动时，请转到**疑难解答&gt;高级选项︰ UEFI 固件设置**。

3.  找到**安全启动**设置，并且如果可能，请将其设置为**启用**。 此选项通常是以**安全**选项卡、**启动**选项卡或**身份验证**选项卡。

    在一些个人电脑上，选择**自定义**、，然后加载内置于 PC 的安全启动键。

    如果计算机不允许您启用安全启动，请尝试重置回出厂设置的 BIOS。

4.  保存更改并退出。 计算机将重新启动。

5.  如果 PC 将不能启用安全启动后启动，请转回的 BIOS 菜单，禁用安全启动，并尝试再次启动 PC。

6.  在某些情况下，您可能需要刷新，或您可以打开安全启动之前，您的 PC 重置到其原始状态。 有关详细信息，请参阅[如何还原、 刷新或重置您的 PC](http://go.microsoft.com/fwlink/p/?linkid=279534)。

7.  如果以上步骤不起作用，并且您仍然要使用安全启动功能，与制造商联系，寻求帮助。

    PC 制造商的其他疑难解答步骤︰ 请参阅[安全启动配置错误︰ 确定计算机是否在制造模式下 （制造商信息）](secure-boot-isnt-configured-correctly-determine-if-the-pc-is-in-a-manufacturing-mode--info-for-manufacturers.md)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[安全引导概述](secure-boot-overview.md)

[未正确配置安全启动︰ 疑难解答](secure-boot-isnt-configured-correctly-troubleshooting.md)

 

 






