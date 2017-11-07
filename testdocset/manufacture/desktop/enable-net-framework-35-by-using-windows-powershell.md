---
author: Justinha
Description: "通过使用 Windows PowerShell 启用.NET Framework 3.5"
ms.assetid: af189974-cffa-46d9-950a-40f5e28d378f
MSHAttr: PreferredLib:/library/windows/hardware
title: "通过使用 Windows PowerShell 启用.NET Framework 3.5"
ms.openlocfilehash: 47447b9e70763eb5242e29851584c458b23baf07
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="enable-net-framework-35-by-using-windows-powershell"></a>通过使用 Windows PowerShell 启用.NET Framework 3.5


没有连接到互联网对于 Windows Server® 2012年核心安装，您可以使用 Windows PowerShell 添加.NET Framework 3.5 和引荐给**\\源\\sxs**安装介质上的文件夹。 **\\源\\sxs**可以将文件夹复制到网络共享 (例如， \\\\网络\\共享\\sxs) 以使其能够方便地访问多台计算机。 目标计算机帐户域\\服务器名称 $ 必须至少拥有读访问权限的网络共享。

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>要求


-   Windows Server 2012

-   安装介质

-   用户的管理员权限。 当前用户必须是本地的管理员组的成员才能添加或删除 Windows 功能。

-   目标计算机可能需要的网络访问和使用备用源或 Internet 连接使用 Windows Update 权限。

## <a name="span-idstepsspanspan-idstepsspanspan-idstepsspansteps"></a><span id="Steps"></span><span id="steps"></span><span id="STEPS"></span>步骤


1.  启动 Windows PowerShell 中管理员命令提示符下键入︰

    ``` syntax
    powershell
    ```

2.  若要从位于网络共享上的安装媒体中安装.NET Framework 3.5，使用下面的命令︰

    ``` syntax
    Install-WindowsFeature Net-Framework-Core -source \\network\share\sxs
    ```

    其中*\\\\网络\\共享\\sxs*是源文件的位置。

    有关安装 WindowsFeature cmdlet 的详细信息，请参阅[安装 WindowsFeature](http://go.microsoft.com/fwlink/p/?linkid=329977)。

3.  要验证安装，请运行以下命令︰

    ``` syntax
    Get-WindowsFeature
    ```

    **安装状态**列应显示**已安装**的**.NET Framework 3.5 （包括.NET 2.0 和 3.0）**功能。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Microsoft.NET Framework 3.5 部署注意事项](microsoft-net-framework-35-deployment-considerations.md)

 

 






