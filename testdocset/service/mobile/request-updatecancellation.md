---
author: kpacquer
Description: "请求 UpdateCancellation cmdlet"
ms.assetid: a01ab740-d6a2-4c9e-bfb6-ee3fabb3799a
MSHAttr: PreferredLib:/library/windows/hardware
title: "请求 UpdateCancellation cmdlet"
ms.openlocfilehash: b151e57bf0dd69809618137d3d3def7d76928270
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="span-idrequest-updatecancellationspanrequest-updatecancellation-cmdlet"></a><span id="request-updatecancellation"></span>请求 UpdateCancellation cmdlet


请求使用该**请求 UpdateCancellation** cmdlet 的固件提交请求的取消。

您可以取消[新建 RequestForUpdate cmdlet](new-requestforupdate-cmdlet.md)通过发送任意混合 OEM/更新。 您不能取消更新 (RFU) 发送到 Microsoft 更新请求已获批准进行实时装运。

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>语法


``` syntax
    Request-UpdateCancellation [-RequestForUpdateTicketId] <String> 
    [-ServiceUri <Uri>] [-ServiceAccessControlNamespace <String>] 
    [-CertificateStoreLocation <StoreLocation>] [-CertificateStoreName 
    <StoreName>] [-ClientCertificateThumbprint <String>] 
    [-EncryptionCertificateThumbprint <String>] [<CommonParameters>]
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>参数


通常情况下，指定在此 cmdlet 的唯一参数是固件提交票证 id。

``` syntax
Request-UpdateCancellation -RequestForUpdateTicketId 
    TKT-RFU-PROD-ABCD56-1
```

## <a name="span-idhelpdocumentationfrompowershellspanspan-idhelpdocumentationfrompowershellspanspan-idhelpdocumentationfrompowershellspanhelp-documentation-from-powershell"></a><span id="Help_documentation_from_PowerShell"></span><span id="help_documentation_from_powershell"></span><span id="HELP_DOCUMENTATION_FROM_POWERSHELL"></span>从 PowerShell 的帮助文档


以下是从 Windows PowerShell**新建 FirmwareSubmission** cmdlet 的帮助文档。

``` syntax
NAME
    Request-UpdateCancellation
    
SYNOPSIS
    Requests cancellation for the specified ticket.
    
SYNTAX
    Request-UpdateCancellation [-RequestForUpdateTicketId] <String> 
    [-ServiceUri <Uri>] [-ServiceAccessControlNamespace <String>] 
    [-CertificateStoreLocation <StoreLocation>] [-CertificateStoreName 
    <StoreName>] [-ClientCertificateThumbprint <String>] 
    [-EncryptionCertificateThumbprint <String>] [<CommonParameters>]
    
    
DESCRIPTION
    Requests cancellation for the specified update request. The request could 
    be for a MicrosoftOemMixed or MicrosoftAKOnly update.
    

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
    
        
        
    
     
    
NOTES
    
    
        
    
    --------------  Example 1 --------------
    
    C:\PS>Request-UpdateCancellation -RequestForUpdateTicketId 
    TKT-RFU-PROD-ABCD56-1
    
    
    Requests cancellation for a given RequestForUpdateTicketId
    
    
    
    
    
    
RELATED LINKS
```

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>要求


**标头︰**无

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[提交要零售签名的二进制文件](https://msdn.microsoft.com/library/windows/hardware/dn789223)

[新 RequestForUpdate cmdlet](new-requestforupdate-cmdlet.md)

[新 RequestForMicrosoftUpdate cmdlet](new-requestformicrosoftupdate-cmdlet.md)

 

 






