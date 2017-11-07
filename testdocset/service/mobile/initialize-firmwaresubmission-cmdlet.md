---
author: kpacquer
Description: "初始化 FirmwareSubmission cmdlet"
ms.assetid: f941c3e5-dea6-444b-aebe-41ca07b24377
MSHAttr: PreferredLib:/library/windows/hardware
title: "初始化 FirmwareSubmission cmdlet"
ms.openlocfilehash: 993a7d88c700c9a8e95598c4a77ff530d36adcd8
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="initialize-firmwaresubmission-cmdlet"></a>初始化 FirmwareSubmission cmdlet


使用此独立 cmdlet 准备固件提交。 此 cmdlet 合并到 zip 文件在本地计算机上的固件提交并不与合作伙伴服务通信。

使用此 cmdlet 后, 使用[New FirmwareSubmission cmdlet](new-firmwaresubmission-cmdlet.md)上载包含固件提交的 zip 文件。 此 cmdlet 提供为输出只有一个.NET 文件对象。 若要提交此 cmdlet 从创建的 zip 文件，请使用**New FirmwareSubmission** cmdlet。

## <a name="span-idprerequisitesspanspan-idprerequisitesspanspan-idprerequisitesspanprerequisites"></a><span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>系统必备组件


创建一个包，使用 ImgGen.cmd。 这将创建多个文件，其中包括一个 UpdateHistory.xml 文件和目标的包文件，将用以下格式命名，其中&lt;OEM&gt;的 OEM 名称和&lt;设备&gt;是该设备的名称︰

&lt;OEM&gt;。&lt;设备&gt;。Customizations.MainOS.spkg

若要为多个 Oem 或设备使用相同的映像，添加目标文件 (PhoneMetadataDeviceTargetingInfo.xml)。 有关详细信息，请参阅[DeviceInfo](https://msdn.microsoft.com/library/windows/hardware/mt138322)。

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>参数


以下是此 cmdlet 的输入的参数。

<span id="-UpdateHistoryPath__required_"></span><span id="-updatehistorypath__required_"></span><span id="-UPDATEHISTORYPATH__REQUIRED_"></span>*-UpdateHistoryPath （必填）*  
UpdateHistory 文件的字符串路径。

<span id="-OemInputPath__required_"></span><span id="-oeminputpath__required_"></span><span id="-OEMINPUTPATH__REQUIRED_"></span>*-OemInputPath （必填）*  
OEMInput.xml 文件的字符串路径。

<span id="-TypeOfSubmission__required_"></span><span id="-typeofsubmission__required_"></span><span id="-TYPEOFSUBMISSION__REQUIRED_"></span>*-TypeOfSubmission （必填）*  
提交类型中。 该类型必须是**图像**、 **FfuCatalog**或**PartialImage**。

<span id="-OutputFilePath__required_"></span><span id="-outputfilepath__required_"></span><span id="-OUTPUTFILEPATH__REQUIRED_"></span>*-OutputFilePath （必填）*  
生成的输出 zip 文件字符串路径。 如果此参数不包含完整的路径，输出文件将保存在当前工作目录中。

<span id="-TypeOfProduct"></span><span id="-typeofproduct"></span><span id="-TYPEOFPRODUCT"></span>*-TypeOfProduct*  
一个可选参数，指定目标产品的固件提交。 产品必须是 WindowsPhoneBlue、 WindowsPhoneThreshold 和 WindowsIoTCoreThreshold。 默认值为 WindowsPhoneBlue。

**请注意** 可以添加或删除定期产品值。

 

<span id="-SignedRemovalPackageFolder"></span><span id="-signedremovalpackagefolder"></span><span id="-SIGNEDREMOVALPACKAGEFOLDER"></span>*-SignedRemovalPackageFolder*  
该文件夹中删除的字符串路径 （与以.spkr 结尾的文件扩展名） 包添加到映像。

<span id="-PackagesToRemoveFolder"></span><span id="-packagestoremovefolder"></span><span id="-PACKAGESTOREMOVEFOLDER"></span>*-PackagesToRemoveFolder*  
字符串包含可用于生成删除程序包添加到映像 （使用以.spkg 结尾的文件扩展名） 的文件包的文件夹路径。

<span id="-Baseline"></span><span id="-baseline"></span><span id="-BASELINE"></span>*基准线*  
声明的固件提交为基准，以便它可用于零售服务 （通过请求更新 (RFU)）。 比较基准提交必须是 Windows 标准软件包配置符合要求。 有关详细信息，请参阅[零售映像的 Windows 标准包装配置 (WSPC) 要求](https://msdn.microsoft.com/library/dn756781)。

不能与**-TypeOfSubmission FfuCatalog** **-TypeOfSubmission PartialImage**使用此标志。

此外，不能与**-SignedRemovalPackageFolder**或**– PackagesToRemoveFolder**使用此标志。

<span id="-NonWspcCompliant"></span><span id="-nonwspccompliant"></span><span id="-NONWSPCCOMPLIANT"></span>*-NonWspcCompliant*  
不推荐使用此参数。 它最初用来表示，提交已打算不符合与第 Windows Phone 标准软件包配置 (WSPC)。 WSPC 模型已更改，不再使用此标志。

关于 WSPC 要求的详细信息，请参阅[Windows 标准包装配置 (WSPC) 要求零售映像](https://msdn.microsoft.com/library/dn756781)。

<span id="-FfuPath"></span><span id="-ffupath"></span><span id="-FFUPATH"></span>*-FfuPath*  
包含 FFU 目录提交要签名 FFU 文件的完整路径。 指定**-TypeOfSubmission FfuCatalog**时，请使用该参数。

<span id="-PartialImageDirectory"></span><span id="-partialimagedirectory"></span><span id="-PARTIALIMAGEDIRECTORY"></span>*-PartialImageDirectory*  
对包含 SPKG 文件只包含部分图像的目录的完整路径。 指定**-TypeOfSubmission PartialImage**时，请使用该参数。

## <a name="span-idsamplewindowspowershellscriptsspanspan-idsamplewindowspowershellscriptsspanspan-idsamplewindowspowershellscriptsspansample-windows-powershell-scripts"></a><span id="Sample_Windows_PowerShell_scripts"></span><span id="sample_windows_powershell_scripts"></span><span id="SAMPLE_WINDOWS_POWERSHELL_SCRIPTS"></span>Windows PowerShell 的示例脚本


可以使用下面的 Windows PowerShell 脚本提交 FFU 目录要签名。

``` syntax
Initialize-FirmwareSubmission -TypeOfSubmission FfuCatalog –UpdateHistoryPath [path] –OemInputPath [path] –OutputFilePath [path] –FfuPath [path]
```

可以使用下面的 Windows PowerShell 脚本提交要签名的部分图像。

``` syntax
Initialize-FirmwareSubmission -TypeOfSubmission PartialImage –UpdateHistoryPath [path] –OemInputPath [path] –OutputFilePath [path] –PartialImageDirectoy [path]
```

可以使用以下 Windows PowerShell 脚本来读取此 cmdlet 的输出管道中的验证错误处\[路径\]将被替换为相应的绝对文件路径。

``` syntax
try 
{
Initialize-FirmwareSubmission -TypeOfSubmission Image –UpdateHistoryPath [path] –OemInputPath [path] –OutputFilePath [path] –SignedRemovalPackageFolder [path] –PackagesToRemoveFolder [path]
}
catch 
{
# Assuming exception is a validation error
Write-Host $_.Exception.ValidationErrorLog
}
```

## <a name="span-iderrorsspanspan-iderrorsspanspan-iderrorsspanerrors"></a><span id="Errors"></span><span id="errors"></span><span id="ERRORS"></span>错误


如果不正确地构造提交 zip，此 Windows Powershell cmdlet 将返回一个空字符串。 如果提交 zip 构造，但出现验证错误，这些错误中的错误日志中提交 zip 捕获。

Windows Phone 8.1 中的目标包是必需的 (&lt;OEM&gt;。&lt;设备&gt;。Customizations.MainOS.spkg)。 如果此程序包不包含，则将引发异常。

## <a name="span-idhelpdocumentationfromwindowspowershellspanspan-idhelpdocumentationfromwindowspowershellspanspan-idhelpdocumentationfromwindowspowershellspanhelp-documentation-from-windows-powershell"></a><span id="Help_documentation_from_Windows_PowerShell"></span><span id="help_documentation_from_windows_powershell"></span><span id="HELP_DOCUMENTATION_FROM_WINDOWS_POWERSHELL"></span>从 Windows PowerShell 的帮助文档


``` syntax
NAME
    Initialize-FirmwareSubmission

SYNOPSIS


SYNTAX
Initialize-FirmwareSubmission [[-TypeOfProduct] <String>] [[-TypeOfSubmission] <String>] [-UpdateHistoryPath]
    <String> [-OemInputPath] <String> -OutputFilePath <String> [-SignedRemovalPackageFolder <String>]
    [-PackagesToRemoveFolder <String>] [-Baseline] -FfuPath -PartialImageDirectory [<CommonParameters>]]


DESCRIPTION
    This cmdlet is used to prepare a submission .zip for code signing,
    including packages to be signed and related metadata. This cmdlet only
    works on an x86 instance of PowerShell.


PARAMETERS
    -TypeOfProduct <String>
        An optional parameter that specifies the target product of the
        firmware submission. The product must be one of WindowsPhoneBlue and
        WindowsPhoneThreshold. Default is WindowsPhoneBlue.

        Required?                    false
        Position?                    0
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -TypeOfSubmission <String>
        Acceptable values are Image, PartialImage, and FfuCatalog.
        Mandatory parameters for Image submission are: UpdateHistoryPath,
        OemInputPath, and OutputFilePath. If you forget a mandatory parameter,
        the cmdlet will prompt you for it.

        Required?                    false
        Position?                    1
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -UpdateHistoryPath <String>
        Full path to UpdateHistory.xml file.

        Required?                    true
        Position?                    2
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -OemInputPath <String>
        Full path to OEMInput.xml file.

        Required?                    true
        Position?                    3
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -OutputFilePath <String>
        Full path to directory which will contain output .zip file.

        Required?                    true
        Position?                    Named
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -SignedRemovalPackageFolder <String>
        Full path to directory containing spkrs available to include in
        submission .zip.

        Required?                    false
        Position?                    Named
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -PackagesToRemoveFolder <String>
        Full path to directory containing spkgs for which spkrs need to be
        generated and submitted.

        Required?                    false
        Position?                    Named
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -Baseline
        Indicates that the submission should be marked as baseline, which make this submission eligible for retail
        servicing updates.

        Required?                    false
        Position?                    Named
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -FfuPath <String>
        Full path to an FFU file that contains the FFU catalog to be submitted
        for code signing.  This parameter is only used for a FfuCatalog
        submission.

        Required?                    true
        Position?                    Named
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -PartialImageDirectory <String>
        Full path to a directory containing a partial image that consists of
        only SPKG files.  This parameter is only used for a PartialImage
        submission.

        Required?                    true
        Position?                    Named
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information,
    see
        about_CommonParameters
    (http://go.microsoft.com/fwlink/p/?linkid=113216).

INPUTS



OUTPUTS
    .NET FileInfo object.

        .NET FileInfo object contains submission .zip ready to submit for code
        signing.

NOTES
    --------------  Non-baseline image submission example.  --------------

    PS C:\> Initialize-FirmwareSubmission -TypeOfProduct WindowsPhoneBlue -TypeOfSubmission Image -UpdateHistoryPath
    c:\input -OemInputPath c:\input -OutputFilePath c:\output





    --------------  Baseline image submission example.  --------------

    PS C:\> Initialize-FirmwareSubmission -TypeOfProduct WindowsPhoneThreshold -TypeOfSubmission Image
    -UpdateHistoryPath c:\input -OemInputPath c:\input -OutputFilePath c:\output -baseline





    --------------  FFU catalog submission example.  --------------

    PS C:\> Initialize-FirmwareSubmission -TypeOfProduct WindowsPhoneThreshold
            -TypeOfSubmission FfuCatalog -UpdateHistoryPath c:\input -OemInputPath
            c:\input -OutputFilePath c:\output -FfuPath c:\input\flash.ffu




    --------------  Partial image submission example.  --------------

    PS C:\> Initialize-FirmwareSubmission -TypeOfProduct WindowsPhoneBlue
            -TypeOfSubmission PartialImage -UpdateHistoryPath c:\input -OemInputPath
            c:\input -OutputFilePath c:\output -PartialImageDirectory c:\input\spkg




    --------------  Print usage text example.  --------------

    PS C:\> Initialize-FirmwareSubmission


RELATED LINKS
```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[零售映像的 Windows 标准包装配置 (WSPC) 要求](https://msdn.microsoft.com/library/dn756781)

[新 FirmwareSubmission cmdlet](new-firmwaresubmission-cmdlet.md)

[提交要零售签名的二进制文件](https://msdn.microsoft.com/library/windows/hardware/dn789223)

 

 






