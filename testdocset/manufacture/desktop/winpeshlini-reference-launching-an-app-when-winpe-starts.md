---
author: Justinha
Description: "Winpeshl.ini 引用︰ 启动 WinPE 时启动应用程序"
ms.assetid: 107a3c05-791a-4daf-b188-b28dac96ef74
MSHAttr: PreferredLib:/library/windows/hardware
title: "Winpeshl.ini 引用︰ 启动 WinPE 时启动应用程序"
ms.openlocfilehash: 4d78819285ad43c36ff8c7ad86cd2df842782a22
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="winpeshlini-reference-launching-an-app-when-winpe-starts"></a>Winpeshl.ini 引用︰ 启动 WinPE 时启动应用程序


使用 Windows 预安装环境 (Windows PE) 中的**Winpeshl.ini**文件来替换为外壳应用程序或其他应用程序的默认命令提示符。 例如，您的 shell 应用程序可以提供部署工程师可以选择一种安装 Windows 的图形用户界面。

若要添加一个自定义的应用程序，创建名为 Winpeshl.ini 的文件，并将其放置在 %SYSTEMROOT%\\System32 的自定义的 Windows PE 映像。 有关详细信息，请参阅[WinPE︰ 安装和自定义](winpe-mount-and-customize.md)。

## <a name="span-idexamplespanspan-idexamplespanspan-idexamplespanexample"></a><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>示例


``` syntax
[LaunchApp]
AppPath = %SYSTEMDRIVE%\Fabrikam\shell.exe
[LaunchApps]
%SYSTEMDRIVE%\Fabrikam\app1.exe
%SYSTEMDRIVE%\Fabrikam\app2.exe, /s "C:\Program Files\App3"
```

Wpeshl.ini 文件可能具有一个或两个部分︰ \[LaunchApp\]和\[LaunchApps\]。 中列出的应用程序\[LaunchApp\]和\[LaunchApps\]运行顺序的外观，和以前的应用程序已终止之前不启动。

## <a name="span-idlaunchappspanspan-idlaunchappspanspan-idlaunchappspanlaunchapp"></a><span id="LaunchApp"></span><span id="launchapp"></span><span id="LAUNCHAPP"></span>LaunchApp


设置`AppPath`条目到您的应用程序的路径。 您可以使用完全限定的路径，也可以包括环境变量，如`%SYSTEMDRIVE%`描述路径。

**请注意**  
-   \[LaunchApp\]条目只能包含一个应用程序。

-   不能指定多于 250 个字符的命令。

-   您不能指定任何命令行选项与 LaunchApp。

 

## <a name="span-idlaunchappsspanspan-idlaunchappsspanspan-idlaunchappsspanlaunchapps"></a><span id="LaunchApps"></span><span id="launchapps"></span><span id="LAUNCHAPPS"></span>LaunchApps


使用`[LaunchApps]`部分中可使用命令行选项来运行应用程序。

**请注意**  
-   LaunchApps 支持运行应用程序，但不支持通用的脚本命令。 若要运行命令，请改为添加启动脚本 (startnet.cmd)。 有关详细信息，请参阅[WinPE︰ 安装和自定义](winpe-mount-and-customize.md)。

-   不能指定多于 250 个字符的命令。

-   若要将命令行选项添加到应用程序︰ 应用程序名称后面添加一个逗号 （，）︰`%SYSTEMDRIVE%\Fabrikam\app2.exe,  <option>`

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[对于 Windows 10 WinPE](winpe-intro.md)

[WinPE︰ 调试应用程序](winpe-debug-apps.md)

 

 






