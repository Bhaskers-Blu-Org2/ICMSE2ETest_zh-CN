---
title: "创建文件感兴趣的区域"
description: "创建文件感兴趣的区域"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: e8818fd2-3536-4b02-840d-f7d2eb4fbd91
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 929a65a01f45c2b4de4d1f1d4140f92c80c7a5f5
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="creating-a-regions-of-interest-file"></a>创建文件感兴趣的区域


感兴趣的区域文件是有效的 XML 文件，其中包含以下节点︰

-   **InstrumentationManifest**

-   **检测**

-   **地区**

-   **RegionsRoot**，一个用于所有已定义区域

-   一个或多个**区域**节点

**请注意**  
在该区域的定义中，*版本*属性在 XML 声明中，如`version='1.0'`，是可选的。

 

下面的示例为定义一个简单的区域的完整感兴趣的区域文件。 在示例之后描述了属性和**区域**内的节点的说明。

``` syntax
<?xml version='1.0' encoding='utf-8' standalone='yes'?>
<?Copyright (c) Microsoft Corporation. All rights reserved.?>
<InstrumentationManifest>
   <Instrumentation>
      <Regions>
         <RegionRoot Guid="{EFA7A927-BAE3-48F6-92E1-000000000000}"
                     Name="Sample Region File Root"
                     FriendlyName="Root">
            <Region Guid="{d8d639a0-cf4c-45fb-976a-000111000100}"
                    Name="FastStartup-Suspend-UserSession-Shutdown"
                    FriendlyName="User Session Shutdown">
               <Start>
                  <Event Provider="{dbe9b383-7cf3-4331-91cc-a3cb16a3b538}" Id="301" Version="0" />
               </Start>
               <Stop>
                  <Event Provider="{331c3b3a-2005-44c2-ac5e-77220c37d6b4}" Id="22" Version="0" />
               </Stop>
            </Region>
         </RegionRoot>
      </Regions>
   </Instrumentation>
</InstrumentationManifest>
```

本主题包含以下内容︰

-   [定义一个区域](#defining-a-region)
-   [区域类型](#region-types)
-   [使用有效负载字段来标识事件](#using-payload-fields-to-identify-events)
-   [区域匹配的事件](#matching-events-for-regions)
-   [筛选区域根据某一条件](#filtering-a-region-based-on-a-condition)
-   [父-子关系](#parent-child-relationships)
-   [自嵌套区域](#self-nesting-regions)
-   [实例名称](#instance-names)
-   [元数据](#metadata)

### <a name="defining-a-region"></a>定义一个区域

区域定义包含**区域**节点中的以下属性︰

-   *Guid*（必需），该区域的 GUID。

-   *名称*（必需），该区域的唯一名称。 建议*名称*格式为`Root-GrandparentName-ParentName-RegionName`。

-   *友好名称*（可选），该地区的备用名称。

### <a name="region-types"></a>区域类型

您可以创建以下类型的基础如何启动和停止的区域︰

-   [基于事件的区域](#regions-based-on-events)
-   [基于持续时间的区域](#regions-based-on-duration)
-   [根据其他地区的区域](#regions-based-on-other-regions)
-   [是其他地区的容器的区域](#regions-within-regions)

### <a name="regions-based-on-events"></a>基于事件的区域

最常见类型是区域的其启动和停止点定义的事件之一。

若要指定事件的开始或结束点，您需要提供以下属性︰

-   *提供程序*指定的事件提供程序 ID 的 GUID。

-   *标识*、 符号的短整型，指定的事件 ID。

-   *版本*，无符号字符，用于指定事件的版本。

此外，您可以通过添加一个或多个**PayloadIdentifier**节点进一步细化您的定义。 这些标记包含两个字符串属性、*操作符*和*FieldValue*，用于指定字段必须包含事件。 **PayloadIdentifier**标记中**使用有效负载字段来标识事件**进一步说明如下。

### <a name="examples"></a>示例

下面是这种区域的基本示例︰

``` syntax
<Region Guid="{d8d639a0-cf4c-45fb-976a-000111000100}"
        Name="FastStartup-Suspend-UserSession-Shutdown"
        FriendlyName="User Session Shutdown">
   <Start>
      <Event Provider="{dbe9b383-7cf3-4331-91cc-a3cb16a3b538}" Id="301" Version="0" />
   </Start>
   <Stop>
      <Event Provider="{331c3b3a-2005-44c2-ac5e-77220c37d6b4}" Id="22" Version="0" />
   </Stop>
</Region>
```

在以下示例中，该区域结束仅当指定的事件包含名为的字段`StartOrStop`值为`Stop`:

``` syntax
<Region Guid="{d8d639a0-cf4c-45fb-976a-000111000100}"
        Name="FastStartup-Suspend-UserSession-Shutdown"
        FriendlyName="User Session Shutdown">
   <Start>
      <Event Provider="{dbe9b383-7cf3-4331-91cc-a3cb16a3b538}" Id="301" Version="0" />
   </Start>
   <Stop>
      <Event Provider="{331c3b3a-2005-44c2-ac5e-77220c37d6b4}" Id="22" Version="0" />
      <PayloadIdentifier FieldName="StartOrStop" FieldValue="Stop" />
   </Stop>
</Region>
```

### <a name="regions-based-on-duration"></a>基于持续时间的区域

许多 ETW 事件被定义为具有持续负载字段的单个停止事件。 我们可以通过减去从停止事件时间的持续时间计算的起始点。

**持续时间**标记可用于**启动**或**停止**标记中指定从中获取持续时间信息的有效负载字段。 如果您定义的起始点的持续时间，将从停止点扣除持续时间。 同样，如果您定义的停止点的持续时间，持续时间将被添加到起始点。

**持续时间**节点可以具有以下特性︰

-   *提供程序*，指定包含负载字段的事件提供程序 ID 的 GUID。

-   *标识*、 符号的短整型，指定包含负载字段的事件 ID。

-   *版本*，无符号字符，指定包含负载字段事件的版本。

-   *持续时间*，指定负载字段的名称的字符串。

-   *倍频*。 WPA 要求要以毫微秒为单位的持续时间。 使用此特性将工期转换为毫微秒为单位，如有必要。 例如，使用 1000000 （一百万） 转换毫秒到纳秒。

如果您定义的起始点的持续时间，将从停止点扣除持续时间。 同样，如果您定义的停止点的持续时间，持续时间将被添加到起始点。

### <a name="example"></a>示例

下面的示例定义在另一个区域启动时停止的区域。 若要计算的起始点，我们持续时间减去从我们停止点。 持续时间是在 HiberHiberFileTime 负载字段中找到的。 我们再乘以 1000000 减去停止点并将其转换为纳秒的持续时间。

``` syntax
<Region Guid="{7D6BA3F6-BC04-4776-8A7F-93CF7F4E2B6D}"
   Name="FastStartup-Suspend-WriteHiberFile"
   FriendlyName="Subscribers for Create Session">
   <Region Guid="{93783B2C-A67F-49cb-89BC-BF305D7E2CEA}"
         Name="FastStartup-Suspend-Winlogon-CreateSession-Subscribers-Child"
         FriendlyName="Hiberfile Write">
      <Start>
         <Duration Provider="{331c3b3a-2005-44c2-ac53-77220c37d6b4}" 
                   Id="117"
                   Version="0"
                   Duration="HiberHiberFileTime"
                   Multiplier="1000000" />
      </Start>
      <Stop>
         <Region RegionGuid="{EC1BB2D9-4AA8-4d82-84AA-6042FF4CFBE3}" />
      </Stop>
   </Region>
</Region>
```

### <a name="regions-based-on-other-regions"></a>根据其他地区的区域

您可以定义其启动和停止点定义的其他地区通过**区域**节点中**启动**或**停止**节点的区域。 此区域节点都有一个强制属性， *RegionGuid*，用于指定目标区域的 GUID。

默认情况下，起始点地区停止时将启动其起始点基于另一区域的区域。 同样，其停止点基于另一区域的区域将停止停止点地区启动时。 通过向区域节点添加可选属性，*终结点*，可以重写此默认行为。 *终结点*可以具有的值`Start`或`Stop`，并指定要用于启动或停止事件的区域的终结点。

### <a name="example"></a>示例

下面的区域定义包含启动和停止点所定义的其他区域︰

``` syntax
<Region Guid="{93783B2C-A67F-49cb-89BC-BF305D7E2CEA}"
        Name="FastStartup-Suspend-HiberInitTime"
        FriendlyName="Hiberfile Initialization">
   <Start>
      <Region RegionGuid="{5E81D74C-0CCC-43f9-8119-953F827BCD12}" />
   </Start>
   <Stop>
      <Region RegionGuid="{7D6BA3F6-BC04-4776-8A7F-93CF7F4E2B6D}" />
   </Stop>
</Region>
```

### <a name="a-href-idregions-within-regionsaregions-that-are-containers-of-other-regions"></a><a href="" id="regions-within-regions"></a>是其他地区的容器的区域

包含其他区域的区域被称为*容器*。 包含区域的第一个实例启动并停止时的最后一个实例停止时，将启动容器。 这些区域不具有任何其他属性。

**RegionRoot**是您定义的区域的所有容器。 因此， **RegionRoot**启动时启动区域的第一个实例，并停止在一个区域的最后一个实例停止时。

若要定义一个容器区域，只需定义起始点或停止点的区域。

### <a name="example"></a>示例

在下面的示例中，*订阅服务器上创建的会话*是*子的订阅服务器的创建会话*的容器。 注意到*订阅服务器上创建的会话*没有起始点或停止点。 它将一个子区域的第一个实例启动时启动和停止子区域的最后一个实例停止时。

``` syntax
<Region Guid="{A75D8F5D-E8F8-40b8-B453-5CC70DEAC06F}"
   Name="FastStartup-Suspend-Winlogon-CreateSession-Subscribers"
   FriendlyName="Subscribers for Create Session">
   <Region Guid="{93783B2C-A67F-49cb-89BC-BF305D7E2CEA}"
           Name="FastStartup-Suspend-Winlogon-CreateSession-Subscribers-Child"
           FriendlyName="Child of Subscribers for Create Session">
      <Start>
         <Region RegionGuid="{5E81D74C-0CCC-43f9-8119-953F827BCD12}" />
      </Start>
      <Stop>
         <Region RegionGuid="{7D6BA3F6-BC04-4776-8A7F-93CF7F4E2B6D}" 
                 Endpoint="Stop" />
      </Stop>
   </Region>
</Region>
```

### <a name="using-payload-fields-to-identify-events"></a>使用有效负载字段来标识事件

事件 ID 属性 （进程 ID、 线程 ID 和活动 ID） 通常不足以确定具体的方案。 例如，服务启动时，泛型事件引发，可能无法识别的服务已启动。 在这种情况下，必须依靠*负载字段*的其他信息。 在这种情况下，其他域中的一个应包括的服务名称。 此信息可用于进一步指定地区启动和停止点。

以负载字段用作附加事件标识符，请将一个或多个**PayloadIdentifier**节点添加到**启动**或**停止**节点。

**PayloadIdentifier**节点具有以下特性︰

-   *FieldName*（必需），有效载荷字段的名称。

-   *FieldValue*（必需），有效载荷值。

-   *FieldValueRelationship*（可选）。 **IsEqual**用于指定事件必须包含有效载荷值。 **DoesNotContain**用于指定事件必须包含有效载荷值。 如果未指定此属性，则默认值是**IsEqual**。

**请注意**  
负载字段区分大小写，并且 XML 定义必须完全匹配的负载值。 例如，如果负载字段的值为`00000`，还必须指定区域定义`00000`作为有效载荷值。

 

### <a name="example"></a>示例

下面的示例包含**PayloadIdentifier**节点的起始点和停止点︰

``` syntax
<Region Guid="{AB719FB1-D863-4305-AE8E-F21281899A85}"
        Name="FastStartup-ConsoleSessionDisconnect"
        FriendlyName="Console Session Disconnect">
   <Start>
      <Event Provider="{dbe9b383-7cf3-4331-91cc-a3cb16a3b538}" Id="801" Version="0" />
      <PayloadIdentifier FieldName="Event" FieldValue="8" />
      <PayloadIdentifier FieldName="Key" FieldValue="00000" />
   </Start>
   <Stop>
      <Event Provider="{dbe9b383-7cf3-4331-91cc-a3cb16a3b538}" Id="802" Version="0" />
      <PayloadIdentifier FieldName="Event"
                         FieldValue="20"
                         FieldValueRelationship="DoesNotContain" />
   </Stop>
</Region>
```

### <a name="matching-events-for-regions"></a>区域匹配的事件

WPA 匹配起始事件停止事件到窗体区域的一个称为*事件匹配*的过程。 在事件级别，WPA 尝试匹配一个起始值或基于提供程序 ID、 事件 ID、 事件的版本和任何其他指定的负载字段停止事件。

此外可以到地区级别，可以在其中指定条件必须满足由起始和停止点扩展匹配。 在地区层面上，您可以要求这两个点具有匹配 Id 的线程、 进程 Id 和活动 Id。 此外，您还可以定义在地区级别的负载条件。

您可以使用区域级别通过包括在该**区域**节点**匹配**节点匹配。 **匹配**节点包含子节点的**事件**，可以具有下列属性的任意组合︰

-   `TID="true"`– 需要匹配的线程 Id

-   `PID="true"`– 要求匹配进程 Id

-   `AID="true"`– 要求匹配活动 Id

**事件**节点可以具有的可选**负载**子节点包含*FieldName*属性。 此节点要求同时启动和停止节点包含匹配的负载值为指定的*字段名*。

另外，**负载**节点还可以包含一个可选特性， *TargetFieldName*。 如果指定了该属性，然后*FieldName*对应于一个负载字段仅在起始节点中，虽然*TargetFieldName*中的停止节点的负载字段对应。

### <a name="example"></a>示例

下面的示例窗体区域起始事件包含负载字段， *SubscriberName*，其值与匹配的有效负载中的字段，*客户端*，停止节点时。 启动和停止事件还必须具有匹配的线程 Id。

``` syntax
<Region Guid="{A75D8F5D-E8F8-40b8-B453-5CCC70DEAC06F}"
        Name="FastStartup-Suspend-Winlogon-CreateSession-Subscribers"
        FriendlyName="Subscribers for Create Session">
   <Start>
      <Event Provider="{dbe9b383-7cf3-4331-91cc-a3cb16a3b538}" Id="805" Version="0" />
      <PayloadIdentifier FieldName="Event" FieldValue="0" />
   </Start>
   <Stop>
      <Event Provider="{dbe9b383-7cf3-4331-91cc-a3cb16a3b538}" Id="806" Version="0" />
      <PayloadIdentifier FieldName="Event" FieldValue="0" />
   </Stop>
   <Match>
      <Event TID="true">
         <Payload FieldName="SubscriberName" TargetFieldName="Client" />
      </Event>
   </Match>
</Region>
```

### <a name="filtering-a-region-based-on-a-condition"></a>筛选区域根据某一条件

WPA 可以包括或排除根据条件或*触发器*，可以是一个事件或另一个区域的区域。 触发器指定在**筛选器**元素中，且该区域包含**筛选器**的*目标*。

如果触发器*区域*，然后**筛选**其必须包含区域 id。

如果触发器*事件*，则**筛选器**必须包含**事件**元素与*ProviderId* ETW 提供程序和一个或多个以下特性︰ *Id*、*版本*、*操作码*和*类型*。

*Id*和*版本*是前面所述[区域类型](#region-types)。 *操作码*是您选择的任何值。 *类型*指定筛选目标的区域、 包括或排除根据下表中所描述的情况的模式。

| 筛选器类型 | 说明                                                                                          |
|----------------|------------------------------------------------------------------------------------------------------|
| 从内到外            | 当找到时触发的事件或地区排除的目标区域。                              |
| OutPost        | 当目标出现后最近触发的事件或地区排除的目标区域。 |
| OutPrev        | 目标区域的第一个触发事件之前发生时排除的目标区域。    |
| 从外到内             | 仅当找到触发事件或地区包括目标地区。                         |
| InPost         | 仅当发生在最近触发的事件或区域中包含目标地区。    |
| InPrev         | 只有在该地区的第一个触发事件之前发生时，包括的目标区域。       |


### <a name="parent-child-relationships"></a>父-子关系

您可以定义在创建父-子关系另一个地区。 针对的父区域，它必须有一个开始时间早于或等于的子区域的开始时间。 它还必须晚于或等于结束时间的子区域的停止时间。 如果不满足这些条件，不能形成一个父-子关系。

若要指定的父区域的附加条件，使用的**匹配**节点的**父**节点。 **父**节点与地区级匹配中使用的**事件**节点具有相同的属性和子节点。 您可以指定父和子区域内的必须具有相同的线程 ID、 进程 ID、 活动 ID 和任意数量的字段相匹配的有效负载。

在使用负载字段，如果指定只有*FieldName*属性时，父级和子级区域必须具有匹配该字段的有效载荷值。 如果还指定了*TargetFieldName*属性， *TargetFieldName*属性适用于父和子，即子区域必须具有匹配负载值父级中的*TargetFieldName*字段的*FieldName*字段有效载荷值。

如果孩子有几个潜在的父，将选择父项与最早开始时间。

### <a name="example"></a>示例

下面的示例定义为父的条件。 父级必须具有匹配的线程 ID，并为一个有效载荷值`SubscriberName`中子字段必须匹配的值`Client`在父字段。

``` syntax
<Region Guid="{A75D8F5D-E8F8-40b8-B453-5CC70DEAC06F}"
        Name="FastStartup-Suspend-Winlogon-CreateSession-Subscribers"
        FriendlyName="Subscribers for Create Session">
   <Start>
      <Event Provider="{dbe9b383-7cf3-4331-91cc-a3cb16a3b538}" Id="805" Version="0" />
      <PayloadIdentifier FieldName="Event" FieldValue="0" />
   </Start>
   <Stop>
      <Event Provider="{dbe9b383-7cf3-4331-91cc-a3cb16a3b538}" Id="806" Version="0" />
      <PayloadIdentifier FieldName="Event" FieldValue="0" />
   </Stop>
   <Match>
      <Event TID="true">
         <Payload FieldName="SubscriberName" TargetFieldName="Client" />
      </Event>
      <Parent TID="true">
         <Payload FieldName="SubscriberName" TargetFieldName="Client" />
      </Parent>
   </Match>
</Region>
```

### <a name="self-nesting-regions"></a>自嵌套区域

*自嵌套*是可选功能，优化了父-子关系。

*自嵌套区域*是其持续时间完全包含在兄弟地区的持续时间。 该地区有效地成为其更持久同级子级。

例如，假定自嵌套启用了以下区域︰

-   父区域 A

-   子区域 B1，其中 0 次启动和停止 6 次

-   子区域 B2，其中 2 次启动和停止 5 次

-   子区域 B3，其中 3 次启动和停止 4 次

在此示例中，B2 成为 B1、 子区域和 B3 成为 B2 的子区域。 当创建此类型的父-子关系，请选择父与子起始时间最接近的开始时间。

若要激活自嵌套，添加**SelfNest**节点内的**匹配**节点。

**SelfNest**节点没有任何必需的参数。 但是，您可以使用相同的匹配参数用于创建普通的父-子关系。 有关详细信息，请参阅本主题前面的**父-子关系**。

### <a name="examples"></a>示例

下面的示例定义**匹配**标记的只是调用自嵌套︰

``` syntax
<Match>
   <SelfNest />
</Match>
```

下面的示例定义匹配的线程 Id 和负载字段需要更复杂的自嵌套方案︰

``` syntax
<Match>
   <SelfNest TID="true">
      <Payload FieldName="SubscriberName" />
   </SelfNest>
</Match>
```

### <a name="instance-names"></a>实例名称

您可以使用**命名**节点到匹配区域的每个实例分配一个唯一的名称。 当有大量的实例相同的区域或需要进行分类，根据其他条件的地区，命名功能非常有用。 可以基于实例名称，或者负载字段或与其他地区的关系。

可以通过使用**命名**节点内的**PayloadBased**节点基于负载值命名实例。 该**PayloadBased**节点具有一个必需的属性*（name） 字段*，用于指定负载字段值要用作实例名称。 这些有效载荷字段可以在开始或结束点的区域。

下面是与基于负载的**命名**节点区域的示例︰

``` syntax
<Region Guid="{9261872F-D3A7-4d80-BDE3-8479CC920639}"
        Name="FastStartup-Suspend-Winlogon-EndShell-CallSubscriber"
        FriendlyName="Call Subscriber for End Shell">
   <Start>
      <Event Provider="{dbe9b383-7cf3-4331-91cc-a3cb16a3b538}" Id="811" Version="0" />
      <PayloadIdentifier FieldName="Event" FieldValue="13" />
   </Start>
   <Stop>
      <Event Provider="{dbe9b383-7cf3-4331-91cc-a3cb16a3b538}" Id="812" Version="0" />
      <PayloadIdentifier FieldName="Event" FieldValue="13" />
   </Stop>
   <Match>
      <Event PID="true" />
      <Parent PID="true" />
   </Match>
   <Naming>
      <PayloadBased NameField="SubscriberName" />
   </Naming>
</Region>
```

在前面的示例中的**命名**节点表示的开始或停止事件包含一个名为的有效负载字段`SubscriberName`。 用于创建该区域的每个实例，实例名称是相关联的负载值。

**请注意**  
当命名区域实例，WPA 首先检查匹配负载字段的起始事件。 如果未找到，WPA 再将搜索负载字段的停止事件。 如果不是事件中找到匹配，则将错误打印到控制台。

 

有时，有效负载中的信息不是我们想要的唯一信息。 例如，如果在负载中包含的信息是设备 ID，我们可能希望将此信息返回到设备描述和名称。 受支持的*类型*属性包括︰

-   `Device`将相关联的名称和说明

-   `GUID`将与该区域关联的 GUID

-   `CLSID`将相关联的类 ID 的类名

-   `PID`将与区域关联的进程名称

``` syntax
<Naming>
   <PayloadBased NameField="SubscriberName" Type="Device" />
</Naming>
```

如果有可能要找中启动和停止点的负载值，可以使用可选的*InstanceEndpoint*属性中指定该点使用。 可能值为*InstanceEndpoint* `Start` ， `Stop`。

``` syntax
<Naming>
   <PayloadBased NameField="SubscriberName" InstanceEndpoint="Start" />
</Naming>
```

此外可以使用命名区域基础与其他地区的关系。 与其他区域关联，请向**命名**节点添加**RegionBased**节点。 **RegionBased**节点具有四个必需的属性︰

-   *RegionGuid*，关联的区域的 GUID。

-   *关系*，一个条件的值，描述所定义的区域，并与您相关联的区域之间的关系。 目前，唯一受支持的关系，是`IsPresent`，这意味着如果某个地方跟踪中找到关联的区域为条件。

-   *IfRelationTrue*，如果所描述的*关系*的关系，就用作实例名称的字符串值。

-   *IfRelationFalse*，如果所描述的*关系*的关系为用作实例名称的字符串值。

下面的示例定义了基于区域的命名区域。 如果一个匹配的 GUID 的区域在跟踪，则每个实例的某处找到`Launch`被命名为`Warm`。 否则，每个实例被命名为`Cold`。

``` syntax
<Region Guid="{C99EFA90-F645-4A24-9576-740351171BD0}"
        Name="WinStoreAppActivationDuration"
        FriendlyName="Launch">
   <Start>
      <Event Provider="{315a8872-923e-4ea2-9889-33cd4754bf64}" Id="5901" Version="0" />
      <PayloadIdentifier FieldName="SqmableContractID" FieldValue="Windows.Launch" />
   </Start>
   <Stop>
      <Event Provider="{315a8872-923e-43a2-9889-33cd4754bf64}" Id="5902" Version="0" />
      <PayloadIdentifier FieldName="SqmableContractID" FieldValue="Windows.Launch" />
   </Stop>
   <Match>
      <Event PID="true" />
   </Match>
   <Naming>
      <RegionBased RegionGuid="{1539A93E-129C-4602-A011-431E7F73A353}" Relation="IsPresent" IfRelationTrue="Warm" IfRelationFalse="Cold" />
   </Naming>
</Region>
```

**请注意**  
您可以通过将鼠标悬停在感兴趣的区域图中的区域实例看到 WPA 中的实例名称。

 

### <a name="metadata"></a>元数据

对区域定义*的元数据*，**元数据**节点中包含的窗体中，可以添加其他信息。 例如，您可能包括在元数据中，以便其他用户可以更方便地了解该地区的目的解释的区域条件的信息。 元数据是简单地附加数据 — — 它不影响区域的处理。

WPA 的感兴趣区域的图表的图表视图中每个区域实例添加此元数据。 若要查看 WPA 匹配的事件的元数据，只需到所需的元数据展开图表视图中滚动的区域。 WPA 的元数据分配一个唯一的编号，该节点的名称显示为列的信息。

### <a name="example"></a>示例

下面的示例包含一个**元数据**节点区域定义中︰

``` syntax
<Region Guid="{F466EE67-192C-4772-B13D-052CCD2D70B3}"
        Name="FastStartup-Suspend-Winlogon-Logoff-Subscribers"
        FriendlyName="Subscribers for Logoff">
   <Start>
      <Event Provider="{dbe9b383-7cf3-4331-91cc-a3cb16a3b538}" Id="805" Version="0" />
      <PayloadIdentifier FieldName="Event" FieldValue="3" />
   </Start>
   <Stop>
      <Event Provider="{db39b383-7cf3-4331-91cc-a3cb16a3b538}" Id="806" Version="0" />
      <PayloadIdentifier FieldName="Event" FieldValue="3" />
   </Stop>
   <Match>
      <Event>
         <Payload FieldName="Event" />
      </Event>
   </Match>
   <Naming>
      <PayloadBased NameField="SubscriberName" />
   </Naming>
   <Metadata>
      <FAS.TestNode>yes</FAS.TestNode>
   </Metadata>
</Region>
```

## <a name="related-topics"></a>相关的主题


[感兴趣的区域](regions-of-interest.md)

[WPA 功能](wpa-features.md)

 

 







