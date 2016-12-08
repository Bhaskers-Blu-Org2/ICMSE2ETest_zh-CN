---
title: "加载符号"
description: "加载符号"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: db27f063-0ae8-4762-8df4-66e3d14e55ed
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: aba08b62d0207c1c26054849b1e68cf3f9186c3b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="loading-symbols"></a>加载符号


在 Windows 性能分析器 (WPA)，可以设置下列用户首选项︰

-   **加载符号**

-   **配置符号路径**

若要更改这些选项，请打开录制，然后选择**跟踪**菜单中的选项。

在这篇文章︰

-   [托管的符号](#mansym)

-   [相对路径和嵌入式的环境变量](#relative)

-   [SymCache 路径](#symcachepath)

-   [符号路径](#symbolpath)

## <a name="a-href-idmansymamanaged-symbols"></a><a href="" id="mansym"></a>托管的符号


在下列系统上支持符号解析和受管理的进程的堆栈︰

-   与.NET Framework 4.5 或更高版本的 Windows 8 或更高版本

-   与.NET Framework 4.0 或更高版本在 x86 机

当您通过使用 WPR 捕获跟踪时、 WPR 使需解析托管的符号跟踪中的所有提供程序。 WPR 创建文件夹旁边这些托管符号的 PDB 文件包含已保存的跟踪。 当 WPA 打开跟踪时，WPA 查找此文件夹并自动将其添加到符号路径。 如果 WPR 不被用来生成跟踪，则任何符号的.NET Framework 程序可能不完全解码或根本解码。

## <a name="javascript-symbols"></a>JavaScript 的符号


符号解析和堆栈的 JavaScript 流程支持在运行下列软件的系统:

-   与 Internet Explorer 10 或更高版本的 Windows 7

-   在 Windows 8 使用 JavaScript 应用程序

WP 会使必需的提供程序进行解码为受支持的系统上的 JavaScript 代码的符号。 JavaScript 方法地址和堆栈帧解码到 JavaScript 文件名称、 方法名称、 行号和列号。

## <a name="a-href-idrelativearelative-paths-and-embedded-environment-variables"></a><a href="" id="relative"></a>相对路径和嵌入式的环境变量


** \_NT\_符号\_路径**和**\_NT\_SYMCACHE\_路径**环境变量可以使用相对路径、 绝对路径、 网络共享的路径，或嵌入的环境变量。 第一次设置相对路径时，WPA 将相对路径转换为绝对路径。 WPA 将 WPA 从环境变量在程序启动时将加载的相对路径。

WPA 转换您关闭对话框时，在**配置符号路径**对话框中输入的相对路径。 对当前目录的更改不影响已设置的相对路径。 **配置符号路径**对话框中显示的当前设置当您首次打开对话框中的路径框中，以便您可以看到 WPA 展开任何相对路径的方式。

WPA 扩展相对路径的同时扩展了嵌入式的环境变量。 WPA 捕获环境变量在程序启动时，由于对环境变量可能会超出当前运行的实例的 WPA 的更改未出现在该实例中。

使用其他程序**\_NT\_SYMCACHE\_路径**环境变量，如**WinDbg**或**Microsoft Visual Studio**时，可能无法处理相对路径或嵌入方式相同的环境变量。

## <a name="a-href-idsymcachepathasymcache-path"></a><a href="" id="symcachepath"></a>SymCache 路径


WPA 使用缓存符号信息以一种简洁、 易于访问的程序数据库 (PDB) 文件中的 SymCache 文件。 WPA 填充跟踪的符号的 SymCache 文件夹之后，重新加载该跟踪的符号是快得多。 如果 SymCache 文件变得太大，或者不再需要您可以安全地删除 SymCache 文件。 根据需要将 WPA 重新与新文件填充 SymCache 文件夹。 此外可以将 SymCache 文件复制到另一台计算机或通过网络以加快符号加载在不同的计算机上共享的文件。

如果您使用**配置符号路径**对话框来设置**\_NT\_SYMCACHE\_路径**环境变量对 WPA 无法访问，一个文件夹的**确定**按钮不会关闭对话框。 但是，您不会收到一条错误消息。

如果**\_NT\_SYMCACHE\_路径**环境变量未指定或为空，WPA WPA 的可执行文件所在的驱动器的根目录中创建的 SymCache 文件夹。 如果**\_NT\_SYMCACHE\_路径**在网络共享上运行环境变量，该变量包含程序文件文件夹的驱动器的根目录创建的 SymCache 文件夹。 这通常是驱动器 c。

### <a name="symcache-examples"></a>SymCache 示例

下面的命令将 SymCache 文件放置**c:\\SymCache**文件夹︰

``` syntax
C:\SymCache
```

下面的命令将 SymCache 文件放置**c:\\SymCache 文件夹**，搜索**\\\\网络\\SymCache**符号，然后进程文件夹**\_NT\_符号\_路径**环境变量︰

``` syntax
C:\SymCache*\\network\SymCache
```

本示例复制示例查找字符串中的任何符号**\\\\网络\\SymCache**文件夹复制到**c:\\SymCache**文件夹。 这使用户能够创建一个较大的 SymCache 文件夹，然后将复制到指定的文件夹，用户需要为特定的跟踪的文件。

若要搜索多个可选的 SymCache 文件夹，附加文件夹的搜索路径使用星号 (\*) 分隔符。 当 WPA 可选位置中的一个找到 SymCache 文件时，WPA 只到路径中的第一个 SymCache 文件夹中复制文件。 WPA 还将新创建的 SymCache 文件放入的路径中的第一个 SymCache 文件夹中。

要禁用复制和书写，但仍使用分层搜索功能时，您应该保持的第一个位置中的路径空，如下面的示例中所示︰

``` syntax
*\\network\SymCache
```

当发出此命令时，WPA 搜索\\**\\网络\\SymCache**文件夹。 但是，WPA 不将结果复制或写入生成的 SymCache 文件到另一个文件夹。

## <a name="a-href-idsymbolpathasymbol-path"></a><a href="" id="symbolpath"></a>符号路径


有关基本信息**\_NT\_符号\_路径**环境变量，请参阅下面的 MSDN 文章︰

-   [Symsrv 会使用](http://go.microsoft.com/fwlink/p/?linkid=226201)

-   [符号路径](http://go.microsoft.com/fwlink/p/?linkid=226202)

在 WPA 中加载的符号取决于路径的**\_NT\_符号\_路径**环境变量指定 （不包括符号 WPA 具有已缓存的 SymCache 文件夹中）。 WPA 搜索路径顺序，从左边开始。 但是，从这些路径之一 PDB 文件加载符号可能非常耗时，特别是在远程计算机上存在的 PDB。 因此，我们建议将网络路径放置之后任何本地路径和任何远程符号服务器使用本地的 PDB 缓存。 但是，即使所有符号都存储在本地，WPA 无反应期间加载符号的时间。 WPA 完成加载符号后返回交互状态。

当**\_NT\_符号\_路径**未设置环境变量，WPA 使用以下默认值︰

``` syntax
 .;SRV*\Symbols* http://msdl.microsoft.com/download/symbols;
```

分号 （;） 分隔的不同路径。 第一条路径是句点 （.）。 WPA 加载跟踪时，WPA 将该路径映射到当前文件夹。 请参阅本文有关 WPA 处理相对路径的方式的详细信息的[SymCache 的路径](#symcachepath)部分。

第二条路径是如下︰

``` syntax
 SRV*\Symbols* http://msdl.microsoft.com/download/symbols
```

您还必须设置 NGEN PB 路径︰

``` syntax
set _NT_SYMBOL_PATH=srv*C:\Symbols.NGEN;srv*http://msdl.microsoft.com/download/symbols
```

WPA 时指定此路径，请从 Microsoft 公共符号服务器下载符号和缓存中的 PDB 文件**\\符号**文件夹 （该文件夹是相对于 Windows 性能 Toolkit 安装文件夹）。 因此，WPA 放置符号文件夹旁边的 SymCache 文件夹。 但是，如果 SymCache 文件夹的网络共享上，WPA 就保留程序文件文件夹的驱动器的根目录创建符号文件夹。 这通常是驱动器 c。

如果不想搜索和加载 PDB 文件中的符号，您可以设置**\_NT\_符号\_路径**环境变量不包含符号，如句点 （.） 的本地文件夹。 不要让**\_NT\_符号\_路径**环境变量为空。 如果将**\_NT\_符号\_路径**环境变量为空，WPA 使用默认值。

当 WPA 打开录制时，WPA 查找具有跟踪使用**.ngenpdb**扩展名的名称相同的文件夹。 如果 WPA 找到此文件夹，WPA 结尾追加文件夹**\_NT\_符号\_路径**环境变量。 Windows 性能记录器 (WPR) 自动创建包含 WPR 捕获在录制过程中的托管代码的 PDB 文件的文件夹。 例如，如果您打开**c:\\trace.etl**录制在 WPA，WPA 搜索**c:\\trace.etl.ngenpdb**文件夹。 如果该文件夹存在，WPA 文件夹添加到文件夹**\_NT\_符号\_路径**环境变量。

## <a name="related-topics"></a>相关的主题


[WPA 功能](wpa-features.md)

[加载符号或符号路径进行配置](load-symbols-or-configure-symbol-paths.md)

[使用 CLR 4.0 NGEN PDB 支持](using-clr-40-ngen-pdb-support.md)

[深入分析常见问题](../assessments/common-in-depth-analysis-issues.md)

 

 







