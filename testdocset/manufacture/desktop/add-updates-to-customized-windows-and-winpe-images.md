---
author: Justinha
Description: "Microsoft 将提供到需要自定义 Windows 映像上安装的 Windows 10 更新程序包。 将零天包 (ZDP) 添加到现有的 Windows 10 图像来向用户提供最新的更新。"
ms.assetid: 3273a638-d635-45e8-b418-ee9c5b06333e
MSHAttr: PreferredLib:/library/windows/hardware
title: "将更新添加到自定义 Windows 映像"
ms.openlocfilehash: 45f861a9e61b35c48ee20fce7138996ffb673c08
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add-updates-to-customized-windows-images"></a>将更新添加到自定义 Windows 映像


Microsoft 将提供到需要自定义 Windows 映像上安装的 Windows 10 更新程序包。 将零天包 (ZDP) 添加到现有的 Windows 10 图像来向用户提供最新的更新。

本主题介绍如何安装到 Windows 映像，以及任何其他更新，Microsoft 发布的 Windows 10 ZDP。

ZDP 更新为 10240 和今天的所有更新汇总发布 Windows 10 生成之间。

**请注意** 截止于 2015 年 8 月 8 日︰
-   使用 Windows PE 和 Windows RE ADK 10240 生成版本。 除非另有指示，否则不要更新 Windows PE 或 Windows RE 的版本。
-   不要在应用 ZDP 脱机之后使用**/ResetBase** (DISM /Cleanup-Image /ResetBase)。 ZDP 有挂起的操作，必须在运行 /ResetBase 前完成。
-   只是不能到无人参与的安装应答文件添加 ZDP-它在安装之前，必须更新整个图像。

 

## <a name="span-idstartwithyourcustomizedimagespanspan-idstartwithyourcustomizedimagespanspan-idstartwithyourcustomizedimagespan-start-with-your-customized-image"></a><span id="_Start_with_your_customized_image"></span><span id="_start_with_your_customized_image"></span><span id="_START_WITH_YOUR_CUSTOMIZED_IMAGE"></span>开始使用您的自定义映像


开始使用您现有的自定义 Windows 映像，使用 Windows 10 10240 生成。

考虑添加语言包之前添加 ZDP 更新--它可能会节省您的时间以后。 若要了解详细信息，请参阅该主题并[将语言包添加到 Windows](add-language-packs-to-windows.md)的末尾的注释。

## <a name="span-iddownloadthezdpspanspan-iddownloadthezdpspanspan-iddownloadthezdpspan-download-the-zdp"></a><span id="_Download_the_ZDP"></span><span id="_download_the_zdp"></span><span id="_DOWNLOAD_THE_ZDP"></span>下载 ZDP


下载最新的更新。 注意，ZDP 是累积更新，因此您只需要获取最新的更新包。

-   Windows 10 64 位版本︰ <http://go.microsoft.com/fwlink/?LinkId=619271>。
-   Windows 10 32 位版本︰ [http://go.microsoft.com/fwlink/?LinkId=619272](http://go.microsoft.com/fwlink/?LinkId=619271)。

## <a name="span-idupdateyourimagesspanspan-idupdateyourimagesspanspan-idupdateyourimagesspanupdate-your-images"></a><span id="Update_your_images"></span><span id="update_your_images"></span><span id="UPDATE_YOUR_IMAGES"></span>更新您的图像


1.  从技术人员计算机，单击**开始**并键入**部署**。 用鼠标右键单击**部署和图像处理工具环境**，然后选择**以管理员身份运行**。
2.  创建 Windows 映像 (install.wim) 的安装目录，然后装载映像。

    ``` syntax
    md C:\mount\Windows

    Dism /Mount-Image /ImageFile:"C:\Images\install.wim" /Index:1 /MountDir:C:\mount\Windows
    ```

3.  与最新 ZDP 更新 Windows 映像。 示例：

    ``` syntax
    Dism /Add-Package /Image:C:\mount\Windows /PackagePath:C:\MSU\Windows10-KBxxxxxxx-x64.msu /LogPath:AddPackage.log
    ```

    其中 c:\\MSU\\Windows10-KBxxxxxxx-x64.msu 是 ZDP 可用的最新版本。

4.  卸载 Windows 映像。

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\mount\Windows /Commit
    ```

**建议︰ 启动以完成更新过程中，该图像，然后清理图像**

1.  引导到 Windows PE 的参考设备。
2.  按**Ctrl + Shift + F3**在 OOBE 屏幕进入审核模式。
3.  以管理员身份打开命令提示符。
4.  Windows 映像进行清理。 （它是确定现在，PC 已启动到审核模式下使用 /ResetBase）。

    ``` syntax
    Dism /Cleanup-Image /Online /StartComponentCleanup /ResetBase
    ```

    **请注意** 您将无法清理 Windows 映像之前后中已启动它。

     

5.  使用 Sysprep 来归纳和关闭 PC。

    ``` syntax
    C:\Windows\System32\Sysprep\sysprep /generalize /shutdown /oobe
    ```

6.  到 Windows PE 启动 PC。 如果 PC 启动重新启动到 Windows 后，您需要让它完成启动，然后使用 Sysprep 归纳并再次关闭 PC。
7.  DISM 物理驱动器，而不是默认 Windows PE 虚拟驱动器，以避免问题与短文件名创建临时的暂存目录。 要防止捕获 DISM 日志在您的映像中，请选择一个位置，位于在 DISM 的排除列表中，例如，c:\\回收程序。 有关更多信息，请参见[DISM 配置列表和 WimScript.ini 文件](dism-configuration-list-and-wimscriptini-files-winnext.md)。

    ``` syntax
    md C:\Recycler\Scratch
    ```

8.  重新捕获 Windows 映像。 这捕获应用的更新，并删除已标记为在 DISM /Cleanup-Image 所取代的任何文件。 USB 驱动器或网络上将该文件保存到一个位置 (示例︰ n:\\图像)，并为图像指定名称 (示例:"企业\_ZDP KBxxxxxxx 使用 x64")。

    ``` syntax
    DISM /Capture-Image /ImageFile:"N:\Images\install_updated.wim" /CaptureDir:C: /Name: "Enterprise_x64 with ZDP KBxxxxxxx" /ScratchDir:C:\Recycler\Scratch
    ```

 **更新 Windows 安装程序可引导介质**

1.  将可启动的介质 （Dvd 或其它可引导介质为 Windows 安装程序、 Windows 部署服务 (WDS) 或 System Center） 复制到可写文件夹在您的 PC 上。

    ``` syntax
    Xcopy D:\ C:\InstallMedia /s /h
    ```

2.  装载文件︰ 源\\boot.wim。

    ``` syntax
    md C:\mount\boot
    Dism /Mount-Image /ImageFile:"C:\InstallMedia\sources\boot.wim" /Index:1 /MountDir:C:\mount\boot
    ```

3.  添加 ZDP。

    ``` syntax
    Dism /Add-Package /PackagePath:/PackagePath:C:\MSU\Windows10-KBxxxxxxx-x64.msu /Image:C:\mount\boot /LogPath:AddPackage.log
    ```

    其中 c:\\MSU\\Windows10-KBxxxxxxx-x64.msu 是 ZDP 可用的最新版本。

4.  在 Windows 资源管理器，定位到已装载的映像的根文件夹，按修改日期对文件列表进行排序。 将所有内容已被复制到安装媒体的根最近修改 （setup.exe、 locale.nls、 setupplatform.dll、 setupplatform.exe、 reagent.dll，和别处查找最近修改的）。
5.  卸载的 boot.wim 文件。

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\mount\boot /Commit
    ```

6.  创建可引导介质 （Dvd 或其它可引导介质为 Windows 安装程序、 Windows 部署服务 (WDS) 或 System Center） 使用的文件。 若要了解详细信息，请参阅[Windows 安装程序技术参考](windows-setup-technical-reference.md)。

## <a name="span-idaddinglanguagesafteraddingthezdporotherrolluppackagesspanspan-idaddinglanguagesafteraddingthezdporotherrolluppackagesspanspan-idaddinglanguagesafteraddingthezdporotherrolluppackagesspanadding-languages-after-adding-the-zdp-or-other-rollup-packages"></a><span id="Adding_languages_after_adding_the_ZDP_or_other_rollup_packages"></span><span id="adding_languages_after_adding_the_zdp_or_other_rollup_packages"></span><span id="ADDING_LANGUAGES_AFTER_ADDING_THE_ZDP_OR_OTHER_ROLLUP_PACKAGES"></span>添加 ZDP 或其他汇总程序包之后添加语言


理想情况下，您需要添加任何 ZDPs 或 Windows 汇总程序包之前添加的所有语言包和组件。

如果您需要按需安装 ZDP 或其他汇总程序包之后添加语言包或语言功能，您需要以后重新应用 ZDP/汇总包。 否则为 Windows 用户体验可能不会正确本地化，并且用户可能会提示您从 Windows Update 下载的语言资源。

## <a name="span-idsamplescriptspanspan-idsamplescriptspanspan-idsamplescriptspansample-script"></a><span id="Sample_script"></span><span id="sample_script"></span><span id="SAMPLE_SCRIPT"></span>示例脚本


下面的示例脚本修改给定的 Windows 映像的特定文件夹中的所有更新添加到图像。 添加图像之后, 它清除图像。

``` syntax
REM # InjectPackages.cmd: Adds packages (.cbs, .cab, .msu) to a Windows image
REM # Usage:   InjectPackages <.WIM file> <Index> <Folder with CBS packages>
REM # Example: InjectPackages C:\Images\install.wim 1 C:\Packages\ZDP
REM #
REM # Given a Windows image, an index, and a folder with packages (.cbs, .cab, or .msu),
REM # this injects the packages into the wim offline
REM #

@echo off
echo %date% - %time%:: starting ,,,

set _dism_log=%~dp0dism_add_packages.log
del %_dism_log%

set _input_wim=%1
echo %date% - %time%:: caller gave us a wim: [%_input_wim%]. dir it to verify ,,,
     dir %_input_wim%
if not exist %_input_wim% (
 echo fail!!! %_input_wim% not found
 exit /b 2
)

set _index=%2
echo %date% - %time%:: caller gave us index=[%_index%]. verify it,,,
echo %date% - %time%:: dism /logpath=%_dism_log% /get-imageinfo /imagefile=%_input_wim% /index=%_index%
     dism /logpath=%_dism_log% /get-imageinfo /imagefile=%_input_wim% /index=%_index%
if %errorlevel% neq 0 (
  echo dism failed!!! please verify index [%_index%] is correct.
  exit /b %errorlevel%
)


set _package_folder=%3
echo %date% - %time%:: caller gave us folder: [%_package_folder%]. dir it to verify ,,,
     dir %_package_folder%\
if not exist %_package_folder%\ (
 echo fail!!! %_package_folder%\ not found!
 exit /b 2
)

if not exist %~dp0mnt\ (
 mkdir %~dp0mnt\
)

echo %date% - %time%:: unmount to start clean. you can ignore if this fails.
echo %date% - %time%:: dism /logpath=%_dism_log% /unmount-image /mountdir=%~dp0mnt\ /discard
     dism /logpath=%_dism_log% /unmount-image /mountdir=%~dp0mnt\ /discard

echo %date% - %time%:: mount the input wim ,,,
echo dism /logpath=%_dism_log% /mount-image /imagefile=%_input_wim% /index=%_index% /mountdir=%~dp0mnt\ 
     dism /logpath=%_dism_log% /mount-image /imagefile=%_input_wim% /index=%_index% /mountdir=%~dp0mnt\ 
if %errorlevel% neq 0 (
  echo dism failed!!! 
  exit /b %errorlevel%
)
echo %date% - %time%:: good.

echo %date% - %time%:: look for *.msu files ,,,
echo dir %_package_folder%\*.msu
     dir %_package_folder%\*.msu
for /r %_package_folder% %%a in (*.msu) do (
  echo dism /logpath=%_dism_log% /image=%~dp0mnt\ /add-package=%%a
       dism /logpath=%_dism_log% /image=%~dp0mnt\ /add-package=%%a
  if %errorlevel% neq 0 (
    echo dism failed!!! 
    exit /b %errorlevel%
  )
)

echo %date% - %time%:: look for *.cab files ,,,
echo dir %_package_folder%\*.cab
     dir %_package_folder%\*.cab
for /r %_package_folder% %%a in (*.cab) do (
  echo dism /logpath=%_dism_log% /image=%~dp0mnt\ /add-package=%%a
       dism /logpath=%_dism_log% /image=%~dp0mnt\ /add-package=%%a
  if %errorlevel% neq 0 (
    echo dism failed!!! 
    exit /b %errorlevel%
  )
)

echo %date% - %time%:: DONE adding packages.

echo %date% - %time%:: run clean up ,,,
  echo dism /logpath=%_dism_log% /image=%~dp0mnt\ /cleanup-image /startcomponentcleanup
       dism /logpath=%_dism_log% /image=%~dp0mnt\ /cleanup-image /startcomponentcleanup
  REM ### Do not use /ResetBase. The ZDP has pending actions that must be completed first.##

  if %errorlevel% neq 0 (
    echo dism failed to clean up. we ignore this for now.
  )



echo %date% - %time%:: commiting the changes ,,,
echo dism /logpath=%_dism_log% /unmount-image /mountdir=%~dp0mnt\ /commit
     dism /logpath=%_dism_log% /unmount-image /mountdir=%~dp0mnt\ /commit
if %errorlevel% neq 0 (
  echo dism failed!!! 
  exit /b %errorlevel%
)


echo %date% - %time%:: exporting the wim to reduce size ,,,
echo dism /logpath=%_dism_log% /export-image /sourceimagefile=%_input_wim% /sourceindex=%_index% /destinationimagefile=%_input_wim%_exported.wim
     dism /logpath=%_dism_log% /export-image /sourceimagefile=%_input_wim% /sourceindex=%_index% /destinationimagefile=%_input_wim%_exported.wim
if %errorlevel% neq 0 (
  echo dism failed!!! 
  exit /b %errorlevel%
)

echo %date% - %time%:: ALL DONE.
dir %_input_wim% 
dir %_input_wim%_exported.wim
echo please use %_input_wim%_exported.wim for further testing.
```

 

 





