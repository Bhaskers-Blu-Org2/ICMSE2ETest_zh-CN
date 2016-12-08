---
author: Justinha
Description: "添加和删除在运行 Windows 安装的语言包"
ms.assetid: 0e3f0b85-417e-4e17-869e-05ae37e98c8f
MSHAttr: PreferredLib:/library/windows/hardware
title: "添加和删除在运行 Windows 安装的语言包"
ms.openlocfilehash: 14f96d0bc2f2ec2361a4f3f105ae983dafcc7dca
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add-and-remove-language-packs-on-a-running-windows-installation"></a>添加和删除在运行 Windows 安装的语言包


在正在运行的操作系统，或脱机映像时，可以添加对其他语言的支持。 有关如何安装语言到脱机映像的信息，请参阅[添加和删除语言包脱机使用 DISM](add-and-remove-language-packs-offline-using-dism.md)。

有关安装语言界面包 (Lip) 的信息，请参阅[windows 添加语言界面包](add-language-interface-packs-to-windows.md)。

在 Windows 10 用户可以安装多个语言和功能转到**设置** &gt; **时间和语言** &gt; **地区和语言** &gt; **添加一种语言**。 

## <a name="span-idonlinespanspan-idonlinespanadd-a-language-pack-online"></a><span id="online"></span><span id="ONLINE"></span>添加语言包


当您添加语言包使用 DISM 时，不验证允许多少语言包的 Windows 版本上运行的授权要求。 如果添加多个语言包，请所有非默认情况下，非用户选择的语言将从计算机中删除后一段时间。 有关详细信息，请参阅[将语言包添加到 Windows](add-language-packs-to-windows.md)。

**请注意**  
此外可以对 Windows 预安装和 Windows 恢复安装语言包。 有关详细信息，请参阅[WinPE︰ 安装和自定义](winpe-mount-and-customize.md)和[自定义 Windows RE](customize-windows-re.md)。

 

**通过使用 DISM 添加语言包**

1.  在正在运行的操作系统，打开提升的命令行提示符。

2.  键入以下命令以便将语言包 （在此示例中为西班牙语） 添加到操作系统。 

    ``` syntax
    Dism /online /Add-Package /PackagePath:C:\test\LangPacks\Microsoft-Windows-Client-Language-Pack_x64_es-es.cab
    ```

有关 DISM 国际服务命令的详细信息，请参阅[DISM 语言和国际服务命令行选项](dism-languages-and-international-servicing-command-line-options.md)

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[使用 DISM Windows 映像提供服务](service-a-windows-image-using-dism.md)

[了解处理策略](understanding-servicing-strategies.md)

[将语言包添加到 Windows](add-language-packs-to-windows.md)

 

 






