---
title: "2.系统和事件提供程序定义"
description: "2"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 24358037-a8ad-41c8-b82c-b4c5111b17d3
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 577c2715b4d81c17fbd8eec2a8fd3c3f9ffdf902
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="2-system-and-event-provider-definitions"></a>2.系统和事件提供程序定义


Windows 性能记录器 (WPR) 录制配置文件存储在 XML 文件具有.wprp 扩展名。 系统提供商定义在.wprp 文件中指定系统关键字、 堆栈和内存池标记。

在这篇文章︰

-   [提供程序定义](#provdef)

-   [系统提供商](#sys)

-   [事件提供程序](#event)

-   [堆事件提供程序](#heap)

-   [捕获状态提供程序](#cap)

-   [示例](#ex)

## <a name="a-href-idprovdefaprovider-definition"></a><a href="" id="provdef"></a>提供程序定义


必须按以下顺序定义在.wprp 文件中的项︰

1.  所有收集器

2.  系统提供商

3.  事件提供程序

4.  如果存在堆提供程序

5.  所有配置文件

在某些情况下，提供程序可以定义中，而不是在这之前，配置文件定义。 例如︰

``` syntax
<EventCollector Id="Collector1" Name="Sample Event Collector">
   <BufferSize Value="128"/>
   <Buffers Value="64"/>
</EventCollector>

<Profile Id="Sample.Verbose.File" Name="Sample" Description="Sample profile" DetailLevel="Verbose" LoggingMode="File">
   <Collectors>
      <EventCollectorId Value="Collector1">
         <EventProviders>
            <EventProvider Id="EventProvider_Microsoft-Windows-Kernel-Power" Name="Microsoft-Windows-Kernel-Power" NonPagedMemory="true">
               <Keywords>
                  <Keyword Value="0x4"/>
               </Keywords>
            </EventProvider>
         </EventProviders>
      </EventCollectorId>
   </Collectors>
</Profile>
```

## <a name="a-href-idsysasystem-providers"></a><a href="" id="sys"></a>系统提供商


系统提供程序定义的唯一的必填属性是**Id**。 内部的 XML 标记指定的关键字、 堆栈和池标记，以启用。 有关所有受支持的关键字和堆栈的列表，请参阅[堆栈](stack-wpa.md)和[关键字 （在 SystemProvider)](keyword--in-systemprovider-.md)。

下面的代码示例演示系统提供程序定义。

``` syntax
<SystemProvider
  Id="system-provider">
  <Keywords>
    <Keyword
      Value="ProcessThread"/>
    <Keyword
      Value="Loader"/>
    <Keyword
      Value="CSwitch"/>
  </Keywords>
  <Stacks>
    <Stack
      Value="ThreadCreate"/>
    <Stack
      Value="ReadyThread"/>
    <Stack
      Value="CSwitch"/>
  </Stacks>
  <PoolTags>
    <PoolTag
      Value="a*"/>
    <PoolTag
      Value="b*"/>
    <PoolTag
      Value="c*"/>
    <PoolTag
      Value="d*"/>
  </PoolTags>
</SystemProvider>
```

## <a name="a-href-ideventaevent-providers"></a><a href="" id="event"></a>事件提供程序


事件提供程序定义指定要使用事件跟踪 Windows (ETW) 提供程序的关键字和级别启用。 ，事件提供程序定义需要强制**名称**属性和强制的**Id**属性。

**名称**属性指定以下名称之一︰

-   已注册深提供程序的名称，如"Microsoft Windows 的搜索-核"。

-   提供程序的 GUID，例如"49c2c27c-fe2d-40bf-8c4e-c3fb518037e7"。

-   早期的提供商，如"IE6"的名称。

-   特殊用例的名称，例如"PerfTrack"或"DotNetProvider"。

您可以使用以下可选特性调整提供程序参数︰

-   **堆栈**︰ 指示提供程序是否捕获堆栈。 默认设置为"false"。

-   **级别**︰ 指定 ETW 日志记录级别。 默认设置是 0xFF。

-   **NonPagedMemory**︰ 指示是否 WPR 非分页内存缓冲区对使用此提供程序。 默认设置为"false"。

    **警告**  
    某些 Windows 事件提供程序在跟踪捕获过程中需要非分页内存的使用。 下面举例说明的事件提供程序需要 NonPagedMemory 是`EventProvider_Microsoft-Windows-Win32k`。

     

-   **CaptureStateOnly**︰ 如果设置为"true"，表示 WPR 使此提供程序的指定的捕获状态。

-   **SID**︰ 指定是否记录的事件将扩展的数据包含用户的安全标识符 (SID)。

-   **TSID**︰ 如果设置为"真"，指定终端会话标识符的扩展数据记录的事件。

可选的内部 XML 标记指定要启用的关键字。 与系统提供商，不同的是事件提供程序没有定义文本常数。 因此，事件提供程序包含十六进制值。 但是，语法是相同的系统提供商。 如果未指定关键字，则默认值是 0xFFFFFFFFFFFFFFFF。

## <a name="a-href-idheapaheap-event-providers"></a><a href="" id="heap"></a>堆事件提供程序


堆提供程序定义指定为其 WPR 捕获堆事件的进程的进程标识符。 **Id**是唯一的必填属性。 **HeapProcessId**子元素不是必需的。 此元素指定要分析的进程的**Id**属性的过程。 下面的示例演示如何执行此操作。

``` syntax
<HeapEventProvider
  Id="Base_Heap_Provider">
</HeapEventProvider>
<HeapEventProvider
  Base="Base_Heap_Provider"
  Id="Derived_Heap_Provider">
  <HeapProcessIds Operation="Set">
    <HeapProcessId Value="2314"/>
  </HeapProcessIds>
</HeapEventProvider>
```

## <a name="a-href-idcapacapture-state-providers"></a><a href="" id="cap"></a>捕获状态提供程序


与常规的提供程序在整个跟踪会话启用，仅在保存或捕获会话开始时启用捕获状态提供程序。 下面的示例演示常规和捕获状态提供程序。

``` syntax
<EventProvider Id="sample-provider" Name="SampleProvider" NonPagedMemory="true" Level="5">
  <Keywords>
    <Keyword Value="0x98"/> <!-- Provider is enabled with these keywords throughout the tracing session. -->
  </Keywords>
  <CaptureStateOnStart>
    <Keyword Value="0xff4"/> <!-- Provider is enabled with these keywords when tracing is started. -->
  </CaptureStateOnStart>
  <CaptureStateOnSave>
    <Keyword Value="0x118"/> <!-- Provider is enabled with these keywords when tracing is saved. -->
  </CaptureStateOnSave>
</EventProvider>

<EventProvider Id="EventProvider_DWMWin32k_CaptureState" Name="e7ef96be-969f-414f-97d7-3ddb7b558ccc" NonPagedMemory="true" CaptureStateOnly="true" >
  <!-- CaptureStateOnly="true" means provider is not enabled throughout the tracing session. -->
  <CaptureStateOnSave>
    <Keyword Value="0x80000"/> <!-- Provider is enabled with these keywords when tracing is saved. -->
  </CaptureStateOnSave>
</EventProvider>
```

## <a name="a-href-idexaexample"></a><a href="" id="ex"></a>示例


下面的代码示例定义两个事件提供程序。

``` syntax
<EventProvider
  Id="Win32K-provider"
  Name="Microsoft-Windows-Win32K"
  NonPagedMemory="true"
  Stack="true">
  <Keywords>
    <Keyword
      Value="0x240000"/>
  </Keywords>
</EventProvider>

<EventProvider
  Id="Search-Core-provider"
  Name="Microsoft-Windows-Search-Core"/>
```

## <a name="related-topics"></a>相关的主题


[编写配置文件记录](authoring-recording-profiles.md)

[1.收集器定义](1-collector-definitions.md)

[3.配置文件定义](3-profile-definitions.md)

[SystemProvider](systemprovider.md)

[EventProvider](eventprovider.md)

[HeapEventProvider](heapeventprovider.md)

[关键字 （在 SystemProvider)](keyword--in-systemprovider-.md)

[堆栈](stack-wpa.md)

[PoolTag](pooltag.md)

 

 







