---
author: Justinha
Description: "通过使用应答文件来启用远程桌面"
ms.assetid: bee7ad87-7fb4-4313-baab-109a6f067ccc
MSHAttr: PreferredLib:/library/windows/hardware
title: "通过使用应答文件来启用远程桌面"
ms.openlocfilehash: 6b3fd47cb4701ba1c4b918fb1cfd7b7bf3cdd23d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="enable-remote-desktop-by-using-an-answer-file"></a>通过使用应答文件来启用远程桌面


要在无人参与安装过程中启用远程桌面连接，您必须配置多个设置并启用具有高级安全性的 Windows® 防火墙中的远程桌面组。

**若要创建一个应答文件以启用远程桌面连接**

1.  技术人员计算机上打开 Windows 系统映像管理器 （Windows sim 卡）。 单击**开始**，键入**Windows 系统映像管理器**，然后选择**Windows 系统映像管理器**。

2.  创建新的应答文件，或更新现有的应答文件。 有关详细信息，请参阅[创建或打开答案文件](https://msdn.microsoft.com/library/windows/hardware/dn915085)和[创作答案文件的最佳做法](https://msdn.microsoft.com/library/windows/hardware/dn915073)。

    将这些设置添加到答案文件中列出的配置阶段中︰

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left">组件</th>
    <th align="left">配置阶段</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><p>Microsoft Windows TerminalServices LocalSessionManager</p></td>
    <td align="left"><p><strong>4 专用化</strong></p></td>
    </tr>
    <tr class="even">
    <td align="left"><p>网络连接-mpssvc-Svc\FirewallGroups\FirewallGroup</p></td>
    <td align="left"><p><strong>4 专用化</strong></p></td>
    </tr>
    </tbody>
    </table>

     

3.  在**应答文件**窗格中，配置下列设置︰

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left">组件</th>
    <th align="left">值</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><p>Microsoft Windows TerminalServices LocalSessionManager</p></td>
    <td align="left"><p><code>fDenyTSConnections=false</code></p></td>
    </tr>
    <tr class="even">
    <td align="left"><p>网络连接-mpssvc-Svc\FirewallGroups\FirewallGroup</p></td>
    <td align="left"><p><code>Active=true</code></p>
    <p><code>Group=Remote Desktop</code></p>
    <p><code>Profile=all</code></p></td>
    </tr>
    </tbody>
    </table>

     

4.  （可选）指定如何对用户进行身份验证。 指定以下设置将帮助确保用户可以远程连接中不使用网络级身份验证运行远程桌面的计算机。 要启用远程桌面运行任意版本远程桌面的计算机连接，请将此设置添加到答案文件︰

    <table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left">组件</th>
    <th align="left">配置阶段</th>
    <th align="left">值</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><p>Microsoft 的 Windows-TerminalServices-RDP-WinStationExtensions</p></td>
    <td align="left"><p><strong>4 专用化</strong></p></td>
    <td align="left"><p><code>UserAuthentication=0</code></p></td>
    </tr>
    </tbody>
    </table>

您现在准备好进行安装的 Windows 映像。

有关 Windows® 组件和设置，您可以将它们添加到答案文件的详细信息，请参阅[无人参与的 Windows 安装程序参考](https://msdn.microsoft.com/library/windows/hardware/dn923277)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[具有高级安全性的 Windows 防火墙配置通过使用应答文件](configure-windows-firewall-with-advanced-security-by-using-an-answer-file.md)

[自动执行 Windows 安装程序](automate-windows-setup.md)

[配置无人参与安装中的网络设置](configure-network-settings-in-an-unattended-installation.md)

[Windows 部署选项](windows-deployment-options.md)

 

 






