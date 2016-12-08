---
title: "ResultsUtil 命令行选项"
description: "ResultsUtil 命令行选项"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 7cf8c26e-50b5-4634-9e60-80ff7d69c22d
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: ca497a3c82481e2f20c1c3bc1e81bbd9dec0f4f2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="resultsutil-command-line-options"></a>ResultsUtil 命令行选项


当您想要将评估结果存储在 SQL Server 数据库中使用 ResultsUtil 命令。 默认情况下 Windows 评估服务结果存储在服务器上存储结果。 ResultsUtil 命令用于配置 Windows 评估服务服务器 （或独立服务器） 来存储作业结果从结果共享到 SQL 数据库。 它还用于将现有结果导入到 SQL 数据库。 在服务器上安装 Windows 评估服务后，使用 ResultsUtil 命令来导入单个结果或 Windows 评估将服务配置为自动过帐到数据库结果之前初始化结果数据库的 SQL Server 实例上。

**警告**  
在 SQL Server 数据库中存储的结果不包括评估平台表示层，不能在 Windows 评估服务的客户端 (Windows ASC) 中查看。 自定义的报告解决方案需要查看结果。

 

## <a name="remarks"></a>备注


从 Windows 8.1，现在可以批处理将结果集导入到数据库和从数据库中删除的批次。 用于标记结果导入批次中的跟踪机制是批次 id。 批导入 (/ B) 可以指向结果集的文件夹并将其导入使用一条命令。 此命令的输出提供了以后可用于删除批次，如果发生任何导入错误的批次 ID，如果没有输入错误在元数据中，例如。

**请注意**  
/Tags 选项不再受支持。

 

**请注意**  
当使用数据库连接字符串，与 /db 选项或使用 /FileSave 选项保存到 ResultsUtil.exe.config 时，必须指定**RelaxResults**的初始目录。 请参阅下面的选项的示例表。

 

### <a name="metadata"></a>元数据

元数据是非常有用的在比较结果时或报告上的结果集合。 有三种类型的元数据，可以用于对齐数据导入数据库。 请参阅下面示例的完整选项表中的对应项。

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>类型</th>
<th>选项</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Project</strong></p></td>
<td><p>/p</p></td>
<td><p>表示一组计算机分组</p></td>
</tr>
<tr class="even">
<td><p><strong>测试通过</strong></p></td>
<td><p>/t</p></td>
<td><p>由一个测试阶段或特定生成创建的结果集</p></td>
</tr>
<tr class="odd">
<td><p><strong>运行标记</strong></p></td>
<td><p>/rt</p></td>
<td><p>在测试运行期间使用的配置。 例如，您可以运行之前和之后来衡量性能的驱动程序更新</p></td>
</tr>
</tbody>
</table>

 

## <a name="system-requirements"></a>系统要求


运行 ResultsUtil 命令系统要求如下︰

-   Windows 评估服务

-   Windows Server 2008 R2、 Windows Server 2012 或 Windows Server 2012 R2

-   完整版本的 SQL Server 2008 R2 或更高版本

## <a name="configuration-overview"></a>配置概述


ResultsUtil 使用配置文件存储在与可执行文件位于同一目录中。 下面各节所述的各个配置选项。 部分未在下面列出的配置文件特定于 SQL 服务器，应该只能由经验丰富的管理员进行编辑。

## <a name="resultsutilexe-command-line-options"></a>ResultsUtil.exe 命令行选项


若要初始化数据库，请使用下面的语法︰

**ResultsUtil /InitializeDatabase \[/DB&lt;数据库连接字符串&gt;\] \[/User&lt;数据库用户名称&gt;\] \[/FileSave\]**

若要将结果导入，请使用以下语法︰

**ResultsUtil.exe /I \[/s&lt;文件路径&gt;\] \[/b&lt;文件夹路径&gt;\] \[/a\] \[/db&lt;数据库连接字符串&gt;\] \[/user&lt;数据库用户名称&gt;\] \[/p&lt;项目名称&gt;\] \[/t&lt;测试阶段名称&gt;\] \[/rt&lt;运行标记&gt;\] \[/标记&lt;用户定义的标记&gt;\]**

若要删除一批的结果已导入到数据库中，请使用下面的语法︰

**ResultsUtil /D /BID&lt;生成批次 ID&gt; \[DB&lt;数据库连接字符串&gt;\] \[/User&lt;数据库用户名称&gt;\]**

下表提供了如何使用每个选项的说明。 这些选项不是区分大小写的。

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
<td><p>/ InitializeDatabase</p></td>
<td><p>指定的 SQL Server 实例上安装结果数据库。</p>
<p>连接字符串可以用于配置与数据库的连接。 如果不提供任何命令行选项，则 /InitializeDatabase 命令使用在配置文件中的是什么。</p>
<div class="alert">
<strong>请注意</strong>  
<p>默认文件中的两个配置不使用，并且可以删除。</p>
</div>
<div>
 
</div>
<p>示例：</p>
<p><strong>ResultsUtil /InitializeDatabase /db&quot;数据源 = localhost\WAS_SQLSERVER; Initial Catalog = RelaxResults; 集成安全性 = True&quot; /user MyName /filesave</strong></p></td>
</tr>
<tr class="even">
<td><p>/ ImportResults</p>
<p>/I</p></td>
<td><p>指定的结果文件导入到数据库中的结果。</p>
<p>示例：</p>
<p><strong>ResultsUtil /ImportResults /inputfile C:\WAS\Results\JobResultsComputerGUID.xml /db&quot;数据源 = localhost\WAS_SQLSERVER; Initial Catalog = RelaxResults; 集成安全性 = True&quot; /user MyName /project MyProject /testpass Milestone1 /runtag 命名为 Run1 /tags M1Results</strong></p></td>
</tr>
<tr class="odd">
<td><p>/ ConfigureWASserver</p>
<p>/C</p></td>
<td><p>配置 Windows 评估服务来存储结果到指定的结果数据库的指定的实例。</p>
<p>示例：</p>
<p><strong>ResultsUtil /ConfigureWASserver /db&quot;数据源 = localhost\WAS_SQLSERVER; Initial Catalog = RelaxResults; 集成安全性 = True&quot; /user MyName /WasServer http://WASserver:8000/放松/服务</strong></p></td>
</tr>
<tr class="even">
<td><p>/ 输入文件<em>&lt;文件名&gt;</em></p>
<p>/S</p></td>
<td><p>标识要导入到结果数据库的结果文件。 必须指定结果文件的完整路径。</p>
<p>示例：</p>
<p><strong>ResultsUtil /ImportResults /inputfile C:\WAS\Results\JobResultsComputerGUID.xml</strong></p></td>
</tr>
<tr class="odd">
<td><p>/B</p></td>
<td><p>批量导入结果文件夹中的文件。 可以以后使用的批次 ID 来从数据库中删除此数据。</p>
<p>示例：</p>
<p><strong>ResultsUtil /ImportResults /B C:\WAS\Results\ /db&quot;数据源 = localhost\WAS_SQLSERVER; Initial Catalog = RelaxResults; 集成安全性 = True&quot; /user MyName /project MyProject /testpass Milestone1 /runtag 命名为 Run1 /tags M1Results</strong></p></td>
</tr>
<tr class="even">
<td><p>/DB <em> &lt;database_connection_string&gt;</em></p></td>
<td><p>连接字符串，其中包含要创建的 SQL Server 和数据库的实例。</p>
<p>示例：</p>
<p><strong>ResultsUtil /InitializeDatabase /db&quot;数据源 = localhost\WAS_SQLSERVER; Initial Catalog = RelaxResults; 集成安全性 = True&quot; /user MyName /filesave</strong></p></td>
</tr>
<tr class="odd">
<td><p>/ 用户<em>&lt;用户名&gt;</em></p></td>
<td><p>SQL 服务器连接的用户名。</p>
<p>示例：</p>
<p><strong>ResultsUtil /ImportResults /inputfile C:\WAS\Results\JobResultsComputerGUID.xml /db&quot;数据源 = localhost\WAS_SQLSERVER; Initial Catalog = RelaxResults; 集成安全性 = True&quot; /user MyName</strong></p></td>
</tr>
<tr class="even">
<td><p>/ 项目<em>&lt;文件的内容&gt;</em></p>
<p>/P</p></td>
<td><p>将项目名称与要导入的数据，或者如果已经存在，则将覆盖它。 为从本地计算机运行的 Windows 评估控制台作业导入的评估结果，项目名称不存在。 如果从运行在实验室环境中使用 Windows 评估服务作业生成结果，项目名称已存在。</p>
<p>示例：</p>
<p><strong>ResultsUtil /ImportResults /inputfile C:\WAS\Results\JobResultsComputerGUID.xml /project 项目 1</strong></p></td>
</tr>
<tr class="odd">
<td><p>/ TestPass <em> &lt;test_pass_name&gt;</em></p>
<p>/T</p></td>
<td><p>创建一个测试通过元数据标记，或如果已经存在覆盖它。 测试通过元数据可帮助您组织特定里程碑或测试周期的结果。</p>
<p>示例：</p>
<p><strong>ResultsUtil /ImportResults /inputfile C:\WAS\Results\JobResultsComputerGUID.xml /project 项目 1 /testpass Milestone1</strong></p></td>
</tr>
<tr class="even">
<td><p>/ RunTag <em> &lt;run_tag_name&gt;</em></p>
<p>/RT</p></td>
<td><p>创建运行的标记的元数据或如果已经存在，则覆盖它。 搜索结果时运行标记的元数据可帮助识别特定的作业运行实例。</p>
<p>示例：</p>
<p><strong>ResultsUtil /ImportResults /inputfile C:\WAS\Results\JobResultsComputerGUID.xml /project MyProject /testpass Milestone1 /runtag 命名为 Run1</strong></p></td>
</tr>
<tr class="odd">
<td><p>/ 投标&lt;result_batch_ID&gt;</p></td>
<td><p>指定要删除的结果的批次 ID。</p>
<p>示例：</p>
<p><strong>ResultsUtil /D /BID&lt;生成批次 ID&gt;</strong></p></td>
</tr>
<tr class="even">
<td><p>/ 归档</p>
<p>/A</p></td>
<td><p>归档文件之前将其导入的结果。</p>
<p>通过使用指定的存档路径<code>archivePath</code>配置文件中的节点。 为了存档文件，则必须配置存档路径。</p>
<p>示例：</p>
<p><strong>ResultsUtil /ImportResults /inputfile C:\WAS\Results\JobResultsComputerGUID.xml /db&quot;数据源 = localhost\WAS_SQLSERVER; Initial Catalog = RelaxResults; 集成安全性 = True&quot; /user MyName /project MyProject /testpass Milestone1 /runtag 命名为 Run1 /tags M1Results/存档</strong></p></td>
</tr>
<tr class="odd">
<td><p>/D</p></td>
<td><p>删除批导入数据库的结果。</p>
<p>示例：</p>
<p><strong>ResultsUtil /D /BID&lt;生成批次 ID&gt;</strong></p></td>
</tr>
<tr class="even">
<td><p>/ 存</p></td>
<td><p>将数据库配置文件中，resultsutil.exe.config，保存到与 ResultsUtil 相同的位置。 数据库配置文件与数据库的连接字符串和用户名称预先设置，以便不需要输入每次导入结果。</p>
<div class="alert">
<strong>请注意</strong>  
<p>有是一个数据库配置文件。 如果您有多个结果数据库命令行选项将优先于配置文件。</p>
</div>
<div>
 
</div>
<p>示例：</p>
<p><strong>ResultsUtil /InitializeDatabase /db&quot;数据源 = localhost\WAS_SQLSERVER; Initial Catalog = RelaxResults; 集成安全性 = True&quot; /user MyName /filesave</strong></p></td>
</tr>
<tr class="odd">
<td><p>/ 安静</p></td>
<td><p>不显示状态消息。</p>
<p>示例：</p>
<p><strong>ResultsUtil /ConfigureWASserver /db&quot;数据源 = localhost\WAS_SQLSERVER; Initial Catalog = RelaxResults; 集成安全性 = True&quot; /User MyName /WasServer http://MyServer:8000/放松/服务 /Quiet</strong></p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[Windows 评估服务](windows-assessment-services-technical-reference.md)

 

 







