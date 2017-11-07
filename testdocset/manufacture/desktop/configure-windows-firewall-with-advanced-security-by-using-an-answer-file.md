---
author: Justinha
Description: "具有高级安全性的 Windows 防火墙配置通过使用应答文件"
ms.assetid: 6243caf7-3b74-431e-b6f9-76b98106bf42
MSHAttr: PreferredLib:/library/windows/hardware
title: "具有高级安全性的 Windows 防火墙配置通过使用应答文件"
ms.openlocfilehash: c2e4dfa7b38c180f5ca9bad38cdaebe3310a7336
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="configure-windows-firewall-with-advanced-security-by-using-an-answer-file"></a>具有高级安全性的 Windows 防火墙配置通过使用应答文件


对于无人参与安装，您可以使用网络-mpssvc Svc 组件使用答案文件中的高级安全性设置配置 Windows （） 防火墙。 除了具有高级安全性的 Windows 防火墙的应答文件 (Unattend.xml) 设置，您可以创建[auditUser](audituser.md)或[oobeSystem](oobesystem.md)配置阶段运行**由**命令**RunSynchronous**命令。

## <a name="span-idaddingmodifyingordeletingrulesforwindowsfirewallwithadvancedsecurityspanspan-idaddingmodifyingordeletingrulesforwindowsfirewallwithadvancedsecurityspanspan-idaddingmodifyingordeletingrulesforwindowsfirewallwithadvancedsecurityspanadding-modifying-or-deleting-rules-for-windows-firewall-with-advanced-security"></a><span id="Adding__Modifying__or_Deleting_Rules_for_Windows_Firewall_with_Advanced_Security"></span><span id="adding__modifying__or_deleting_rules_for_windows_firewall_with_advanced_security"></span><span id="ADDING__MODIFYING__OR_DELETING_RULES_FOR_WINDOWS_FIREWALL_WITH_ADVANCED_SECURITY"></span>添加、 修改或具有高级安全性的 Windows 防火墙中删除规则


使用**RunSynchronous**命令来添加、 修改或删除具有高级安全性的 Windows 防火墙规则。 若要修改规则组，使用**网络-mpssvc Svc**组件中的**FirewallGroups**设置。 有关 Windows 组件和设置，您可以将它们添加到答案文件的详细信息，请参阅[无人参与的 Windows 安装程序参考指南 》](http://go.microsoft.com/fwlink/?LinkId=206281)。

**要将 Netsh 命令添加到答案文件**

1.  技术人员计算机上打开 Windows 系统映像管理器 （Windows sim 卡）。 单击**开始**，键入**Windows 系统映像管理器**，然后选择**Windows 系统映像管理器**。

2.  创建新的应答文件，或更新现有的应答文件。 有关详细信息，请参阅[创建或打开答案文件](https://msdn.microsoft.com/library/windows/hardware/dn915085)和[创作答案文件的最佳做法](https://msdn.microsoft.com/library/windows/hardware/dn915073)。

3.  单击**插入**菜单上的**RunSynchronous**。

4.  选择想要安装命令的配置阶段。 这可能是在[auditUser](audituser.md)或[oobeSystem](oobesystem.md)配置阶段。

    **请注意**  
    不要在[specialize](specialize.md)配置阶段中使用**RunSynchronousNetsh 由**命令。

     

5.  **创建同步命令**对话框中出现。

6.  在**输入命令行**框中，键入**Netsh 由防火墙**等的命令行语法。 有关详细信息，请参阅[网络外壳程序 (Netsh) 技术参考](http://go.microsoft.com/fwlink/?LinkId=234733)。

7.  在**顺序**框中，选择命令将运行程序，然后单击**确定**的顺序。

    命令将添加到答案文件中的选定的配置阶段，如下所示︰

    1.  添加到**6 auditUser 刀**配置传递的命令出现在设置 Microsoft Windows 部署\\RunSynchronous。

    2.  到**7 oobeSystem**配置阶段添加的命令出现在设置 Microsoft Windows 外壳程序安装\\FirstLogonCommands。

8.  在**SynchronousCommand 属性**窗格中的**说明**，旁边的**设置**部分中，输入**启用 Windows Messenger**等说明。

9.  该命令添加到您选定的配置阶段下的答案文件。 此示例说明了如何配置用于 Windows Messenger 入站规则︰

    ``` syntax
          <RunSynchronous>
             <RunSynchronousCommand wcm:action="add">
                <Path>Netsh advfirewall firewall 
                      add rule name="allow messenger" dir=in 
                      program="c:\programfiles\messenger\msmsgs.exe"
                      action=allow
                </Path>
                <Description>Enable Windows Messenger</Description>
                <Order>1</Order>
             </RunSynchronousCommand>
          </RunSynchronous>
    ```

**请注意**  
**由**命令需要管理员权限才能运行。 如果在用户上下文中运行一个配置阶段运行**RunSynchronous**命令，该用户帐户必须具有管理员权限。

 

## <a name="span-idusingthenetshadvfirewallcommand-linetoolspanspan-idusingthenetshadvfirewallcommand-linetoolspanspan-idusingthenetshadvfirewallcommand-linetoolspanusing-the-netsh-advfirewall-command-line-tool"></a><span id="Using_the_Netsh_Advfirewall_Command-Line_Tool"></span><span id="using_the_netsh_advfirewall_command-line_tool"></span><span id="USING_THE_NETSH_ADVFIREWALL_COMMAND-LINE_TOOL"></span>使用由命令行工具


下面的示例演示如何添加一个新传出的防火墙规则，以阻止端口使用**由**命令行工具。

**若要添加新传出防火墙规则**

-   在提升的命令提示符下，输入语法来添加一个新传出的防火墙规则，以阻止的端口。 例如︰

    ``` syntax
    Netsh advfirewall firewall add rule name="allow80" protocol=TCP
    dir=out localport=80 action=block
    ```

    其中，则禁用的端口是 TCP 端口 80。

您可以对 Windows PowerShell 命令将**Netsh**命令。 有关详细信息，请参阅[Netshell 到 Powershell 转换指南 》](http://go.microsoft.com/fwlink/?LinkId=234734)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Windows 部署选项](windows-deployment-options.md)

 

 






