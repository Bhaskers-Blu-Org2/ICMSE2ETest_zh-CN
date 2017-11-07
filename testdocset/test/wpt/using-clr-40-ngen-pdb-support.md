---
title: "使用 CLR 4.0 NGEN PDB 支持"
description: "使用 CLR 4.0 NGEN PDB 支持"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 0297661e-99bf-44fa-9d1c-f624d6a96f41
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 1b7e27954acca6dd36bafbc19210de8cda263720
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="using-clr-40-ngen-pdb-support"></a>使用 CLR 4.0 NGEN PDB 支持


Xperf 和 Windows 性能记录器 (WPR) 可以使用公共语言运行时 (CLR) 4.0 本机映像生成器 (NGEN) PDB 支持已启用运行。

**请注意** WPR 直接处理 CLR 的符号，因此不不需要在配置和使用 NGEN 支持任何标志。

 

当您启动录制 WPR 用户界面 (UI) 中时，NGEN 程序数据库 (Pdb) 生成旁边保存的录制。 这些 Pdb 解码的托管方案使用 NGEN 创建的模块的符号。 对于**Recording.etl**，NGEN Pdb 位于**Recording.etl.NGENPDB**文件夹中。

## <a name="using-ngen-support-with-wpr"></a>使用 WPR ngen 格式支持


我们使用 NGEN 支持启用运行 WPR 之前建议以下设置︰

-   （可选，但建议这样做）将 SymCache path 环境变量设置为本地目录

## <a name="using-ngen-support-with-xperf"></a>使用 Xperf ngen 格式支持


若要使用 Xperf NGEN 支持，执行以下操作︰

1.  在提升的命令提示符下，键入以下命令︰

    ``` syntax
    set _NT_SYMBOL_PATH=srv*C:\Symbols.NGEN;srv*http://msdl.microsoft.com/download/symbols
    ```

2.  键入以下命令以启动内核会话︰

    ``` syntax
    xperf -on Base -stackwalk Profile -f kernel.etl
    ```

3.  键入以下命令以启动 CLR 运行时会话记录︰

    ``` syntax
    xperf -start ClrSession -on ClrAll:0x98:5 -f clr.etl -buffersize 128 -minbuffers 256 -maxbuffers 512
    ```

4.  运行您的应用场景。

5.  键入以下命令以启动 CLR 断开会话︰

    ``` syntax
    xperf -start ClrRundownSession -on ClrAll:0x118:5+a669021c-c450-4609-a035-5af59af4df18:0x118:5 -f clr_DCend.etl -buffersize 128 -minbuffers 256 -maxbuffers 512
    ```

6.  键入以下命令以允许 CLR 断开通过将超时时间设置为 15 完成时间︰

    ``` syntax
    timeout /t 15
    ```

7.  键入以下内容来阻止 CLR 运行时会话、 CLR 断开会话和内核会话，并将它们合并到一个文件︰

    ``` syntax
    xperf -stop ClrSession ClrRundownSession -stop -d recording.etl
    ```

## <a name="decoding-a-recording-that-has-clr-40-ngen-pdb-support-enabled"></a>解码录制具有支持 CLR 4.0 NGEN PDB 启用


在提升的命令提示符下，键入以下命令︰

``` syntax
set _NT_SYMBOL_PATH=srv*C:\Symbols.NGEN;srv*http://msdl.microsoft.com/download/symbols
```

## <a name="transferring-a-recording-that-has-clr-40-ngen-pdb-support-enabled"></a>传输已支持 CLR 4.0 NGEN PDB 录制启用


要启用 CLR 4.0 NGEN PDB 支持传送录制，符号路径中包括以下内容︰

``` syntax
srv*C:\Symbols.NGEN
```

若要将录音传送到另一台计算机，请确保**Recording.etl**和整个文件夹**c:\\Symbols.NGEN** （以及其子文件夹） 转移。

## <a name="related-topics"></a>相关的主题


[符号的支持](symbol-support.md)

[符号](symbols.md)

 

 







