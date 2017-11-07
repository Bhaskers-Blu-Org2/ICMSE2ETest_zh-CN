---
author: Justinha
Description: "WinPE︰ 将 Windows PowerShell 支持添加到 Windows PE"
ms.assetid: 8b653cf6-3584-4c80-be84-ca32d60aeba2
MSHAttr: PreferredLib:/library/windows/hardware
title: "WinPE︰ 将 Windows PowerShell 支持添加到 Windows PE"
ms.openlocfilehash: 28bdc32f0ed7b4fe614d292014263709d2058a6c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="winpe-adding-windows-powershell-support-to-windows-pe"></a>WinPE︰ 将 Windows PowerShell 支持添加到 Windows PE


下面的示例脚本创建 Windows PE 的版本 Windows PowerShell 和其 DISM 和存储的 cmdlet，可用来以帮助自动执行 Windows 部署。

**准备 Windows PE 文件的本地副本**

1.  安装[Windows 评估和部署工具包 (ADK)](http://go.microsoft.com/fwlink/p/?LinkID=526803)，添加的**部署工具**和**Windows PE**的功能。

2.  作为**管理员**启动**部署和图像处理工具环境**。

3.  创建 Windows PE 文件的工作副本。 指定任一 x86，amd64 或配置︰

    ``` syntax
    copype amd64 C:\WinPE_amd64_PS
    ```

## <a name="span-idsamplescriptspanspan-idsamplescriptspanspan-idsamplescriptspansample-script"></a><span id="SampleScript"></span><span id="samplescript"></span><span id="SAMPLESCRIPT"></span>示例脚本


使用下面的脚本来装载 Windows 映像，添加 Windows PowerShell Windows PE 可选组件并卸载映像。

``` syntax
Dism /Mount-Image /ImageFile:"C:\WinPE_amd64_PS\media\sources\boot.wim" /Index:1 /MountDir:"C:\WinPE_amd64_PS\mount"

Dism /Add-Package /Image:"C:\WinPE_amd64_PS\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-WMI.cab"

Dism /Add-Package /Image:"C:\WinPE_amd64_PS\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-WMI_en-us.cab"

Dism /Add-Package /Image:"C:\WinPE_amd64_PS\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-NetFX.cab"

Dism /Add-Package /Image:"C:\WinPE_amd64_PS\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-NetFX_en-us.cab"

Dism /Add-Package /Image:"C:\WinPE_amd64_PS\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-Scripting.cab"

Dism /Add-Package /Image:"C:\WinPE_amd64_PS\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-Scripting_en-us.cab"

Dism /Add-Package /Image:"C:\WinPE_amd64_PS\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-PowerShell.cab"

Dism /Add-Package /Image:"C:\WinPE_amd64_PS\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-PowerShell_en-us.cab"

Dism /Add-Package /Image:"C:\WinPE_amd64_PS\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-StorageWMI.cab"

Dism /Add-Package /Image:"C:\WinPE_amd64_PS\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-StorageWMI_en-us.cab"

Dism /Add-Package /Image:"C:\WinPE_amd64_PS\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-DismCmdlets.cab"

Dism /Add-Package /Image:"C:\WinPE_amd64_PS\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-DismCmdlets_en-us.cab"

Dism /Unmount-Image /MountDir:C:\WinPE_amd64_PS\mount /Commit
```

## <a name="span-idinstallthisversionofwindowspetoausbkeyspanspan-idinstallthisversionofwindowspetoausbkeyspanspan-idinstallthisversionofwindowspetoausbkeyspaninstall-this-version-of-windows-pe-to-a-usb-key"></a><span id="Install_this_version_of_Windows_PE_to_a_USB_key"></span><span id="install_this_version_of_windows_pe_to_a_usb_key"></span><span id="INSTALL_THIS_VERSION_OF_WINDOWS_PE_TO_A_USB_KEY"></span>Usb 闪存盘上安装此版本的 Windows PE


``` syntax
MakeWinPEMedia /UFD C:\WinPE_amd64_PS F:
```

## <a name="span-idstartwindowspowershellinwindowspespanspan-idstartwindowspowershellinwindowspespanspan-idstartwindowspowershellinwindowspespanstart-windows-powershell-in-windows-pe"></a><span id="Start_Windows_PowerShell_in_Windows_PE"></span><span id="start_windows_powershell_in_windows_pe"></span><span id="START_WINDOWS_POWERSHELL_IN_WINDOWS_PE"></span>在 Windows PE 启动 Windows PowerShell


引导到 Windows PE 中使用此 usb 闪存盘的 PC 后，启动 Windows PowerShell:

``` syntax
X:\Windows\system32\WindowsPowerShell\v1.0\powershell
```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[对于 Windows 10 WinPE](winpe-intro.md)

[WinPE︰ 添加软件包 （可选的组件参考）](winpe-add-packages--optional-components-reference.md)

[WinPE︰ 创建可引导 USB 驱动器](winpe-create-usb-bootable-drive.md)

[WinPE︰ 创建启动 CD、 DVD、 ISO 或 VHD](winpe-create-a-boot-cd-dvd-iso-or-vhd.md)

[WinPE︰ 安装和自定义](winpe-mount-and-customize.md)

 

 






