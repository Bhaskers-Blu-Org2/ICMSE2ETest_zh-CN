---
author: Justinha
Description: 'Secure Boot isn''t configured correctly: Determine if the PC is in a manufacturing mode (info for manufacturers)'
ms.assetid: 68f143f8-c689-474f-a7b7-2f0fe7b0f1ec
MSHAttr: PreferredLib:/library/windows/hardware
title: 'Secure Boot isn''t configured correctly: Determine if the PC is in a manufacturing mode (info for manufacturers)'
ms.openlocfilehash: 8a5a3413a4135dc69e74cea3998844e3910bb9af
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="secure-boot-isnt-configured-correctly-determine-if-the-pc-is-in-a-manufacturing-mode-info-for-manufacturers"></a>未正确配置安全启动︰ 确定计算机是否在制造模式下 （制造商的信息）


同时生产个人电脑，如果"安全启动不正确地配置"水印将出现在 Windows 桌面上，您可能需要确定是否禁用安全启动或 PC 制造/调试模式。 计算机是在制造/调试模式下，每次安装时的非生产策略。 有关详细信息，请参阅白皮书︰ Microsoft **Windows 8.1 安全启动密钥创建和管理指南**上的[Microsoft 连接](http://go.microsoft.com/fwlink/p/?linkid=92770)网站或联系人帐户经理。

**请注意**  
**没有升级到 Windows 8.1、 Windows Server 2012 R2 或 Windows RT 8.1 后看见水印，"安全启动不正确配置"？**

我们将发布一个修补程序不久，摒弃水印。

Windows 8.1 和 Windows Server 2012 R2 的用户才能安装修补程序以立即删除水印︰ [Microsoft 知识库文章 ID 2902864](http://go.microsoft.com/fwlink/p/?linkid=329932)。

有关详细信息，请参阅[没有正确配置安全启动︰ 故障排除](secure-boot-isnt-configured-correctly-troubleshooting.md)。

 

## <a name="span-iddeterminingifthepcisinamanufacturingmodespanspan-iddeterminingifthepcisinamanufacturingmodespanspan-iddeterminingifthepcisinamanufacturingmodespandetermining-if-the-pc-is-in-a-manufacturing-mode"></a><span id="Determining_if_the_PC_is_in_a_manufacturing_mode"></span><span id="determining_if_the_pc_is_in_a_manufacturing_mode"></span><span id="DETERMINING_IF_THE_PC_IS_IN_A_MANUFACTURING_MODE"></span>确定计算机是否处于制造模式


可以使用以下方法之一来确定是否已禁用安全启动或 PC 制造 / 调试模式。

-   **使用 MSInfo32。** 单击**开始**，键入**msinfo32**。 如果**BIOS 模式︰ UEFI**是**UEFI**和**安全启动状态**为**OFF**，则禁用安全启动。

-   **检查事件日志**。 转到**启动&gt;查看事件日志&gt;应用程序和服务日志&gt;Microsoft &gt; Windows &gt; VerifyHardwareSecurity&gt;管理**，并寻找其中任一记录的事件︰

    "安全启动当前被禁用。 请启用 Secureboot 通过系统固件。 （PC 处于 UEFI 模式和安全启动处于禁用状态）。

    "检测到非生产安全引导策略。 删除通过系统固件调试/预发布版策略"。 （电脑是在制造/调试模式下）。

-   **使用 PowerShell 命令。**

    打开作为管理员，PowerShell 窗口，然后使用下列命令︰

    `Confirm-SecureBootUEFI`︰ 如果禁用安全启动检查。 响应︰

    -   "真": 启用了安全引导，并且不会显示水印。

    -   "假": 禁用定时器和水印将出现。

    -   "在此平台上不支持的 Cmdlet": PC 可能不支持安全启动，或者可能在旧的 BIOS 模式下配置 PC。 不会出现水印。

    -   无法设置适当的权限。 访问被拒绝。": 关闭 PowerShell 并以管理员身份重新打开它。

    "获得 SecureBootPolicy": 检查以查看您是否具有安装一个非生产策略。 响应︰

    -   "{77FA9ABD-0359-4D32-BD60-28F4E78F784B}": 正确的安全启动策略已就绪。

    -   任何其他 GUID: 电脑是在制造/调试模式中，并显示非生产安全引导策略的 GUID。

    -   "不在此计算机上启用安全启动策略": 既安全引导被禁用，或计算机被配置为旧的 BIOS 模式下启动。 如果计算机是在旧的 BIOS 模式下，不应出现水印。

    -   "不正确的身份验证数据": 关闭 PowerShell 并以管理员身份重新打开它。

## <a name="span-idhowdoifixitspanspan-idhowdoifixitspanspan-idhowdoifixitspanhow-do-i-fix-it"></a><span id="How_do_I_fix_it_"></span><span id="how_do_i_fix_it_"></span><span id="HOW_DO_I_FIX_IT_"></span>如何解决它？


**如果安全引导处于禁用状态**，重新启用它。 有关详细信息，请参阅[没有正确配置安全启动︰ 故障排除](secure-boot-isnt-configured-correctly-troubleshooting.md)。

**如果安全启动已启用，但电脑是制造/调试模式中**，您将需要卸载非生产策略。 有关详细信息，请参阅白皮书︰ Microsoft **Windows 8.1 安全启动密钥创建和管理指南**上的[Microsoft 连接](http://go.microsoft.com/fwlink/p/?linkid=92770)网站或联系人帐户经理。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[未正确配置安全启动︰ 疑难解答](secure-boot-isnt-configured-correctly-troubleshooting.md)

 

 






