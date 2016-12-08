---
author: Justinha
Description: "DISM 语言和国际服务命令行选项"
ms.assetid: 6434373a-a7f9-43ff-be28-e4d48fa0b70f
MSHAttr: PreferredLib:/library/windows/hardware
title: "DISM 语言和国际服务命令行选项"
ms.openlocfilehash: 8d9ac0bae96fc24984fe1af22ee38c500b2d5d07
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="dism-languages-and-international-servicing-command-line-options"></a>DISM 语言和国际服务命令行选项


国际命令可用于更改国际设置，在 Windows 和 Windows 预安装环境 (WinPE) 的图像。 您也可以查询现有脱机或联机 Windows 映像中的设置。

为提供服务的 Windows 映像，使用部署映像服务和管理 (DISM.exe) 工具的基本语法是︰

**DISM.exe** {**/图像︰**&lt;*路径\_到\_脱机\_图像\_目录*&gt; | **/Online**} \[ **dism\_全局\_选项**\] {**服务\_选项**} \[ &lt;*服务\_参数*&gt;\]

有三种类型的国际服务命令︰

-   **获取命令**。 检索脱机映像或运行的操作系统的国际设置的报告。
-   **设置命令**。 设置脱机映像的其他国际设置。
-   **Gen LangIni 命令**。 生成 Lang.ini 文件在安装过程中使用。

下列国际服务选项可用于脱机映像︰

**DISM.exe /Image:**&lt;*路径\_到\_脱机\_图像\_目录*&gt; \[ **/Get-Intl** \] \[ **/Set-UILang** | **/Set-UILangFallback** | **/Set-SysLocale** | **/Set-UserLocale** | **/Set-InputLocale** | **/Set-AllIntl** | **/Set-Timezone** | **/Set-SKUIntlDefaults** | **/Set-LayeredDriver** \] \[ **/Gen-Langini** | **/Set-SetupUILang** | **/Distribution**\]

下列国际服务选项是可用于运行状态的操作系统︰

**DISM.exe / 在线****/Get-Intl**

下表描述了可以如何使用每个国际服务选项。 这些选项不是区分大小写的。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">选项/参数</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>选项︰ <strong>/Get-Help /？</strong></p></td>
<td align="left"><p>国际服务命令行选项后紧接着使用，显示的选项和参数的信息。 其他主题可能会在指定了映像之后变为可用。</p>
<p>示例︰</p>
<p><strong>Dism /image:C:\test\offline /Set-UILang /？</strong></p>
<p><strong>Dism 在线 / /Get-intl /？</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>选项︰ <strong>/Get-Intl</strong></p></td>
<td align="left"><p>显示国际设置和语言有关的信息。</p>
<p>使用<strong>/Online</strong>选项可以显示正在运行的操作系统中的国际设置和语言有关的信息。</p>
<p>使用<strong>/Image</strong>:&lt;<em>path_to_offline_image_directory</em> &gt;选项将显示脱机映像中的国际设置和语言有关的信息。</p>
<p>当与<strong>/Distribution</strong>选项一起使用，将显示有关国际设置和语言分布中的信息。 未验证的分布共享中的文件夹名称。 它将被报告为...\Langpacks\&lt;<em>locale_name</em>&gt;\Lp.cab。 其中&lt; <em>locale_name</em> &gt;是该文件夹的名称。</p>
<div class="alert">
<strong>请注意</strong>  
<p>用户区域设置报告仅为脱机映像。 有关运行操作系统的系统报告不包括此设置。</p>
</div>
<div>
 
</div>
<p>示例︰</p>
<p><strong>Dism / 在线 /Get-Intl</strong></p>
<p><strong>Dism /image:C:\test\offline /Get-Intl</strong></p>
<p><strong>Dism /image:C:\test\offline /distribution:C:\windows_distribution /Get-Intl</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>选项︰ <strong>/Set-UILang:</strong></p>
<p>参数︰ &lt; <em>language_name</em>&gt;</p></td>
<td align="left"><p>设置默认系统用户界面 (UI) 语言。 如果在 Windows 映像中未安装的语言，则该命令将失败。</p>
<p>&lt;<em>language_name</em> &gt;指定的名称的语言设置为默认值;例如，ja-JP。</p>
<div class="alert">
<strong>请注意</strong>  
<p>如果您安装语言界面包 (LIP)，其语言指定为默认 UI 语言 LIP 语言将设置作为系统默认 UI 语言 （或安装语言） 和母语将设置为默认 UI 语言。</p>
</div>
<div>
 
</div>
<p>示例：</p>
<p><strong>Dism /image:C:\test\offline /Set-UILang:fr-FR</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>选项︰ <strong>/Set-UILangFallback:</strong></p>
<p>参数︰ &lt; <em>language_name</em>&gt;</p></td>
<td align="left"><p>将系统用户界面的回退的默认语言设置脱机 Windows 映像中。 仅当<strong>/Set-UILang</strong>选项所指定的语言部分本地化的语言，使用此设置。</p>
<p>&lt;<em>language_name</em> &gt;指定要设置为默认回退; 语言名称例如，EN-US。</p>
<p>示例：</p>
<p><strong>Dism /image:C:\test\offline /Set-UILangFallBack:fr-FR</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>选项︰ <strong>/Set-Syslocale:</strong></p>
<p>参数︰ &lt; <em>locale_name</em>&gt;</p></td>
<td align="left"><p>设置脱机 Windows 映像中的非 Unicode 程序 （也称为的系统区域设置） 和字体设置的语言。</p>
<p>&lt;<em>locale_name</em> &gt;指定语言和区域设置设置为非 Unicode; 默认语言的名称例如，EN-US。</p>
<div class="alert">
<strong>重要</strong>  
<p>不能将系统区域设置设置仅 Unicode 语言。 如果您尝试， <strong>/Set-SysLocale</strong>选项将失败，并且不会更改为非 Unicode 程序的语言。</p>
</div>
<div>
 
</div>
<p>示例：</p>
<p><strong>Dism /image:C:\test\offline /Set-SysLocale:fr-FR</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>选项︰ <strong>/Set-UserLocale:</strong></p>
<p>参数︰ &lt; <em>locale_name</em>&gt;</p></td>
<td align="left"><p>设置&quot;标准和格式&quot;脱机 Windows 映像中的语言 （也称为用户区域设置）。 &quot;标准和格式&quot;语言的日期、 时间、 货币和数字的格式是每个用户的设置来确定默认的排序顺序和默认设置。</p>
<p>示例：</p>
<p><strong>Dism /image:C:\test\offline /Set-UserLocale:fr-FR</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>选项︰ <strong>/Set-InputLocale:</strong></p>
<p>参数︰ &lt; <em>input_locale</em>&gt;:&lt;<em>keyboard_layout</em>&gt;</p></td>
<td align="left"><p>设置脱机 Windows 映像中使用的键盘布局和输入法区域设置。</p>
<p>值&lt; <em>input_locale</em>&gt;:&lt;<em>keyboard_layout</em> &gt;对可以是以下之一︰</p>
<ul>
<li><p>&lt;<em>language_id</em>:<em>keyboard_layout</em>&gt;</p>
<p>例如，0409: 00000409</p></li>
<li><p>&lt;<em>locale_name</em>&gt;</p>
<p>例如，如果您指定的本地名称为 EN-US<strong>集-InputLocale:</strong>选项也设置为此区域设置定义的默认键盘布局。</p></li>
</ul>
<p>您可以通过使用分号作为分隔符指定多个值。 当您想要包括在单个计算机上的多个键盘的支持，这非常有用。 第一个值将设置为默认键盘。</p>
<p>在下面的注册表项中列出可以在您的计算机配置的有效键盘布局。</p>
<p><strong>置此变量 \SYSTEM\CurrentControlSet\Control\Keyboard 布局</strong></p>
<p>有关这些值的列表，请参阅[默认输入法区域设置](default-input-locales-for-windows-language-packs.md)和[默认键盘设置](windows-language-pack-default-values.md)。</p>
<p>使用要配置的语言 ID 和键盘布局的十六进制值。</p>
<p>此参数是可选的。</p>
<p>示例：</p>
<pre class="syntax" space="preserve"><code>Dism /image:C:\test\offline /Set-InputLocale:fr-fr</code></pre>
<pre class="syntax" space="preserve"><code>Dism /image:C:\test\offline /Set-InputLocale:0410:00010410</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p>选项︰ <strong>/Set-AllIntl:</strong></p>
<p>参数︰ &lt; <em>language_name</em>&gt;</p></td>
<td align="left"><p>设置的默认系统用户界面语言为非 Unicode 程序的语言&quot;标准和格式&quot;语言和输入法区域设置和脱机 Windows 映像中指定的语言的键盘布局。 此选项指定下面的语言值︰</p>
<ul>
<li><p>用户界面语言</p></li>
<li><p>系统区域设置</p></li>
<li><p>用户区域设置</p></li>
<li><p>输入法区域设置</p></li>
</ul>
<p>如果与任何单个语言或区域设置指定的选项一起使用，则单个设置优先。</p>
<p>&lt;<em>language_name</em> &gt;指定语言名称和区域设置的代码;例如，EN-US，es-ES 或 fr 法属</p>
<p>示例：</p>
<p><strong>Dism /image:C:\test\offline /Set-AllIntl:fr-FR</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>选项︰ <strong>/Set-TimeZone:</strong></p>
<p>参数︰ &lt; <em>timezone_name</em>&gt;</p></td>
<td align="left"><p>在 Windows 映像中设置默认时区。 设置时区之前, DISM 验证指定的时区字符串是有效的图像。</p>
<p>&lt;<em>timezone_name</em> &gt;指定的时区使用;例如，太平洋标准时间。 时区字符串的完整列表，请参阅 Windows® 无人参与安装参考。 在计算机上运行 Windows 7，您可以使用 tzutil 命令行工具列出该计算机所在的时区。 默认情况下，在 Windows 7 上安装 tzutil 工具。</p>
<p>时区的名称必须与在<strong>HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\TimeZones\</strong>注册表中的时区设置的名称完全匹配。</p>
<p>如果将自定义时区添加到计算机时，您可以指定该自定义时区字符串。</p>
<p>示例：</p>
<p><strong>Dism /image:C:\test\offline /Set-TimeZone:&quot;w。 欧洲标准时间&quot;</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>选项︰ <strong>/Set-SKUIntlDefaults:</strong></p>
<p>参数︰ &lt; <em>language_name</em>&gt;</p></td>
<td align="left"><p>设置的默认系统用户界面语言为非 Unicode 程序的语言&quot;标准和格式&quot;语言和输入法区域设置，键盘布局，和时间区域中指定的默认值为脱机 Windows 映像的值&lt; <em>language_name</em>&gt;。 <strong>/Set-SKUIntlDefaults</strong>选项不会更改日语和朝鲜语键盘的键盘驱动程序。 您必须使用<strong>/Set-LayeredDriver</strong>选项更改此设置。</p>
<p>使用<strong>/ 集 SKUIntlDefaults</strong>若要更改所有国际设置脱机 Windows 映像中以匹配在零售安装过程中设置的默认值。 每个语言包默认值的详细信息，请参阅[默认输入法区域设置的 Windows 语言包](default-input-locales-for-windows-language-packs.md)。</p>
<p>此参数是可选的。 如果再加上此部分前面的设置之一，单独设置优先。</p>
<p>如果传递的语言匹配仅 Unicode 区域设置，将不会更改系统区域设置，但命令不会失败。</p>
<p>示例：</p>
<p><strong>Dism /image:C:\test\offline /Set-SKUIntlDefaults:fr-FR</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>选项︰ <strong>/Set-LayeredDriver:</strong></p>
<p>参数︰ &lt; <em>1 6</em>&gt;</p></td>
<td align="left"><p>指定要用于日语或朝鲜语键盘的键盘驱动程序。</p>
<p>在日本，很多零售用户有 106 个键键盘，而其他人有 101 或 102 键的键盘。 在韩国，有几种不同类型的键盘，一些具有不同数目的项。</p>
<p>有关这些设置的可能值为 [1-6]:</p>
<ol>
<li><p>指定 PC / AT 增强型键盘 （102/101-键）。</p></li>
<li><p>指定朝鲜语的 PC / 101 键兼容的键盘 MS 自然键盘 （类型 1） 处。</p></li>
<li><p>指定朝鲜语的 PC / 101 键兼容的键盘 MS 自然键盘 （类型 2） 处。</p></li>
<li><p>指定朝鲜语的 PC / 101 键兼容的键盘 MS 自然键盘 （类型 3） 处。</p></li>
<li><p>指定朝鲜语键盘 （103/106 键）。</p></li>
<li><p>指定日语键盘 （106/109 项）。</p></li>
</ol>
<p>示例：</p>
<p><strong>Dism /image:C:\test\offline /Set-LayeredDriver:1</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>选项︰ <strong>/Gen-LangINI:</strong></p></td>
<td align="left"><p>生成一个新的 Lang.ini 文件，它是由安装程序用于定义图像中的语言包和外部通讯组中。 它还定义安装程序的默认 UI 语言。</p>
<p>新的 Lang.ini 文件将添加到 Windows 分发的源文件夹中。</p>
<div class="alert">
<strong>请注意</strong>  
<p>您将不会提示您覆盖现有 Lang.ini 文件的权限。 现有的 Lang.ini 文件将被自动覆盖。</p>
</div>
<div>
 
</div>
<p>您必须指定脱机 Windows 映像 (<strong>/图像︰</strong>&lt;<em>path_to_offline_image.wim</em> &gt;和分发 (<strong>/Distribution:</strong>&lt;<em>path_to_distribution_directory</em>&gt;)。</p>
<p>示例：</p>
<p><strong>Dism /image:C:\test\offline /Gen-LangINI /distribution:C:\windows_distribution</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>选项︰ <strong>/Set-SetupUILang:</strong></p>
<p>参数︰ &lt; <em>language_name</em>&gt;</p></td>
<td align="left"><p>定义将使用由安装程序安装的默认语言。 如果不使用这种语言，安装程序将自动使用英语。</p>
<p>这是一个可选的命令。 如果不使用，则将使用图像中的默认 UI 语言。 如果不存在该语言，则将使用的显示语言列表中的第一语言。</p>
<p>示例：</p>
<p><strong>Dism /image:C:\test\offline /Set-SetupUILang:fr-FR /distribution:C:\windows_distribution</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p>选项︰ <strong>/Distribution:</strong></p>
<p>参数︰ &lt; <em>path_to distribution_directory</em>&gt;</p></td>
<td align="left"><p>指定的路径窗口分布。 Windows 分发是内容的释放在 Windows 产品 DVD 的副本。 如果有外部语言包，此选项是仅供与<strong>/Get-Intl</strong>和<strong>/Gen-LangINI</strong>选项一起使用。</p>
<p>示例：</p>
<p><strong>Dism /image:C:\test\offline /Gen-LangINI /distribution:C:\windows_distribution</strong></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idlimitationsspanspan-idlimitationsspanspan-idlimitationsspanlimitations"></a><span id="Limitations"></span><span id="limitations"></span><span id="LIMITATIONS"></span>限制


-   无法在 Windows Vista 或 Windows Server 2008 的图像上使用 DISM 国际服务命令。 有关处理 Windows Vista 和 Windows Server 2008 的映像的信息，请参阅 Windows OEM 预安装工具包 (Windows OPK) 或 Windows 自动安装工具包 (Windows AIK) 的 Windows Vista SP1 版本。
-   不能与国际服务命令相同的命令行上使用其他服务命令。
-   不能将系统区域设置设置仅 Unicode 语言。

    以下语言仅 Unicode (在格式表中列出的语言︰ 语言-国家/地区):

    阿姆哈拉语-埃塞俄比亚

    哈萨克语-哈萨克斯坦

    Odia-印度 （Odia 脚本）

    亚美尼亚语-亚美尼亚

    高棉语-柬埔寨

    普什图语-阿富汗

    阿萨姆语-印度

    贡根语-印度

    旁遮普语-印度 （果鲁穆）

    孟加拉语-孟加拉国

    老挝语-老挝人民民主共和国

    梵语-印度

    孟加拉语-印度 （孟加拉语）

    马拉雅拉姆语-印度 （马拉雅拉姆语字符集）

    僧伽罗语-斯里兰卡

    马尔代夫语-马尔代夫

    马耳他-马耳他

    叙利亚语-叙利亚

    格鲁吉亚语-格鲁吉亚

    毛利语-新西兰

    泰米尔语-印度

    古吉拉特语-印度 （古吉拉特语字符集）

    马拉地语-印度

    泰卢固语-印度 （泰卢固语字符集）

    北印度语-印度

    蒙古语 （蒙古语）-中国

    西藏语-中国

    因纽特语 （音节）-加拿大

    尼泊尔语-尼泊尔联邦民主共和国

    彝语-中国

    卡纳达语-印度 （埃纳）

     

-   不要更新之后安装语言包。

    如果您安装的更新 (修补程序后，常规分发版本\[GDR\]，或服务包\[SP\]) 在安装语言包之前包含依赖于语言的资源，不会应用更新中包含的特定于语言的更改。 总是在安装更新之前安装语言包。

-   通过使用指定时区时**/Set-TimeZone:**&lt;*时区\_名称*&gt;必须使用直引号替换多个单词。 例如， **/Set-TimeZone:"太平洋标准时间"**。 如果您复制并粘贴该时区名称，包括引号，从 Microsoft® Word 文档中，可能无法识别在引号和命令行可能会失败。
-   如果您处理的是国际的映像，并且宿主环境中不支持该映像中的语言，您可能无法从国际图像读取产生一条错误消息。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[DISM 是什么？](what-is-dism.md)

[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)

[部署映像服务和管理 (DISM) 命令行选项](deployment-image-servicing-and-management--dism--command-line-options.md)

 

 






