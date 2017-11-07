---
title: "OMA DM 置备文件的结构"
description: "OMA DM 置备文件的结构"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 7bd3ef57-c76c-459b-b63f-c5a333ddc2bc
ms.openlocfilehash: e4d8c4baf6d1fd9217af02d064a3e1fda482bb59
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="structure-of-oma-dm-provisioning-files"></a>OMA DM 置备文件的结构

OMA DM 命令在服务器和邮件中的客户端设备之间传输。 消息可以包含一个或多个命令。 支持的命令列表，请参阅[支持的 OMA DM 协议](oma-dm-protocol-support.md)中的表。

DM 消息的 XML 文档。 在 OMA DM 表示协议中定义的结构和文档的内容 (OMA-SyncML 的 DevInfo 的 DTD 的 V1\_1\_2-20030505-D.dtd) 可从[OMA 网站](http://go.microsoft.com/fwlink/p/?LinkId=526900)。

每个消息组成 SyncHdr 元素中指定的标头和邮件正文中，SyncBody 元素指定的。

下表显示了支持的 OMA DM 版本。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>版本</th>
<th>Format</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>OMA DM 1.1.2 版</p></td>
<td><p><code>&lt;SyncML xmlns='SYNCML:SYNCML1.1'&gt;</code></p>
<p><code>&lt;/SyncML&gt;</code></p></td>
</tr>
<tr class="even">
<td><p>OMA DM 1.2 版</p></td>
<td><p><code>&lt;SyncML xmlns='SYNCML:SYNCML1.2'&gt;</code></p>
<p><code>&lt;/SyncML&gt;</code></p></td>
</tr>
</tbody>
</table>

 

## <a name="file-format"></a>文件格式

下面的示例显示 XML 文档由使用仅用于演示目的的 OMA DM 1.2.1 版的服务器发送的常规结构。 客户端和服务器之间交换的初始 XML 包可能包含附加的 XML 标记。 有关详细的说明和这些包的示例，请参见[OMA 设备管理协议 1.2.1](http://go.microsoft.com/fwlink/p/?LinkId=526902)规范。

``` syntax
<SyncML xmlns='SYNCML:SYNCML1.2'>
   <SyncHdr>
      <VerDTD>1.2</VerDTD>
      <VerProto>DM/1.2</VerProto>
      <SessionID>1</SessionID>
      <MsgID>1</MsgID>
      <Target>
         <LocURI>{unique device ID}</LocURI>
      </Target>
      <Source>
         <LocURI>https://www.contoso.com/mgmt-server</LocURI>
      </Source>
   </SyncHdr>
   <SyncBody>
      <!-- query a device OS system version -->
      <Get>
         <CmdID>2</CmdID>
         <Item>
            <Target>
               <LocURI>./DevDetail/SwV</LocURI>
            </Target>
         </Item>
      </Get>
      <!-- Update device policy -->
      
      <Final />
   </SyncBody>
</SyncML>
```

## <a name="synchdr-element"></a>SyncHdr 元素

SyncHdr 包括以下信息︰

-   文档类型定义 (DTD) 和协议版本号码

-   会话和消息的标识符。 DM 同一会话中的每个消息必须具有不同的邮件 Id。

-   消息源和目标统一资源标识符 (Uri)

-   身份验证凭据

此信息用于向客户端设备通过正确地管理 DM 会话。


**代码示例**

下面的示例演示一个 DM 消息的标头组件。 在这种情况下，仅用作示例，将使用 OMA DM 版本 1.2。

> **请注意**  &lt;LocURI&gt;节点值&lt;源&gt;SyncHdr 的设备生成 DM 包中的元素应该是相同的值。 / DevInfo/DevID。 有关 DevID 的详细信息，请参阅[DevInfo 配置服务提供程序](devinfo-csp.md)。

 

``` syntax
<SyncHdr>
   <VerDTD>1.2</VerDTD>
   <VerProto>DM/1.2</VerProto>
   <SessionID>1</SessionID>
   <MsgID>1</MsgID>
   <Target>
      <LocURI>{unique device ID}</LocURI>
   </Target>
   <Source>
      <LocURI>https://www.contoso.com/mgmt-server</LocURI>
   </Source>
</SyncHdr>
```

## <a name="syncbody-element"></a>SyncBody 元素

SyncBody 包含一个或多个 DM 命令。 SyncBody 可以包含多个 DM 命令;每个命令必须具有不同的 CmdID 值。

**代码示例**

下面的示例演示 DM 消息的正文部分。 在此示例中，SyncBody 包含只能有一个命令，获得。 这由&lt;最终 /&gt; Get 命令终止标记之后立即发生的标记。

``` syntax
<SyncBody>
   <!-- query device OS software version -->
   <Get>
      <CmdID>2</CmdID>
      <Item>
         <Target>
            <LocURI>./DevDetail/SwV</LocURI>
         </Target>
      </Item>
   </Get>
   <Final />
</SyncBody>
```

如果使用 SyncML OMA DM 资源调配，在 SyncBody LocURI 可能会有"。"作为有效段名称仅在第一段。 但是，"。"不是为其它部门有效的段的名称。 例如，下面的 LocURI 是无效的第七段的段的名称是因为"。"。

```
<LocURI>./Vendor/MSFT/Registry/HKLM/Security/./Test</LocURI>
```

## <a name="update-device-settings-example"></a>更新设备设置示例

使用替换命令来更新设备的设置。

下面的示例阐释了如何使用替换命令来更新设备的设置。

``` syntax
<SyncHdr>
   <VerDTD>1.2</VerDTD>
   <VerProto>DM/1.2</VerProto>
   <SessionID>1</SessionID>
   <MsgID>1</MsgID>
   <Target>
      <LocURI>{unique device ID}</LocURI>
   </Target>
   <Source>
      <LocURI>https://www.contoso.com/mgmt-server</LocURI>
   </Source>
</SyncHdr>
<SyncBody>
   <!-- update device setting -->
   <Replace>
      <CmdID>2</CmdID>
      <Item>
         <Target>
            <LocURI>./Vendor/MSFT/PolicyManager/My/DeviceLock/MinDevicePasswordLength</LocURI>
         </Target>
         <Meta>
            <Type xmlns="syncml:metinf">text/plain</Type>
            <Format xmlns="syncml:metinf">int</Format>
         </Meta>
         <Data>6</Data>
      </Item>
   </Replace>
   <Final />
</SyncBody>
```

 






