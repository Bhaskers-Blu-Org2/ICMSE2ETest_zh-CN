---
author: Justinha
Description: "Windows 安装程序状态"
ms.assetid: f67b1396-b2a5-4ac1-8104-7188e5cff54c
MSHAttr: PreferredLib:/library/windows/hardware
title: "Windows 安装程序状态"
ms.openlocfilehash: a3cef06c11e28eff172e69249d205c36b91cb4ae
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-setup-states"></a>Windows 安装程序状态


有几个在安装过程中分配给 Windows® 图像的状态。 此状态信息可以用于不同的状态和阶段的 Windows 安装程序自动检测。

## <a name="span-idwindowssetupstatesspanspan-idwindowssetupstatesspanspan-idwindowssetupstatesspanwindows-setup-state-information"></a><span id="WindowsSetupStates"></span><span id="windowssetupstates"></span><span id="WINDOWSSETUPSTATES"></span>Windows 安装程序状态信息


在两个位置、 注册表和文件中存储 Windows 映像的状态。

-   注册表中︰

    键︰ **HKEY\_本地\_机\\软件\\Microsoft\\Windows\\CurrentVersion\\安装程序\\状态**

    类型︰ REG\_SZ

    值︰ *StateName*

-   文件中︰

    文件: %WINDIR%\\安装程序\\状态\\State.ini

    部分︰\[状态\]

    值︰ *StateName*

下表描述存在*StateName*的值。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">状态名称</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>IMAGE_STATE_COMPLETE</p></td>
<td align="left"><p>已成功安装映像。 <strong>专门负责</strong>和<strong>oobeSystem</strong>配置阶段已完成。 此图像不部署到的计算机，因为它现在是依赖于硬件，都有不同的硬件配置。 若要将此映像部署到具有不同硬件配置的计算机，您必须运行<strong>sysprep 一般化 /</strong>。</p></td>
</tr>
<tr class="even">
<td align="left"><p>IMAGE_STATE _UNDEPLOYABLE</p></td>
<td align="left"><p>Windows 安装程序尚未完成一个给定阶段处于默认状态的图像。 如果返回的值 IMAGE_STATE 和 IMG_UNDEPLOYABLE 处理查询，则镜像将处于以下状态之一︰</p>
<ul>
<li><p>安装程序当前正在运行，且尚未完全完成的阶段。 给定的阶段完成后，IMAGE_STATE 将设置为适当的完成值。</p></li>
<li><p>如果安装程序未运行时联机查询，当完成安装阶段时失败。 必须重新安装此映像。</p></li>
<li><p>如果脱机查询，图像未完成某一阶段，并将永远不会部署。</p></li>
</ul></td>
</tr>
<tr class="odd">
<td align="left"><p>IMAGE_STATE_GENERALIZE_RESEAL_TO_OOBE</p></td>
<td align="left"><p>该图像已成功完成的<strong>一般化</strong>配置阶段，并将继续到<strong>OOBEsystem</strong>配置阶段中，安装程序启动时。</p></td>
</tr>
<tr class="even">
<td align="left"><p>IMAGE_STATE_GENERALIZE_RESEAL_TO_AUDIT</p></td>
<td align="left"><p>该图像已成功完成的<strong>一般化</strong>配置阶段，并将继续到审核模式下启动安装程序时。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>IMAGE_STATE_SPECIALIZE_RESEAL_TO_OOBE</p></td>
<td align="left"><p>已成功完成的<strong>专门</strong>处理图像，并将继续到<strong>OOBEsystem</strong>配置阶段中，安装程序启动时。</p></td>
</tr>
<tr class="even">
<td align="left"><p>IMAGE_STATE_SPECIALIZE_RESEAL_TO_AUDIT</p></td>
<td align="left"><p>该图像已成功完成在<strong>specialize</strong>配置阶段，并将继续到审核模式下启动安装程序时。</p></td>
</tr>
</tbody>
</table>

 

下面的示例演示如何访问状态信息。

-   从注册表访问状态信息︰

    ``` syntax
    C:\>reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Setup\State /v Imag
    eState

    HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Setup\State
        ImageState    REG_SZ    IMAGE_STATE_SPECIALIZE_RESEAL_TO_OOBE
    ```

-   从文件访问状态信息︰

    ``` syntax
    C:\>type %windir%\Setup\State\State.ini
    [State]
    ImageState="IMAGE_STATE_SPECIALIZE_RESEAL_TO_OOBE"
    ```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Windows 安装程序命令行选项](windows-setup-command-line-options.md)

[Windows 安装程序版本配置和产品 ID 文件 （EI.cfg 和 PID.txt）](windows-setup-edition-configuration-and-product-id-files--eicfg-and-pidtxt.md)

[Windows 安装程序日志文件和事件日志](windows-setup-log-files-and-event-logs.md)

 

 






