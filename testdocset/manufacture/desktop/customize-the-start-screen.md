---
author: Justinha
Description: "自定义开始屏幕"
ms.assetid: b28584ec-487e-4b59-a7f6-deb797d464a8
MSHAttr: PreferredLib:/library/windows/hardware
title: "自定义开始屏幕"
ms.openlocfilehash: 80032db4abf171bc31cf195207af2c3c0b9e524f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="customize-the-start-screen"></a>自定义开始屏幕


您可以添加您的业务应用程序与 Windows 映像，并自定义**开始**屏幕包含这些。 Windows 10 企业、 Windows 服务器 2016，或运行 Windows 10 专业人员加入域的计算机，可以自定义**开始**屏幕。

业务线 (LOB) Windows 应用商店应用程序无需安装 Windows 应用商店通过或认证。 添加不是从 Windows 应用商店应用程序被称为*sideloading*。 Sideloaded 应用程序必须链接到受信任的根证书的证书进行签名。 有关 sideloading 的 Windows 应用商店应用程序的详细信息，包括要求，请参阅[使用 DISM 的 Sideload 应用程序](sideload-apps-with-dism-s14.md)。

若要安装 Windows 应用商店应用程序不是业务线的一部分，您必须使用 Windows 应用商店。

**本主题︰**

[使用 CopyProfile 保留开始屏幕布局](#bkmk-copyprofile)

[若要设置默认的启动屏幕布局将 AppsFolderLayout.Bin 文件复制](#bkmk-appfolder)

[使用 StartTiles 设置来设置开始屏幕布局](#bkmk-starttiles)

## <a name="span-idbkmkcopyprofilespanspan-idbkmkcopyprofilespanspan-idbkmkcopyprofilespanuse-copyprofile-to-preserve-start-screen-layout"></a><span id="BKMK_CopyProfile"></span><span id="bkmk_copyprofile"></span><span id="BKMK_COPYPROFILE"></span>使用 CopyProfile 保留开始屏幕布局


CopyProfile 方法允许您从**开始**屏幕删除麻将牌、 添加平铺、 调整平铺和拼贴组的标签。 CopyProfile 还允许您自定义**启动**屏幕颜色、**启动**屏幕重音和桌面背景。

您可以添加提供应用程序软件包 (.appx) 和之前部署映像为 Windows 映像自定义**开始**屏幕。 添加到 Windows 映像的 Windows 应用程序被称为*配置*应用程序。 提供应用程序图像中转移，并计划为每个用户首次登录 Windows 映像的安装。

**请注意**  
如果使用无人参与的答案文件中的 CopyProfile 和 StartTiles 的设置，则 CopyProfile 将重写 StartTiles 设置。 若要在使用 CopyProfile 生成的图像上使用 StartTiles 的设置，请从图像中删除 appsFolderLayout.bin 文件。 有关此文件的详细信息，请参阅[复制的 AppsFolderLayout.Bin 文件来设置默认的启动屏幕布局](#bkmk-appfolder)。

 

**若要将应用程序可以将锁定添加到开始屏幕**

-   添加或从映像中删除应用程序。

    可以将脱机 Windows 映像安装并添加为业务线提供应用程序的包。 提供应用程序将为每个用户首次登录 Windows 映像的安装。 此外可以从 Windows 映像，包括收件箱的应用程序中删除已设置的应用程序的包。 使用 Get AppxProvisionedPackage cmdlet PowerShell 或部署映像服务和管理工具 (DISM.exe) 获取的图像中设置，然后选择您想要删除的应用程序的 Windows 应用商店应用程序列表。

    设置应用程序的详细信息，请参阅[使用 DISM 的 Sideload 应用程序](sideload-apps-with-dism-s14.md)。

    **请注意**  
    在部署该映像之前，请使用 Windows 应用商店。 如果您下载的应用程序或下载的图像中任何已设置的应用程序的应用程序更新，Sysprep 将失败。 有关详细信息，请参阅[删除或更新 Windows 8 内置 Windows 应用商店应用程序使 Sysprep 失败](http://go.microsoft.com/fwlink/?LinkId=271005)。

     

    有关安装的 Windows 映像的详细信息，请参阅[装载和修改 Windows 映像使用 DISM](mount-and-modify-a-windows-image-using-dism.md)。 有关 DISM cmdlet 的 PowerShell 的详细信息，请参阅[部署映像服务和管理 (DISM) 在 Windows PowerShell 的 Cmdlet](http://go.microsoft.com/fwlink/?LinkId=239926)。

**若要启用管理员帐户**

1.  将映像部署到一台测试计算机。

    将映像应用到一台测试计算机。 例如，在提升的命令提示符下，键入︰

    ``` syntax
    Dism /apply-image /imagefile:F:\install.wim /index:1 /ApplyDir:C:\
    ```

    应用映像的详细信息，请参阅[使用 DISM 应用图像](apply-images-using-dism.md)。

2.  创建一个测试帐户。

    完成的全新安装体验 (OOBE) 来设置新的用户配置文件。

3.  启用 sideloading。

    一旦创建新的用户配置文件，可以登录到该图像，如果您未启用的组策略设置为 sideloading。 有关详细信息，请参阅[使用 DISM 的 Sideload 应用程序](sideload-apps-with-dism-s14.md)。

4.  启用管理员帐户。

    您可以启用 Windows 映像中的管理员帐户。 例如︰

    1.  从**开始**屏幕中，键入计算机。 用鼠标右键单击搜索结果中的**计算机**，单击屏幕底部的应用程序栏中的**管理**。
    2.  在**计算机管理**窗口中，单击**系统工具** &gt; **本地用户和组** &gt; **用户** &gt; **管理员**。
    3.  在**管理员属性**窗口中，取消选择**帐户已停用**。

5.  设置 FilterAdministratorToken 注册表项。

    必须将 FilterAdministratorToken 注册表项设置以允许管理员帐户，以便运行 Windows 应用商店应用程序。 例如，在命令提示符处，键入︰

    ``` syntax
    cmd /c reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\system /v FilterAdministratorToken /t REG_DWORD /d 1 /f
    ```

6.  以管理员身份登录。

    从测试帐户，登录并以管理员身份登录。

现在您可以配置**启动**屏幕在您想要复制的每个新用户配置文件的管理员帐户。

### <a name="span-idstartscreenspanspan-idstartscreenspanspan-idstartscreenspanto-design-the-start-screen"></a><span id="StartScreen"></span><span id="startscreen"></span><span id="STARTSCREEN"></span>若要设计**启动**屏幕

为您的业务在很多方面，可以自定义开始屏幕。 可以为 LOB 应用程序中添加平铺、 删除麻将牌、 移动拼块组和组拼贴的标签。

1.  针的**启动**屏幕的应用程序。 从**开始**屏幕中，键入该应用程序的名称。 当应用程序出现在搜索结果视图中时，用鼠标右键单击该应用程序，然后单击**Pin 才能开始**。
2.  在**启动**屏幕上重新排序或分组将拼贴。
3.  单击**开始**菜单以语义缩放以查看**启动**屏幕右下角的放大镜图标。
4.  右键单击应用程序的组，然后选择**名称组**。
5.  在**开始**屏幕上指定应用程序的每个组的名称。

### <a name="span-idtosetcopyprofileinanunattendedanswerfilespanspan-idtosetcopyprofileinanunattendedanswerfilespanspan-idtosetcopyprofileinanunattendedanswerfilespanto-set-copyprofile-in-an-unattended-answer-file"></a><span id="To_set_CopyProfile_in_an_unattended_answer_file"></span><span id="to_set_copyprofile_in_an_unattended_answer_file"></span><span id="TO_SET_COPYPROFILE_IN_AN_UNATTENDED_ANSWER_FILE"></span>若要设置无人参与的答案文件中的 CopyProfile

无人参与的答案文件可用于保留的**启动**屏幕的设计布局。 在答案文件中，将 CopyProfile 设置添加到专业化阶段。

1.  创建或打开答案文件在 Windows 系统映像管理器 （Windows sim 卡）。 有关详细信息，请参阅[Windows 系统映像管理器技术参考](https://msdn.microsoft.com/library/windows/hardware/dn922445)。
2.  在**Windows 映像**窗格中，右键单击**amd64\_Microsoft Windows 外壳程序安装**或**x86\_Microsoft Windows 外壳程序安装**，然后选择**将设置添加到传递 4 专用化**。
3.  在 Windows SIM 中的**应答文件**窗格中，选择**组件\\4 擅长\\Microsoft Windows 外壳程序安装\_中性**。
4.  **属性的 Microsoft Windows 的外壳程序-安装**的窗格中，在**设置**部分中，设置**为** **CopyProfile** 。

在应答文件中设置 CopyProfile 的 XML 的示例︰

``` syntax
<settings pass="specialize">
   <component name="Microsoft-Windows-Shell-Setup" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
     <CopyProfile>true</CopyProfile>
   </component>
</settings>
```

此示例是使用 x86 计算机体系结构。

### <a name="span-idtogeneralizeanddeploytheimagespanspan-idtogeneralizeanddeploytheimagespanspan-idtogeneralizeanddeploytheimagespanto-generalize-and-deploy-the-image"></a><span id="To_generalize_and_deploy_the_image"></span><span id="to_generalize_and_deploy_the_image"></span><span id="TO_GENERALIZE_AND_DEPLOY_THE_IMAGE"></span>归纳和部署映像

您在部署之前，您可以清除图像。 此外必须对图像进行一般化之前可以将其部署到其他计算机。 如果您不做一般化映像时，该图像可能无法使用。

**请注意**  验证映像中的所有应用程序程序包资源调配。 在运行 sysprep 之前删除任何未设置的应用程序软件包。 例如，在 PowerShell，您可以移除不提供应用程序的所有软件包︰`Get-appxpackage | Remove-appxpackage`

 

当您使用 Sysprep 工具一般化图像时，从图像中删除特定于硬件的设置。 指定无人参与的答案文件来保留自定义的 CopyProfile 设置与您创建的屏幕**开始**布局。

**若要清除图像**

1.  删除该测试帐户。

    您可以删除用来启用管理员帐户，如果您不想将其包含在企业中部署 Windows 映像中的用户配置文件。 有关详细信息，请参阅[如何禁用和删除用户配置文件](http://go.microsoft.com/fwlink/?LinkId=272330)。

2.  重置注册表项。

    在部署该映像之前，应重置的 FilterAdministratorToken 注册表项。 例如，在命令提示符处，键入︰

    ``` syntax
    cmd /c reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\system /v FilterAdministratorToken /t REG_DWORD /d 0 /f
    ```

**以一般化映像**

-   在提升的命令提示符下，运行 Sysprep 并指定无人参与的答案文件的位置。 例如，键入︰

    ``` syntax
    %windir%\system32\Sysprep\Sysprep.exe /oobe /generalize /shutdown /unattend:f:\unattend.xml
    ```

您可以捕获使用 DISM 工具的通用的图像并将其部署到多台计算机。 有关详细信息，请参阅[DISM 的部署映像服务和管理技术参考的窗口](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md)。 应用映像时，必须以保留对**启动**屏幕的与 CopyProfile 设置为 true，使用自定义的 Unattend.xml 文件。

## <a name="span-idbkmkappfolderspanspan-idbkmkappfolderspanspan-idbkmkappfolderspancopy-the-appsfolderlayoutbin-file-to-set-default-start-screen-layout"></a><span id="BKMK_AppFolder"></span><span id="bkmk_appfolder"></span><span id="BKMK_APPFOLDER"></span>若要设置默认的启动屏幕布局将 AppsFolderLayout.Bin 文件复制


Windows 10 企业、 Windows 服务器 2016，或通过将自定义的 AppsFolderLayout.bin 文件复制到 Windows 映像中的默认用户配置文件运行 Windows 10 专业人员加入域的计算机，您可以自定义**开始**屏幕。 在此方法中，您将映像部署到测试计算机、 创建用户配置文件、 视觉设计的**开始**屏幕中，和返回到您的主映像复制该设计。 可以从**开始**屏幕中删除应用程序图块、 拼贴的 Windows 应用程序中添加、 调整拼贴，并标记拼贴组。

1.  在运行 Windows 10 企业 PC 的引用，Windows 服务器 2016 或运行 Windows 10 专业人员，加入域的计算机自定义**开始**屏幕。

2.  运行 Sysprep 工具来初始化系统清理。 例如，从命令提示符下键入︰

    ``` syntax
    %windir%\System32\Sysprep\sysprep.exe
    ```

    选择**输入系统审核模式**并**重新启动**，然后单击**确定**。

3.  将 AppsFolderLayout.bin 文件复制用户配置文件与自定义**启动**屏幕。 例如，若要复制**启动**屏幕的自定义项"TestProfile"到 USB 闪存驱动器，在命令提示符下，键入︰

    ``` syntax
    xcopy C:\Users\TestProfile\AppData\Local\Microsoft\Windows\AppsFolderLayout.bin F:\ /h
    ```

4.  您想要添加已装入或联机 Windows 映像中的**启动**屏幕定制，AppsFolderLayout.bin 文件复制到默认用户配置文件。 例如，在命令提示符处，键入︰

    ``` syntax
    xcopy F:\AppsFolderLayout.bin C:\Users\Default\AppData\Local\Microsoft\Windows
    ```

    有关装载服务脱机 Windows 映像的详细信息，请参阅[安装和修改 Windows 映像使用 DISM](mount-and-modify-a-windows-image-using-dism.md)。

**启动**屏幕自定义设置将应用于创建每个新用户配置文件。

如果您一般化映像时，AppsFolderLayout.bin 文件将被覆盖。 具有通用图像后，您必须添加该文件。

## <a name="span-idbkmkstarttilesspanspan-idbkmkstarttilesspanspan-idbkmkstarttilesspanuse-starttiles-settings-to-lay-out-the-start-screen"></a><span id="BKMK_StartTiles"></span><span id="bkmk_starttiles"></span><span id="BKMK_STARTTILES"></span>使用 StartTiles 设置来设置开始屏幕布局


可以使用无人参与的答案文件中的设置来指定应用程序的平铺在**启动**屏幕上的显示方式。 无法从**开始**屏幕中删除麻将牌或标签组使用无人参与的设置，但您可以指定拼贴 24 已安装的应用程序是如何使用的 StartTiles 设置显示。 每个设置映射为固定在**开始**屏幕模板位置，这些位置而异的目标 PC 的屏幕尺寸、 分辨率和 DPI。 每个设置指定图块是否宽的平铺或方形平铺视图的应用程序，或者如果它是一个桌面应用程序的正方形拼贴。

**请注意**  如果使用无人参与的答案文件中的 CopyProfile 和 StartTiles 的设置，则 CopyProfile 将重写 StartTiles 设置。

 

1.  获取应用程序标识的 LOB 应用程序。

    若要使用无人参与的设置，您需要与已安装的应用程序相关联的特定应用程序标识字符串。 可以通过在 Windows PowerShell 使用 get AppxPackage cmdlet 创建此字符串。 下面的示例演示如何获取应用程序标识字符串，要在无人参与设置用于每个已安装在计算机的应用程序︰

    ``` syntax
    $installedapps = get-AppxPackage
    foreach ($app in $installedapps)
    {
        foreach ($id in (Get-AppxPackageManifest $app).package.applications.application.id)
        {
            $app.packagefamilyname + "!" + $id
        }
    }
    ```

2.  打开答案文件。

    创建或打开答案文件在 Windows 系统映像管理器 （Windows sim 卡）。 有关详细信息，请参阅[Windows 系统映像管理器技术参考](https://msdn.microsoft.com/library/windows/hardware/dn922445)。

3.  将 StartTiles 设置添加到答案文件。

    使用 Microsoft Windows 的外壳程序-安装 |StartTiles |&lt;tileSetting&gt;设置，以指定的图块应出现在**启动**屏幕上的特定位置，默认情况下应用程序的应用程序标识。 图块的设置遵循三个命名的方式︰

    -   WideTile，一个从 01 06 到数字。

        指定这些设置的每个应用程序必须提供提供宽的平铺的资产，在应用程序清单中。 每个应用程序设置需要您输入应用程序标识。

    -   SquareTile，从 01 至 12 的数字。

        每个应用程序设置需要您输入应用程序标识。

    -   DesktopOrSquareTile，一个从 01 06 到数字。

        用于在任何或所有的 DesktopOrSquare 设置的应用程序，您需要指定应用程序标识对应的应用程序，或桌面应用程序的路径。

    **请注意** 如果将应用程序在一个正方形拼贴点支持宽的拼贴，被迫是正方形拼而不是范围。

     

    如果您跳过设置，Windows 可以重新排列应用程序图块在**启动**屏幕上设置的应用程序图块位置的流动。

4.  部署 Windows 映像使用修改过的答案文件。

    有关详细信息，请参阅[部署自定义映像](deploy-a-custom-image.md)。

有关这些设置的详细信息，请参阅 TechNet 上的 Microsoft Windows 外壳程序安装在[Windows 无人参与安装参考](http://go.microsoft.com/fwlink/?LinkId=206281)组件中的 StartTiles 设置主题。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[使用 DISM 的 sideload 应用程序](sideload-apps-with-dism-s14.md)

[装载和修改 Windows 映像使用 DISM](mount-and-modify-a-windows-image-using-dism.md)

[通过使用 CopyProfile 自定义默认用户配置文件](customize-the-default-user-profile-by-using-copyprofile.md)

[图像处理服务管理 (DISM) 在 Windows PowerShell 的 Cmdlet 的部署](http://go.microsoft.com/fwlink/?LinkId=239926)

 

 






