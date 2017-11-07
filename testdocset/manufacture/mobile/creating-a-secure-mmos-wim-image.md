---
author: kpacquer
Description: "创建安全的 MMO WIM 映像"
ms.assetid: c3ab9a94-a0a6-4831-9ac9-09c2972bb074
MSHAttr: PreferredLib:/library/windows/hardware
title: "创建安全的 MMO WIM 映像"
ms.openlocfilehash: 3e1af1c21c4b8ea97fe3868483e03aabacff7f31
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="creating-a-secure-mmos-wim-image"></a>创建安全的 MMO WIM 映像


可以使用 SecWimTool 来创建可以用于对服务零售设备安全 WIM 映像。

您可以创建安全的 WIM 之前，必须首先创建的 WIM 映像本身。 有关如何创建 WIM 映像的信息，请参阅[使用 WIM MMO 图像](working-with-wim-mmos-images.md)。

若要使用在零售业的 MMO WIM，它需要使用零售证书进行签名。 此文档中关于如何处理零售图像的更高版本中，将提供更多的信息。

在设备上运行安全 WIM，签名证书必须匹配的证书在设备配置的平台键 (PK)。

## <a name="span-idinstallingtheneededcertificatesonthephonespanspan-idinstallingtheneededcertificatesonthephonespanspan-idinstallingtheneededcertificatesonthephonespaninstalling-the-needed-certificates-on-the-phone"></a><span id="Installing_the_needed_certificates_on_the_phone"></span><span id="installing_the_needed_certificates_on_the_phone"></span><span id="INSTALLING_THE_NEEDED_CERTIFICATES_ON_THE_PHONE"></span>在手机上安装所需的证书


在运行这些工具之前，您必须首先配置设备上适当的证书。 熟悉 SecWimTool，合作伙伴可以使用安全启动*测试*工具来提供设备上的测试 （非零售） 证书。 使用安全启动*零售*工具零售设备。

## <a name="span-idcreatingasecuremmoswimimagespanspan-idcreatingasecuremmoswimimagespanspan-idcreatingasecuremmoswimimagespancreating-a-secure-mmos-wim-image"></a><span id="Creating_a_secure_MMOS_WIM_image"></span><span id="creating_a_secure_mmos_wim_image"></span><span id="CREATING_A_SECURE_MMOS_WIM_IMAGE"></span>创建安全的 MMO WIM 映像


若要创建安全的 wim 映像，请完成以下步骤。

1.  打开的目录中包含 ImgToWim 图像生成过程的输出提升开发人员的提示。 有关如何创建 WIM 映像的信息，请参阅[使用 WIM MMO 图像](working-with-wim-mmos-images.md)。

    **请注意**  
    图像生成可执行文件都位于 %WPDKCONTENTROOT%\\工具\\bin\\i386。 您可以使用`set`命令将该路径添加到您的环境。

     

2.  平台 ID 必须用于创建特定平台 WIM。 中使用的设备平台 XML 文件设置了平台 ID。

    您可以显示使用 ffutool 命令的平台 ID **-列表**选项。

    ``` syntax
    C:\> ffutool -list
    Name:   Contoso.DCD9X0X.BD301_ATT.3.2.1
    ID:     00000011-f151-a509-0000-FF0000000000
    ```

    生成未签名的安全针对特定平台使用 WIM *-平台*命令选项，如下所示。 如果该命令成功完成，则不返回任何输出。

    ``` syntax
    C:\> SecWimTool -build MMOSwim.wim MMOS wim.secwim -platform Contoso.DCD9X0X.BD301_ATT.3.2.1
    ```

3.  从安全的 WIM 映像解压目录。 如果该命令成功完成，则不返回任何输出。

    ``` syntax
    C:\> SecWimTool -extractcat MMOSwim.secwim MMOSwim.cat
    ```

4.  您可以签名 WIM 测试证书与测试 WIM 过程。 面向零售业必须由 Microsoft 签名安全 WIM、 FFU。

    **重要**  
    将在以后的版本的文档中提供的最终零售证书与签名有关的信息。

    对目录进行签名使用测试图像证书，请使用此命令。

    ``` syntax
    C:\> sign /pk MMOSwim.cat
    ```

    此命令将生成类似下面的输出。

    ``` syntax
    signtool.exe sign /v /a /u 1.3.6.1.4.1.311.76.5.10 /r "Microsoft Testing Root Certificate Authority 2010" /fd SHA256 /s my /c "1.3.6.1.4.1.311.21.8.7587021.7518
    74.11030412.6202749.3702260.207.4167089.4524209"    "MMOSwim.cat"
    The following certificate was selected:
        Issued to: User1
        Issued by: MSIT Test CodeSign CA 3
        Expires:   Sat Jun 21 15:05:01 2014
        SHA1 hash: F571C183F768638B424A59772A1AFB1168164AFC

    Done Adding Additional Store
    Successfully signed: MMOSwim.cat

    Number of files successfully Signed: 1
    Number of warnings: 0
    Number of errors: 0
    signed:  "MMOSwim.cat"
    Sign.Cmd RC=0
    ```

5.  有符号的目录替换现有目录。 如果该命令成功完成，则不返回任何输出。

    ``` syntax
    C:\> SecWimTool -replacecat flashwim.cat MMOSwim.secwim
    ```

6.  将设备放在闪烁模式。

7.  闪存设备到 WIM，它使用 FFUTool 进行测试。

    ``` syntax
    C:\> ffutool -wim MMOSwim.secwim
    ```

    该命令将生成类似下面的输出。

    ``` syntax
    Found device:
    Name:   Contoso.MSM8X0X.BD301_ATT.3.2.1
    ID:     00000011-f151-a509-0000-FF0000000000
    Booting WIM: MMOSwim.secwim
    WIM transfer completed in 26.550073 seconds.
   
    ```

## <a name="span-idworkingwithserialnumbersspanspan-idworkingwithserialnumbersspanspan-idworkingwithserialnumbersspanworking-with-serial-numbers"></a><span id="Working_with_serial_numbers"></span><span id="working_with_serial_numbers"></span><span id="WORKING_WITH_SERIAL_NUMBERS"></span>使用序列号


序列号选项可用时包括应仅用于特定设备的工具。

**序列号**的序列号是手机自动生成的唯一 ID。 您可以显示使用 ffutool 命令的序列号*-串行*选项。

``` syntax
C:\> ffutool -serial
Serial No. : 01000500000000000000000000001234
```

若要生成安全 WIM 针对特定设备，使用*-串行*命令选项，如下所示。

``` syntax
C:\> SecWimTool -build MMOSwim.wim MMOS wim.secwim -serial 01000500000000000000000000001234
```

## <a name="span-idtroubleshootingspanspan-idtroubleshootingspanspan-idtroubleshootingspantroubleshooting"></a><span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>故障排除


当您刷新图像如果 PK 不符时，请您将收到此消息。

``` syntax
An FFU error occurred: Device returned WIM boot failure status code 0x80000004.
```

## <a name="span-idsecwimtoolcommandlinereferencespanspan-idsecwimtoolcommandlinereferencespanspan-idsecwimtoolcommandlinereferencespansecwimtool-command-line-reference"></a><span id="SecWimTool_command_line_reference"></span><span id="secwimtool_command_line_reference"></span><span id="SECWIMTOOL_COMMAND_LINE_REFERENCE"></span>SecWimTool 命令行参考


以下总结的命令语法和 SecWimTool 的四个命令行选项。

``` syntax
SecWimTool <command> <arguments>
```

**-生成**-适用于签名和转移到零售设备 secwim 为包指定的 WIM。

-   *平台*-包括定位 WIM 适用于特定的平台类型的信息。 针对特定平台的 WIM，必须使用此选项。

-   *串行*-包括 WIM 将在使用某个具体设备的序列号。 包括应仅用于特定设备的工具时，可以使用此选项。

``` syntax
SecWimTool -build <WIM> <output file> [-platform <ID>] [-serial <serial number>]
```

**-extractcat** -从安全的 WIM 文件，检索目录，并写到标准输出的输出文件 （如果已指定）。

``` syntax
secwim -extractcat <path to .secwim> [<output file>]
```

**-replacecat** -替换为新目录的内容的目录中指定.secwim。

``` syntax
secwim -replacecat <path to catalog> <path to .secwim>
```

**-?** -显示命令行帮助。 使用`secwimtool -<command> -?`级命令的帮助。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[使用 WIM MMO 图像](working-with-wim-mmos-images.md)

 

 






