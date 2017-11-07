---
author: kpacquer
Description: "OEM 和企业客户可以利用一套脚本和工具来提供应用程序更新 Windows 10 IoT 核心 （IoT 核心） 设备。"
ms.assetid: 010c4836-a8ad-4ab9-b5a8-45babcc8a3f3
MSHAttr: PreferredLib:/library/windows/hardware
title: "更新 IoT 核心设备上的应用程序"
ms.openlocfilehash: 92348a061555f21b1c4d35f1723a28bc42972b4e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="update-apps-on-your-iot-core-devices"></a>更新 IoT 核心设备上的应用程序

**新的 Windows 10、 版本 1607年**: Oem 和企业客户可以提供应用程序更新到 Windows 10 IoT 核心设备通过提交到 Windows 应用商店的更新。 如果您的设备连接到互联网，他们定期从 Windows 应用商店，检查更新并自动安装更新。 

将更新发送到存储区之前，我们建议先在自己的设备上进行测试。 

## <a name="span-idsendupdatestothewindowsstorespansend-updates-to-the-windows-store"></a><span id="Send_updates_to_the_Windows_Store"></span>将更新发送到 Windows 应用商店

创建更新您的应用程序中创建的原始应用程序的方式相同。

每次使用更高的版本号。 (示例中，为 1.0.0.0--> 1.0.1.0。)

它是确定重新使用现有的软件包名称，甚至覆盖旧的文件夹名称和位置。 备份您的文件第一次，以防您想要以后恢复更改。

我们建议您[测试和跟踪更新](#Test_and_track_the_update)使用本主题中的过程。

最后，签名，并提交到 Windows 应用商店应用程序软件包。 

若要了解详细信息，请参阅[安装和维护应用程序在 Windows 10 IoT 核心](https://developer.microsoft.com/en-us/windows/iot/docs/store)

## <a name="span-idtestandtracktheupdatespanspan-idtest-and-track-the-updatespanspan-idtest-and-track-the-upatespantest-and-track-the-update-recommended"></a><span id="Test_and_track_the_update"></span><span id="test and track the update"></span><span id="TEST AND TRACK THE UPATE"></span>测试和跟踪更新 （推荐）

您在您的设备上的更新尝试之前将它们提交到 Windows 应用商店。

### <a name="span-idcreateanupdatepackagespancreate-an-update-package"></a><span id="Create_an_update_package"></span>创建更新程序包

1.  创建更新程序包的工作文件夹。 

    使用新的版本号。 此版本号将适用于所有在项目中的文件包。

    ``` syntax
    newupdate Update1 10.0.0.1
    ```

2.  使用更改更新该应用程序。

3.  生成应用程序使用新的版本号。 
    
4.  更新程序包的信息︰

    - 创建一份现有的包 (例如，Appx.HelloWorld) 在 Update1\ 文件夹下，然后更新的版本号。
    
    - 新的 appx 文件复制到该目录。
    
    - 打开 c:\\iot-adk-addonkit\\源臂\\软件包\\Appx.HelloWorld\\Appx.HelloWorld.pkg.xml 和更新的版本编号。
        
5.  生成更新包

    ``` syntax
    createupdatepkgs Update1
    ```

    输出将显示 c:\\iot-adk-addonkit\\生成\\arm\\Update1。

### <a name="span-idapplytheupdatedirectlytothedevicespanspan-idapplytheupdatedirectlytothedevicespanspan-idapplytheupdatedirectlytothedevicespanapply-the-update-directly-to-the-device"></a><span id="Apply_the_update_directly_to_the_device"></span><span id="apply_the_update_directly_to_the_device"></span><span id="APPLY_THE_UPDATE_DIRECTLY_TO_THE_DEVICE"></span>此更新将直接应用于该设备

1.  向移动设备复制.cab 文件。 您可以执行此过程通过 FTP 工具如[WinSCP](http://winscp.net)，或通过将文件复制到设备的驱动器 （如微 SD 卡） 直接。

2.  在技术人员计算机，连接到您的设备使用 SSH 客户端，如[PuTTY](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe)。 例如，使用 IP 地址和端口 22 以连接到该设备，然后使用管理员帐户和密码登录。 （若要了解详细信息，请参阅[使用 SSH 连接并配置运行 Windows IoT 核心设备](https://developer.microsoft.com/windows/iot/docs/ssh)。

3.  从设备命令行阶段更新。 您可以重复此步骤以阶段化安装多个更新。
    ``` syntax
    ApplyUpdate.exe -stage <DownloadedPackageName.cab>
    ```

4.  提交更改。 此命令还会触发 Windows 更新过程中，安装所有适用的更新。 
    ``` syntax
    ApplyUpdate.exe -commit
    ```
    
    (若要拒绝所有的更新，请使用︰`ApplyUpdate.exe -clear`相反。)
    
    故障排除︰
    -  **错误︰ 证书链不能建立到受信任的根颁发机构。(0x800B010A)。 签名验证失败。** 可能的原因︰ 添加测试签名图像到零售映像。 签名图像，然后再试。
       
    -  **错误︰ 0x80188302。**
       可能的原因︰ 软件包版本不正确。 请确保新的版本号将高于旧版本，然后重试。 
    
    -  **错误︰ 无法启动更新 (0x8024A10F)**可能的原因︰ Windows 更新正在进行中。 新的 Windows 更新完成后重试。
       

### <a name="span-idkeeptrackofversionsspankeep-track-of-versions"></a><span id="Keep_track_of_versions"></span>跟踪的版本

打开`UpdateVersion.txt`来查看您的软件包的说明。 创建一个新的更新时，createupdatepkgs 工具更新此文件。

### <a name="span-idtestnewimagesspantest-new-images"></a><span id="Test_new_images"></span>测试新的图像
创建新的程序包使用相同的过程，如中所示[实验室 1b︰ 将应用程序添加到映像](../../manufacture/iot/deploy-your-app-with-a-standard-board.md)。
