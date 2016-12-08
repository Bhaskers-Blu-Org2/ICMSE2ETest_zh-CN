---
author: kpacquer
Description: "新 RequestForMicrosoftUpdate cmdlet"
ms.assetid: be21b20d-a3bf-4b83-9633-211dcbeecdb3
MSHAttr: PreferredLib:/library/windows/hardware
title: "新 RequestForMicrosoftUpdate cmdlet"
ms.openlocfilehash: 173bd02d19491964c6ace884d2673ad572301578
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="new-requestformicrosoftupdate-cmdlet"></a>新 RequestForMicrosoftUpdate cmdlet


使用**New RequestForMicrosoftUpdate** cmdlet 来创建包含给定的产品、 CPU、 更新类型、 源和目标微软操作系统的版本号，以及目标移动运营商名称和目标电话名称仅用于 Microsoft AK 的二进制文件的更新 (RFU) 新请求。

从发布的 Windows 10 开始，Oem 可以不再仅操作系统更新零售设备使用提交新建 RequestForMicrosoftUpdate cmdlet。 将由 Microsoft Windows Update 上提供零售设备仅操作系统更新。

Oem 可以继续提交试用版和 PartnerSelfHost 预览环境仅操作系统更新。

**重要**  
您需要提交每个电话操作员配对的更新。 例如，如果特定的移动运营上有两部电话，将需要提交更新 (RFU) 这两个请求。 如果您有四个不同的 MOs 电话，需要提交四个 RFUs。

 

这是**新 RequestForMicrosoftUpdate**的语法︰

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>语法


``` syntax
New-RequestForMicrosoftUpdate [-TypeOfCPU <string>] [-TypeOfProduct <string>] 
[-SourceOSVersion <String>] [-TargetOSVersion <String>] [-RequestForUpdateType <RequestForUpdateType>]
[-OemDeviceName <String>] [-MOId <String>] [-ServiceUri <Uri>] [-ServiceAccessControlNamespace <String>]
[-CertificateStoreLocation <StoreLocation>] [-CertificateStoreName <StoreName>]
[-ClientCertificateThumbprint <String>] [-EncryptionCertificateThumbprint <String>]
 [<CommonParameters>]
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>参数


通常情况下，为此 cmdlet 指定的唯一参数是**SourceOSVersion**、 **TargetOSVersion**、 **RequestForUpdateType**、 **OemDeviceName**和**MOId**。

**SourceOSVersion**是上一次更新的版本。 建议使用此设置，并可帮助防止出现发布可能导致更新错误的更新。 设备更新发布服务有权拒绝不包括上一次更新的 SourceOSVersion 的 RFUs。 版本控制的详细信息，请参阅[更新的要求](update-requirements.md)。

**TargetOS**版本是提交了更新的版本。

必须将**RequestForUpdateType**设置为汇总如下的两个值之一。

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
<td align="left"><p>OEM BSP 更新旨在到服务市场中的设备。 这些更新是作为计划的 OEM 更新节奏 （A4、 A5、 A6 等） 的一部分提供的。</p></td>
</tr>
<tr class="even">
<td align="left"><p>试用</p></td>
<td align="left"><p>与移动操作员 OTA 试验和 OEM 工程试验使用试用版更新。</p>
<ul>
<li><p>移动操作员 OTA 试验 – OEM BSP 更新用于允许 MOs 实现新设备商品化。</p></li>
<li><p>OEM 工程试验 – OEM R&amp;D 试验旨在使 Oem 测试更新的设备图像的候选项。</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

**OemDeviceName**是为在目标更新请求的名称。 这只是所需设备是否更新到 Windows Phone 8.1 或更高版本。

**MOId**是移动运营商为目标的更新请求。

## <a name="span-idscenariosspanspan-idscenariosspanspan-idscenariosspanscenarios"></a><span id="Scenarios"></span><span id="scenarios"></span><span id="SCENARIOS"></span>方案


### <a name="span-idcreateanewrfuforuseintrialsspanspan-idcreateanewrfuforuseintrialsspanspan-idcreateanewrfuforuseintrialsspancreate-a-new-rfu-for-use-in-trials"></a><span id="Create_a_new_RFU_for_use_in_trials"></span><span id="create_a_new_rfu_for_use_in_trials"></span><span id="CREATE_A_NEW_RFU_FOR_USE_IN_TRIALS"></span>在试验中创建用于新 RFU

### <a name="span-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanspan-idscenarioprerequisitesspanscenario-prerequisites"></a><span id="Scenario_prerequisites"></span><span id="scenario_prerequisites"></span><span id="SCENARIO_PREREQUISITES"></span>方案的前提条件

-   没有希望的 OEM 研发提交新的试验，例如，更新请求

### <a name="span-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanspan-idexampleusagewithexpectedoutputspanexample-usage-with-expected-output"></a><span id="Example_usage_with_expected_output"></span><span id="example_usage_with_expected_output"></span><span id="EXAMPLE_USAGE_WITH_EXPECTED_OUTPUT"></span>与预期的输出的示例用法

请求新的更新，并将结果对象存储在一个名为 $result 的 Windows PowerShell 变量︰

``` syntax
$result = New-RequestForMicrosoftUpdate -SourceOSVersion 8.10.12349.825 -TargetOSVersion 8.10.12359.845 -RequestForUpdateType Trial -OemDeviceName P4301 -MOId 000-22
```

在控制台上显示结果︰

``` syntax
PS> $result | Format-List

Ticket                   : TKT-RFU-PROD-PQRST-1
RfuType                  : Trial
IsApproved               : False
CreatedOn                : 5/2/2014 5:42:51 PM
ModifiedOn               : 5/2/2014 5:42:52 PM
FirmwareSubmission       :
SourceFirmwareSubmission :
SourceOSVersion          : 8.10.12349.825
TargetOSVersion          : 8.10.12359.845
Pop                      : Microsoft.Phone.PartnerServices.Rfu.Pop
Bundles                  :
Attachments              :
Operations               : {Microsoft.Phone.PartnerServices.Rfu.RequestForUpdateOperation}
Status                   : Microsoft.Phone.PartnerServices.Rfu.RfuStatusInfo
RfuPayloadType           : MicrosoftAKOnly
ExtensionData            : System.Runtime.Serialization.ExtensionDataObject
      
```

### <a name="span-idhelpdocumentationfromwindowspowershellspanspan-idhelpdocumentationfromwindowspowershellspanspan-idhelpdocumentationfromwindowspowershellspanhelp-documentation-from-windows-powershell"></a><span id="Help_documentation_from_Windows_PowerShell"></span><span id="help_documentation_from_windows_powershell"></span><span id="HELP_DOCUMENTATION_FROM_WINDOWS_POWERSHELL"></span>从 Windows PowerShell 的帮助文档

以下是从 Windows PowerShell**新建 RequestForMicrosoftUpdate** cmdlet 的帮助文档。

``` syntax
PS C:\Windows\system32> get-help New-RequestForMicrosoftUpdate -full

NAME
    New-RequestForMicrosoftUpdate

SYNOPSIS
    Creates a new request for update of Microsoft AK-only binaries.

SYNTAX
    New-RequestForMicrosoftUpdate [-TypeOfCPU <string>] [-TypeOfProduct <string>] 
[-SourceOSVersion <String>] [-TargetOSVersion <String>] [-RequestForUpdateType <RequestForUpdateType>]
[-OemDeviceName <String>] [-MOId <String>] [-ServiceUri <Uri>] [-ServiceAccessControlNamespace <String>]
[-CertificateStoreLocation <StoreLocation>] [-CertificateStoreName <StoreName>]
[-ClientCertificateThumbprint <String>] [-EncryptionCertificateThumbprint <String>]
 [<CommonParameters>]

DESCRIPTION
    Creates a new request for update of Microsoft AK-only binaries with a
    given update type, source and target Microsoft OS version numbers, along
    with the target mobile operator name, and target device name.


PARAMETERS
    -TypeOfProduct <String>
        The product targeted for the update.The product must be one of WindowsPhoneBlue, WindowsPhoneThreshold, WindowsHolographicThreshold.

        Required?                    true
        Position?                    2
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -TypeOfCPU <String>
        The CPU of the product targeted for the update.The CPU must be one of ARM, x86.

        Required?                    true
        Position?                    2
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -SourceOSVersion <String>
        Microsoft AK OS version the phone updates from.

        Required?                    true
        Position?                    2
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -TargetOSVersion <String>
        Microsoft AK OS version the phone updates to.

        Required?                    true
        Position?                    3
        Default value
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Accept wildcard characters?  false

    -RequestForUpdateType <RequestForUpdateType>
        The type of update request.

        Required?                    true
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

        Provides detailed information about the request for update (RFU) of
        Microsoft AK-only binaries.  The Ticket property is the ticket id for
        the actual RFU that should be recorded to allow for future
        communication about the RFU, for example through the command
        Get-RequestForUpdate which returns current status of the RFU.



    --------------  Example 1 --------------

    C:\PS>New-RequestForMicrosoftUpdate -SourceOSVersion 8.10.12349.825
    -TargetOSVersion 8.10.12359.845 -RequestForUpdateType Trial -OemDeviceName
    P4301 -MOId 000-22


    Creates a new request for update for retail servicing with source and
    target firmware submission ticket ids, meaning that the target OS version
    of the update is Windows Phone 8.1 or later.



    Ticket                   : TKT-RFU-PROD-PQRST-1
                RfuType                  : Trial
                IsApproved               : False
                CreatedOn                : 5/2/2014 5:42:51 PM
                ModifiedOn               : 5/2/2014 5:42:52 PM
                FirmwareSubmission       :
                SourceFirmwareSubmission :
                SourceOSVersion          : 8.10.12349.825
                TargetOSVersion          : 8.10.12359.845
                Pop                      :
    Microsoft.Phone.PartnerServices.Rfu.Pop
                Bundles                  :
                Attachments              :
                Operations               :
    {Microsoft.Phone.PartnerServices.Rfu.RequestForUpdateOperation}
                Status                   :
    Microsoft.Phone.PartnerServices.Rfu.RfuStatusInfo
                RfuPayloadType           : MicrosoftAKOnly
                ExtensionData            :
    System.Runtime.Serialization.ExtensionDataObject

RELATED LINKS

PS C:\Windows\system32>
```

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>要求


**标头︰**无

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[提交更新](submit-an-update.md)

[请求-UpdateCancellation](request-updatecancellation.md)

 

 