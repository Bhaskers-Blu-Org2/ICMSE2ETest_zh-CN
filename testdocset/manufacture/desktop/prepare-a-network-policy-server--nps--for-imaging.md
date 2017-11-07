---
author: Justinha
Description: "网络策略服务器 (NPS) 准备映像"
ms.assetid: 7ac7f98a-f3db-4c54-a56a-fe766beb4344
MSHAttr: PreferredLib:/library/windows/hardware
title: "网络策略服务器 (NPS) 准备映像"
ms.openlocfilehash: 7f8bfda08005d1295576a3c26b901a0577542d6a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="prepare-a-network-policy-server-nps-for-imaging"></a>网络策略服务器 (NPS) 准备映像


如果您想要创建的安装程序部署到另一台计算机的映像，在源服务器上安装网络策略服务器 (NPS) 服务，您可能需要先删除存储在该服务器的机密信息。 使用这些过程来从 NPS 配置中删除相关的设置和数据。

**若要删除从 NPS 配置为 RADIUS 客户端**

1.  在 NPS 服务器上显示列表中的远程身份验证拨入用户服务 (RADIUS) 客户端。 要做到这一点，打开提升的命令提示符下，键入以下命令，然后按 enter 键︰

    ``` syntax
    Netsh nps show client
    ```

2.  删除每个 RADIUS 客户端列表中。 为此，在提升的命令提示符下，键入以下命令，然后按 enter 键︰

    ``` syntax
    Netsh nps delete client [name]
    ```

    例如，该命令将删除名为的 RADIUS 客户端*&lt;WirelessAP1&gt;*从 NPS 服务器配置︰

    ``` syntax
    Netsh nps delete client name = <WirelessAP1>
    ```

    通过插入每个客户端间的逗号，您可以删除多个 RADIUS 客户端。 例如︰

    ``` syntax
    Netsh nps delete client name = <WirelessAP1>,<WirelessAP2>,<WirelessAP3>
    ```

    您还可以通过使用下面的命令删除 RADIUS 客户端。

    ``` syntax
    Remove-NpsRadiusClient [-Name] <Radius Client Name>-
    ```

3.  为每个 RADIUS 客户端配置 NPS 服务器上重复此过程。

**若要删除从 NPS 服务器配置远程 RADIUS 服务器组**

1.  显示配置 NPS 服务器的远程 RADIUS 服务器组的列表。 要做到这一点，打开提升的命令提示符下，键入以下命令，然后按 enter 键︰

    ``` syntax
    Netsh nps show remoteservergroup
    ```

2.  删除列表中的每个远程服务器组。 为此，在提升的命令提示符下，键入以下命令，然后按 enter 键︰

    ``` syntax
    Netsh nps delete remoteservergroup [name =] name
    ```

    例如，该命令将删除远程 RADIUS 服务器组名为*&lt;RemoteServers1&gt;*从 NPS 服务器配置︰

    ``` syntax
    Netsh nps delete remoteservergroup name = <RemoteServers1>
    ```

    **请注意**  
    删除远程 RADIUS 服务器组时，将删除所有包含在组中的 RADIUS 服务器。

     

3.  NPS 服务器上配置每个远程 RADIUS 服务器组重复此过程。

您可以将**Netsh**命令转换为 Windows PowerShell® 命令。 有关详细信息，请参阅[Netshell 到 Powershell 转换指南 》](http://go.microsoft.com/fwlink/?LinkId=234734)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[配置 Windows 服务器角色](configure-windows-server-roles.md)

[Sysprep （通用化） Windows 安装](sysprep--generalize--a-windows-installation.md)

[Windows 服务器的部署选项](windows-server-deployment-options.md)

 

 






