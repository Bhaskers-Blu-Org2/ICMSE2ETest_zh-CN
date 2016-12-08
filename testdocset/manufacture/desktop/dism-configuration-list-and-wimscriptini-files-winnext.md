---
author: Justinha
Description: "DISM 配置列表和 WimScript.ini 文件"
ms.assetid: 8e765558-4138-4215-bf53-09e46666a718
MSHAttr: PreferredLib:/library/windows/hardware
title: "DISM 配置列表和 WimScript.ini 文件"
ms.openlocfilehash: 167aaaa7c4c096de29844fb3c27f6499a51b679e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="dism-configuration-list-and-wimscriptini-files"></a>DISM 配置列表和 WimScript.ini 文件


部署映像服务和管理 (DISM) 工具是一个命令行工具可以用来捕获和应用 Windows 映像。 可以创建配置列表文件来确定如下︰

-   使用 DISM 工具使用**/Capture-Image**选项时，必须从捕获过程中排除的哪些文件和文件夹。

-   当使用**/compress**参数时，必须从压缩过程中排除的哪些文件夹、 文件和文件类型。

**/ConfigFile**参数使您能够捕获图像使用 DISM.exe 时自定义特定的每个文件和文件夹压缩、 捕获和边界对齐操作。 您可以使用记事本之类的文本编辑器创建配置列表 (.ini) 文件。

## <a name="span-idcreatingaconfigurationlistfilespanspan-idcreatingaconfigurationlistfilespanspan-idcreatingaconfigurationlistfilespancreating-a-configuration-list-file"></a><span id="Creating_a_Configuration_List_File"></span><span id="creating_a_configuration_list_file"></span><span id="CREATING_A_CONFIGURATION_LIST_FILE"></span>创建配置列表文件


以下几节显示在 DISM 配置列表文件中。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">节</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><code>[ExclusionList]</code></p></td>
<td align="left"><p>使您能够定义的文件和文件夹，当您使用<strong>/Capture-Image</strong>选项中排除。</p></td>
</tr>
<tr class="even">
<td align="left"><p><code>[ExclusionException]</code></p></td>
<td align="left"><p>使您可以重写默认的排除列表，当您使用<strong>/Capture-Image</strong>选项。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><code>[CompressionExclusionList]</code></p></td>
<td align="left"><p>使您能够定义的特定文件和文件夹，并还可指定文件类型，则使用<strong>/compress</strong>参数时要排除。</p>
<div class="alert">
<strong>请注意</strong>  
<p>您可以使用文件或文件夹的匹配排除从压缩文件。 您可以提供完整路径匹配，也可以使用通配符 （*）。 例如，您可以使用<strong>\WINDOWS\inf\*.pnf</strong>以匹配特定类型的文件，或<strong>\WINDOWS\inf\*</strong>以匹配整个文件夹。</p>
</div>
<div>
 
</div></td>
</tr>
</tbody>
</table>

 

### <a name="span-iddefaultexclusionlistspanspan-iddefaultexclusionlistspanspan-iddefaultexclusionlistspandefault-exclusion-list"></a><span id="Default_Exclusion_List"></span><span id="default_exclusion_list"></span><span id="DEFAULT_EXCLUSION_LIST"></span>默认的排除列表

默认情况下，DISM.exe 工具将排除下列文件。

``` syntax
[ExclusionList]
\$ntfs.log
\hiberfil.sys
\pagefile.sys
\swapfile.sys
"\System Volume Information"
\RECYCLER
\Windows\CSC

[CompressionExclusionList]
*.mp3
*.zip
*.cab
\WINDOWS\inf\*.pnf
```

### <a name="span-idexclusionlistguidelinesspanspan-idexclusionlistguidelinesspanspan-idexclusionlistguidelinesspanexclusion-list-guidelines"></a><span id="Exclusion_List_Guidelines"></span><span id="exclusion_list_guidelines"></span><span id="EXCLUSION_LIST_GUIDELINES"></span>排除列表的原则

-   只能在没有以反斜杠开头的文件路径的最后一部分中使用通配符字符。 例如︰

    ``` syntax
    myfolder\*.txt
    ```

-   您可以使用文件匹配和相对于根目录的目录匹配限制为反斜杠。 例如，您可以使用此排除列表︰

    ``` syntax
    \myfolder
    \folder\subfolder
    ```

    此列表将捕获时排除下列文件和目录"c:\\"驱动器︰

    ``` syntax
    C:\myfolder
    C:\folder\subfolder
    ```

    但是，DISM 将排除的文件或目录包含在下面的示例。

    ``` syntax
    C:\main\myfolder
    C:\data\folder\subfolder
    ```

-   您可以通过使用重写默认的排除列表`[ExclusionException]`部分。 例如︰

    ``` syntax
    [ExclusionException]
    \pagefile.sys
    "\System Volume Information"
    ```

-   如果显式`[ExclusionException]`节是提供在 WIM 配置文件中，它将始终优先于`[Exclusion List]`部分。

-   不能通过使用重写默认的压缩排除列表`[ExclusionException]`部分。

## <a name="span-idusingtheconfigurationfilespanspan-idusingtheconfigurationfilespanspan-idusingtheconfigurationfilespanusing-the-configuration-file"></a><span id="Using_the_Configuration_File"></span><span id="using_the_configuration_file"></span><span id="USING_THE_CONFIGURATION_FILE"></span>使用配置文件


如果您创建一个自定义命名的配置文件并将其存储在 DISM 目录外，您可以使用 DISM 命令来运行该文件。 在命令提示符处，打开 DISM 目录。 例如︰

``` syntax
Dism /Capture-Image /ImageFile:install.wim /CaptureDir:D:\ /Name:Drive-D /ConfigFile:<configuration list>
```

或

``` syntax
Dism /Append-Image /ImageFile:install.wim /CaptureDir:D:\ /Name:Drive-D /ConfigFile:<configuration list>
```

其中*&lt;配置列表&gt;*提供的配置文件的完整目录位置。 例如， `c:\imaging\configuration_list.ini`。 您必须使用**/Capture-Image**选项来创建新的.wim 文件或**/Append-Image**选项将追加现有.wim 文件。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)

 

 






