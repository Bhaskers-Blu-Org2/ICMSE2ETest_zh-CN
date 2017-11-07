---
author: Justinha
Description: "Oobe.xml 设置"
ms.assetid: 2c8ecddc-7099-451e-a069-642f654d4fbf
MSHAttr: PreferredLib:/library/windows/hardware
title: "Oobe.xml 设置"
ms.openlocfilehash: e8817a2407a831cabd0e4264ceb69cc9a7e17e1d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="oobexml-settings"></a>Oobe.xml 设置


本主题介绍可以在 Oobe.xml 设置的设置。

## <a name="span-idoobexmlsettingsspanspan-idoobexmlsettingsspanoobexml-settings"></a><span id="oobe.xml_settings"></span><span id="OOBE.XML_SETTINGS"></span>Oobe.xml 设置


下表显示了可用的设置在 Oobe.xml 文件中，通过部分，说明以及有关每个设置的值。

**HID 配对**

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">设置</th>
<th align="left">说明</th>
<th align="left">值</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>mouseImagePath</p></td>
<td align="left"><p>鼠标配对指令图像的绝对路径。</p>
<p>不得大于 630 x 372 像素图像。 缩放以适合在纵向模式下或在小板型。</p></td>
<td align="left"><p>图像的绝对路径</p></td>
</tr>
<tr class="even">
<td align="left"><p>mouseText</p></td>
<td align="left"><p>帮助文本，如果不能打开鼠标配对指令图像显示在页面的底部。 此文本还通过讲述人用于可访问性。</p></td>
<td align="left"><p>String</p></td>
</tr>
<tr class="odd">
<td align="left"><p>mouseErrorImagePath</p></td>
<td align="left"><p>鼠标配对错误图像的绝对路径。</p>
<p>不得大于 630 x 372 像素图像。 它将缩放以适合在纵向模式下或在小板型。</p></td>
<td align="left"><p>图像的绝对路径</p></td>
</tr>
<tr class="even">
<td align="left"><p>mouseErrorText</p></td>
<td align="left"><p>如果没有加载鼠标配对图像时出错的问题，会显示该错误文本。 此文本还通过讲述人用于可访问性。</p></td>
<td align="left"><p>String</p></td>
</tr>
<tr class="odd">
<td align="left"><p>keyboardImagePath</p></td>
<td align="left"><p>到第一个键盘配对指令图像的绝对路径。</p>
<p>不得大于 630 x 372 像素图像。 它将缩放以适合在纵向模式下或在小板型。</p></td>
<td align="left"><p>图像的绝对路径</p></td>
</tr>
<tr class="even">
<td align="left"><p>keyboardText</p></td>
<td align="left"><p>帮助文本，如果不能打开键盘配对指令图像显示在页面的底部。 此文本还通过讲述人用于可访问性。</p></td>
<td align="left"><p>String</p></td>
</tr>
<tr class="odd">
<td align="left"><p>keyboardPINImagePath</p></td>
<td align="left"><p>到第二个键盘配对指令图像的绝对路径。</p>
<p>不得大于 630 x 372 像素图像。 缩放以适合在纵向模式下或在小板型。</p></td>
<td align="left"><p>图像的绝对路径</p></td>
</tr>
<tr class="even">
<td align="left"><p>keyboardErrorImagePath</p></td>
<td align="left"><p>与键盘配对错误图像的绝对路径。</p>
<p>不得大于 630 x 372 像素图像。 缩放以适合在纵向模式下或在小板型。</p></td>
<td align="left"><p>图像的绝对路径</p></td>
</tr>
<tr class="odd">
<td align="left"><p>keyboardErrorText</p></td>
<td align="left"><p>如果没有加载键盘配对图像时出错的问题，将显示此错误文本。 此文本还通过讲述人用于可访问性。</p></td>
<td align="left"><p>String</p></td>
</tr>
</tbody>
</table>

 

**注册页**

下表显示在 OOBE.xml 注册页面设置和允许的值。

**请注意**  
连字符的符号，&，不能使用 OOBE.xml 本部分中。 使用单词和相反。

 

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Section</th>
<th align="left">设置</th>
<th align="left">说明</th>
<th align="left">值</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p>title</p></td>
<td align="left"><p>必需。 注册页的标题的文本。</p></td>
<td align="left"><p>最多 25 个字符的字符串。</p></td>
</tr>
<tr class="even">
<td align="left"><p></p></td>
<td align="left"><p>副标题</p></td>
<td align="left"><p>必需。 用于描述注册页的文本。</p></td>
<td align="left"><p>多达 200 个字符的字符串。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>textbox1</strong></p></td>
<td align="left"><p></p></td>
<td align="left"><p></p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p></p></td>
<td align="left"><p>label</p></td>
<td align="left"><p>为 textbox1 的标签的文本。 对于 textbox1 显示必需。</p></td>
<td align="left"><p>最多 20 个字符的字符串。</p></td>
</tr>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p>inputscope</p></td>
<td align="left"><p>要设置的触摸键盘范围值。</p></td>
<td align="left"><p>两个支持的范围︰</p>
<p>4 (IS_EMAIL_USERNAME)</p>
<p>29 (IS_NUMBERS)</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>textbox2</strong></p></td>
<td align="left"><p></p></td>
<td align="left"><p></p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p>label</p></td>
<td align="left"><p>Textbox2 的标签的文本。 对于 textbox2 显示必需。</p>
<p></p></td>
<td align="left"><p>最多 20 个字符的字符串。</p></td>
</tr>
<tr class="even">
<td align="left"><p></p></td>
<td align="left"><p>inputscope</p></td>
<td align="left"><p>要设置的触摸键盘范围值。</p></td>
<td align="left"><p>两个支持的范围︰</p>
<p>4 (IS_EMAIL_USERNAME)</p>
<p>29 (IS_NUMBERS)</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>checkbox1</strong></p></td>
<td align="left"><p></p></td>
<td align="left"><p></p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p></p></td>
<td align="left"><p>label</p></td>
<td align="left"><p>文本标签 checkbox1。 对于 checkbox1 显示必需。</p></td>
<td align="left"><p>多达 250 个字符的字符串。 我们强烈建议使用不超过 100 个字符，因为此长度的文本将放在一行上。</p></td>
</tr>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p>默认值</p></td>
<td align="left"><p>要设置 checkbox1 为选中或未选中的值。</p></td>
<td align="left"><p>真或假。 值为 true 表示复选框默认情况下处于选中状态。 False 表示复选框默认情况下未被选中。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>checkbox2</strong></p>
<p></p></td>
<td align="left"><p></p></td>
<td align="left"><p></p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p>label</p></td>
<td align="left"><p>Checkbox2 的标签的文本。 所需的 checkbox2 显示</p></td>
<td align="left"><p>多达 250 个字符的字符串。 我们强烈建议使用不超过 100 个字符，因为此长度的文本将放在一行上。</p>
<p></p></td>
</tr>
<tr class="even">
<td align="left"><p></p></td>
<td align="left"><p>默认值</p></td>
<td align="left"><p>要将 checkbox2 设置为选中或未选中的值。</p></td>
<td align="left"><p>真或假。 值为 true 表示复选框默认情况下处于选中状态。 False 表示复选框默认情况下未被选中。</p>
<p></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>checkbox3</strong></p></td>
<td align="left"><p></p></td>
<td align="left"><p></p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p></p></td>
<td align="left"><p>label</p></td>
<td align="left"><p>Checkbox3 的标签的文本。 所需的 checkbox3 显示</p></td>
<td align="left"><p>多达 250 个字符的字符串。 我们强烈建议使用不超过 100 个字符，因为此长度的文本将放在一行上。</p>
<p></p></td>
</tr>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p>默认值</p></td>
<td align="left"><p>要将 checkbox3 设置为选中或未选中的值。</p></td>
<td align="left"><p>真或假。 值为 true 表示复选框默认情况下处于选中状态。 False 表示复选框默认情况下未被选中。</p>
<p></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>link1</strong></p></td>
<td align="left"><p></p></td>
<td align="left"><p></p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p>label</p></td>
<td align="left"><p><strong>.Rtf</strong>文件的链接的标签。 所需的 link1 显示。</p></td>
<td align="left"><p>最多 100 个字符的字符串。</p>
<p></p></td>
</tr>
<tr class="even">
<td align="left"><p></p></td>
<td align="left"><p>链接</p></td>
<td align="left"><p>文件必须命名为 linkfile1.rtf。 OOBE 搜索命名为 linkfile1.rtf、 linkfile2.rtf 或 linkfile3.rtf 的 oobe\info 文件夹下的文件。 OOBE 搜索下的 oobe\info 的相应区域设置和语言特定子文件。</p></td>
<td align="left"><p>linkfile1.rtf</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>link2</strong></p></td>
<td align="left"><p></p></td>
<td align="left"><p></p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p></p></td>
<td align="left"><p>label</p></td>
<td align="left"><p><strong>.Rtf</strong>文件的链接的标签。 所需的 link2 显示。</p></td>
<td align="left"><p>最多 100 个字符的字符串。</p>
<p></p></td>
</tr>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p>链接</p></td>
<td align="left"><p>文件必须命名为 linkfile2.rtf。 OOBE 搜索命名为 linkfile1.rtf、 linkfile2.rtf 或 linkfile3.rtf 的 oobe\info 文件夹下的文件。 OOBE 搜索适当区域设置和语言特定子文件夹下的 oobe\info 文件。</p></td>
<td align="left"><p>linkfile2.rtf</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>link3</strong></p></td>
<td align="left"><p></p></td>
<td align="left"><p></p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p>label</p></td>
<td align="left"><p><strong>.Rtf</strong>文件的链接的标签。 所需的 link3 显示。</p></td>
<td align="left"><p>最多 100 个字符的字符串。</p>
<p></p></td>
</tr>
<tr class="even">
<td align="left"><p></p></td>
<td align="left"><p>链接</p></td>
<td align="left"><p>文件必须命名为 linkfile3.rtf。 OOBE 搜索命名为 linkfile1.rtf、 linkfile2.rtf 或 linkfile3.rtf 的 oobe\info 文件夹下的文件。 OOBE 搜索适当区域设置和语言特定子文件夹下的 oobe\info 文件。</p></td>
<td align="left"><p>linkfile3.rtf</p></td>
</tr>
</tbody>
</table>

 

**最终用户许可协议文件及语言、 区域设置和时区的默认值。**

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Section</th>
<th align="left">设置</th>
<th align="left">说明</th>
<th align="left">值</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p>eulafilename</p></td>
<td align="left"><p>特定于语言和位置的制造商最终用户许可协议 (EULA) 的版本。</p></td>
<td align="left"><p>.rtf 文件。</p></td>
</tr>
<tr class="even">
<td align="left"><p>默认值</p></td>
<td align="left"><p></p></td>
<td align="left"><p></p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p>language</p></td>
<td align="left"><p>输入法区域设置的十进制标识符。</p></td>
<td align="left"><p>输入法区域设置的十进制标识符。 可以在下列主题中，[为 Windows 语言包默认输入区域设置](default-input-locales-for-windows-language-packs.md)中找到这些值。</p></td>
</tr>
<tr class="even">
<td align="left"><p></p></td>
<td align="left"><p>位置</p></td>
<td align="left"><p>通过使用 GEOID 值转换为其十进制值的指定位置。</p></td>
<td align="left"><p>GEOIDs 的列表，请参阅[MSDN Web 站点](http://go.microsoft.com/fwlink/?LinkId=141804)。</p></td>
</tr>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p>区域设置</p></td>
<td align="left"><p>通过使用区域设置标识符 (LCID) 值指定区域设置。</p></td>
<td align="left"><p>Lcid 的完整列表，请参阅此[Microsoft 全球开发 Web 站点](http://go.microsoft.com/fwlink/?LinkId=63028)。 有关 Lcid 和它们是可用的 Windows 版本的列表，下载[&quot;Windows 语言代码标识符 (LCID) 引用&quot;](http://go.microsoft.com/fwlink/?LinkId=140989)从 MSDN。 在此白皮书中，在左窗格中，请转到&quot;附录 a: Windows 行为&quot;显示 LCID 和它是可用的 Windows 版本的表。</p></td>
</tr>
<tr class="even">
<td align="left"><p></p></td>
<td align="left"><p>键盘</p></td>
<td align="left"><p>指定的键盘布局。</p></td>
<td align="left"><p>使用在<strong>HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\Keyboard 布局</strong>注册表中列出的键盘值。</p></td>
</tr>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p>时区</p></td>
<td align="left"><p>指定的计算机的最终用户的时区。 一个字符串，用于指定计算机的时区设置时区。 最大长度为 256 个字符。 新时区可能会出现在将来的发行版。 若要添加对新时区的支持，必须输入确切的时区字符串。</p></td>
<td align="left"><p>有关时区的完整列表，请参阅<strong>HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time</strong>区域上运行 Windows® 7 的计算机的注册表中列出的值。 运行 Windows 7 的计算机上您可以使用 tzutil 命令行工具列出该计算机所在的时区。 默认情况下，Windows Server 2008 R2 上安装 tzutil 工具。</p>
<div class="alert">
<strong>警告</strong>  
<p>如果未指定时区，则使用默认时区值。 默认时区基于安装的语言和答案文件中指定的区域。 如果某个区域有多个时区，时间区域设置为该区域的默认时区。 默认时区，该地区的首都/主要城市的位置来指定。 例如，如果指定 en CA，则<strong>美国东部标准时间</strong>用作默认时区因为加拿大的首都渥太华，使用东部标准时间。 如果 EN-US 指定为<code>UserLocale</code>，默认为太平洋标准时间的时区的 Windows 安装。</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td align="left"><p></p></td>
<td align="left"><p>adjustForDST</p></td>
<td align="left"><p>指定是否为夏时制调整。 此设置仅当时才有效结合<code>timezone</code>和<code>hideTimeAndDate</code>设置，以指定最终用户的时间设置。</p></td>
<td align="left"><p>真或假。</p></td>
</tr>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p>hideRegionalSettings</p></td>
<td align="left"><p>如果未将该设置指定为<strong>True</strong>，则将显示区域设置页，即使该页的值的所有预先配置。</p></td>
<td align="left"><p>真或假。</p></td>
</tr>
<tr class="even">
<td align="left"><p></p></td>
<td align="left"><p>hideTimeAndDate</p></td>
<td align="left"><p>如果未将该设置指定为<strong>True</strong>，则将显示时间和日期页，即使该页的值的所有预先配置。</p></td>
<td align="left"><p>真或假。</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idhowtocustomizeoobespanspan-idhowtocustomizeoobespanspan-idhowtocustomizeoobespanhow-to-customize-oobe"></a><span id="How_to_Customize_OOBE"></span><span id="how_to_customize_oobe"></span><span id="HOW_TO_CUSTOMIZE_OOBE"></span>如何自定义 OOBE


**若要通过使用 Oobe.xml 自定义 OOBE**

1.  创建一个名为 Oobe.xml 文件并将该文件存储在 Windows\\System32\\Oobe\\信息。

2.  通过使用 XML 编辑器或文本编辑器，如记事本，相应的文件、 路径和内容更新 Oobe.xml。

3.  在 Windows 中保存您已更新的版本的 Oobe.xml\\System32\\Oobe\\信息，或所需的自定义设置适当的语言和区域设置特定文件夹中。

4.  测试 OOBE。

    **OOBE 测试**

    1.  在**开始**菜单上，指向**所有程序**，然后单击**附件**。

    2.  右键单击命令提示符的快捷方式，然后单击**以管理员身份运行**。 接受**用户帐户控制**对话框。

    3.  定位到\\Windows\\System32\\Sysprep

    4.  运行**sysprep /oobe**。

    5.  启动计算机。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[配置 Oobe.xml](configure-oobexml.md)

 

 






