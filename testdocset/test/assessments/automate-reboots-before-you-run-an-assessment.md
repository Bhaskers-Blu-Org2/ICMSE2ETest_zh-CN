---
title: "自动重新启动前运行评估"
description: "自动重新启动前运行评估"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 4aadbc09-9c0a-4b38-b79d-989906c0aa50
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: e17d93d41b4eac22c3b8396a41de77bccca39183
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="automate-reboots-before-you-run-an-assessment"></a>自动重新启动前运行评估


一些评估需要计算机重新启动时运行评估。 如果要手动运行评估期间监视的计算机，就可以登录每次时，计算机将重新启动。 但是，如果您不打算监视计算机运行评估时，您可以配置自动登录的计算机。 本主题中的步骤说明︰

-   如何配置一台计算机而不登录提示通过调整注册表中的设置。 当您使用 Windows 评估控制台评估本地计算机时，我们建议此过程。

-   如何创建将自动登录到一台计算机在重新启动后的用户帐户。 我们建议测试计算机的域访问权限或其他潜在的网络漏洞没有此的过程。

**若要调整注册表设置自动登录。**

1.  单击**开始**，键入**注册表编辑器**，然后单击**注册表编辑器**。

2.  在注册表编辑器中找到以下注册表项︰

    **HKEY\_本地\_机\\软件\\Microsoft\\Windows NT\\CurrentVersion\\Winlogon**

3.  双击**DefaultUserName**项，键入您的用户名，然后单击**确定**。

4.  双击**DefaultPassword**项，键入您的密码，然后单击**确定**。

    **安全说明︰**

    此密码以纯文本格式存储，提供了一个安全漏洞。 我们建议使用测试帐户，当您完成了运行评估删除的键值。

5.  如果**DefaultPassword**值不存在，请按照下列步骤︰

    1.  单击**编辑**，单击**新建**，然后单击**字符串值**。

    2.  在**数值名称**框中，键入**DefaultPassword**。

    3.  在**数据类型**框中，确认**REG\_SZ**处于选中状态。

    4.  在**数值数据**框中，键入您的密码。

    5.  单击**确定**以保存所做的更改。

    6.  从 0 （假） 的**AutoAdminLogon**项的值更改为 1 (TRUE)。 这使 AutoAdminLogon 功能。

    7.  退出注册表编辑器。

6.  重新启动计算机，请确保，它使您登录自动。

    **请注意**  
    若要绕过 AutoAdminLogon 过程中，并以其他用户身份登录，请注销后或 Windows 重新启动后按住 Shift 键。

     

在计算机上运行评估完毕后，您可以重新设置为原始值执行常规登录过程，更改注册表设置。

**准备用户帐户并禁用安全登录**

1.  创建一个标准用户的计算机。

    **重要**  
    -   不为用户提供一个密码。

    -   不允许或配置与域的连接。

     

2.  删除所有的用户、 密码和域连接。

3.  通过执行下列步骤禁用安全登录︰

    1.  单击**开始**，然后键入**netplwiz**可以找到并打开**用户帐户**对话框。

    2.  在**高级**选项卡上，清除**要求用户按 Ctrl + Alt + Delete**复选框。

此单个用户帐户允许在没有监视或手动登录的任何步骤的计算机上运行的评估。

## <a name="related-topics"></a>相关的主题


[开/关切换性能](onoff-transition-performance.md)

[内存占用量](memory-footprint.md)

[评估 Windows 控制台](windows-assessment-console.md)

 

 







