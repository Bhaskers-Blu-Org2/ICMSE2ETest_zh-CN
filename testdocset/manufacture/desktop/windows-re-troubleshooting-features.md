---
author: Justinha
Description: "Windows RE 疑难解答功能"
ms.assetid: 5812bba2-a4ed-4659-87b0-774de7a84bf5
MSHAttr: PreferredLib:/library/windows/hardware
title: "Windows RE 疑难解答功能"
ms.openlocfilehash: 9fea5e93c73a17cd5468102da2bf93afc1980a95
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-re-troubleshooting-features"></a>Windows RE 疑难解答功能


如果无法启动 Windows 设备，其自动故障转移到 Windows 恢复环境 (Windows RE)。 Windows RE 中的自动修复工具可以自动诊断和修复无法启动的 Windows 安装。 Windows RE 也是多个工具进行手动系统恢复的起点。 本主题介绍的自动故障切换行为、 手动诊断和 Windows RE 中的修复过程。

本主题︰

-   [从启动故障恢复](#bkmk-1)

-   [高级故障排除实用程序在 Windows RE](#bkmk-2)

## <a name="span-idbkmk1spanspan-idbkmk1spanrecovering-from-startup-failures"></a><span id="bkmk_1"></span><span id="BKMK_1"></span>从启动故障恢复


如果系统检测到运行 Windows 的计算机上启动故障，系统自动将故障转移到磁盘上的 Windows RE 工具。 在启动时，Windows 加载程序设置状态标志以指示引导过程已启动。 Windows 登录屏幕出现之前，Windows 通常会清除此标志。 但是，如果启动尝试失败时，Windows 不会清除标志。 下次计算机启动时，加载程序检测到该标志，并假定出现启动失败。 在这种情况下，加载程序将启动 Windows RE，而不是 Windows。

**请注意**  
启动故障检测依赖于引导完成和未是否发生错误在 Windows 8 中。 例如，如果在启动过程中，电源将丢失，并且您的用户启动 Windows RE，即使是可引导的 Windows 安装，则可能会出现假阳性。

 

由于故障切换机制依赖于 Windows 启动管理器和 Windows 引导加载程序，一些故障可以使 Windows RE 不可访问。 在下面的情形中，您的用户必须使用可引导的 Windows RE 介质恢复计算机︰

-   损坏的磁盘元数据存在于主启动记录 (MBR) 分区表、 Windows RE 分区的启动扇区。

-   启动管理器是丢失或已损坏。

-   引导配置数据 (BCD) 存储已丢失或已损坏。

如果引导加载程序不能读取或写入引导状态标志，则 Windows 不能自动故障转移到 Windows RE。 但是，您的用户可以仍然手动启动磁盘上 Windows RE 工具，通过**启动选项**菜单。

## <a name="span-idbkmk2spanspan-idbkmk2spanadvanced-troubleshooting-utilities-in-windows-re"></a><span id="bkmk_2"></span><span id="BKMK_2"></span>高级故障排除实用程序在 Windows RE


从恢复介质，或从**启动选项**菜单启动磁盘上 Windows RE 工具后，您的用户可以手动启动几个系统恢复工具。 自动修复，但 Windows 评估和部署工具包 (Windows ADK) 并不包括这些工具。 依靠以点击方式重置是 Windows 中的建议的恢复解决方案。

### <a name="span-idbkmkaspanspan-idbkmkaspanautomatic-repair"></a><span id="bkmk_a"></span><span id="BKMK_A"></span>自动修复

自动修复工具自动化常见诊断和修复不可引导的操作系统安装任务。 如果计算机发生故障转移到 Windows RE 的检测到的启动失败，启动自动修复。 如果自动故障转移到 Windows RE 的磁盘上的实例不可用，您的用户还可以作为一种工具手动恢复从 Windows RE CD 或 DVD 启动自动修复。

### <a name="span-idbkmkcspanspan-idbkmkcspansystem-image-recovery"></a><span id="bkmk_c"></span><span id="BKMK_C"></span>系统映像恢复

文件备份和系统映像备份，使用系统映像恢复。 系统映像恢复要求外部存储设备。 对于文件的备份，您的用户可以让 Windows 选择要备份的内容或者他们可以选择个别文件夹、 库和驱动器。 默认情况下，定期创建备份。 您的用户可以更改日程安排，并在任何时候手动创建备份。 您的用户设置系统映像恢复后，Windows 将跟踪的新的或修改过的文件和文件夹，将其添加到备份。

对于系统映像备份，您的用户可以创建系统映像或驱动器完全相同的映像。 系统映像包含 Windows 和系统设置、 程序和文件。 您的用户可以使用系统映像来还原计算机的内容，如果硬盘或计算机无法工作。

如果您的用户从系统映像还原计算机，还原已完全恢复。 您的用户不能选择个别项进行还原。 所有当前程序、 系统设置和文件将被替换。

如果设置计划的文件备份时，您可以包括与仅在 Windows 运行所需的驱动器的系统映像。 如果您想要包含其他数据驱动器，您可以手动创建系统映像。

**请注意**  
早期的系统映像版本是文件和系统保护过程中由 Windows 自动保存的文件夹的副本。 根据文件或文件夹的类型，您的用户可以打开以前的版本，将版本保存到其他位置，或还原以前的版本。 您的用户可以使用这些以前版本还原意外修改、 删除或损坏的文件或文件夹。 然而，因为 Windows 用新版本替换这些文件文件将不可用如果驱动器出现故障。

 

### <a name="span-idbkmkdspanspan-idbkmkdspancommand-prompt"></a><span id="bkmk_d"></span><span id="BKMK_D"></span>命令提示符

所有的 Windows PE 命令行工具可以从命令提示符窗口。 例如，可以使用注册表编辑器 (Regedit.exe) 中包含的命令行开关，可以修改 Windows 注册表。 或者，您可以使用 Chkdisk.exe 工具来诊断并修复卷。 有关详细信息，请参阅[注册表编辑器](http://go.microsoft.com/fwlink/?LinkId=207693)、 [Chkdsk](http://go.microsoft.com/fwlink/?LinkId=207694)，和[疑难解答的工具和策略](http://go.microsoft.com/fwlink/?LinkId=207695)。

### <a name="span-idbkmkespanspan-idbkmkespancustom-support-and-recovery-tools"></a><span id="bkmk_e"></span><span id="BKMK_E"></span>自定义支持和恢复工具

计算机制造商可以提供自定义的支持和恢复工具。 这些工具制造商而异。 有关详细信息，请参阅制造商提供的文档。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[BCDboot 命令行选项](bcdboot-command-line-options-techref-di.md)

[REAgentC 命令行选项](reagentc-command-line-options.md)

 

 






