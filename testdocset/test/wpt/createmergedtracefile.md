---
title: CreateMergedTraceFile
description: CreateMergedTraceFile
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: d641530d-2be1-4266-962b-97863cff2e57
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: ed2f3f973e839c65390e3e886ae0d2ea07e16960
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="createmergedtracefile"></a>CreateMergedTraceFile


此函数合并到单一的输出文件的多个跟踪文件。

``` syntax
ULONG
WINAPI
CreateMergedTraceFile(
__in LPCWSTR wszMergedFileName,
__in LPCWSTR wszTraceFileNames[],
__in ULONG cTraceFileNames,
__in DWORD dwExtendedDataFlags
);
```

## <a name="parameters"></a>参数


<a href="" id="wszmergedfilename--in-"></a>*wszMergedFileName*\[in\]  
指定输出跟踪文件的名称。

<a href="" id="wsztracefilenames--in-"></a>*wszTraceFileNames*\[in\]  
为要合并的跟踪文件的数组的指针。

<a href="" id="ctracefilenames--in-"></a>*cTraceFileNames*\[in\]  
*WszTraceFileNames*数组中的元素数。

<a href="" id="dwextendeddataflags--in-"></a>*dwExtendedDataFlags*\[in\]  
这些标志指定要将注入合并的跟踪文件的系统信息。 有关有效标志的详细信息，请参阅[自定义系统注入信息](custom-injection-of-system-information.md)。

## <a name="return-value"></a>返回值


错误\_成功表示成功。

可能的错误值如下表所述。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>错误值</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ERROR_INSUFFICIENT_BUFFER</p></td>
<td><p>可能是指示合并的跟踪不包含一套完整的每个文件中的事件。</p></td>
</tr>
<tr class="even">
<td><p>ERROR_REVISION_MISMATCH</p></td>
<td><p>可能表示要合并的跟踪文件包含无法合并的不同版本的事件。</p></td>
</tr>
</tbody>
</table>

 

如果这些错误值都不会返回，则返回的系统错误代码。

## <a name="remarks"></a>备注


您可以合并两个或多个跟踪文件从同一台计算机捕获到一个跟踪文件的并发会话。 如果这些文件具有相同的启动时间，也可以合并来自其他跟踪会话的跟踪文件。 （可选） 合并操作添加了有关跟踪记录的元数据。

此函数可以插入到一个跟踪文件的扩展的数据。 在这种情况下， *wszMergedFileName*数组包含仅包含一个元素，即跟踪文件的名称。

**请注意**  
未并入的内核跟踪无法正确解码的符号。

 

该 API 仅实现以 Unicode。

**要求**

**版本︰**可用于在 Windows Vista 中开始。 这种结构被随 Windows 性能分析器。

**标头︰**在 KernelTraceControl.h 中声明。 包括 KernelTraceControl.h。

**库︰**包含在 KernelTraceControl.dll 中。

## <a name="related-topics"></a>相关的主题


[函数](functions-wpa.md)

[自定义注入的系统信息](custom-injection-of-system-information.md)

 

 







