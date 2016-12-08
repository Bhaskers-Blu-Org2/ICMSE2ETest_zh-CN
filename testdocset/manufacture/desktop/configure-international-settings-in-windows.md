---
author: Justinha
Description: "在 Windows 中配置国际设置"
ms.assetid: 2ed4a22d-8cd1-49b8-8141-06ebbf26b24d
MSHAttr: PreferredLib:/library/windows/hardware
title: "在 Windows 中配置国际设置"
ms.openlocfilehash: 477da06f42bb60c5e16bd064cddb4666165df612
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="configure-international-settings-in-windows"></a>在 Windows 中配置国际设置


在配置过程中或安装 Windows 后，可以指定默认语言、 区域设置和键盘值。 通过使用 Windows PowerShell 国际模块、 使用 Windows 安装程序答案文件或通过使用部署映像服务和管理 (DISM)，您可以配置国际设置。

有关使用 DISM 脱机 Windows 映像中配置国际设置的信息，请参阅[DISM 语言和国际服务命令行选项](dism-languages-and-international-servicing-command-line-options.md)。

**重要**  
在 Windows 10，intl.cpl 命令行工具不支持控制面板的区域和语言选项部分中的新设置。 对于 Windows 10，我们建议使用国际 Windows PowerShell cmdlet 设置来自动执行自定义区域设置。

此外，部署映像服务和管理 (DISM) 也只应针对脱机 Windows 映像。 Windows 10 中的语言设置自动配置基于用户的语言列表。 个人设置，例如显示语言、 默认输入的法和用户区域设置可能重置根据用户首选项在运行 Windows 安装动态。 国际 PowerShell cmdlet 设置用于更改正在运行的 Windows 安装的区域设置。


## <a name="span-idpowershellspanspan-idpowershellspanspan-idpowershellspanconfigure-international-settings-by-using-winbows-powershell"></a><span id="PowerShell"></span><span id="powershell"></span><span id="POWERSHELL"></span>通过使用 Winbows PowerShell 配置国际设置


在 Windows 10，您可以使用国际设置 Windows PowerShell cmdlet 更改正在运行的 Windows 安装上的语言。 

1.  打开 Windows PowerShell 提示符。

3.  通过运行下面的命令显示计算机上的区域设置信息︰

    ``` syntax
    Get-WinSystemLocale
    ```

    设置区域和语言选项所需的区域设置。 例如，以下命令将系统区域设置设置为日语 （日本）︰

    ``` syntax
    Set-WinSystemLocale ja-JP
    ```

    这些 cmdlet 的完整说明，请参阅[获取 WinSystemLocale](http://go.microsoft.com/fwlink/p/?linkid=242247)和[一组 WinSystemLocale](http://go.microsoft.com/fwlink/p/?linkid=242254)。 有关使用国际 PowerShell cmdlet 的详细信息，请参阅[国际设置 Cmdlet](http://go.microsoft.com/fwlink/p/?linkid=238265)。

## <a name="span-idcontrolpanelspanspan-idcontrolpanelspanspan-idcontrolpanelspanconfigure-international-settings-by-using-control-panel"></a><span id="ControlPanel"></span><span id="controlpanel"></span><span id="CONTROLPANEL"></span>通过使用控制面板中配置国际设置

在正在运行 Windows 安装中，您可以使用控制面板选择语言包并配置国际设置的更多。

1.  在开始页上，键入**语言**，并选择**添加一种语言**。

4.  浏览或搜索您想要安装的语言。 例如，选择**加泰罗尼亚语**，然后再选择**添加**。

    加泰罗尼亚语现在被添加为您的语言之一。

5.  **更改您的语言首选项**窗格中，选择**选项**旁边您所添加的语言。

6.  如果可用语言的语言包，请选择**下载并安装语言包**。

7.  安装语言包后，语言将显示为可用，以用于 Windows 的显示语言。

8.  若要使这种语言显示语言，请将其移动到您的语言列表的顶部。

9.  注销，然后重新登录到 Windows 以使更改生效。

安装很多其他语言包对磁盘空间和系统性能的影响。 特别要说明的是，在服务操作，例如 service pack 安装期间影响磁盘空间和系统性能。 因此，我们建议只有当您计划使用该语言包将语言包添加到计算机。

语言包还可以让多个用户共享的计算机选择不同的显示语言。 例如，一个用户可以选择要查看对话框、 菜单和其他文本在日语中，而另一个用户可以选择以法语中相同的内容，请参阅。

## <a name="span-iddismspanspan-iddismspanconfigure-international-settings-by-using-dism"></a><span id="DISM"></span><span id="dism"></span>通过使用 DISM 配置国际设置


您可以使用部署映像服务和管理 (DISM) 可以更改针对脱机 Windows 映像的国际设置

1.  安装的 Windows 映像。 例如，

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\my_distribution\sources\install.wim /Index:1 /MountDir:C:\mount\windows
    ```

2.  获取使用**/Get-Intl**参数配置 Windows 映像中的语言设置。 例如

    ``` syntax
    Dism /image:C:\mount\windows /Get-Intl
    ```

3.  通过使用**/set-allInlt**参数来更改默认语言、 区域设置，以及其他国际设置。

    ``` syntax
    Dism /image:C:\mount\windows /set-allIntl:fr-fr
    ```

额外的参数和其他选项，请参阅[DISM 语言和国际服务命令行选项](dism-languages-and-international-servicing-command-line-options.md)。

## <a name="span-idanswerfilespanspan-idanswerfilespanspan-idanswerfilespanconfigure-international-settings-by-using-an-answer-file"></a><span id="AnswerFile"></span><span id="answerfile"></span><span id="ANSWERFILE"></span>使用答案文件中配置国际设置


通过以下方法，可以在答案文件中配置国际设置︰

-   从分布共享中安装语言包并配置安装在**WindowsPE**配置阶段的设置。

    通常部署多语言 Windows 版本的公司创建的应答文件中配置国际设置，在**WindowsPE**配置阶段。 对于多语言部署，分布共享中，并在图像中可以存在语言包。 可以添加和配置分发共享中的语言包，在**WindowsPE**配置阶段中，也可以添加这些语言 pa cks **WindowsPE**配置期间传递并在另一个配置阶段中配置的设置。

    Microsoft 的 Windows-国际的核心-WinPE 组件包括可用来修改语言和区域设置在**windowsPE**配置期间传递的设置。 此外，可以为 Windows 安装程序通过此组件中指定值来更改安装程序用户界面语言。

-   语言包安装到 Windows 映像，并设置**专门**和**oobesystem**配置过程中传递。

    Oem 和公司通常部署到多个不同区域的是单一语言版本的 Windows 创建应答文件为每个地区，并在**specialize**配置阶段中设置的区域设置和键盘设置。 在这种情况下，该语言包添加到 Windows 映像之前配置国际设置。

    Microsoft Windows 国际核心组件包括可用于修改语言和区域设置**专门**和**oobeSystem**配置期间传递的设置。

    可以预先选择一种语言并跳欢迎使用 Windows 的语言选择用户界面页，用户通过指定语言并在**oobeSystem**配置区域设置传入的 Microsoft Windows 国际核心组件。 一般情况下，用户可以选择默认安装语言和映像中安装的任何其他语言。 语言的所选内容将更新与该语言相关联的默认值的其他区域设置。 用户可以分别更改默认设置。

**若要配置国际设置 Windows PE 配置期间传递**

1.  验证必需的语言包会在图像或 Windows 分布共享中可用。 有关多语言分布共享的详细信息，请参阅[Windows 分发到添加多语言支持](add-multilingual-support-to-a-windows-distribution.md)。

2.  打开 Windows 系统映像管理器 (Windows SIM) 并创建一个答案文件。 有关详细信息，请参阅[创建或打开答案文件](https://msdn.microsoft.com/library/windows/hardware/dn915085)。

3.  Microsoft 的 Windows-国际的核心-WinPE 将组件添加到答案文件在**windowsPE**配置阶段期间应用设置。

4.  Microsoft 的 Windows-国际的核心-WinPE 组件中配置国际设置。 例如，如果分布共享中可用西班牙语语言包，可以*es-ES*值为组件设置在**windowsPE**配置传递。

    大多数的系统区域设置需要重新启动。 配置设置在**windowsPE**配置期间传递您的区域设置时，计算机将自动重新启动。 需要重新启动不是必需的。

    有关这些设置的详细信息，请参阅无人参与安装参考 Windows® 中的 Microsoft 的 Windows-国际的核心-WinPE 组件。

5.  保存答案文件并关闭 Windows sim 卡。 分布共享中的语言包会自动添加并将应用国际设置，当您运行 Windows 安装程序并指定该答案文件。

**若要配置国际设置专业化配置期间传递**

1.  验证必需的语言包的映像中可用。 有关如何添加脱机的语言包的详细信息，请参阅[添加和删除语言包脱机使用 DISM](add-and-remove-language-packs-offline-using-dism.md)。 有关如何添加语言包，使用答案文件的详细信息，请参阅[添加到答案文件的包](https://msdn.microsoft.com/library/windows/hardware/dn915066)。

2.  打开 Windows sim 卡并创建新的应答文件。 有关详细信息，请参阅[创建或打开答案文件](https://msdn.microsoft.com/library/windows/hardware/dn915085)。

3.  添加**专用化**和**oobeSystem**配置阶段期间应用设置 Microsoft Windows 国际核心组件。

    大多数的系统区域设置需要重新启动。 当您**擅长**或**oobeSystem**配置阶段期间处理的语言设置时，计算机可能需要另外重新启动计算机。

4.  编辑的 Microsoft Windows 国际核心组件的设置以配置国际设置的特定区域。 例如，您可以添加到 Microsoft Windows 国际核在**specialize**配置设置*EN-US*值传递。

    此外可以预先选择一种语言，和指定语言和区域设置在**oobeSystem**配置传入的 Microsoft Windows 国际核心组件。 执行此操作时，欢迎使用 Windows 语言选择用户界面页将跳过当用户引导至 Windows 欢迎。 一般情况下，用户可以选择默认安装语言和映像中安装的任何其他语言之间。 语言的所选内容将更新与该语言相关联的默认值的其他区域设置。 然后，用户可以更改这些默认设置单独。

    有关这些设置的详细信息，请参阅在 Windows® 无人参与安装参考 Microsoft Windows 国际核心组件。

5.  保存答案文件并关闭 Windows sim 卡。 指定该答案文件的 Windows 安装程序运行时，将应用答案文件中指定的区域设置。

**若要更改国际设置相同的应答文件中的单个配置阶段中︰**

-   在将 Windows 安装的不同阶段处理不同语言设置的答案文件中创建多个分区。 这使您可以通过指定不同的设置以处理在不同的配置阶段中的答案文件中配置多个语言设置。 有关详细信息，请参阅[如何配置阶段的工作](how-configuration-passes-work.md)。

    例如，您可以创建语言和区域设置在**windowsPE**配置传递与 Microsoft 的 Windows-国际的核心-WinPE 组件。

    然后，您可以更改**oobeSystem**或**专用化**配置中的设置将设置添加到 Microsoft Windows 国际核心组件传递默认值。

    例如，您可以指定*EN-US*作为在**windowsPE**配置阶段中的计算机上使用的默认语言。 然后，如果您打算将计算机发送到其他区域，您可以添加更多的语言和区域设置到**oobeSystem**配置阶段。

    如果语言设置处理在**oobeSystem**配置阶段，可能需要重新启动。 此外，计算机处理语言设置所需的时间可能阻止最终用户快速启动 Windows 欢迎。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Windows 安装程序技术参考](windows-setup-technical-reference.md)

[Windows 系统映像管理器技术参考](https://msdn.microsoft.com/library/windows/hardware/dn922445)

[将语言包添加到 Windows](add-language-packs-to-windows.md)

[添加和删除语言包使用 DISM 脱机](add-and-remove-language-packs-offline-using-dism.md)

 

 






