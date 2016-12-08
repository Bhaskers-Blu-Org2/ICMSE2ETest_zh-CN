---
author: Justinha
Description: "使用 DISM 的预安装应用程序"
ms.assetid: 707607d6-eb3a-4a5b-b52d-4d465d82f69d
MSHAttr: PreferredLib:/library/windows/hardware
title: "使用 DISM 的预安装应用程序"
ms.openlocfilehash: d041efad416d618a1cc9c24cdfa02cf5e6fe4892
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="preinstall-apps-using-dism"></a>使用 DISM 的预安装应用程序


预安装 Windows 应用商店应用程序时，是否有兴趣，但不是 OEM 呢？ 有关组织的 sideloading 应用程序的信息，请参阅[使用 DISM 的 Sideload 应用程序](sideload-apps-with-dism-s14.md)。

预安装 Windows 应用商店应用程序在您的图像中，您将需要使用 Windows 评估和部署工具包 (Windows ADK)。 此部分说明了在预安装应用程序，作为映像的一部分所涉及的步骤。

## <a name="span-idbkmkworkwithapppackagesspanspan-idbkmkworkwithapppackagesspanspan-idbkmkworkwithapppackagesspanwork-with-app-packages"></a><span id="BKMK_WorkWithAppPackages"></span><span id="bkmk_workwithapppackages"></span><span id="BKMK_WORKWITHAPPPACKAGES"></span>使用应用程序程序包


对于脱机配置应用程序到图像，可用于 Dism.exe 工具或 DISM cmdlet 在 Windows PowerShell 解包文件的文件夹中添加一个应用程序。

**若要解压缩程序包文件**

1.  浏览到保存从合作伙伴仪表板应用程序程序包的文件夹。
2.  用鼠标右键单击每个.zip 文件夹包含您的应用程序的包文件。 单击**全部提取**，并选择一个位置来保存包文件的文件夹。

    文件夹中包含的包，其中包括主程序包、 任何依赖的包和许可证文件解包文件的所有。

**重要**  一旦提取程序包文件，则不修改文件夹。 如果您更改、 添加或删除文件夹中的所有文件，该应用程序将失败或者在安装过程中或启动。 即使浏览该文件夹可能会导致问题。

 

您需要使用从包文件的许可证文件测试配置的映像。 创建您自己的自定义数据文件将不允许您准确地测试由 OEM 预安装的应用程序。

对于脱机配置应用程序到图像，可用于 Dism.exe 工具或 DISM cmdlet 在 Windows PowerShell 解包文件的文件夹中添加一个应用程序。

**预存储签名的应用程序安装使用 Dism.exe 工具**

1.  打开部署工具命令提示符下安装有 Windows ADK，具有管理员特权。 从开始屏幕中，键入**部署和图像处理工具环境**，用鼠标右键单击该图标，并选择**以管理员身份运行**。
2.  装载脱机映像以便进行处理。 在命令提示符下，键入︰

    ``` syntax
    Dism /Mount-Image /ImageFile:c:\images\myimage.wim /Index:1 /mountdir:c:\test\offline
    ```

3.  将应用程序添加到已装载的映像。 使用 /PackagePath 选项和 /DependencyPackagePath 选项来指定包含所有解包的文件和从存储包的依赖项文件的文件夹的位置。 / PackagePath 应指定提取文件夹的根文件夹。 根文件夹包含 license.xml、 AUMIDs.txt，和所有的包文件。 在命令提示符下，键入︰

    ``` syntax
    Dism /Image:c:\test\offline /Add-ProvisionedAppxPackage /PackagePath:c:\downloads\appxpackage /DependencyPackagePath:c:\downloads\appxpackagedependency
    ```

4.  保存更改并卸载映像。 在命令提示符下，键入︰

    ``` syntax
    Dism /Unmount-Image /mountdir:c:\test\offline /commit
    ```

**预安装存储签名的应用程序，使用 Windows PowerShell**

1.  使用管理员权限打开 Windows PowerShell。 您必须运行 Windows 10 或 Windows 8.1 宿主 PC 上安装的 Windows PowerShell 支持的版本。 有关详细信息，请参阅[如何使用 DISM 中 Windows PowerShell](http://go.microsoft.com/fwlink/p/?linkid=239927)。
2.  将映像装载。 在 Windows PowerShell 提示符下，键入︰

    ``` syntax
    Mount-WindowsImage -ImagePath c:\images\myimage.wim -Index 1 -Path c:\test\offline
    ```

3.  使用在 Windows PowerShell 添加 AppxProvisionedPackage cmdlet 来预安装应用程序。 使用 /PackagePath 选项和 /DependencyPackagePath 选项来指定包含所有解包的文件和从存储包的依赖项文件的文件夹的位置。 在 Windows PowerShell，请键入︰

    ``` syntax
    Add-AppxProvisionedPackage -Path c:\test\offline -FolderPath c:\downloads\appxpackage -DependencyPackagePath c:\downloads\appxpackagedependency
    ```

4.  保存更改并卸载映像。 在 Windows PowerShell 提示符下，键入︰

    ``` syntax
    Dismount-WindowsImage -Path c:\test\offline -Save
    ```

**请注意**  在审核模式下，请不要运行 Windows 应用商店应用程序。 若要测试您的部署，运行 Windows 和创建新的用户配置文件。 有关审核模式的详细信息，请参阅 TechNet 库，[了解审核模式](http://go.microsoft.com/fwlink/p/?LinkId=311789)。

 

**重要**  如果移动宽带设备应用程序预安装，必须在运行 Sysprep 的专业化阶段之前 PC 插入 SIM 卡。 有关移动宽带设备应用程序预安装的详细信息，请参阅[预安装必需的组件，为用户提供移动宽带应用程序体验](#bkmk-broadband-intro)。

 

## <a name="span-idbkmkupdateorremovepackagesspanspan-idbkmkupdateorremovepackagesspanspan-idbkmkupdateorremovepackagesspanupdate-or-remove-packages"></a><span id="BKMK_UpdateOrRemovePackages"></span><span id="bkmk_updateorremovepackages"></span><span id="BKMK_UPDATEORREMOVEPACKAGES"></span>更新或删除程序包


您可以删除预安装的应用程序，包括许可和自定义数据文件，从使用中 Windows PowerShell DISM.exe 工具或 DISM cmdlet 的 Windows 映像。 应该安装一个新之前删除旧版本的应用程序。

**若要使用 Dism.exe 工具删除预安装应用程序**

1.  打开部署工具命令提示符下安装有 Windows ADK，具有管理员特权。 从开始屏幕中，键入**部署和图像处理工具环境**，用鼠标右键单击该图标，并选择**以管理员身份运行**。
2.  装载脱机映像以便进行处理。 在命令提示符下，键入︰

    ``` syntax
    Dism /Mount-Image /ImageFile:c:\images\myimage.wim /Index:1 /mountdir:c:\test\offline
    ```

3.  找到您想要删除的应用程序的完整的包名称。 在命令提示符下，键入︰

    ``` syntax
    Dism /Image:C:\test\offline /Get-ProvisionedAppxPackages
    ```

4.  从已装载的映像中删除该应用程序。 例如，在命令提示符下，键入︰

    ``` syntax
    Dism /Image:c:\test\offline /Remove-ProvisionedAppxPackage /PackageName:microsoft.devx.appx.app1_1.0.0.0_neutral_en-us_ac4zc6fex2zjp
    ```

    **请注意**  如果应用程序没有注册到图像中的用户配置文件 — 例如，如果图像通用并没有部署 — — 它从图像中删除。 如果 Windows 映像已启动，并且已创建的用户配置文件，配置应用程序为该用户注册，必须通过使用删除 AppxPackage cmdlet，您删除应用程序资源调配后删除。

     

5.  如果您想要更新应用程序，您可以预安装存储签名应用程序的更新的版本。 在命令提示符处，键入︰

    ``` syntax
    Dism /Image:c:\test\offline /Add-ProvisionedAppxPackage/FolderPath:c:\downloads\appxpackage
    ```

6.  保存更改并卸载映像。 在命令提示符下，键入︰

    ``` syntax
    Dism /Unmount-Image /mountdir:c:\test\offline /commit
    ```

**若要使用 Windows PowerShell 删除已设置的应用程序**

1.  使用管理员权限打开 Windows PowerShell。 您必须运行 Windows 10 或 Windows 主机 PC 上的 8.x 或安装 Windows PowerShell 的受支持的版本。 有关详细信息，请参阅[如何使用 DISM 中 Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=239927)。
2.  将映像装载。 在 Windows PowerShell 提示符下，键入︰

    ``` syntax
    Mount-WindowsImage -ImagePath c:\images\myimage.wim -Index 1 -Path c:\test\offline
    ```

3.  找到您想要删除的应用程序的完整的包名称。 在 Windows PowerShell 提示符下，键入︰

    ``` syntax
    Get-AppxProvisionedPackage -Path c:\test\offline
    ```

4.  使用 Windows PowerShell 中添加 AppxProvisionedPackage cmdlet 删除该应用程序。 在 Windows PowerShell，请键入︰

    ``` syntax
    Remove-AppxProvisionedPackage -Path c:\test\offline -PackageName microsoft.devx.appx.app1_1.0.0.0_neutral_en-us_ac4zc6fex2zjp 
    ```

**请注意** 如果应用程序没有注册到图像中的用户配置文件 — 例如，如果图像通用并没有部署 — — 它从图像中删除。 如果 Windows 映像已启动，并且已创建的用户配置文件，配置应用程序为该用户注册，必须通过使用删除 AppxPackage cmdlet，您删除应用程序资源调配后删除。

 

1.  如果您想要更新应用程序，您可以预安装存储签名应用程序的更新的版本。 在 Windows PowerShell 提示符下，键入︰

    ``` syntax
    Add- AppxProvisionedPackage -Path c:\test\offline -FolderPath c:\downloads\appxpackage
    ```

2.  保存更改并卸载映像。 在 Windows PowerShell 提示符下，键入︰

    ``` syntax
    Dismount-WindowsImage -Path c:\test\offline -Save
    ```

## <a name="span-idbkmkusecustomdatefilesspanspan-idbkmkusecustomdatefilesspanspan-idbkmkusecustomdatefilesspanuse-custom-data-files"></a><span id="BKMK_UseCustomDateFiles"></span><span id="bkmk_usecustomdatefiles"></span><span id="BKMK_USECUSTOMDATEFILES"></span>使用自定义数据文件


在一台电脑预装的应用程序可以访问安装特定的自定义数据。 此自定义数据在预安装过程中添加到应用程序，并在运行时可用。 自定义数据使开发人员能够自定义应用程序的特性和功能，其中包括提供报告功能。

### <a name="span-idbkmkaddcustomdatafilespanspan-idbkmkaddcustomdatafilespanspan-idbkmkaddcustomdatafilespanadd-a-custom-data-file-to-a-windows-image"></a><span id="BKMK_AddCustomDataFile"></span><span id="bkmk_addcustomdatafile"></span><span id="BKMK_ADDCUSTOMDATAFILE"></span>向 Windows 映像中添加自定义数据文件

通过使用 DISM 工具并通过使用**添加 AppxProvisionedPackage** cmdlet 的 Windows PowerShell 预安装应用程序时，必须指定自定义数据文件。 下面的命令演示了如何使用 DISM 工具︰

``` syntax
Dism /Image:C:\test\offline /Add-ProvisionedAppxPackage / FolderPath:f:\Apps\Fabrikam_KnowMyPC /CustomDataPath:f:\Contoso_Promotion.xml
```

自定义数据文件是否已经存在一个应用程序的数据存储区中 — — 例如，如果已添加到映像包 — — 将覆盖现有的文件。 如果安装失败，不会还原该文件。

**请注意**  
而不会丢失自定义数据文件，您可以发布到存储应用程序的更新。 但是，如果用户删除该应用程序，自定义数据文件不再可用，即使用户重新安装应用程序。

 

### <a name="span-idbkmktestcustomdatafilespanspan-idbkmktestcustomdatafilespanspan-idbkmktestcustomdatafilespantest-custom-data-for-preinstalled-apps"></a><span id="BKMK_TestCustomDataFile"></span><span id="bkmk_testcustomdatafile"></span><span id="BKMK_TESTCUSTOMDATAFILE"></span>预安装应用程序的测试自定义数据

在一台电脑预装的应用程序可以访问安装特定的自定义数据。 此自定义数据在预安装过程中添加到应用程序，该应用程序在运行时可用。 自定义数据使开发人员能够自定义应用程序的特性和功能，其中包括提供报告功能。

Custom.data 文件将出现在应用程序的安装位置。 该名称 Custom.data 是硬编码，并且不能修改。 您的应用程序可以检查存在此文件，以确定是否在电脑上预装应用程序。 这里是如何访问 Custom.data 文件的一个示例。

``` syntax
var outputDiv = document.getElementById("CustomData");
Windows.ApplicationModel.Package.current.installedLocation.getFileAsync
     ("microsoft.system.package.metadata\\Custom.data").then(function (file) {
         // Read the file
         Windows.Storage.FileIO.readTextAsync(file).done(function (fileContent) {
            outputDiv.innerHTML = 
                 "App is preinstalled. CustomData contains:<br /><br />"
                 + fileContent;
         },
         function (error) {
             outputDiv.innerText = "Error reading CustomData " + error;
         });
     },
     function (error) {
         outputDiv.innerText = "CustomData was not available. App not preinstalled";
     });
```

您的 Custom.data 文件可以包含任何内容，并是您的应用程序需要的任何格式。 在预安装过程只是使其可用于您的应用程序。 开发人员可以提供数据文件到预安装的伙伴，或者您可以同意使合作伙伴要生成的内容的格式。

### <a name="span-idtestyourcustomdataspanspan-idtestyourcustomdataspanspan-idtestyourcustomdataspantest-your-custom-data"></a><span id="Test_your_custom_data"></span><span id="test_your_custom_data"></span><span id="TEST_YOUR_CUSTOM_DATA"></span>测试自定义数据

当您正在生成和调试您的应用程序在 Microsoft Visual Studio 中时，不能从应用程序的安装位置访问 Custom.data 文件，因为应用程序不预先安装尚未。 您可以通过将测试 Custom.data 文件放入应用程序自身，然后加载和测试应用程序的本地文件，使用 Custom.data 文件来模拟。 为此，修改中的代码示例︰

``` syntax
("microsoft.system.package.metadata\\Custom.data").then(function (file) {
```

自：

``` syntax
("Custom.data").then(function (file) {
```

验证您的文件格式和内容后，可以如原始上面的示例中所示到最终位置，更改 Custom.data 文件的位置。

**若要测试您的 Custom.data 文件**

1.  打开部署工具命令提示符下安装有 Windows ADK，具有管理员特权。 从开始屏幕中，键入**部署和图像处理工具环境**，用鼠标右键单击该图标，并选择**以管理员身份运行**。
2.  将应用程序添加自定义数据文件︰

    ``` syntax
    dism /online /Add-ProvisionedAppxPackage /PackagePath:.\CustomData_1.0.0.1_AnyCPU_Debug.appx /CustomDataPath:.\Test.txt /SkipLicense
    ```

    其中`/PackagePath:.\CustomData_1.0.0.1_AnyCPU_Debug.appx`指向您本地应用程序的测试包，以及在何处`/CustomDataPath:.\Test.txt`指向您的 Custom.data 文件。 请注意，此处提供的文件名不会继续使用后数据安装在您的应用程序。

    App 现在 PC 用于测试应用程序的**启动**屏幕上有一张牌。 应用程序应该能够访问 Custom.data 文件。 如果需要附加的调试，应用程序从**启动**屏幕后附加一个调试程序。

    **请注意**  您可能需要注销并重新登录以查看该应用程序在**启动**屏幕上。

     

3.  在完成后测试您的应用程序，您必须删除预安装的软件包，以继续使用您的开发环境。 若要删除使用 Windows PowerShell 的预安装的包，可以使用**Get AppxPackage** cmdlet 以提供完整的应用程序软件包名称为**删除 ProvisionedAppxPackage** cmdlet 的管道通过︰

    `Get-AppxPackage *CustomData* | Remove-ProvisionedAppxPackage`

    其中`*CustomData*`属于已知的应用程序的名称

## <a name="span-idbkmkbroadbandintrospanspan-idbkmkbroadbandintrospanspan-idbkmkbroadbandintrospanpreinstall-a-windows-store-device-app-or-mobile-broadband-app"></a><span id="BKMK_broadband_intro"></span><span id="bkmk_broadband_intro"></span><span id="BKMK_BROADBAND_INTRO"></span>预安装 Windows 应用商店设备应用程序或移动宽带应用程序


您可以预安装 Windows 应用商店设备应用程序或使用部署映像服务和管理 (DISM) 平台移动宽带应用程序所需的组件。

**请注意**  本文旨在为 Oem，将支持 Windows 应用商店设备应用程序或移动宽带应用程序在其设备。

 

对于每种类型的应用程序，两件事情应预先提供正确的 Windows 应用商店设备应用程序或移动宽带应用程序︰

-   Windows 应用商店设备应用程序，预安装︰
    1.  设备元数据包
    2.  该应用程序
-   Windows 应用商店移动宽带应用程序，预安装︰
    1.  服务元数据包
    2.  该应用程序

**重要**  虽然在 OOBE 过程完成后立即分析元数据的软件包和相应的应用程序，用户可能无法启动应用程序之前的元数据包进行分析。 在这种情况下，用户将看到拒绝访问错误。 若要避免此问题，应用于系统映像的元数据软件包和应用程序。

 

## <a name="span-idpreinstallthedevicemetadataorservicemetadatapackagespanspan-idpreinstallthedevicemetadataorservicemetadatapackagespanspan-idpreinstallthedevicemetadataorservicemetadatapackagespanpreinstall-the-device-metadata-or-service-metadata-package"></a><span id="Preinstall_the_device_metadata_or_service_metadata_package"></span><span id="preinstall_the_device_metadata_or_service_metadata_package"></span><span id="PREINSTALL_THE_DEVICE_METADATA_OR_SERVICE_METADATA_PACKAGE"></span>预安装设备元数据或服务元数据包


**预安装设备元数据或服务元数据包**

1.  如果预安装 Windows 应用商店设备应用程序然后您应购买设备元数据封装。 如果预安装移动宽带应用程序然后您应购买的服务元数据包。

    **请注意**  设备元数据软件包和服务元数据包使用相同文件扩展名 （.devicemetadata 毫秒）。

     

2.  将设备元数据或服务元数据包 （devicemetadata ms 文件） 复制到您的系统映像中**%programdata%\\Microsoft\\Windows\\DeviceMetadataStore**文件夹。 你可以通过以下方法之一︰

    -   在运行 Sysprep 之前在线
    -   通过使用 DISM 运行 Sysprep 后离线。 若要此操作︰

        1.  装载脱机映像以便进行处理。

            ``` syntax
            Dism /Mount-Image /ImageFile:C:\test\images\myimage.wim /index:1 /MountDir:C:\test\offline
            ```

        2.  将元数据包文件复制到已装载的映像的设备元数据存储区。 例如，若要将**0ECF2029-2C6A-41AE-9E0A-63FFC9EAD877.devicemetadata-ms**的元数据包文件复制到设备元数据存储区， **ProgramData\\Microsoft\\Windows\\DeviceMetadataStore**:

            ``` syntax
            copy 0ECF2029-2C6A-41AE-9E0A-63FFC9EAD877.devicemetadata-ms C:\test\offline\ProgramData\Microsoft\Windows\DeviceMetadataStore
            ```

        3.  保存更改并卸载映像。

            ``` syntax
            dism /Unmount-Image /mountdir: c:\test\offline /commit
            ```

        有关脱机映像服务的详细信息，请参阅[DISM 概述](http://technet.microsoft.com/library/hh825236.aspx)。

关于服务元数据的详细信息，请参阅[服务元数据](http://go.microsoft.com/fwlink/p/?LinkId=698640)。

## <a name="span-idpreinstallthewindowsstoredeviceappormobilebroadbandappspanspan-idpreinstallthewindowsstoredeviceappormobilebroadbandappspanspan-idpreinstallthewindowsstoredeviceappormobilebroadbandappspanpreinstall-the-windows-store-device-app-or-mobile-broadband-app"></a><span id="Preinstall_the_Windows_Store_device_app_or_mobile_broadband_app"></span><span id="preinstall_the_windows_store_device_app_or_mobile_broadband_app"></span><span id="PREINSTALL_THE_WINDOWS_STORE_DEVICE_APP_OR_MOBILE_BROADBAND_APP"></span>预安装的 Windows 应用商店设备应用程序或移动宽带应用程序


**预安装的 Windows 应用商店设备应用程序或移动宽带应用程序**

1.  装载脱机映像以便进行处理。

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\myimage.wim /index:1 /MountDir:C:\test\offline
    ```

2.  Windows 应用商店设备应用程序的移动宽带应用程序添加到映像。

    ``` syntax
    dism /Image:<mounted folder> /Add-ProvisionedAppxPackage /FolderPath:<appxpackage path>
    ```

3.  保存更改并卸载映像。

    ``` syntax
    dism /Unmount-Image /mountdir: c:\test\offline /commit
    ```

 

 





