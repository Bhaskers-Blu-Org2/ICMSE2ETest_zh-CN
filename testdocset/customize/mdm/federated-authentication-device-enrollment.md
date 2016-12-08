---
title: "联合身份验证设备注册"
description: "本节提供了一种使用联合身份验证策略的移动设备注册协议。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 049ECA6E-1AF5-4CB2-8F1C-A5F22D722DAA
ms.openlocfilehash: 230f54c834822f6f2232b94b433a87c8bafc0e47
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="federated-authentication-device-enrollment"></a>联合身份验证设备注册


本节提供了一种使用联合身份验证策略的移动设备注册协议。 当身份验证策略设置为联盟时，被利用 web 身份验证代理注册客户端以获取安全令牌。 注册客户端调用 web 身份验证代理 API 内启动过程的响应消息。 服务器应该构建 web 身份验证代理程序页面以适合设备的屏幕，并应与现有注册用户界面保持一致。 因为结束页用作注册客户端的设备安全机密客户端证书请求调用过程返回从代理程序不透明的安全令牌。

&lt;AuthenticationServiceURL&gt;元素发现响应消息指定 web 身份验证代理页起始 URL。

有关 Windows 10 Microsoft 移动设备注册协议的详细信息，请参阅[\[MS MDE2\]︰ 移动设备注册协议版本 2]( http://go.microsoft.com/fwlink/p/?LinkId=619347)。

## <a name="in-this-topic"></a>本主题中


[发现服务](#discovery-service)  
[注册策略 web 服务](#enrollment-policy-web-service)  
[注册 web 服务](#enrollment-web-service)  

不支持 Windows 10 注册方案的列表，请参阅[注册不受支持的方案](mobile-device-enrollment.md#enrollment-scenarios-not-supported)。

## <a name="discovery-service"></a>发现服务


发现 web 服务提供了用户注册与管理服务电话所需的配置信息。 该服务通过 HTTPS （仅服务器身份验证） 是 rest 风格的 web 服务。

> **请注意** 发现服务的管理员必须创建的地址 enterpriseenrollment 的主机。*域\_名称*。 com。

 

设备的自动发现流程使用登录时已提交至工作场所设置屏幕的电子邮件地址的域名。 自动发现系统构造一个 URI，它使用此主机名通过追加到的电子邮件地址域的子域"enterpriseenrollment"，并将路径追加"/ EnrollmentServer/Discovery.svc"。 例如，如果电子邮件地址为“sample@contoso.com”,是第一个 Get 请求的结果 URI: http:<span></span>//enterpriseenrollment.contoso.com/EnrollmentServer/Discovery.svc

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
                <AuthPolicy>Federated</AuthPolicy>
            </AuthPolicies>
          </request>
        </Discover>
      </s:Body>
```

发现响应是 XML 格式，并包含下列字段︰

-   注册服务 URL (EnrollmentServiceUrl) – 指定的 URL 注册终结点公开的管理服务。 用户已通过身份验证后，该设备应调用此 URL。 此字段是必填字段。
-   身份验证策略 (AuthPolicy) – 指示哪种类型的身份验证是必需的。 对于 MDM 服务器中，OnPremise 是受支持的值，这意味着调用管理服务 URL 时，将验证用户。 此字段是必填字段。
-   在 Windows 中，联盟将作为另一种受支持的值。 这使得服务器可以利用 Web 身份验证代理程序执行自定义的用户身份验证，并使用认可的期限。

> **请注意** 不必须分块的 HTTP 服务器响应;它必须作为一个邮件被发送。

 

当身份验证策略被设置为注册客户机获取一个安全令牌将利用联盟、 Web 身份验证代理 (WAB)。 WAB 起始的页的 URL 提供的响应消息中发现服务。 注册客户端将调用 WAB API 中开始 WAB 过程的响应消息。 WAB 网页是服务器承载的 web 页。 服务器应生成这些页面可以很好地适应设备屏幕的大小，并尽可能在 MDM 注册用户界面的其他生成一致。 作为 endpage 的 WAB 从返回的不透明的安全令牌将用作注册客户端的设备安全机密客户端证书注册请求调用过程。

> **请注意** 而不是依赖于用户代理字符串传递期间身份验证来获取信息，如操作系统版本中，使用以下指南︰
> -   分析发现请求期间发送的数据中的操作系统版本。
> -   追加的 OS 版本为 AuthenticationServiceURL 中的参数。
> -   当操作系统发送身份验证的响应中分析出 AuthenticiationServiceURL 中的操作系统版本。

 

新的 XML 标记，AuthenticationServiceUrl，DiscoveryResponse XML 允许服务器指定 WAB 页起始 URL 中引入。 联合身份验证，必须存在此 XML 标记。

> **请注意** 注册客户端是在进行身份验证并返回安全令牌协议流方面不可知的。 而服务器可能直接提示输入用户凭据或输入到另一台服务器和目录服务具有的联盟协议，是独立于所有这些注册客户端。 要保持中立，所有协议流与身份验证有关的涉及注册客户端都是被动，即浏览器实现的。

 

以下是服务器的明确要求。

-   &lt;DiscoveryResponse&gt;&lt;AuthenticationServiceUrl&gt;元素必须支持 HTTPS。
-   身份验证服务器必须使用的设备受信任的根证书。 否则，WAP 调用将失败。
-   WP 不支持集成的身份验证窗口 (WIA) ADFS WAB 身份验证过程。 ADFS 2012 R2 如果使用需要进行配置，以尝试 Windows 的 WIA 设备。

注册客户端发出的 HTTPS 请求，如下所示︰

```
AuthenticationServiceUrl?appru=<appid>&amp;login_hint=<User Principal Name>
```

-   &lt;应用程序标识&gt;的窗体 ms-app://string
-   &lt;用户主体名称&gt;是注册的用户名，例如，user@constoso.com作为用户在注册登录页中输入。 此属性的值用作可以由身份验证服务器身份验证部分的提示。

完成身份验证后，身份验证服务器应具有开机自检方法操作的应用程序标识的标识查询字符串参数返回 HTML 窗体文档。

```
HTTP/1.1 200 OK 
Content-Type: text/html; charset=UTF-8
Vary: Accept-Encoding
Content-Length: 556

<!DOCTYPE>
<html>
   <head>
      <title>Working...</title>
      <script>
         function formSubmit() {
            document.forms[0].submit();
         }
           window.onload=formSubmit;
      </script>
   </head>
   <body>
    <!-- appid below in post command must be same as appid in previous client https request. -->
      <form method="post" action="ms-app://appid">
         <p><input type="hidden" name="wresult" value="token value"/></p>
         <input type="submit"/>
      </form>
   </body>
</html>
```

服务器已开机自检方法操作中所述 （URL 方案是 ms app） 窗体 ms app://string 的重定向 url 发送公告。 安全令牌值是 base64 编码的字符串"http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd\#base64binary"中包含&lt;wsse:BinarySecurityToken&gt; EncodingType 属性。 Windows 执行二进制文件进行编码时它将其发送回注册服务器，它是只是 HTML 编码的形式。 此字符串是不透明的注册客户端，则为客户端没有解释该字符串。

下面的示例演示从要求身份验证通过 WAB 发现 web 服务接收到的响应。

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
            <AuthPolicy>Federated</AuthPolicy>
            <EnrollmentVersion>3.0</EnrollmentVersion>
            <EnrollmentPolicyServiceUrl>
              https://enrolltest.contoso.com/ENROLLMENTSERVER/DEVICEENROLLMENTWEBSERVICE.SVC
            </EnrollmentPolicyServiceUrl>
            <EnrollmentServiceUrl>
              https://enrolltest.contoso.com/ENROLLMENTSERVER/DEVICEENROLLMENTWEBSERVICE.SVC
            </EnrollmentServiceUrl>
            <AuthenticationServiceUrl>
              https://portal.manage.contoso.com/LoginRedirect.aspx
            </AuthenticationServiceUrl>
          </DiscoverResult>
        </DiscoverResponse>
      </s:Body>
    </s:Envelope>
```

## <a name="enrollment-policy-web-service"></a>注册策略 web 服务


策略服务是可选的。 默认情况下，如果未不指定任何策略，最小密钥长度是 2 k 和哈希算法是 sha-1。

此 web 服务实现的 X.509 证书注册策略协议 (MS XCEP) 规范的允许自定义证书注册，以匹配在不同时间的不同安全需求的企业 （加密灵活性）。 该服务处理来自客户端的 GetPolicies 消息、 对客户端进行身份验证和 GetPoliciesResponse 消息中返回匹配的注册策略。

联合身份验证策略，安全令牌凭据提供在请求消息中使用&lt;wsse:BinarySecurityToken&gt;元素\[WSS\]。 发现响应节中所述检索安全令牌。 身份验证信息如下所示︰

-   wsse:Security︰ 注册客户端实现&lt;wsse:Security&gt;中定义的元素\[WSS\]节 5。 &lt;Wsse:Security&gt;必须的子元素， &lt;s:Header&gt;元素。
-   wsse:BinarySecurityToken︰ 注册客户端实现&lt;wsse:BinarySecurityToken&gt;中定义的元素\[WSS\]节 6.3。 &lt;Wsse:BinarySecurityToken&gt;元素必须包含的子元素&lt;wsse:Security&gt;在 SOAP 标头中的元素。

在查询响应中所述的部分，包括&lt;wsse:BinarySecurityToken&gt;元素是不透明的注册客户端，客户端不解释字符串，和包含该元素的达成一致的安全令牌身份验证服务器 (中标识&lt;AuthenticationServiceUrl&gt;元素的&lt;DiscoveryResponse&gt;和企业服务器。

&lt;Wsse:BinarySecurityToken&gt;元素中包含使用 base64 编码的字符串。 注册客户端使用安全令牌来自的身份验证服务器和 base64-编码的标记来填充&lt;wsse:BinarySecurityToken&gt;元素。 wsse:BinarySecurityToken/属性/值︰ &lt;wsse:BinarySecurityToken&gt;属性值必须为"http:<span></span>/ / schemas.microsoft.com/5.0.0.0/ConfigurationManager/Enrollment/DeviceEnrollmentUserToken"。

wsse:BinarySecurityToken/属性/EncodingType: &lt;wsse:BinarySecurityToken&gt; EncodingType 属性必须是"http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd\#base64binary"。

以下是一个注册策略请求接收到的安全令牌作为客户端凭据。

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
          <wsse:BinarySecurityToken  ValueType= 
    "http: //schemas.microsoft.com/5.0.0.0/ConfigurationManager/Enrollment/DeviceEnrollmentUserToken"
          EncodingType=
          "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd#base64binary"
          xmlns=
          "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
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
      </s:Body>
    </s:Envelope>
```

对用户进行验证后，web 服务检索用户应与注册并创建基于证书模板属性的注册策略的证书模板。 响应的示例可以在 MSDN 上找到。

MS XCEP 支持非常灵活地进行注册策略使用各种复杂类型和特性。 Windows 设备，我们将首先为 minimalKeyLength、 hashAlgorithmOIDReference 策略和 CryptoProviders 支持。 HashAlgorithmOIDReference 具有相关 OID OIDReferenceID 和 policySchema 在 GetPolicesResponse 中。 PolicySchema 是指证书模板版本。 版本 3 的 MS XCEP 支持哈希算法。

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

请注意，RequestSecurityToken 将使用自定义的 TokenType (http:<span></span>/ / schemas.microsoft.com/5.0.0.0/ConfigurationManager/Enrollment/DeviceEnrollmentToken)，这是因为我们的注册标记了多个 X.509 v3 证书。 有关详细信息，请参阅响应部分。

RST 还可能指定的 AdditionalContext 项目，如数据库和版本数。 根据这些值，例如，web 服务可以返回特定于设备的和特定于版本的 DM 配置。

> **请注意** 该策略服务和注册服务必须在同一台服务器;也就是说，它们必须具有相同的主机名。

 

下面的示例演示注册的联合身份验证 web 服务请求。

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
          <wsse:BinarySecurityToken  wsse:ValueType= 
    "http:"//schemas.microsoft.com/5.0.0.0/ConfigurationManager/Enrollment/DeviceEnrollmentUserToken
          wsse:EncodingType=
          http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd#base64binary"
          
    >
          B64EncodedSampleBinarySecurityToken
          </wsse:BinarySecurityToken>
        </wsse:Security>
      </s:Header>
      <s:Body>
        <wst:RequestSecurityToken>
          <wst:TokenType>
            http://schemas.microsoft.com/5.0.0.0/ConfigurationManager/Enrollment/DeviceEnrollmentToken
          </wst:TokenType>
          <wst:RequestType>
            http://docs.oasis-open.org/ws-sx/ws-trust/200512/Issue
          </wst:RequestType>
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
```

后对该请求进行验证，web 服务查找分配的证书模板为客户端、 更新它如果需要请发送 PKCS\#10 向 CA 请求，处理来自 CA 的响应、 构造 OMA 客户端置备 XML 格式，并将其返回 RequestSecurityTokenResponse (RSTR) 中。

> **请注意** 不必须分块的 HTTP 服务器响应;它必须作为一个邮件被发送。

 

类似于在 RST TokenType，RSTR 将使用自定义的值类型中 BinarySecurityToken (http:<span></span>/ / schemas.microsoft.com/ConfigurationManager/Enrollment/DeviceEnrollmentProvisionDoc)，这是因为标记了多个 X.509 v3 证书。

置备 XML 包含︰

-   所请求的证书 （必需）
-   DM 客户端配置 （必需）

如果有的话，客户端将安装客户端证书、 企业根证书和中间 CA 证书。 当 DM 客户端到服务器回拨时，DM 配置包括名称和地址的 DM 服务器，使用，和日程表的客户端证书。

置备 XML 注册应包含一个根证书和一个链结 MDM 客户机证书所需的中间 CA 证书的最多。 OMA DM 会话期间无法调配其他根和中间 CA 证书。

当资源调配根和中间 CA 证书，支持的 CSP 节点路径是︰ CertificateStore/根/系统的资源调配，CertificateStore/我/用户对资源调配的中间 CA 证书的根证书。

下面是示例 RSTR 消息和 OMA 客户端配置 RSTR 内的 XML 的示例。 有关配置服务提供程序 (Csp) 的置备 XML 中使用的详细信息，请参阅企业设置、 策略和应用程序管理部分。

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

下面的代码演示示例置备 XML （在前面包作为安全令牌中显示）︰

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
          <parm name="UPN" value="UserPrincipalName@contoso.com" datatype="string" /> 
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
        protocol. -->
</wap-provisioningdoc>
```

**备注**

-   &lt;参数名称&gt;和&lt;特征类型 =&gt; w7 应用 CSP XML 中的元素是否区分大小写并且必须全部大写。
-   W7 应用程序特性，在 XML 中应提供客户端和 APPSRV 的凭据。
-   在本文档的部分[企业设置、 策略和应用程序管理](windows-mdm-enterprise-settings.md)位于这些设置的详细的说明。
-   **PrivateKeyContainer**特性是必需的必须是注册登记的置备 XML 中存在。 其他重要设置将设备配置资源调配可以连接的位置**提供程序 ID**、**名称**和**地址**参数元素，其中需要包含的唯一 ID 和您的 DM 提供程序的名称和地址。 ID 和名称可以是任意值，但它们必须是唯一的。
-   另一个重点是 SSLCLIENTCERTSEARCHCRITERIA，用于选择要用于客户端身份验证的证书。 搜索基于签名的用户证书的主题属性。
-   CertificateStore/WSTEP 使证书续订。 如果服务器不支持它，则不设置它。

 






