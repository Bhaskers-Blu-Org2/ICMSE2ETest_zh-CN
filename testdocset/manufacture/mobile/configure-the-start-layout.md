---
Description: You can now easily configure the default Start layout to include Web links, secondary tiles, folders, and apps. The converged Windows 10 Start layout requires that you create a LayoutModification.xml file, which we'll create in this walkthrough.
ms.assetid: 99238b56-5c9c-4b5e-a750-e64a10e417af
MSHAttr: PreferredLib:/library
title: "配置开始布局"
author: CelesteDG
ms.openlocfilehash: 82d6babe0297b290a3da03f37a5ab34afc390446
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="configure-the-start-layout"></a>配置开始布局


现在，您可以轻松地配置默认的开始布局包括 Web 链接、 辅助磁贴、 文件夹和应用程序。 聚合的 Windows 10 开始布局要求您创建一个 LayoutModification.xml 文件，我们将在本演练中创建的。

**请注意** LayoutModification.xml 文件的架构是不同于 MCSF 自定义答案文件架构或 Windows 提供的答案文件架构。 您将需要使用 LayoutModification.xml 完全利用开始自定义 Windows 10 中，您可以使用引用 LayoutModification.xml MCSF 或 Windows 资源调配中的开始设置。

 

如果不是新窗口移动开发和使用预先存在的 MCSF 设置与开始布局有关，我们强烈建议您切换到 LayoutModification.xml，以充分利用开始体验。 此外请注意，并非所有预先存在的 MCSF 开始设置支持 Windows 10。

在本演练中，我们将︰

-   创建两个版本的开始布局，一个和另一个文件夹的文件夹。

-   配置 MCSF 开始布局设置，指定用于新布局修改 XML 我们布局，创建变型咖啡馆文件中，并指定哪些开始布局应用于我们创建的变量。

**请注意** 请确保您读过[启动 Windows 10 移动版的版式](https://msdn.microsoft.com/library/windows/hardware/mt171093)进行本演练之前。 该主题提供了在 LayoutModification.xml，不包括在此演练中，以及限制和限制，您需要知道的每个元素的更多详细的信息。

 

**若要配置开始布局修改文件**

1.  创建名为 LayoutModification1.xml 的文件。

2.  添加 XML 代码︰

    -   中等规模的针行 6 列 0 平铺。 拼贴是 MSN 新闻应用程序。
    -   中等规模的针行 6，第 2 列上的方块。 拼贴是 Contoso 主页上的 Web 链接。
    -   针行第四列第 6 的小型文件夹。 文件夹名称是"Contoso 应用程序"，它包含以下︰
        -   MSN 的应用程序应用程序中型平铺。
        -   MSN Money app 中型平铺。

    以下 XML 示例显示了您需要添加到 LayoutModification.xml 文件。

    ```XML
    <?xml version="1.0" encoding="utf-8"?>
    <LayoutModificationTemplate
        xmlns="http://schemas.microsoft.com/Start/2014/LayoutModification"
        xmlns:defaultlayout="http://schemas.microsoft.com/Start/2014/FullDefaultLayout"
        xmlns:start="http://schemas.microsoft.com/Start/2014/StartLayout"
        Version="1">
        <DefaultLayoutOverride>
          <StartLayoutCollection>
                <defaultlayout:StartLayout>
                  <start:Group>
                      <start:Tile
                        AppUserModelID="Microsoft.BingNews_8wekyb3d8bbwe!ApplicationID"
                        Size="2x2"
                        Row="6"
                        Column="0"/>
                      <start:SecondaryTile
                        AppUserModelID="Microsoft.MicrosoftEdge_8wekyb3d8bbwe!MicrosoftEdge"
                        TileID="MyWeblinkTile"
                        Arguments="http://www.contoso.com"
                        DisplayName="Contoso Homepage"
                        Square150x150LogoUri="ms-appx:///Assets/MicrosoftEdgeSquare150x150.png" 
                        Wide310x150LogoUri="ms-appx:///Assets/MicrosoftEdgeWide310x150.png"
                        ShowNameOnSquare150x150Logo="true"
                        ShowNameOnWide310x150Logo="false"
                        BackgroundColor="#FF112233"
                        Size="2x2"
                        Row="6"
                        Column="2"/>
                      <start:Folder
                        Name="Contoso apps"
                        Size="2x2"
                        Row="6"
                        Column="4">
                        <start:Tile
                          AppUserModelID="Microsoft.BingMaps_8wekyb3d8bbwe!ApplicationID"
                          Size="2x2"
                          Row="0"
                          Column="0"/>
                        <start:Tile
                          AppUserModelID="Microsoft.BingFinance_8wekyb3d8bbwe!ApplicationID"
                          Size="2x2"
                          Row="0"
                          Column="2"/>
                        <!-- Remove these comments if you have an app that you can preload and want to add to the folder
                        <start:Tile
                          AppUserModelID="TBD"
                          Size="2x2"
                          Row="0"
                          Column="4"/>
                        -->
                      </start:Folder>
                  </start:Group>
                </defaultlayout:StartLayout>
          </StartLayoutCollection>
        </DefaultLayoutOverride>
    </LayoutModificationTemplate>
    ```

3.  保存 xml 文件并记下该位置的文件;例如， *c:\\Contoso\\的自定义\\LayoutModification1.xml*。

4.  使用相同的 xml 文件，现在将其保存为*LayoutModification2.xml*。

5.  通过删除所有内容**开始︰ 文件夹**元素内和 MSN Money 应用程序用来替换该文件夹拼贴的位置来修改新的*LayoutModification2.xml*文件的内容。

    您的 XML 文件的内容应如下所示︰

    ```XML
    <?xml version="1.0" encoding="utf-8"?>
    <LayoutModificationTemplate
        xmlns="http://schemas.microsoft.com/Start/2014/LayoutModification"
        xmlns:defaultlayout="http://schemas.microsoft.com/Start/2014/FullDefaultLayout"
        xmlns:start="http://schemas.microsoft.com/Start/2014/StartLayout"
        Version="1">
        <DefaultLayoutOverride>
          <StartLayoutCollection>
                <defaultlayout:StartLayout>
                  <start:Group>
                      <start:Tile
                        AppUserModelID="Microsoft.BingNews_8wekyb3d8bbwe!ApplicationID"
                        Size="2x2"
                        Row="6"
                        Column="0"/>
                      <start:SecondaryTile
                        AppUserModelID="Microsoft.MicrosoftEdge_8wekyb3d8bbwe!MicrosoftEdge"
                        TileID="MyWeblinkTile"
                        Arguments="http://www.contoso.com"
                        DisplayName="Contoso Homepage"
                        Square150x150LogoUri="ms-appx:///Assets/MicrosoftEdgeSquare150x150.png" 
                        Wide310x150LogoUri="ms-appx:///Assets/MicrosoftEdgeWide310x150.png"
                        ShowNameOnSquare150x150Logo="true"
                        ShowNameOnWide310x150Logo="false"
                        BackgroundColor="#FF112233"
                        Size="2x2"
                        Row="6"
                        Column="2"/>
                      <start:Tile
                        AppUserModelID="Microsoft.BingFinance_8wekyb3d8bbwe!ApplicationID"
                        Size="2x2"
                        Row="6"
                        Column="4"/>
                  </start:Group>
                </defaultlayout:StartLayout>
          </StartLayoutCollection>
        </DefaultLayoutOverride>
    </LayoutModificationTemplate>
    ```

6.  保存 xml 文件并记下该位置的文件;例如， *c:\\Contoso\\的自定义\\LayoutModification2.xml*。

7.  添加布局修改文件和 MCSF 咖啡馆或 Windows 设置应答文件 (WPAF) 中配置的开始布局设置。

    -   MCSF︰ 请参阅[配置自定义设置](configure-customization-settings.md)中*配置的开始布局*。
    -   有关 Windows 设置︰ 如果您使用的是 Windows 图像处理和配置设计器 (ICD) 用户界面，请参阅*配置开始布局*中[使用 Windows ICD 用户界面进行自定义和生成的移动图像](use-the-windows-icd-ui-to-customize-and-build-a-mobile-image.md)。 如果您使用的 Windows ICD CLI （混合方法），请参阅*配置开始布局*中[使用 Windows ICD CLI 可以自定义和增强的移动图像](use-the-windows-icd-cli-to-customize-and-build-a-mobile-image.md)。

 

 



