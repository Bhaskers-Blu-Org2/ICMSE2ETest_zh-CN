---
author: Justinha
Description: "Windows 安装程序版本配置和产品 ID 文件 （EI.cfg 和 PID.txt）"
ms.assetid: 1c0f17a9-6a74-40af-8d0b-fc6d807a6616
MSHAttr: PreferredLib:/library/windows/hardware
title: "Windows 安装程序版本配置和产品 ID 文件 （EI.cfg 和 PID.txt）"
ms.openlocfilehash: f52df3e504fec7e65d37abefa50dc46723d5e734
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-setup-edition-configuration-and-product-id-files-eicfg-and-pidtxt"></a>Windows 安装程序版本配置和产品 ID 文件 （EI.cfg 和 PID.txt）


版 (EI.cfg) 配置文件和产品 ID (PID.txt) 文件是可选配置文件可用于在 Windows 安装过程中指定的 Windows® 产品密钥和 Windows 版。 您可以使用这些文件而不是使用答案文件自动在 Windows 安装的产品密钥条目页。 如果您使用 EI.cfg 文件来区分批量许可证媒体，但不是包括一个 PID.txt 文件，用户会收到输入产品密钥才能继续运行 Windows 安装程序的提示。

您可以重复使用产品 ID 文件中的多个安装的产品密钥。 产品 ID 文件中的产品密钥仅用于安装 Windows。 不使用此密钥来激活 Windows。 有关详细信息，请参阅[使用产品密钥和激活](work-with-product-keys-and-activation-auth-phases.md)。

## <a name="span-idusingeicfgandpidtxtspanspan-idusingeicfgandpidtxtspanspan-idusingeicfgandpidtxtspanusing-eicfg-and-pidtxt"></a><span id="Using_EI.cfg_and_PID.txt"></span><span id="using_ei.cfg_and_pid.txt"></span><span id="USING_EI.CFG_AND_PID.TXT"></span>使用 EI.cfg 和 PID.txt


1.  在文本编辑器 （如记事本） 中创建这些配置文件。

2.  保存到文件`\Sources`在安装介质上的文件夹。 Windows 安装程序将在安装过程中自动使用这些文件。

3.  运行 Windows 安装程序。 安装程序在 Windows PE 配置阶段中使用这些文件，只要启动它。

**请注意**  
答案文件优先于这些文件。 如果您在安装过程中使用应答文件，Windows 安装程序将忽略的 EI.cfg 和 PID.txt 文件。

 

## <a name="span-ideicfgformatspanspan-ideicfgformatspaneicfg-format"></a><span id="ei.cfg_format"></span><span id="EI.CFG_FORMAT"></span>EI.cfg 格式


EI.cfg 文件的版本 ID、 通道和批量许可证中指定的值。

EI.cfg 文件具有以下格式︰

``` syntax
[EditionID]
{Edition ID}
[Channel]
{Channel Type}
[VL]
{Volume License}
```

*{版本 ID}*必须是有效的 Windows 版本 ID，例如，"企业"。 若要获取当前 EditionID，使用**Dism /Get-ImageInfo**命令或**Dism /Get-CurrentEdition**命令。 有关详细信息，请参阅[映像或组件使用 DISM 的采取库存](take-inventory-of-an-image-or-component-using-dism.md)和[DISM Windows 版服务命令行选项](dism-windows-edition-servicing-command-line-options.md)。

*{通道类型}*必须"OEM"或"零售"

如果这是批量许可证，则为 0，如果不是批量许可证，必须是 1， *{批量许可证}* 。 例如︰

``` syntax
[EditionID]
Enterprise
[Channel]
OEM
[VL]
0
```

## <a name="span-idpidtxtformatspanspan-idpidtxtformatspanpidtxt-format"></a><span id="pid.txt_format"></span><span id="PID.TXT_FORMAT"></span>PID.txt 格式


PID.txt 文件中包含您要安装的 Windows 版本的产品密钥。

PID.txt 文件具有以下格式︰

``` syntax
[PID]
Value=XXXXX-XXXXX-XXXXX-XXXXX-XXXXX
```

其中*XXXXX-XXXXX-XXXXX-XXXXX-XXXXX*是产品密钥。

## <a name="span-idtroubleshootingspanspan-idtroubleshootingspanspan-idtroubleshootingspantroubleshooting"></a><span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>故障排除


**"输入的产品密钥不匹配任何可供安装的 Windows 映像。请输入不同的产品密钥。"**︰ 您可能需要下载不同版本的 Windows。 OEM 版本仅供 Oem、 和批量许可证才可到 MSDN 订阅服务器。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[使用产品密钥和激活](work-with-product-keys-and-activation-auth-phases.md)

[Windows 安装程序命令行选项](windows-setup-command-line-options.md)

[Windows 安装程序状态](windows-setup-states.md)

 

 






