---
author: Justinha
Description: "向 Windows 安装程序中添加自定义脚本"
ms.assetid: a22c2f2f-c297-4027-9712-d747b08f7476
MSHAttr: PreferredLib:/library/windows/hardware
title: "向 Windows 安装程序中添加自定义脚本"
ms.openlocfilehash: d78a352e8d2e8817c755377e0acfca7067d2ebd8
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add-a-custom-script-to-windows-setup"></a>向 Windows 安装程序中添加自定义脚本


**Windows 安装程序脚本**︰ **Setupcomplete.cmd**和**ErrorHandler.cmd**是运行期间或之后 Windows 安装程序的自定义脚本。 它们可以用于安装应用程序或通过使用**cscript/wscript**脚本运行其他任务。

-   **%WINDIR%\\安装程序\\脚本\\SetupComplete.cmd**︰ 用户可以看到桌面后立即运行此脚本。 使用 OEM 产品密钥时，禁用此设置。 它将使用本地系统权限运行。
-   **%WINDIR%\\安装程序\\脚本\\ErrorHandler.cmd**︰ 该脚本将自动运行时，安装程序遇到致命错误。 它将使用本地系统权限运行。

**无人参与的 Windows 脚本**︰ 创建 Unattend.xml 文件与其中一个设置可以在 Windows 安装过程中运行。 这可以使用 OEM 产品密钥。

若要运行服务或命令，可以在同一时间启动，请使用 RunAsynchronousCommands。 运行其他命令之前完成所需的命令可以启动，请使用 RunSynchronousCommands。

**请注意** Windows 10 年[Microsoft 窗口外壳安装\\LogonCommands\\AsynchronousCommand](https://msdn.microsoft.com/library/windows/hardware/dn915476)的作用现在类似 LogonCommands\\AsynchronousCommand︰ 所有命令使用这些无人都参与设置被现在启动一次，不再等待前一个命令来完成。

 

其中的某些设置的用户上下文中运行，其他人根据配置阶段的系统上下文中运行。

-   添加[Microsoft Windows 安装程序\\RunAsynchronousCommand](https://msdn.microsoft.com/library/windows/hardware/dn915798)或[RunSynchronousCommand](https://msdn.microsoft.com/library/windows/hardware/dn915802)在 Windows 安装程序启动时运行的脚本。 这可以有助于设置硬盘分区。
-   添加[Microsoft Windows 部署\\RunAsynchronousCommand](https://msdn.microsoft.com/library/windows/hardware/dn915797)或[RunSynchronousCommand](https://msdn.microsoft.com/library/windows/hardware/dn915801)与**auditUser**配置阶段运行计算机进入审核模式时运行的脚本。 这可以有助于自动化应用程序安装或测试等任务。
-   添加[Microsoft Windows 外壳程序安装\\LogonCommands\\AsynchronousCommand](https://msdn.microsoft.com/library/windows/hardware/dn915476)或[FirstLogonCommands\\SynchronousCommand](https://msdn.microsoft.com/library/windows/hardware/dn922797)后全新体验 (OOBE) 之前运行用户可以看到桌面。 这可以非常有用，可以设置特定于语言的应用程序或内容后用户已经选择了自己的语言。

    尽量少使用这些脚本，因为长的脚本可以防止用户快速到达开始屏幕。 对于零售版本的 Windows 中，附加的限制应用到这些脚本。 信息，请参阅[OEM 合作伙伴中心](http://go.microsoft.com/fwlink/?LinkId=131358)的授权和政策指导。

    **请注意**  当您添加脚本使用 FirstLogonCommands 时，它将会触发下一次启动，即使启动到审核模式下使用 Ctrl + Shift + F3。 要引导到审核模式，而不会触发这些脚本，请添加设置︰ Microsoft Windows 部署\\重新封装\\[模式](https://msdn.microsoft.com/library/windows/hardware/dn923110)= 审核。

     

## <a name="span-idrunascriptaftersetupiscompletesetupcompletecmdspanspan-idrunascriptaftersetupiscompletesetupcompletecmdspanrun-a-script-after-setup-is-complete-setupcompletecmd"></a><span id="run_a_script_after_setup_is_complete__setupcomplete.cmd_"></span><span id="RUN_A_SCRIPT_AFTER_SETUP_IS_COMPLETE__SETUPCOMPLETE.CMD_"></span>在安装程序完成 (SetupComplete.cmd) 之后运行脚本


**运算顺序**

1.  后安装了 Windows，但在登录屏幕出现之前，Windows 安装程序搜索中的**SetupComplete.cmd**文件**%WINDIR%\\安装程序\\脚本\\目录**。
2.  如果找到**SetupComplete.cmd**文件，则 Windows 安装程序将运行的脚本。 Windows 安装程序将该操作记录在**c:\\Windows\\黑豹\\UnattendGC\\Setupact.log**文件。

    安装程序不验证任何退出代码或脚本中的错误级别，它执行**SetupComplete.cmd**后。

    **警告** 您不能重新引导系统并继续运行**SetupComplete.cmd**。 不应该加上如**关闭-r**命令重新启动系统。 这将使系统处于错误状态。

     

3.  如果计算机在安装过程中加入域时，域中定义的组策略不应用到计算机直到完成**Setupcomplete.cmd** 。 这是为了确保组策略配置活动不会干扰该脚本。

## <a name="span-idrunascriptifwindowssetupencountersafatalerrorerrorhandlercmdspanspan-idrunascriptifwindowssetupencountersafatalerrorerrorhandlercmdspanrun-a-script-if-windows-setup-encounters-a-fatal-error-errorhandlercmd"></a><span id="run_a_script_if_windows_setup_encounters_a_fatal_error__errorhandler.cmd_"></span><span id="RUN_A_SCRIPT_IF_WINDOWS_SETUP_ENCOUNTERS_A_FATAL_ERROR__ERRORHANDLER.CMD_"></span>如果 Windows 安装程序遇到致命错误 (ErrorHandler.cmd)，运行脚本


在同时安装多个系统时，此脚本很有用。 这有助于您在 Windows 安装期间发生错误时检测。 这样，安装程序将自动运行脚本可以包含自定义命令或操作来解决该错误的原因。

如果 Windows 安装程序遇到致命错误，无法完成安装，Windows 安装程序将搜索以下目录中的命令脚本︰ **%WINDIR%\\安装程序\\脚本\\ErrorHandler.cmd**。 会发生两个操作之一，具体取决于是否找到该脚本。

-   如果未找到该脚本，对话框中显示的错误文本。 Windows 安装程序退出之前，用户必须关闭该对话框。
-   如果找到该脚本，该脚本将同步执行。 将不显示任何对话框或错误文本。 **ErrorHandler.cmd**脚本运行完毕后，Windows 安装程序将退出。

这取决于 Windows 安装程序的阶段，计算机将返回到其 Windows 安装程序执行，如较早版本的操作系统或 Windows 预安装环境 (Windows PE)，例如环境。

当 Windows 安装程序遇到多个错误，并且多次运行 ErrorHandler.cmd 脚本，则可能存在实例。 当为**ErrorHandler.cmd**开发代码，请确保运行此脚本多次。


**使用 ErrorHandler.cmd**，可以执行下列任一操作︰

-   装入该映像，并将其添加到图像上时，在**%WINDIR%\\安装程序\\脚本\\ErrorHandler.cmd**。 卸载该映像。

    -或者-

-   将**ErrorHandler.cmd**添加到临时文件的位置 (例如，c:\\温度\\ErrorHandler.cmd)，然后运行 Windows 安装程序使用**/m**选项。
    ``` syntax
    Setup /m:C:\Temp
    ```

    若要了解详细信息，请参阅[Windows 安装程序命令行选项](windows-setup-command-line-options.md)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Windows 安装程序技术参考](windows-setup-technical-reference.md)

[从 DVD 启动](boot-from-a-dvd.md)

[使用 Windows 安装程序配置集](use-a-configuration-set-with-windows-setup.md)

[部署自定义映像](deploy-a-custom-image.md)

[引导到审核模式或 OOBE 的窗口](boot-windows-to-audit-mode-or-oobe.md)

[在 Windows 安装期间添加到 Windows 的设备驱动程序](add-device-drivers-to-windows-during-windows-setup.md)

 

 






