---
author: kpacquer
Description: "部署和测试 MMO 在用户模式下测试应用程序"
ms.assetid: f8a7c14f-66b6-4023-86cb-c10bc3f52734
MSHAttr: PreferredLib:/library/windows/hardware
title: "部署和测试 MMO 在用户模式下测试应用程序"
ms.openlocfilehash: 9cdb6abfb13eab870c71976b58a7f20aeb6aebe0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="deploy-and-test-a-user-mode-test-application-in-mmos"></a>部署和测试 MMO 在用户模式下测试应用程序


若要将文件复制到一个 MMO 图像并运行程序，可以通过虚拟以太网连接使用 FTP 和远程登录。

**重要**  
不制造或零售服务中必须使用的 USB 驱动程序和此处所述的协议。 它们是有关工程的提出提供方便。

 

## <a name="span-idpreparingthedevicespanspan-idpreparingthedevicespanspan-idpreparingthedevicespanpreparing-the-device"></a><span id="Preparing_the_device"></span><span id="preparing_the_device"></span><span id="PREPARING_THE_DEVICE"></span>准备设备


工程版本的 os 通常包括 Ping、 FTP 和 Telnet 服务器。 要确认这些是操作系统中处于活动状态，请检查启动配置或建立与 MMO 查看已加载的文件的调试连接。

将设备通过 USB 支持 TCP/IP 配置，必须安装必要的工具，并使用 BCDEdit 工具来修改 BCD 文件中存储的设备的启动选项。

## <a name="span-idrunningvirtualethernetanddeterminingtheipaddressofthedevicespanspan-idrunningvirtualethernetanddeterminingtheipaddressofthedevicespanspan-idrunningvirtualethernetanddeterminingtheipaddressofthedevicespanrunning-virtual-ethernet-and-determining-the-ip-address-of-the-device"></a><span id="Running_Virtual_Ethernet_and_determining_the_IP_address_of_the_device"></span><span id="running_virtual_ethernet_and_determining_the_ip_address_of_the_device"></span><span id="RUNNING_VIRTUAL_ETHERNET_AND_DETERMINING_THE_IP_ADDRESS_OF_THE_DEVICE"></span>运行虚拟以太网和确定该设备的 IP 地址


虚拟以太网的电脑上创建设备的 USB 连接和 TCP/IP 传输之间的连接。 将设备连接或打开其电源，PC 上启动虚拟以太网。 VirtEth.exe 位于"%programfiles(x86)%\\Microsoft Windows Phone 8 KDBG 连接\\bin"文件夹。

虚拟以太网控制台窗口将打开。 使该窗口保持打开状态以保持连接的移动电话;关闭窗口会关闭连接。

1.  虚拟以太网运行时，连接，并接通电话。 当设备连接时，您会看到输出行包含设备的 MAC 地址。 虚拟以太网报告设备的 MAC 地址与下面类似的输出︰

    ``` syntax
    NIC UP: 00-11-38-EA-88-7E : SUCCESS
    ```

    请注意 12 位设备 VirtEth 控制台窗口中的 MAC 地址并使用它的下一步确定设备的 TCP/IP 的地址。

2.  打开一个新的命令提示符窗口并键入**arp-a**。 将显示类似以下的输出。

    ``` syntax
    C:\>arp -a

    Interface: 10.178.1.40 --- 0xb
      Internet Address      Physical Address      Type
      10.178.0.1            cc-ef-48-a7-6f-3f     dynamic
      10.178.1.94           00-11-38-ea-88-7e     dynamic
      10.178.3.255          ff-ff-ff-ff-ff-ff     static
      ... 
    ```

使用与设备连接到通过 FTP 和 Telnet 设备的 MAC 地址关联的 IP 地址。

## <a name="span-idestablishinganftpconnectionspanspan-idestablishinganftpconnectionspanspan-idestablishinganftpconnectionspanestablishing-an-ftp-connection"></a><span id="Establishing_an_FTP_connection"></span><span id="establishing_an_ftp_connection"></span><span id="ESTABLISHING_AN_FTP_CONNECTION"></span>建立 FTP 连接


若要浏览和复制通过 FTP 文件︰

-   打开 Windows 资源管理器，然后键入︰ **FTP:\\**在地址栏中，使用该设备的 IP 地址替换*W.X.Y.Z* *W.X.Y.Z* 。

您应该看到列出的设备上的文件。 使用 Windows 资源管理器将文件复制到或从该设备，可执行的测试程序和测试结果的日志。

若要关闭 FTP 连接，请通过选择 Windows 通知区域中的**安全删除硬件**卸载电话文件系统。

## <a name="span-idestablishingatelnetsessionspanspan-idestablishingatelnetsessionspanspan-idestablishingatelnetsessionspanestablishing-a-telnet-session"></a><span id="Establishing_a_Telnet_session"></span><span id="establishing_a_telnet_session"></span><span id="ESTABLISHING_A_TELNET_SESSION"></span>建立 Telnet 会话


请确保在计算机上启用 Telnet。 若要在 Windows 操作系统中启用远程登录，请选择**控制面板** &gt; **程序和功能** &gt; **打开或关闭 Windows 功能**。 在 Windows 功能列表中，选择**Telnet 客户端**，，然后单击**确定**。

与设备建立 Telnet 会话︰

-   打开一个命令提示符窗口并键入︰ **telnet** *W.X.Y.Z*， *W.X.Y.Z*替换设备的 IP 地址

出现命令提示符窗口是 cmd.exe 设备上运行。 该命令提示符下，可以在设备上，如执行包括在 MMO 映像的测试应用程序来运行命令。

## <a name="span-idtroubleshootingconfirmingtcpipconnectivityspanspan-idtroubleshootingconfirmingtcpipconnectivityspanspan-idtroubleshootingconfirmingtcpipconnectivityspantroubleshooting-confirming-tcpip-connectivity"></a><span id="Troubleshooting__Confirming_TCP_IP_connectivity"></span><span id="troubleshooting__confirming_tcp_ip_connectivity"></span><span id="TROUBLESHOOTING__CONFIRMING_TCP_IP_CONNECTIVITY"></span>故障排除︰ 确认 TCP/IP 连接


您可以使用**ping**测试与此设备的 TCP/IP 连接︰

-   打开一个命令提示符窗口并键入︰ **ping***W.X.Y.Z*， *W.X.Y.Z*替换设备的 IP 地址

该命令应指示返回数据包。 如果这不起作用，一个常见的问题进行调查是在计算机上的防火墙配置。

## <a name="span-iddebugginginmmosspanspan-iddebugginginmmosspanspan-iddebugginginmmosspandebugging-in-mmos"></a><span id="Debugging_in_MMOS"></span><span id="debugging_in_mmos"></span><span id="DEBUGGING_IN_MMOS"></span>在 MMO 调试


若要启用调试器支持在 MMO，通信和操作系统设置，必须修改。

### <a name="span-idenablingdebugsupportspanspan-idenablingdebugsupportspanspan-idenablingdebugsupportspanenabling-debug-support"></a><span id="Enabling_debug_support"></span><span id="enabling_debug_support"></span><span id="ENABLING_DEBUG_SUPPORT"></span>启用调试支持

要启用调试支持在 MMO，在 MfgOEMInput.xml 文件中指定以下内部的可选功能。

``` syntax
<Microsoft>
  ...
  <Feature>KDNETUSB_ON</Feature>
   ...
</Microsoft>
```

这增加的 MMO 图像所需的程序包。 有关如何使用 MfgOEMInput.xml 文件的详细信息，请参阅[MMO 图像定义](mmos-image-definition.md)。

### <a name="span-idenablingcommunicationsettingsspanspan-idenablingcommunicationsettingsspanspan-idenablingcommunicationsettingsspanenabling-communication-settings"></a><span id="Enabling_communication_settings"></span><span id="enabling_communication_settings"></span><span id="ENABLING_COMMUNICATION_SETTINGS"></span>启用通信设置

若要启用操作系统，图像被快闪后必须更改通信设置。

### <a name="span-idestablishingthedebugconnectionspanspan-idestablishingthedebugconnectionspanspan-idestablishingthedebugconnectionspanestablishing-the-debug-connection"></a><span id="Establishing_the_debug_connection"></span><span id="establishing_the_debug_connection"></span><span id="ESTABLISHING_THE_DEBUG_CONNECTION"></span>建立调试连接

要调试连接 MMO，使用 WinDbg 指定密钥和使用 BCDEdit 早先配置的端口。

``` syntax
windbg.exe -k net:Port=50000,Key=1.2.3.4
```

 

 





