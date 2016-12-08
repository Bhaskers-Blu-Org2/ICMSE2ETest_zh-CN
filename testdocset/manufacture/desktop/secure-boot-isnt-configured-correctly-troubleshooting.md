---
author: Justinha
Description: 'Secure Boot isn''t configured correctly: troubleshooting'
ms.assetid: a2b9b89f-9d42-4537-a3f8-0403cd67df16
MSHAttr: PreferredLib:/library/windows/hardware
title: 'Secure Boot isn''t configured correctly: troubleshooting'
ms.openlocfilehash: b6d799d77e6265b0892fe981fc603194ecdd2193
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="secure-boot-isnt-configured-correctly-troubleshooting"></a>未正确配置安全启动︰ 疑难解答


"安全启动不正确地配置"水印会出现在 Windows 桌面电脑能够使用安全启动安全功能，但该功能未启用或未正确配置。

更新到 Windows 8.1 从 Windows 8 PC 后可能会出现此消息。

## <a name="span-idwhatissecurebootspanspan-idwhatissecurebootspanspan-idwhatissecurebootspanwhat-is-secure-boot"></a><span id="What_is_Secure_Boot_"></span><span id="what_is_secure_boot_"></span><span id="WHAT_IS_SECURE_BOOT_"></span>什么是安全启动？


安全启动有助于确保您的 PC 启动使用受信任的制造商的固件。 安全启动的详细信息，请参阅[安全引导概述](secure-boot-overview.md)。

## <a name="span-idismypcunsafespanspan-idismypcunsafespanspan-idismypcunsafespanis-my-pc-unsafe"></a><span id="Is_my_PC_unsafe_"></span><span id="is_my_pc_unsafe_"></span><span id="IS_MY_PC_UNSAFE_"></span>我的 PC 是否是不安全的？


您的电脑可能会成功，但它不是为受保护来说，因为没有运行安全启动。

您可能需要禁用安全启动运行某些硬件、 图形卡或操作系统，如 Linux 或以前版本的 Windows。 有关详细信息，请参阅[禁用安全引导](disabling-secure-boot.md)。

您检查您的 PC 安全启动的状态。 单击`Start`，和类型 msinfo32 然后按 enter。 在系统摘要下您可以看到您的 BIOS 模式和安全启动状态。 如果 Bios 模式是 （uefi），并且安全启动状态处于关闭状态，则会禁用安全启动。

## <a name="span-idcanijustdismissthisalertorremovethewatermarkspanspan-idcanijustdismissthisalertorremovethewatermarkspanspan-idcanijustdismissthisalertorremovethewatermarkspancan-i-just-dismiss-this-alert-or-remove-the-watermark"></a><span id="Can_I_just_dismiss_this_alert_or_remove_the_watermark_"></span><span id="can_i_just_dismiss_this_alert_or_remove_the_watermark_"></span><span id="CAN_I_JUST_DISMISS_THIS_ALERT_OR_REMOVE_THE_WATERMARK_"></span>可以只是消除此警报或删除水印？


是。 转到 Windows 更新的摒弃水印的修补程序。

-   Windows 8.1 和 Windows Server 2012 R2 的用户还可以下载此修补程序手动︰[更新删除 Windows 8.1 和 Windows Server 2012 R2 (Microsoft 知识库文章 ID 2902864) 中的"Windows 8.1 SecureBoot 没有正确配置"水印](http://go.microsoft.com/fwlink/p/?linkid=329932)

-   Windows RT 8.1︰ 通过 Windows update 获取该修补程序。

## <a name="span-ididliketousethisfeaturehowcanienableitspanspan-ididliketousethisfeaturehowcanienableitspanid-like-to-use-this-feature-how-can-i-enable-it"></a><span id="i_d_like_to_use_this_feature._how_can_i_enable_it_"></span><span id="I_D_LIKE_TO_USE_THIS_FEATURE._HOW_CAN_I_ENABLE_IT_"></span>我想使用此功能。 如何启用它？


请尝试通过使用 PC 的 BIOS 菜单中启用安全启动。

**警告**  
更改 BIOS 设置时要小心。 BIOS 菜单为高级用户设计，它有可能更改阻止计算机正确启动的设置。 一定要严格按照制造商的说明进行操作。

 

**启用安全启动**

1.  打开 PC 的 BIOS 菜单。 通常可以通过在启动过程中，如 F1、 F2、 f12 键或 esc 键按下一个键来访问该菜单。

    或从 Windows︰ 转到**设置超级按钮&gt;更改 PC 设置&gt;更新和恢复&gt;恢复&gt;高级启动︰ 立即重新启动**。 当计算机重新启动时，请转到**疑难解答&gt;高级选项︰ UEFI 固件设置**。

2.  找到**安全启动**设置，并且如果可能，请将其设置为**启用**。 此选项通常是以**安全**选项卡、**启动**选项卡或**身份验证**选项卡。

    在一些个人电脑上，选择**自定义**、，然后加载内置于 PC 的安全启动键。

    如果计算机不允许您启用安全启动，请尝试重置回出厂设置的 BIOS。

3.  保存更改并退出。 计算机将重新启动。

4.  如果 PC 将不能启用安全启动后启动，请转回的 BIOS 菜单，禁用安全启动，并尝试再次启动 PC。

5.  在某些情况下，您可能需要刷新，或您可以打开安全启动之前，您的 PC 重置到其原始状态。 有关详细信息，请参阅[如何还原、 刷新或重置您的 PC](http://go.microsoft.com/fwlink/p/?linkid=279534)。

6.  如果以上步骤不起作用，并且您仍然要使用安全启动功能，与制造商联系，寻求帮助。

    PC 制造商的其他疑难解答步骤︰ 请参阅[安全启动配置错误︰ 确定计算机是否在制造模式下 （制造商信息）](secure-boot-isnt-configured-correctly-determine-if-the-pc-is-in-a-manufacturing-mode--info-for-manufacturers.md)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[在我的桌面上有为什么"SecureBoot 没有正确配置"水印？](http://go.microsoft.com/fwlink/?LinkId=624321)

[安全引导概述](secure-boot-overview.md)

[Microsoft 支持知识文库文章 2902864](http://support.microsoft.com/kb/2902864)

[禁用安全启动](disabling-secure-boot.md)

 

 






