---
title: "3.配置文件定义"
description: "3"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 1d072198-f631-463a-886c-b69a48c1acd1
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: f36c15fe80b8b5ee91f4e9a29dc3ba46f47ebc5c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="3-profile-definitions"></a>3.配置文件定义


Windows 性能记录器 (WPR) 录制配置文件存储在 XML 文件具有.wprp 扩展名。 *配置文件定义*将组合在一起的收集器和提供程序定义在.wprp 文件中。

在这篇文章︰

-   [配置文件](#profiles)

-   [收集器元素](#collectors)

-   [配置文件定义示例](#profdefex)

## <a name="profiles"></a>配置文件


通过使用定义一个 WPR 配置文件`(<Profile> … </Profile>`参考收集器和提供程序定义定义同一个.wprp 文件中或通过在另一个.wprp 文件中使用继承的 XML 标记的 XML 标记。 每个配置文件定义 XML 标记必须具有以下特性︰

-   **Id**︰ 配置文件定义的唯一标识符。 使用下面的配置文件标识符结构︰

    &lt;*名称*&gt;。&lt; *DetailLevel*&gt;。&lt; *LoggingMode*&gt;。

-   **名称**︰ 指示配置文件名称的字符串。

-   **DetailLevel**︰ 指定配置文件定义了用于定时跟踪 （*光*） 或分析跟踪 （*详细*） 的特性。

-   **LoggingMode**︰ 指定该配置文件记录事件，到连续的文件或循环内存缓冲区的特性。 所有配置文件必须具有相同的.wprp 文件中的文件和内存版本。

-   **说明**︰ 配置文件的用户将看到的文本说明。

WPR 支持记录文件和内存*打开/关闭配置文件*除了每个.wprp 文件的日志记录模式的性能。 您必须登录/注销文件，配置文件，但文件和内存版本必须定义。 因为单个配置文件定义中可以支持只有一种日志记录模式，所以可以有两个或四个配置文件定义在.wprp 文件中，对于每个日志记录模式和明细数据级别组合之一。 一个.wprp 文件中的所有配置文件定义必须具有相同的**名称**属性。

&lt;*名称*&gt;。&lt; *DetailLevel*&gt;。&lt; *LoggingMode*&gt;

下面的代码示例显示**Example1.wprp**。 此文件包含两个配置文件定义。 省略号 （...） 表示配置文件的主体。

``` syntax
<Profile
  Id="Example1.Verbose.File"
  Name="Example1"
  DetailLevel="Verbose"
  LoggingMode="File"
  Description="Example1 profile">
…
</Profile>
<Profile
  Id="Example1.Verbose.Memory"
  Name="Example1"
  DetailLevel="Verbose"
  LoggingMode="Memory"
  Description="Example1 profile">
…
</Profile>
```

下面的代码示例显示**Example2.wprp**。 此文件包含四个配置文件定义。 省略号 （...） 表示配置文件的主体。

``` syntax
<Profile
  Id="Example2.Verbose.File"
  Name="Example2"
  DetailLevel="Verbose"
  LoggingMode="File"
  Description="Example2 profile">
…
</Profile>
<Profile
  Id="Example2.Light.File"
  Name="Example2"
  DetailLevel="Light"
  LoggingMode="File"
  Description="Example2 profile">
…
</Profile>
<Profile
  Id="Example2.Verbose.Memory"
  Name="Example2"
  DetailLevel="Verbose"
  LoggingMode="Memory"
  Description="Example2 profile">
…
</Profile>
<Profile
  Id="Example2.Light.Memory"
  Name="Example2"
  DetailLevel="Light"
  LoggingMode="Memory"
  Description="Example2 profile">
…
</Profile>
```

## <a name="a-href-idcollectorsacollectors-element"></a><a href="" id="collectors"></a>收集器元素


该**收集器**元素包含以前定义的系统和事件收集器的引用。 [SystemCollectorId](systemcollectorid.md)和[EventCollectorId](eventcollectorid.md)元素标识这些收集器。

**SystemCollectorId**和**EventCollectorId**的每个元素包含指定用于收集器的**Id**属性的强制**值**特性。 **SystemCollectorId**和**EventCollectorId**的每个元素还包含[SystemProviderId](systemproviderid.md)或[EventCollectorId](eventcollectorid.md)元素的列表。 这些元素有相似的语法。 但是，这些元素引用以前定义的系统和事件提供程序。

您还可以定义收集器和提供程序的配置文件定义中。

## <a name="a-href-idprofdefexaprofile-definition-example"></a><a href="" id="profdefex"></a>配置文件定义示例


下面的代码示例演示了一个完整的配置文件定义。

``` syntax
<Profile
  Id="Example.Light.File"
  Name="Example"
  DetailLevel="Light"
  LoggingMode="File"
  Description="Example profile">
  <ProblemCategories> 
    <ProblemCategory
      Value="First Level Triage"/>
  </ProblemCategories> 
  <Collectors> 
    <SystemCollectorId
      Value="WPRSystemCollector">
      <!--Enables the system provider for this system collector. --> 
      <SystemProviderId
        Value="system-provider"/>
    </SystemCollectorId> 
    <EventCollectorId
      Value="WPREventCollector">
      <EventProviders> 
      <!--Enables two event providers for this event collector. --> 
        <EventProviderId
          Value="Win32K-provider"/>
        <EventProviderId
          Value="Search-Core-provider"/>
      </EventProviders> 
    </EventCollectorId> 
  </Collectors>
</Profile>
```

## <a name="related-topics"></a>相关的主题


[编写配置文件记录](authoring-recording-profiles.md)

[2.系统和事件提供程序定义](2-system-and-event-provider-definitions.md)

[记录模式](logging-mode.md)

[详细信息级别](detail-level.md)

[ProblemCategories](problemcategories.md)

[SystemCollectorId](systemcollectorid.md)

[HeapEventProviderId](heapeventproviderid.md)

 

 







