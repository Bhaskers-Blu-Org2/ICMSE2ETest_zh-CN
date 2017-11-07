---
author: Justinha
Description: "WinPE︰ 存储区域网络 (SAN) 策略"
ms.assetid: fb9b42b2-432e-4c88-9973-4d9d832645df
MSHAttr: PreferredLib:/library/windows/hardware
title: "WinPE︰ 存储区域网络 (SAN) 策略"
ms.openlocfilehash: efd546b56510f7bc295b6b758c2bcdd286de3894
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="winpe-storage-area-network-san-policy"></a>WinPE︰ 存储区域网络 (SAN) 策略


存储区域网络 (SAN) 的功能允许计算机从其他计算机自动装载磁盘和其他存储设备。 通过在 Windows 预安装环境 (Windows PE) 映像上配置 SAN 策略，您可以控制自动装载磁盘并且可以装载哪些磁盘。 您还可以禁用自动装载磁盘的策略。

## <a name="span-idconfiguringthesanpolicyonawindowspeimagespanspan-idconfiguringthesanpolicyonawindowspeimagespanspan-idconfiguringthesanpolicyonawindowspeimagespanconfiguring-the-san-policy-on-a-windows-pe-image"></a><span id="Configuring_the_SAN_policy_on_a_Windows_PE_image"></span><span id="configuring_the_san_policy_on_a_windows_pe_image"></span><span id="CONFIGURING_THE_SAN_POLICY_ON_A_WINDOWS_PE_IMAGE"></span>在 Windows PE 映像上配置 SAN 策略


对于 Windows 评估和部署工具包 (Windows ADK) 中可用的 Windows PE 映像，默认 SAN 策略是自动装入可用磁盘。 但如果对 SAN 环境具有多个可用磁盘，自动挂载它们可能会降低 Windows PE 的性能。 容器 ID 确定外部和内部磁盘的状态。 磁盘设备容器 ID 是根容器 ID 相同，如果是内部磁盘。 否则，它是一个外部磁盘。 Windows PE 工具路径中的 Setsanpolicy.cmd 文件可用于在 Windows PE 映像上配置 SAN 策略。

**若要在 Windows PE 映像上配置 SAN 策略**

1.  Windows PE 映像装载到一个可用的装入点。 例如︰

    ``` syntax
    Dism /mount-image /imagefile:C:\winpe_x86\ISO\sources\boot.wim /index:<image_index> /mountdir:C:\winpe_x86\mount
    ```

    其中*&lt;图像\_索引&gt;*是.wim 文件中的所选图像的数字。

2.  运行**setsanpolicy**命令。 例如︰

    ``` syntax
    Setsanpolicy.cmd <image_path> <policy_number>
    ```

    其中*&lt;图像\_路径&gt;*是已装载的 Windows PE 映像的路径和*&lt;策略\_号&gt;*是 SAN 策略编号。

    这些值是有效的*&lt;策略\_号&gt;*的值︰

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left">SAN 策略编号</th>
    <th align="left">说明</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><p>1</p></td>
    <td align="left"><p>安装所有可用的存储设备。</p>
    <p>这是默认值。</p></td>
    </tr>
    <tr class="even">
    <td align="left"><p>2</p></td>
    <td align="left"><p>装载除共享总线上的所有存储设备。</p></td>
    </tr>
    <tr class="odd">
    <td align="left"><p>3</p></td>
    <td align="left"><p>不能装载存储设备。</p></td>
    </tr>
    <tr class="even">
    <td align="left"><p>4</p></td>
    <td align="left"><p>新的 Windows 8。 将内部磁盘脱机。</p>
    <div class="alert">
    <strong>请注意</strong>  
    <p>所有外部磁盘并启动磁盘均为联机。</p>
    </div>
    <div>
     
    </div></td>
    </tr>
    </tbody>
    </table>

    此示例演示如何配置 SAN 策略上的 Windows PE 映像装载共享总线上的所有磁盘，这些磁盘除外︰

        Setsanpolicy C:\winpe_x86\mount <2>

    其中*&lt;2&gt;*是 SAN 策略数，装载除共享总线上的所有存储设备。

3.  卸载映像并提交更改。 例如︰

    ``` syntax
    Dism /unmount-image /mountdir:C:\winpe_x86\mount /commit
    ```

## <a name="span-idconfiguringthesanpolicyonawindowsimagespanspan-idconfiguringthesanpolicyonawindowsimagespanspan-idconfiguringthesanpolicyonawindowsimagespanconfiguring-the-san-policy-on-a-windows-image"></a><span id="Configuring_the_SAN_Policy_on_a_Windows_Image"></span><span id="configuring_the_san_policy_on_a_windows_image"></span><span id="CONFIGURING_THE_SAN_POLICY_ON_A_WINDOWS_IMAGE"></span>在 Windows 映像上配置 SAN 策略


通过使用 Windows 系统映像管理器 (Windows SIM) 来自定义 Microsoft 的 Windows PartitionManager 组件，可以更改默认的 SAN 策略的 Windows 映像。 使用`SanPolicy`设置为在无人参与安装期间配置的 Windows 映像。

**若要通过使用应答文件来配置 SAN 策略**

1.  技术人员计算机上打开 Windows 系统映像管理器 （Windows sim 卡）。 单击**开始**，键入**Windows 系统映像管理器**，然后选择**Windows 系统映像管理器**。

2.  创建新的应答文件，或更新现有的应答文件。 有关详细信息，请参阅[创建或打开答案文件](https://msdn.microsoft.com/library/windows/hardware/dn915085)和[创作答案文件的最佳做法](https://msdn.microsoft.com/library/windows/hardware/dn915073)。

3.  单击**插入**菜单上的**RunSynchronous**。

4.  选择想要安装命令的配置阶段。 这可能是在[auditUser](audituser.md)或[oobeSystem](oobesystem.md)配置阶段。

    **请注意**  
    不要在[specialize](specialize.md)配置阶段中使用**RunSynchronousNetsh 由**命令。

    **创建同步命令**对话框中出现。

5.  输入**由防火墙 Netsh**命令，将它们添加到答案文件中，然后再单击**确定**。

    有关详细信息，请参阅[网络外壳程序 (Netsh) 技术参考](http://go.microsoft.com/fwlink/?LinkId=234733)。 您可以将**Netsh**命令转换为 Windows PowerShell® 命令。 有关详细信息，请参阅[Netshell 到 Powershell 转换指南 》](http://go.microsoft.com/fwlink/?LinkId=234734)。

6.  在**SynchronousCommand 属性**窗格中的**说明**，旁边的**设置**部分中，输入**启用 Windows Messenger**等说明。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[对于 Windows 10 WinPE](winpe-intro.md)

[WinPE︰ 安装和自定义](winpe-mount-and-customize.md)

[WinPE 网络驱动程序︰ 初始化和添加驱动程序](winpe-network-drivers-initializing-and-adding-drivers.md)

[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)

[配置无人参与安装中的网络设置](configure-network-settings-in-an-unattended-installation.md)

[Windows 部署选项](windows-deployment-options.md)

 

 






