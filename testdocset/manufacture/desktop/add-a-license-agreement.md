---
author: KPacquer
Description: "实验 8︰ 添加 OEM 许可协议"
ms.assetid: a29101dc-4922-44ee-a758-d555e6cf39fa
MSHAttr: PreferredLib:/library/windows/hardware
title: "实验 8︰ 添加许可协议"
ms.openlocfilehash: 77cf27ac6dc75a59fad4307579a5fc00f4bee061
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add-an-oem-license-agreement"></a>添加 OEM 许可协议

您可以添加到 Windows 的您的 OEM 许可协议条款。 

对于多区域或多语言映像，您可以创建区域特定许可条款。 这些过程中显示给用户首次登录体验，根据地区或他们选择的语言。 

注意︰ 如果许可协议条款包括，OEM 必须包含版本的许可条款中每种语言都预安装到计算机上。 许可条款文字必须是。另存为**rtf**文件。**rtf**格式。

在[USB B.zip](http://download.microsoft.com/download/5/8/4/5844EE21-4EF5-45B7-8D36-31619017B76A/USB-B.zip)项中使用的示例。

## <a name="span-idcreatelicensefilesspancreate-license-files"></a><span id="Create_license_files"></span>创建许可证文件

1.  创建下一个工作文件夹，例如，C:\oobe 文件夹。 

2.  作为**语言十进制标识符**相对应的语言命名每个 C:\oobe\info\default\ 目录下的文件夹。 执行此步骤，每个语言包添加到 Windows 映像。

    语言的相应语言的十进制标识符的完整列表，请参阅[可用语言包的 Windows](available-language-packs-for-windows.md)。

    例如，如果 en-我们，de de 语言包添加到 Windows 映像，添加一个名为"1033"文件夹 (表示 en-我们语言) 在 C:\mount\windows\Windows\System32\oobe\info\default\.然后添加名为"1031"（表示 de de 语言） 在同一个目录下的文件夹。

    ```syntax
    md c:\oobe\info\default\1033
    md c:\oobe\info\default\1031
    ```

1.  创建每种语言指定许可术语的文档。 将每个许可证术语文档移动到相应语言文件夹。

    例如，移动 agreement.rtf 文件**以英文**为︰  
    
    ```syntax
    C:\oobe\info\default\\**1033**\  
    ```

    移动 agreement.rtf 文件**以德语**为︰ 
    
    ```syntax
    C:\oobe\info\default\\**1031**\ 
    Copy C:\USB-B\resources\agreement.rtf c:\oobe\info\default\1033
    ```

1.  创建**oobe.xml**文件以指定的 agreement.rtf 文件的路径。 在以下图像中，您可以看到示例 oobe.xml 位于**USB B**\ConfigSet\oobe.xml 目标。

    ![OOBE 的示例](images/sample-oobe.png)

2.  将**oobe.xml 文件**复制到每个语言文件夹。

    例如，将 oobe.xml 复制到 C:\oobe\info\default\\**1033年**\ 其中英文 agreement.rtf 是有效和 C:\oobe\info\default\\**1031年**\ 其中德语 agreement.rtf 是有效的目录。

    ```syntax
    Copy C:\USB-B\configset\oobe.xml c:\oobe\info\default\1033
    ```

1.  最后，每个语言文件夹必须包含**oobe.xml**文件和 agreement.rtf 文件中的相应的语言。

    ![协议和 OOBE 文件](images/agreement-and-oobe-files.png)


### <a name="span-idmounttheimagespanmount-the-image"></a><span id="Mount_the_image"></span>装入该映像

使用步骤，可从[实验室 3︰ 添加设备驱动程序 （.inf 样式）](add-device-drivers.md)装载映像。 短的版本︰

1.  打开命令行以管理员身份 (**开始**> 键入**部署**> 右键单击**部署和图像处理工具环境** > **以管理员身份运行**。)

2.  对该文件进行备份 (`copy "C:\Images\Win10_x64\sources\install.wim" C:\Images\install-backup.wim`)

3.  装入该映像 (`md C:\mount\windows`，然后`Dism /Mount-Image /ImageFile:"C:\Images\install.wim" /Index:1 /MountDir:"C:\mount\windows" /Optimize`)

### <a name="span-idaddthelicense-filesspanadd-the-license-files"></a><span id="Add_the_license files"></span>添加许可证文件

1.  将答案文件复制到图像分解成\\Windows\\System32\\oobe\\文件夹。 如果它不存在，则创建该文件夹。

    ``` syntax
    MkDir c:\mount\windows\windows\system32\oobe
    xcopy C:\oobe \c:\mount\windows\windows\system32\oobe /s
    ```

## <a name="span-idunmounttheimagesspan-unmount-the-images"></a><span id="Unmount_the_images"></span>卸载映像

1.  关闭所有应用程序可能会访问从图像文件。

2.  提交更改并卸载 Windows 映像︰

    ``` syntax
    Dism /Unmount-Image /MountDir:"C:\mount\windows" /Commit
    ```

    其中*C*是驱动器的包含图像的驱动器号。

    此过程可能需要几分钟。

## <a name="span-idtryitoutspantry-it-out"></a><span id="Try_it_out"></span>试一下

**应用到新计算机的图像**使用步骤，可从[实验室 2︰ 使用脚本的部署 Windows](deploy-windows-with-a-script-sxs.md)将映像复制到 USB 驱动器的存储中，将 Windows 映像和恢复映像，应用和启动它。 短的版本︰

1.  将图像文件复制到的存储驱动器。
2.  [引导到 Windows PE 中使用 Windows PE usb 闪存盘的参考设备](install-windows-pe-sxs.md)。
3.  查找存储驱动器的驱动器号 (`diskpart, list volume, exit`)。
4.  将映像应用︰ `D:\ApplyImage.bat D:\Images\install.wim`。
5.  断开连接的驱动器，然后重新启动 (`exit`)。
    
**验证许可证条款**

好像一个新用户身份登录到系统。 选择您的语言或区域所需。 在此首次登录体验的过程中应显示正确的许可证条款。

下一步行动︰[实验室 9︰ 更改从 Windows （审核模式）](prepare-a-snapshot-of-the-pc-generalize-and-capture-windows-images-blue-sxs.md)