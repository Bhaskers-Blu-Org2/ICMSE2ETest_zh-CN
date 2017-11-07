---
author: kpacquer
Description: "新 RequestForUpdate cmdlet"
ms.assetid: 8fef568e-4687-4862-ac7e-7a518ccbfe67
MSHAttr: PreferredLib:/library/windows/hardware
title: "新 RequestForUpdate cmdlet"
ms.openlocfilehash: b37cd9197912c2c6de92155d3604e19e009518d7
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="new-requestforupdate-cmdlet"></a>新 RequestForUpdate cmdlet


使用**New RequestForUpdate**来创建新的请求进行更新 (RFU) 根据一个给定的更新类型和固件提交票证 id。 固件提交必须成功进行签名。

可以创建 RFU 之前，您需要准备固件提交， **TypeOfSubmission**设置为**图像**中使用[初始化 FirmwareSubmission cmdlet](initialize-firmwaresubmission-cmdlet.md) 。 有关图像提交过程的详细信息，请参阅[提交二进制文件是零售签名](https://msdn.microsoft.com/library/windows/hardware/dn789223)。

**重要**  
提交对每个电话操作员单独 RFUs。 例如，如果您在特定移动操作员 (MO) 有两部电话，将需要提交两个 RFUs。 如果您有四个不同的 MOs 设备，您需要提交四个 RFUs。

 

这是**新 RequestForUpdate**的语法︰

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>语法


``` syntax
NAME
    New-RequestForUpdate
SYNTAX
    New-RequestForUpdate [-FirmwareSubmissionTicketId] <String>
    [-RequestForUpdateType] <RequestForUpdateType>
    [-SourceFirmwareSubmissionTicketId] <String>[[-OemDeviceName] <String>]
    [[-MOId] <String>]
    [-ServiceUri <Uri>]
    [-CertificateStoreLocation <StoreLocation>]
    [CertificateStoreName <StoreName>]
    [-ClientCertificateThumbprint <String>]
    [-EncryptionCertificateThumbprint <String>]
    [<CommonParameters>]
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>参数


通常情况下，为此 cmdlet 指定的唯一参数是**FirmwareSubmissionTicketId**、 **RequestForUpdateType**、 **SourceFirmwareSubmissionTicketId**、 **OemDeviceName**和**MOId**。

**FirmwareSubmissionTicketId**属性是与新 RFU 相关联的固件提交票证 ID 的 ID。

必须将**RequestForUpdateType**设置为这两个值之一︰

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">RequestForUpdateType</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>RetailServicing</p></td>
<td align="left"><p>由 Oem 用于使更新可通过无线 (OTA) 供 MOs 的实验室试验和技术验收。 在预览中的更新接收 OEM 审核 （投入） 后发布到发布的目标，根据实际生产环境。</p></td>
</tr>
<tr class="even">
<td align="left"><p>试用</p></td>
<td align="left"><p>由 Oem 用于 OTA 更新进行测试和评估他们 RFUs 提交的零售服务提交前的质量。 它还用于更新的 commercializing 新设备进行测试。</p>
<p>它不是供 MO 实验室试验。 在此处发布的更新做不被发布到 Microsoft 更新实际生产中。</p></td>
</tr>
</tbody>
</table>

 

**SourceFirmwareSubmissionTicketId**是从更新的固件提交设备 ID 的票证。 它只需要电话是否更新到 Windows Phone 8.1 或更高版本。 若要防止出现发布更新，可能导致更新错误，Windows Phone 设备更新发布服务有权拒绝不包括上一次更新**SourceFirmwareSubmissionTicketId**的 RFUs。 版本控制的详细信息，请参阅[更新的要求](update-requirements.md)。

**OemDeviceName**是为在目标更新请求的名称。 这只是所需设备是否更新到 Windows Phone 8.1 或更高版本。

**MOId**是移动运营商为目标的更新请求。

## <a name="span-idscenariocreateanewrfuforuseinretailservicingspanspan-idscenariocreateanewrfuforuseinretailservicingspanspan-idscenariocreateanewrfuforuseinretailservicingspanscenario-create-a-new-rfu-for-use-in-retail-servicing"></a><span id="Scenario__Create_a_new_RFU_for_use_in_retail_servicing"></span><span id="scenario__create_a_new_rfu_for_use_in_retail_servicing"></span><span id="SCENARIO__CREATE_A_NEW_RFU_FOR_USE_IN_RETAIL_SERVICING"></span>方案︰ 创建用于新 RFU 零售服务


### <a name="span-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanscenario-prerequisites"></a><span id="Scenario_prerequisites"></span><span id="scenario_prerequisites"></span><span id="SCENARIO_PREREQUISITES"></span>方案的前提条件

-   固件签名请求已成功提交。

-   固件签名请求票证编号是可用的。

-   没有提交新申请更新零售服务的愿望。

### <a name="span-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanexample-usage-with-expected-output"></a><span id="Example_usage_with_expected_output"></span><span id="example_usage_with_expected_output"></span><span id="EXAMPLE_USAGE_WITH_EXPECTED_OUTPUT"></span>与预期的输出的示例用法

请求新的更新，并将结果对象存储在一个名为 $result 的 Windows PowerShell 变量︰

``` syntax
$result = New-RequestForUpdate -FirmwareSubmissionTicketId TKT-SIGN-PROD-ABCD56 –RequestForUpdateType RetailServicing -SourceFirmwareSubmissionTicketId TKT-SIGN-PROD-XYZ123 -OemDeviceName P4301 -MOId 000-22
```

在控制台上显示结果︰

``` syntax
PS> $result | Format-List

Ticket             : TKT-SIGN-TEST-AB03ST-2
RfuType            : RetailServicing
IsApproved         : False
CreatedOn          : 7/18/2013 8:26:23 PM
ModifiedOn         : 7/18/2013 8:26:23 PM 
FirmwareSubmission : Microsoft.Phone.PartnerServices.Rfu.FirmwareSubmission
Pop                : Microsoft.Phone.PartnerServices.Rfu.Pop
Bundles            :
Attachments        :
Operations         : {Microsoft.Phone.PartnerServices.Rfu.RequestForUpdateOpera
                     tion}
ExtensionData      : System.Runtime.Serialization.ExtensionDataObjectFile      
```

## <a name="span-idscenarioattempttocreateanewrfuwhenthefirmwareticketdoesnotexistspanspan-idscenarioattempttocreateanewrfuwhenthefirmwareticketdoesnotexistspanspan-idscenarioattempttocreateanewrfuwhenthefirmwareticketdoesnotexistspanscenario-attempt-to-create-a-new-rfu-when-the-firmware-ticket-does-not-exist"></a><span id="Scenario__Attempt_to_create_a_new_RFU_when_the_firmware_ticket_does_not_exist"></span><span id="scenario__attempt_to_create_a_new_rfu_when_the_firmware_ticket_does_not_exist"></span><span id="SCENARIO__ATTEMPT_TO_CREATE_A_NEW_RFU_WHEN_THE_FIRMWARE_TICKET_DOES_NOT_EXIST"></span>方案︰ 尝试创建新 RFU 固件票证不存在时


### <a name="span-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanscenario-prerequisites"></a><span id="Scenario_prerequisites"></span><span id="scenario_prerequisites"></span><span id="SCENARIO_PREREQUISITES"></span>方案的前提条件

-   OEM 在尝试检索不存在 RFU 证号。

### <a name="span-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanexample-usage-with-expected-output"></a><span id="Example_usage_with_expected_output"></span><span id="example_usage_with_expected_output"></span><span id="EXAMPLE_USAGE_WITH_EXPECTED_OUTPUT"></span>与预期的输出的示例用法

``` syntax
$result = New-RequestForUpdate -FirmwareSubmissionTicketId TKT-SIGN-TEST-NONONO -RequestForUpdateType Trial -SourceFirmwareSubmissionTicketId TKT-SIGN-PROD-XYZ123 -OemDeviceName P4301 -MOId 000-22
```

``` syntax
New-RequestForUpdate : An error has ocurred.  The request could not be
processed because operation is not valid for current state of service.
Details: The specified FirmwareSubmission ticket does not exist.
Reason: TicketDoesNotExist.
Correlation: 05818963-a8f4-4d9f-9472-5257374549a9.
At line:1 char:11
+ $result = New-RequestForUpdate -FirmwareSubmissionTicketId
TKT-SIGN-TEST-NONONO  ...
```

## <a name="span-idhelpdocumentationfrompowershellspanspan-idhelpdocumentationfrompowershellspanspan-idhelpdocumentationfrompowershellspanhelp-documentation-from-powershell"></a><span id="Help_documentation_from_PowerShell"></span><span id="help_documentation_from_powershell"></span><span id="HELP_DOCUMENTATION_FROM_POWERSHELL"></span>从 PowerShell 的帮助文档


以下是从 Windows PowerShell**新建 RequestForUpdate** cmdlet 的帮助文档。

``` syntax
PS C:\Windows\system32> get-help New-RequestForUpdate -full

NAME
    New-RequestForUpdate

SYNOPSIS
    Creates a new request for update of OEM binaries only.

SYNTAX
    New-RequestForUpdate [-FirmwareSubmissionTicketId] <String>
    [-RequestForUpdateType] <RequestForUpdateType>
    [[-SourceFirmwareSubmissionTicketId] <String>] [[-OemDeviceName] <String>]
    [[-MOId] <String>] [-ServiceUri <Uri>] [-ServiceAccessControlNamespace
    <String>] [-CertificateStoreLocation <StoreLocation>]
    [-CertificateStoreName <StoreName>] [-ClientCertificateThumbprint
    <String>] [-EncryptionCertificateThumbprint <String>] [<CommonParameters>]


DESCRIPTION
    Creates a new request for update of OEM binaries, with a
    given update type and firmware submission ticket id. To create a Request
    For Update to Windows Phone 8.1 or higher, a source (ie. update "from")
    firmware submission ticket id is also required, along with the target
    mobile operator name, and target device name.


PARAMETERS
    -FirmwareSubmissionTicketId <String>
        Ticket id of the firmware submission phones update to.

        Required?                    true
        Position?                    2
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -RequestForUpdateType <RequestForUpdateType>
        The type of update request.

        Required?                    true
        Position?                    3
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -SourceFirmwareSubmissionTicketId <String>
        Ticket id of the firmware submission phones update from. Only required
        if phones are updating to Windows Phone 8.1 or higher.

        Required?                    false
        Position?                    4
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -OemDeviceName <String>
        Device name at which the Request for Update is being targeted. Only
        required if phones are updating to Windows Phone 8.1 or higher.

        Required?                    false
        Position?                    5
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -MOId <String>
        Mobile operator ID at which the Request for Update is being targeted.
        Only required if phones are updating to Windows Phone 8.1 or higher.

        Required?                    false
        Position?                    6
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

        Provides detailed information about the request for update (RFU).  The
        Ticket property is the ticket id for the actual RFU that should be
        recorded to allow for future communication about the RFU, for example
        through the command Get-RequestForUpdate which returns current status
        of the RFU.



    --------------  Example 1 --------------

    C:\PS>New-RequestForUpdate -FirmwareSubmissionTicketId
    TKT-SIGN-PROD-ABCD56 -RequestForUpdateType RetailServicing


    Creates a new request for update for retail servicing and links it to the
    firmware submission ticket id, TKT-SIGN-PROD-ABCD56.



    Ticket                   : TKT-RFU-PROD-ABCD56-1
                RfuType                  : RetailServicing
                IsApproved               : False
                CreatedOn                : 6/29/2013 7:44:07 AM
                ModifiedOn               : 6/29/2013 7:44:08 AM
                FirmwareSubmission       :
    Microsoft.Phone.PartnerServices.Rfu.FirmwareSubmission
                SourceFirmwareSubmission :
                SourceOSVersion          :
                TargetOSVersion          :
                Pop                      :
    Microsoft.Phone.PartnerServices.Rfu.Pop
                Bundles                  :
                Attachments              :
                Operations               :
    {Microsoft.Phone.PartnerServices.Rfu.RequestForUpdateOperation}
                ExtensionData            :
    System.Runtime.Serialization.ExtensionDataObject
                RfuPayloadType           : MicrosoftOemMixed



    --------------  Example 2 --------------

    C:\PS>New-RequestForUpdate -FirmwareSubmissionTicketId
    TKT-SIGN-PROD-ABCD56 -RequestForUpdateType RetailServicing
    -SourceFirmwareSubmissionTicketId TKT-SIGN-PROD-XYZ123 -OemDeviceName
    P4301 -MOId 000-22


    Creates a new request for update for retail servicing with source and
    target firmware submission ticket ids, meaning that the target OS version
    of the update is Windows Phone 8.1 or later.



    Ticket                   : TKT-RFU-PROD-ABCD56-1
                RfuType                  : RetailServicing
                IsApproved               : False
                CreatedOn                : 3/14/2014 7:44:07 AM
                ModifiedOn               : 3/14/2014 7:44:08 AM
                FirmwareSubmission       :
    Microsoft.Phone.PartnerServices.Rfu.FirmwareSubmission
                SourceFirmwareSubmission :
    Microsoft.Phone.PartnerServices.Rfu.FirmwareSubmission
                SourceOSVersion          : 8.10.12349.825
                TargetOSVersion          : 8.10.12359.845
                Pop                      :
    Microsoft.Phone.PartnerServices.Rfu.Pop
                Bundles                  :
                Attachments              :
                Operations               :
    {Microsoft.Phone.PartnerServices.Rfu.RequestForUpdateOperation}
                ExtensionData            :
    System.Runtime.Serialization.ExtensionDataObject
                RfuPayloadType           : MicrosoftOemMixed

RELATED LINKS
PS C:\Windows\system32>
```

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>要求


**标头︰**无

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[提交更新](submit-an-update.md)

[提交要零售签名的二进制文件](https://msdn.microsoft.com/library/windows/hardware/dn789223)

[请求-UpdateCancellation](request-updatecancellation.md)

 

 

