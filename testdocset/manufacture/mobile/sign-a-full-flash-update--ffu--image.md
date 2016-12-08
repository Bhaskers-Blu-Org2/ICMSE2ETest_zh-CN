---
title: "签名的完整闪存更新 (FFU) 图像"
description: "可以将它部署到一个设备之前，必须加密签名 FFU 图像。 此步骤是必需以防止篡改和恶意攻击。 正确签名之后，才可以闪烁到 10 Windows Mobile 设备的图像。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 94761827-8c91-4477-9483-c61095151f90
ms.openlocfilehash: 0c5134f11b4af2859557d38bc92ca0f6a027f33c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="sign-a-full-flash-update-ffu-image"></a>签名的完整闪存更新 (FFU) 图像


可以将它部署到一个设备之前，必须加密签名 FFU 图像。 此步骤是必需以防止篡改和恶意攻击。 正确签名之后，才可以闪烁到 10 Windows Mobile 设备的图像。

OEM 必须签署 FFU 图像使用证书链到 UEFI PK 启动键，OEM 规定。

在开发和测试，测试证书用于签名 FFU 图像而不是零售证书。 使用安全启动测试工具调配到设备的适当测试证书

对于零售电话零售证书调配使用零售安全启动工具设备。

## <a name="test-signing-images-using-windows-imaging-and-configuration-designer-icd"></a>测试签名图像使用 Windows 图像处理和配置设计器 (ICD)


使用安全启动测试工具来提供一部电话到适当的测试证书后，您可以使用 Windows 图像处理和配置设计器 (ICD) 来生成测试签名图像。 ICD Windows 自动将签名图像使用正确的测试证书。 这是推荐的过程，因为它是最简单的方法来准备正确签名的图像。 有关详细信息，请参阅[Windows ICD](https://msdn.microsoft.com/library/windows/hardware/dn916113)。

## <a name="retail-signing-ffu-images"></a>零售签名 FFU 图像


图像可以装运的零售设备之前，他们必须通过 Microsoft 签名。 使用来创建零售本部分中介绍的过程签名 FFU 映像文件可以刷新为零售设备。

1.  可以对二进制文件进行签名之前，首先必须通过[设置签名的环境](https://msdn.microsoft.com/library/windows/hardware/dn789236)中的步骤的电脑上安装 OEM 测试证书。

2.  将该目录位于 %WPDKCONTENTROOT%的 sign.cmd 脚本添加\\工具\\bin\\i386 到路径中使用 path 命令。

    ``` syntax
    C:\> PATH = %PATH%;%WPDKCONTENTROOT%\Tools\bin\I386
    ```

3.  打开具有管理员权限的目录中包含的输出图像生成过程的开发人员的提示。

4.  确认您具有最新版本的工具包，可以通过键入以下命令，包括 imagesigner.exe 和 imagecommon.dll 的更新的版本。 确认显示的截断选项。

    ``` syntax
    C:\> ImageSigner /?
    Usage:
            imagsigner sign <FFU> <catalog file>
            imagesigner getcatalog <FFU> <catalog file>
            imagesigner truncate <FFU> <truncated FFU>
    ```

    如果您没有最新版本的工具包，其中包括更新的 ImageSigner，下载并安装最新的工具包。

5.  提取 FFU 映像，其中包含 FFU 目录和相关的元数据使用截断选项第 1 MB。

    ``` syntax
    C:\> ImageSigner TRUNCATE OEM.ffu OEM.trunc
    ```

6.  从第 5 步中的截断 FFU 图像中提取目录。

    ``` syntax
    C:\> ImageSigner GETCATALOG OEM.trunc OEM.cat
    Platform ID: <OEMID>.QC8960.P728
    Successfully extracted catalog.
    C:\>
    ```

7.  验证&lt;OEMID&gt;返回第 6 步中与 OEMID 分配给您的 Microsoft。 

8.  创建和提交到 Microsoft 服务台 FFU 目录进行签名的 TFS 票证。  请确保您将在步骤 4 中创建的截断的 FFU 图像。

    1.  打开*更新*类型票证。

    2.  对于票证标题，输入*FFU 编录签名请求从&lt;OEMID&gt;*。 票图块中指定您的 OEM 标识其中&lt;OEMID&gt;显示。

    3.  将**类别**设置为*接收和发布*。

    4.  设置为*新*的**问题类型**。

9.  Microsoft 将处理该请求，解决票据回 OEM。  解析的票证中，Microsoft 将包括零售已签名的版本 FFU 目录从附加到原始票据 FFU 截断图像中提取。 对于此示例，假定，Microsoft 将返回名为 OEM.cat 的签名的 FFU 目录。

10. 符号与零售 Microsoft FFU 签名的目录文件使用 ImageSigner。

    ``` syntax
    C:\> ImageSigner SIGN OEM.ffu OEM.cat
    ```

11. 闪存设备到零售签名的零售映像并验证其行为与预期相同。

    ``` syntax
    C:\> FFUTool -flash OEM.ffu
    ```

12. 后经已签名的映像零售它可以用于零售设备闪存。 详细信息请参阅[闪烁工具](flashing-tools.md)，并[使用由 Microsoft 提供的闪烁的工具](use-the-flashing-tools-provided-by-microsoft.md)。

**重要**  
安全的零售所有签名的二进制文件使用业界最佳做法。

 

## <a name="test-signing-images-manually"></a>手动测试签名图像


如果您的开发环境包含 Windows ICD 之外的工作，您可以手动登录使用 sign.cmd 的图像。 测试证书上使用安全启动测试工具的设备已设置后，您可以您可以使用 sign.cmd 工具的 /pk 选项进行签名的图像，通过完成以下步骤。

1.  可以对二进制文件进行签名之前，首先必须通过[设置签名的环境](https://msdn.microsoft.com/library/windows/hardware/dn789236)中的步骤的电脑上安装 OEM 测试证书。

2.  将该目录位于 %WPDKCONTENTROOT%的 sign.cmd 脚本添加\\工具\\bin\\i386 到路径中使用 path 命令。

    ``` syntax
    C:\> PATH = %PATH%;%WPDKCONTENTROOT%\Tools\bin\I386
    ```

3.  打开具有管理员权限的目录中包含的输出图像生成过程的开发人员的提示。

4.  提取签字 FFU 文件的目录。

    ``` syntax
    C:\> ImageSigner GETCATALOG TestSigned.FFU TestSigned.Cat
    ```

5.  签名使用 /pk 选项的目录。

    ``` syntax
    C:\> Set SIGN_OEM=1
    C:\> Sign.cmd /pk TestSigned.cat
    ```

6.  对 FFU 签名与签名的编录文件使用 ImageSigner。

    ``` syntax
    C:\> ImageSigner SIGN TestSigned.FFU TestSigned.Cat
    ```

## <a name="creating-custom-signed-images"></a>创建自定义签名的图像


**请注意**  
一些 Oem 可能想要使用自定义密钥管理映像。 此选项更复杂，并不建议使用。

 

创建图像时，还创建一个相关的目录文件。 此目录文件已签名，然后使用 ImageSigner 工具来签署 FFU 图像。 签名证书是否链接到 UEFI 引导由 OEM 提供的键的.cat 的文件。 不同的证书用于测试和零售签名。

对目录文件，请执行下列步骤使用适当的证书进行签名。

1.  打开具有管理员权限的目录中包含的输出图像生成过程的开发人员的提示。 有关详细信息，请参阅[构建映像使用 ImgGen.cmd](building-a-phone-image-using-imggencmd.md)。

2.  测试签名的目录文件命名为`TestRetailSigned.cat`使用证书名为`TestCertName.pfx`通过键入以下命令。

    ``` syntax
    C:\> SignTool sign /f TestCertName.pfx  TestRetailSigned.cat
    ```

    **重要**  
    与内部开发测试环境中的本地文件**/f**选项，应仅使用 signtool.exe。 使用硬件安全模块 (HSM) 时， **/csp**选项用于指定包含私钥的密钥容器的加密服务提供程序 (CSP)。 签名图像最终分发的更新软件包时，应遵从业界最佳做法。

     

3.  创建未签名的.ffu 文件中的签名的.ffu 文件和匹配的签名的.cat 文件使用 ImageSigner.exe 工具。

    ``` syntax
    C:\> ImageSigner SIGN TestRetailSigned.FFU TestRetailSigned.Cat
    ```

## <a name="imagesigner-syntax-reference"></a>ImageSigner 的语法引用


``` syntax
ImageSigner {SIGN|GETCATALOG|TRUNCATE} FFUFile CatalogFile|TruncatedFFU
```

-   **符号**-**符号**操作用于 FFU 文件签名。

-   **GETCATALOG** — **GETCATALOG**操作从 FFU 文件中提取一个目录，并将其写入目录文件。 此选项可用于确定是否 FFU 准备了正确，通过使用文件属性或诸如 SignTool 之类的工具检查提取的目录文件。

-   **截断**– 截断操作用于创建截断的 FFU。

-   *FFUFile* -FFU 图像文件的路径。

-   *CatalogFile* – 该编录文件的路径。

-   *TruncatedFFU* – 截断 FFU 文件的路径。

## <a name="related-topics"></a>相关的主题


[构建使用 ImgGen.cmd 电话映像](building-a-phone-image-using-imggencmd.md)

 

 

[发送有关此主题的意见的评论](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_phFlashing\p_phFlashing%5D:%20Sign%20a%20full%20flash%20update%20%28FFU%29%20image%20%20RELEASE:%20%2810/4/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "发送有关此主题的意见的评论")





