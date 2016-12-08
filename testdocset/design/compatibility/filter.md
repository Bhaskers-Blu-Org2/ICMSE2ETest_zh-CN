---
title: "筛选器用于 Windows 10 版本 1607年硬件兼容性规范"
Description: "本节文档提供筛选驱动程序 Windows 10，1607年版本在硬件兼容性的规范。"
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 4e20698db8c2fa7fa36c47f25859bd21415d51a2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="hardware-compatibility-specification-for-filter-for-windows-10-version-1607"></a>筛选器用于 Windows 10 版本 1607年硬件兼容性规范

本节文档提供筛选驱动程序 Windows 10，1607年版本在硬件兼容性的规范。

这些指标划分为以下类别和主题︰

- [Filter.Driver.AntiVirus](#filterdriverantivirus)
- [Filter.Driver.DeviceGuard](#filterdriverdeviceguard)
- [Filter.Driver.EarlyLaunchAntiMalware](#filterdriverearlylaunchantimalware)
- [Filter.Driver.FileSystem](#filterdriverfilesystem)
- [Filter.Driver.Fundamentals](#filterdriverfundamentals)
- [Filter.Driver.Network LWF](#filterdrivernetworklwf)
- [Filter.Driver.Security](#filterdriversecurity)
- [Filter.Driver.vSwitchExtension](#filterdrivervswitchextension)
- [Filter.Driver.WindowsFilteringPlatform](#filterdriverwindowsfilteringplatform)

<a name="filterdriverantivirus"></a>
## <a name="filterdriverantivirus"></a>Filter.Driver.AntiVirus 

*防病毒筛选器驱动程序要求。*

### <a name="filterdriverantivirusfunctionality"></a>Filter.Driver.AntiVirus.Functionality

*内核模式筛选器驱动程序必须进行设计，以便最大化可靠性和功能的 Windows 文件系统，以及准确地交互系统的核心组件。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

内核模式筛选器驱动程序必须进行设计，以便最大化可靠性和功能的 Windows 文件系统，以及准确地交互系统的核心组件。 特别感兴趣的一些领域是︰ 
 

-   本地文件系统
    -   NT API、 Win32 API 和 Win32 映射 IO API 的使用情况
    -   对象 ID 功能
    -   重分析点
    -   机会锁定
    -   系统缓存使用率
    -   事务处理能力
-   远程文件系统
-   通过 SMB 操作锁定语义

有关文件系统问题的信息︰ <http://download.microsoft.com/download/4/3/8/43889780-8d45-4b2e-9d3a-c696a890309f/File%20System%20Behavior%20Overview.pdf>

有关通过 SMB 操作锁定语义信息，请参阅\[MS SMB2\]在协议文档︰ <http://msdn.microsoft.com/en-us/library/cc246482(PROT.13).aspx>

### <a name="filterdriverantivirusicardetection"></a>Filter.Driver.AntiVirus.IcarDetection

*防病毒筛选器驱动程序必须被设计为可行使基本的防病毒功能，以及准确地交互系统的核心组件。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
            
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

防病毒筛选器驱动程序必须被设计为可行使基本的防病毒功能，以及准确地交互系统的核心组件。  特别感兴趣的一些领域是︰    

-   文件系统
-   防病毒功能

### <a name="filterdriverantivirusminifilter"></a>Filter.Driver.AntiVirus.MiniFilter

*文件系统筛选器驱动程序必须是使用文件系统筛选器管理器的微筛选器驱动程序。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

此要求将隐式地进行测试。 这样，传统的文件系统筛选器驱动程序不会枚举，则将写入 Windows 硬件实验室工具包的驱动程序检测机制。 将枚举并出现在工具箱仅微筛选器驱动程序。 在这种情况下，用户将无法选择徽标测试工具包通过传统筛选器驱动程序。

有关此处筛选器管理器和微筛选器驱动程序可用︰ <http://msdn.microsoft.com/en-us/library/ff540402(v=VS.85).aspx>
<http://msdn.microsoft.com/en-us/windows/hardware/gg462968.aspx>

### <a name="filterdriverantivirusnamedpipeandmailslots"></a>Filter.Driver.AntiVirus.NamedPipeAndMailSlots

*内核模式筛选器驱动程序必须进行设计，以便最大化可靠性和命名管道和邮件插槽的功能，以及准确地交互系统的核心组件。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

内核模式筛选器驱动程序必须进行设计，以便最大化可靠性和命名管道和邮件插槽的功能，以及准确地交互系统的核心组件。  特别感兴趣的一些领域是︰ 

-   命名的管道文件系统

    -   功能和公共 Api 的压力

    -   匿名管道

    -   管道模式

    -   打开模式

    -   无效的管道名称

    -   清洗管道

    -   最大的管道实例

    -   管道方向 （在/出/双面打印）

    -   输入和输出缓冲区大小

    -   各种调用语义，如重新连接已断开连接的服务器端的管道。

    -   对于每个不同的管道实例状态的所有命名的管道操作行为验证。

    -   创建命名的管道和连接的性能。

    -   吞吐量/输出缓冲区大小和数量的客户端不同。 

    -   可扩展性的客户端连接到命名的管道实例所用的时间的数量增加

-   邮件插槽文件系统

-   功能和公共 Api 的压力

命名管道和邮件插槽的信息，请访问︰ <http://msdn.microsoft.com/en-us/library/aa365574(v=VS.85).aspx>

### <a name="filterdriverantivirusregistryandprocess"></a>Filter.Driver.AntiVirus.RegistryAndProcess

*内核模式筛选器驱动程序必须进行设计，以便最大化的可靠性和 Windows 注册表和流程的功能，以及准确地交互系统的核心组件。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

内核模式筛选器驱动程序必须进行设计，以便最大化的可靠性和 Windows 注册表和流程的功能，以及准确地交互系统的核心组件。  特别感兴趣的一些领域是︰      

-   注册表

    -   NT API 和 Win32 API 的使用情况

    -   关键功能

    -   交易记录的注册表操作

    -   符号链接行为

-   混色

    -   常规的模块管理

    -   在线程/进程终止时的争用条件

    -   流程管理回调功能

-   线程和进程句柄操作

### <a name="filterdriverantiviruswinsock"></a>Filter.Driver.AntiVirus.Winsock

*内核模式筛选器驱动程序必须进行设计，以便最大化的可靠性和 Windows 套接字的功能，以及准确地交互系统的核心组件。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

内核模式筛选器驱动程序必须进行设计，以便最大化的可靠性和 Windows 套接字的功能，以及准确地交互系统的核心组件。  特别感兴趣的一些领域是︰   

-   Winsock

-   Winsock API 功能

Winsock Api 的信息，请访问︰ <http://msdn.microsoft.com/en-us/library/ms740673(VS.85).aspx>

<a name="filterdriverdeviceguard"></a>
## <a name="filterdriverdeviceguard"></a>Filter.Driver.DeviceGuard 

*构建所有的内核驱动程序必须有[设备保护装置](http://blogs.msdn.com/b/windows_hardware_certification/archive/2015/05/22/driver-compatibility-with-device-guard-in-windows-10.aspx)兼容。*

### <a name="filterdriverdeviceguarddrivercompatibility"></a>Filter.Driver.DeviceGuard.DriverCompatibility

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

Windows 10 提供了一种称为[*设备监护*](http://blogs.windows.com/business/2015/04/21/windows-10-security-innovations-at-rsa-device-guard-windows-hello-and-microsoft-passport/)程序将使组织能够锁定的方式提供新的和未知的恶意软件变种的高级恶意软件防护设备以及高级持久威胁 (APTs) 功能。 设备保护可以使用硬件技术和虚拟化来隔离代码完整性 (CI) 决策函数，从 Windows 操作系统的其余部分。 当使用基于虚拟化的安全隔离代码完整性，可以成为可执行内核内存的唯一方法是通过代码完整性验证。 这意味着，内核内存页永远不能写和可执行文件 (W + X) 并不能直接修改可执行代码。

Windows 硬件认证博客上提供了详细信息︰[有 Windows 10 中设备保护装置的驱动程序兼容性](http://aka.ms/DeviceGuard)。

Sys 文件，必须设置以下属性。
<table>
<tr><th>属性名称</th><th>说明</th></tr>
<tr><td>CompanyName</td><td>公司名称</td></tr>
<tr><td>FileDescription</td><td>驱动程序文件中的产品说明</td></tr>
<tr><td>OriginalFilename</td><td>原始文件名</td></tr>
<tr><td>产品名称</td><td></td></tr>
<tr><td>与\_FIXEDFILEINFO:</td><td></td></tr>
<tr><td>&nbsp;&nbsp;&nbsp;FileVer</td><td>文件版本号</td></tr>
<tr><td>&nbsp;&nbsp;&nbsp;FileVer</td><td>产品版本号</td></tr>
</table>

您可以在下面的 MSDN 上找到更多详细信息︰

-   <https://msdn.microsoft.com/en-us/library/windows/desktop/aa381058 (v=vs.85).aspx>

所有的内核驱动程序，Windows 必须在通过 SysDev 操控板由 Microsoft （经 WHQL 证书） 签名。

<a name="filterdriverearlylaunchantimalware"></a>
## <a name="filterdriverearlylaunchantimalware"></a>Filter.Driver.EarlyLaunchAntiMalware 

*本部分介绍早期启动驱动程序的要求。*

### <a name="filterdriverearlylaunchantimalwarebackupdriver"></a>Filter.Driver.EarlyLaunchAntiMalware.BackupDriver

*早期的启动反恶意软件驱动程序必须包括在发生损坏时的备份副本。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

反恶意软件 (AM) 驱动程序是计算机的启动成功的关键。  如果驱动程序被破坏，可能不会成功启动。  若要提供最佳的用户体验，则需要，上午驱动程序安装时，它还安装了一个备份驱动程序存储区中。  这将确保平滑修正经验情况下的受损的主要驱动因素。

由 Windows，ELAM 备份存储的位置并将其存储在注册表中︰ HKEY\_本地\_机\\系统\\开目前控制设置\\控件\\EarlyLaunch ！ BackupPath

*设计备注︰*在 NTOS 内核启动之后立即启动早期启动反恶意软件 (AM) 驱动程序。  每个后续启动的驱动程序，上午驱动程序从即插即用管理器来确定是否应初始化启动驱动程序将收到回调。  上午驱动程序启动驱动程序的计算结果，并且必须返回好、 坏的或者不知道。  根据返回的分类和定义的策略，即插即用管理器决定是否初始化启动驱动程序。

### <a name="filterdriverearlylaunchantimalwareelamsignatureattributes"></a>Filter.Driver.EarlyLaunchAntiMalware.ELAMSignatureAttributes

*ELAM INF 文件中的 SignatureAttribute 部分的要求。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

ELAM 文件必须使用特殊的签名，作为提交过程的一部分进行签名。 确定每个模块需要何种签名的过程是被标准化;现在，每个 INF 文件必须包含 SignatureAttributes 节，用于唯一标识适用于相关的驱动程序二进制文件是什么类型的签名。 向现有 inf 文件添加该节是一个非常简单的过程。

下面是一个示例。
```
\[SignatureAttributes\]
ELAMFILE.dll = SignatureAttributes.Elam
\[SignatureAttributes.Elam\]
Elam=true
```

### <a name="filterdriverearlylaunchantimalwaremvimembership"></a>Filter.Driver.EarlyLaunchAntiMalware.MVIMembership

*由 MVI 成员，才可创建早期启动反恶意软件驱动程序。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

由 Microsoft 病毒计划 (MVI) 成员，才可创建任何早期启动反恶意软件 (AM) 驱动程序。

 *设计备注︰*在 NTOS 内核启动之后立即启动早期上午启动驱动程序。  每个后续启动的驱动程序，上午驱动程序从即插即用管理器来确定是否应初始化启动驱动程序将收到回调。  上午驱动程序启动驱动程序的计算结果，并且必须返回好、 坏的或者不知道。  根据返回的分类和定义的策略，即插即用管理器决定是否初始化启动驱动程序。

### <a name="filterdriverearlylaunchantimalwareperformance"></a>Filter.Driver.EarlyLaunchAntiMalware.Performance

*早期的启动反恶意软件驱动程序必须是性能。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

回叫滞后时间︰ 反恶意软件 (AM) 驱动程序需要返回接收回调的 0.5 毫秒内每个回调的结果。

内存分配︰ 上午驱动程序，其中包括驱动程序映像以及配置 （签名） 的数据，是必需具有内存有限的占地面积为 256 KB 或更少。

卸载阻止︰ 指示上午驱动程序将被卸载初始化引导驱动程序之后，每个上午驱动程序将收到同步回调。 此时，上午驱动程序需要整理和保存持久状态的任何信息。 这必须发生在当内核发出回调到上午驱动程序返回回调的时间到驱动程序的时间从 0.5 毫秒内。

*设计备注︰*在 NTOS 内核启动之后立即启动早期上午启动驱动程序。  每个后续启动的驱动程序，上午驱动程序从即插即用管理器来确定是否应初始化启动驱动程序将收到回调。  上午驱动程序启动驱动程序的计算结果，并且必须返回好、 坏的或者不知道。  根据返回的分类和定义的策略，即插即用管理器决定是否初始化启动驱动程序。 

### <a name="filterdriverearlylaunchantimalwaresignaturedata"></a>Filter.Driver.EarlyLaunchAntiMalware.SignatureData

*早期的启动反恶意软件驱动程序必须只使用 Microsoft 特定位置中存储的签名数据。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

上午驱动程序必须从一个众所周知的位置，并没有其他获得其恶意软件签名数据。  签名的数据应存储在注册表中加载的 Winload，并将因此可供上午驱动程序正在初始化文件系统之前 HKLM 下新 ELAM 配置单元中。   每个上午驱动程序将有唯一的键用来存储其签名 blob。   注册表路径和密钥应 HKLM 的格式为\\ELAM\\<*供应商名称*>\\Measured︰ 二进制 = <*blob*>。

*设计备注︰*在 NTOS 内核启动之后立即启动早期启动反恶意软件 (AM) 驱动程序。  每个后续启动的驱动程序，上午驱动程序从即插即用管理器来确定是否应初始化启动驱动程序将收到回调。  上午驱动程序启动驱动程序的计算结果，并且必须返回好、 坏的或者不知道。  根据返回的分类和定义的策略，即插即用管理器决定是否初始化启动驱动程序。

<a name="filterdriverfilesystem"></a>
## <a name="filterdriverfilesystem"></a>Filter.Driver.FileSystem 

### <a name="filterdriverfilesystemfunctionality"></a>Filter.Driver.FileSystem.Functionality

*内核模式筛选器驱动程序必须进行设计，以便最大化可靠性和功能的 Windows 文件系统，以及准确地交互系统的核心组件。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

内核模式筛选器驱动程序必须进行设计，以便最大化可靠性和功能的 Windows 文件系统，以及准确地交互系统的核心组件。 特别感兴趣的一些领域是︰   

-   本地文件系统

    -   NT API、 Win32 API 和 Win32 映射 IO API 的使用情况

    -   对象 ID 功能

    -   重分析点

    -   机会锁定

    -   系统缓存使用率

    -   事务处理能力

-   远程文件系统

-   通过 SMB 操作锁定语义

有关文件系统问题的信息︰ <http://download.microsoft.com/download/4/3/8/43889780-8d45-4b2e-9d3a-c696a890309f/File%20System%20Behavior%20Overview.pdf>

有关通过 SMB 操作锁定语义信息，请参阅\[MS SMB2\]在协议文档︰ <http://msdn.microsoft.com/en-us/library/cc246482(PROT.13).aspx>

### <a name="filterdriverfilesystemminifilter"></a>Filter.Driver.FileSystem.MiniFilter

*文件系统筛选器驱动程序必须是使用文件系统筛选器管理器的微筛选器驱动程序。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

此要求将隐式地进行测试。 这样它枚举和曲面仅微筛选器驱动程序的 Windows 硬件认证工具包 (WHCK)，将写入收集程序。 因此，用户将无法选择传统筛选器驱动程序的认证测试。

筛选器管理器和微筛选器驱动程序可从以下站点信息︰ <http://msdn.microsoft.com/en-us/library/ff540402(v=VS.85).aspx>

### <a name="filterdriverfilesystemnamedpipeandmailslots"></a>Filter.Driver.FileSystem.NamedPipeAndMailSlots

*内核模式筛选器驱动程序必须进行设计，以便最大化可靠性和命名管道和邮件插槽的功能，以及准确地交互系统的核心组件。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

内核模式筛选器驱动程序必须进行设计，以便最大化可靠性和命名管道和邮件插槽的功能，以及准确地交互系统的核心组件。  特别感兴趣的一些领域是︰  

-   命名的管道文件系统

    -   功能和公共 Api 的压力

    -   匿名管道

    -   管道模式

    -   打开模式

    -   无效的管道名称

    -   清洗管道

    -   最大的管道实例

    -   管道方向 （在/出/双面打印）

    -   输入和输出缓冲区大小

    -   各种调用语义，如重新连接已断开连接的服务器端的管道。

    -   对于每个不同的管道实例状态的所有命名的管道操作行为验证。

    -   创建命名的管道和连接的性能。

    -   吞吐量/输出缓冲区大小和数量的客户端不同。 

    -   可扩展性的客户端连接到命名的管道实例所花费的时间的数量增加

-   邮件插槽文件系统

-   功能和公共 Api 的压力

命名管道和邮件插槽的信息，请访问︰ <http://msdn.microsoft.com/en-us/library/aa365574(v=VS.85).aspx>

### <a name="filterdriverfilesystemregistryandprocess"></a>Filter.Driver.FileSystem.RegistryAndProcess

*内核模式筛选器驱动程序必须进行设计，以便最大化的可靠性和 Windows 注册表和流程的功能，以及准确地交互系统的核心组件。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

内核模式筛选器驱动程序必须进行设计，以便最大化的可靠性和 Windows 注册表和流程的功能，以及准确地交互系统的核心组件。  特别感兴趣的一些领域是︰      

-   注册表

    -   NT API 和 Win32 API 的使用情况

    -   关键功能

    -   交易记录的注册表操作

    -   符号链接行为

-   混色

    -   常规的模块管理

    -   在线程/进程终止时的争用条件

    -   流程管理回调功能

-   线程和进程句柄操作


## <a name="filterdriverfundamentals"></a>Filter.Driver.Fundamentals 

*对应到设备驱动程序的基础，但对于筛选器驱动程序。*

### <a name="filterdriverfundamentalsdriverquality"></a>Filter.Driver.Fundamentals.DriverQuality

*筛选器驱动程序必须是高质量。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

驱动程序组件不会导致系统崩溃或泄漏资源。 这些资源包括但不是限于以下︰  

-   Memory

-   图形设备接口 (GDI) 或用户对象

-   内核对象，例如文件、 mutex、 信号量，并且设备句柄

-   关键部分

-   磁盘空间

-   打印机句柄

*设计备注*︰

睡眠和 IO 之前和之后测试-PNP 测试周期系统通过所有睡眠状态，并执行基本 PNP 系统上的所有设备上。

使用标准设置启用驱动程序验证程序将运行此测试。

<a name="filterdrivernetworklwf"></a>
## <a name="filterdrivernetworklwf"></a>Filter.Driver.Network.LWF 

*局域网的要求。*

### <a name="filterdrivernetworklwfbase"></a>Filter.Driver.Network.LWF.Base

*重量轻的所有筛选器必须是 NDIS 6.30 或更高版本。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

重量轻的所有筛选器必须是 NDIS 6.30 或更高版本并且符合到 MSDN 上的 NDIS 规范。

### <a name="filterdrivernetworklwfmtusize"></a>Filter.Driver.Network.LWF.MTUSize

*重量轻的所有筛选器必须能够接受任意数据包大小，它可能会大于微型端口的 MTU。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

重量轻的所有筛选器必须是 NDIS 6.30 或更高版本。 重量轻的所有筛选器必须能够接受任意数据包大小，它可能会大于微型端口的 MTU。


## <a name="filterdriversecurity"></a>Filter.Driver.Security 

*与 TDI 筛选驱动程序和 Lsp 的安全性相关的其他要求。*

### <a name="filterdriversecuritynotdifilterandlsp"></a>Filter.Driver.Security.NoTDIFilterAndLSP

*没有 TDI 筛选器或 Lsp 由驱动程序或关联的软件包安装期间安装或使用。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

可以无需使用的 TDI 筛选器或 Lsp 由内核模式软件或驱动程序，或者用户模式软件或驱动程序。

<a name="filterdrivervswitchextension"></a>
## <a name="filterdrivervswitchextension"></a>Filter.Driver.vSwitchExtension 

### <a name="filterdrivervswitchextensionextensionrequirements"></a>Filter.Driver.vSwitchExtension.ExtensionRequirements

*实现虚拟机开关可扩展性的筛选器驱动程序必须支持所需的功能、 模式和协议。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

实现虚拟机开关可扩展性的筛选器驱动程序必须支持所需的功能、 模式和协议。

要求

-   扩展名必须通过 NDIS 筛选徽标要求。

    -   一个扩展必须具有有效的 INF。

    -   扩展名必须进行唯一的 NDIS、 WDF 或 WDM 调用;不允许有任何的其它内核模式组件的调用。

-   扩展名必须支持 Hyper-V 实时迁移。

    -   不破解 LM，保存/恢复，导出/导入

    -   不阻止其他扩展名保存的数据

    -   不要阻止其他扩展交互

-   通过虚拟交换机的所有流量来自于一个虚拟机，一台主机 VNIC，外部 NIC 或扩展不能修改扩展标头。   从这一要求的例外情况包括︰

    -   将通信重定向到网络设备

    -   可变的 IP 数据包头字段 （按照 RFC 4302 3.3.3.1.1.1 为 IPv4 和 IPv6 的 3.3.3.1.2.1 部分中指定）

-   未配置的扩展必须不会中断主机和外部网络之间的连接。

-   捕获扩展必须中断 vSwitch 端口之间的连接。

-   扩展名必须通过下列开关/端口/NIC 配置 Oid 下扩展的堆栈︰

    -   OID\_开关\_参数

    -   OID\_开关\_端口\_数组

    -   OID\_开关\_端口\_拆卸

    -   OID\_开关\_端口\_删除

    -   OID\_开关\_NIC\_数组

    -   OID\_开关\_NIC\_连接

    -   OID\_开关\_NIC\_断开连接

    -   OID\_开关\_NIC\_删除

    -   OID\_开关\_NIC\_请求

-   扩展名必须通过以下策略/状态不占用沿堆栈向下的 Oid:

    -   OID\_开关\_端口\_属性\_添加

    -   OID\_开关\_端口\_属性\_更新

    -   OID\_开关\_端口\_属性\_删除

    -   OID\_开关\_属性\_添加

    -   OID\_开关\_属性\_更新

    -   OID\_开关\_属性\_删除

    -   OID\_开关\_端口\_功能\_状态\_查询

    -   OID\_开关\_功能\_状态\_查询

-   扩展名必须通过以下策略 Oid 沿堆栈向下︰

    -   OID\_开关\_端口\_属性\_枚举

    -   OID\_开关\_属性\_枚举

-   扩展名必须通过在堆栈中向上以下︰

    -   NDIS\_开关\_NIC\_状态\_指示

-   "捕获"扩展不得调用下面的函数︰

*设计备注︰*请参见 VM 开关可扩展性规范。

<a name="filterdriverwindowsfilteringplatform"></a>
## <a name="filterdriverwindowsfilteringplatform"></a>Filter.Driver.WindowsFilteringPlatform 

### <a name="filterdriverwindowsfilteringplatformarchitecturaldesignappcontainerssupportmodernapplications"></a>Filter.Driver.WindowsFilteringPlatform.ArchitecturalDesign.AppContainers.SupportModernApplications

*基于 WFP 的产品必须不会阻止应用程序容器应用程序默认情况下，工作符合其声明的网络意图和按照特定的用户管理目的应该只有块应用程序容器应用程序或保护系统受到特定的威胁。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

基于 WFP 的产品一定不能阻塞应用程序容器应用程序默认情况下，工作符合其网络声明的意图和应*阻止应用程序容器应用程序*仅按照特定的用户管理意图或保护系统受到特定的威胁。

### <a name="filterdriverwindowsfilteringplatformarchitecturaldesigncleanuninstall"></a>Filter.Driver.WindowsFilteringPlatform.ArchitecturalDesign.CleanUninstall

*基于 WFP 的产品必须完全停止，并清理所有正在运行状态时卸载。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

这是为了确保主机防火墙不会离开时卸载，因此可能导致诊断问题，如果在同一台 PC 上安装另一个单独的主机防火墙，则未使用的对象。 下面的 WFP 对象需要被清理︰ 提供者、 providerContext、 筛选器、 子图层或标注。
此外，还必须满足 （通过软件徽标计划） 的应用程序的附加的安装要求。

*设计备注*︰

应用程序可以使用 MSI 或满足这一要求确保在 Windows® 上的令人满意的安装/卸载体验基于 PC 的另一个安装程序。
（在软件徽标计划） 的应用程序的安装要求都位于下面的链接︰ <http://www.microsoft.com/downloads/details.aspx?FamilyID=27028822-B172-4CEC-91A3-26B610A4DA79&displaylang=en>
 

### <a name="filterdriverwindowsfilteringplatformarchitecturaldesignconnectionproxyingnodeadlocks"></a>Filter.Driver.WindowsFilteringPlatform.ArchitecturalDesign.ConnectionProxying.NoDeadlocks

*重定向或代理重定向层 （连接重定向），必须使用新的代理 API，以便其他基于 WFP 的产品可以确定连接已代理基于 WFP 的产品。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

WFP 基于代理服务器的重定向重定向的层 （连接重定向），必须使用新的 proxy'ing API，以便其他基于 WFP 的产品可以确定连接已 proxy'ed 的产品。
 

### <a name="filterdriverwindowsfilteringplatformarchitecturaldesignfwpmfiltersmaintainoneterminating"></a>Filter.Driver.WindowsFilteringPlatform.ArchitecturalDesign.FwpmFilters.MaintainOneTerminating

*基于 WFP 的产品必须创建和维护至少一个终止 FWPM\_筛选器对象。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

终止的筛选器是一种返回允许 / 阻止决策。 它可能存在的静态筛选器或标注中。 这一要求背后的意图是确保高级主机防火墙执行至少允许或阻止决策并不是简单地维护的筛选器检查的目的，只而基本主机防火墙可能会这样做，通过 WFP 或通过其他方式如 TDI、 NDIS，以及 WinSock LSP 的筛选器。

*设计备注︰*FWPM 的定义\_可以在下面的 URL 中找到筛选器对象︰ <http://go.microsoft.com/fwlink/?LinkID=116902&clcid=0x409>

### <a name="filterdriverwindowsfilteringplatformarchitecturaldesignfwpmprovidersassociatewithobjects"></a>Filter.Driver.WindowsFilteringPlatform.ArchitecturalDesign.FwpmProviders.AssociateWithObjects

*基于 WFP 的产品必须与相关联的所有提供程序上下文、 筛选器、 子图层和标注其相应的标识提供程序对象。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

有关说明预期的各种类型的对象的代码行为的示例，请参见下面︰ 引用名称与标识提供程序对象内的公司的产品︰
```
const PWSTR pCompanyName = L"Microsoft Corporation";
const PWSTR pProductName = L"Windows Firewall";
FWPM\_PROVIDER0 myProvider;
myProvider.displayData.name = pCompanyName;
myProvider.displayData.description = pProductName; 
```
初始化提供程序的对象︰
```
FWPM\_PROVIDER\_CONTEXT0 myProviderContext;
FWPM\_PROVIDER0 myProvider;
myProviderContext.providerKey = &(myProvider.providerKey);
```
初始化子图层的对象并将其与相应的提供程序对象相关联︰
```
FWPM\_SUBLAYER0 mySubLayer;
FWPM\_PROVIDER0 myProvider;
mySubLayer.providerKey = &(myProvider.providerKey); 
```
初始化该标注对象和将其与相应的提供程序对象相关联︰
```
FWPM\_CALLOUT0 myCallout;
FWPM\_PROVIDER0 myProvider;
myCallout.providerKey = &(myProvider.providerKey); 
```
初始化筛选器的对象并将其与相应的提供程序对象相关联︰
```
FWPM\_FILTER0 myFilter;
FWPM\_PROVIDER0 myProvider;
myFilter.providerKey = &(myProvider.providerKey);
```
 

### <a name="filterdriverwindowsfilteringplatformarchitecturaldesignfwpmprovidersmaintainidentifying"></a>Filter.Driver.WindowsFilteringPlatform.ArchitecturalDesign.FwpmProviders.MaintainIdentifying

*基于 WFP 的产品必须创建和维护至少一个标识 FWPM\_提供程序提供程序对象。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

*必须*标识提供程序对象引用名称和产品的公司，如下面的示例中所示。  
FWPM\_PROVIDER0

1.  所有供应商必须创建和维护至少一个提供程序。

2.  Provider.displayData.Name 必须包含公司的名称。

3.  Provider.displayData.Description 必须包含产品的名称。

创建与该供应商所拥有的所有对象必须都引用仅是其供应商︰
```
const PWSTR pCompanyName = L"Microsoft Corporation";
const PWSTR pProductName = L"Windows Firewall";
FWPM\_PROVIDER0 myProvider;
 
myProvider.displayData.name = pCompanyName;
myProvider.displayData.description = pProductName;
```

*设计备注︰*定义的 FWPM\_可以在下面的 URL 中找到提供程序对象︰ <http://go.microsoft.com/fwlink/?LinkID=116844&clcid=0x409>
 

### <a name="filterdriverwindowsfilteringplatformarchitecturaldesignfwpmsublayersuseownorbuiltin"></a>Filter.Driver.WindowsFilteringPlatform.ArchitecturalDesign.FwpmSublayers.UseOwnOrBuiltIn

*基于 WFP 的产品所需的只是自己子图层或一个内置 sublayers。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

一个主机防火墙的子图层可能用于确保通过从另一台主机防火墙更高重量筛选器必须不回避其筛选器。 此外，主机防火墙必须重写属于另一个主机防火墙筛选器。

*设计备注︰*定义 FWPM\_SUBLAYERobject 可在下面的 URL: <http://go.microsoft.com/fwlink/?LinkID=116845&clcid=0x409>
 

### <a name="filterdriverwindowsfilteringplatformarchitecturaldesignnetworkdiagnosticsframeworkhelperclass"></a>Filter.Driver.WindowsFilteringPlatform.ArchitecturalDesign.NetworkDiagnosticsFramework.HelperClass

*基于 WFP 的产品必须包含扩展筛选平台帮助器类 (FPHC) 的网络诊断框架 (NDF) 帮助器类。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

Windows 筛选平台 (WFP) 包括网络诊断框架 (NDF) 的帮助器类，称为筛选平台帮助器类 (FPHC)。 FPHC 可以帮助识别由 WFP 引起连接问题的根本原因。 将主机防火墙可以调用自己 NDF 的帮助器类。 FPHC 可扩展性允许诊断过程中要调用这些第三方帮助器类。

FPHC 可以标识 WFP 为连接问题的原因。 如果可用，FPHC 还可以标识创建提供程序会阻塞网络通信的筛选器。 FPHC 将此信息传递到 NDF，又可以再通知用户 WFP 导致的连接问题，并为阻止通信的提供程序的名称。

但是，FPHC 不能提供建议的纠正措施，对用户来说，也可以提供筛选器将阻止用户的通信的原因。 只有一个 FPHC 扩展可以执行这些任务。

主机防火墙必须能够成功地诊断入站/出站连接而导致的失败主机防火墙，并提供适当的响应最终用户根据故障诊断。 （例如，修复机制，向用户说明连接失败的原因，原因的消息，诸如此类）。

*设计备注︰*以下链接中可以找到有关 NDF 和 FPHC 的详细信息︰

NDF: <http://go.microsoft.com/fwlink/?LinkID=125463&clcid=0x409><br/>
FPHC: <http://go.microsoft.com/fwlink/?LinkID=125464&clcid=0x409>

### <a name="filterdriverwindowsfilteringplatformarchitecturaldesignnoaccessviolations"></a>Filter.Driver.WindowsFilteringPlatform.ArchitecturalDesign.NoAccessViolations

*基于 WFP 的产品不能在高负载情况下或在驱动程序加载/卸载任何访问冲突的产生原因。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

基于 WFP 的产品不能在高负载情况下或在驱动程序加载/卸载任何访问冲突的产生原因 （或不在网络负载时）。
 

### <a name="filterdriverwindowsfilteringplatformarchitecturaldesignnotamperingwith3rdpartyobjects"></a>Filter.Driver.WindowsFilteringPlatform.ArchitecturalDesign.NoTamperingWith3rdPartyObjects

*基于 WFP 的产品不得尝试删除或修改另一基于 WFP 的产品 WFP 对象和内置对象。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

这样一来，可以确保多个主机之间的互操作性在操作系统中的防火墙的 WFP 对象。
 

### <a name="filterdriverwindowsfilteringplatformarchitecturaldesignpacketinjectionnodeadlocks"></a>Filter.Driver.WindowsFilteringPlatform.ArchitecturalDesign.PacketInjection.NoDeadlocks

*基于 WFP 的产品必须不断地修改网络数据包已修改并重新插入，以便创建潜在的死锁。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

防火墙可以使用标注来修改并重新插入网络数据包筛选在任意层时。 一个或多个主机防火墙可能会出现在同一个系统上。 当只有一个主机防火墙是存在于系统，不断地修改和重新注入相同的数据包可能会导致性能降低，是避免使用。 系统上存在多个主机防火墙 （带标注） 时，不断地可以由多个标注修改相同的网络数据包。 当主机防火墙不断修改，而且 reinjects 同一个数据包时，它可能会导致网络数据包永远不会得到处理，并可能形成死锁，这是要避免。

不，主机防火墙必须修改和每层 reinject 相同的网络数据包 2 倍以上。 如果发生这种情况，可以选择主机防火墙允许数据包通过，或删除网络数据包。
 

### <a name="filterdriverwindowsfilteringplatformarchitecturaldesignstreaminjectionnostreamstarvation"></a>Filter.Driver.WindowsFilteringPlatform.ArchitecturalDesign.StreamInjection.NoStreamStarvation

*基于 WFP 的产品标注处 FWPM\_层\_流必须不使数据吞吐量。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

到*不运行*意味着流层标注指示不应挂起，排队等候超过 8 MB 的数据。
 

### <a name="filterdriverwindowsfilteringplatformarchitecturaldesignsupportpowermanagedstates"></a>Filter.Driver.WindowsFilteringPlatform.ArchitecturalDesign.SupportPowerManagedStates

*基于 WFP 的产品必须确保网络连接时恢复从电源管理状态。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

必须支持所有的电源状态的计算机上运行测试 (待机模式，休眠，混合、 关闭、 重新启动)。 主机防火墙允许进入和从上面提到的电源恢复系统管理状态。 在继续从这些特定的电源管理状态，应满足从 WFP 的要求。

防火墙永远不应挂起数据包，以便电源状态变化拒绝工作由于挂起的数据包。
 

### <a name="filterdriverwindowsfilteringplatformarchitecturaldesignwfpobjectacls"></a>Filter.Driver.WindowsFilteringPlatform.ArchitecturalDesign.WFPObjectACLs

*基于 WFP 的产品必须 ACL 的所有其他基于 WFP 的产品至少可以枚举对应 WFP 枚举 Api 使用这些对象的方式及其对象。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

基于 WFP 的产品必须 ACL 的所有其他基于 WFP 的产品至少可以枚举对应 WFP 枚举 Api 使用这些对象的方式及其对象。
这是为了确保在系统上的所有 WFP 对象可以由任何主机防火墙和应用程序都枚举用于诊断目的。

*设计备注︰*举一个例子，过滤对象必须要能够被记录在下面的 URL 中的 FwpmFilterEnum 函数枚举︰ <http://go.microsoft.com/fwlink/?LinkID=116839&clcid=0x409>同样，（提供程序、 子图层等） 的其他对象的枚举函数可在下面的 URL: <http://go.microsoft.com/fwlink/?LinkID=116840&clcid=0x409>

### <a name="filterdriverwindowsfilteringplatformarchitecturaldesignwinsock"></a>Filter.Driver.WindowsFilteringPlatform.ArchitecturalDesign.Winsock

*内核模式筛选器驱动程序被设计为可最大化的可靠性和 Windows 套接字的功能，以及准确地交互系统的核心组件。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

内核模式筛选器驱动程序被设计为可最大化的可靠性和 Windows 套接字的功能，以及准确地交互系统的核心组件。  特别感兴趣的一些领域是︰   

-   Winsock

-   Winsock API 功能

Winsock Api 的信息，请访问︰ <http://msdn.microsoft.com/en-us/library/ms740673(VS.85).aspx>

### <a name="filterdriverwindowsfilteringplatformfirewalldisablewindowsfirewallproperly"></a>Filter.Driver.WindowsFilteringPlatform.Firewall.DisableWindowsFirewallProperly

*主机防火墙必须禁用 Windows 防火墙使用受支持的方法。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

能够有选择地打开或关闭的部分 Windows 防火墙提供了主机防火墙。 这些部件指定不同类型的规则 （和随后的过滤器集合），并且可能还被称为类别。 可能会有选择地关闭筛选器集都会引导时间筛选器、 防火墙筛选器、 连接安全筛选器和隐藏筛选器。
HNetCfg.FwProducts COM 对象支持的注册界面。 将\_DisplayName() 调用必须用于填充您的产品信息。
关闭防火墙规则类别之前, 供应商的防火墙必须确保所有筛选器，必须安装。

这一要求可确保与 Windows 更好的互操作性。 另外，如果系统上的所有已安装的主机防火墙卸载出于任何原因，Windows 防火墙已意识到这一点，并且将自动打开防火墙筛选器，可确保系统始终受到保护。
连接安全筛选器需要一直保持启用状态，保持 Windows 保护的方案。 具体而言，连接安全筛选器确保系统支持要求身份验证和加密的通信。

*设计备注*︰

此要求确保防火墙供应商记录准则每禁用 Windows 防火墙。

### <a name="filterdriverwindowsfilteringplatformfirewallnotonlypermitallfilters"></a>Filter.Driver.WindowsFilteringPlatform.Firewall.NotOnlyPermitAllFilters

*不能仅有主机防火墙"允许\_所有"筛选器。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

主机防火墙必须不突破意图的 Windows 筛选平台 API 测试时，只需保持在所有允许\_所有所有种类的网络通信量，实质上是没有意义的过滤筛选网络通信。 这适用于同时标注的筛选器以及静态。 同样，主机防火墙必须维护仅块\_所有筛选器。 但是，，将解决使用者情况中的测试时。
 

### <a name="filterdriverwindowsfilteringplatformfirewallsupport5tupleexceptions"></a>Filter.Driver.WindowsFilteringPlatform.Firewall.Support5TupleExceptions

*所有基于主机的防火墙必须能够阻止/允许按 5 元组部件 (包括 （ICMP 类型和代码，UDP 和 TCP） 端口 IP 地址和协议 （例如，ICMP/TCP/UDP）。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

所有基于主机的防火墙必须能够阻止/允许按 5 元组部件 (包括 （ICMP 类型和代码，UDP 和 TCP） 端口 IP 地址 （例如，ICMP/TCP/UDP） 协议)。

### <a name="filterdriverwindowsfilteringplatformfirewallsupportapplicationexceptions"></a>Filter.Driver.WindowsFilteringPlatform.Firewall.SupportApplicationExceptions

*基于 WFP 的产品必须支持相应的应用程序中的异常。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

除了支持方案根据 Windows® 中的应用程序很重要支持安装的应用程序 （家庭用户），注册的主机防火墙筛选的目的。 防火墙可以使用参数，如路径和端口，允许或阻止特定于应用程序通信的基础。 这种情况下需要使用本机 IPv4、 本机 IPv6，6to4 和 Teredo 数据包。
*支持*单词是指*主机防火墙功能*以确保应用程序中的异常处理的主机防火墙中，如果应用程序/用户/网络需要它。 主机防火墙还必须具有正确配置对象，例如，筛选器，以支持所需的功能，即使可能未启用功能，默认情况下，用户界面中。
 

### <a name="filterdriverwindowsfilteringplatformfirewallsupportmacaddressexceptions"></a>Filter.Driver.WindowsFilteringPlatform.Firewall.SupportMACAddressExceptions

*L2 中有筛选器的所有基于主机的防火墙 (本机/Mac) 层必须能够阻止或允许的 MAC 地址。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

L2 中有筛选器的所有基于主机的防火墙 (本机/Mac) 层必须能够阻止或允许的 MAC 地址。

### <a name="filterdriverwindowsfilteringplatformfirewallusewindowsfilteringplatform"></a>Filter.Driver.WindowsFilteringPlatform.Firewall.UseWindowsFilteringPlatform

*防火墙必须遵守 Windows 筛选平台的基于 Api 的筛选上家庭用户解决方案的网络通信。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

必须没有 TDI，NDIS，WinSock LSP 筛选器主机防火墙在 PC 上安装时出现。 家庭用户产品，只有静态筛选器 / 必须使用基于 Windows 筛选平台 (WFP) 上的标注。

*设计备注︰*有关 Windows 筛选平台的详细信息，请参阅下面的链接︰ <http://go.microsoft.com/fwlink/?LinkID=116899&clcid=0x409>

 

### <a name="filterdriverwindowsfilteringplatformnetworkingfundamentalsupportaddressresolution"></a>Filter.Driver.WindowsFilteringPlatform.NetworkingFundamental.SupportAddressResolution

*基于 WFP 的产品必须支持允许成功的 ARP 和 ICMP 邻居发现交换。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

基于 WFP 的产品必须支持 ARP （适用于 IPv4) 和交换 ICMP 邻居发现 （适用于 IPv6)。

防火墙允许系统发送 ARP 和 ICMP 相邻节点搜索请求和答复，以及接收到 ARP 和 ICMP 相邻节点搜索请求和答复。
*支持*单词指的是为使 arp 更加有效，，如果应用程序/用户/网络需要*主机防火墙的功能*。 主机防火墙还必须具有正确配置对象，例如，筛选器，以支持所需的功能，即使可能未启用功能，默认情况下，用户界面中。

*设计备注︰*主机防火墙都应该允许 PC 发送 ARP 请求代表另一个节点，而不是只代表自己，在 ICS 主机上运行。
作为 Internet 连接共享的 (ICS) DHCP 功能，ICS DHCP 可以发出代表子网中的另一节点的 ARP 请求。
 

### <a name="filterdriverwindowsfilteringplatformnetworkingfundamentalsupportdynamicaddressing"></a>Filter.Driver.WindowsFilteringPlatform.NetworkingFundamental.SupportDynamicAddressing

*基于 WFP 的产品支持对于成功的 DHCP 交换允许通过 IPv4 和 IPv6。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

主机防火墙通过 IPv4 和 IPv6 支持允许成功的 DHCP 交换。

DHCP 发现，DHCP 请求和通知 DHCP 数据包可以通过目标端口 67 到出站 UDP 源端口 68 传输。 DHCP 提供和 DHCP 确认和 DHCP NACK 数据包可以通过目标端口 68 到入站 UDP 源端口 67 接收。 DHCPv6 数据包可以通过目标端口 547 到出站 UDP 源端口 546 传输。 DHCPv6 数据包可以通过入站 UDP 源端口 547 接收到目标端口 546。  

*支持*单词是指*主机防火墙的功能*，允许成功 DHCP 交换，如果应用程序/用户/网络需要它。 主机防火墙还必须具有正确配置对象，例如，筛选器，以支持所需的功能，即使可能未启用功能，默认情况下，用户界面中。

*设计备注︰*可以在以下 URL 中找到详细信息︰ <http://go.microsoft.com/fwlink/?LinkID=116834&clcid=0x409>

主机防火墙都应该允许 DHCP 入站和出站服务器通过无线接口服务如 ICS 主机上运行时。

Internet 连接共享 (ICS) 充当 DHCP 服务器，并且希望接收传入的 DHCP 客户端。
可以通过目标端口 67 的入站 UDP 源端口 68 收到 DHCP 发现，DHCP 请求和 DHCP 通知的数据包。
DHCP 提供和 DHCP 确认和 DHCP NACK 数据包可以通过目标端口 68 到出站 UDP 源端口 67 传输。

### <a name="filterdriverwindowsfilteringplatformnetworkingfundamentalsupportipv4"></a>Filter.Driver.WindowsFilteringPlatform.NetworkingFundamental.SupportIPv4

*基于 WFP 的产品必须支持的 IPv4 通信。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

这是为了确保使用者主机防火墙或其他过滤组件不会丢失的 IPv4 连通 PC 上。
*支持*单词是指*主机防火墙功能*使 IPv4 起作用，如果应用程序/用户/网络需要它。 主机防火墙还必须具有正确配置对象，例如，筛选器，以支持所需的功能，即使可能未启用功能，默认情况下，用户界面中。

*设计备注︰*IPv4 的更多信息，可以在下面的链接中找到 Rfc: <http://go.microsoft.com/fwlink/?LinkID=116835&clcid=0x409>

### <a name="filterdriverwindowsfilteringplatformnetworkingfundamentalsupportipv6"></a>Filter.Driver.WindowsFilteringPlatform.NetworkingFundamental.SupportIPv6

*基于 WFP 的产品必须支持 IPv6 通信量。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

Windows® 具有默认情况下启用 IPv6。 主机防火墙不应该中断本机 IPv6 连通性 （和因此，基于 IPv6 的 Windows 方案） 的客户。

*支持*单词是指*主机防火墙功能*进行 IPv6 的工作，如果应用程序/用户/网络需要它。 主机防火墙还必须具有正确配置对象，例如，筛选器，以支持所需的功能，即使可能未启用功能，默认情况下，用户界面中。

*设计备注︰*有关 IPv6 的更多信息可在以下链接︰ <http://go.microsoft.com/fwlink/?LinkID=116832&clcid=0x409>

### <a name="filterdriverwindowsfilteringplatformnetworkingfundamentalsupportnameresolution"></a>Filter.Driver.WindowsFilteringPlatform.NetworkingFundamental.SupportNameResolution

*基于 WFP 的产品必须支持允许成功的 DNS 客户端查询。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

可以发送 DNS 查询数据包转移出\[出站 UDP 目标端口 53 （域名服务器）\]和 DNS 查询响应数据包，通过接收\[入站 UDP 源端口 53 （域名服务器）\]。 主机防火墙应允许成功的 DNS 客户端查询通过 IPv4 和 IPv6。
*支持*单词是指*主机防火墙功能*允许成功的 DNS 客户端查询，如果应用程序/用户/网络需要它。 主机防火墙还必须具有正确配置对象，例如，筛选器，以支持所需的功能，即使可能未启用功能，默认情况下，用户界面中。

*设计备注︰*有关 DNS 的详细信息，可以在以下链接中找到 Rfc: <http://go.microsoft.com/fwlink/?LinkID=116835&clcid=0x409>主机防火墙都应该允许这种类型的 （作为服务器的主机） 的 DNS 通信量通过无线接口服务如 ICS 主机上运行时。
此要求适用于 Internet 连接共享，它就像一个 DNS 服务器 （代理服务器） 和期望接收传入的 UDP 端口 53，目标客户端的 DNS 请求和响应 DNS 客户端与目标 UDP 端口 53 的 DNS 响应。

### <a name="filterdriverwindowsfilteringplatformscenariosupport6to4"></a>Filter.Driver.WindowsFilteringPlatform.Scenario.Support6to4

*基于 WFP 的产品必须支持 6to4。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

在某些市场，6to4 技术可以帮助某些客户迁移到 IPv6 连接。 下列准则可帮助满足这一要求︰

-   主机防火墙允许系统以发送和接收通过 IPv4 协议 41 的 IPv6 数据包。

*支持*word 指 6to4 工作*主机防火墙的功能*，如果应用程序/用户/网络需要它。 主机防火墙还必须具有正确配置对象，例如，筛选器，以支持所需的功能，即使可能未启用功能，默认情况下，用户界面中。

*设计备注︰*以下文章下面有关 6to4 的详细信息，请参阅︰ <http://go.microsoft.com/fwlink/?LinkID=116837&clcid=0x409>
 

### <a name="filterdriverwindowsfilteringplatformscenariosupportautomaticupdates"></a>Filter.Driver.WindowsFilteringPlatform.Scenario.SupportAutomaticUpdates

*在 Windows 中，WFP 基于产品必须支持自动更新。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

这与自动更新 Windows 更新 (WU)，这是通过其重要修补程序安装到计算机，以使其保持最新的主要方案。 下面的准则有助于满足这一要求︰
 

-   主机防火墙允许出站 TCP 连接到目标端口 80 和 443。

*支持*单词是指*主机防火墙的功能*以使自动更新工作，如果应用程序/用户/网络需要它。 主机防火墙还必须具有正确配置对象，例如，筛选器，以支持所需的功能，即使可能未启用功能，默认情况下，用户界面中。

*设计备注︰*了解更多有关 Windows 更新 / 自动更新，请参阅下面的链接︰ <http://go.microsoft.com/fwlink/?LinkID=116898&clcid=0x409>

### <a name="filterdriverwindowsfilteringplatformscenariosupportbasicwebsitebrowsing"></a>Filter.Driver.WindowsFilteringPlatform.Scenario.SupportBasicWebsiteBrowsing

*基于 WFP 的产品必须支持基本的互联网浏览体验。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

这是为了确保在 Windows 上的主机防火墙安装支持的基本互联网浏览体验&ndash;基于计算机。
主机防火墙必须允许 TCP 数据包通过端口 80 和 443，来支持此方案。 这种情况下必须使用本机 IPv4、 本机 IPv6，6to4 和 Teredo 数据包。
*支持*单词是指*主机防火墙功能*以确保成功的互联网浏览体验，如果应用程序/用户/网络需要它。 主机防火墙还必须具有正确配置对象，例如，筛选器，以支持所需的功能，即使可能未启用功能，默认情况下，用户界面中。

### <a name="filterdriverwindowsfilteringplatformscenariosupportfileandprintersharing"></a>Filter.Driver.WindowsFilteringPlatform.Scenario.SupportFileAndPrinterSharing

*基于 WFP 的产品必须支持文件和打印机共享。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

这是为了确保家庭用户将能够共享内容与在其家庭网络中，除了在共享打印机上的打印内容外的其他 Pc。
主机防火墙必须允许 UDP 数据包特定于端口 137 协议 17 / 138 和特定于协议 6 139/445 端口的 TCP 数据包。 这种情况下必须使用本机 IPv4、 本机 IPv6，6to4 和 Teredo 数据包。
TCP 数据包应允许通过端口 5357/5358 和 UDP 数据包应允许通过端口 3702。 这种情况下应使用本机 IPv4、 本机 IPv6，6to4 和 Teredo 数据包。
*支持*单词是指*主机防火墙功能*进行文件和打印机共享的工作，如果应用程序/用户/网络需要它。 主机防火墙还必须具有正确配置对象，例如，筛选器，以支持所需的功能，即使可能未启用功能，默认情况下，用户界面中。

*设计备注︰*下面的链接的详细信息，请参阅︰                 <http://go.microsoft.com/fwlink/?LinkID=116838&clcid=0x409>

请参考下面的文档的详细信息︰

-   家庭组防火墙要求︰ <http://technet.microsoft.com/en-us/appcompat/default.aspx>

-   网络位置对话框︰ <http://technet.microsoft.com/en-us/appcompat/default.aspx>

-   PNRP: <http://technet.microsoft.com/en-us/appcompat/default.aspx>

### <a name="filterdriverwindowsfilteringplatformscenariosupporticmperrormessages"></a>Filter.Driver.WindowsFilteringPlatform.Scenario.SupportICMPErrorMessages

*基于 WFP 的产品必须支持 ICMP 错误消息和发现功能。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

这是为了确保主机防火墙支持 ICMP 错误消息 （每个 IETF Rfc 4890 和 RFC 2979），必须除去的入站/出站数据包。 此外必须支持重要的发现功能。 需要为 ICMPv4 和 ICMPv6 支持特定的错误消息︰ 无法到达目标、 超出时间，和参数问题。 此外，ICMPv6、 数据包太大，路由器请求、 相邻节点请求、 路由器通告和相邻节点通告必须支持搜索功能。
*支持*单词是指*主机防火墙功能*使 ICMP 处理时，如果应用程序/用户/网络需要它。 主机防火墙还必须具有正确配置对象，例如，筛选器，以支持所需的功能，即使可能未启用功能，默认情况下，用户界面中。

*设计备注︰*有关详细信息，请参见<http://go.microsoft.com/fwlink/?LinkID=116835&clcid=0x409>

### <a name="filterdriverwindowsfilteringplatformscenariosupportinternetstreaming"></a>Filter.Driver.WindowsFilteringPlatform.Scenario.SupportInternetStreaming

*基于 WFP 的产品必须支持流式处理的互联网和媒体共享的媒体玩家网络共享服务。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

这与自动更新 Windows 更新 (WU)，这是通过其重要修补程序安装到计算机，以使其保持最新的主要方案。 下列准则可帮助满足这一要求︰

主机防火墙允许出站 TCP 连接到目标端口 80 和 443。
*支持*单词是指*主机防火墙的功能*以使自动更新工作，如果应用程序/用户/网络需要它。 主机防火墙还必须具有正确配置对象，例如，筛选器，以支持所需的功能，即使可能未启用功能，默认情况下，用户界面中。

*设计备注︰*了解更多有关 Windows 更新 / 自动更新，请参阅下面的链接︰ <http://go.microsoft.com/fwlink/?LinkID=116898&clcid=0x409>

 

### <a name="filterdriverwindowsfilteringplatformscenariosupportmediaextenderstreaming"></a>Filter.Driver.WindowsFilteringPlatform.Scenario.SupportMediaExtenderStreaming

*基于 WFP 的产品必须支持媒体流基于扩展的技术方案。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

扩展程序技术内置于家庭娱乐设备，如电视、 DVD 播放机和冷却、 安静，可以使您的 PC 有意义的组件和使用它为中心的整个家向电视提供数字娱乐活动。 这些设备被称为扩展器设备。
例如︰ 与新扩展程序的 Windows Media Center，可以传输数字媒体对 Windows Media Center PC 中家中多达五个房间。 家庭用户可以访问通过有线或无线家庭网络直播和录制的电视、 音乐、 电影、 视频、 体育、 互联网电视和 Windows® Pc 上的其他联机内容。 Windows 媒体中心扩展器使用的网络端口与 Windows Pc 进行通讯。 以下各表的异常可能会有用在满足这一要求。

**表 1。媒体中心扩展器 – 特定**
<table>
<tr><th>二进制可执行文件</th><th>端口</th><th>方向</th><th>Scope</th></tr>
<tr><td>svchost.exe (ssdpsrv)</td><td>UDP 1900</td><td>入站</td><td>本地子网</td></tr>
<tr><td>svchost.exe (termservice)</td><td>TCP 3390</td><td>入站</td><td>本地子网</td></tr>
<tr><td>svchost.exe (QWave)</td><td>TCP 2177</td><td>出站、 入站</td><td>本地子网</td></tr>
<tr><td>svchost.exe (QWave)</td><td>UDP 2177</td><td>出站、 入站</td><td>本地子网</td></tr>
<tr><td> System</td><td>TCP 10244</td><td>出站、 入站</td><td>本地子网</td></tr>
<tr><td>ehshell.exe</td><td>TCP 554</td><td>出站、 入站</td><td>本地子网</td></tr>
<tr><td>ehshell.exe</td><td>UDP 5004 5005</td><td>出站、 入站</td><td>本地子网</td></tr>
<tr><td>ehshell.exe</td><td>TCP 8554 8558</td><td>出站、 入站</td><td>本地子网</td></tr>
<tr><td>ehshell.exe</td><td>UDP 50004 50013</td><td>出站、 入站</td><td>本地子网</td></tr>
<tr><td>ehshell.exe</td><td>UDP 7777 7781</td><td>出站、 入站</td><td>本地子网</td></tr>
<tr><td>mcrmgr.exe</td><td>随机</td><td>出站</td><td>Internet</td></tr>
<tr><td>mc2prov.exe</td><td>随机</td><td>出站</td><td>Internet</td></tr>
<tr><td>Svchost.exe (mcs2svc)</td><td>随机</td><td>出站</td><td>本地子网</td></tr>
</table>

**表 2。Media Center 的二进制可执行程序和端口**

<table>
<tr><th>二进制可执行文件</th><th>端口</th><th>方向</th><th>Scope</th></tr>
<tr><td>ehrecvr.exe</td><td>随机</td><td>出站</td><td>Internet</td></tr>
<tr><td>ehrec.exe</td><td>随机</td><td>出站</td><td>Internet</td></tr>
<tr><td>ehexthost.exe</td><td>随机</td><td>出站、 入站</td><td>Internet</td></tr>
<tr><td>mcupdate.exe</td><td>随机</td><td>出站</td><td>Internet</td></tr>
</table>

**表 3。数字有线电视接收器设备 (OCUR)**

<table>
<tr><th>二进制可执行文件</th><th>端口</th><th>方向</th><th>Scope</th></tr>
<tr><td>ehprivjob.exe</td><td>UDP 5001 5006</td><td>入站</td><td>本地子网</td></tr>
<tr><td>svchost.exe</td><td>UDP 1900</td><td>出站、 入站</td><td>本地子网</td></tr>
<tr><td>System</td><td>TCP 2869</td><td>出站、 入站</td><td>本地子网</td></tr>
<tr><td>ehprivjob.exe</td><td>TCP 554</td><td>出站</td><td>本地子网</td></tr>
<tr><td>ehprivjob.exe</td><td>UDP 5757 5772</td><td>出站</td><td>本地子网</td></tr>
</table>
 
*支持*单词指*主机防火墙的功能*，以使互联网流和媒体共享的媒体玩家网络共享服务、 起作用，如果应用程序/用户/网络需要它。 主机防火墙还必须具有正确配置对象，例如，筛选器，以支持所需的功能，即使可能未启用功能，默认情况下，用户界面中。

### <a name="filterdriverwindowsfilteringplatformscenariosupportmobilebroadband"></a>Filter.Driver.WindowsFilteringPlatform.Scenario.SupportMobileBroadBand

*基于 WFP 的产品必须允许移动宽带设备符合 Windows 移动宽带驱动程序模型才能正常工作。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

基于 WFP 的产品必须允许符合正常的 Windows 移动宽带驱动程序模型的移动宽带设备。
这是为了确保主机防火墙功能不会阻止移动宽带连接和防火墙功能适用于 MB 设备。
Windows 提供本机支持移动宽带 (MB) 数据卡和嵌入模块使用 Windows。 MB 设备需要实现 Windows 移动宽带驱动程序模型根据其驱动程序。 MB 的驱动程序模型定义应如何为 Windows 和网络数据包格式 MB 设备应在其中交换网络和系统之间的数据公开设备。

### <a name="filterdriverwindowsfilteringplatformscenariosupportpeernameresolution"></a>Filter.Driver.WindowsFilteringPlatform.Scenario.SupportPeerNameResolution

*对等名称解析协议和对等分组协议，必须支持基于 WFP 的产品。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

对等名称解析协议 (PNRP) 和对等分组协议，某些对等应用程序所需的主机防火墙都支持。 对等名称解析协议提供了安全、 无服务器的名称解析，并对等分组协议提供安全、 可靠的多方通信。 以下准则可能有助于满足这一要求︰

1.  主机防火墙支持本机 IPv6 (网络-0244) 以及 Teredo (网络 0248) 和 41 的 IPv4 协议 IPv6 数据包 (^ to4) (网络-0249)。

2.  主机防火墙可以为系统可以发送出站的收发站，UDP 数据包通过端口 3540。

3.  主机防火墙可以为系统可以发送出站的收发站，TCP 数据包通过端口 3587。

*支持*单词是指*主机防火墙的功能*，允许成功 DHCP 交换，如果应用程序/用户/网络需要它。 主机防火墙还必须具有正确配置对象，例如，筛选器，以支持所需的功能，即使可能未启用功能，默认情况下，用户界面中。

*设计备注*︰

请参阅以下文档以这些文档的详细信息︰
 

-   家庭组防火墙要求︰ <http://technet.microsoft.com/en-us/appcompat/default.aspx>

-   网络位置对话框︰ <http://technet.microsoft.com/en-us/appcompat/default.aspx>

-   PNRP: <http://technet.microsoft.com/en-us/appcompat/default.aspx>

### <a name="filterdriverwindowsfilteringplatformscenariosupportremoteassistance"></a>Filter.Driver.WindowsFilteringPlatform.Scenario.SupportRemoteAssistance

*基于 WFP 的产品必须支持远程协助方案。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

一个帮助器连接到计算机，并显示问题的解决方案的用户使用远程协助方案。 下列准则可帮助满足这一要求︰ 主机防火墙允许计算机能达到通过本机 IPv4，本机 IPv6，Teredo，6to4 （通过相应测试），还允许从远程协助应用程序 Windows® (msra.exe) 中通过防火墙的通信。
*支持*单词是指*主机防火墙功能*若要使远程协助工作，如果应用程序/用户/网络需要它。 主机防火墙还必须具有正确配置对象，例如，筛选器，以支持所需的功能，即使可能未启用功能，默认情况下，用户界面中。

*设计备注︰*有关远程协助的一般工作方式的信息，请参阅以下文章︰ <http://go.microsoft.com/fwlink/?LinkID=116842&clcid=0x409>
 

### <a name="filterdriverwindowsfilteringplatformscenariosupportremotedesktop"></a>Filter.Driver.WindowsFilteringPlatform.Scenario.SupportRemoteDesktop

*基于 WFP 的产品必须支持远程桌面。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

远程桌面连接是一种技术，使您可以连接到不同的位置中的远程计算机。 远程桌面是关键的 Windows® 方案，用于在多台 Pc 与消费者家庭试图访问存在于一台 PC，从另一台计算机的内容就更加密切。
下面的准则有助于满足这一要求︰

主机防火墙允许通过来支持此方案的目标端口 3389 的入站的 TCP 数据包。 这种情况下需要使用本机 IPv4、 本机 IPv6，6to4 和 Teredo 数据包。
*支持*单词是指*主机防火墙的功能*以使远程桌面的工作，如果应用程序/用户/网络需要它。 主机防火墙还必须具有正确配置对象，例如，筛选器，以支持所需的功能，即使可能未启用功能，默认情况下，用户界面中。

*设计备注︰*有关远程桌面的详细信息，请参阅以下文章︰ <http://go.microsoft.com/fwlink/?LinkID=116841&clcid=0x409>

### <a name="filterdriverwindowsfilteringplatformscenariosupportteredo"></a>Filter.Driver.WindowsFilteringPlatform.Scenario.SupportTeredo

*基于 WFP 的产品必须支持 Teredo。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

Teredo 可能作为连接机制，用于支持远程协助、 即时消息和其他人等某些 Windows 方案。 因此，保留 Teredo 连接是支持 Windows 使用者方案的关键。
这种要求，以下必须满足︰

-   主机防火墙允许 DNS 解析的 teredo.ipv6.microsoft.com。

-   若要允许客户端到服务器通信 Teredo，主机防火墙必须允许将出站 UDP/IPv4 数据包发送到 UDP 端口 3544 系统。

-   为了让 Teredo 连接，主机防火墙必须通过 Teredo 客户端系统端口允许入站和出站 UDP/IPv4 通信。 这些端口可以使用 FWPMSystemPortsGet 通知确定用于使用 Teredo 接口进行通信系统端口号。

-   主机的防火墙支持 ICMP 错误消息和发现函数 （网络 0250年徽标要求）。

-   主机防火墙允许通过 UDP 端口 1900，UPnP 框架数据包并通过 TCP 端口 2869 UPnP frameworkpackets。

*支持*单词是指*主机防火墙功能*使 Teredo 起作用，如果应用程序/用户/网络需要它。 主机防火墙还必须具有正确配置对象，例如，筛选器，以支持所需的功能，即使可能未启用功能，默认情况下，用户界面中。

*设计备注︰*以下文章下面 Teredo 有关的详细信息，请参阅︰ <http://go.microsoft.com/fwlink/?LinkID=116836&clcid=0x409>

### <a name="filterdriverwindowsfilteringplatformscenariosupportvirtualprivatenetworking"></a>Filter.Driver.WindowsFilteringPlatform.Scenario.SupportVirtualPrivateNetworking

*在 Windows 中，WFP 基于产品必须支持 VPN 方案。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

必须允许下列协议和端口︰

-   IP 协议 50︰ 允许 ESP 通讯            

-   IP 协议 51︰ 允许 AH 通信            

-   UDP 端口 500 / 4500︰ 允许 ISAKMP 通信           

-   TCP / UDP 端口 88︰ 允许 Kerberos 通信

这将确保防火墙支持 IPsec 方案，如 IPsec VPN 可用于在客户端 Pc 上通过 internet 安全地连接。
此外，主机防火墙应该允许通过 IPv4 和 IPv6 的成功的 IPsec 通信。 主机防火墙还允许通过端口 1701，UDP 数据包和 TCP 数据包通过端口 443 来支持此方案。 它还建议主机防火墙允许 TCP 数据包特定在端口 1723年上。 此外应通过主机防火墙允许 IP 协议 47 基于数据包。
*支持*单词是指*主机防火墙的功能*以使 VPN 方案工作，如果应用程序/用户/网络需要它。 主机防火墙还必须具有正确配置对象，例如，筛选器，以支持所需的功能，即使可能未启用功能，默认情况下，用户界面中。

*设计备注︰*以下文章有关的详细信息，请参阅︰ <http://go.microsoft.com/fwlink/?LinkID=116843&clcid=0x409>

### <a name="filterdriverwindowsfilteringplatformscenariovswitchinteropwithotherextensions"></a>Filter.Driver.WindowsFilteringPlatform.Scenario.vSwitch.InteropWithOtherExtensions

*WFP 必须不阻止来自另一个 vSwitch 扩展 （WFP 或 LWF） 通信，默认情况下，才应这样做时遵循特定的用户管理意图及保护系统受到特定的威胁。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

WFP 必须不阻止来自另一个 vSwitch 扩展 （WFP 或 LWF） 通信，默认情况下，才应这样做时遵循特定的用户管理意图及保护系统受到特定的威胁。

### <a name="filterdriverwindowsfilteringplatformscenariovswitchnoegressmodification"></a>Filter.Driver.WindowsFilteringPlatform.Scenario.vSwitch.NoEgressModification

*在 vSwitch 中运行的基于 WFP 的产品不能修改的 vSwitch 出口路径上的数据包。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

在 vSwitch 中运行的基于 WFP 的产品不能修改的 vSwitch 出口路径上的数据包。

### <a name="filterdriverwindowsfilteringplatformscenariovswitchsupportlivemigration"></a>Filter.Driver.WindowsFilteringPlatform.Scenario.vSwitch.SupportLiveMigration

*在 vSwitch 中运行的基于 WFP 的产品必须出示小 MOF 用于实时迁移。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

在 vSwitch 中运行的基于 WFP 的产品必须出示小 MOF 用于实时迁移。 在 MOF 中，它必须声明本身徽标符合实时迁移并允许自行迁移或默认情况下阻止迁移。 实时迁移的迁移的总时间不能超过 2 秒钟。

### <a name="filterdriverwindowsfilteringplatformscenariovswitchsupportremoval"></a>Filter.Driver.WindowsFilteringPlatform.Scenario.vSwitch.SupportRemoval

*必须允许运行在 vSwitch 的基于 WFP 的产品管理员禁用 WFP vSwitch 实例时被删除。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

必须允许运行在 vSwitch 的基于 WFP 的产品管理员禁用 WFP vSwitch 实例时被删除。

### <a name="filterdriverwindowsfilteringplatformscenariovswitchsupportreordering"></a>Filter.Driver.WindowsFilteringPlatform.Scenario.vSwitch.SupportReordering

*在 vSwitch 中运行的基于 WFP 的产品必须响应 WFP vmSwitch 重新排序事件。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

在 vmSwitch 中运行的基于 WFP 的产品必须响应 WFP vmSwitch 重新排序事件。
