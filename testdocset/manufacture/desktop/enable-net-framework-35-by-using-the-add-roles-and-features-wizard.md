---
author: Justinha
Description: "通过使用添加角色和功能向导启用.NET Framework 3.5"
ms.assetid: 08b011c7-7f15-4fd5-9a19-c99249e4f642
MSHAttr: PreferredLib:/library/windows/hardware
title: "通过使用添加角色和功能向导启用.NET Framework 3.5"
ms.openlocfilehash: fb6f73220f86e4cd4e0891dbb98eae41de909970
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="enable-net-framework-35-by-using-the-add-roles-and-features-wizard"></a>通过使用添加角色和功能向导启用.NET Framework 3.5


可以使用服务器管理器来启用 Windows Server 2012 R2 的本地或远程安装的.NET Framework 3.5。

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>要求


-   Windows Server 2012 R2

-   安装介质

-   用户的管理员权限。 当前用户必须是本地的管理员组的成员才能添加或删除 Windows 功能。

-   目标计算机可能需要的网络访问和使用备用源或 Internet 连接使用 Windows Update 权限。

## <a name="span-idstepsspanspan-idstepsspanspan-idstepsspansteps"></a><span id="Steps"></span><span id="steps"></span><span id="STEPS"></span>步骤


1.  在服务器管理器中，单击**管理**，然后选择**添加角色和功能**启动添加角色和功能向导。

2.  在**选择安装类型**屏幕中，选择**基于角色或功能的安装**。

3.  选择目标服务器。

4.  在**选择功能**屏幕上，旁边的复选框**.Net Framework 3.5 的功能**。

5.  **确认安装选择**屏幕上将显示警告询问**您需要指定一个备用源路径？**。 如果目标计算机不能访问 Windows 更新，请单击指定的路径**指定一个备用源路径**链接**\\源\\sxs**安装介质上的文件夹，然后单击**确定**。 您指定的备用源后或目标计算机有权访问 Windows 更新，单击警告，旁边的**X** ，然后单击**安装**。

    如果您使用服务器管理器中 Windows Server 2012 将角色或功能添加到远程服务器，远程服务器的计算机帐户 (域\\ComputerName$) 因为部署操作在目标服务器上运行系统环境中需要访问备用源的文件路径。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Microsoft.NET Framework 3.5 部署注意事项](microsoft-net-framework-35-deployment-considerations.md)

 

 






