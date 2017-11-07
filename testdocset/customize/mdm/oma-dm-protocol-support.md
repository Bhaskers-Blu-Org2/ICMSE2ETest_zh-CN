---
title: "OMA DM 协议支持"
description: "OMA DM 协议支持"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: e882aaae-447e-4bd4-9275-463824da4fa0
ms.openlocfilehash: 993b24c5659c8985b2a1d374cd5bee671f7747cc
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="oma-dm-protocol-support"></a>OMA DM 协议支持

OMA DM 客户端与服务器通过 HTTPS 进行通信，并作为消息有效负载使用 DM 同步 (OMA DM v1.2)。 本主题介绍了 DM 客户端支持一般的 OMA DM 功能。 [OMA 网站](http://go.microsoft.com/fwlink/p/?LinkId=267526)上找不到 OMA DM 协议 v1.2 的完整说明。


## <a name="in-this-topic"></a>本主题中

-   [OMA DM 标准](#oma-dm-standards)

-   [OMA DM 协议公共元素](#protocol-common-elements)

-   [设备管理会话](#device-management-session)

-   [用户与目标设备的配置目标](#user-targeted-vs-device-targeted-configuration)

-   [SyncML 响应代码](#syncml-response-codes)


## <a name="oma-dm-standards"></a>OMA DM 标准

下表显示了使用 Windows 的 OMA DM 标准。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>常规区域</th>
<th>OMA DM 标准支持</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top"><p>数据传输和会话</p></td>
<td style="vertical-align:top"><ul>
<li><p>客户端启动远程 DM HTTPS 会话通过 SSL。</p></li>
<li><p>通过 SSL 的 HTTPS DM 会话远程。</p></li>
<li><p>远程 DM 服务器启动通知使用 WAP 推通过短消息服务 (SMS)。 不使用企业管理。</p></li>
<li><p>通过 WAP 推通过 SMS 的远程引导。 不使用企业管理。</p></li>
</ul></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>引导数据库的 XML</p></td>
<td style="vertical-align:top"><ul>
<li><p>OMA 客户端配置 XML。</p></li>
</ul></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>DM 协议命令</p></td>
<td style="vertical-align:top"><p>下面的列表显示设备使用的命令。 OMA DM 命令元素的详细信息，请参阅&quot;SyncML 表示协议设备管理使用情况 (OMA-SyncML-DMRepPro-V1_1_2-20030613-A)&quot;从[OMA 网站](http://go.microsoft.com/fwlink/p/?LinkId=267526)可用。</p>
<ul>
<li><p>添加 （隐式添加支持）</p></li>
<li><p>警报 （DM 警报）︰ 一般警报 (1226) 当用户触发 MDM 注销操作设备或 CSP 完成某些异步操作时使用企业管理客户端。 设备警报 (1224) 用于某些触发设备事件通知服务器。</p></li>
<li><p>原子︰ 请注意，不支持执行跟替换同一节点内的原子元素上添加命令。 嵌套的原子和 Get 命令不允许，将生成错误代码 500。</p></li>
<li><p>删除︰ DM 树中，并在该节点下的整个子树中移除节点，如果有的话</p></li>
<li><p>Exec︰ 调用客户端设备上的可执行文件</p></li>
<li><p>获取︰ 检索数据从客户端设备中;对于内部节点，在数据元素的子节点名称返回 URI 编码格式</p></li>
<li><p>替换︰ 将客户端设备上的数据覆盖</p></li>
<li><p>结果︰ Get 命令的数据结果返回给 DM 服务器</p></li>
<li><p>序列︰ 指定必须处理一组命令的顺序</p></li>
<li><p>状态︰ 表示操作的完成状态 （成功或失败）</p></li>
</ul>
<p>如果以下元素的其中一个下︰ 是不是一个有效的 OMA DM 命令的 XML 元素，该元素返回状态代码 400:</p>
<ul>
<li><p>SyncBody</p></li>
<li><p>原子</p></li>
<li><p>Sequence</p></li>
</ul>
<p>如果没有 CmdID DM 命令中提供，该客户端返回空白状态元素和 400 的状态代码。</p>
<p>如果原子元素嵌套的则会返回以下状态代码︰</p>
<ul>
<li><p>嵌套的原子命令返回 500。</p></li>
<li><p>父原子命令返回 507。</p></li>
</ul>
<p>有关原子的命令的详细信息，请参阅 OMA DM 协议公共元素。</p>
<p>不支持执行跟替换同一节点内的原子元素上添加命令。</p>
<p>无法启动 LocURI &quot; / &quot;。</p>
<p>设备会忽略中 SyncHdr 元的 XML 标记。</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>OMA DM 标准对象</p></td>
<td style="vertical-align:top"><ul>
<li><p>DevInfo</p></li>
<li><p>DevDetail</p></li>
<li><p>OMA DM DMS 帐户对象 （OMA DM 1.2 版）</p></li>
</ul></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>安全性</p></td>
<td style="vertical-align:top"><ul>
<li><p>身份验证 DM 服务器启动通知 SMS 消息 （不使用企业管理）</p></li>
<li><p>应用程序层基本和 MD5 客户端身份验证</p></li>
<li><p>对服务器和应用程序级别的 MD5 凭据进行身份验证</p></li>
<li><p>数据完整性和 HMAC 在应用程序级别的身份验证</p></li>
<li><p>基于 SSL 级别证书的客户端/服务器身份验证、 加密和数据完整性检查</p></li>
</ul></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>Nodes</p></td>
<td style="vertical-align:top"><p>在 OMA DM 树中，下列规则适用于节点名称︰</p>
<ul>
<li><p>&quot;.&quot; 可以是节点名称的一部分。</p></li>
<li><p>节点名称不能为空。</p></li>
<li><p>节点名称不能为只有星号 （*） 字符。</p></li>
</ul></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>自动配置文件</p></td>
<td style="vertical-align:top"><p>置备 XML 必须使用标准格式并按照[SyncML 表示协议](http://go.microsoft.com/fwlink/p/?LinkId=526905)规范中的定义。</p>
<p>如果在 SyncBody 下，是不是有效的 OMA DM 命令的 XML 元素，该元素返回状态代码 400。</p>
<div class="alert">
<strong>请注意</strong>  
<p>若要表示一个 Unicode 字符串作为 URI，首先对字符串进行编码为 utf-8。 然后对每个使用 URI 编码 utf-8 字节编码。</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>WBXML 支持</p></td>
<td style="vertical-align:top"><p>Windows 支持发送和接收 SyncML XML 格式和编码的 WBXML 格式中。 这是可配置使用 w7 应用程序特性下的 DEFAULTENCODING 节点在注册过程中。 有关 WBXML 编码的详细信息，请参阅第 8 节的[SyncML 表示协议](http://go.microsoft.com/fwlink/p/?LinkId=526905)规范。</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>大对象的处理</p></td>
<td style="vertical-align:top"><p>Windows 10 1511，版本中添加了对大对象上载到服务器的客户端支持。</p></td>
</tr>
</tbody>
</table>


<a href="" id="protocol-common-elements"></a>
##OMA DM 协议公共元素

其他 OMA DM 元素类型使用通用元素。 下表列出了用于配置设备的 OMA DM 常见元素。 有关 OMA DM 常见元素的详细信息，请参阅"SyncML 表示协议设备管理用法"(OMA SyncML DMRepPro V1\_1\_2 20030613 A) 可从[OMA 网站](http://go.microsoft.com/fwlink/p/?LinkId=526900)。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>元素</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top"><p>问题</p></td>
<td style="vertical-align:top"><p>指定身份验证质询。 服务器或客户端可以发送质询到其他如果没有凭据或不适当的凭据被给与原始请求消息中。</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>Cmd</p></td>
<td style="vertical-align:top"><p>指定状态元素中引用的 OMA DM 命令的名称。</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>CmdID</p></td>
<td style="vertical-align:top"><p>指定 OMA DM 命令的唯一标识符。</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>CmdRef</p></td>
<td style="vertical-align:top"><p>指定的状态或结果返回信息的命令 ID。 此元素采用相应的请求消息的 CmdID 元素的值。</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>凭据</p></td>
<td style="vertical-align:top"><p>指定为该邮件的原始发件人身份验证凭据。</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>最终</p></td>
<td style="vertical-align:top"><p>指示当前消息包中的最后一条消息。</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>LocName</p></td>
<td style="vertical-align:top"><p>目标和源元素，用于发送用于 MD5 验证的用户 ID 中指定显示名称。</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>LocURI</p></td>
<td style="vertical-align:top"><p>指定的目标或源位置的地址。 如果地址中包含非字母数字字符，它必须被正确地转义 URL 编码标准。</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>邮件 Id</p></td>
<td style="vertical-align:top"><p>指定错误信息 OMA DM 会话的唯一标识符。</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>MsgRef</p></td>
<td style="vertical-align:top"><p>指定相应的请求消息的 ID。 此元素将请求消息的邮件 Id 元素的值。</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>RespURI</p></td>
<td style="vertical-align:top"><p>指定的收件人发送此消息的响应时必须使用的 URI。</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>会话标识符</p></td>
<td style="vertical-align:top"><p>指定包含的信息与相关的 OMA DM 会话的标识符。</p>
<div class="alert">
<strong>请注意</strong> 服务器不会通知该设备支持 （通过 SyncApplicationVersion DMClient CSP 中的节点） 的新版本，如果台式客户机以十进制格式整数返回会话 Id 和移动设备客户端以字符串形式返回 2 个字节。 如果服务器支持 DM 会话同步版本 2.0 中，使用 Windows 10，桌面和移动设备客户端返回 2 个字节。
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>源</p></td>
<td style="vertical-align:top"><p>指定消息的源地址。</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>SourceRef</p></td>
<td style="vertical-align:top"><p>指定相应的请求消息的来源。 此元素采用请求消息源元素的值，并返回中的状态或结果元素。</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>Target</p></td>
<td style="vertical-align:top"><p>指定的地址的节点，在 DM 树，OMA DM 命令的目标。</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>TargetRef</p></td>
<td style="vertical-align:top"><p>相应的请求消息中指定的目标地址。 此元素采用请求消息目标元素的值，并返回中的状态或结果元素。</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>VerDTD</p></td>
<td style="vertical-align:top"><p>指定用于表示消息的 OMA DM 表示协议规范的主要和次要版本标识符。</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>VerProto</p></td>
<td style="vertical-align:top"><p>指定与消息一起使用的 OMA DM 协议规范的主要和次要版本标识符。</p></td>
</tr>
</tbody>
</table>


## <a name="device-management-session"></a>设备管理会话

设备管理 (DM) 会话包含一系列命令 DM 服务器和客户端设备之间交换。 服务器发送命令，指示必须在客户端设备的管理树执行的操作。 客户端通过发送包含结果以及任何请求的状态信息的命令做出响应。

短的 DM 会话可总结如下︰

服务器向客户端设备来检索内容之一的管理树中的节点发送一个 Get 命令。 设备执行操作，并使用结果命令，其中包含请求的内容作出反应。

DM 会话可以分为两个阶段︰
1.  **安装阶段**︰ 在触发事件响应，客户端设备将启动消息发送到 DM 服务器。 设备和服务器交换需要身份验证和设备信息。 这一阶段的步骤 1、 2 和 3 下表中的表示。
2.  **管理阶段**︰ DM 服务器是在控件中。 它将管理命令发送到设备，该设备响应。 第二阶段结束时 DM 服务器停止发送命令并终止会话。 这一阶段表示通过 3、 4 和 5 下表中的步骤。

下表显示在典型的 DM 会话过程中的事件序列。

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>步骤</th>
<th>操作</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top"><p>1</p></td>
<td style="vertical-align:top"><p>DM 客户端调用来管理服务器回叫</p>
<p>企业级方案 – 设备任务计划调用 DM 客户端。</p></td>
<td style="vertical-align:top"><p>MO 服务器发送服务器触发器消息调用 DM 客户端。</p>
<p>触发器消息包含的服务器 ID 并告诉客户端设备来启动与服务器的会话。 客户端设备对触发器消息进行身份验证，并验证服务器有权与之通信。</p>
<p>企业级方案-在预定的时间，DM 客户端调用定期回叫企业管理服务器通过 HTTPS。</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>2</p></td>
<td style="vertical-align:top"><p>通过 IP 连接来启动会话，设备会发送一条消息。</p></td>
<td style="vertical-align:top"><p>此消息中包含的设备信息和凭据。 在客户端和服务器执行相互身份验证，通过 SSL 通道还是在 DM 应用程序级别。</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>3</p></td>
<td style="vertical-align:top"><p>DM 服务器的响应，通过 IP 连接 (HTTPS)。</p></td>
<td style="vertical-align:top"><p>服务器发送初始设备管理命令，如果有的话。</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>4</p></td>
<td style="vertical-align:top"><p>设备响应服务器管理命令。</p></td>
<td style="vertical-align:top"><p>此邮件包含执行指定的设备管理操作的结果。</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>5</p></td>
<td style="vertical-align:top"><p>DM 服务器终止会话，或发送另一个命令。</p></td>
<td style="vertical-align:top"><p>DM 会话重复出现结束或第 4 步。</p></td>
</tr>
</tbody>
</table>

 

表中的步骤编号不表示邮件标识号 (邮件 Id)。 来自服务器的所有消息必须都具有邮件 Id 都是唯一在会话中，对第一条消息，从 1 开始并增加增量为 1 的其他各个邮件。 有关邮件 Id 和 OMA SyncML 协议的详细信息，请参阅"OMA 设备管理表示协议"(OMA TS DM\_RepPro V1\_2 20070209 A) 可从[OMA 网站](http://go.microsoft.com/fwlink/p/?LinkId=526900)。

OMA DM 应用程序级相互身份验证期间，如果到服务器的请求中的凭据元素的设备响应代码是 212，没有进一步的身份验证需要 DM 会话的其余部分。 在 MD5 验证，可以返回那个问题。 然后下一步的问题现时必须对使用 MD5 摘要下一步的 DM 会话启动时。

如果请求包含凭据，并对请求的响应代码是 200，必须在下一个请求中发送相同的凭据。 如果是包括在内的问题元素和 MD5 验证是必需的是通过下一步的问题元素通过现时用于下一个请求创建新的摘要。

基本或 MD5 客户端身份验证、 MD5 服务器身份验证、 MD5 哈希值和 MD5 现时有关详细信息，请参阅 OMA 设备管理安全性指标 (OMA TS DM\_安全 V1\_2\_1 20080617 A)，身份验证响应代码 OMA 设备管理协议规范中的处理和分步示例 (OMA TS DM\_协议 V1\_2\_1 20080617 A)，可从[OMA 网站](http://go.microsoft.com/fwlink/p/?LinkId=526900)。


## <a name="user-targeted-vs-device-targeted-configuration"></a>用户与目标设备的配置目标

Csp 和每个用户配置支持的策略，MDM 服务器无法将目标用户设置值发送到注册 MDM 用户主动登录设备。 设备会通知服务器登录状态通过设备警报 (1224) 警报类型 = 在 DM pkg\#1。

此警报的数据部分可能是下列字符串之一︰

-   用户 – 注册设备的用户是主动登录。 MDM 服务器可以发送用户特定的配置，对于每个用户配置支持的 Csp/策略
-   其他人-另一个用户登录，但该用户不具有 MDM 帐户。 服务器仅可在应用范围的设备配置，如将配置应用到设备中的所有用户。
-   无 – 没有活动用户登录。 服务器仅可在应用设备配置并可用的配置仅限于设备环境 （没有活动用户登录

下面是一个警报的示例︰

```
<Alert>
        <CmdID>1</CmdID>
        <Data>1224</Data>
        <Item>
            <Meta>
                <Type xmlns=”syncml:metinf”>com.microsoft/MDM/LoginStatus</Type>
                <Format xmlns=”syncml:metinf”>chr</Format>
            </Meta>
            <Data>user</Data>
        </Item>
    </Alert>
```

服务器将通知该设备是否是针对用户或设备的管理节点的 LocURL 的前缀与目标配置。 / 用户输入用户的目标配置，或。 / 设备的设备目标配置。 默认情况下，如果使用任何前缀。 / 设备或。 用户，它是为目标设备配置。

下面的 LocURL 显示每个用户的 CSP 节点配置︰ **./user/vendor/MSFT/EnterpriseModernAppManagement/AppInstallation/&lt;PackageFamilyName&gt;/StoreInstall**

下面的 LocURL 演示每个设备的 CSP 节点配置︰ **./device/vendor/MSFT/RemoteWipe/DoWipe**


<a href="" id="syncml-response-codes"></a>
## <a name="syncml-response-status-codes"></a>SyncML 响应状态代码

在使用时 SyncML OMA DM，有标准的响应返回的状态代码。 下表列出了您很可能会看到的常见 SyncML 响应的状态代码。 SyncML 响应状态代码的详细信息，请参阅部分 10 的[SyncML 表示协议](http://go.microsoft.com/fwlink/p/?LinkId=526905)规范。

| 状态代码 | 说明                                                                                                                                                                                                                       |
|-------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 200         | SyncML 命令成功完成。                                                                                                                                                                                        |
| 202         | 接受处理。 这通常是异步操作，如运行应用程序的远程执行的请求。                                                                                                |
| 212         | 接受的身份验证。 通常情况下您将仅看到此响应 （用于在 OMA DM 标准身份验证） 的 SyncHdr 元素。 如果您查看 OMA DM 日志但 Csp 不通常会生成此，您可能会看到这样。 |
| 214         | 操作已取消。 SyncML 命令已成功完成，但没有更多的命令将在会话中进行处理。                                                                                                        |
| 215         | 不会执行。 由于用户以交互方式取消命令未执行命令。                                                                                                                                   |
| 216         | `Atomic`回滚确定。 命令已在`Atomic`元素和`Atomic`失败。 该命令已成功回滚。                                                                                                   |
| 400         | 错误的请求。 因为语法不正确，无法执行请求的命令。 Csp 不通常会生成此错误，但您可能会看到它，如果您 SyncML 的格式不正确。                                             |
| 401         | 凭据无效。 请求的命令失败，因为请求者必须提供适当的身份验证。 Csp 不通常会生成此错误。                                                                              |
| 403         | 禁止访问。 请求的命令失败，但收件人了解请求的命令。                                                                                                                                      |
| 404         | 找不到。 找不到请求的目标。 如果查询不存在的节点，则将生成此代码。                                                                                                               |
| 405         | 不允许使用的命令。 此响应将生成的代码，如果您尝试写入只读节点。                                                                                                                                 |
| 406         | 不受支持的可选功能。 如果您尝试访问的 CSP 不支持的属性，则将生成此响应代码。                                                                                                |
| 415         | 不受支持的类型或格式。 XML 分析或格式设置的错误可能会导致此响应代码。                                                                                                                                  |
| 418         | 已存在。 如果尝试添加已存在的节点，则会发生此响应代码。                                                                                                                                       |
| 425         | 权限被拒绝。 请求的命令失败，因为发件人不具有适当的访问控制权限 (ACL) 的接收方。 "拒绝访问"错误通常转换为此响应代码。                 |
| 500         | 命令失败。 一般故障。 收件人时遇到了意外的情况，无法完成该请求。 SyncML DPU 无法映射的原始的错误代码，则会发生此响应代码。       |
| 507         | `Atomic`失败。 在操作之一`Atomic`块失败。                                                                                                                                                               |
| 516         | `Atomic`将鼠标移回失败。 `Atomic`操作失败，并且该命令不成功回滚了。                                                                                                                         |

 

## <a name="related-topics"></a>相关的主题

[配置服务提供程序的引用](configuration-service-provider-reference.md)

 






