---
author: Justinha
Description: "部署自定义映像"
ms.assetid: 7eb6bc78-d1ce-42f2-bf1a-b34c4b14ed66
MSHAttr: PreferredLib:/library/windows/hardware
title: "部署自定义映像"
ms.openlocfilehash: 9d3b1da2ee4abf32c25640a358c1b5745a807a83
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="deploy-a-custom-image"></a>部署自定义映像


本主题中创建参考安装，捕获安装映像并重新指向您的自定义映像的答案文件运行 Windows® 安装。 部署自定义映像，使用 Windows 安装程序在应用映像使用映像捕获工具提供以下几个优点。

安装程序支持以下功能︰

-   在部署过程中应用另一个答案文件进行其他自定义设置。

-   重新配置磁盘配置。

-   添加其他驱动程序。

-   更换产品密钥。

-   选择要安装的不同语言。

-   从列表中选择的映像来安装，如果您的图像文件包含多个图像。

-   安装到不同的驱动器位置。

-   升级现有的 Windows 安装。

-   将计算机配置为双启动的操作系统。

-   确保硬件能够支持 Windows 8。

有一些限制，对安装使用 Windows 安装程序的自定义图像。 有关详细信息，请参阅[Windows 安装方案和最佳做法](windows-setup-scenarios-and-best-practices.md)。

本主题︰

-   [将 Windows 产品 DVD 源文件复制到网络共享](#bkmk-1)

-   [创建主安装](#bkmk-2)

-   [捕获安装映像](#bkmk-3)

-   [创建自定义答案文件](#bkmk-4)

-   [通过使用 Windows 安装程序部署映像](#bkmk-5)

## <a name="span-idprerequisitesspanspan-idprerequisitesspanspan-idprerequisitesspanprerequisites"></a><span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>系统必备组件


若要完成本演练，您需要以下各项︰

-   技术人员计算机。 技术人员计算机是任何具有 Windows 评估和部署工具包 (Windows ADK) 工具安装的计算机。.

-   Windows 8 产品 DVD。

-   一台主计算机安装和捕获自定义映像。

-   可引导 Windows PE 介质。 有几种类型的 Windows PE 介质，您可以创建。 有关这些选项的详细信息，请参阅[Windows 10 的 WinPE](winpe-intro.md)。

-   若要保存您的自定义图像和 Windows 安装资源文件的网络共享的访问。

## <a name="span-idbkmk1spanspan-idbkmk1spanstep-1-copy-the-windows-product-dvd-source-files-to-a-network-share"></a><span id="bkmk_1"></span><span id="BKMK_1"></span>步骤 1︰ 将 Windows 产品 DVD 源文件复制到网络共享


在技术人员计算机上，Windows 产品 DVD 的整个内容复制到网络共享。 例如︰

``` syntax
net use N: \\server\share\
xcopy D: N:\WindowsDVD\ /s
```

其中，d︰ 是您的本地计算机上的 DVD-ROM 驱动器。

## <a name="span-idbkmk2spanspan-idbkmk2spanstep-2-create-a-master-installation"></a><span id="bkmk_2"></span><span id="BKMK_2"></span>步骤 2︰ 创建主安装


1.  通过使用下列方法之一来创建主安装︰

    -   [从 DVD 启动](boot-from-a-dvd.md)

    -   [使用 Windows 安装程序配置集](use-a-configuration-set-with-windows-setup.md)

2.  安装完毕后，关闭计算机。

## <a name="span-idbkmk3spanspan-idbkmk3spanstep-3-capture-an-image-of-the-installation"></a><span id="bkmk_3"></span><span id="BKMK_3"></span>第 3 步︰ 捕获安装映像


在此步骤中，将使用部署映像服务和管理 (**DISM**) 工具捕获参考安装的映像，然后将自定义映像存储在网络共享上。

1.  使用可引导的 Windows PE 介质引导参考计算机。

2.  在命令提示符下，捕获安装映像。 您指定的名称和说明作为图像捕获的一部分。 所有值所都需的 Windows 安装程序。 如果.wim 文件不包含这些值，然后映像将无法正确安装。 例如︰

    ``` syntax
    Dism /Capture-Image /ImageFile:C:\myimage.wim /CaptureDir:c:\ /Compress:fast /CheckIntegrity /ImageName:"x86_Ultimate" /ImageDescription:"x86 Ultimate Compressed"
    ```

3.  您的自定义图像替换默认值 Install.wim 网络共享上。 图像必须调用 Install.wim。 例如︰

    ``` syntax
    net use N: \\server\share\
    copy C:\myimage.wim N:\WindowsDVD\sources\install.wim
    ```

    如果有必要，请提供网络凭据以进行适当的网络访问。

有关详细信息，请参阅[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)。

## <a name="span-idbkmk4spanspan-idbkmk4spanstep-4-create-a-custom-answer-file"></a><span id="bkmk_4"></span><span id="BKMK_4"></span>步骤 4︰ 创建自定义答案文件


在此步骤中，您将创建指向您的自定义映像的答案文件。 此步骤假定您已经生成一个应答文件，有一个工作目录。

1.  技术人员计算机上打开**Windows 系统映像管理器**。

2.  在**文件**菜单上，单击**新的应答文件**。

3.  在 Windows SIM 中的**Windows 映像**窗格中，展开**组件**节点以显示可用的设置。

4.  通过右键单击组件，然后选择适当的配置阶段，将以下组件添加到答案文件。

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left">组件</th>
    <th align="left">配置阶段</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><p><strong>Microsoft 的 Windows Setup\DiskConfiguration\Disk\CreatePartitions\ CreatePartition</strong></p></td>
    <td align="left"><p><strong>windowsPE</strong></p></td>
    </tr>
    <tr class="even">
    <td align="left"><p><strong>Microsoft 的 Windows Setup\DiskConfiguration\Disk\ModifyPartitions\ ModifyPartition</strong></p></td>
    <td align="left"><p><strong>windowsPE</strong></p></td>
    </tr>
    <tr class="odd">
    <td align="left"><p><strong>Microsoft 的 Windows Setup\ImageInstall\OSImage\InstallTo</strong></p></td>
    <td align="left"><p><strong>windowsPE</strong></p></td>
    </tr>
    </tbody>
    </table>

    **请注意**  
    展开组件列表，直到您看到在前面的表中，列出的最低设置，然后将该设置添加到答案文件。 此快捷方式会将该设置和所有父设置添加到答案文件中的一个步骤。

5.  所有您添加的设置必须出现在**应答文件**窗格中。 选择并配置在下表中指定的每个设置。

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left">组件</th>
    <th align="left">值</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><p><strong>Microsoft 的 Windows Setup\DiskConfiguration</strong></p></td>
    <td align="left"><pre class="syntax" space="preserve"><code>WillShowUI = OnError</code></pre></td>
    </tr>
    <tr class="even">
    <td align="left"><p><strong>Microsoft 的 Windows Setup\DiskConfiguration\Disk</strong></p></td>
    <td align="left"><pre class="syntax" space="preserve"><code>DiskID = 0
    WillWipeDisk = true</code></pre></td>
    </tr>
    <tr class="odd">
    <td align="left"><p><strong>Microsoft 的 Windows Setup\DiskConfiguration\Disk\CreatePartitions\CreatePartition</strong></p></td>
    <td align="left"><pre class="syntax" space="preserve"><code>Extend = false
    Order = 1
    Size = 300</code></pre>
    <pre class="syntax" space="preserve"><code>Type = Primary</code></pre></td>
    </tr>
    <tr class="even">
    <td align="left"><p><strong>Microsoft 的 Windows Setup\DiskConfiguration\Disk\CreatePartitions\CreatePartition</strong></p></td>
    <td align="left"><pre class="syntax" space="preserve"><code>Extend = true
    Order = 2</code></pre>
    <pre class="syntax" space="preserve"><code>Type = Primary</code></pre></td>
    </tr>
    <tr class="odd">
    <td align="left"><p><strong>Microsoft 的 Windows Setup\DiskConfiguration\Disk\ModifyPartitions\ModifyPartition</strong></p></td>
    <td align="left"><pre class="syntax" space="preserve"><code>Active = true
    Extend = false
    Format = NTFS
    Label = System
    Letter = S
    Order = 1
    PartitionID = 1</code></pre></td>
    </tr>
    <tr class="even">
    <td align="left"><p><strong>Microsoft 的 Windows Setup\DiskConfiguration\Disk\ModifyPartitions\ModifyPartition</strong></p></td>
    <td align="left"><pre class="syntax" space="preserve"><code>Extend = false
    Format = NTFS
    Label = Windows
    Letter = C
    Order = 2
    PartitionID = 2</code></pre>
    <p></p></td>
    </tr>
    <tr class="odd">
    <td align="left"><p><strong>Microsoft 的 Windows Setup\ImageInstall\OSImage\</ 强 ></p></td>
    <td align="left"><pre class="syntax" space="preserve"><code>WillShowUI = OnError</code></pre></td>
    </tr>
    <tr class="even">
    <td align="left"><p><strong>Microsoft 的 Windows Setup\ImageInstall\OSImage\InstallTo</strong></p></td>
    <td align="left"><pre class="syntax" space="preserve"><code>DiskID = 0
    PartitionID = 2</code></pre></td>
    </tr>
    </tbody>
    </table>

6.  在命令提示符窗口将答案文件复制到某个网络位置中。 例如︰

    ``` syntax
    net use N: \\server\share\
    md N:\AnswerFiles
    copy C:\deploy_unattend.xml N:\AnswerFiles\
    ```

    如果有必要，请提供网络凭据以进行适当的网络访问。

## <a name="span-idbkmk5spanspan-idbkmk5spanstep-5-deploy-the-image-by-using-windows-setup"></a><span id="bkmk_5"></span><span id="BKMK_5"></span>步骤 5︰ 部署映像，使用 Windows 安装程序


在此步骤中，您将部署自定义映像从网络共享到目标计算机。

1.  使用可引导的 Windows PE 介质引导目标计算机。

2.  连接到网络共享中指定[步骤 4︰ 创建自定义答案文件](#bkmk-4)，然后使用答案文件运行安装程序。 例如︰

    ``` syntax
    net use N: \\server\share
    N:\WindowsDVD\setup /unattend:N:\AnswerFiles\deploy_unattend.xml
    ```

    如果有必要，请提供网络凭据以进行适当的网络访问。

## <a name="span-idnextstepsspanspan-idnextstepsspanspan-idnextstepsspannext-steps"></a><span id="Next_Steps"></span><span id="next_steps"></span><span id="NEXT_STEPS"></span>下一步行动


您可以进一步自定义答案文件以包含其他选项。 您还可以生成包含相同的内容放在网络共享上的 DVD 部署介质。 单个部署 DVD 提供了一种便携式安装解决方案，不需要网络或任何其他资源。 该过程包括构建配置集和重新捕获到单个 DVD 的所有源文件。

**重要**  
DVD 介质，您创建的是仅用于内部部署。 不能重新分发该媒体。

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Windows 安装程序技术参考](windows-setup-technical-reference.md)

[从 DVD 启动](boot-from-a-dvd.md)

[使用 Windows 安装程序配置集](use-a-configuration-set-with-windows-setup.md)

[引导到审核模式或 OOBE 的窗口](boot-windows-to-audit-mode-or-oobe.md)

[在 Windows 安装期间添加到 Windows 的设备驱动程序](add-device-drivers-to-windows-during-windows-setup.md)

[向 Windows 安装程序中添加自定义脚本](add-a-custom-script-to-windows-setup.md)

 

 






