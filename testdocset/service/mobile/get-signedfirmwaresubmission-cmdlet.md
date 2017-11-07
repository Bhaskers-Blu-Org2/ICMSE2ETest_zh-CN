---
author: kpacquer
Description: "获得 SignedFirmwareSubmission cmdlet"
ms.assetid: 911d3704-0508-4aae-8236-59cfd380867b
MSHAttr: PreferredLib:/library/windows/hardware
title: "获得 SignedFirmwareSubmission cmdlet"
ms.openlocfilehash: ec94ca2379643afdd80024bf3575b272ba82998d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="get-signedfirmwaresubmission-cmdlet"></a>获得 SignedFirmwareSubmission cmdlet


给 Microsoft 在成功提交后，可以检索代码签名固件。 如果提交成功，OEM 接收票证编号。 使用**Get SignedFirmwareSubmission** cmdlet 来检索为代码注册证号的签名的提交。

以下是**获取 SignedFirmwareSubmission** cmdlet 的语法。

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>语法


``` syntax
NAME
     Get-SignedFirmwareSubmission
SYNTAX
     Get-SignedFirmwareSubmission
      [-TicketId] <string>
      [[-DownloadDirectory] <string>]
      [-ServiceUri <uri>]
      [-CertificateStoreLocation <StoreLocation> {CurrentUser | LocalMachine}]
      [-CertificateStoreName <StoreName> {AddressBook | AuthRoot | CertificateAuthority
         | Disallowed | My | Root | TrustedPeople | TrustedPublisher}]
      [-ClientCertificateThumbprint <string>]
      [-EncryptionCertificateThumbprint <string>]
      [<CommonParameters>]
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>参数


通常情况下，为此 cmdlet 指定的唯一参数是**票证 Id**和**DownloadDirectory**。

该 cmdlet 从配置文件获取其他参数的默认的值。 默认情况下，此配置文件放置在安装程序: %programfiles(x86)%\\Microsoft\\WP 接收客户端\\模块\\Microsoft.Phone.PartnerServices.Client\\ Microsoft.Phone.PartnerServices.Client.dll.config

在本文档的配置文件一节中提供了示例配置文件。

如果在命令行上显式指定的任何非必需参数，这些值将覆盖存储在配置文件中的默认值。

为了支持 Windows PowerShell 自动化脚本，该 cmdlet 返回的类型对象`Microsoft.Phone.PartnerServices.SignedFirmwareSubmission`:

``` syntax
TypeName: Microsoft.Phone.PartnerServices.SignedFirmwareSubmission

Name        MemberType Definition
----        ---------- ----------
Equals      Method     bool Equals(System.Object obj)
GetHashCode Method     int GetHashCode()
GetType     Method     type GetType()
ToString    Method     string ToString()
File        Property   System.IO.FileInfo File {get;set;}
FirmwareSubmissionTicketId    Property   string TicketId {get;set;}
```

使用 Windows PowerShell 或在命令行上显示，可处理此对象。 以下部分显示了常见的使用方案和常见的错误情况，用于检索签名提交。

**请注意**  
其中的许多命令如下所示为多行，但必须按中 Windows PowerShell 的单行输入。

 

## <a name="span-idexceptionsspanspan-idexceptionsspanspan-idexceptionsspanexceptions"></a><span id="Exceptions"></span><span id="exceptions"></span><span id="EXCEPTIONS"></span>例外情况


对其相应的错误情形引发以下异常。

<span id="FaultException_ArgumentFaultDetail_"></span><span id="faultexception_argumentfaultdetail_"></span><span id="FAULTEXCEPTION_ARGUMENTFAULTDETAIL_"></span>**FaultException&lt;ArgumentFaultDetail&gt;**  
-   提供的票证无效 ID。 票证 ID 为 null 或为空。

<span id="FaultException_InvalidOperationFaultDetail_"></span><span id="faultexception_invalidoperationfaultdetail_"></span><span id="FAULTEXCEPTION_INVALIDOPERATIONFAULTDETAIL_"></span>**FaultException&lt;InvalidOperationFaultDetail&gt;**  
-   提供的票证无效 ID。

-   在服务中未定义的票证 ID。

-   已验证身份的用户不是所有者的固件提交。

-   票证 ID 是重新提交票证。

-   代码签名是仍在进行。

-   代码签名是挂起的来自 Microsoft 的手动干预。 不需要任何 OEM 操作。

-   代码签名失败。

## <a name="span-idscenariosspanspan-idscenariosspanspan-idscenariosspanscenarios"></a><span id="Scenarios"></span><span id="scenarios"></span><span id="SCENARIOS"></span>方案


### <a name="span-idretrieveasuccessfullysignedsubmissionspanspan-idretrieveasuccessfullysignedsubmissionspanspan-idretrieveasuccessfullysignedsubmissionspanretrieve-a-successfully-signed-submission"></a><span id="Retrieve_a_successfully_signed_submission"></span><span id="retrieve_a_successfully_signed_submission"></span><span id="RETRIEVE_A_SUCCESSFULLY_SIGNED_SUBMISSION"></span>检索成功签名的提交

### <a name="span-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanscenario-prerequisites"></a><span id="Scenario_prerequisites"></span><span id="scenario_prerequisites"></span><span id="SCENARIO_PREREQUISITES"></span>方案的前提条件

-   固件请求已成功提交的代码签名。

-   返回由固件请求提交票证才可用。

-   由 OEM 已收到指示已成功签名固件提交成功的电子邮件通知。

### <a name="span-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanexample-usage-with-expected-output"></a><span id="Example_usage_with_expected_output"></span><span id="example_usage_with_expected_output"></span><span id="EXAMPLE_USAGE_WITH_EXPECTED_OUTPUT"></span>与预期的输出的示例用法

检索一个票证的签名的提交和 Windows PowerShell 变量中存储的结果对象︰

``` syntax
PS> $result = Get-SignedFirmwareSubmission –FirmwareSubmissionTicketId TKT-SIGN-TEST-BTUADL 
-DownloadDirectory C:\temp
```

在控制台上显示结果︰

``` syntax
PS> $result | Format-List

TicketId : TKT-SIGN-TEST-BTUADL
File     : c:\temp\OemTest.TKT-SIGN-TEST-BTUADL.zip
```

### <a name="span-idattempttoretrieveasignedfirmwaresubmissionbeforecompletionspanspan-idattempttoretrieveasignedfirmwaresubmissionbeforecompletionspanspan-idattempttoretrieveasignedfirmwaresubmissionbeforecompletionspanattempt-to-retrieve-a-signed-firmware-submission-before-completion"></a><span id="Attempt_to_retrieve_a_signed_firmware_submission_before_completion"></span><span id="attempt_to_retrieve_a_signed_firmware_submission_before_completion"></span><span id="ATTEMPT_TO_RETRIEVE_A_SIGNED_FIRMWARE_SUBMISSION_BEFORE_COMPLETION"></span>尝试检索签名的固件提交完成之前

### <a name="span-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanscenario-prerequisites"></a><span id="Scenario_prerequisites"></span><span id="scenario_prerequisites"></span><span id="SCENARIO_PREREQUISITES"></span>方案的前提条件

-   固件请求已成功提交的代码签名。

-   返回由固件请求提交票证才可用。

-   签名过程的固件代码是仍在进行。 也就是说，颁发的票证，但尚未收到成功的电子邮件。

### <a name="span-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanexample-usage-with-expected-output"></a><span id="Example_usage_with_expected_output"></span><span id="example_usage_with_expected_output"></span><span id="EXAMPLE_USAGE_WITH_EXPECTED_OUTPUT"></span>与预期的输出的示例用法

尝试检索签名仍在进行一个票证提交︰

``` syntax
PS> Get-SignedFirmwareSubmission -FirmwareSubmissionTicketId TKT-SIGN-TEST-XD252Y 
-DownloadDirectory c:\temp
```

``` syntax
Get-SignedFirmwareSubmission : An error has occurred.  The request could not be processed because the operation is not
valid for the current state of service.
Details: Unable to retrieve the specified firmware submission. Reason: Code signing is still in progress.
Reason: FirmwareSubmissionIsInProgress.
Correlation: 4ab98c1a-df9c-40a9-ac6a-f9b1e9d42e87.
At line:1 char:1
+ Get-SignedFirmwareSubmission TKT-SIGN-TEST-06TV0O c:\temp -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Get-SignedFirmwareSubmission], FirmwareSubmissionInProgressExcept
   ion
    + FullyQualifiedErrorId : Microsoft.Phone.PartnerServices.Exceptions.FirmwareSubmissionInProgressException,Microso
   ft.Phone.PartnerServices.Cmdlets.GetSignedFirmwareSubmissionCommand            
```

此状态表示返回的原因，通过"代码签名是仍在进行"。

如果正在使用自定义的 PowerShell 脚本，它可以进行编程，以捕获异常 (Microsoft.Phone.PartnerServices.Exceptions.FirmwareSubmissionInProgressException)。 该异常可以进行检查，以确定是否已完成提交。 下面的代码示例演示了如何从返回的结果对象中提取信息的错误。

``` syntax
      $result = ''
        try {
            $result = Get-SignedFirmwareSubmission -FirmwareSubmissionTicketId "TKT-SIGN-TEST-17Y8M5" -DownloadDirectory c:\MyFirmwareSubmissions
        }
        catch [Microsoft.Phone.PartnerServices.Exceptions.FirmwareSubmissionInProgressException] {
            write-host "Error Message" + $_.Exception.Message
            write-host "Error Detail" + $_.Exception.Detail
            
            #exit or take other action since we've detected a failure
            exit 1
        } 
```

可以构造一个循环来等待 （至少 30 分钟），然后尝试确定是否已完成提交。 强烈建议您不必须会轮询样式调用使用少于 30 分钟，以避免急剧更新服务器的时间间隔。

### <a name="span-idattempttoretrieveasignedfirmwaresubmissionwhentherequesthasfailedspanspan-idattempttoretrieveasignedfirmwaresubmissionwhentherequesthasfailedspanspan-idattempttoretrieveasignedfirmwaresubmissionwhentherequesthasfailedspanattempt-to-retrieve-a-signed-firmware-submission-when-the-request-has-failed"></a><span id="Attempt_to_retrieve_a_signed_firmware_submission_when_the_request_has_failed"></span><span id="attempt_to_retrieve_a_signed_firmware_submission_when_the_request_has_failed"></span><span id="ATTEMPT_TO_RETRIEVE_A_SIGNED_FIRMWARE_SUBMISSION_WHEN_THE_REQUEST_HAS_FAILED"></span>尝试检索签名的固件提交请求失败时

### <a name="span-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanscenario-prerequisites"></a><span id="Scenario_prerequisites"></span><span id="scenario_prerequisites"></span><span id="SCENARIO_PREREQUISITES"></span>方案的前提条件

-   固件请求已成功提交的代码签名。

-   返回由固件请求提交票证才可用。

-   签名过程的固件代码永久失败。 也就是说，票证的 oem 已收到失败的电子邮件通知。

### <a name="span-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanexample-usage-with-expected-output"></a><span id="Example_usage_with_expected_output"></span><span id="example_usage_with_expected_output"></span><span id="EXAMPLE_USAGE_WITH_EXPECTED_OUTPUT"></span>与预期的输出的示例用法

尝试检索签名的提交永久失败一个票证︰

``` syntax
PS> Get-SignedFirmwareSubmission -FirmwareSubmissionTicketId TKT-SIGN-TEST-TUKJGG -DownloadDirectory c:\temp
```

``` syntax
Get-SignedFirmwareSubmission : An error has occurred.  The request could not be
processed because the operation is not valid for the current state of service.
Details: Unable to retrieve the specified firmware submission. Reason: Code
signing has failed.
Reason: FirmwareSubmissionHasFailed.
Correlation: 67a645af-19b7-468d-9f7a-4a3fd341a15e.
At line:1 char:11
+ $result = Get-SignedFirmwareSubmission -FirmwareSubmissionTicketId
TKT-SIGN-TEST ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
~~~
    + CategoryInfo          : InvalidOperation: (:) [Get-SignedFirmwareSubmiss
   ion], FirmwareSubmissionFailedException
    + FullyQualifiedErrorId : Microsoft.Phone.PartnerServices.Exceptions.Firmw
   areSubmissionFailedException,Microsoft.Phone.PartnerServices.Cmdlets.GetSi
  gnedFirmwareSubmissionCommand
```

### <a name="span-idattempttoretrieveasignedfirmwaresubmissionwhentheticketdoesnotexistspanspan-idattempttoretrieveasignedfirmwaresubmissionwhentheticketdoesnotexistspanspan-idattempttoretrieveasignedfirmwaresubmissionwhentheticketdoesnotexistspanattempt-to-retrieve-a-signed-firmware-submission-when-the-ticket-does-not-exist"></a><span id="Attempt_to_retrieve_a_signed_firmware_submission_when_the_ticket_does_not_exist"></span><span id="attempt_to_retrieve_a_signed_firmware_submission_when_the_ticket_does_not_exist"></span><span id="ATTEMPT_TO_RETRIEVE_A_SIGNED_FIRMWARE_SUBMISSION_WHEN_THE_TICKET_DOES_NOT_EXIST"></span>尝试检索签名的固件提交票证不存在时

### <a name="span-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanscenario-prerequisites"></a><span id="Scenario_prerequisites"></span><span id="scenario_prerequisites"></span><span id="SCENARIO_PREREQUISITES"></span>方案的前提条件

-   OEM 尝试检索不存在票据编号。

### <a name="span-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanexample-usage-with-expected-output"></a><span id="Example_usage_with_expected_output"></span><span id="example_usage_with_expected_output"></span><span id="EXAMPLE_USAGE_WITH_EXPECTED_OUTPUT"></span>与预期的输出的示例用法

``` syntax
PS> Get-SignedFirmwareSubmission -FirmwareSubmissionTicketId bad_ticket_number -DownloadDirectory c:\temp
```

``` syntax
Get-SignedFirmwareSubmission : An error has ocurred.  The request could not be
processed because the operation is not valid for the current state of service.
Details: The specified FirmwareSubmission ticket does not exist.
Reason: TicketDoesNotExist.
Correlation: fd8bb041-fe0f-46ea-9b89-ccf91a57178c.
At line:1 char:11
+ $result = Get-SignedFirmwareSubmission -FirmwareSubmissionTicketId
TKT-SIGN-TEST ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
~~~
    + CategoryInfo          : InvalidOperation: (:) [Get-SignedFirmwareSubmiss
   ion], TicketDoesNotExistException
    + FullyQualifiedErrorId : Microsoft.Phone.PartnerServices.Exceptions.Ticke
   tDoesNotExistException,Microsoft.Phone.PartnerServices.Cmdlets.GetSignedFi
  rmwareSubmissionCommand
```

## <a name="span-idhelpdocumentationfrompowershellspanspan-idhelpdocumentationfrompowershellspanspan-idhelpdocumentationfrompowershellspanhelp-documentation-from-powershell"></a><span id="Help_documentation_from_PowerShell"></span><span id="help_documentation_from_powershell"></span><span id="HELP_DOCUMENTATION_FROM_POWERSHELL"></span>从 PowerShell 的帮助文档


以下是从 Windows PowerShell **Get SignedFirmwareSubmission** cmdlet 的帮助文档。

``` syntax
NAME
    Get-SignedFirmwareSubmission

SYNOPSIS
    Gets a signed firmware submission for a given firmware submission ticket.

SYNTAX
    Get-SignedFirmwareSubmission [-FirmwareSubmissionTicketId] <String>
    [[-DownloadDirectory] <String>] [-ServiceUri <Uri>]
    [-ServiceAccessControlNamespace <String>] [-CertificateStoreLocation
    <StoreLocation>] [-CertificateStoreName <StoreName>]
    [-ClientCertificateThumbprint <String>] [-EncryptionCertificateThumbprint
    <String>] [<CommonParameters>]


DESCRIPTION
    Downloads a signed firmware submission for a given ticket id.

            The download can only be performed after a new firmware submission
    has been created and uploaded with the OemSubmit tool or WP Ingestion
    Client and the uploaded files have been signed by Microsoft. Otherwise it
    will throw an error.


PARAMETERS
    -FirmwareSubmissionTicketId <String>
        Firmware-Submission ticket. Must be a valid ticket.

        Required?                    true
        Position?                    2
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -DownloadDirectory <String>
        The download directory for the signed firmware-submission. Must be a
        full path to the download directory.

                    A default value can be defined in the configuration file.

        Required?                    false
        Position?                    3
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -ServiceUri <Uri>
        The service URI. The default value for this parameter is read from the
        configuration file.

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
        The certificate store location. The default value for this parameter
        is read from the configuration file.

        Required?                    false
        Position?                    named
        Default value
        Accept pipeline input?       false
        Accept wildcard characters?  false

    -CertificateStoreName <StoreName>
        The certificate store name. The default value for this parameter is
        read from the configuration file.

        Required?                    false
        Position?                    named
        Default value
        Accept pipeline input?       false
        Accept wildcard characters?  false

    -ClientCertificateThumbprint <String>
        The client certificate thumbprint. The default value for this
        parameter is read from the configuration file. Should only be modified
        if instructed by the system administrator or Microsoft

        Required?                    false
        Position?                    named
        Default value
        Accept pipeline input?       false
        Accept wildcard characters?  false

    -EncryptionCertificateThumbprint <String>
        The encryption certificate thumbprint. The default value for this
        parameter is read from the configuration file.

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
    SignedFirmwareSubmission

        Contains information about the downloaded file and the firmware
        submission ticket related to the signing.

NOTES
    --------------  Example 1 --------------

    C:\PS>Get-SignedFirmwareSubmission -FirmwareSubmissionTicketId
    TKT-SIGN-PROD-ABCDEF -DownloadDirectory
    C:\SignedFirmwareSubmissionDownloads | Format-List


    Successful download of a signed firmware-submission read for download.

                The ticket id is TKT-SIGN-PROD-ABCDEF and the zip-file is
    downloaded to directory C:\SignedFirmwareSubmissionDownloads.



    FirmwareSubmissionTicketId : TKT-SIGN-PROD-ABCDEF
                File     :
    c:\SignedFirmwareSubmissionDownloads\OemTest.TKT-SIGN-PROD-ABCDEF.zip

RELATED LINKS
```

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>要求


**标头︰**无

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[提交要零售签名的二进制文件](https://msdn.microsoft.com/library/windows/hardware/dn789223)

 

 






