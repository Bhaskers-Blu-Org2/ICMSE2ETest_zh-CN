---
title: "在命令提示符下使用字段 Medic"
description: "在命令提示符下使用字段 Medic"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: CFC32516-C794-40D8-BFED-6C607E85E6CD
ms.openlocfilehash: 248222851a3e1e5c1f40a7cf66a4c68b33ac3d01
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="use-field-medic-from-a-command-prompt"></a>在命令提示符下使用字段 Medic


若要使用字段 Medic 从命令提示符处 （字段 Medic 助手），您可以安装 Microsoft.Phone.Test.Tools.FieldMedicHelper 软件包。

您必须使用 IUTool 将其安装在您的设备上。

``` syntax
%WPDKCONTENTROOT%\tools\bin\i386\IUTool.exe -p Microsoft.Phone.Test.Tools.FieldMedicHelper.spkg
```

字段 Medic 帮助程序包括以下模块︰

-   **FileMedicHelper.exe**字段 Medic 帮助器可执行文件

-   **DiagnosticSvcRPC.dll**诊断服务 RPC 包装

-   **DICData.dll**设备信息库

## <a name="syntax"></a>语法


``` syntax
FieldMedicHelper parameter <options>
```

## <a name="parameters"></a>参数


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>参数</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>-netlog</p></td>
<td><p><strong>启动</strong> - NETLOG 启动日志记录。</p>
<p><strong>停止</strong> - NETLOG 停止日志记录。</p></td>
</tr>
<tr class="even">
<td><p>-qxdm</p></td>
<td><p><strong>启动</strong> - QXDM 启动日志记录。</p>
<p><strong>停止</strong> - QXDM 停止日志记录。</p></td>
</tr>
<tr class="odd">
<td><p>-etw</p></td>
<td><p><strong>启动</strong> -启动 ETW 日志记录功能。</p>
<p><strong>停止</strong> -停止 ETW 日志记录功能。</p></td>
</tr>
<tr class="even">
<td><p>-用户转储</p></td>
<td><p>启动用户模式转储。</p></td>
</tr>
<tr class="odd">
<td><p>-kerneldump</p></td>
<td><p>启动的内核模式转储。</p></td>
</tr>
</tbody>
</table>

 

## <a name="options"></a>Options


使用参数可以使用以下选项︰

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>选项</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>-模式</p></td>
<td><p>转储模式为用户模式或内核模式转储的。</p>
<p><strong>默认</strong>使用默认转储模式。</p>
<p><strong>全</strong>使用全部转储模式。</p></td>
</tr>
<tr class="even">
<td><p>-存储</p></td>
<td><p>存储类型。 这不能与 path 参数一起使用。</p>
<p><strong>SD</strong>使用 SD 卡进行存储。</p>
<p><strong>电话</strong>se 存储设备。 默认值。</p></td>
</tr>
<tr class="odd">
<td><p>路径</p></td>
<td><p>用于存储报表的 MTP 路径。 这不能与存储参数一起使用。</p></td>
</tr>
<tr class="even">
<td><p>-timeoutduration</p></td>
<td><p>日志记录应以小时为单位的持续时间。 默认情况下，这是 48 小时。</p>
<div class="alert">
<strong>警告︰</strong>  
<p>如果指定值大于 48 小时，确保有足够的缓冲区分配和内存。</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td><p>-dmcinputpath</p></td>
<td><p>自定义 DMCFile QXDM 的路径。</p></td>
</tr>
<tr class="even">
<td><p>-custominputpath</p></td>
<td><p>ETW 或 QXDM 的自定义配置文件 XML 文件的路径。</p></td>
</tr>
</tbody>
</table>

 

## <a name="examples"></a>示例


下面的示例用于在命令提示符下运行字段 Medic 帮助器。 在 TShell 中，应使用 Cmd 设备从 PC 上运行这些命令。

启动 QXDM、 将日志存储在 SD 卡中，并在 48 小时之后停止︰

``` syntax
FieldMedicHelper -qxdm start -storage SD -timeoutduration 48
```

启动 QXDM，将日志存储在 c:\\数据\\测试\\bin\\日志︰

``` syntax
FieldMedicHelper -qxdm start -path C:\data\test\bin\logs
```

停止 QXDM:

``` syntax
FieldMediaHelper -qxdm stop
```

启动 Netlog，将日志存储在 SD 卡中，并在 10 小时后停止︰

``` syntax
FieldMedicHelper -netlog start -storage SD -timeoutduration 10
```

从 Netlog 开始默认值︰

``` syntax
FieldMedicHelper -netlog start
```

启动 Netlog，将日志存储在设备上，并在 10 小时后停止︰

``` syntax
FieldMedicHelper -netlog start -timeoutduration 10
```

或

``` syntax
FieldMedicHelper -netlog start -storage Phone -timeoutduration 10
```

停止 Netlog:

``` syntax
FieldMedicHelper -netlog stop
```

若要启动 ETW 与自定义提供程序︰

``` syntax
FieldMedicHelper -etw start -custominputpath c:\data\test\bin\FieldMedicHelper\mycustomprofile.xml
```

以 QXDM 开头中自定义路径的自定义提供程序︰

``` syntax
FieldMedicHelper -qxdm start -dmcinputpath c:\data\test\MyDMCFile.dmc -custominputpath c:\data\test\mycustomprofile.xml -path C:\data\test\bin\logs
```

 

 






