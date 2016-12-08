---
title: "移动设备注册"
description: "移动设备注册是企业管理的第一阶段。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 08C8B3DB-3263-414B-A368-F47B94F47A11
ms.openlocfilehash: e84903ed8e91ff6e04aa36e9896289937317f052
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mobile-device-enrollment"></a>移动设备注册


移动设备注册是企业管理的第一阶段。 设备配置为 MDM 服务器在注册过程中使用的安全防范措施与通信。 只有经过验证的注册服务验证和经授权的设备可以通过他们的企业进行管理。

注册过程包括以下步骤︰

1.  发现的注册终结点

    此步骤提供注册终结点配置设置。

2.  证书安装

    此步骤处理用户身份验证、 证书生成和证书的安装。 将在以后使用已安装的证书来管理客户端/服务器安全套接字层 (SSL) 相互身份验证。

3.  DM 客户端资源调配

    此步骤将配置设备管理 (DM) 客户端连接到移动设备管理 (MDM) 服务器通过 DM SyncML 注册后通过 HTTPS (也称为开放移动联盟设备管理 (OMA DM) XML)。

## <a name="enrollment-protocol"></a>注册协议


有大量的跨所有平台注册协议更好地支持各种方案所做的更改。 关于移动设备注册协议的详细信息，请参阅[\[MS MDM\]︰ 移动设备管理协议](http://go.microsoft.com/fwlink/p/?LinkId=619346)和[\[MS MDE2\]︰ 移动设备注册协议版本 2]( http://go.microsoft.com/fwlink/p/?LinkId=619347)。

注册过程涉及以下步骤︰

**查询请求**  
   发现请求是通过 HTTP 返回 XML 的简单 HTTP post 调用。 返回的 XML 中包含身份验证 URL、 管理服务 URL 和用户凭据类型。

**证书注册策略**  
证书注册策略配置是 MS XCEP 协议中所述的一种实现\[MS XCEP\]: X.509 证书注册策略协议规范。 在规范第 4 部分提供策略请求和响应的一个示例。 X.509 证书注册策略协议具有匹配的服务器响应消息 (GetPoliciesResponse) 是最小的消息传递协议包含的单个客户端请求消息 (GetPolicies)。 有关详细信息，请参阅[\[MS XCEP\]: X.509 证书注册策略协议](http://go.microsoft.com/fwlink/p/?LinkId=619345)

**证书注册**  
证书注册是 MS WSTEP 协议的实现。

**管理配置**  
服务器发送置备 XML 包含服务器证书 （用于 SSL 服务器身份验证），客户端证书的企业 CA、 DM 客户端引导数据库信息 （对于客户端与管理服务器进行通信）、 企业应用程序的标记 （用于用户安装企业应用程序） 和公司中心应用程序下载的链接。

下列主题描述使用多种身份验证方法的端到端注册过程︰

-   [联合身份验证设备注册](federated-authentication-device-enrollment.md)
-   [证书身份验证设备注册](certificate-authentication-device-enrollment.md)
-   [内部部署身份验证设备注册](on-premise-authentication-device-enrollment.md)

> **请注意** 作为最佳操作，不要使用硬编码值的服务器端检查如︰
> -   用户代理字符串
> -   在注册过程中传递的 Uri 的任何固定
> -   特定的格式设置任何值除非另有说明，如格式的设备 id。

 

## <a name="prevent-mdm-enrollments"></a>防止 MDM 招生名额


启动 Windows 10 中，版本 1607，以防 MDM 注册加入域的计算机，您可以设置以下组策略︰

键︰\\软件\\策略\\Microsoft\\Windows\\CurrentVersion\\MDM

值︰ DisableRegistration

使用 GP 编辑器的路径是计算机配置&gt;管理模板&gt;Windows 组件&gt;MDM&gt;禁用 MDM 注册。

## <a name="enrollment-scenarios-not-supported"></a>不支持注册情况


以下情形不允许 MDM 招生名额︰

-   在 Windows 的桌面上内置的管理员帐户不能注册到 mdm。
-   在 Windows 桌面上的标准用户无法注册到 MDM 通过**设置**中的工作访问页。 要注册到 MDM 标准用户，我们建议使用资源调配包或到 Azure AD 加入设备，从**设置** - &gt; **系统** - &gt; **有关**。
-   注册 MDM 通过注册上的代表的 (EOBO) 到 Windows 8.1 设备可以升级到 Windows 10，但不是支持注册。 我们建议执行服务器启动 unenroll 去这些注册和再注册到 Windows 10 升级完成后。

## <a name="enrollment-migration"></a>注册迁移


**桌面︰**MDM 客户端升级后从 Windows 8.1 到 Windows 10，注册迁移开始第一次与 MDM 服务客户端启动同步。 注册迁移开始时间取决于 MDM 服务器配置。 例如，对于 Intune 它运行了每 6 小时一次。

直到注册迁移完成后，用户界面会显示没有注册和服务器推送操作将不起作用。

若要手动触发注册迁移，您可以运行 MDMMaintenenceTask。

**移动设备︰**MDM 客户端升级后从 Windows Phone 8.1 到 Windows 10 手机，注册迁移期间第一次启动执行升级后。

## <a name="enrollment-error-messages"></a>注册错误消息


注册服务器可以拒绝注册邮件使用 SOAP 错误的格式。 错误创建可发送，如下所示︰

``` syntax
<s:envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://www.w3.org/2005/08/addressing">
    <s:header>
        <a:action s:mustunderstand="1">http://schemas.microsoft.com/windows/pki/2009/01/enrollment/rstrc/wstep</a:action>
        <activityid correlationid="2493ee37-beeb-4cb9-833c-cadde9067645" xmlns="http://schemas.microsoft.com/2004/09/servicemodel/diagnostics">2493ee37-beeb-4cb9-833c-cadde9067645</activityid>
        <a:relatesto>urn:uuid:urn:uuid:0d5a1441-5891-453b-becf-a2e5f6ea3749</a:relatesto>
    </s:header>
    <s:body>
        <s:fault>
            <s:code>
                <s:value>s:receiver</s:value>
                <s:subcode>
                    <s:value>s:authorization</s:value>
                </s:subcode>
            </s:code>
            <s:reason>
                <s:text xml:lang="en-us">This User is not authorized to enroll</s:text>
            </s:reason>
        </s:fault>
    </s:body>
</s:envelope>
```

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th>命名空间</th>
<th>子代码</th>
<th>错误</th>
<th>说明</th>
<th>HRESULT</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top"><p>s:</p></td>
<td style="vertical-align:top"><p>MessageFormat</p></td>
<td style="vertical-align:top"><p>MENROLL_E_DEVICE_MESSAGE_FORMAT_ERROR</p></td>
<td style="vertical-align:top"><p>消息格式不正确</p></td>
<td style="vertical-align:top"><p>80180001</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>s:</p></td>
<td style="vertical-align:top"><p>身份验证</p></td>
<td style="vertical-align:top"><p>MENROLL_E_DEVICE_AUTHENTICATION_ERROR</p></td>
<td style="vertical-align:top"><p>无法识别的用户</p></td>
<td style="vertical-align:top"><p>80180002</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>s:</p></td>
<td style="vertical-align:top"><p>授权</p></td>
<td style="vertical-align:top"><p>MENROLL_E_DEVICE_AUTHORIZATION_ERROR</p></td>
<td style="vertical-align:top"><p>不允许注册用户</p></td>
<td style="vertical-align:top"><p>80180003</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>s:</p></td>
<td style="vertical-align:top"><p>CertificateRequest</p></td>
<td style="vertical-align:top"><p>MENROLL_E_DEVICE_CERTIFCATEREQUEST_ERROR</p></td>
<td style="vertical-align:top"><p>未能获取证书</p></td>
<td style="vertical-align:top"><p>80180004</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>s:</p></td>
<td style="vertical-align:top"><p>EnrollmentServer</p></td>
<td style="vertical-align:top"><p>MENROLL_E_DEVICE_CONFIGMGRSERVER_ERROR</p></td>
<td style="vertical-align:top"></td>
<td style="vertical-align:top"><p>80180005</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>答︰</p></td>
<td style="vertical-align:top"><p>InternalServiceFault</p></td>
<td style="vertical-align:top"><p>MENROLL_E_DEVICE_INTERNALSERVICE_ERROR</p></td>
<td style="vertical-align:top"><p>服务器命中意外的问题</p></td>
<td style="vertical-align:top"><p>80180006</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>答︰</p></td>
<td style="vertical-align:top"><p>InvalidSecurity</p></td>
<td style="vertical-align:top"><p>MENROLL_E_DEVICE_INVALIDSECURITY_ERROR</p></td>
<td style="vertical-align:top"><p>无法分析安全标头</p></td>
<td style="vertical-align:top"><p>80180007</p></td>
</tr>
</tbody>
</table>

 

在第 10 Windows 版本 1507，我们添加的 deviceenrollmentserviceerror 元素。 下面是一个示例︰

``` syntax
<s:envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://www.w3.org/2005/08/addressing">
    <s:header>
        <a:action s:mustunderstand="1">http://schemas.microsoft.com/windows/pki/2009/01/enrollment/rstrc/wstep</a:action>
        <activityid correlationid="2493ee37-beeb-4cb9-833c-cadde9067645" xmlns="http://schemas.microsoft.com/2004/09/servicemodel/diagnostics">2493ee37-beeb-4cb9-833c-cadde9067645</activityid>
        <a:relatesto>urn:uuid:urn:uuid:0d5a1441-5891-453b-becf-a2e5f6ea3749</a:relatesto>
    </s:header>
    <s:body>
        <s:fault>
            <s:code>
                <s:value>s:receiver</s:value>
                <s:subcode>
                    <s:value>s:authorization</s:value>
                </s:subcode>
            </s:code>
            <s:reason>
                <s:text xml:lang="en-us">device cap reached</s:text>
            </s:reason>
            <s:detail>
                <deviceenrollmentserviceerror xmlns="http://schemas.microsoft.com/windows/pki/2009/01/enrollment">
                    <errortype>devicecapreached</errortype>
                    <message>device cap reached</message>
                    <traceid>2493ee37-beeb-4cb9-833c-cadde9067645</traceid>
                </deviceenrollmentserviceerror>
            </s:detail>
        </s:fault>
    </s:body>
</s:envelope>
```

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>子代码</th>
<th>错误</th>
<th>说明</th>
<th>HRESULT</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top"><p>DeviceCapReached</p></td>
<td style="vertical-align:top"><p>MENROLL_E_DEVICECAPREACHED</p></td>
<td style="vertical-align:top"><p>用户已注册的设备太多。 删除或 unenroll 旧的要修复此错误。 用户可以修复它无需管理员的帮助。</p></td>
<td style="vertical-align:top"><p>80180013</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>DeviceNotSupported</p></td>
<td style="vertical-align:top"><p>MENROLL_E_DEVICENOTSUPPORTED</p></td>
<td style="vertical-align:top"><p>特定的平台 (如 Windows) 或版本不受支持。 没有点重试或调用管理员。 用户无法更新设备。</p></td>
<td style="vertical-align:top"><p>80180014</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>NotSupported</p></td>
<td style="vertical-align:top"><p>MENROLL_E_NOTSUPPORTED</p></td>
<td style="vertical-align:top"><p>通常不支持的移动设备管理 （可节省管理调用）</p></td>
<td style="vertical-align:top"><p>80180015</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>NotEligibleToRenew</p></td>
<td style="vertical-align:top"><p>MENROLL_E_NOTELIGIBLETORENEW</p></td>
<td style="vertical-align:top"><p>设备尝试续订但服务器拒绝请求。 客户端可能会显示此通知 Robo 是否失败。 请检查设备上的时间。 用户通过注册可以修复它。</p></td>
<td style="vertical-align:top"><p>80180016</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>InMaintenance</p></td>
<td style="vertical-align:top"><p>MENROLL_E_INMAINTENANCE</p></td>
<td style="vertical-align:top"><p>帐户正在维护，请稍后重试。 用户可以重试以后，但他们可能需要联系管理员，因为他们不知道当问题得到解决。</p></td>
<td style="vertical-align:top"><p>80180017</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>用户许可</p></td>
<td style="vertical-align:top"><p>MENROLL_E_USERLICENSE</p></td>
<td style="vertical-align:top"><p>许可的用户处于不良状态和阻止登记。 用户需要致电联系管理员。</p></td>
<td style="vertical-align:top"><p>80180018</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>InvalidEnrollmentData</p></td>
<td style="vertical-align:top"><p>MENROLL_E_ENROLLMENTDATAINVALID</p></td>
<td style="vertical-align:top"><p>服务器拒绝注册数据。 服务器可能未正确配置。</p></td>
<td style="vertical-align:top"><p>80180019</p></td>
</tr>
</tbody>
</table>

 

TraceID 是一个自由格式的文本节点的记录。 它应该确定此注册尝试服务器端状态。 支持可能会使用此信息来查找服务器为什么拒绝登记。

## <a name="related-topics"></a>相关的主题


-   [基于 Windows 的设备的 MDM 注册](mdm-enrollment-of-windows-devices.md)
-   [联合身份验证设备注册](federated-authentication-device-enrollment.md)
-   [证书身份验证设备注册](certificate-authentication-device-enrollment.md)
-   [内部部署身份验证设备注册](on-premise-authentication-device-enrollment.md)






