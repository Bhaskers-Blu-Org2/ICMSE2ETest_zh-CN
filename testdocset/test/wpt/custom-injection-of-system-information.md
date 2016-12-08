---
title: "自定义注入的系统信息"
description: "自定义注入的系统信息"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 18d70466-eb0c-4a3a-a711-59cda913b477
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 93154357f92ff783f1e6f57d1e785d90f959ecb0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="custom-injection-of-system-information"></a>自定义注入的系统信息


在多个跟踪文件合并到单个输出跟踪文件时，内核跟踪控制允许自定义的系统信息注入。 若要包含系统信息，一个标志的组合设置[CreateMergedTraceFile](createmergedtracefile.md)函数中。 以下标志定义要添加到合并的跟踪文件系统信息︰

<a href="" id="-define-event-trace-merge-extended-data-none-0x00000000"></a>\#定义事件\_跟踪\_合并\_扩展\_数据\_无 0x00000000  
没有系统信息应添加到合并的跟踪文件。

<a href="" id="-define-event-trace-merge-extended-data-imageid-0x00000001"></a>\#定义事件\_跟踪\_合并\_扩展\_数据\_图像 0x00000001 ID  
插入图像信息，如校验和及在符号搜索过程中使用的时间戳。

<a href="" id="-define-event-trace-merge-extended-data-buildinfo-0x00000002"></a>\#定义事件\_跟踪\_合并\_扩展\_数据\_BUILDINFO 0x00000002  
插入操作系统版本信息，例如产品名称和建立实验室。

<a href="" id="-define-event-trace-merge-extended-data-volume-mapping-0x00000004"></a>\#定义事件\_跟踪\_合并\_扩展\_数据\_卷\_0x00000004 映射  
插入卷 MS-DOS 和 Windows NT 路径之间的映射。 该事件的有效负载部分包含两个空终止的 Unicode 字符串。 第一个字符串包含 Windows NT 路径，第二个字符串包含 MS-DOS 路径。 负载的大小的大小，以字节为单位，两个 NULL 字符的字符串。

例如，Windows NT 路径"\\设备\\HarddiskVolume1\\"将转换为 MS-DOS 路径"c:\\"。

<a href="" id="-define-event-trace-merge-extended-data-winsat-0x00000008"></a>\#定义事件\_跟踪\_合并\_扩展\_数据\_WINSAT 0x00000008  
注入 WinSat 信息。

<a href="" id="-define-event-trace-merge-extended-data-event-metadata-0x00000010"></a>\#定义事件\_跟踪\_合并\_扩展\_数据\_事件\_0x00000010 的元数据  
插入用于捕获事件正在分析的计算机以外的计算机的事件跟踪数据头 (TDH) 元数据。 有关跟踪数据标头信息的详细信息，请参阅[事件跟踪](https://msdn.microsoft.com/library/bb968803.aspx)。

<a href="" id="-define-event-metadata-log-type-trace-event-info-0x20"></a>\#定义事件\_元数据\_日志\_类型\_跟踪\_事件\_信息 0x20  
插入跟踪信息用于标识记录的事件通过事件\_跟踪\_合并\_扩展\_数据\_事件\_元数据。

<a href="" id="-define-event-metadata-log-type-event-map-info-0x21"></a>\#定义事件\_元数据\_日志\_类型\_事件\_映射\_0x21 信息  
定义通过设置事件记录的事件的元数据信息中插入\_跟踪\_合并\_扩展\_数据\_事件\_元数据标记。 有关详细信息，请参阅[事件\_映射\_信息结构](https://msdn.microsoft.com/library/windows/desktop/aa964762.aspx)。

<a href="" id="-define-event-trace-merge-extended-data-perftrack-metadata-0x00000020"></a>\#定义事件\_跟踪\_合并\_扩展\_数据\_PERFTRACK\_0x00000020 的元数据  
插入**PerfTrack**事件的元数据进行解码的**PerfTrack**在不同计算机上的事件。 这些事件仅在 Windows 7 和 Windows Server 2008 上注入。

<a href="" id="-define-event-trace-merge-extended-data-default-0x000fffff"></a>\#定义事件\_跟踪\_合并\_扩展\_数据\_0x000FFFFF 默认  
插入图像，生成、 卷映射、 WinSat、 事件元数据和**PerfTrack**元数据的数据。

<a href="" id="-define-event-trace-merge-extended-data-all-0xfffffff"></a>\#定义事件\_跟踪\_合并\_扩展\_数据\_所有 0xFFFFFFF  
插入到输出跟踪文件的所有扩展的数据信息。

<a href="" id="-define-event-trace-merge-extended-data-network-interface-0x00000040"></a>\#定义事件\_跟踪\_合并\_扩展\_数据\_网络\_0x00000040 接口  
将网络接口的信息。

<a href="" id="-define-event-trace-merge-extended-data-ngen-pdb------------0x00000080"></a>\#定义事件\_跟踪\_合并\_扩展\_数据\_NGEN\_0x00000080 PDB  
创建 Pdb 以启用跟踪中出现的 NGEN 二进制文件的符号加载。

<a href="" id="-define-event-trace-merge-extended-data-compress-trace------0x10000000"></a>\#定义事件\_跟踪\_合并\_扩展\_数据\_压缩\_跟踪 0x10000000  
压缩合并的跟踪。 仅支持在 Windows 8 及更高版本。

<a href="" id="-define-event-trace-merge-extended-data-inject-only---------0x40000000"></a>\#定义事件\_跟踪\_合并\_扩展\_数据\_插入\_仅 0x40000000  
仅插入图像识别信息，不要从输入的跟踪复制事件。

## <a name="remarks"></a>备注


**要求︰**

**版本︰**可用于在 Windows Vista 中开始。 这种结构被随 Windows 性能分析器。

**标头︰**在 KernelTraceControl.h 中声明。 包括 KernelTraceControl.h。

**库︰**包含在 KernelTraceControl.dll 中。

## <a name="related-topics"></a>相关的主题


[内核跟踪控件 API 参考](kernel-trace-control-api-reference.md)

[CreateMergedTraceFile](createmergedtracefile.md)

 

 







