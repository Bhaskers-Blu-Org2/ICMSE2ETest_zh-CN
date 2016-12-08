---
author: kpacquer
Description: "获得 RequestForUpdate cmdlet"
ms.assetid: f2b86f24-b5ff-4c9d-ac46-66898ad79e8c
MSHAttr: PreferredLib:/library/windows/hardware
title: "获得 RequestForUpdate cmdlet"
ms.openlocfilehash: f4588cc4658c7e8114eb8f875b6e412b72d62a71
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="get-requestforupdate-cmdlet"></a>获得 RequestForUpdate cmdlet


使用**Get RequestForUpdate** cmdlet 来检索更新请求的当前状态。

这是**获取 RequestForUpdate**的语法。

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>语法


``` syntax
NAME
     Get-RequestForUpdate
SYNTAX
     Get-RequestForUpdate
      [-RequestForUpdateTicketId] <string> 
      [-ServiceUri <uri>]
      [-ServiceAccessControlNamespace <string>]
      [-CertificateStoreLocation <StoreLocation> {CurrentUser | LocalMachine}]
      [-CertificateStoreName <StoreName> {AddressBook | AuthRoot | CertificateAuthority
          | Disallowed | My | Root | TrustedPeople | TrustedPublisher}]
      [-ClientCertificateThumbprint <string>]
      [-EncryptionCertificateThumbprint <string>]
      [<CommonParameters>]
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>参数


通常情况下，指定给此 cmdlet 的唯一参数是**RequestForUpdateTicketId**。

## <a name="span-idoutputspanspan-idoutputspanspan-idoutputspanoutput"></a><span id="Output"></span><span id="output"></span><span id="OUTPUT"></span>输出


此 cmdlet 返回一个 Microsoft.Phone.PartnerServices.Cmdlets.RequestForUpdate 对象，该对象包含以下字段。

<span id="Status"></span><span id="status"></span><span id="STATUS"></span>**状态**  
这是 RFU 提交的进度。 以下是状态字段的成员。

-   **错误代码**。 这是所遇到的错误的错误代码。

-   **ErrorMessage**。 此属性包含受到与 RFU 提交失败。

-   **状态**。 此列表包含当前 RFU 提交的状态状态。 下面的列表包含的状态。

    -   **InProcessOnTrack**。 RFU 提交，目前正在进行中。

    -   **InProcessFailure**。 RFU 提交已完成但有错误;但是，用户仍可以选择重试。

    -   **CompletedFailure**。 RFU 提交已完成但有错误，并且用户不选择重试。

    -   **CompletedSuccess**。 RFU 提交已完成没有任何问题。

    -   **FailedToRetrieveStatus**。 这意味着状态计算失败。 ErrorMessage 在这种情况下是"出错时检索 RFU 状态。 OEM 不需要执行任何操作。 Microsoft 将会调查问题导致此。"

## <a name="span-idexceptionsspanspan-idexceptionsspanspan-idexceptionsspanexceptions"></a><span id="Exceptions"></span><span id="exceptions"></span><span id="EXCEPTIONS"></span>例外情况


对其相应的错误情形引发以下异常。

<span id="FaultException_ArgumentFaultDetail_"></span><span id="faultexception_argumentfaultdetail_"></span><span id="FAULTEXCEPTION_ARGUMENTFAULTDETAIL_"></span>**FaultException&lt;ArgumentFaultDetail&gt;**  
-   提供的票证无效 ID。 票证 ID 为 null 或为空。

<span id="FaultException_InvalidOperationFaultDetail_"></span><span id="faultexception_invalidoperationfaultdetail_"></span><span id="FAULTEXCEPTION_INVALIDOPERATIONFAULTDETAIL_"></span>**FaultException&lt;InvalidOperationFaultDetail&gt;**  
-   提供的票证无效 ID。 在服务中未定义的票证 ID。

-   已验证身份的用户不是所有者的固件提交。

-   票证 ID 是重新提交票证。

## <a name="span-idscenariosspanspan-idscenariosspanspan-idscenariosspanscenarios"></a><span id="Scenarios"></span><span id="scenarios"></span><span id="SCENARIOS"></span>方案


### <a name="span-idretrievethestatusofasuccessfullyprocessedrequestforupdatespanspan-idretrievethestatusofasuccessfullyprocessedrequestforupdatespanspan-idretrievethestatusofasuccessfullyprocessedrequestforupdatespanretrieve-the-status-of-a-successfully-processed-request-for-update"></a><span id="Retrieve_the_status_of_a_successfully_processed_request_for_update"></span><span id="retrieve_the_status_of_a_successfully_processed_request_for_update"></span><span id="RETRIEVE_THE_STATUS_OF_A_SUCCESSFULLY_PROCESSED_REQUEST_FOR_UPDATE"></span>检索更新已成功处理请求的状态

### <a name="span-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanscenario-prerequisites"></a><span id="Scenario_prerequisites"></span><span id="scenario_prerequisites"></span><span id="SCENARIO_PREREQUISITES"></span>方案的前提条件

-   已成功提交更新请求。

-   更新证号的请求是可用的。

### <a name="span-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanexample-usage-with-expected-output"></a><span id="Example_usage_with_expected_output"></span><span id="example_usage_with_expected_output"></span><span id="EXAMPLE_USAGE_WITH_EXPECTED_OUTPUT"></span>与预期的输出的示例用法

检索更新的状态，并将结果对象存储在一个名为 $result 的 PowerShell 变量︰

``` syntax
PS> $result = Get-RequestForUpdate -RequestForUpdateTicketId TKT-SIGN-TEST-FO03ST-1
```

在控制台上显示结果︰

``` syntax
PS> $result | Format-List

Ticket             : TKT-SIGN-TEST-FO03ST-1
RfuType            : Trial
IsApproved         : False
CreatedOn          : 7/18/2013 5:22:44 PM
ModifiedOn         : 7/18/2013 5:22:45 PM
FirmwareSubmission : Microsoft.Phone.PartnerServices.Rfu.FirmwareSubmission
Pop                : Microsoft.Phone.PartnerServices.Rfu.Pop
Bundles            :
Attachments        :
Operations         : {Microsoft.Phone.PartnerServices.Rfu.RequestForUpdateOpera
                     tion}
ExtensionData      : System.Runtime.Serialization.ExtensionDataObjectFile    
```

在控制台上显示导致的状态︰

``` syntax
PS> $result.Status

## StatusErrorCodeErrorMessageExtensionData

InProcessOnTrack    System.Runtime.Serializati... 
```

### <a name="span-idattempttoretrievethestatusforanrfuwhentheticketdoesnotexistspanspan-idattempttoretrievethestatusforanrfuwhentheticketdoesnotexistspanspan-idattempttoretrievethestatusforanrfuwhentheticketdoesnotexistspanattempt-to-retrieve-the-status-for-an-rfu-when-the-ticket-does-not-exist"></a><span id="Attempt_to_retrieve_the_status_for_an_RFU_when_the_ticket_does_not_exist"></span><span id="attempt_to_retrieve_the_status_for_an_rfu_when_the_ticket_does_not_exist"></span><span id="ATTEMPT_TO_RETRIEVE_THE_STATUS_FOR_AN_RFU_WHEN_THE_TICKET_DOES_NOT_EXIST"></span>尝试检索状态 RFU 票证不存在时

### <a name="span-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanscenario-prerequisites"></a><span id="Scenario_prerequisites"></span><span id="scenario_prerequisites"></span><span id="SCENARIO_PREREQUISITES"></span>方案的前提条件

-   OEM 在尝试检索不存在 RFU 证号。

### <a name="span-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanexample-usage-with-expected-output"></a><span id="Example_usage_with_expected_output"></span><span id="example_usage_with_expected_output"></span><span id="EXAMPLE_USAGE_WITH_EXPECTED_OUTPUT"></span>与预期的输出的示例用法

尝试检索签名仍在进行一个票证提交︰

``` syntax
PS> $result = Get-RequestForUpdate –RequestForUpdateTicketId TKT-SIGN-TEST-NONONO
```

``` syntax
Get-RequestForUpdate : An error has ocurred.  The request could not be
processed because operation is not valid for current state of service.
Details: The specified RequestForUpdate ticket does not exist.
Reason: TicketDoesNotExist.
Correlation: 994c438c-a6e1-44eb-8f06-2cbfa6c097bb.
At line:1 char:11
+ $result = Get-RequestForUpdate -RequestForUpdateTicketId TKT-SIGN-TEST-NONONO
+           ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Get-RequestForUpdate], Ti
   cketDoesNotExistException
    + FullyQualifiedErrorId : Microsoft.Phone.PartnerServices.Exceptions.Ticke
   tDoesNotExistException,Microsoft.Phone.PartnerServices.Cmdlets.GetRequestF
  orUpdateCommand            
```

## <a name="span-idhelpdocumentationfrompowershellspanspan-idhelpdocumentationfrompowershellspanspan-idhelpdocumentationfrompowershellspanhelp-documentation-from-powershell"></a><span id="Help_documentation_from_PowerShell"></span><span id="help_documentation_from_powershell"></span><span id="HELP_DOCUMENTATION_FROM_POWERSHELL"></span>从 PowerShell 的帮助文档


以下是从 Windows PowerShell **Get RequestForUpdate** cmdlet 的帮助文档。

``` syntax
PS C:\Windows\system32> get-help get-requestforupdate -full

NAME
    Get-RequestForUpdate

SYNOPSIS
    Gets the status of a current request for update.

SYNTAX
    Get-RequestForUpdate [-RequestForUpdateTicketId] <String> [-ServiceUri
    <Uri>] [-ServiceAccessControlNamespace <String>]
    [-CertificateStoreLocation <StoreLocation>] [-CertificateStoreName
    <StoreName>] [-ClientCertificateThumbprint <String>]
    [-EncryptionCertificateThumbprint <String>] [<CommonParameters>]


DESCRIPTION
    Gets the status of a current request for update. The request could be for
    a MicrosoftOemMixed or MicrosoftAKOnly update.


PARAMETERS
    -RequestForUpdateTicketId <String>
        The request for update ticket id.

        Required?                    true
        Position?                    2
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
        parameter is read from the configuration file.

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
    RequestForUpdate

        Provides detailed information of the request for update (RFU).



NOTES




    --------------  Example 1 --------------

    C:\PS>Get-RequestForUpdate -RequestForUpdateTicketId TKT-RFU-PROD-ABCD56-1


    Gets the status for a given RequestForUpdateTicketId



    Ticket             : TKT-RFU-PROD-ABCD56-1
                RfuType            : RetailServicing
                IsApproved         : False
                CreatedOn          : 6/29/2013 7:44:07 AM
                ModifiedOn         : 6/29/2013 7:44:08 AM
                FirmwareSubmission :
    Microsoft.Phone.PartnerServices.Rfu.FirmwareSubmission
                Pop                : Microsoft.Phone.PartnerServices.Rfu.Pop
                Bundles            :
                Attachments        :
                Operations         :
    {Microsoft.Phone.PartnerServices.Rfu.RequestForUpdateOperation}
                ExtensionData      :
    System.Runtime.Serialization.ExtensionDataObject




RELATED LINKS



PS C:\Windows\system32>NAME
    Get-RequestForUpdate

SYNOPSIS
    Gets the status of a current request for update.

SYNTAX
    Get-RequestForUpdate [-RequestForUpdateTicketId] <String> 
    [-ServiceUri <Uri>] 
    [-CertificateStoreLocation <StoreLocation>] 
    [-CertificateStoreName <StoreName>] 
    [-ClientCertificateThumbprint <String>]
    [-EncryptionCertificateThumbprint <String>]
    [<CommonParameters>]

DESCRIPTION
    Gets the status of a current request for update.


PARAMETERS
    -RequestForUpdateTicketId <String>
        The request for update ticket id.

        Required?                    true
        Position?                    2
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -ServiceUri <Uri>
        The service URI. The default value for this parameter is read from the configuration file. 

        Required?                    false
        Position?                    named
        Default value
        Accept pipeline input?       false
        Accept wildcard characters?  false

    -CertificateStoreLocation <StoreLocation>
        The certificate store location. The default value for this parameter is read from the configuration file.
        
        Required?                    false
        Position?                    named
        Default value
        Accept pipeline input?       false
        Accept wildcard characters?  false

    -CertificateStoreName <StoreName>
        The certificate store name. The default value for this parameter is read from the configuration file. 

        Required?                    false
        Position?                    named
        Default value
        Accept pipeline input?       false
        Accept wildcard characters?  false

    -ClientCertificateThumbprint <String>
        The client certificate thumbprint. The default value for this parameter is read from the configuration file.
        
        Required?                    false
        Position?                    named
        Default value
        Accept pipeline input?       false
        Accept wildcard characters?  false

    -EncryptionCertificateThumbprint <String>
        The encryption certificate thumbprint. The default value for this parameter is read from the configuration
        file. 
        Required?                    false
        Position?                    named
        Default value
        Accept pipeline input?       false
        Accept wildcard characters?  false

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, and OutVariable. For more information, see
        about_CommonParameters (http://go.microsoft.com/fwlink/p/?linkid=113216).

INPUTS



OUTPUTS
    RequestForUpdate

        Provides detailed information about the request for update (RFU).



NOTES




    --------------  Example 1 --------------

    C:\PS>Get-RequestForUpdate -RequestForUpdateTicketId TKT-RFU-PROD-ABCD56-1


    Gets the status for a given RequestForUpdateTicketId.



    Ticket             : TKT-RFU-PROD-ABCD56-1
    RfuType            : RetailServicing
    IsApproved         : False
    CreatedOn          : 6/29/2013 7:44:07 AM
    ModifiedOn         : 6/29/2013 7:44:08 AM
    FirmwareSubmission : Microsoft.Phone.PartnerServices.Rfu.FirmwareSubmission
    Pop                : Microsoft.Phone.PartnerServices.Rfu.Pop
    Bundles            :
    Attachments        :
    Operations         : 
{Microsoft.Phone.PartnerServices.Rfu.RequestForUpdateOperation}
    Status             : Microsoft.Phone.PartnerServices.Rfu.RfuStatusInfo
    ExtensionData      : System.Runtime.Serialization.ExtensionDataObject




RELATED LINKS
```

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>要求


**标头︰**无

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[提交更新](submit-an-update.md)

 

 






