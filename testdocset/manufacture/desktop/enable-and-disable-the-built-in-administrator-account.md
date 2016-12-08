---
author: Justinha
Description: "启用和禁用内置管理员帐户"
ms.assetid: d6011433-badb-4707-a5b9-9325f33b6a95
MSHAttr: PreferredLib:/library/windows/hardware
title: "启用和禁用内置管理员帐户"
ms.openlocfilehash: 817440ec1abb4b5e8c157c40a7d657df0c96fdaf
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="enable-and-disable-the-built-in-administrator-account"></a>启用和禁用内置管理员帐户


当制造 Pc，可以使用内置的管理员帐户来运行程序和应用程序，然后创建一个用户帐户。

**请注意**  
本主题是关于制造电脑。 在您自己计算机上管理员帐户的帮助，请尝试这些页面︰

-   [以管理员身份登录](http://go.microsoft.com/fwlink/?LinkId=506857)

-   [删除名为"管理员"帐户](http://go.microsoft.com/fwlink/?LinkId=506858)

-   [用户帐户控制](http://go.microsoft.com/fwlink/?LinkId=277139)

 

当使用审核模式登录系统或您添加到[auditUser](audituser.md)配置脚本通过使用此帐户。

## <a name="span-idenablingthebuilt-inadministratoraccountspanspan-idenablingthebuilt-inadministratoraccountspanspan-idenablingthebuilt-inadministratoraccountspanenabling-the-built-in-administrator-account"></a><span id="Enabling_the_Built-in_Administrator_Account"></span><span id="enabling_the_built-in_administrator_account"></span><span id="ENABLING_THE_BUILT-IN_ADMINISTRATOR_ACCOUNT"></span>启用内置管理员帐户


**可以使用以下方法之一来启用内置管理员帐户︰**

1.  [使用答案文件](#useananswerfile)

2.  [使用审核模式下登录](#logonusingauditmode)

3.  [使用本地用户和组 MMC （仅服务器版本）](#usemmcconsole)

### <a name="span-iduseananswerfilespanspan-iduseananswerfilespanspan-iduseananswerfilespanuse-an-answer-file"></a><span id="UseAnAnswerFile"></span><span id="useananswerfile"></span><span id="USEANANSWERFILE"></span>使用答案文件

您可以通过设置在无人参与安装期间启用内置管理员帐户`AutoLogon`在 Microsoft Windows 外壳程序安装组件设置为**管理员**。 这将启用内置管理员帐户，即使在不指定密码`AdministratorPassword`设置。

您可以通过使用 Windows® 系统映像管理器 (Windows SIM) 创建答案文件。

以下的答案文件示例演示如何启用管理员帐户，指定管理员的密码，自动登录到系统。

**请注意**  
这两种 Microsoft Windows 的外壳-安装\\`Autologon`节和 Microsoft Windows 的外壳程序-安装\\`UserAccounts` \\ `AdministratorPassword`部分需要为自动登录在审核模式下工作。 **AuditSystem**的配置阶段必须包含两个这些设置。

 

以下 XML 输出显示如何设置适当的值︰

``` syntax
   <component name="Microsoft-Windows-Shell-Setup" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
      <AutoLogon>
         <Password>
            <Value>SecurePasswd123</Value> 
            <PlainText>true</PlainText> 
         </Password>
         <Username>Administrator</Username> 
         <Enabled>true</Enabled> 
         <LogonCount>5</LogonCount> 
      </AutoLogon>
      <UserAccounts>
         <AdministratorPassword>
            <Value>SecurePasswd123</Value> 
            <PlainText>true</PlainText> 
         </AdministratorPassword>
      </UserAccounts>
   </component>
```

为了防止无需内置管理员帐户输入的密码后完成的全新体验，设置 Microsoft Windows 外壳程序安装\\`UserAccounts` \\ `AdministratorPassword`在**oobeSystem**配置阶段。

以下 XML 输出显示如何设置适当的值︰

``` syntax
            <UserAccounts>
                <AdministratorPassword>
                    <Value>SecurePasswd123</Value>
                    <PlainText>true</PlainText>
                </AdministratorPassword>
            </UserAccounts>
```

对于 Windows Server® 2012年，内置的管理员首次登录时必须更改密码。 这样可以防止内置管理员帐户具有空白密码默认情况下。

### <a name="span-idlogonusingauditmodespanspan-idlogonusingauditmodespanspan-idlogonusingauditmodespanlog-on-by-using-audit-mode"></a><span id="LogOnUsingAuditMode"></span><span id="logonusingauditmode"></span><span id="LOGONUSINGAUDITMODE"></span>使用审核模式下登录

如果计算机尚未办通过的全新体验 (OOBE)，您可以输入内置的管理员帐户重新进入审核模式。 有关详细信息，请参阅[启动到审核模式或 OOBE 的 Windows](boot-windows-to-audit-mode-or-oobe.md)。

### <a name="span-idusemmcconsolespanspan-idusemmcconsolespanspan-idusemmcconsolespanuse-the-local-users-and-groups-mmc-server-versions-only"></a><span id="UseMMCConsole"></span><span id="usemmcconsole"></span><span id="USEMMCCONSOLE"></span>使用本地用户和组 MMC （仅服务器版本）

通过使用本地用户和组 Microsoft 管理控制台 (MMC) 更改管理员帐户的属性。

1.  打开 MMC，然后选择**本地用户和组**。

2.  右键单击**管理员**帐户，然后选择**属性**。

    **管理员属性**窗口将显示。

3.  在**常规**选项卡上清除**帐户已停用**复选框。

4.  关闭 MMC。

现在启用管理员访问权限。

## <a name="span-iddisablingthebuilt-inadministratoraccountspanspan-iddisablingthebuilt-inadministratoraccountspanspan-iddisablingthebuilt-inadministratoraccountspandisabling-the-built-in-administrator-account"></a><span id="Disabling_the_Built-in_Administrator_Account"></span><span id="disabling_the_built-in_administrator_account"></span><span id="DISABLING_THE_BUILT-IN_ADMINISTRATOR_ACCOUNT"></span>禁用内置管理员帐户


为新的安装，在 OOBE，最终用户创建了用户帐户后将禁用内置管理员帐户。

对于升级安装，内置管理员帐户保持启用以及计算机未加入到域的计算机上，没有任何其他活动的本地管理员时。

**使用以下方法之一禁用内置管理员帐户︰**

1.  **运行 sysprep/一般化命令**

    当您运行**sysprep 一般化 /**命令，下次计算机启动时，内置的管理员帐户将被禁用。

2.  **使用 net user 命令**

    运行以下命令来禁用管理员帐户︰

    ``` syntax
    net user administrator /active:no
    ```

    您可以配置计算机之后, 并在将计算机交付给客户之前运行此命令。

原始设备制造商 (Oem) 和系统构建者需要在将计算机交付给客户之前禁用内置管理员帐户。 若要执行此操作，可以使用下列方法之一。

## <a name="span-idconfiguringthebuilt-inadministratorpasswordspanspan-idconfiguringthebuilt-inadministratorpasswordspanspan-idconfiguringthebuilt-inadministratorpasswordspanconfiguring-the-built-in-administrator-password"></a><span id="Configuring_the_Built-in_Administrator_Password"></span><span id="configuring_the_built-in_administrator_password"></span><span id="CONFIGURING_THE_BUILT-IN_ADMINISTRATOR_PASSWORD"></span>配置内置管理员密码


**说明**

-   当您运行**sysprep 一般化 /**上 Windows Server 2012 和 Windows Server 2008 R2，Sysprep 工具命令将内置管理员帐户密码重置。 Sysprep 工具仅清除服务器版本，不能为客户端版本的内置管理员帐户的密码。 下次计算机启动时，安装程序将显示密码提示。

    **请注意**  
    在 Windows Server 2012，Windows Server 2008 R2 和 Windows Server 2008 中，默认密码策略要求对所有用户帐户使用强密码。 若要配置一个弱密码，可以使用答案文件包含 Microsoft Windows 的外壳程序-安装\\`UserAccounts` \\ `AdministratorPassword`设置。 手动或使用脚本，如**net user**命令，则不能配置一个弱密码。

     

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Windows 部署选项](windows-deployment-options.md)

[审核模式概述](audit-mode-overview.md)

 

 






