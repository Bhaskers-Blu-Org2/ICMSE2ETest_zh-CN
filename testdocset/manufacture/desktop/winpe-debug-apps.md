---
author: Justinha
Description: "WinPE︰ 调试应用程序"
ms.assetid: 30fe59bc-f169-4534-b5a5-dbe58a10cb83
MSHAttr: PreferredLib:/library/windows/hardware
title: "WinPE︰ 调试应用程序"
ms.openlocfilehash: ef34d5de6f3a443b5f058fb0ed4703be98f79d93
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="winpe-debug-apps"></a>WinPE︰ 调试应用程序


调试应用程序的 Windows PE 和调试 Windows PE 内核，您可以使用 Windows 调试，如 Ntsd.exe、 Cdb.exe，和 Windbg.exe，以及支持工具。 [Windows 10 SDK]( http://go.microsoft.com/fwlink/?LinkId=526807)中包含的调试工具。 通过本地复制或从共享使用它们，必须使调试工具可用应用 Windows PE 的计算机上。

若要远程调试 Windows PE，可能需要关闭电脑上的内置防火墙︰

``` syntax
wpeutil disablefirewall
```

## <a name="span-iduser-modedebuggingspanspan-iduser-modedebuggingspanspan-iduser-modedebuggingspanuser-mode-debugging"></a><span id="User-mode_debugging"></span><span id="user-mode_debugging"></span><span id="USER-MODE_DEBUGGING"></span>用户模式调试


最简单的用户模式调试方法是运行在 Windows PE 计算机上，进程内服务器并在另一台计算机上使用调试器连接到它。 进程内服务器将包含在[Windows 10 SDK]( http://go.microsoft.com/fwlink/?LinkId=526807)中的调试工具。

**若要在用户模式下运行流程服务器**

1.  复制 Windows 调试进程内服务器工具︰ **dbgsrv.exe**， [Windows 10 SDK]( http://go.microsoft.com/fwlink/?LinkId=526807)调试工具文件夹中 (示例︰ c:\\程序文件 (x86)\\窗口工具包\\10.0\\调试器\\x64)，到 Windows PE 的计算机。

2.  在 Windows PE 命令提示符下，禁用防火墙。

    ``` syntax
    wpeutil disablefirewall
    ```

3.  启动 Windows 调试流程服务器，指定方法连接到 PC 时，例如，TCP 端口︰

    ``` syntax
    dbgsrv.exe -t tcp:port=1234
    ```

    有关详细信息，请参阅[激活流程服务器 （Windows 调试器）]( http://go.microsoft.com/fwlink/p/?LinkId=698645)。

4.  从远程计算机上，使用进程内服务器附加到或启动 Windows PE 在目标计算机上的进程︰

    ``` syntax
    windbg -premote tcp:server=Server, port=1234
    ```

    有关详细信息，请参阅[激活智能客户端 （Windows 调试器）](http://go.microsoft.com/fwlink/p/?LinkId=698646)。

它也是可以直接在 Windows PE 的计算机上运行调试器。 但是，这样做需要设置 Windows PE 计算机每次重启之后的符号和源路径。 我们建议您执行调试从运行完整版本的 Windows 的计算机，在此过程中所述。

当您想要绕过 startnet.cmd 或 setup.exe，并直接进入命令提示符出于调试目的，下面的调试过程很有用。 此过程会跳过所有的初始化，包括安装程序，并不运行任何命令，如 Wpeinit.exe。 必须联机在线操作系统上执行此过程。

**若要启用用户模式调试前的任何初始化**

1.  如果存在，请删除 winpeshl.ini 文件。 如果 winpeshl.ini 文件不存在，则用户模式调试无法访问默认情况。

2.  按住 Ctrl 键在启动过程中显示命令提示符之前。 出现命令提示符。

3.  继续进行调试。

## <a name="span-idkernel-modedebuggingspanspan-idkernel-modedebuggingspanspan-idkernel-modedebuggingspankernel-mode-debugging"></a><span id="Kernel-mode_debugging"></span><span id="kernel-mode_debugging"></span><span id="KERNEL-MODE_DEBUGGING"></span>内核模式调试


若要调试在内核模式下，您必须启用内核模式调试引导系统之前。 启动配置文件有一个通过使用 bcdedit.exe 命令行工具来修改引导配置数据 (BCD) 存储启用内核模式调试，设置。 只能通过使用 bcdedit.exe 执行内核调试。 Bcdedit.exe 位于\\Windows\\的 Windows 分区 System32 目录。

默认调试器设置，如下所示︰

``` syntax
----------------- 
identifier              {dbgsettings} 
debugtype               Serial 
debugport               1 
baudrate                115200
```

为虚拟机环境中创建 Iso，创建 ISO 之前启用内核中的 BCD 条目。

有关如何修改默认 BCD 存储 (default.bcd)，请参阅[如何修改 BCD 存储使用 Bcdedit](http://go.microsoft.com/fwlink/p/?LinkId=698647)。

**若要启用内核模式调试**

1.  查找 BCD 存储，包含在一个名为**bcd**文件。 该文件位于根目录中包含 Windows PE 映像的介质的启动目录中。

2.  在命令提示符下，键入以下 bcdedit 命令来设置调试标志用来引导到映像的 BCD 存储的`debug on`:

    ``` syntax
    bcdedit /store <path to winpe>/boot/bcd /set {default} debug on
    ```

    `{default}`可能需要替换为唯一标识符 (UID)，Windows PE 的启动选项。

    另外，您还可以启用内核调试在启动过程中按 f8 键，然后选择调试选项。

    **请注意**  
    若要使用符号服务器从 Windows PE 中的，使用`net use`上的符号服务器的命令和文件共享。

     

有关控制调试的命令行选项的详细信息，请参阅[BCDEdit 命令行选项](http://go.microsoft.com/fwlink/p/?LinkId=526808)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[对于 Windows 10 WinPE](winpe-intro.md)

[WinPE︰ 安装和自定义](winpe-mount-and-customize.md)

[Wpeutil 命令行选项](wpeutil-command-line-options.md)

[Winpeshl.ini 引用︰ 启动 WinPE 时启动应用程序](winpeshlini-reference-launching-an-app-when-winpe-starts.md)

[BCDEdit 命令行选项](http://go.microsoft.com/fwlink/p/?LinkId=526808)

 

 






