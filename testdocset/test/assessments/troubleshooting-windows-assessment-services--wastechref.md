---
title: "疑难解答 Windows 评估服务"
description: "疑难解答 Windows 评估服务"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: f0a1c2cb-9566-4451-a201-5dab89c7a0b9
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 4c96ec15974a40b3a6684b895c64b61fe92e335c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="troubleshooting-windows-assessment-services"></a>疑难解答 Windows 评估服务


以下信息可以帮助您解决常见的问题。

本主题包括︰

-   [日志文件](#bkmk-ts-logfiles)

-   [设置符号服务器](#bkmk-ts-symbolserver)

-   [无法连接到服务器](#bkmk-ts-unableconnect)

-   [在库存中已存在的计算机](#bkmk-ts-computerexists)

-   [运行的按钮将不可用](#bkmk-ts-runbuttondimmed)

-   [清点测试机器失败与 WS\_E\_操作\_TIMED\_出](#bkmk-ts-inventoryfails)

-   [没有足够的信息，监视页上映像部署失败。](#bkmk-ts-deploymentfails)

-   [DISM 计算机库存过程中出现错误](#bkmk-ts-dismerr)

-   [如果您更改服务器名称，则必须最先测试计算机](#bkmk-ts-reimagetestcomp)

-   ["机器无法访问"错误](#bkmk-ts-machinereach)

-   [在运行 Windows 评估服务-从 Windows 评估服务服务器以外的服务器的客户端](#bkmk-ts-msmq)

-   [转储文件夹不包含任何转储文件](#bkmk-ts-dumps)

## <a name="a-href-idbkmk-ts-logfilesalog-files"></a><a href="" id="bkmk-ts-logfiles"></a>日志文件


-   日志文件复制到服务器中，当您将计算机添加到服务器的清单。 存储在**c:\\放松\\日志**。

-   服务器日志捕获 Windows 评估服务的事件。 可以在上找到此日志文件**c:\\Windows\\温度\\relaxservice.tracelistener.Tracing**。

-   可以在**应用程序和服务日志**客户端计算机上的事件查看器中查看来自 UI 错误 - **Windows 评估服务客户端**。 日志文件是 ETL 文件位于**%systemroot%\\system32\\Winevt\\日志\\Windows 评估服务 Client.evtx**。

-   从测试计算机复制映像部署日志 (Windows PE) **%系统驱动器 %\\放松\\日志**

-   在 Windows Server 2012，Windows 部署服务 (Windows DS) 问题找不到在事件查看器**的应用程序和服务日志**下 -**Microsoft** -**Windows** - **Windows 部署服务诊断**。

-   在 Windows Server 2008 R2 上必须通过设置以下启用 Windows DS 日志记录︰

    -   **HKLM\\系统\\开目前控制设置\\服务\\WDSServer\\提供商\\WDSPXE ！TracingDisabled 为 0**

    -   **HKLM\\软件\\Microsoft\\跟踪\\WDSServer ！为 1 EnableFileTracing**

    WDS 日志将在生成**%systemroot%\\跟踪\\wdsserver.log**。

-   WinRM 可找到日志的事件查看器**的应用程序和服务日志**下 -**Microsoft** -**Windows** -**Windows 远程管理**。

-   如果结果不会被复制到服务器，则可以在测试计算机上找到它们。 在系统驱动器 %%日志文件\\放松\\&lt;GUID&gt;\\作业\\results.log 指向结果文件夹保存结果。

## <a name="a-href-idbkmk-ts-symbolserveraset-up-a-symbol-server"></a><a href="" id="bkmk-ts-symbolserver"></a>设置符号服务器


一些评估需要访问符号。 在某些情况下评估结果中的信息可以不正确或已丢失的信息，如果符号服务器不可用。 在许多情况下这种依赖性是通过互联网连接和访问 Microsoft 公共符号服务器来满足的。 在其他情况下，在与 Internet 的连接不可用如实验室环境，可以设置私有符号服务器或本地计算机来获得评估的全部好处上能安装这些符号。

**要测试计算机上设置符号环境变量**

1.  打开文件资源管理器中，右键单击**计算机**，然后选择**属性**。

2.  在属性窗口中单击**高级系统设置**。

3.  在系统属性窗口上的**高级**选项卡上，单击**环境变量**。

4.  在系统变量下，请单击**新建**符号将环境变量设置通过使用以下方法之一︰

    1.  使用公共符号服务器 （需要 Internet 连接）

        将计算机连接到 Internet，以便它可以访问 Microsoft 的符号服务器，，然后配置\_NT\_符号\_ **http://msdl.microsoft.com/downloads/symbols**在使用 Microsoft 的符号服务器的路径环境变量。

    2.  使用网络连接的符号路径 （需要通过本地网络连接）

        将计算机连接到本地，然后配置\_NT\_符号\_PATH 环境变量，使用内联网的符号路径。

    3.  使用本地符号路径

        将符号下载到 Windows 评估服务服务器计算机上，并指向该位置设置测试计算机\_NT\_符号\_PATH 环境变量，如在服务器上，使用符号的路径\\ \\WASServer\\放松\\符号。

**若要设置内部符号**

1.  安装在 ADK，并初始化 WAS。

2.  获得 WAS 服务器计算机的 IPsec 边界异常。 这将确保 WAS 测试计算机能够访问放松共享。

3.  WAS 服务器计算机加入到域中。

4.  为有权访问内部符号服务器管理员组到 WAS 服务器计算机添加域用户。

5.  通过从提升的命令提示符处运行以下命令来停止 WAS 服务︰

    **net stop WASSVC**

6.  将服务登录帐户更改为新的域帐户。

7.  从提升的命令提示符处，运行以下命令替换&lt;*内部符号的路径*&gt;与相应的路径︰

    **SETX\_NT\_符号\_路径\\ \\&lt;内部符号的路径&gt;/M**

8.  重新启动计算机。

有关如何设置符号路径，并将符号下载的详细信息，请参阅[MSDN︰ 符号支持](http://go.microsoft.com/fwlink/?LinkId=235359)。 有关如何解决缺少符号的信息，请参阅[In-Depth 分析的常见问题](common-in-depth-analysis-issues.md#missingsymbols)。

## <a name="a-href-idbkmk-ts-unableconnectaunable-to-connect-to-server"></a><a href="" id="bkmk-ts-unableconnect"></a>无法连接到服务器


如果 Windows 评估服务的客户端 (Windows ASC) 不能连接到服务器，您可能会收到以下错误消息︰

*无法连接到远程服务器︰ 连接尝试失败，因为被连接的方没有正确响应后一段时间，或已建立的连接失败，因为被连接的主机未能响应。*

使用**sc 查询 wassvc**命令来检查服务器状态。 如果未运行服务器，通过**网络启动 wassvc**命令启动该服务。

**警告**  
当 Windows 评估服务服务器上运行，sc 查询命令才有效。

 

## <a name="a-href-idbkmk-ts-computerexistsacomputer-already-exists-in-inventory"></a><a href="" id="bkmk-ts-computerexists"></a>在库存中已存在的计算机


如果您收到以下消息时，Windows 评估服务库存中已存在的测试计算机︰

*手动执行任何方案。单击退出以重新启动*

如果看不到计算机窗口中的项服务器清单，关闭，然后重新打开此窗口可刷新内容。

## <a name="a-href-idbkmk-ts-runbuttondimmedarun-button-is-unavailable"></a><a href="" id="bkmk-ts-runbuttondimmed"></a>运行的按钮将不可用


如果**运行**按钮不可用，请确保您拥有**资产**详细信息中选择特定的计算机和图像。 如果选择了特定的计算机和图像，但在**结果**页上没有任何评估，关闭，然后重新创建当前作业。

## <a name="a-href-idbkmk-ts-inventoryfailsainventorying-test-machine-fails-with-wseoperationtimedout"></a><a href="" id="bkmk-ts-inventoryfails"></a>清点测试机器失败与 WS\_E\_操作\_TIMED\_出


如果您收到以下错误︰

``` syntax
Error updating machine configuration in RelaxServer. Please check that the server is available and try again later. (ErrorCode:-2143485946)
```

请检查错误日志以**c:\\放松\\CompleteDeployment.log**其他错误的详细信息，然后重新运行**CompleteDeployment.cmd**。

## <a name="a-href-idbkmk-ts-deploymentfailsaimage-deployment-failures-dont-have-enough-information-on-the-monitoring-page"></a><a href="" id="bkmk-ts-deploymentfails"></a>没有足够的信息，监视页上映像部署失败。


**错误代码︰ 退出方案部署︰ ErrorId = 2**

或者您正在使用不支持的格式的图像，无人参与的答案文件丢失或找不到图像文件。

**错误代码︰ 退出方案部署︰ ErrorId = 38**

图像文件已损坏。

**错误代码︰ 退出方案部署︰ ErrorId = 87**

Bcdboot BCD 存储，更新失败。 这是特定于某些 UEFI 的计算机的原型。 这一次没有解决方法才可用。

**错误代码︰ 退出方案部署︰ ErrorId = 193**

Bcdboot BCD 存储，更新失败。 不兼容的体系结构的图像被应用于一台测试计算机。

**错误代码︰ 退出方案部署︰ ErrorId = 2147024809**

Diskpart 未能找到任何硬盘驱动器的驱动器可用于应用到图像。

## <a name="a-href-idbkmk-ts-dismerradism-error-during-computer-inventory"></a><a href="" id="bkmk-ts-dismerr"></a>DISM 计算机库存过程中出现错误


如果您收到以下错误清点的计算机时，您必须使用 x86 为库存创建可引导 USB 驱动器的 Windows PE 映像。

``` syntax
An error occurred. You cannot service an x86-based image from an x64-based host that does not support WOW64. Try the operation again from a host environment that supports WOW64. 
Error running Driver Scavenge. ErrorCode 193.
```

驱动程序信息时清点计算机，收集和存储在**&lt;%系统驱动器 %\\放松\\驱动程序**使用 DISM。 DISM 无法运行驱动程序服务命令在 X86 上 Windows 映像，从 Windows PE X64 环境。 有关详细信息，请参阅 DISM 支持的平台。

**解析**

使用 （或创建） 可引导 USB 驱动器创建 X86 体系结构。 有关详细信息，请参阅[Windows 评估服务安装和配置](windows-assessment-services-setup-and-configuration-wastechref.md)。

## <a name="a-href-idbkmk-ts-reimagetestcompatest-computers-must-be-reimaged-if-you-change-the-server-name"></a><a href="" id="bkmk-ts-reimagetestcomp"></a>如果您更改服务器名称，则必须最先测试计算机


如果您重命名 Windows 评估服务服务器，并重新对其进行初始化，必须重新部署了 Windows 在测试计算机上运行其他评估之前。

## <a name="a-href-idbkmk-ts-machinereachamachine-not-reachable-errors"></a><a href="" id="bkmk-ts-machinereach"></a>"机器无法访问"错误


当评估以远程方式运行，Windows 评估服务依赖于 DNS 解析测试计算机名。 如果 DNS 中有重复的条目相同的计算机名称、 计算机加入域中的一个，另一个从工作组计算机，Windows 和 WinRM 将选择 DNS 解析到该计算机。

如果您收到的错误，包括"机器无法访问"，请检查 DNS 条目的重复项。

**请注意**  
计算机名称必须包含只能包含字母数字字符和短划线。 如果计算机名称包含下划线符号或其他扩展的字符，则计算机可能无法通过域名系统 (DNS) 中发现。

 

## <a name="a-href-idbkmk-ts-msmqarunning-windows-asc-from-a-server-other-than-the-windows-assessment-services-server"></a><a href="" id="bkmk-ts-msmq"></a>运行 Windows 评估服务服务器以外的服务器上 Windows ASC


如果您运行的 Windows ASC 的 Windows 服务器上，并且您不具有在该服务器上安装的 Windows 评估服务，推式通知将无法启用 Windows ASC 在当您需要启动它。

**解决方法**

在服务器上装有 Windows ASC，启用 MSMQ 服务器使用以下 DISM 命令从提升的命令提示符的可选组件。

``` syntax
Dism /Online /Enable-Feature:MSMQ-Server
```

或客户端计算机或同一台服务器上运行 Windows ASC 装有 Windows 评估服务。

## <a name="a-href-idbkmk-ts-dumpsathe-dumps-folder-does-not-contain-any-dump-files"></a><a href="" id="bkmk-ts-dumps"></a>转储文件夹不包含任何转储文件


默认情况下，转储文件未复制到服务器中，评估运行后。 如果您想要收集评估运行的转储，编辑&lt;放松目录&gt;\\脚本\\工具\\斧\\CompleteAssessment.cmd 和更改集的值\_copydumpstoserver 为 true。 默认情况下，此值为 false。

## <a name="related-topics"></a>相关的主题


[Windows 评估服务](windows-assessment-services-technical-reference.md)

 

 







