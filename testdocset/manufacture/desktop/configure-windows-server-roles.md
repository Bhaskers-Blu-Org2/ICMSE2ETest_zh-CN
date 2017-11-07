---
author: Justinha
Description: "配置 Windows 服务器角色"
ms.assetid: c7ad0ffa-30a5-4fb3-9e69-b70fed86b694
MSHAttr: PreferredLib:/library/windows/hardware
title: "配置 Windows 服务器角色"
ms.openlocfilehash: dd62bd2ceb8cb33b90bf0cdd90d6eaefd2134a9b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="configure-windows-server-roles"></a>配置 Windows 服务器角色


要在无人参与安装期间配置一个或多个服务器角色，您可以使用 PowerShell 或服务器管理器命令行工具。 有关服务器角色的详细信息，请参阅此[Microsoft Web 站点上](http://go.microsoft.com/fwlink/?LinkId=140100)。

您可以创建`FirstLogonCommands`要在答案文件中指定服务器角色的正确参数进行配置。 `FirstLogonCommands`在[oobeSystem](oobesystem.md)配置阶段中配置设置。 `FirstLogonCommands`在用户登录到计算机，并显示桌面之前后立即运行时设置。

**请注意**  
您必须拥有管理员权限的帐户运行 PowerShell 和服务器管理器命令。

 

有关添加`FirstLogonCommands`设置，请参阅[添加到答案文件中自定义命令](https://msdn.microsoft.com/library/windows/hardware/dn915058)。

下面的示例演示 PowerShell.exe ServerManager 模块和 DHCP、 传真、 DNS 和文件服务角色的安装。

``` syntax
<FirstLogonCommands>
   <SynchronousCommand wcm:action="add">
      <Order>1</Order>
      <CommandLine> Powershell.exe –command Import-Module ServerManager; Install-WindowsFeature DHCP,FAX,DNS,File-Services</CommandLine>
      <Description>Configure Server Role</Description>
   </SynchronousCommand>
</FirstLogonCommands>
```

**请注意**  
不是所有的服务器角色支持 Sysprep。 映像和部署后，您必须配置某些服务器角色。 有关详细信息，请参阅[Sysprep 支持的服务器角色](sysprep-support-for-server-roles.md)。

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Windows 部署选项](windows-deployment-options.md)

 

 






