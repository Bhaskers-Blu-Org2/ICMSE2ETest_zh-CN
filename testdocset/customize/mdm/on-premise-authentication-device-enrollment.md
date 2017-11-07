---
title: "内部部署身份验证设备注册"
description: "本节提供了一种使用内部部署身份验证策略的移动设备注册协议。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 626AC8B4-7575-4C41-8D59-185D607E3A47
ms.openlocfilehash: 55d7dd5cbdbb27eeddfc68e7ce5b1d00758d710c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="on-premise-authentication-device-enrollment"></a>内部部署身份验证设备注册


本节提供了一种使用内部部署身份验证策略的移动设备注册协议。 有关 Windows 10 Microsoft 移动设备注册协议的详细信息，请参阅[\[MS MDE2\]︰ 移动设备注册协议版本 2]( http://go.microsoft.com/fwlink/p/?LinkId=619347)。

## <a name="in-this-topic"></a>本主题中

-   [发现服务](#discovery-service)
-   [注册策略 web 服务](#enrollment-policy-web-service)
-   [注册 web 服务](#enrollment-web-service)

不支持 Windows 10 注册方案的列表，请参阅[注册不受支持的方案](mobile-device-enrollment.md#enrollment-scenarios-not-supported)。

## <a name="discovery-service"></a>发现服务

发现 web 服务提供了用户注册与管理服务的设备所需的配置信息。 该服务通过 HTTPS （仅服务器身份验证） 是 rest 风格的 web 服务。

> **请注意** 发现服务的管理员必须创建的地址 enterpriseenrollment 的主机。*域\_名称*。 com。

 
设备的自动发现流使用登录时已提交至工作场所设置屏幕的电子邮件地址的域名。 自动发现系统构造一个 URI，它使用此主机名通过追加到的电子邮件地址域的子域"enterpriseenrollment"，并将路径追加"/ EnrollmentServer/Discovery.svc"。 例如，如果电子邮件地址为“sample@contoso.com”,是第一个 Get 请求的结果 URI: http:<span></span>//enterpriseenrollment.contoso.com/EnrollmentServer/Discovery.svc

在第一个请求是标准的 HTTP GET 请求。

下面的示例显示与给定的搜索服务器通过 HTTP GET 请求user@contoso.com的电子邮件地址。

```
Request Full Url: http://EnterpriseEnrollment.contoso.com/EnrollmentServer/Discovery.svc
Content Type: unknown
Header Byte Count: 153
Body Byte Count: 0
```

```
GET /EnrollmentServer/Discovery.svc HTTP/1.1
User-Agent: Windows Phone 8 Enrollment Client
Host: EnterpriseEnrollment.contoso.com
Pragma: no-cache
```

```
Request Full Url: http://EnterpriseEnrollment.contoso.com/EnrollmentServer/Discovery.svc
Content Type: text/html
Header Byte Count: 248
Body Byte Count: 0
```

```
HTTP/1.1 200 OK
Connection: Keep-Alive
Pragma: no-cache
Cache-Control: no-cache
Content-Type: text/html
Content-Length: 0
```

设备获取来自服务器的响应后，设备会向 enterpriseenrollment 发送 POST 请求。*域\_名称*/EnrollmentServer/Discovery.svc。 它从服务器 （它应告知设备位置注册服务器） 获取其他响应后，从设备发送的下一个邮件是 enterpriseenrollment。*域\_名称*到注册服务器。

将应用以下逻辑︰

1.  该设备首先尝试 HTTPS。 如果服务器证书不受信任设备，HTTPS 无法正常工作。
2.  如果查找失败，设备将尝试 HTTP 是否重定向，请参阅︰
    -   如果该设备未被重定向，它会提示用户输入服务器地址。
    -   如果该设备重定向，它会提示用户以允许重定向。

下面的示例演示通过 HTTP POST 命令到给定发现 web 服务请求user@contoso.com的电子邮件地址

```
https://EnterpriseEnrollment.Contoso.com/EnrollmentServer/Discovery.svc
```

下面的示例演示查询服务请求。

``` syntax
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
            <OSEdition>3</OSEdition> <!--New -->
            <RequestVersion>3.0</RequestVersion> <!-- Updated -->
            <DeviceType>WindowsPhone</DeviceType> <!--Updated -->
            <ApplicationVersion>10.0.0.0</ApplicationVersion>
            <AuthPolicies>
               <AuthPolicy>OnPremise</AuthPolicy>
            </AuthPolicies>
          </request>
        </Discover>
      </s:Body>
    </s:Envelope>
```

如果一个域和用户的名称而不是电子邮件地址，用户提供了&lt;电子邮件地址&gt;标记应包含域\\用户名。 在这种情况下，用户需要可以直接输入服务器地址。

&lt;电子邮件地址&gt;contoso\\用户&lt;/EmailAddress&gt;响应

发现响应是 XML 格式，并包含下列字段︰

-   注册服务 URL (EnrollmentServiceUrl) – 指定的 URL 注册终结点公开的管理服务。 用户已通过身份验证后，该设备应调用此 URL。 此字段是必填字段。
-   身份验证策略 (AuthPolicy) – 指示哪种类型的身份验证是必需的。 对于 MDM 服务器中，OnPremise 是受支持的值，这意味着调用管理服务 URL 时，将验证用户。 此字段是必填字段。
-   联合将作为另一种受支持的值。 这使得服务器可以利用 Web 身份验证代理程序执行自定义的用户身份验证，并使用认可的期限。

> **请注意** 不必须分块的 HTTP 服务器响应;它必须作为一个邮件被发送。

 
下面的示例演示从 OnPremise 身份验证发现 web 服务接收到的响应︰

``` syntax
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
            <AuthPolicy>OnPremise</AuthPolicy>
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

对于 OnPremise 身份验证策略，在 GetPolicies UsernameToken 包含其值取决于查询中的身份验证策略的用户凭据。 在 MSDN 网站; 找不到请求的示例下面是另一个示例中，使用"user@contoso.com"作为用户名和密码为"mypassword"。

下面的示例演示策略 web 服务请求。

``` syntax
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
          <wsse:UsernameToken u:Id="uuid-cc1ccc1f-2fba-4bcf-b063-ffc0cac77917-4">
            <wsse:Username>user@contoso.com</wsse:Username>
            <wsse:Password wsse:Type="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordText">mypassword</wsse:Password>
          </wsse:UsernameToken>
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
      </s:Body>
    </s:Envelope>
```

对用户进行验证后，web 服务检索用户应与注册并创建基于证书模板属性的注册策略的证书模板。 响应的示例可以在 MSDN 上找到。

MS XCEP 支持非常灵活地进行注册策略使用各种复杂类型和特性。 首先，我们将支持 minimalKeyLength，hashAlgorithmOIDReference 策略和 CryptoProviders。 HashAlgorithmOIDReference 具有相关 OID OIDReferenceID 和 policySchema 在 GetPolicesResponse 中。 PolicySchema 是指证书模板版本。 版本 3 的 MS XCEP 支持哈希算法。

> **请注意** 不必须分块的 HTTP 服务器响应;它必须作为一个邮件被发送。

 
下面的代码段显示了策略 web 服务响应。

``` syntax
      <s:Envelope
         xmlns:u="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd"
         xmlns:s="http://www.w3.org/2003/05/soap-envelope"
         xmlns:a="http://www.w3.org/2005/08/addressing">
        <s:Header>
          <a:Action s:mustUnderstand="1">
            http://schemas.microsoft.com/windows/pki/2009/01/enrollmentpolicy/IPolicy/GetPoliciesResponse
          </a:Action>
          <a:RelatesTo>urn:uuid: 69960163-adad-4a72-82d2-bb0e5cff5598</a:RelatesTo>
        </s:Header>
        <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xmlns:xsd="http://www.w3.org/2001/XMLSchema">
          <GetPoliciesResponse
             xmlns="http://schemas.microsoft.com/windows/pki/2009/01/enrollmentpolicy">
            <response>
            <policyID />
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
                    <commonName>CEPUnitTest</commonName>
                    <policySchema>3</policySchema>
                    <certificateValidity>
                      <validityPeriodSeconds>1209600</validityPeriodSeconds>
                      <renewalPeriodSeconds>172800</renewalPeriodSeconds>
                    </certificateValidity>
                    <permission>
                      <enroll>true</enroll>
                      <autoEnroll>false</autoEnroll>
                    </permission>
                    <privateKeyAttributes>
                      <minimalKeyLength>2048</minimalKeyLength>
                      <keySpec xsi:nil="true" />
                      <keyUsageProperty xsi:nil="true" />
                      <permissions xsi:nil="true" />
                      <algorithmOIDReference xsi:nil="true" />
                      <cryptoProviders xsi:nil="true" />
                    </privateKeyAttributes>
                    <revision>
                      <majorRevision>101</majorRevision>
                      <minorRevision>0</minorRevision>
                    </revision>
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

此 web 服务实现的 MS WSTEP 协议。 它处理来自客户端的 RequestSecurityToken (RST) 消息、 对客户端进行身份验证，从 CA 请求证书和在 RequestSecurityTokenResponse (RSTR) 返回给客户端。 除了颁发的证书中，响应也包含提供 DM 客户端所需的配置。

RequestSecurityToken (RST) 必须具有用户凭据和证书申请。 RST SOAP 信封中的用户的凭据是 GetPolicies，一样，会因身份验证策略是否是 OnPremise 或联合。 BinarySecurityToken RST SOAP 正文中的包含 Base64 编码的 PKCS\#10 证书请求，生成基于注册策略的客户端。 客户端可以请求使用 MS WSTEP 证书之前使用 MS XCEP 请求的注册策略。 如果 PKCS\#由证书颁发机构 (CA) （密钥长度、 散列算法，以及匹配的证书模板等等） 接受 10 个证书请求，客户端可以注册成功。

RequestSecurityToken 将使用自定义的 TokenType (http:<span></span>/ / schemas.microsoft.com/5.0.0.0/ConfigurationManager/Enrollment/DeviceEnrollmentToken)，这是因为我们的注册标记了多个 X.509 v3 证书。 有关详细信息，请参阅响应部分。

RST 还可能指定的 AdditionalContext 项目，如数据库和版本数。 根据这些值，例如，web 服务可以返回特定于设备的和特定于版本的 DM 配置。

> **请注意** 该策略服务和注册服务必须在同一台服务器;也就是说，它们必须具有相同的主机名。

 
下面的示例演示注册的 OnPremise 身份验证 web 服务请求。

``` syntax
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
             <wsse:UsernameToken u:Id="uuid-cc1ccc1f-2fba-4bcf-b063-ffc0cac77917-4">
                <wsse:Username>user@contoso.com</wsse:Username>
                <wsse:Password wsse:Type=
                  "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordText">mypassword
                </wsse:Password>
             </wsse:UsernameToken>
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
                <ac:ContextItem Name="OSEdition">
                   <ac:Value> 4</ac:Value>
                </ac:ContextItem>
                <ac:ContextItem Name="OSVersion">
                   <ac:Value>10.0.9999.0</ac:Value>
                </ac:ContextItem>
                <ac:ContextItem Name="DeviceName">
                   <ac:Value>MY_WINDOWS_DEVICE</ac:Value>
                </ac:ContextItem>
                <ac:ContextItem Name="MAC">
                   <ac:Value>FF:FF:FF:FF:FF:FF</ac:Value>
                </ac:ContextItem>
                <ac:ContextItem Name="MAC">
                   <ac:Value>CC:CC:CC:CC:CC:CC</ac:Value>
                </ac:ContextItem>
                <ac:ContextItem Name="IMEI">
                   <ac:Value>49015420323756</ac:Value>
                </ac:ContextItem>
                <ac:ContextItem Name="IMEI">
                   <ac:Value>30215420323756</ac:Value>
                </ac:ContextItem>
                <ac:ContextItem Name="EnrollmentType">
                   <ac:Value>Full</ac:Value>
                </ac:ContextItem>
                <ac:ContextItem Name="DeviceType">
                   <ac:Value>CIMClient_Windows</ac:Value>
                </ac:ContextItem>
                <ac:ContextItem Name="ApplicationVersion">
                   <ac:Value>10.0.9999.0</ac:Value>
                </ac:ContextItem>
                <ac:ContextItem Name="DeviceID">
                   <ac:Value>7BA748C8-703E-4DF2-A74A-92984117346A</ac:Value>
                </ac:ContextItem>
                
                <ac:ContextItem Name="TargetedUserLoggedIn">
                   <ac:Value>True</ac:Value>
                </ac:ContextItem>
             </ac:AdditionalContext>
          </wst:RequestSecurityToken>
       </s:Body>
    </s:Envelope>
```

下面的示例演示注册 web 服务响应。

``` syntax
    <s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/" 
       xmlns:a="http://www.w3.org/2005/08/addressing" 
       xmlns:u="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">
       <s:Header>
          <a:Action s:mustUnderstand="1" >
             http://schemas.microsoft.com/windows/pki/2009/01/enrollment/RSTRC/wstep
          </a:Action>
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
                 <DispositionMessage xmlns="http://schemas.microsoft.com/windows/pki/2009/01/enrollment"/>           <RequestedSecurityToken>
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
   <!-- For Windows 10, we removed EnterpriseAppManagement from the enrollment 
        protocol. This configuration service provider is being deprecated for Windows 10. -->
</wap-provisioningdoc>
```

 






