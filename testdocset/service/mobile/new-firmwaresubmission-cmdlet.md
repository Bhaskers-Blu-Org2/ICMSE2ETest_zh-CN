---
author: kpacquer
Description: "新 FirmwareSubmission cmdlet"
ms.assetid: f2a9e48c-a046-466b-8cfb-661e3bae88a8
MSHAttr: PreferredLib:/library/windows/hardware
title: "新 FirmwareSubmission cmdlet"
ms.openlocfilehash: 5cf1b44cd61e2dc53ade61d4d21e27947b8bd539
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="new-firmwaresubmission-cmdlet"></a>新 FirmwareSubmission cmdlet


使用**New FirmwareSubmission** cmdlet 以创建新的固件提交并上载包含有效负载的 zip 文件。

这是**新 FirmwareSubmission**的语法︰

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>语法


``` syntax
NAME
    New-FirmwareSubmission
SYNOPSIS
    Creates a new firmware submission.
SYNTAX
    New-FirmwareSubmission [-Path] <String>
    [-ServiceUri <Uri>]
    [-CertificateStoreLocation <StoreLocation>]
    [-CertificateStoreName <StoreName>]
    [-ClientCertificateThumbprint <String>]
    [-EncryptionCertificateThumbprint <String>]
    [<CommonParameters>]
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>参数


通常情况下，指定在此 cmdlet 的唯一参数是准备好的提交 zip 文件的路径。

## <a name="span-idscenariosspanspan-idscenariosspanspan-idscenariosspanscenarios"></a><span id="Scenarios"></span><span id="scenarios"></span><span id="SCENARIOS"></span>方案


### <a name="span-idcreateanewfirmwaresubmissionspanspan-idcreateanewfirmwaresubmissionspanspan-idcreateanewfirmwaresubmissionspancreate-a-new-firmware-submission"></a><span id="Create_a_new_firmware_submission"></span><span id="create_a_new_firmware_submission"></span><span id="CREATE_A_NEW_FIRMWARE_SUBMISSION"></span>创建新的固件提交

### <a name="span-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanscenario-prerequisites"></a><span id="Scenario_prerequisites"></span><span id="scenario_prerequisites"></span><span id="SCENARIO_PREREQUISITES"></span>方案的前提条件

-   使用固件负载创建 zip 文件。 有关详细信息，请参阅[初始化 FirmwareSubmission cmdlet](initialize-firmwaresubmission-cmdlet.md)。

### <a name="span-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanexample-usage-with-expected-output"></a><span id="Example_usage_with_expected_output"></span><span id="example_usage_with_expected_output"></span><span id="EXAMPLE_USAGE_WITH_EXPECTED_OUTPUT"></span>与预期的输出的示例用法

申请新固件提交，并将结果对象存储在一个名为 $result 的 PowerShell 变量︰

``` syntax
PS> $result=New-FirmwareSubmission -path C:\Data1\TESTOEM1-MS.TKT-SIGN-TEST-M3ZABC.zip
```

在控制台上显示结果︰

``` syntax
PS> $result | Format-List

FirmwareSubmissionTicketId : TKT-SIGN-TEST-761234    
```

### <a name="span-idattempttocreateanewfirmwaresubmissionwithamissingfilespanspan-idattempttocreateanewfirmwaresubmissionwithamissingfilespanspan-idattempttocreateanewfirmwaresubmissionwithamissingfilespanattempt-to-create-a-new-firmware-submission-with-a-missing-file"></a><span id="Attempt_to_create_a_new_firmware_submission_with_a_missing_file"></span><span id="attempt_to_create_a_new_firmware_submission_with_a_missing_file"></span><span id="ATTEMPT_TO_CREATE_A_NEW_FIRMWARE_SUBMISSION_WITH_A_MISSING_FILE"></span>尝试使用丢失的文件创建新的固件提交

### <a name="span-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanscenario-prerequisites"></a><span id="Scenario_prerequisites"></span><span id="scenario_prerequisites"></span><span id="SCENARIO_PREREQUISITES"></span>方案的前提条件

-   OEM 试图用缺少文件创建固件提交。

### <a name="span-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanexample-usage-with-expected-output"></a><span id="Example_usage_with_expected_output"></span><span id="example_usage_with_expected_output"></span><span id="EXAMPLE_USAGE_WITH_EXPECTED_OUTPUT"></span>与预期的输出的示例用法

尝试检索签名仍在进行一个票证提交︰

``` syntax
PS> $result=New-FirmwareSubmission -path C:\Data1\TESTOEM1-MS.TKT-SIGN-TEST-NOT-HERE.zip
```

``` syntax
PS C:\windows\system32> $result=New-FirmwareSubmission -path C:\Data1\TESTOEM1-M
S.TKT-SIGN-TEST-NOT-HERE.zip
New-FirmwareSubmission : File
'C:\Data1\TESTOEM1-MS.TKT-SIGN-TEST-NOT-HERE.zip' does not exist.
At line:1 char:9
+ $result=New-FirmwareSubmission -path
C:\Data1\TESTOEM1-MS.TKT-SIGN-TEST-NOT-HERE ...
+
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [New-FirmwareSubmission], A
   rgumentException
    + FullyQualifiedErrorId : System.ArgumentException,Microsoft.Phone.Partner
   Services.Cmdlets.NewFirmwareSubmissionCommand
            
```

## <a name="span-idhelpdocumentationfromwindowspowershellspanspan-idhelpdocumentationfromwindowspowershellspanspan-idhelpdocumentationfromwindowspowershellspanhelp-documentation-from-windows-powershell"></a><span id="Help_documentation_from_Windows_PowerShell"></span><span id="help_documentation_from_windows_powershell"></span><span id="HELP_DOCUMENTATION_FROM_WINDOWS_POWERSHELL"></span>从 Windows PowerShell 的帮助文档


以下是从 Windows PowerShell**新建 FirmwareSubmission** cmdlet 的帮助文档。

``` syntax
PS C:\Windows\system32> get-help New-FirmwareSubmission -full

NAME
    New-FirmwareSubmission

SYNOPSIS
    Creates a new firmware submission.

SYNTAX
    New-FirmwareSubmission [-Path] <String> [-ServiceUri <Uri>]
    [-ServiceAccessControlNamespace <String>] [-CertificateStoreLocation
    <StoreLocation>] [-CertificateStoreName <StoreName>]
    [-ClientCertificateThumbprint <String>] [-EncryptionCertificateThumbprint
    <String>] [<CommonParameters>]


DESCRIPTION
    Creates a new firmware submission and uploads the file containing the
    payload.


PARAMETERS
    -Path <String>
        The full path to file containing the firmware-submission to be
        uploaded.

        Required?                    true
        Position?                    2
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -ServiceUri <Uri>


        Required?                    false
        Position?                    named
        Default value
        Accept pipeline input?       false
        Accept wildcard characters?  false

    -ServiceAccessControlNamespace <String>
        The namespace for Partner Services Access Control. The default value
        for this parameter is read from the configuration file. Should only be
        modified if instructed by the system administrator or Microsoft.

        Required?                    false
        Position?                    named
        Default value
        Accept pipeline input?       false
        Accept wildcard characters?  false

    -CertificateStoreLocation <StoreLocation>


        Required?                    false
        Position?                    named
        Default value
        Accept pipeline input?       false
        Accept wildcard characters?  false

    -CertificateStoreName <StoreName>


        Required?                    false
        Position?                    named
        Default value
        Accept pipeline input?       false
        Accept wildcard characters?  false

    -ClientCertificateThumbprint <String>


        Required?                    false
        Position?                    named
        Default value
        Accept pipeline input?       false
        Accept wildcard characters?  false

    -EncryptionCertificateThumbprint <String>


        Required?                    false
        Position?                    named
        Default value
        Accept pipeline input?       false
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
    FirmwareSubmission

        Contains the firmware submission ticket Id

NOTES


RELATED LINKS

PS C:\Windows\system32>
```

## <a name="span-idtroubleshootingspanspan-idtroubleshootingspanspan-idtroubleshootingspantroubleshooting"></a><span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>故障排除


错误消息︰

``` syntax
New-FirmwareSubmission : An error has occurred. There was no endpoint
    listening at http://wp8partnerservicesv1.cloudapp.net:7159/Firmware.svc that
    could accept the message. This is often caused by an incorrect address or SOAP
```

常见的原因︰ 公司网络网关配置不允许您连接到 Microsoft 签名服务器。

解决方案︰ 请与您的 IT 管理部门打开或重新配置的网络端口。

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>要求


**标头︰**无

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[提交要零售签名的二进制文件](https://msdn.microsoft.com/library/windows/hardware/dn789223)

 

 






