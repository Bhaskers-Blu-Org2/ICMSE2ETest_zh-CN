---
title: "SurfaceHub 的 CSP"
description: "使用 SurfaceHub 配置服务提供程序 (CSP) 来配置 Microsoft Surface 中心设置。 Windows 10 1511年版本中添加了该 CSP。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 36FBBC32-AD6A-41F1-86BF-B384891AA693
ms.openlocfilehash: c6c687fe8e69c3fb4ee34e99bdcd7b8808616343
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="surfacehub-csp"></a>SurfaceHub 的 CSP


使用 SurfaceHub 配置服务提供程序 (CSP) 来配置 Microsoft Surface 中心设置。 Windows 10 1511年版本中添加了该 CSP。

下面的关系图以树格式显示 SurfaceHub CSP 管理对象。

![曲面中心关系图](images/provisioning-csp-surfacehub.png)

<a href="" id="--vendor-msft-surfacehub"></a>**./Vendor/MSFT/SurfaceHub**  
面中心配置服务提供程序的根节点。

<a href="" id="deviceaccount"></a>**DeviceAccount**  
有关设置设备帐户信息的节点。 设备帐户是 Microsoft Exchange 帐户连接与 Skype 的业务，使人们能够加入计划的会议，Skype 进行业务联络和共享设备中的内容。 面中心管理员指南中有关设备帐户设置的详细信息，请参阅。

**若要使用 Azure Active Directory 中的设备帐户**

1.  设置 （针对 Azure AD) 的范围。
2.  设置一个有效的密码。
3.  执行 ValidateAndCommit 来验证对 Azure 的广告指定的用户名和密码组合。
4.  在验证过程中出现错误的情况下获取 ErrorContext

> **请注意** 如果该设备不能自动发现的 Exchange 服务器和会话启动协议 (SIP) 地址通过此信息，则应指定 ExchangeServer 和 SipAddress。

 

这里是 SyncML 示例。

``` syntax
 <SyncML xmlns="SYNCML:SYNCML1.2">
        <SyncBody>
            <Replace>
                <CmdID>1</CmdID>
                <Item>
                    <Target>
                        <LocURI>./Vendor/MSFT/SurfaceHub/DeviceAccount/UserPrincipalName</LocURI>
                    </Target>
                    <Meta>
                        <Format xmlns="syncml:metinf">chr</Format>
                    </Meta>
                    <Data>user@contoso.com</Data>
                </Item>
            </Replace>
            <Replace>
                <CmdID>2</CmdID>
                <Item>
                    <Target>
                        <LocURI>./Vendor/MSFT/SurfaceHub/DeviceAccount/Password</LocURI>
                    </Target>
                    <Meta>
                        <Format xmlns="syncml:metinf">chr</Format>
                    </Meta>
                    <Data>password</Data>
                </Item>
            </Replace>
            <Exec>
                <CmdID>3</CmdID>
                <Item>
                    <Target>
                        <LocURI>./Vendor/MSFT/SurfaceHub/DeviceAccount/ValidateAndCommit</LocURI>
                    </Target>
                </Item>
            </Exec>
            <Get>
                <CmdID>4</CmdID>
                <Item>
                    <Target>
                        <LocURI>./Vendor/MSFT/SurfaceHub/DeviceAccount/ErrorContext</LocURI>
                    </Target>
                </Item>
            </Get>
            <Final/> 
        </SyncBody>
    </SyncML>
```

**若要使用设备从 Active Directory 帐户**

1.  设置域名。
2.  设置用户名。
3.  设置一个有效的密码。
4.  执行 ValidateAndCommit 节点。

<a href="" id="deviceaccount-domainname"></a>**DeviceAccount/域名**  
当您使用 Active Directory 的设备帐户域。 要使用设备从 Active Directory 帐户，应为设备帐户指定域名和用户名。

数据类型为 char。 受支持的操作是获得和替换。

<a href="" id="deviceaccount-username"></a>**DeviceAccount/用户名**  
当您使用 Active Directory 的设备帐户用户名。 要使用设备从 Active Directory 帐户，应为设备帐户指定域名和用户名。

数据类型为 char。 受支持的操作是获得和替换。

<a href="" id="deviceaccount-userprincipalname"></a>**DeviceAccount/范围内**  
用户主体名称 (UPN) 设备的帐户。 要使用从 Azure Active Directory 或混合部署设备帐户，您应该指定设备帐户的 UPN。

数据类型为 char。 受支持的操作是获得和替换。

<a href="" id="deviceaccount-sipaddress"></a>**DeviceAccount/SipAddress**  
会话启动协议 (SIP) 地址的设备的帐户。 通常情况下，该设备将尝试自动发现的 SIP。 此字段只是要求如果自动检测失败。

数据类型为 char。 受支持的操作是获得和替换。

<a href="" id="deviceaccount-password"></a>**DeviceAccount/密码**  
设备的帐户的密码。

数据类型为 char。 受支持的操作是获得和替换。 获取允许进行此操作，但它将始终返回空。

<a href="" id="deviceaccount-validateandcommit"></a>**DeviceAccount/ValidateAndCommit**  
此方法验证所提供的数据，然后提交更改。

数据类型为 char。 受支持的操作被执行。

<a href="" id="deviceaccount-email"></a>**DeviceAccount/电子邮件**  
设备的帐户的电子邮件地址。

数据类型为 char。

<a href="" id="deviceaccount-passwordrotationperiod"></a>**DeviceAccount/PasswordRotationPeriod**  
指定是否启用自动密码轮换。 如果强制设备帐户的密码过期策略，请使用此设置以允许设备管理它自己的密码，通常情况下，无需手动更新的帐户信息，密码到期时对其进行更改。 您可以在任何时候使用 Active Directory （或 Azure 的广告） 重设密码。

有效值︰

-   0-启用密码轮换
-   1-已禁用

数据类型是 int。 受支持的操作是获得和替换。

<a href="" id="deviceaccount-exchangeserver"></a>**DeviceAccount/ExchangeServer**  
Exchange 服务器的设备的帐户。 通常情况下，该设备将尝试自动发现 Exchange 服务器。 此字段只是要求如果自动检测失败。

数据类型为 char。 受支持的操作是获得和替换。

<a href="" id="deviceaccount-calendarsyncenabled"></a>**DeviceAccount/CalendarSyncEnabled**  
指定是否启用日历同步和其他 Exchange 服务器服务。

数据类型是布尔值。 受支持的操作是获得和替换。

<a href="" id="deviceaccount-errorcontext"></a>**DeviceAccount/ErrorContext**  
如果调用 ValidateAndCommit 时出错，则此节点中的该错误的附加上下文。 下面是可能出现的错误值︰

<table>
<colgroup>
<col width="15%" />
<col width="20%" />
<col width="65%" />
</colgroup>
<thead>
<tr class="header">
<th>ErrorContext 值</th>
<th>阶段发生错误的位置</th>
<th>说明和建议</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1</p></td>
<td><p>未知</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>2</p></td>
<td><p>填充帐户</p></td>
<td><p>不能检索使用的用户名和密码的帐户详细信息供您选择。</p>
<ul>
<li>对于 Azure 的广告帐户，确保范围内和密码有效。</li>
<li>对于广告客户，确保的域名、 用户名和密码有效。</li>
<li>请确保指定的帐户具有 Exchange 服务器邮箱。</li>
</ul></td>
</tr>
<tr class="odd">
<td><p>3</p></td>
<td><p>填充 Exchange 服务器地址</p></td>
<td><p>不能自动发现您的 Exchange 服务器地址。 尝试手动指定 Exchange 服务器使用 ExchangeServer 字段的地址。</p></td>
</tr>
<tr class="even">
<td><p>4</p></td>
<td><p>验证 Exchange 服务器地址</p></td>
<td><p>无法验证 Exchange 服务器的地址。 确保 ExchangeServer 字段有效。</p></td>
</tr>
<tr class="odd">
<td><p>5</p></td>
<td><p>保存帐户信息</p></td>
<td><p>无法保存到系统的帐户的详细信息。</p></td>
</tr>
<tr class="even">
<td><p>6</p></td>
<td><p>验证 EAS 策略</p></td>
<td><p>设备的帐户使用不受支持的 EAS 策略。 请确保按照管理指南 》 的 EAS 策略的配置正确。</p></td>
</tr>
</tbody>
</table>

 

数据类型是 int。 受支持的操作是获得。

<a href="" id="maintenancehourssimple-hours"></a>**MaintenanceHoursSimple/小时**  
维护日程安排的节点。

<a href="" id="maintenancehourssimple-hours-starttime"></a>**开始时间 MaintenanceHoursSimple/小时**  
在几分钟内从午夜指定维护时段的开始时间。 例如，要设置一个上午 2:00 开始时间，请将此值设置为 120。

数据类型是 int。 受支持的操作是获得和替换。

<a href="" id="maintenancehourssimple-hours-duration"></a>**持续时间 MaintenanceHoursSimple/小时**  
以分钟为单位指定维护窗口的持续的时间。 例如，要设置 3 小时持续时间，请将该值设置为 180。

数据类型是 int。 受支持的操作是获得和替换。

<a href="" id="inboxapps"></a>**InBoxApps**  
框中的应用程序设置的节点。

<a href="" id="inboxapps-welcome"></a>**InBoxApps/欢迎**  
欢迎屏幕的节点。

<a href="" id="inboxapps-welcome-autowakescreen"></a>**AutoWakeScreen/InBoxApps/欢迎**  
在屏幕上使用运动传感器，会自动打开。

数据类型是布尔值。 受支持的操作是获得和替换。

<a href="" id="inboxapps-welcome-currentbackgroundpath"></a>**CurrentBackgroundPath/InBoxApps/欢迎**  
欢迎屏幕的背景图像。 若要设置，指定 https URL 到 PNG 文件 （仅 Png 支持出于安全原因）。

数据类型是字符串。 受支持的操作是获得和替换。

<a href="" id="inboxapps-welcome-meetinginfooption"></a>**MeetingInfoOption/InBoxApps/欢迎**  
在欢迎使用屏幕上显示会议信息。

有效值︰

-   0-组织者和时间只
-   1-管理器、 时间和主题。 主题被隐藏在私人会议。

数据类型是 int。 受支持的操作是获得和替换。

<a href="" id="inboxapps-wirelessprojection"></a>**InBoxApps/WirelessProjection**  
无线投影仪的应用程序设置的节点。

<a href="" id="inboxapps-wirelessprojection-pinrequired"></a>**InBoxApps/WirelessProjection/PINRequired**  
用户必须输入 PIN 来无线为设备项目。

数据类型是布尔值。 受支持的操作是获得和替换。

<a href="" id="inboxapps-wirelessprojection-enabled"></a>**InBoxApps/WirelessProjection/启用**  
启用无线设备的投影。

数据类型是布尔值。 受支持的操作是获得和替换。

<a href="" id="inboxapps-wirelessprojection-channel"></a>**InBoxApps/WirelessProjection/通道**  
Miracast 操作要使用的无线频道。 Wi-fi 联盟 Wi-Fi 直接规范定义支持的渠道。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>适用于所有区域中的所有 Miracast 发件人</p></td>
<td><p>1、 3、 4、 5、 6、 7、 8、 9、 10、 11</p></td>
</tr>
<tr class="even">
<td><p>适用于所有 5ghz 频段 Miracast 在所有区域中的发件人</p></td>
<td><p>36、 40、 44、 48</p></td>
</tr>
<tr class="odd">
<td><p>适用于所有 5 ghz 区段 Miracast 在除日本以外的所有地区的发件人</p></td>
<td><p>149、 153、 157、 161、 165</p></td>
</tr>
</tbody>
</table>

 

默认值为 255。 外部管理法规的问题，如果通道配置不正确驱动程序也无法启动，或将广播上了错误的频道 （这将不会寻求发件人）。

数据类型是 int。 受支持的操作是获得和替换。

<a href="" id="properties"></a>**属性**  
设备属性的节点。

<a href="" id="properties-friendlyname"></a>**属性/友好名称**  
该设备的友好名称。 这是他们想要使用无线设备项目时，用户看到的名称。

数据类型是字符串。 受支持的操作是获得和替换。

<a href="" id="momagent"></a>**MOMAgent**  
Microsoft 操作管理套件的节点。

<a href="" id="momagent-workspaceid"></a>**MOMAgent/WorkspaceID**  
要收集的数据的 Microsoft 操作管理套件区 ID 标识的 GUID。 将此设置为空字符串，以便禁用 MOM 代理。

数据类型是字符串。 受支持的操作是获得和替换。

<a href="" id="momagent-workspacekey"></a>**MOMAgent/WorkspaceKey**  
与工作区进行身份验证的主键。

数据类型是字符串。 受支持的操作是获得和替换。 获取操作允许的但它将始终返回一个空字符串。

 

 






