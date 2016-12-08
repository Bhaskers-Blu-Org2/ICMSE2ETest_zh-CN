---
title: "续订证书"
description: "使用一段时间后过期所注册的客户端证书。"
MS-HAID:
- p\_phdevicemgmt.certificate\_renewal
- p\_phDeviceMgmt.certificate\_renewal\_windows\_mdm
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: F910C50C-FF67-40B0-AAB0-CA7CE02A9619
ms.openlocfilehash: b75c9706cd9185df3105bd8e6424e6ebac73801e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="certificate-renewal"></a>续订证书


使用一段时间后过期所注册的客户端证书。 由服务器指定证书的到期日期。 为了确保连续访问企业应用程序，Windows 支持用户触发证书续订过程。 系统会提示用户提供的当前密码的公司帐户，并从注册服务器获取新的客户端证书注册客户端，并删除旧证书。 客户端生成一个新的专用/公共密钥对时，都会生成 PKCS\#7 请求，并有迹象 PKCS\#7 使用现有的证书请求。 在 Windows 中，还支持自动 MDM 客户机证书续订。

> **请注意** 请确保 EntDMID 在 DMClient 配置服务提供程序设置触发证书续订请求之前。

 

## <a name="in-this-topic"></a>本主题中


-   [自动证书续订请求](#automatic-certificate-renewal-request)
-   [证书续订计划配置](#certificate-renewal-schedule-configuration)
-   [证书续订响应](#certificate-renewal-response)
-   [在 MDM 注册和证书续订过程中支持的配置服务提供程序](#configuration-service-providers-supported-during-mdm-enrollment-and-certificate-renewal)

<a href="" id="automatic-certificate-renewal"></a>
## <a name="automatic-certificate-renewal-request"></a>自动证书续订请求


除了手动证书续订 Windows 包含对自动续订证书，也称为续订代表 (ROBO)，不需要任何用户交互的支持。 自动续订的注册客户端使用现有的 MDM 客户端证书执行客户端传输层安全 (TLS)。 在 SOAP 标头，则不需要用户安全令牌。 因此，MDM 证书注册服务器都需要支持客户端 TLS 证书自动续订证书基于客户端的身份验证。

> **请注意** 通过 ROBO 注册证书的续订证书的支持仅限于 Microsoft PKI。

 

自动续订证书是唯一受支持的 MDM 客户机证书续订方法为使用 WAB 身份验证 （AuthPolicy 设置为联盟的含义） 注册该设备。 这还意味着如果服务器支持的身份验证 WAB，MDM 证书注册服务器还必须要续订 MDM 客户机证书支持 TLS 客户端。

注册了 OnPremise 身份验证方法，用于向后兼容性，该设备的默认续订方法是用户手动证书续订。 但是，对于 Windows 的设备，或 MDM 管理 MDM 客户机证书注册阶段期间部分、 注册服务器或 MDM 服务器无法将设备配置为支持 CertificateStore/我/WSTEP/续订 URL 下的 CertificateStore CSP ROBOSupport 节点通过自动 MDM 客户机证书续订。 有关更新的详细信息相关的配置设置，请参阅 CertificateStore 配置服务提供程序。

与手动证书续订没有额外的 b64 编码的 PKCS\#7 消息内容，自动续订，PKCS\#7 消息内容并不单独编码的 b64。

在自动证书续订过程中，如果根证书不受信任设备，身份验证将失败。 请确保使用设备预安装的根证书或通过 CertificateStore 配置服务提供程序通过 DM 会话设置根证书之一。

在自动证书续订过程，该设备将拒绝 HTTP 重定向服务器请求，除非它是同一初始 MDM 注册过程中显式地接受用户的重定向 URL。

下面的示例演示了自动续订请求的详细信息。

```
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope" 
   xmlns:a="http://www.w3.org/2005/08/addressing" xmlns:u=
   "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">
   <s:Header>
      <a:Action s:mustUnderstand="1">
         http://schemas.microsoft.com/windows/pki/2009/01/enrollment/RST/wstep</a:Action>
      <a:MessageID>urn:uuid:61a17f2c-42e9-4a45-9c85-f15c1c8baee8</a:MessageID>
      <a:ReplyTo>
         <a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>
      </a:ReplyTo>
      <a:To s:mustUnderstand="1">
         https://dm.contoso.com/EnrollmentService/DeviceEnrollmentService.svc</a:To>
      <o:Security s:mustUnderstand="1" xmlns:o=
         "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
         <u:Timestamp u:Id="_0">
            <u:Created>2011-07-11T19:49:08.579Z</u:Created>
            <u:Expires>2011-07-11T19:54:08.579Z</u:Expires>
         </u:Timestamp>
         <o:UsernameToken u:Id="uuid-2a734df6-b227-4e60-82a8-ed53c574b718-5">
            <o:Username>user@contoso.com</o:Username>
            <o:Password o:Type=
               "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordText">                
            </o:Password>
         </o:UsernameToken>
      </o:Security>
   </s:Header>
   <s:Body>
      <RequestSecurityToken xmlns="http://docs.oasis-open.org/ws-sx/ws-trust/200512">
         <TokenType>
    http://schemas.microsoft.com/5.0.0.0/ConfigurationManager/Enrollment/DeviceEnrollmentToken
         </TokenType>
         <RequestType>http://docs.oasis-open.org/ws-sx/ws-trust/200512/Renew</RequestType>
         <BinarySecurityToken 
            ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd#PKCS7" 
            EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd#base64binary" 
            xmlns="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
            BinarySecurityTokenInsertedHere
         </BinarySecurityToken>
         <AdditionalContext xmlns="http://schemas.xmlsoap.org/ws/2006/12/authorization">
            <ContextItem Name="DeviceType">
               <Value>WindowsPhone</Value>
            </ContextItem>
            <ContextItem Name="ApplicationVersion">
               <Value>5.0.7616.0</Value>
            </ContextItem>
         </AdditionalContext>
      </RequestSecurityToken>
   </s:Body>
</s:Envelope>
```


<a href="" id="certificate-renewal-schedule"></a>
## <a name="certificate-renewal-schedule-configuration"></a>证书续订计划配置

在 Windows 中，只能注册 MDM 阶段设置续订期。 Windows 支持证书续订期限和续订失败重试将可由这两个 MDM 注册服务器配置及更高版本使用 CertificateStore CSP MDM 管理服务器 RenewPeriod 和 RenewInterval 节点。 该设备无法重试自动续订证书多次直到在证书过期。 手动证书续订，而不是只有一次，提醒用户的 Windows 设备将在每个更新重试时间直到该证书已过期提醒用户提供提示对话框。

有关参数的详细信息，请参阅 CertificateStore 配置服务提供程序。

与手动证书续订不同设备如果将不执行自动的 MDM 客户机证书续订的证书已过期。 要确保设备有足够的时间来执行自动续订，则建议您将设置续订期两个月 （40-60 天） 证书过期并设置更新之前重试间隔设置为每隔几天每隔 4-5 天如改为每 7 天 （每周） 来增加设备，在不同的星期数将连接的机会。

> **请注意** 以前注册的 Windows 8.1 MDM，然后升级到 Windows 10 台 pc，续订将触发注册证书。 此后，续订时间间隔配置 ROBO 反应。
> 对于 Windows Phone 8.1 升级到 Windows 10 移动设备，更新会在内部配置 ROBO。 这预期的和设计。

 

## <a name="certificate-renewal-response"></a>证书续订响应

当 RequestType 设置为重新设置时，web 服务将验证 （在附加到初始注册）︰

-   PKCS 的签名\#7 BinarySecurityToken 是正确的
-   客户端的证书是在续订期
-   证书的颁发由注册服务
-   请求者等同于初始登记的申请者
-   对于标准客户端的请求，客户端未被阻止

在完成验证后，web 服务中检索 PKCS\#内容从 PKCS 10\#7 BinarySecurityToken。 其余部分是相同初始登记，只不过置备 XML 只需要有新的证书由 CA 颁发。

> **请注意** 不必须分块的 HTTP 服务器响应;它必须作为一个邮件被发送。


下面的示例演示一个证书续订响应的详细信息。

```
<wap-provisioningdoc version="1.1">
   <characteristic type="CertificateStore">
<!-- Root certificate provision is only needed here if it is not in the device already -->      <characteristic type="Root">
         <characteristic type="System">
            <characteristic type="EncodedRootCertHashInsertedHere ">
               <parm name="EncodedCertificate" value="EncodedCertInsertedHere" />
            </characteristic>
         </characteristic>
      </characteristic>
      <characteristic type="My" >
         <characteristic type="User">
            <characteristic type="EncodedClientCertHashInsertedHere">
               <parm name="EncodedCertificate" value="EncodedCertInsertedHere" />
               <characteristic type="PrivateKeyContainer"/>
            </characteristic>
         </characteristic>
      </characteristic>
   </characteristic>
   <characteristic type="APPLICATION">
      <parm name="PROVIDER-ID" value="TestMDMServer"/>
   </characteristic>
</wap-provisioningdoc>
```

> **请注意** 客户端会收到一个新的证书，而不是初始证书续订。 管理员可以控制哪些客户端应使用的证书模板。 这些模板可能不同在续订时比初始注册时间。

 

<a href="" id="csp-support-during-enrollment-and-renewal"></a>
## <a name="configuration-service-providers-supported-during-mdm-enrollment-and-certificate-renewal"></a>在 MDM 注册和证书续订过程中支持的配置服务提供程序


在 MDM 注册和证书续订过程中支持下列配置服务提供程序。 配置服务提供程序引用的每个配置服务提供程序的详细说明，请参阅。

-   CertificateStore
-   w7 应用程序
-   DMClient
-   EnterpriseAppManagement

 






