---
author: Justinha
Description: "审核模式概述"
ms.assetid: c4d7921f-0709-40bd-bbc5-38fd793d6b88
MSHAttr: PreferredLib:/library/windows/hardware
title: "审核模式概述"
ms.openlocfilehash: ef245b8febfd1b8c11117aed8cc1e5b03c916467
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="audit-mode-overview"></a>审核模式概述


当 Windows 启动时，它开始在任何一种全新的体验 (OOBE) 模式或在审核模式下。 OOBE 是允许最终用户输入他们的帐户信息，选择语言，接受 Microsoft 服务，然后设置网络默认的全新体验。

您可以将 Windows 配置为启动到审核模式。 在审核模式下，您可以对 Windows 安装进行其他更改之前发送给客户的计算机或您的组织中捕获的图像以供重用。 例如，可以安装驱动程序软件包中包括驱动程序、 安装应用程序，或将需要运行在 Windows 安装其他更新程序。 使用答案文件时，Windows 将处理中[auditSystem](auditsystem.md)和[auditUser](audituser.md)配置阶段的设置。

引导到审核模式时登录到系统中使用内置的管理员帐户。 在登录到系统后，将立即在[auditUser](audituser.md)配置阶段期间禁用内置管理员帐户。 在下次计算机重新启动时，内置的管理员帐户一直保持禁用状态。 有关详细信息，请参阅[启用和禁用内置管理员帐户](enable-and-disable-the-built-in-administrator-account.md)。

**重要**  
-   如果在审核模式中，并且受密码保护的屏幕保护程序启动，则无法重新登录到系统。 登录后立即禁用内置管理员帐户，用于登录到审核模式。

    若要禁用屏幕保护程序，或者更改通过控制面板电源计划或配置和部署一个自定义计划。 有关详细信息，请参阅[创建自定义电源计划](create-a-custom-power-plan-technicalreference.md)。

-   在审核模式下不出现[oobeSystem](oobesystem.md)配置阶段从无人参与的答案文件中的设置。

 

## <a name="span-idbenefitsofusingauditmodespanspan-idbenefitsofusingauditmodespanspan-idbenefitsofusingauditmodespanbenefits-of-using-audit-mode"></a><span id="Benefits_of_using_Audit_Mode"></span><span id="benefits_of_using_audit_mode"></span><span id="BENEFITS_OF_USING_AUDIT_MODE"></span>使用审核模式的优点


在审核模式下，可以执行以下操作︰

-   **旁路 OOBE。** 您可以尽快访问桌面。 不需要配置默认设置，如用户帐户、 位置和时区。

-   **安装应用程序、 添加设备驱动程序，并运行脚本。** 您可以连接到网络并访问其他安装文件和脚本。 您还可以安装其他语言包和设备驱动程序。 有关详细信息，请参阅[添加驱动程序在线在审核模式下](add-a-driver-online-in-audit-mode.md)。

-   **测试 Windows 安装的有效性。** 将系统部署到最终用户之前，可以无需创建用户帐户在系统上执行测试。 然后您可以准备在 OOBE 在下次引导系统。

-   **将多个自定义项添加到参考映像。** 这将减少需要管理的映像的数目。 例如，您可以创建单个参考映像，其中包含您要应用到所有 Windows 映像的基本自定义。 然后可以启动参考映像，以审核模式并进行特定于计算机的其他更改。 这些更改可以是客户请求的应用程序或特定设备驱动程序。

## <a name="span-idboottoauditmodespanspan-idboottoauditmodespanspan-idboottoauditmodespanboot-to-audit-mode"></a><span id="Boot_to_Audit_Mode"></span><span id="boot_to_audit_mode"></span><span id="BOOT_TO_AUDIT_MODE"></span>引导到审核模式


您可以启动到审核模式，在新的或现有的 Windows 安装。 有关详细信息，请参阅[启动到审核模式或 OOBE 的 Windows](boot-windows-to-audit-mode-or-oobe.md)。

## <a name="span-idautomaticallydisplaythewindows8desktopspanspan-idautomaticallydisplaythewindows8desktopspanspan-idautomaticallydisplaythewindows8desktopspanautomatically-display-the-windows-8-desktop"></a><span id="Automatically_Display_the_Windows_8_Desktop"></span><span id="automatically_display_the_windows_8_desktop"></span><span id="AUTOMATICALLY_DISPLAY_THE_WINDOWS_8_DESKTOP"></span>自动显示 Windows 8 桌面


某些 Windows 8 中可能需要自动显示 Windows 8 桌面而不是 Windows 8 的制造业或测试方案计算机重新启动后启动屏幕。 如果您使用显示在桌面上的窗口状态的制造工具，并且您希望工厂技术人员可以轻松地识别问题，而无需手动从 Windows 8 开始屏幕切换到桌面，则可能需要。

您可以通过使用 %WINDIR%自动显示 Windows 8 桌面\\System32\\oobe\\AuditShD.exe。 AuditShD.exe 必须具有管理员权限的帐户运行。

我们建议作为 RunAsynchronousCommand 在 auditUser 配置阶段中添加此命令行答案文件。 使用 Windows 系统映像管理器添加**Microsoft Windows 部署** | **RunAsynchronous** | **RunAsynchronousCommand**的值**%WINDIR%\\System32\\oobe\\AuditShD.exe**。

您创建的应答文件将类似于以下︰

``` syntax
<settings pass="auditUser">
<component name="Microsoft-Windows-Deployment" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
    <RunAsynchronous>
       <RunAsynchronousCommand wcm:action="add">
          <Description>Show Desktop</Description>
          <Order>1</Order>
          <Path>cmd.exe /c %WINDIR%\System32\oobe\AuditShD.exe</Path>
       </RunAsynchronousCommand>
    </RunAsynchronous>
  </component>
</settings> 
```

Windows 8 PC 发货给客户之前，必须配置 Windows 引导至 OOBE 屏幕并显示开始屏幕上第一次启动。 AuditShD.exe 仅配置为在审核模式下运行，并在 OOBE 期间不使用验证。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[了解处理策略](understanding-servicing-strategies.md)

[Windows 安装程序配置阶段](windows-setup-configuration-passes.md)

[配置阶段的工作](how-configuration-passes-work.md)

[Windows 安装程序方案和最佳做法](windows-setup-scenarios-and-best-practices.md)

[Windows 安装程序安装过程](windows-setup-installation-process.md)

[Windows 安装程序自动化概述](windows-setup-automation-overview.md)

[Windows 安装程序支持的平台和跨平台部署](windows-setup-supported-platforms-and-cross-platform-deployments.md)

 

 






