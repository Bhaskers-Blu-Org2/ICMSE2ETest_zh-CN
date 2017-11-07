---
title: "从管理基础架构 （注销） 断开连接"
description: "断开连接可能会从手机用户通过本地或由 IT 管理员使用管理服务器远程启动。"
MS-HAID:
- p\_phdevicemgmt.disconnecting\_from\_the\_management\_infrastructure\_\_unenrollment\_
- p\_phDeviceMgmt.disconnecting\_from\_mdm\_unenrollment
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 33B2B248-631B-451F-B534-5DA095C4C8E8
ms.openlocfilehash: a1502f31f72f8de7b6057c68f531b630d68b1117
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="disconnecting-from-the-management-infrastructure-unenrollment"></a>从管理基础架构 （注销） 断开连接

断开连接可能会从手机用户通过本地或由 IT 管理员使用管理服务器远程启动。 得象初始连接，执行用户启动断开连接并启动创建工作场所帐户设置控制面板中的位置相同。 用户可以选择任意数量的原因，包括离开公司或获得新的设备，并对其 LOB 应用程序不再需要访问旧设备上断开连接。 当管理员启动时断开连接时，则注册客户端执行在其下一次的定期维护会话断开连接。 管理员可以选择断开连接用户的设备，或者他们已经离开公司后因为设备定期未能符合组织的安全设置策略。

连接断开，在客户端执行以下任务︰

-   删除允许安装和运行 LOB 应用程序的企业应用程序标记。 与该企业标记相关联的任何业务应用程序同样也会删除。
-   删除由 MDM 服务器配置的证书。
-   不再设置策略应用的管理基础结构的实施。
-   删除设备管理客户端配置和由 MDM 服务器，包括定期的维护任务添加其他设置配置。 除非用户重新连接它到管理基础架构，客户端仍不活跃。
-   报告成功启动解除关联到管理基础设施，如果管理员启动该进程。 请注意，在 Windows 中，用户启动解除关联报告给服务器作为最大的努力。


## <a name="in-this-topic"></a>本主题中

-   [用户启动断开连接](#user-initiated-disconnection)
-   [服务器启动断开连接](#server-initiated-disconnection)
-   [从工作访问设置页的注销](#unenrollment-from-work-access-settings-page)
-   [IT 管理员 – 请求断开连接](#it-admin-requested-disconnection)
-   [从 Azure Active Directory 联接的注销](#dataloss)


## <a name="user-initiated-disconnection"></a>用户启动断开连接

在 Windows 中，用户确认帐户删除命令并删除帐户之前，MDM 客户端将发送通知到 MDM 服务器通知的服务器后的帐户将被删除。 这是最佳的精力处理，不能重试是内置以确保通知已成功发送到设备。

此操作使用的 OMA DM 一般警报 1226年函数发送用户 MDM 注销用户报警到 MDM 服务器设备接受用户注销请求，但之前删除任何企业数据。 服务器应设置期望，并且注销可能成功或失败，服务器可以检查是否在预定的时间或向设备以查看是否回响应发送推式通知的回拨设备是否通过任何检查 unenrolled 设备。 如果服务器计划发送推式通知，应允许一定的延迟，使设备的注销工作完成的时间。

> **请注意** 用户注销是 OMA DM 标准。 关于 1226年一般警报的详细信息，请参阅 OMA 设备管理协议规范 (OMA TS DM\_协议 V1\_2\_1 20080617 A)，可从[OMA 网站](http://go.microsoft.com/fwlink/p/?LinkId=267526)。

 
供应商使用 Type 属性指定它是哪种类型的一般性警报。 对于设备启动 MDM 注销，报警类型为**com.microsoft:mdm.unenrollment.userrequest**。

用户选择 unenroll 后，MDM OMA DM 的所有活动会话将被终止。 在此之后，DM 客户端启动一个 DM 会话，包括用户 unenroll 一般警报将发送到服务器的第一个包中。

下面的示例演示包含泛型的警报消息 OMA DM 第一个包。 WP OMA DM 支持的详细信息，请参阅[支持的 OMA DM 协议](oma-dm-protocol-support.md)主题。

```
<SyncML xmlns=&#39;SYNCML:SYNCML1.2&#39;>
   <SyncHdr>
      <VerDTD>1.2</VerDTD>
      <VerProto>DM/1.2</VerProto>
      <SessionID>1</SessionID>
      <MsgID>1</MsgID>
      <Target>
         <LocURI>{unique device ID}</LocURI>
      </Target>
      <Source>
         <LocURI>https://www.thephone-company.com/mgmt-server</LocURI>
      </Source>
   </SyncHdr>
   <SyncBody>
      <Alert>
    <CmdID>2</CmdID>
        <Data>1226</Data> <!-- generic alert -->
        <Item>
          <Meta>
             <Type xmlns=”syncml:metinfo”> com.microsoft:mdm.unenrollment.userrequest</Type>
          <Format xmlns= “syncml:metinfo”>int</Format>
           </Meta>
        <Data>1</Data>
         </Item>
       </Alert>

<!-- other device information -->
      <Replace>
         <CmdID>2</CmdID>
         <Item>
            <Source>
               <LocURI>./DevInfo/DevID</LocURI>
            </Source>
         <Data>{unique device ID}</Data>
         </Item>
         <Item>
        ...
         </Item>
      </Replace>
      <Final/>
   </SyncBody>
</SyncML>
```

以前的数据包被发送后，注销过程开始。


## <a name="server-initiated-disconnection"></a>服务器启动断开连接

当服务器启动时断开连接时，会立即中止注册 id 的所有 undergoing 会话来避免死锁。 服务器不会响应注销，相反通用警报通知发送的邮件 id = 1。

``` syntax
<Alert>
      <CmdID>4</CmdID>
      <Data>1226</Data>
      <Item>
        <Meta>
          <Type xmlns="syncml:metinf">com.microsoft:mdm.unenrollment.userrequest</Type>
         <Format xmlns="syncml:metinf">int</Format>
        </Meta>
        <Data>1</Data>
      </Item>
</Alert>
```


<a href="" id="work-access"></a>
## <a name="unenrollment-from-work-access-settings-page"></a>从工作访问设置页的注销

如果将用户注册到 MDM 使用 Azure Active Directory (AAD 加入或通过添加 Microsoft 工作帐户)，MDM 帐户将显示在工作访问页。 但是，出和不能访问，则是灰显**断开连接**按钮。 用户可以删除该 MDM 帐户删除 AAD 关联到设备。

仅可以使用工作访问页以 unenroll 在以下情况下︰

-   未进行注册使用批量注册。
-   使用工作访问页创建注册。


<a href="" id="dataloss"></a>
## <a name="unenrollment-from-azure-active-directory-join"></a>从 Azure Active Directory 联接的注销

当用户注册到 MDM 通过 Azure 活动目录加入，然后断开连接注册时，系统不会警告用户将丢失窗口信息保护 (WIP) 的数据。 断开连接消息不指明 WIP 数据的丢失。

![aadj unenerollment](images/azure-ad-unenrollment.png)

当设备注册到 MDM 通过 Azure 活动目录加入并远程 unenrolled 时，设备可能进入一种状态，它必须被重新映像。 在设备的远程 unenrolled 从 MDM，还会删除 AAD 关联。 这一安全措施到位，以避免离开 corporated 设备处于非托管状态。

之前远程 unenrolling 公司的设备，您必须确保不是 Azure 租户的一部分设备上有至少一个管理员用户，否则设备将不具有任何管理员用户完成操作后。

在移动设备中，远程注销 Azure 活动目录联接的设备将会失败。 若要删除这些设备公司的内容，我们建议您远程擦除设备。

<a href="" id="it-admin-requested-disconnection"></a>
## <a name="it-adminrequested-disconnection"></a>IT 管理员 – 请求断开连接

服务器通过向客户端启动下一个 DM 会话期间使用 DMClient 配置服务提供程序的 Unenroll 节点的设备发出 Exec OMA DM SyncML XML 命令请求企业管理断开连接请求。 数据标记内 Exec 命令应该调配 DM 服务器 ProviderID 的价值。 有关详细信息，请参阅特定于企业的 DM 客户端配置主题。

断开连接完成后，通知用户已断开设备连接从企业管理。

 






