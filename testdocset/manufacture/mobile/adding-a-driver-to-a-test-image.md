---
title: "将驱动程序添加到测试映像"
description: "本主题演示如何创建特征，并将其添加到测试映像。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 9ac41806-b3c5-4cbf-8c41-cb838d7d0d52
ms.openlocfilehash: 7ef4d22ac4f404bd0636ccfb46fa8f9ea496ec08
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="adding-a-driver-to-a-test-image"></a>将驱动程序添加到测试映像


本主题演示如何创建特征，并将其添加到测试映像。

## <a name="a-href-idprocess-overview---adding-a-driver-feature-to-a-test-imageaprocess-overview-adding-a-driver-feature-to-a-test-image"></a><a href="" id="process-overview---adding-a-driver-feature-to-a-test-image"></a>过程概述 – 将驱动程序功能添加到测试映像


若要创建包含驱动程序的功能并将其添加到测试图像，请完成以下步骤。

1.  [创建测试 KMDF 驱动程序](#create-test)

2.  [生成该驱动程序包](#generate-the-driver)

3.  [创建引用包的功能清单文件](#create-a-feature)

4.  [将此功能添加到 OEMInput.xml 文件](#add-a-feature)

5.  [生成、 签名和闪存设备图像](#generate-sign)

6.  [验证设备上 KMDFDriver1](#verify)

7.  [请验证该驱动程序加载使用 Windows 调试](#windbg)

下图总结了打包和图像生成元素，用于添加到设备驱动程序。

![oem\-功能\-创建\-包装\-方案](images/oem-feature-creation-packaging-scenario.png)

## <a name="a-href-idwalkthrough---adding-a-driver-to-a-test-imageawalkthrough-adding-a-driver-to-a-test-image"></a><a href="" id="walkthrough---adding-a-driver-to-a-test-image"></a>演练 – 将驱动程序添加到测试映像


本主题中介绍的步骤，您需要执行到测试映像添加驱动程序。 在开始本演练之前，您必须首先创建一个简单的 KMDF 驱动程序。

本演练假定您命名的项目*KmdfDriver1*。

### <a name="a-href-idcreate-testacreate-a-test-kmdf-driver"></a><a href="" id="create-test"></a>创建测试 KMDF 驱动程序

若要创建测试 KMDF 驱动程序，请完成以下步骤。

1.  在**解决方案资源管理器**窗口中，展开**KmdfDriver1** ，然后展开**源文件夹**。

2.  通过单击编辑"Driver.c"文件。

3.  右后的变量声明部分，如下面所示，添加**IoReportRootDevice**例程。 **IoReportRootDevice**例程报告不能检测到即插即用管理器即插即用总线驱动程序的设备。 这允许仅针对软件的驱动程序仍保持加载。

    ``` syntax
    ...
    {
        WDF_DRIVER_CONFIG config;
        NTSTATUS status;
        WDF_OBJECT_ATTRIBUTES attributes;

       //
       // IoReportRootDevice routine reports a device that cannot be detected by 
       // a PnP bus driver to the PnP Manager. This allows our software-only
       // driver to remain loaded.  
      IoReportRootDevice(DriverObject);

        //
        // Initialize WPP tracing.
        //
        WPP_INIT_TRACING( DriverObject, RegistryPath );
        TraceEvents(TRACE_LEVEL_INFORMATION, TRACE_DRIVER, "%!FUNC! Entry");

    ... 
    ```

4.  保存 Driver.c。

5.  生成您的驱动程序并创建驱动程序软件包，请**生成**菜单中选择**生成解决方案**。 Visual Studio 在**输出**窗口中显示生成进度。 （如果*输出*窗口中不可见，选择**输出**从**视图**菜单。

6.  若要查看内置驱动程序软件包，定位在 Windows 资源管理器中对**KmdfDriver1**文件夹，然后指向**ARM\\Win8.1Debug\\**。 此目录包含下列文件︰

    -   KmdfDriver1.sys-一个内核模式驱动程序文件。

    -   KmdfDriver1.inf-Windows 用来安装驱动程序信息文件。

    -   KmdfDriver1.pdb — 包含可用于调试的调试符号的文件。

    -   KmdfDriver1.cat-不在本演练中使用的目录文件。

    此外，还有共同安装程序文件将不能与 Windows Phone 使用 Windows 驱动程序框架 (WDF) 的。

7.  由于 Windows 10 移动 INF 文件中的差异，我们不会使用桌面生成的 Visual Studio 的 INF 文件。

    ``` syntax
    ;
    ; KmdfDriver1.inf
    ;
    [Version]
    Signature="$WINDOWS NT$"
    Class=System
    ClassGuid={4d36e97d-e325-11ce-bfc1-08002be10318}
    Provider=%MSFT%
    DriverVer=11/01/2012,1.00.00.00
    BootCritical=1

    [DestinationDirs]
    DefaultDestDir = 12

    [Manufacturer]
    %StdMfg%=KMDFDriver1_DevDesc, NTARM, NTx86

    ;*******************************
    ;** models section (required) **
    ;*******************************
    ; For ARM platforms
    [KMDFDriver1_DevDesc.NTARM]
    ; DisplayName      Section          DeviceId
    ; -----------      -------          --------
    %KMDFDriver1_DevDesc%=KMDFDriver1, Root\KMDFDriver1

    ; For Win2K+
    [KMDFDriver1_DevDesc.NTx86]
    ; DisplayName       Section          DeviceId
    ; -----------       -------          --------
    %KMDFDriver1_DevDesc%=KMDFDriver1, Root\KMDFDriver1

    ;********************************
    ;* ddinstall section (required) *
    ;********************************
    [KMDFDriver1.NT]
    CopyFiles=KMDFDriver1.NT.Copy

    [KMDFDriver1.NT.Copy]
    KMDFDriver1.sys

    ;-------------- Service installation

    [KMDFDriver1.NT.Services]
    AddService = KMDFDriver1, %SPSVCINST_ASSOCSERVICE%, KMDFDriver1_Service_Inst

    [KMDFDriver1_Service_Inst]
    DisplayName    = %KMDFDriver1_DevDesc%
    ServiceType    = %SERVICE_KERNEL_DRIVER%
    StartType      = %SERVICE_SYSTEM_START%
    ErrorControl   = %SERVICE_ERROR_NORMAL%
    ServiceBinary  = %12%\KMDFDriver1.sys


    [Strings]
    SPSVCINST_ASSOCSERVICE= 0x00000002
    MSFT = "Microsoft"
    KMDFDriver1_DevDesc = "KMDF Driver 1"
    SERVICE_KERNEL_DRIVER = 1
    SERVICE_AUTO_START = 2
    SERVICE_SYSTEM_START = 1
    SERVICE_BOOT_START = 0
    SERVICE_ERROR_NORMAL = 1
    ```

8.  签名的驱动程序，使用下列命令︰

    ``` syntax
    C:>set SIGN_OEM=1 
    sign KMDFDriver1.sys 
    ```

### <a name="a-href-idgenerate-the-driveragenerate-a-package-that-contains-the-driver"></a><a href="" id="generate-the-driver"></a>生成包含驱动程序的包

生成一个包，其中包含该驱动程序通过完成以下步骤。

1.  创建名为*KMDFDriver1*的目录并复制到该目录在 Visual Studio 中，创建的 KMDFDriver1.sys 和 KMDFDriver1.inf 文件。

2.  创建一个文本文件，名为*KmdfDriver1。 pkg.xml* ，其中包含以下程序包定义 XML。

    ``` syntax
    <?xml version="1.0" encoding="utf-8"?>
    <Package xmlns="urn:Microsoft.WindowsPhone/PackageSchema.v8.00"
      Owner="Contoso"
      OwnerType="OEM"     
      ReleaseType="Test"          
      Platform="DCD6000"          
      Component="Phone.Test.BaseOS"
      SubComponent="KmdfDriver1"
      Partition="MainOS"
      BinaryPartition="false">
      <Components>
        <OSComponent>
            <Files>
                <File Source="KmdfDriver1.sys" DestinationDir="$(runtime.system32)\drivers"/>
            </Files>
        </OSComponent>
        <Driver InfSource="KmdfDriver1.inf">
            <Reference Source="KmdfDriver1.sys"/>
        </Driver>
      </Components>
    </Package>
    ```

    您可以更新您的组织名称和您的设备的名称的名称相匹配的所有者和平台属性。 这些属性更改将修改生成的包的名称。

    指定*Windows\\System32\\驱动程序*目录上使用 $(runtime.system32) 宏的设备。

3.  下一步是通过打开管理员命令提示符窗口中生成包。

4.  显示管理员命令提示符窗口中键入**设置**环境变量。 *WPDKCONTENTROOT*以确认正确配置了生成环境中寻找。 您应该看到 WPDKCONTENTROOT 被设置。 在 Windows 64 位 PC 上，路径应类似于以下。

    ``` syntax
    ...
    WPDKCONTENTROOT=C:\Program Files (x86)\Windows Kits\10
    ```

5.  生成使用 PkgGen 软件包。 提供的版本 1.0.0.0 数。 /Config 参数指向与 Windows DriverKit 提供的 pkggen.cfg.xml 文件的位置。 /Hive 参数指向配置单元根目录的位置。

    ``` syntax
    C:\KmdfDriver1>PkgGen KmdfDriver1.pkg.xml /version:1.0.0.0 /variables:"HIVE_ROOT=%WPDKCONTENTROOT%\CoreSystem" /config:"%WPDKCONTENTROOT%\Tools\bin\i386\pkggen.cfg.xml"
    ```

6.  如果 PkgGen 成功创建包，则的注册表项创建基于所提供的 INF 文件将显示多行信息。 输出的最后一部分将类似于以下。

    ``` syntax
    ... 
    info: Import Log: :      sto: Unloaded hive key '{bf1a281b-ad7b-4476-ac95-f47682
    990ce7}C:/Users/User1/AppData/Local/Temp/gs5gvfgc.pou/windows/system32/config/S
    OFTWARE'. Time = 0 ms
    info: Import Log: : <<<  Section end 2015/08/06 13:10:22.413
    info: Import Log: : <<<  [Exit status: SUCCESS]
    info: Import Log: :
    info: Import Log: :
    info: Import Log: : >>>  [Unload Offline Registry Hive - DRIVERS]
    info: Import Log: : >>>  Section start 2014/08/06 13:10:22.413
    info: Import Log: :        os: Version = 6.3.9600, Service Pack = 0.0, Suite = 0
    x0100, ProductType = 1, Architecture = x86
    info: Import Log: :       cmd: PkgGen  KmdfDriver1.pkg.xml /version:1.0.0.0 /var
    iables:"HIVE_ROOT=C:\Program Files (x86)\Windows Kits\10\CoreSystem" /con
    fig:"C:\Program Files (x86)\Windows Kits\10\Tools\bin\i386\pkggen.cfg.xml
    "
    info: Import Log: :      sto: Closed hive key '{bf1a281b-ad7b-4476-ac95-f4768299
    0ce7}C:/Users/User1/AppData/Local/Temp/gs5gvfgc.pou/windows/system32/config/DRI
    VERS'.
    info: Import Log: :      sto: Unloaded hive key '{bf1a281b-ad7b-4476-ac95-f47682
    990ce7}C:/Users/User1/AppData/Local/Temp/gs5gvfgc.pou/windows/system32/config/D
    RIVERS'. Time = 0 ms
    info: Import Log: : <<<  Section end 2014/08/06 13:10:22.513
    info: Import Log: : <<<  [Exit status: SUCCESS]
    info: Import Log: :
    info: Building package '.\Contoso.Phone.Test.BaseOS.KmdfDriver1.spkg'
    info: Adding file 'KmdfDriver1.sys' to package '.\Contoso.Phone.Test.BaseOS.Kmdf
    Driver1.spkg' as '\windows\System32\drivers\KmdfDriver1.sys'
    info: Adding file 'C:\Users\User1\AppData\Local\Temp\5bgjkx3p.j01\reg.reg' to p
    ackage '.\Contoso.Phone.Test.BaseOS.KmdfDriver1.spkg' as '\Windows\Packages\Regi
    stryFiles\Contoso.Phone.Test.BaseOS.KmdfDriver1.reg'
    info: Adding file 'C:\Users\User1\AppData\Local\Temp\5bgjkx3p.j01\regMultiSz.rg
    a' to package '.\Contoso.Phone.Test.BaseOS.KmdfDriver1.spkg' as '\Windows\Packag
    es\RegistryFiles\Contoso.Phone.Test.BaseOS.KmdfDriver1.rga'
    info: Done package ".\Contoso.Phone.Test.BaseOS.KmdfDriver1.spkg"
    info: Packages are generated to . successfully
    ```

有关如何使用软件包的详细信息，请参阅[创建程序包](creating-mobile-packages.md)。

### <a name="a-href-idcreate-a-featureacreate-a-feature-manifest-file-that-references-the-package"></a><a href="" id="create-a-feature"></a>创建引用包的功能清单文件

创建将通过完成以下步骤定义驱动因素 1 OEM 功能的功能清单文件。

1.  创建以下目录中名为*OEMCustomAppFM.xml*的功能清单文件。

    ``` syntax
    %WPDKCONTENTROOT%\FMFiles
    ```

2.  通过向*OEMCustomDriverFM.xml*文件中添加以下 XML 定义驱动因素 1 功能。 更新文件包的名称与在上一步中生成的包文件的名称匹配。

    ``` syntax
    <?xml version="1.0" encoding="utf-8"?>  
    <FeatureManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate">  
    <!--  DRIVER1 FM File 7/31/2014   -->
      <Features>  
        <OEM>  
          <PackageFile Path="C:\KmdfDriver1\" Name="Contoso.Phone.Test.BaseOS.KmdfDriver1">  
            <FeatureIDs>  
              <FeatureID>DRIVER1</FeatureID>  
            </FeatureIDs>  
          </PackageFile>  
        </OEM>  
      </Features>  
    </FeatureManifest>
    ```

有关功能清单的详细信息，请参阅[功能清单文件的内容](feature-manifest-file-contents.md)。

### <a name="a-href-idadd-a-featureaadd-the-feature-to-the-oeminputxml-file"></a><a href="" id="add-a-feature"></a>将此功能添加到 OEMInput.xml 文件

通过完成以下步骤，将驱动因素 1 功能添加到 OEMInput.xml 文件。

1.  本演练假定您有一个现有的、 使 TShell 的功能测试 OEMInput 文件。 有关创建测试映像的详细信息，请参阅[构建和闪烁图像](building-and-flashing-images.md)。 有关指定可选功能的详细信息，请参阅[构建映像的可选功能](optional-features-for-building-images.md)。

    确认您正在使用已启用调试测试映像。 有关详细信息，请参阅[构建映像的可选功能](optional-features-for-building-images.md)。

2.  编辑 OEMinput.xml 文件包含您在上一步中创建的*OEMCustomAppFM.xml*功能清单文件。 将类似于以下 XML。

    ``` syntax
    ...
    <AdditionalFMs>
        ...
        <AdditionalFM>%WPDKCONTENTROOT%\FMFiles\OEMCustomDriverFM.xml</AdditionalFM>
      </AdditionalFMs>
    ```

3.  在&lt;功能&gt;部分的 OEMInput.xml 文件中，请添加新的驱动因素 1 功能到列表中的现有功能。

    ``` syntax
    <Features>
      <Microsoft>
       ...
      </Microsoft>
      <OEM>
        ...
        <Feature>DRIVER1</Feature>
      </OEM>
    </Features>
    ```

### <a name="a-href-idgenerate-signagenerate-sign-and-flash-the-image-to-the-device"></a><a href="" id="generate-sign"></a>生成、 签名和闪存设备图像

完成以下步骤来生成、 签名和闪烁图像。

1.  生成使用 ImgGen 和 OEMInput.xml 文件，您在上一步中自定义的图像。

    ``` syntax
    C:\>ImgGen Flash.ffu OEMInput.xml "%WPDKCONTENTROOT%\10\MSPackages"
    ```

2.  可以对图像进行签名之前，首先必须通过[设置签名的环境](https://msdn.microsoft.com/library/windows/hardware/dn789236)中的步骤的电脑上安装 OEM 测试证书。

3.  登录 Sign.cmd 使用**/pk**选项生成的目录。

    ``` syntax
    C:\> Set SIGN_OEM=1
    C:\> Sign.cmd /pk TestSigned.cat
    ```

4.  对 FFU 签名与签名的编录文件使用 ImageSigner。

    ``` syntax
    C:\> ImageSigner Sign Flash.FFU Flash.Cat
    ```

5.  闪烁的图像使用 FFUTool 的移动电话。

    ``` syntax
    C:\> FFUTool –Flash Flash.ffu
    ```

有关生成和闪烁图像的详细信息，请参阅[构建和闪烁图像](building-and-flashing-images.md)。

### <a name="a-href-idverifyaverify-that-the-kmdfdriver1-is-on-the-device"></a><a href="" id="verify"></a>验证设备上 KMDFDriver1

验证 KMDFDriver1 是通过 TShell 设备上存在。

1.  TShell 将连接配置为测试映像。

2.  建立与使用**开放设备**TShell 命令的设备的连接。 提供设备的 MAC 地址。

    ``` syntax
    PS C:\> Open-device 001122334455
    ```

3.  确认在设备上的 KMDFDriver1 使用**Dir 设备**TShell 命令。 显示命令，DirD 的缩写形式。

    ``` syntax
    PS C:\> DirD \KMDFDriver1.sys /s
    ```

4.  您应该看到类似于下面的输出。

    ``` syntax
    Volume in drive C is MainOS
    Volume Serial Number is 965E-2180
    Directory of C:\windows\system32\DRIVERS
    04/21/2014  05:23 PM              8864 KMDFDriver1.sys
                   1 File(s)           8864 bytes
         Total Files Listed:
                   1 File(s)           8864 bytes
                   0 Dir(s)       409976832 bytes free
    ```

5.  通过设置注册表项来启用调试输出的 KdPrint()、 KdPrintEx() 和 DbgPrint() 的消息。 设置注册表项，以便它持久 （用于非零售图像） 重新引导使用**RegD 添加**TShell 命令。

    ``` syntax
    DEVICE C:\
    PS C:\Windows\system32> RegD Add "HKLM\SYSTEM\ControlSet001\Control\Session Manager\Debug Print Filter" /v DEFAULT /t REG_DWORD /d 0xFFFFFFFF

    The operation completed successfully.
    ```

6.  确认使用的**RegD 查询**TShell 命令设置该注册表项。

    ``` syntax
    DEVICE C:\
    PS C:\Windows\system32> RegD Query "HKLM\SYSTEM\ControlSet001\Control\Session Manager\Debug Print Filter"

    HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\Session Manager\Debug Print Filter
        DEFAULT    REG_DWORD    0xffffffff
    ```

### <a name="a-href-idwindbgaverify-that-the-driver-loads-using-windows-debug"></a><a href="" id="windbg"></a>请验证该驱动程序加载使用 Windows 调试

若要查看驱动程序的加载过程，请完成以下步骤以在驱动程序设置调试语句并将设备连接到内核调试程序。

1.  在 Visual Studio 中打开驱动程序项目。

2.  变量声明部分中的驱动程序入口例程之后立即在 Driver.c 中添加调试中断语句。

    ``` syntax
       …
        WDF_DRIVER_CONFIG config;
        NTSTATUS status;
        WDF_OBJECT_ATTRIBUTES attributes;

        // Debug break statement to stop loading of OS 
        // Debugger must be attached to allow the device to boot
         __debugbreak();
    …
    ```

    **警告**  
    调试中断语句将停止引导除非调试器已附加到此设备的电话。

     

3.  重建项目中，Visual Studio。

4.  如有必要，将用于创建生成软件包的目录复制更新的.sys 文件。

5.  然后，重复到上面所述的步骤操作︰

    1.  生成一个更新的驱动程序程序包。

    2.  生成、 签名和闪烁图像。

    **请注意**  
    还有可能在 INF 文件中包括驱动程序的版本，然后使用 IUTool 部署到手机的更新的驱动程序更新版本的驱动程序。 有关使用 IUTool 的详细信息，请参阅[IUTool.exe︰ 更新包在电话上的](update-packages-on-a-phone-and-get-package-update-logs.md)。 此过程非常类似于用来创建的驱动程序更新的过程。 有关的详细信息，请参阅[更新 KMDF 设备驱动程序](../../service/mobile/update-a-kmdf-device-driver.md)。

     

6.  通过 USB 连接到用于调试手机设置 KDNET。

7.  启动 Windows 调试器。

    ``` syntax
    windbg -k net:port=5000,key=1.2.3.4
    ```

8.  设备启动后，它会命中断点，并将停止执行代码。 调试器将指示已命中该断点。

9.  设置符号路径的 Windows 驱动程序工具包符号的位置并重新加载符号。

    ``` syntax
    .SYMPATH+ C:\SYMBOLS
    .reload /f
    ```

10. 将源路径设置为.c 源代码在 Visual Studio 的前面部分中创建的位置。

    ``` syntax
    .srcpath+ C:\KMDFDriver1\Source\
    ```

11. 使用**k**命令列出调用堆栈。

    ``` syntax
    0: kd> k
    # Child-SP RetAddr  Call Site
    00 85679c68 90fd2abe KMDFDriver1!DriverEntry+0xa
    01 85679ce0 90fd2b38 KMDFDriver1!FxDriverEntryWorker+0x6a
    02 85679d00 81770990 KMDFDriver1!FxDriverEntry+0x18
    *** ERROR: Symbol file could not be found.  Defaulted to export symbols for ntkrnlmp.exe - 
    03 85679d10 818f8004 nt!SeTokenIsAdmin+0x1790
    04 85679e10 8190d630 nt!KeFindConfigurationNextEntry+0x7c48
    05 85679e68 8185719e nt!KeHwPolicyLocateResource+0x4698
    06 85679e70 814c5e0c nt!IoReplacePartitionUnit+0x192
    07 85679e80 81460172 nt!IoAllocateIrp+0x57c
    08 85679ec8 00000000 nt!KiDispatchInterrupt+0x234a
    ```

    调用堆栈是催生当前程序计数器的位置的函数调用链。 顶级函数在调用堆栈上的当前函数，并且下一个函数调用当前函数的函数，等等。

12. 显示与 KMDFDriver1 相关联的符号信息使用**x**命令。

    ``` syntax
    0: kd> x KMDFDriver1!*
    90fd4750          KMDFDriver1!WdfDriverGlobals = 0x88ff4de8
    90fd4754          KMDFDriver1!WdfDriverStubDriverObject = 0x88fed768
    90fd4004          KMDFDriver1!__security_cookie_complement = 0x568f867
    90fd336c          KMDFDriver1!__gsfailure_xdata_end = <unknown base type 80000013>
    90fd33b4          KMDFDriver1!__memcpy_reverse_large_neon_xdata = <unknown base type 80000013>
    90fd30c0          KMDFDriver1!WPP_c0dfc8e231dc218098dc0c2ed20d6e73_Traceguids = struct _GUID [1]
    90fd30a0          KMDFDriver1!GUID_DEVINTERFACE_KmdfDriver1 = struct _GUID {e7a4cfb0-56d4-4234-bf60-fe627cb5e981}
    90fd474c          KMDFDriver1!WdfDriverStubDisplacedDriverUnload = 0x00000000
    90fd3370          KMDFDriver1!memcpy_xdata_prolog = <unknown base type 80000013>
    90fd3388          KMDFDriver1!__memcpy_forward_large_neon_xdata = <unknown base type 80000013>
    90fd4758          KMDFDriver1!WdfDriverStubOriginalWdfDriverMiniportUnload = 0x00000000
    ```

13. 通过使用**lm m**命令列出的 KMDFDriver1 模块的信息。

    ``` syntax
    0: kd> lm m KMDFDriver1 v
    Browse full module list
    start    end        module name
    90fd1000 90fd9000   KMDFDriver1   (private pdb symbols)  c:\kmdfdriver1\KmdfDriver1.pdb
        Loaded symbol image file: KMDFDriver1.sys
        Image path: KMDFDriver1.sys
        Image name: KMDFDriver1.sys
        Browse all global symbols  functions  data
        Timestamp:        Thu Jul 31 14:39:34 2014 (53DAB796)
        CheckSum:         000037D2
        ImageSize:        00008000
        Translations:     0000.04b0 0000.04e4 0409.04b0 0409.04e
    ```

14. 加载使用**.load**命令 WDF 驱动程序扩展。

    ``` syntax
    .load C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\winext\Wdfkd.dll
    ```

15. 通过使用已加载的 WDF 调试扩展**！ wdfkd.help** WDK 驱动程序扩展帮助命令。

    ``` syntax
    !wdfkd.help
    ```

16. 显示有关驱动程序使用的信息**！ wdfkd.wdfdriverinfo**命令。

    ``` syntax
    0: kd> !wdfkd.wdfdriverinfo KMDFDriver1
    ----------------------------------
    Default driver image name: KMDFDriver1
    WDF library image name: Wdf01000
    FxDriverGlobals  0x90584008
    WdfBindInfo      0x913d8008
       Version        v1.11
    Library module   0x8283b528
       ServiceName    \Registry\Machine\System\CurrentControlSet\Services\Wdf01000
       ImageName      Wdf01000
    ----------------------------------
    Driver Handles is NULL
    ```

17. 结束调试会话使用**qd**退出和分离命令。

    ``` syntax
    0: kd> qd
    ```

 

 

[发送有关此主题的意见的评论](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_phFlashing\p_phFlashing%5D:%20Adding%20a%20driver%20to%20a%20test%20image%20%20RELEASE:%20%2810/4/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "发送有关此主题的意见的评论")




