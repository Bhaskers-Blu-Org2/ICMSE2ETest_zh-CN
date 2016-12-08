---
title: "流式媒体评估设置远程服务器"
description: "流式媒体评估设置远程服务器"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 7cc47476-f2c3-4f82-8430-731fc035266a
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 98cef8245d64209e79c7b535eb4ff9203dcd5ca5
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="streaming-media-assessment-set-up-a-remote-server"></a>流式媒体评估︰ 将远程服务器设置


流式媒体性能评估包括的选项在两台计算机上运行评估。 在这种情况下，HTTP 流式处理第二个或远程计算机已安装的服务器应用程序传输到计算机正在运行评估的内容。 本主题介绍如何设置流式处理服务器。

**请注意**  
任何计算机上已安装 Windows 评估 Toolkit 可以作为流式处理服务器，可以提供通过 Windows 评估 Toolkit 向任何发出请求的客户端已安装的媒体文件。 对于这一评估，工作负荷是.mp4 文件和相应的.html 文件评估作为流式媒体一起使用。 例如，720p.mp4 和 720p.html 一起构成 720 p 负荷。 2 计算机评估方案中使用这些媒体工作负载，请完成以下步骤。

 

**若要设置服务器的流媒体性能评估**

1.  在远程服务器上，安装 Windows 评估 Toolkit。 有关说明，请参阅[评估控制台窗口的分步指南](windows-assessment-console-step-by-step-guide.md)或[Windows 评估服务的分步指南](windows-assessment-services-step-by-step-guide-was.md)。

2.  打开命令提示符。

3.  这取决于计算机类型中，浏览到 StreamingMediaAssessmentServer.exe 文件︰

    **请注意**  
    前面的路径假定您在其默认位置安装了 Windows 评估 Toolkit。

     

    -   对于基于 x86 的计算机上，键入︰

        ``` syntax
        C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Assessment Toolkit\Content Based Assessments\x86
        ```

    -   对于基于 x64 的计算机上，键入︰

        ``` syntax
        C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Assessment Toolkit\Content Based Assessments\amd64
        ```

4.  在命令提示符下，键入︰

    ``` syntax
    StreamingMediaAssessmentServer.exe -ContentPath <path_to_streaming_content>  [-PopulateCache <file_name_list>] [-Port <number>]
    ```

    下表描述上述命令行文本中的参数。

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>设置</th>
    <th>说明</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><em>ContentPath&lt;path_to_streaming_content&gt;</em></p></td>
    <td><p>键入包含的介质和传输服务器的相应的 HTML 页面的路径。 默认情况下，此路径为︰</p>
    <pre class="syntax" space="preserve"><code>%PROGRAMFILES%\Windows Kits\10\Assessment and Deployment Kit\Windows Assessment Toolkit\Content based Assessments\Content\Streaming Media Assessment</code></pre>
    <p>您可以指定一个绝对路径为媒体和相应的 HTML 页面。</p></td>
    </tr>
    <tr class="even">
    <td><p><em>PopulateCache&lt;file_name_list&gt;</em></p></td>
    <td><p>在内存中键入服务器将缓存的文件名称。 列出所有文件，由逗号分隔。 此示例包含默认评估使用的媒体文件︰</p>
    <pre class="syntax" space="preserve"><code>-populatecache 360p.mp4,360p.html,480p.mp4,480p.html,720p.mp4,720p.html,1080p.mp4,1080p.html,1080p60.mp4,1080p60.html</code></pre>
    <p>评估搜索路径中的所有这些文件名的<code>ContentPath</code>指定设置。 如果任何文件不存在，评估记录<em>文件丢失</em>的事件，但评估继续通过它的路径中找到的文件运行正常的过程。</p></td>
    </tr>
    <tr class="odd">
    <td><p><em>端口&lt;号&gt;</em></p></td>
    <td><p>如果您不想使用默认端口 80 的，指定端口。 默认端口可能会或不能在客户端上指定。 如果您必须使用不同的端口号，请确保您在远程服务器和客户端上指定它。</p>
    <div class="alert">
    <strong>重要</strong>  
    <p>之前指定要使用哪个端口，请验证 Windows 防火墙不会阻止通信。 有关详细信息，请参阅[Windows 防火墙，从开始到结束](http://go.microsoft.com/fwlink/?LinkId=246551)。</p>
    </div>
    <div>
     
    </div></td>
    </tr>
    </tbody>
    </table>

     

*PopulateCache*文件列表中显示以前是评估工作负载所使用文件的默认组。 本地计算机运行的流媒体性能评估的评估过程期间从远程服务器请求这些文件。 远程服务器缓存*PopulateCache*参数指定了和性能测量为他们提供到本地计算机的任何文件。

## <a name="related-topics"></a>相关的主题


[流式媒体性能](streaming-media-performance.md)

[评估服务](assessments.md)

[评估 Windows 控制台](windows-assessment-console.md)

 

 







