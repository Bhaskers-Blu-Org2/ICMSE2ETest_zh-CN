---
author: Justinha
Description: "WinPE 网络驱动程序︰ 初始化和添加驱动程序"
ms.assetid: 36eba03c-ba15-4b34-b1cb-fd83cad08d63
MSHAttr: PreferredLib:/library/windows/hardware
title: "WinPE 网络驱动程序︰ 初始化和添加驱动程序"
ms.openlocfilehash: 5e425e9f82edbd9e998b6eedc840c6d73fb13904
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="winpe-network-drivers-initializing-and-adding-drivers"></a>WinPE 网络驱动程序︰ 初始化和添加驱动程序


一旦启动 WinPE，Wpeutil 命令初始化 Windows PE (WinPE) 网络驱动程序。 默认 WinPE 映像支持许多流行的网络适配器，并支持许多相同网络与 Windows.Windows PE 命令包括一套基本的许多流行的网络适配器，网络驱动程序和支持许多像 Windows 那样相同的网络命令。

连接到文件服务器的受支持的方法是通过 TCP/IP TCP/IP 和 NetBIOS。 Windows PE 不支持其他方法，如网间数据包交换/已排序数据包交换 (IPX/SPX) 网络协议。

Windows PE 支持的独立命名空间的分布式文件系统 (DFS) 名称解析。 它不支持域命名空间。 为 DFS 命名空间仅存在于本地计算机，因此不能使用 Active Directory® 域服务 (AD DS) 允许独立的 DFS 命名空间。

不支持在 IPv6 网络上的 Windows PE 连接到 IPv4 网络。

**若要连接到另一台计算机或网络上的共享的文件夹**

1.  在 Windows PE 中，您可以连接 （或映射） 到共享的网络文件夹使用[net use](http://technet.microsoft.com/library/bb490717.aspx)命令。 如果您正在连接到加入域的计算机，Windows PE 将提示输入用户名和密码。

    ``` syntax
    net use n: \\server\share
    ```

2.  此外可以从网络主机 Windows PE，使用预启动执行环境 (PXE)，它是[Windows 部署服务](http://technet.microsoft.com/library/hh831764)的一部分。

**网络问题的疑难解答**

1.  尝试添加网络设备的驱动程序。

    我们建议[WinPE︰ 安装和自定义](winpe-mount-and-customize.md)，尤其是对于任何驱动程序在安装过程中需要重新启动。

    您还可以使用[Drvload 命令行选项](drvload-command-line-options.md)来运行 Windows PE 时加载某些驱动程序。 但是，在安装过程中对注册表所做的任何更新将不会保留在重启后即使 Windows PE 运行[WinPE︰ 硬驱动器 （平面引导或非 RAM） 上安装](winpe-install-on-a-hard-drive--flat-boot-or-non-ram.md)。

2.  运行[Wpeinit 和 Startnet.cmd︰ 使用 WinPE 启动脚本](wpeinit-and-startnetcmd-using-winpe-startup-scripts.md)初始化网络。 默认情况下，Windows PE 启动时，将运行 wpeinit。

3.  在某些情况下，您可能需要配置防火墙设置，在您尝试连接到 PC 上。 Windows PE 支持[IPSec 配置](http://go.microsoft.com/fwlink/p/?linkid=81713)。

4.  请注意，您不能将 Windows PE 加入到域中，或作为服务器运行 Windows PE。 有关详细信息，请参阅[WinPE 的 Windows 10](winpe-intro.md)。

**若要连接到有线网络使用 802.1 x 身份验证协议**

1.  创建包含**WinPE Dot3Svc**可选组件的自定义 Windows PE 映像。

2.  引导到 Windows PE 的一台电脑。

3.  启动 dot3svc 服务。

    ``` syntax
    net start dot3svc
    ```

4.  添加一个 LAN 配置文件。 例如︰

    ``` syntax
    netsh lan add profile="G:\EthernetLANProfile.xml"
    ```

    LAN 配置文件的示例︰

    ``` syntax
    <?xml version="1.0"?>
    <!-- Sample LAN profile: EthernetLANProfile.xml" -->
    <LANProfile xmlns="http://www.microsoft.com/networking/LAN/profile/v1">
      <MSM>
        <security>
          <OneXEnforced>false</OneXEnforced>
          <OneXEnabled>true</OneXEnabled>
          <OneX xmlns="http://www.microsoft.com/networking/OneX/v1">
            <cacheUserData>true</cacheUserData>
            <authMode>user</authMode>
            <EAPConfig><EapHostConfig 
              xmlns="http://www.microsoft.com/provisioning/EapHostConfig"><EapMethod><Type 
              xmlns="http://www.microsoft.com/provisioning/EapCommon">25</Type><VendorId 
              xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorId><VendorType 
              xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorType><AuthorId 
              xmlns="http://www.microsoft.com/provisioning/EapCommon">0</AuthorId></EapMethod><Config 
              xmlns="http://www.microsoft.com/provisioning/EapHostConfig"><Eap 
              xmlns="http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1">
            <Type>25</Type><EapType 
              xmlns="http://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV1">
            <ServerValidation>
              <DisableUserPromptForServerValidation>false</DisableUserPromptForServerValidation>
              <ServerNames></ServerNames>
              <TrustedRootCA>1a 2b 3c 4d 56 78 90 aa bb cc dd ee ff 1a 2b 3c 4d 5e 6f</TrustedRootCA>
              </ServerValidation><FastReconnect>true</FastReconnect>
              <InnerEapOptional>false</InnerEapOptional><Eap 
                xmlns="http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1">
              <Type>26</Type><EapType 
                xmlns="http://www.microsoft.com/provisioning/MsChapV2ConnectionPropertiesV1">
              <UseWinLogonCredentials>false</UseWinLogonCredentials></EapType></Eap>
              <EnableQuarantineChecks>false</EnableQuarantineChecks>
              <RequireCryptoBinding>false</RequireCryptoBinding><PeapExtensions>
              <PerformServerValidation 
                xmlns="http://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV2">false
              </PerformServerValidation><AcceptServerName 
                xmlns="http://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV2">false
                </AcceptServerName><PeapExtensionsV2 
                xmlns="http://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV2">
              <AllowPromptingWhenServerCANotFound 
                xmlns="http://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV3">true
              </AllowPromptingWhenServerCANotFound></PeapExtensionsV2></PeapExtensions></EapType>
            </Eap></Config></EapHostConfig></EAPConfig>
          </OneX>
        </security>
      </MSM>
    </LANProfile>
    ```

5.  与配置文件的 EAP 用户数据链接。 例如︰

    ``` syntax
    netsh lan set eapuserdata filename="g:\EAP_UserData.xml" alluser=yes Interface="ethernet"
    ```

    EAP 用户数据文件示例︰

    ``` syntax
    <?xml version="1.0"?>
    <!-- Sample EAP user data: EAP_UserData.xml" -->
    <EapHostUserCredentials 
      xmlns="http://www.microsoft.com/provisioning/EapHostUserCredentials" 
      xmlns:eapCommon="http://www.microsoft.com/provisioning/EapCommon" 
      xmlns:baseEap="http://www.microsoft.com/provisioning/BaseEapMethodUserCredentials">
      <EapMethod>
        <eapCommon:Type>25</eapCommon:Type>
        <eapCommon:AuthorId>0</eapCommon:AuthorId>
      </EapMethod>
      <Credentials
        xmlns:eapUser="http://www.microsoft.com/provisioning/EapUserPropertiesV1" 
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
        xmlns:baseEap="http://www.microsoft.com/provisioning/BaseEapUserPropertiesV1" 
        xmlns:MsPeap="http://www.microsoft.com/provisioning/MsPeapUserPropertiesV1" 
        xmlns:MsChapV2="http://www.microsoft.com/provisioning/MsChapV2UserPropertiesV1">
        <baseEap:Eap>
          <baseEap:Type>25</baseEap:Type>
          <MsPeap:EapType>
            <MsPeap:RoutingIdentity>onex\administrator</MsPeap:RoutingIdentity>
            <baseEap:Eap>
              <baseEap:Type>26</baseEap:Type>
              <MsChapV2:EapType>
                <MsChapV2:Username>actualuser</MsChapV2:Username>
                <MsChapV2:Password>actualpassword</MsChapV2:Password>
                <MsChapV2:LogonDomain>actualdomain</MsChapV2:LogonDomain>
              </MsChapV2:EapType>
            </baseEap:Eap>
          </MsPeap:EapType>
        </baseEap:Eap>
      </Credentials>
    </EapHostUserCredentials>
    ```

6.  有关详细信息，请参阅[如何启用 802.1 仅限计算机的身份验证基于 X 网络在 Windows Vista 中，Windows Server 2008 中，和在 Windows XP 服务包 3](http://support.microsoft.com/kb/929847)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[对于 Windows 10 WinPE](winpe-intro.md)

[WinPE︰ 安装和自定义](winpe-mount-and-customize.md)

[Wpeinit 和 Startnet.cmd︰ 使用 WinPE 启动脚本](wpeinit-and-startnetcmd-using-winpe-startup-scripts.md)

[Drvload 命令行选项](drvload-command-line-options.md)

 

 






