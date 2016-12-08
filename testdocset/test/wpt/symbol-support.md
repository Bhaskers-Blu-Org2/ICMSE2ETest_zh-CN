---
title: "符号的支持"
description: "符号的支持"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 3f4fcf1c-9d81-4842-82e5-a443f47f5255
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: e56183594911e2b74a65bc6ff9663615a42e8bbb
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="symbol-support"></a>符号的支持


如果正确配置 Windows 性能分析器 (WPA)，WPA 显示从记录中找到的地址的符号文件的符号名称。

要解码的符号，这些工具必须找到已知为程序数据库 (PDB) 文件或符号文件，构建完整的调用堆栈的程序数据库文件。 编译器和链接器生成 PDB 文件系统生成一个组件时。 Microsoft 提供许多 Microsoft 产品在线符号服务器中的数据库文件的程序。 Microsoft Windows 调试工具和 WPA 使用联机符号服务器查找符号的信息。 因此，计算机必须连接到互联网如果没有本地复制的符号文件。 Windows 性能 Toolkit 使用同一个符号解码为 Windows 调试器， **Windbg.exe**基础结构。 有关详细信息，请参阅[WinDbg](http://go.microsoft.com/fwlink/p/?linkid=212249)。

若要配置符号支持，您必须定义**\_NT\_符号\_路径**环境变量。 下面的示例设置符号路径，使用 Microsoft 公共符号服务器以及下游存储在 c:\\符号︰

``` syntax
set _NT_SYMBOL_PATH= srv*C:\symbols*http://msdl.microsoft.com/downloads/symbols
```

请注意，此示例是一个命令行。

在此符号路径的 URL 指定联机 Microsoft 符号服务器。 星号之间的路径 (c:\\符号) 指定的下游的存储区。 这是本地缓存的符号解析系统保留的符号文件。 WPA 工具还对开发的组件中的符号进行解码。 添加到一个或多个路径**\_NT\_符号\_路径**包含您想要记录的组件的 PDB 文件。 例如，下面的示例演示该路径对于前面的示例的设置的方式︰

``` syntax
set _NT_SYMBOL_PATH=c:\coding\fs\release;srv*C:\symbols*
```

当 Xperf 或 WPA 解码 Xperf 的符号或 WPA 缓存在磁盘上的精简的版本的符号源文件或 Pdb， ** \\symcache**目录。 为此，Xperf 或 WPA 使用时是可用的符号。 有 Microsoft 以外的操作系统符号是公共符号。 这些符号包含较少比内部私有符号的信息。 在黑箱测试中，公共符号也可以包括不正确的信息。 专用的符号，是更可靠，可获得在保密协议下。 如果用户已使用的公共符号，解码录制，并且用户然后获得私有符号，用户必须清除**\\symcache**目录之前 Xperf 或 WPA 可以发现新的私有符号。

## <a name="troubleshooting-symbol-decoding"></a>诊断符号进行解码


符号解码支持是复杂的。 必须满足以下要求︰

-   您必须指定`-symbols`Xperf 在命令行或后打开录制在 WPA 的**跟踪**菜单上选择**加载符号**。

-   必须正确配置的环境变量。 对于 Xperf 的详细信息，请参见[符号](symbols.md)。

-   ETW 内核录制文件必须被停止并正确合并。 有关详细信息，请参阅[停止录制](stop-a-recording.md)。

-   Windows 性能记录器 (WPR) 或 WPA 合并 ETW 用户录制文件和内核录音文件，同时在同一台计算机上执行。

-   您必须具有访问该二进制文件和源代码中的符号**\_NT\_符号\_路径**指定。 如果您使用符号服务器，只需重定向器通常是符号服务器。 在这种情况下，您必须访问符号服务器和符号服务器指向的二进制文件和符号所承载的网站。

-   ** \_NT\_符号\_路径**必须指向正确的文件。 如果从一个不同的生成或体系结构存在这些文件，这些文件将无法工作。 如果应用程序二进制文件的版本不是符号版本相同的**\_NT\_符号\_路径**点到，您不能查看调用堆栈。

    要判断符号不匹配，请使用**Windows 调试工具**分发从**Symchk.exe**以确保符号匹配所采取录制计算机上的符号文件。 例如︰

    ``` syntax
    symchk /v <local_file> /s <sympath_to_name.pdb>
    ```

    要判断一个二进制的不匹配，请使用`fc /b`命令，确保在其拍摄录制的计算机上的二进制文件与匹配上放置共享的二进制文件。 例如︰

    ``` syntax
    fc /b <local_file> <drop_share_file>
    ```

-   在 Xperf，您必须捕获 ETW 内核使用记录至少`PROC_THREAD+LOADER`标志。 这些标志提供有关进程的生存期内，图像的基本信息在内存中进程的虚拟地址范围。 此信息可帮助 XPerf 解码图像和符号的虚拟地址。

    若要验证是否已启用这些标志了 ETW 内核录制中，请检查该 Xperf **-过程**事件 （**创建**、**删除**、**启动断开**、**结束断开**） 和**图像**事件**加载**、**卸载**、**启动断开**（**结束断开**） 都使用下面的命令生成的表中︰

    ``` syntax
    xperf -i kernel.etl -a tracestats -detail
    ```

    **请注意**  
    所有这些事件可能未列入表中，这取决于是否发生了这些事件。

     

### <a name="limitation-in-xperf-symbol-decoding"></a>Xperf 符号解码中的限制

Xperf 默认为系统驱动器，如果驱动器未指定可执行图像 (如**\\路径\\Library.dll**)。 当您运行`-d/-merge`命令，Xperf Xperf 找存在的可执行映像中正在运行的进程在录制过程中，如果不能检索相应的图像和符号文件的标识信息和将信息添加到合并的记录。 如果没有该信息，Xperf 无法执行符号解码该录制中的图像。

此问题不会影响其他的文件路径，如磁盘 I/O 或文件 I/O 路径。

若要启用符号进行解码并帮助启用正确的图像加载和卸载路径 Xperf ETW 录制中的，应将存储可能需要符号进行解码或图像加载和卸载路径在系统驱动器上的所有可执行映像。 然后，从该驱动器运行图像。 如果这是不可能的在系统驱动器上，创建映像的镜像即使您从其他驱动器运行图像。 例如，如果您的系统驱动器 c:，创建副本的**d:\\游戏\\bin\\binkw32.dll**在**c:\\游戏\\bin\\binkw32.dll**。

## <a name="related-topics"></a>相关的主题


[Windows 性能 Toolkit](index.md)

[符号](symbols.md)

[使用 CLR 4.0 NGEN PDB 支持](using-clr-40-ngen-pdb-support.md)

[深入分析常见问题](../assessments/common-in-depth-analysis-issues.md)

 

 







