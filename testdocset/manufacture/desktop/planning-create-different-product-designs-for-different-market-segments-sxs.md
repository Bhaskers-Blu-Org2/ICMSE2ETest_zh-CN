---
author: Justinha
Description: "规划︰ 为不同的观众的自定义引用图像"
ms.assetid: b98343dd-bb5e-4904-9b40-f44cea88fbf0
MSHAttr: PreferredLib:/library/windows/hardware
title: "规划︰ 为不同的观众的自定义引用图像"
ms.openlocfilehash: 746e53de2b5525e27ef41a7dab323e28f5db0657
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="planning-customizing-reference-images-for-different-audiences"></a>规划︰ 为不同的观众的自定义引用图像

而不是让一个尝试适合每个人的设备设计，Windows 映像管理工具可以帮助您定制设备设计，以满足不同客户的特定需要。

首先，我们建议选择硬件设计面向特定受众、 市场或价位。 生成用于这种设计的基图像并对其进行测试。 下一步，自定义该访问者的窗口，包括商标、 徽标、 语言和应用程序。

## <a name="span-iddevicetypesspanspan-iddevicetypesspanspan-iddevicetypesspandevice-types"></a><span id="Device_types"></span><span id="device_types"></span><span id="DEVICE_TYPES"></span>设备类型

请考虑创建另一个设备类型，例如低成本或性能的便携式计算机或低成本或性能台式计算机的单独设计。 这些样式都有不同的关键优异点，如电池寿命或图形性能集。

尽管 Windows 提供了许多常见设备的基本驱动程序，某些硬件需要专用的设备驱动程序，必须安装和偶尔进行更新。

许多驱动程序旨在引导 Windows 映像的情况下脱机安装。

使用 Windows 评估工具，以确保应用程序和您要安装的硬件可以在很多情况下很好地执行。

## <a name="span-idarchitecturespanspan-idarchitecturespanspan-idarchitecturespanarchitecture"></a><span id="Architecture"></span><span id="architecture"></span><span id="ARCHITECTURE"></span>体系结构

如果要生成 64 位和 32 位 (x86) 的设备芯片组和体系结构，您将需要单独的基于图像。 您还将需要不同版本的驱动程序、 程序包和更新。

## <a name="span-idretailcustomersandbusinesscustomersspanspan-idretailcustomersandbusinesscustomersspanspan-idretailcustomersandbusinesscustomersspanretail-customers-and-business-customers"></a><span id="Retail_customers_and_business_customers"></span><span id="retail_customers_and_business_customers"></span><span id="RETAIL_CUSTOMERS_AND_BUSINESS_CUSTOMERS"></span>零售客户和企业客户

如果您正在构建的设计，同时零售和商业客户，您可以开始与单个基如主 Windows 10 或 Windows 10 Pro 版，然后以后将其升级为更高版本，如 Windows 10 企业，根据需要。 一旦已经建立的更高版本，但是，不能降它到较低版本。 有关详细信息，请参阅[Windows 升级路径](http://go.microsoft.com/fwlink/?LinkId=526838)。

如果您正在构建向零售客户销售的设备，您需要满足一组最低要求。 信息，请参阅[OEM 合作伙伴中心](http://go.microsoft.com/fwlink/?LinkId=131358)的授权和政策指导。

如果您要构建适合企业的设备，将有更少的限制。 IT 专业人员可以自定义各种不同的方式在他们的设备。 但是，您应考虑 IT 策略，以及客户的需求，例如将数据迁移、 激活安全工具和批量许可协议和产品密钥管理的问题。

## <a name="span-idregionsspanspan-idregionsspanspan-idregionsspanregions"></a><span id="Regions"></span><span id="regions"></span><span id="REGIONS"></span>地区

请考虑创建不同基图像的不同区域。

窗口和其他应用程序，如 Microsoft Office 可能很大的资源文件的某些资源如本地化的手写和语音识别资源是几百兆字节。

若要保存驱动器空间，我们已经分裂的语言包。 这可以帮助您为您的客户预先加载更多语言或图像上节省空间。 例如，针对较大的地区，可以预加载基本语言组件，例如文本和用户接口文件中的许多领域内的地区，但只使用笔，包括设备的手写识别或仅包括语音和语音工具 Cortana 的设备上有集成麦克风。 以后根据需要用户可以下载这些组件。

## <a name="span-idsampleplanspanspan-idsampleplanspanspan-idsampleplanspansample-plan"></a><span id="Sample_plan"></span><span id="sample_plan"></span><span id="SAMPLE_PLAN"></span>示例性规划

该实验室将使用下面三个示例的硬件配置。

|                              |              |                     |                                   |
|------------------------------|--------------|---------------------|-----------------------------------|
| 硬件配置︰      | 1            | 1B                  | 2                                 |
| 窗体因子                  | 小触 | 2--1              | 笔记本                          |
| 体系结构                 | x86          | x86                 | x64                               |
| RAM                          | 1 GB         | 2 GB                | 4 GB                              |
| 磁盘容量和类型       | 16 GB eMMC   | 32 GB eMMC          | 500 GB 的硬盘驱动器                        |
| 使用磁盘压缩        | 是          | 否                  | 否                                |
| 显示大小                 | 8"           | 10"                 | 14 英寸                               |
| Windows 的 SKU                  | 主页          | 专业人员                 | 主页                               |
| 地区 / 语言           | EN-US        | EN-US，FR-FR，ES-ES | EN GB，特拉华州的特拉华州，FR-FR，ES-ES ZH-CN |
| Cortana                      | 是          | 是                 | 是                               |
| 收件箱的应用程序 （通用）       | 是          | 是                 | 是                               |
| 绘图笔                          | 否           | 是                 | 否                                |
| 办公室 （通用）           | 是          | 是                 | 是                               |
| Windows 桌面应用程序 | 否           | 是                 | 是                               |
| Office 2016 年                  | 否           | 是                 | 是                               |
| 精简的操作系统                   | 是          | 是                 | 否                                |
 
 注释︰
* 我们可以通过使用硬件配置 1 作为基本映像构建硬件配置 1B 的图像。
* 我们不能从硬件配置 1 或 1B，构建硬件配置 2，因为它们使用不同的体系结构。
