---
title: "查看配置文件"
description: "查看配置文件"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 5103d6a8-8136-4667-9316-e824ecb44aaf
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 45534cabac4f49fe67d981e9a70ed0ecbdb3eb53
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="view-profiles"></a>查看配置文件


查看配置文件存储视图的布局，您可以使用快速启动分析。 自定义布局之后，可以将其保存为启动配置文件或创建一个配置文件，您可以应用在任何时候。

查看配置文件是存储在.wpaprofile 文件中，默认情况下，给用户的文档文件夹下的 WPA 文件文件夹中保存。

有关更改视图的布局的信息，请参阅[更改视图的布局](change-the-view-layout.md)。

## <a name="creating-a-profile"></a>创建配置文件


若要创建一个配置文件，请首先为您希望其出现，然后执行下列配置视图布局︰

1.  在菜单中选择 [连接**配置文件**，**导出...**。

2.  导航到所需位置。

3.  命名您的配置文件，并选择**保存**。

## <a name="applying-a-profile"></a>应用配置文件


若要将配置文件应用于一个或多个打开的跟踪，请执行以下操作︰

1.  在菜单中选择 [连接**配置文件**，**应用...**。

2.  在显示窗格中，选择**浏览...** 若要打开一个自定义的配置文件，或选择**浏览目录...** 若要查看 WPA 附带的配置文件列表。

3.  导航到并选择所需的配置，然后选择**打开**。

4.  如果您有多个跟踪打开，或者如果配置文件被配置为多个跟踪，WPA 要求您将跟踪与配置文件相关联。 选择所需的跟踪信息，然后选择**应用**。

**请注意**  
WPA 还维护下**的配置文件**，**应用最近使用的配置文件**菜单中最近使用的配置文件的列表。

 

## <a name="profile-catalog"></a>配置文件目录


WPA 包括一组帮助 jumpstart 分析不同类型的配置文件。 这些配置文件包含在找您将配置文件应用于打开跟踪**配置文件目录**︰

-   AppLaunch

-   FastStartup

-   FullBoot （启动）

-   FullBoot （关机）

-   休眠状态

-   HTMLApplicationAnalysis

-   PresetsForComparativeAnalysis

-   待机

-   XAMLApplicationAnalysis

## <a name="changing-the-startup-profile"></a>更改启动配置文件


您还可以在您首次打开跟踪时使用的默认配置使用您的当前视图︰

1.  在菜单上，选择 [连接**配置文件**，**保存的启动配置文件**。

2.  在出现的确认框中选择**确定**。

**请注意**  
当多个跟踪都打开时，您无法更改启动配置文件。

 

## <a name="related-topics"></a>相关的主题


[WPA 功能](wpa-features.md)

[比较分析视图](comparative-analysis-views.md)

 

 







