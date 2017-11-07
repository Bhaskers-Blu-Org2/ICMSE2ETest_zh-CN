---
title: "证书身份验证设备注册"
description: "本节提供了一种使用证书身份验证策略的移动设备注册协议。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 57DB3C9E-E4C9-4275-AAB5-01315F9D3910
ms.openlocfilehash: 494964fd6f99dcac7085f03c613d7966b0da12f0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="certificate-authentication-device-enrollment"></a>证书身份验证设备注册


本节提供了一种使用证书身份验证策略的移动设备注册协议。 有关 Windows 10 Microsoft 移动设备注册协议的详细信息，请参阅[\[MS MDE2\]︰ 移动设备注册协议版本 2]( http://go.microsoft.com/fwlink/p/?LinkId=619347)。

> **请注意** 若要将设备设置为注册使用证书身份验证，应创建配置包。 有关配置包的详细信息，请参阅[构建和应用资源调配的包](https://msdn.microsoft.com/library/windows/hardware/dn916107)。


## <a name="in-this-topic"></a>本主题中


-   [发现服务](#discovery-service)
-   [注册策略 web 服务](#enrollment-policy-web-service)
-   [注册 web 服务](#enrollment-web-service)

不支持 Windows 10 注册方案的列表，请参阅[注册不受支持的方案](mobile-device-enrollment.md#enrollment-scenarios-not-supported)。

## <a name="discovery-service"></a>发现服务

下面的示例演示查询服务请求。

``` syntax
POST /EnrollmentServer/Discovery.svc HTTP/1.1
Content-Type: application/soap+xml; charset=utf-8
User-Agent: Windows Enrollment Client
Host: EnterpriseEnrollment.Contoso.com
Content-Length: xxx
Cache-Control: no-cache

<?xml version="1.0"?>
<s:Envelope xmlns:a="http://www.w3.org/2005/08/addressing" 
   xmlns:s="http://www.w3.org/2003/05/soap-envelope"> 
   <s:Header> 
      <a:Action s:mustUnderstand="1">
 http://schemas.microsoft.com/windows/management/2012/01/enrollment/IDiscoveryService/Discover
      </a:Action> 
      <a:MessageID>urn:uuid: 748132ec-a575-4329-b01b-6171a9cf8478</a:MessageID> 
      <a:ReplyTo> 
         <a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address> 
      </a:ReplyTo> 
      <a:To s:mustUnderstand="1">
         https://ENROLLTEST.CONTOSO.COM/EnrollmentServer/Discovery.svc
      </a:To> 
   </s:Header> 
   <s:Body> 
      <Discover xmlns="http://schemas.microsoft.com/windows/management/2012/01/enrollment/"> 
         <request xmlns:i="http://www.w3.org/2001/XMLSchema-instance"> 
            <EmailAddress>user@contoso.com</EmailAddress>
            <OSEdition>101</OSEdition> <!--New in Windows 10-->
            <OSVersion>10.0.0.0</OSVersion> <!--New in Windows 10-->
            <RequestVersion>3.0</RequestVersion> <!--Updated in Windows 10-->
               <DeviceType>WindowsPhone</DeviceType> <!--Legacy in Windows 10 for Windows Phone/Handheld-->
            <ApplicationVersion>10.0.0.0</ApplicationVersion>
            <AuthPolicies>Certificate</AuthPolicies> <!--New in Windows 10-->
         </request> 
      </Discover> 
   </s:Body> 
</s:Envelope>
```

下面的示例演示查询服务响应。

```
HTTP/1.1 200 OK
Content-Length: 865
Content-Type: application/soap+xml; charset=utf-8
Server: EnterpriseEnrollment.Contoso.com
Date: Tue, 02 Aug 2012 00:32:56 GMT
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope" 
   xmlns:a="http://www.w3.org/2005/08/addressing">
   <s:Header>
      <a:Action s:mustUnderstand="1">
http://schemas.microsoft.com/windows/management/2012/01/enrollment/IDiscoveryService/DiscoverResponse
      </a:Action>
      <ActivityId>
         d9eb2fdd-e38a-46ee-bd93-aea9dc86a3b8
      </ActivityId>
      <a:RelatesTo>urn:uuid: 748132ec-a575-4329-b01b-6171a9cf8478</a:RelatesTo>
   </s:Header>
   <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
      xmlns:xsd="http://www.w3.org/2001/XMLSchema">
      <DiscoverResponse 
         xmlns="http://schemas.microsoft.com/windows/management/2012/01/enrollment">
         <DiscoverResult>
            <AuthPolicy>Certificate</AuthPolicy>
            <EnrollmentVersion>3.0</EnrollmentVersion>
            <EnrollmentPolicyServiceUrl>
               https://enrolltest.contoso.com/ENROLLMENTSERVER/DEVICEENROLLMENTWEBSERVICE.SVC
            </EnrollmentPolicyServiceUrl>
            <EnrollmentServiceUrl>
               https://enrolltest.contoso.com/ENROLLMENTSERVER/DEVICEENROLLMENTWEBSERVICE.SVC
            </EnrollmentServiceUrl>
         </DiscoverResult>
      </DiscoverResponse>
   </s:Body>
</s:Envelope>
```

## <a name="enrollment-policy-web-service"></a>注册策略 web 服务

下面的示例演示策略 web 服务请求。

```
POST /ENROLLMENTSERVER/DEVICEENROLLMENTWEBSERVICE.SVC HTTP/1.1
Content-Type: application/soap+xml; charset=utf-8
User-Agent: Windows Enrollment Client
Host: enrolltest.contoso.com
Content-Length: xxxx
Cache-Control: no-cache
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope" 
   xmlns:a="http://www.w3.org/2005/08/addressing"  
   xmlns:u="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd"
   xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"
   xmlns:wst="http://docs.oasis-open.org/ws-sx/ws-trust/200512" 
   xmlns:ac="http://schemas.xmlsoap.org/ws/2006/12/authorization">
   <s:Header>
      <a:Action s:mustUnderstand="1">
         http://schemas.microsoft.com/windows/pki/2009/01/enrollmentpolicy/IPolicy/GetPolicies
      </a:Action>
      <a:MessageID>urn:uuid:72048B64-0F19-448F-8C2E-B4C661860AA0</a:MessageID>
      <a:ReplyTo>
         <a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>
      </a:ReplyTo>
      <a:To s:mustUnderstand="1">
         https://enrolltest.contoso.com/ENROLLMENTSERVER/DEVICEENROLLMENTWEBSERVICE.SVC
      </a:To>
      <wsse:Security s:mustUnderstand="1">
         <wsse:BinarySecurityToken  wsse:ValueType="X509v3” wsse:Id="mytoken” wsse:EncodingType=
   http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd#base64binary"
           xmlns="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
                  B64EncodedSampleBinarySecurityToken
         </wsse:BinarySecurityToken>  
      </wsse:Security>
   </s:Header>
   <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
      xmlns:xsd="http://www.w3.org/2001/XMLSchema">
      <GetPolicies 
         xmlns="http://schemas.microsoft.com/windows/pki/2009/01/enrollmentpolicy">
         <client>
            <lastUpdate xsi:nil="true"/>
            <preferredLanguage xsi:nil="true"/>
         </client>
         <requestFilter xsi:nil="true"/>
      </GetPolicies>
         <ac:AdditionalContext xmlns="http://schemas.xmlsoap.org/ws/2006/12/authorization">
            <ac:ContextItem Name="OSPlatform">
               <ac:Value>WindowsMobile</ac:Value>
            <ac:ContextItem Name="OSEdition">
               <ac:Value>Core</ac:Value>
            <ac:ContextItem Name="OSVersion">
               <ac:Value>9.0.9999.0</ac:Value>
            <ac:ContextItem Name="DeviceName">
               <ac:Value>MY_WINDOWS_DEVICE</ac:Value>
            <ac:ContextItem Name="MACAddress">
               <ac:Value>FF:FF:FF:FF:FF:FF</ac:Value>
            <ac:ContextItem Name="IMEI">
               <ac:Value>49015420323756</ac:Value>
            <ac:ContextItem Name="EnrollmentType">
               <ac:Value>Lite</ac:Value>
            <ac:ContextItem Name="DeviceType">
               <ac:Value>WindowsPhone</ac:Value>
            </ac:ContextItem>
            <ac:ContextItem Name="ApplicationVersion">
               <ac:Value>10.0.0.0</ac:Value>
            </ac:ContextItem>
            <ac:ContextItem Name="DeviceID">
               <ac:Value>7BA748C8-703E-4DF2-A74A-92984117346A</ac:Value>
         </ac:AdditionalContext>
   </s:Body>
</s:Envelope>
```

下面的代码段显示了策略 web 服务响应。

```
HTTP/1.1 200 OK
Date: Fri, 03 Aug 2012 20:00:00 GMT
Server: <sever name here>
Content-Type: application/soap+xml
Content-Length: xxxx

<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<s:Envelope 
   xmlns:u="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd"
   xmlns:s="http://www.w3.org/2003/05/soap-envelope" 
   xmlns:a="http://www.w3.org/2005/08/addressing">
   <s:Header>
      <a:Action s:mustUnderstand="1">
   http://schemas.microsoft.com/windows/pki/2009/01/enrollmentpolicy/IPolicy/GetPoliciesResponse
      </a:Action>
      <ActivityId CorrelationId="08d2997e-e8ac-4c97-a4ce-d263e62186ab" 
         xmlns="http://schemas.microsoft.com/2004/09/ServiceModel/Diagnostics">
         d4335d7c-e192-402d-b0e7-f5d550467e3c</ActivityId>
      <a:RelatesTo>urn:uuid: 69960163-adad-4a72-82d2-bb0e5cff5598</a:RelatesTo>
   </s:Header>
   <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
      xmlns:xsd="http://www.w3.org/2001/XMLSchema">
      <GetPoliciesResponse 
         xmlns="http://schemas.microsoft.com/windows/pki/2009/01/enrollmentpolicy">
         <response>   
            <policyFriendlyName xsi:nil="true" 
               xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"/>
            <nextUpdateHours xsi:nil="true" 
               xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"/>
            <policiesNotChanged xsi:nil="true" 
               xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"/>
            <policies>
               <policy>
                  <policyOIDReference>0</policyOIDReference>
                  <cAs xsi:nil="true" />
                  <attributes>
                     <policySchema>3</policySchema>
                     <privateKeyAttributes>
                        <minimalKeyLength>2048</minimalKeyLength>
                        <keySpec xsi:nil="true" />
                        <keyUsageProperty xsi:nil="true" />
                        <permissions xsi:nil="true" />
                        <algorithmOIDReference xsi:nil="true" />
                        <cryptoProviders xsi:nil="true" />
                     </privateKeyAttributes>
                     <supersededPolicies xsi:nil="true" />
                     <privateKeyFlags xsi:nil="true" />
                     <subjectNameFlags xsi:nil="true" />
                     <enrollmentFlags xsi:nil="true" />
                     <generalFlags xsi:nil="true" />
                     <hashAlgorithmOIDReference>0</hashAlgorithmOIDReference>
                     <rARequirements xsi:nil="true" />
                     <keyArchivalAttributes xsi:nil="true" />
                     <extensions xsi:nil="true" />
                  </attributes>
               </policy>
            </policies>
         </response>
         <cAs xsi:nil="true" />
         <oIDs>
            <oID>
               <value>1.3.14.3.2.29</value>
               <group>1</group>
               <oIDReferenceID>0</oIDReferenceID>
               <defaultName>szOID_OIWSEC_sha1RSASign</defaultName>
            </oID>
         </oIDs>
      </GetPoliciesResponse>
   </s:Body>
</s:Envelope>

```

## <a name="enrollment-web-service"></a>注册 web 服务

下面的示例演示注册 web 服务请求。

```
POST /EnrollmentServer/DeviceEnrollmentWebService.svc HTTP/1.1
Content-Type: application/soap+xml; charset=utf-8
User-Agent: Windows Enrollment Client
Host: enrolltest.contoso.com
Content-Length: 3242
Cache-Control: no-cache

<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope" 
   xmlns:a="http://www.w3.org/2005/08/addressing" 
   xmlns:u="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd"
   xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"
   xmlns:wst="http://docs.oasis-open.org/ws-sx/ws-trust/200512" 
   xmlns:ac="http://schemas.xmlsoap.org/ws/2006/12/authorization">
   <s:Header>
      <a:Action s:mustUnderstand="1">
         http://schemas.microsoft.com/windows/pki/2009/01/enrollment/RST/wstep
      </a:Action>
      <a:MessageID>urn:uuid:0d5a1441-5891-453b-becf-a2e5f6ea3749</a:MessageID>
      <a:ReplyTo>
         <a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>
      </a:ReplyTo>
      <a:To s:mustUnderstand="1">
         https://enrolltest.contoso.com:443/ENROLLMENTSERVER/DEVICEENROLLMENTWEBSERVICE.SVC
      </a:To>
      <wsse:Security s:mustUnderstand="1">
         <wsu:Timestamp>
            <wsu:Created>2014-10-16T17:55:13Z</wsu:Created> <!-- Start time in UTC -->
            <wsu:Expires>2014-10-16T17:57:13Z </wsu:Expires> <!-- Expiration time in UTC -->
        </wsu:Timestamp> 
        <wsse:BinarySecurityToken  wsse:ValueType=
http://schemas.microsoft.com/5.0.0.0/ConfigurationManager/Enrollment/DeviceEnrollmentUserToken
                  wsse:EncodingType=
   http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd#base64binary"
                  xmlns=
          http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd
                  wsu:Id=”29801C2F-F26B-46AD-984B-AFAEFB545FF8”>
                  B64EncodedSampleBinarySecurityToken
         </wsse:BinarySecurityToken> <!—X509v3 Exported Public Cert, B64 Encoded, includes ID reference value to reference  -->
         <ds:Signature xmlns:ds="http://www.w3.org/2000/09/xmldsig#">
            <ds:SignedInfo xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" 
                 xmlns:ds="http://www.w3.org/2000/09/xmldsig#" 
                 xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-
                            1.0.xsd”>
               <ds:SignatureMethodAlgorithm="http://www.w3.org/2000/09/xmldsig#rsa-sha1/>
               <ds:Reference URI="#envelop">
                  <ds:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha256"/> 
                  <ds:DigestValue>MessageDigestValue</ds:DigestValue>
                     <!-- Digest value of message using digest method -->
               </ds:Reference>
            </ds:SignedInfo>
            <ds:SignatureValue>SignedMessageBlob/ds:SignatureValue> 
                <!-- Digest value of message signed with the user’s private key using RSA-SHA256 -->
            <ds:KeyInfo>
               <wsse:SecurityTokenReference> 
                  <wsse:Reference URI="29801C2F-F26B-46AD-984B-AFAEFB545FF8" 
                                  ValueType="http://docs.oasis-open.org/wss/2004/01/
                                  oasis-200401-wss-x509-token-profile-1.0#X509"/>
                  <!-— References BinarySecurityToken that contains public key to verify signature -->
               </wsse:SecurityTokenReference>
            </ds:KeyInfo>
         </ds:Signature>
      </wsse:Security>
   </s:Header>
   <s:Body>
      <wst:RequestSecurityToken>
         <wst:TokenType>
    http://schemas.microsoft.com/5.0.0.0/ConfigurationManager/Enrollment/DeviceEnrollmentToken
         </wst:TokenType>
         <wst:RequestType>
            http://docs.oasis-open.org/ws-sx/ws-trust/200512/Issue</wst:RequestType>
         <wsse:BinarySecurityToken 
            ValueType="http://schemas.microsoft.com/windows/pki/2009/01/enrollment#PKCS10" 
            EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd#base64binary">
            DER format PKCS#10 certificate request in Base64 encoding Insterted Here
         </wsse:BinarySecurityToken>
         <ac:AdditionalContext xmlns="http://schemas.xmlsoap.org/ws/2006/12/authorization">
            <ac:ContextItem Name="OSEdition"> <!--New in Windows 10-->
               <ac:Value></ac:Value>
            <ac:ContextItem Name="OSVersion"> <!--New in Windows 10-->
               <ac:Value>10.0.0.0</ac:Value>
            <ac:ContextItem Name="DeviceName"> <!--New in Windows 10-->
               <ac:Value>MY_WINDOWS_DEVICE</ac:Value>
            <ac:ContextItem Name="MAC"> <!--New in Windows 10 -->
               <ac:Value>FF:FF:FF:FF:FF:FF</ac:Value>
            <ac:ContextItem Name="MAC"> <!--New in Windows 10 -->
               <ac:Value>CC:CC:CC:CC:CC:CC</ac:Value>
            <ac:ContextItem Name="IMEI"> <!--New in Windows 10-->
               <ac:Value>49015420323756</ac:Value>
            <ac:ContextItem Name="EnrollmentType"> <!--New in Windows 10-->
               <ac:Value>Full</ac:Value>
            <ac:ContextItem Name="DeviceType"> <!—From Windows Phone 8.1-->
               <ac:Value>WindowsPhone</ac:Value>
            </ac:ContextItem>
            <ac:ContextItem Name="ApplicationVersion"> <!—From Windows Phone 8.1-->
               <ac:Value>10.0.0.0</ac:Value>
            </ac:ContextItem>
            <ac:ContextItem Name="DeviceID"> <!--From Handheld 8.1 -->
               <ac:Value>7BA748C8-703E-4DF2-A74A-92984117346A</ac:Value> 
               <ac:ContextItem Name="EnrollmentData">
               <ac:Value>3J4KLJ9SDJFAL93JLAKHJSDFJHAO83HAKSHFLAHSKFNHNPA2934342</ac:Value>
               <ac:ContextItem Name="TargetedUserLoggedIn">
               <ac:Value>True</ac:Value>
         </ac:AdditionalContext>
      </wst:RequestSecurityToken>
   </s:Body>
</s:Envelope>

```

下面的示例演示注册 web 服务响应。

```
HTTP/1.1 200 OK
Cache-Control: private
Content-Length: 10231
Content-Type: application/soap+xml; charset=utf-8
Server: Microsoft-IIS/7.0
Date: Fri, 03 Aug 2012 00:32:59 GMT

<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/" 
   xmlns:a="http://www.w3.org/2005/08/addressing" 
   xmlns:u="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">
   <s:Header>
      <Action s:mustUnderstand="1" >
         http://schemas.microsoft.com/windows/pki/2009/01/enrollment/RSTRC/wstep
      </Action>
      <a:RelatesTo>urn:uuid:81a5419a-496b-474f-a627-5cdd33eed8ab</a:RelatesTo>
      <o:Security s:mustUnderstand="1" xmlns:o=
         "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
         <u:Timestamp u:Id="_0">
            <u:Created>2012-08-02T00:32:59.420Z</u:Created>
            <u:Expires>2012-08-02T00:37:59.420Z</u:Expires>
         </u:Timestamp>
      </o:Security>
   </s:Header>
   <s:Body>
      <RequestSecurityTokenResponseCollection 
         xmlns="http://docs.oasis-open.org/ws-sx/ws-trust/200512">
         <RequestSecurityTokenResponse>
            <TokenType>
    http://schemas.microsoft.com/5.0.0.0/ConfigurationManager/Enrollment/DeviceEnrollmentToken
            </TokenType>
            <RequestedSecurityToken>
               <BinarySecurityToken 
                  ValueType=
"http://schemas.microsoft.com/5.0.0.0/ConfigurationManager/Enrollment/DeviceEnrollmentProvisionDoc"
                  EncodingType=
   "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd#base64binary"
                  xmlns=
          "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
                  B64EncodedSampleBinarySecurityToken
               </BinarySecurityToken>
            </RequestedSecurityToken>
            <RequestID xmlns="http://schemas.microsoft.com/windows/pki/2009/01/enrollment">0
            </RequestID>
         </RequestSecurityTokenResponse>
      </RequestSecurityTokenResponseCollection>
   </s:Body>
</s:Envelope>

```

下面的示例演示编码的置备 XML。

```
<wap-provisioningdoc version="1.1">
   <characteristic type="CertificateStore">
      <characteristic type="Root">
         <characteristic type="System">
            <characteristic type="031336C933CC7E228B88880D78824FB2909A0A2F">
               <parm name="EncodedCertificate" value="B64 encoded cert insert here" />
            </characteristic>
         </characteristic>
      </characteristic>
   </characteristic>
   <characteristic type="CertificateStore">
      <characteristic type="My" >      
         <characteristic type="User">
            <characteristic type="F9A4F20FC50D990FDD0E3DB9AFCBF401818D5462">
               <parm name="EncodedCertificate" value="B64EncodedCertInsertedHere" />
            </characteristic>
            <characteristic type="PrivateKeyContainer"/> 
            <!-- This tag must be present for XML syntax correctness. -->            
         </characteristic>
         <characteristic type="WSTEP">
            <characteristic type="Renew">
             <!—If the datatype for ROBOSupport, RenewPeriod, and RetryInterval tags exist, they must be set explicitly. -->
               <parm name="ROBOSupport" value="true" datatype="boolean"/>
               <parm name="RenewPeriod" value="60" datatype="integer"/>
               <parm name="RetryInterval" value="4" datatype="integer"/>
            </characteristic>
         </characteristic>
      </characteristic>
   </characteristic>
   <characteristic type="APPLICATION">
      <parm name="APPID" value="w7"/>
      <parm name="PROVIDER-ID" value="TestMDMServer"/>
      <parm name="NAME" value="Microsoft"/>
      <parm name="ADDR" value="https://DM.contoso.com:443/omadm/Windows.ashx"/>
      <parm name="CONNRETRYFREQ" value="6" />
      <parm name="INITIALBACKOFFTIME" value="30000" />
      <parm name="MAXBACKOFFTIME" value="120000" />
      <parm name="BACKCOMPATRETRYDISABLED" />
      <parm name="DEFAULTENCODING" value="application/vnd.syncml.dm+wbxml" />
      <parm name="SSLCLIENTCERTSEARCHCRITERIA" value=
  "Subject=DC%3dcom%2cDC%3dmicrosoft%2cCN%3dUsers%2cCN%3dAdministrator&amp;amp;Stores=My%5CUser"/>
      <characteristic type="APPAUTH">
         <parm name="AAUTHLEVEL" value="CLIENT"/>
         <parm name="AAUTHTYPE" value="DIGEST"/>
         <parm name="AAUTHSECRET" value="password1"/>
         <parm name="AAUTHDATA" value="B64encodedBinaryNonceInsertedHere"/>
      </characteristic>
      <characteristic type="APPAUTH">
         <parm name="AAUTHLEVEL" value="APPSRV"/>
         <parm name="AAUTHTYPE" value="BASIC"/>
         <parm name="AAUTHNAME" value="testclient"/>
         <parm name="AAUTHSECRET" value="password2"/>
      </characteristic>
   </characteristic>
   <characteristic type="DMClient"> <!-- In Windows 10, an enrollment server should use DMClient CSP XML to configure DM polling schedules. -->
      <characteristic type="Provider">
<!-- ProviderID in DMClient CSP must match to PROVIDER-ID in w7 APPLICATION characteristics -->
    <characteristic type="TestMDMServer">
          <parm name="UPN" value="UserPrincipalName" datatype="string" /> 
             <characteristic type="Poll">
                <parm name="NumberOfFirstRetries" value="8" datatype="integer" />
                <parm name="IntervalForFirstSetOfRetries" value="15" datatype="integer" />
                <parm name="NumberOfSecondRetries" value="5" datatype="integer" />
                <parm name="IntervalForSecondSetOfRetries" value="3" datatype="integer" />
                <parm name="NumberOfRemainingScheduledRetries" value="0" datatype="integer" />
<!-- Windows 10 supports MDM push for real-time communication. The DM client long term polling schedule’s retry waiting interval should be more than 24 hours (1440) to reduce the impact to data consumption and battery life. Refer to the DMClient Configuration Service Provider section for information about polling schedule parameters.-->
         <parm name="IntervalForRemainingScheduledRetries" value="1560" datatype="integer" />
         <parm name="PollOnLogin" value="true" datatype="boolean" />
 </characteristic>
        <parm name="EntDeviceName" value="Administrator_Windows" datatype="string" />
</characteristic>
      </characteristic>
   </characteristic>
   <!-- For Windows 10, we have removed EnterpriseAppManagement from the enrollment 
        protocol. This configuration service provider is being deprecated for Windows 10. -->
</wap-provisioningdoc>
```

 





