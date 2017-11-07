---
title: "继承"
description: "继承"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 5caaf667-4c1a-4459-8a45-36001ce6b414
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 4f5bca1fb1c93b710443f284829dc65198f4fa6a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="inheritance"></a>继承


Windows 性能记录器 (WPR) 录制配置文件存储在 XML 文件具有.wprp 扩展名。 WPR 支持继承的对象通过使用**基 =""** WPR 配置文件 XML 架构中的属性。 继承使您得以保持、 重用和公用配置文件定义记录专业的方案基础上进行构建。 例如，可以添加到现有的配置文件提供程序，从而更改缓冲区大小，而不改变实际的配置文件中的定义。

**重要**  
作者 WPRP 配置文件，应该继承 WPR 的内置的基本配置文件，配置文件数据或重复使用相同的会话名称，以避免多次启用相同的提供程序。

 

在这篇文章︰

-   [基本配置文件](#base)

-   [示例](#ex)

-   [继承的最佳做法](#bestprac)

## <a name="a-href-idbaseabase-profiles"></a><a href="" id="base"></a>基本配置文件


您可以使用 XML 标记来更改配置文件的内容。 您必须使用**操作**属性。 **操作**属性的可能值是**设置**并**添加**。 在以下示例中， **DerivedProfile**到**BaseProfile**定义的**CpuConfig**、 **CSwitch**和**SampledProfile**关键字添加**ReadyThread**系统关键字。

``` syntax
<SystemCollector
  Id="BaseSystemCollector" ... />

<SystemProvider
  Id="MainSystemProvider">
  <Keywords>
    <Keyword
      Value="CpuConfig"/>
    <Keyword
      Value="CSwitch"/>
    <Keyword
      Value="SampledProfile"/>
  </Keywords>
</SystemProvider>

<SystemProvider
  Id="AnotherSystemProvider">
  <Keywords> 
    <Keyword
      Value="ReadyThread"/>
  </Keywords>
</SystemProvider>

<Profile
  Id="BaseProfile"...>
  ... 
  <Collectors>
    <SystemCollectorId
      Value="BaseSystemCollector">
      <SystemProviderId
        Value="MainSystemProvider"/>
    </SystemCollectorId>
  </Collectors>
</Profile>

<Profile
  Id="DerivedProfile"
  Base="BaseProfile"...>
... 
  <Collectors Operation="Add"> <!--Use "Add" operation to add new provider to an existing one. -->
    <SystemCollectorId
      Value="BaseSystemCollector">
      <SystemProviderId
        Value="AnotherSystemProvider"/> <!--Specify provider to add. --> 
    </SystemCollectorId> 
  </Collectors>
</Profile>
```

**请注意**  
如果不指定**操作**属性，但使用继承，WPR 使用**设置**的默认值。

 

## <a name="a-href-idexaexample"></a><a href="" id="ex"></a>示例


下面的示例定义一个配置文件，登录模式的文件。 内存版本继承自该文件版本并覆盖的日志记录模式。

``` syntax
<Profile
   Id="SampleProfile.Verbose.File"
   LoggingMode = "File"
   DetailLevel = "Verbose"
   Name = "SampleProfile"
   Description = "A sample profile">
   …

</Profile>

<Profile
   Id="SampleProfile.Verbose.Memory"
   Base="SampleProfile.Verbose.File”
   LoggingMode = "Memory"
   DetailLevel = "Verbose"
   Name = "SampleProfile"
   Description = "A sample profile"/>
```

## <a name="a-href-idbestpracainheritance-best-practices"></a><a href="" id="bestprac"></a>继承的最佳做法


设计不佳的继承可以创建非预期的后果。 我们建议您仅从收集器或从配置文件的配置文件派生收集器。 永远不应在多个类型的对象组合进行派生。

下面三个示例描述了两个很好的方式使用继承;第三个示例说明使用继承。

### <a name="a-href-idex1inheraexample-1-good-use-of-inheritance"></a><a href="" id="ex1inher"></a>示例 1︰ 使用继承的好

您想要使用的事件收集器的规格进行一些修改。 要这样做︰

1.  定义从收集器答︰ 继承其规格的第二个收集 (收集器-B)

2.  修改收集器 b。

3.  将配置文件设置为参照收集器-b。

这是一个好的做法，因为只有收集器对象继承另一个收集对象，然后直接引用的配置文件属性。

### <a name="a-href-idex2inheraexample-2-good-use-of-inheritance"></a><a href="" id="ex2inher"></a>示例 2︰ 使用继承的好

1.  配置文件一个参照收集器-a。

2.  配置文件 B 继承属性从配置文件 a。

3.  修改特定属性中配置文件 b。

这是很好的做法，因为只有配置文件对象派生自另一个配置文件对象。

### <a name="a-href-idex3inheraexample-3-poor-use-of-inheritance"></a><a href="" id="ex3inher"></a>示例 3︰ 差使用继承

1.  配置文件一个参照收集器-a。

2.  收集器-B 继承收集器 a。

3.  配置文件 B 继承自配置文件 A，并还引用收集器 b。

在这种情况下，配置文件 B 引用收集器-B 两次︰ 一次通过继承的配置文件-A 和由收集器 B.直接引用一次 在这种情况下，不清楚应如何评估收集器-B 的定义;也就是说，哪个派生应优先。 本示例描绘了一种错误的做法，因为的顺序是不确定和可能导致矛盾的结果取决于操作的顺序。 应避免使用此类型的继承。

## <a name="related-topics"></a>相关的主题


[编写配置文件记录](authoring-recording-profiles.md)

[WPRControlProfiles 架构](wprcontrolprofiles-schema.md)

 

 







