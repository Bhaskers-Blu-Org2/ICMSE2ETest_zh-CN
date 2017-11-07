---
author: Justinha
Description: "使用产品密钥和激活"
ms.assetid: 923c0cd1-527c-4610-b979-e068fcc0ef99
MSHAttr: PreferredLib:/library/windows/hardware
title: "使用产品密钥和激活"
ms.openlocfilehash: 1dbf0cb2c98b48736789bdb08b462ddf779f15be
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="work-with-product-keys-and-activation"></a>使用产品密钥和激活


可以通过在答案文件中包括的 Windows® 自动化安装过程中输入产品密钥。

产品密钥也可以用于选择要自动化 Windows 安装过程中安装的映像。

## <a name="span-idinthistopicspanspan-idinthistopicspanspan-idinthistopicspanin-this-topic"></a><span id="In_this_Topic"></span><span id="in_this_topic"></span><span id="IN_THIS_TOPIC"></span>本主题中


-   [选择安装的 Windows 版本](#selectwhichwindowstoinstall)

-   [激活窗口](#activatewindowsbyusingaproductkey)

## <a name="span-idselectwhichwindowstoinstallspanspan-idselectwhichwindowstoinstallspanspan-idselectwhichwindowstoinstallspanselect-which-windows-edition-to-install"></a><span id="SelectWhichWindowsToInstall"></span><span id="selectwhichwindowstoinstall"></span><span id="SELECTWHICHWINDOWSTOINSTALL"></span>选择安装的 Windows 版本


若要选择要安装的 Windows 版本，可以执行以下任一操作︰

-   不使用答案文件手动安装 Windows。 Windows 安装程序从 Windows 产品 DVD 安装的默认版本。

-   使用应答文件，安装 Windows 并在 Microsoft Windows 安装程序中包含一个产品密钥\\UserData\\的产品密钥\\`Key`。 每个产品密钥是特定的 Windows 版本。 在此设置中输入的产品密钥不能激活 Windows。

-   使用应答文件，安装 Windows，然后手动键入产品密钥在 Windows 安装过程。 产品密钥选择要安装的 Windows 版本。

**警告**  
如果您有多个 Windows 映像使用的相同的 Windows 版本存储在同一个 Windows 映像文件 (.wim)，您可以使用设置︰ Microsoft Windows 安装程序\\ImageInstall\\OSImage\\InstallFrom\\ `MetaData`以区分它们。 您仍然必须提供产品密钥使用上述列表中列出的方法之一。

 

有关管理时将 Windows 映像更改为较高版本的 Windows 产品密钥的信息，请参阅[更改为更高版本使用 DISM 将 Windows 映像](change-the-windows-image-to-a-higher-edition-using-dism.md)。

## <a name="span-idactivatewindowsbyusingaproductkeyspanspan-idactivatewindowsbyusingaproductkeyspanspan-idactivatewindowsbyusingaproductkeyspanactivate-windows"></a><span id="ActivateWindowsByUsingAProductKey"></span><span id="activatewindowsbyusingaproductkey"></span><span id="ACTIVATEWINDOWSBYUSINGAPRODUCTKEY"></span>激活窗口


要自动通过使用产品密钥激活 Windows，可以执行以下任一操作︰

-   使用 Microsoft Windows 的外壳程序-安装\\`ProductKey`无人参与的设置。 您可以使用一次性产品密钥或卷许可证多次激活密钥。 有关详细信息，请参阅[卷激活规划指南](http://go.microsoft.com/fwlink/p/?LinkID=734870)。

    用来激活 Windows 的产品密钥必须与您所安装的 Windows 版本相匹配。 如果您使用的产品密钥选择 Windows 版本，我们建议使用相同的密钥来激活 Windows，以便您安装的版本是您激活的版本相同。

-   原始设备制造商 (Oem) 可以使用特定于 OEM 激活工具。

如果一个产品密钥未提供之前的全新体验 (OOBE)，OOBE 将提示最终用户提供产品密钥。 如果最终用户跳过这在 OOBE 期间，用户将稍后提醒输入有效的产品密钥。

**警告**  
在大多数 Windows 8 的部署方案，您不再需要使用`SkipRearm`回答时多次在计算机上运行**Sysprep**命令重置 Windows 产品激活时钟的设置文件。 在 Windows 8，`SkipRearm`设置用于指定授权状态的窗口。 如果您指定的零售产品密钥或批量许可证产品密钥，将自动激活 Windows。 您可以运行**Sysprep**命令到 8 次的单一 Windows 映像上。 Windows 8 映像上运行 Sysprep 8 倍后, 您必须重新创建 Windows 映像。 有关 Windows 组件和设置，您可以将它们添加到答案文件的详细信息，请参阅[无人参与的 Windows 安装程序参考](http://go.microsoft.com/fwlink/?LinkId=206281)。

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Windows 部署选项](windows-deployment-options.md)

[配置阶段的工作](how-configuration-passes-work.md)

[Sysprep （通用化） Windows 安装](sysprep--generalize--a-windows-installation.md)

[将 Windows 映像更改为较高版本使用 DISM](change-the-windows-image-to-a-higher-edition-using-dism.md)

 

 






