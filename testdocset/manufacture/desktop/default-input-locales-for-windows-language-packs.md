---
author: Justinha
Description: "输入配置文件 （或输入法区域设置） 描述了输入，输入与所输入的键盘的语言。 当第一个用户登录到 Windows 并标识其所在区域时，Windows 设置输入的配置文件。"
ms.assetid: 0bae00b5-dfcb-472e-a271-07ef62ad5fc5
MSHAttr: PreferredLib:/library/windows/hardware
title: "在 Windows 的默认输入配置文件 （输入法区域设置）"
ms.openlocfilehash: 33fbe882b810cc8d7fbc45ffd68e105cbcd5dfb8
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="default-input-profiles-input-locales-in-windows"></a>在 Windows 的默认输入配置文件 （输入法区域设置）


输入配置文件 （或输入法区域设置） 描述了输入，输入与所输入的键盘的语言。 当第一个用户登录到 Windows 并标识其所在区域时，Windows 设置输入的配置文件。

输入配置文件的[语言标识符](http://go.microsoft.com/fwlink/?LinkId=63026)和一个[键盘标识符](windows-language-pack-default-values.md)组成。 例如，阿拉伯语 （阿尔及利亚） 输入配置文件是 1401:00020401，其中 1401年语言十六进制标识符︰ 阿拉伯语 （阿尔及利亚） 和 00020401 是键盘十六进制标识符︰ 阿拉伯语 101。

当用户第一次确定时间和日期格式 （用户区域设置） 为阿尔及利亚、 Windows 设置这两个主要输入配置文件，和辅助输入配置文件︰ 法语键盘使用法语 （法国）。 辅助输入的模板可帮助用户通过键盘提供拉丁文字符集的任务的需要，如填写电子邮件地址。 一些字符集 （如中文 IME) 具有设置内置的字符。

使用触摸屏键盘时，Windows 使用任务如预期按键进行拼写检查、 断字和文字预测输入配置文件的语言组件。

当设置新设备，为您的用户，您可以使用 DISM 命令︰ /Set-InputLocale 或 /Set-AllIntl 来标识默认输入配置文件。 您可以选择由其语言和键盘对 (1401:00020401) 输入配置文件也可以使用一种语言\\地区标记接收该语言/地区的默认设置。

示例︰

``` syntax
Dism /image:C:\test\offline /Set-InputLocale:042d:0000040a
Dism /image:C:\test\offline /Set-InputLocale:0411:{03B5835F-F03C-411B-9CE2-AA23E1171E36}{A76C93D9-5523-4E90-AAFA-4DB112F9AC76}
Dism /image:C:\test\offline /Set-InputLocale:id-ID
Dism /image:C:\test\offline /Set-AllIntl:fr-FR
```

语言/区域性名称的列表，请参阅[可用语言包的 Windows](available-language-packs-for-windows.md)。

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">语言/区域</th>
<th align="left">主输入的配置文件 （对语言和键盘）</th>
<th align="left">辅助输入配置文件</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>南非荷兰语-南非</p></td>
<td align="left"><p>af-ZA︰ 美国-英语 (0436:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>阿尔巴尼亚语阿尔巴尼亚语</p></td>
<td align="left"><p>sq AL︰ 阿尔巴尼亚 (041 c: 0000041 c)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>阿尔萨斯语-法国</p></td>
<td align="left"><p>gsw FR︰ 法语 (0484:0000040 c)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>阿姆哈拉语-埃塞俄比亚</p></td>
<td align="left"><p>上午 ET︰ 阿姆哈拉语输入法 (045e: {E429B25A-E5D3-4D1F-9BE3-0C608477E3A1}{8F96574E-C86C-4bd6-9666-3F7327D4CBE8})</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>阿拉伯语-阿尔及利亚</p></td>
<td align="left"><p>ar DZ︰ 阿拉伯语 (102) AZERTY (1401:00020401)</p></td>
<td align="left"><p>FR-FR︰ 法语 (040 c: 0000040 c)</p></td>
</tr>
<tr class="even">
<td align="left"><p>阿拉伯语-巴林</p></td>
<td align="left"><p>ar BH︰ 阿拉伯语 (101) (3c 01:00000401)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>阿拉伯语-埃及</p></td>
<td align="left"><p>ar 如︰ 阿拉伯语 (101) (0c 01:00000401)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>阿拉伯语-伊拉克</p></td>
<td align="left"><p>ar IQ︰ 阿拉伯语 (101) (0801:00000401)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>阿拉伯语-约旦</p></td>
<td align="left"><p>ar JO︰ 阿拉伯语 (101) (2c 01:00000401)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>阿拉伯语-科威特</p></td>
<td align="left"><p>ar KW︰ 阿拉伯语 (101) (3401:00000401)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>阿拉伯语-黎巴嫩</p></td>
<td align="left"><p>ar 磅︰ 阿拉伯语 (101) (3001:00000401)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>阿拉伯语-利比亚</p></td>
<td align="left"><p>ar LY︰ 阿拉伯语 (101) (1001:00000401)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>阿拉伯语-摩洛哥</p></td>
<td align="left"><p>ar MA︰ 阿拉伯语 (102) AZERTY (1801:00020401)</p></td>
<td align="left"><p>FR-FR︰ 法语 (040 c: 0000040 c)</p></td>
</tr>
<tr class="even">
<td align="left"><p>阿拉伯语-阿曼</p></td>
<td align="left"><p>ar OM︰ 阿拉伯语 (101) (2001:00000401)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>阿拉伯语-卡塔尔</p></td>
<td align="left"><p>ar QA︰ 阿拉伯语 (101) (4001:00000401)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>阿拉伯语-沙特阿拉伯</p></td>
<td align="left"><p>ar SA︰ 阿拉伯语 (101) (0401:00000401)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>阿拉伯语-叙利亚</p></td>
<td align="left"><p>ar SY︰ 阿拉伯语 (101) (2801:00000401)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>阿拉伯语-突尼斯</p></td>
<td align="left"><p>ar-TN︰ 阿拉伯语 (102) AZERTY (1c 01:00020401)</p></td>
<td align="left"><p>FR-FR︰ 法语 (040 c: 0000040 c)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>阿拉伯语-阿拉伯联合酋长国</p></td>
<td align="left"><p>ar AE︰ 阿拉伯语 (101) (3801:00000401)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>阿拉伯语-也门</p></td>
<td align="left"><p>ar-YE︰ 阿拉伯语 (101) (2401:00000401)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>亚美尼亚语-亚美尼亚</p></td>
<td align="left"><p>hy 上午︰ 亚美尼亚文拼音 (042b:0002042b)</p></td>
<td align="left"><p>hy 上午︰ 亚美尼亚打字机 (042b:0003042b)</p>
<p>RU-RU︰ 俄语 (0419:00000419)</p></td>
</tr>
<tr class="even">
<td align="left"><p>阿萨姆语-印度</p></td>
<td align="left"><p>作为 IN︰ 阿萨姆语-Inscript (044d: 0000044 d)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>阿塞拜疆-阿塞拜疆 （西里尔文）</p></td>
<td align="left"><p>az-符号-AZ︰ 阿塞拜疆西里尔文 (c: 0000082 082c)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p>
<p>az-Latn AZ︰ 阿塞拜疆语拉丁语 (042 c: 0000042 c)</p></td>
</tr>
<tr class="even">
<td align="left"><p>阿塞拜疆-阿塞拜疆 （拉丁语系）</p></td>
<td align="left"><p>az-Latn AZ︰ 阿塞拜疆拉丁语 (042 c: 0000042 c)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p>
<p>az-符号-AZ︰ 阿塞拜疆语西里尔文 (c: 0000082 082c)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>孟加拉语 （孟加拉）</p></td>
<td align="left"><p>bn BD︰ 孟加拉语-孟加拉国 (0845:00000445)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>孟加拉语-印度 （孟加拉语）</p></td>
<td align="left"><p>bn IN︰ 孟加拉语的印度-INSCRIPT (0445:00020445)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>巴什基尔语-俄罗斯</p></td>
<td align="left"><p>ba RU︰ 巴什基尔语 (046 d: 0000046 d)</p></td>
<td align="left"><p>RU-RU 俄语 (0419:00000419)</p>
<p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>巴斯克语-巴斯克语</p></td>
<td align="left"><p>欧盟-ES︰ 西班牙语 (042d:0000040a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>白俄罗斯语-白俄罗斯</p></td>
<td align="left"><p>可通过︰ 白俄罗斯语 (0423:00000423)</p></td>
<td align="left"><p>RU-RU︰ 俄语 (0419:00000419)</p>
<p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>波斯尼亚语-波斯尼亚和黑塞哥维那 （西里尔文）</p></td>
<td align="left"><p>学士-符号-BA︰ 波斯尼亚语 （西里尔文） (201a:0000201a)</p></td>
<td align="left"><p>学士-Latn BA︰ 克罗地亚语 (141a:0000041a)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>波斯尼亚语-波斯尼亚和黑塞哥维那 （拉丁语系）</p></td>
<td align="left"><p>学士-Latn BA︰ 克罗地亚语 (141a:0000041a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Breton-法国</p></td>
<td align="left"><p>br-FR︰ 法语 (047e:0000040 c)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>保加利亚语-保加利亚</p></td>
<td align="left"><p>bg-BG︰ 保加利亚语 (0402:00030402)</p></td>
<td align="left"><p>EN-US︰ 美国-国际 (0409:00020409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>缅甸语-缅甸</p></td>
<td align="left"><p>我 MM︰ 缅甸 (0455:00010 c 00)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>加泰罗尼亚语-加泰罗尼亚语</p></td>
<td align="left"><p>ca-ES︰ 西班牙语 (0403:0000040a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>中央 Atlas 柏柏尔语，（拉丁）-阿尔及利亚</p></td>
<td align="left"><p>FR-FR︰ 法语 (040 c: 0000040 c)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>中央 Atlas 柏柏尔语，（拉丁）-阿尔及利亚</p></td>
<td align="left"><p>tzm-Latn DZ︰ 中央 Atlas 柏柏尔语 (085f:0000085f)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>中央 Atlas 柏柏尔语，（提夫纳语）-摩洛哥</p></td>
<td align="left"><p>tzm-Tfng-MA: (105f:0000105f)</p></td>
<td align="left"><p>FR-FR︰ 法语 (040 c: 0000040 c)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>中央库尔德 （伊拉克）</p></td>
<td align="left"><p>ku-阿拉伯-IQ: (0492:00000492)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>切罗基文 （切罗基文，美国）</p></td>
<td align="left"><p>chr Cher 美国︰ 切罗基文国 (045 c: 0000045 c)</p></td>
<td align="left"><p>切罗基文国拼音 (045 c: 0001045 c)</p>
<p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>中文-中国</p></td>
<td align="left"><p>ZH-CN︰ 微软拼音的快速简单 (0804年: {81D4E9C9-1D3B-41BC-9E6C-4B40BF79E35E}{FA550B04-5AD7-411f-A5AC-CA038EC515D7})</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>中文-中国台湾地区</p></td>
<td align="left"><p>ZH-TW︰ 新拼音的中文 （繁体）-(0404年: {B115690A-EA02-48D5-A231-E3578D2FDF80}{B2F9C502-1742-11D4-9790-0080C882687E})</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>科西嘉语-法国</p></td>
<td align="left"><p>co-FR︰ 法语 (0483:0000040 c)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>克罗地亚语-波斯尼亚与黑塞哥维那</p></td>
<td align="left"><p>hr BA︰ 克罗地亚语 (101a:0000041a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>克罗地亚语-克罗地亚</p></td>
<td align="left"><p>人力资源人力资源︰ 克罗地亚语 (041a:0000041a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>捷克语-捷克共和国</p></td>
<td align="left"><p>cs CZ︰ 捷克语 (0405:00000405)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>丹麦语-丹麦</p></td>
<td align="left"><p>DA-DK︰ 丹麦语 (0406:00000406)</p></td>
<td align="left"><p>EN-US︰ 丹麦语 (0409:00000406)</p></td>
</tr>
<tr class="even">
<td align="left"><p>达里语-阿富汗</p></td>
<td align="left"><p>prs AF︰ 波斯语 （标准） (048 c: 00050429)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>马尔代夫语-马尔代夫</p></td>
<td align="left"><p>dv MV︰ 迪维希语拼音 (0465:00000465)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>荷兰语-比利时</p></td>
<td align="left"><p>nl-是︰ 比利时 （.） (0813:00000813)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>荷兰语-荷兰</p></td>
<td align="left"><p>nl NL︰ 美国-国际 (0413:00020409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>不丹语</p></td>
<td align="left"><p>dz BT: 0c 51:00000 C 51; 0409: 00000409</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>英语-澳大利亚</p></td>
<td align="left"><p>en AU︰ 美国-英语 (0c 09:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>英语-伯利兹</p></td>
<td align="left"><p>en BZ︰ 美国-英语 (2809:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>英语-加拿大</p></td>
<td align="left"><p>en-CA︰ 美国-英语 (1009:00000409)</p></td>
<td align="left"><p>en-CA︰ 加拿大多语言标准 (1009:00011009)</p></td>
</tr>
<tr class="even">
<td align="left"><p>英语-加勒比</p></td>
<td align="left"><p>en-029︰ 美国-英语 (2409:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>英语-印度</p></td>
<td align="left"><p>en IN︰ 印度 (4009:00004009)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>英语-爱尔兰</p></td>
<td align="left"><p>en IE︰ 爱尔兰语 (1809:00001809)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>英语-牙买加</p></td>
<td align="left"><p>en JM︰ 美国-英语 (2009:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>英语-马来西亚</p></td>
<td align="left"><p>en 我︰ 美国-英语 (4409:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>英语-新西兰</p></td>
<td align="left"><p>en NZ︰ 美国-英语 (1409:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>英语-菲律宾</p></td>
<td align="left"><p>en PH︰ 美国-英语 (3409:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>英语-新加坡</p></td>
<td align="left"><p>en-SG︰ 美国-英语 (4809:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>英语-南非</p></td>
<td align="left"><p>en-ZA︰ 美国-英语 (1 c 09:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>英语-特立尼达岛</p></td>
<td align="left"><p>en TT︰ 美国-英语 (2c 09:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>英语-英国</p></td>
<td align="left"><p>EN-GB︰ 英国 (0809:00000809)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>英语-美国</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>英语-津巴布韦</p></td>
<td align="left"><p>en-ZW︰ 美国-英语 (3009:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>爱沙尼亚语-爱沙尼亚</p></td>
<td align="left"><p>et EE︰ 爱沙尼亚语 (0425:00000425)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>法罗语-法罗群岛</p></td>
<td align="left"><p>fo FO︰ 丹麦语 (0438:00000406)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>菲律宾语-菲律宾</p></td>
<td align="left"><p>文件 PH︰ 美国-英语 (0464:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>芬兰语-芬兰</p></td>
<td align="left"><p>fi FI︰ 芬兰语 (040b:0000040b)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>法语-比利时</p></td>
<td align="left"><p>fr 的是︰ 比利时法语 (c: 0000080 080c)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>法语-加拿大</p></td>
<td align="left"><p>fr CA︰ 加拿大多语言标准 (0c0c:00011009)</p></td>
<td align="left"><p>en-CA︰ 加拿大多语言标准 (1009:00011009)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>法语-法国</p></td>
<td align="left"><p>FR-FR︰ 法语 (040 c: 0000040 c)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>法语-卢森堡</p></td>
<td align="left"><p>fr LU︰ 瑞士法语 (140 c: 0000100 C)</p></td>
<td align="left"><p>fr LU︰ 法语 (140 c: 0000040 c)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>法语-摩纳哥</p></td>
<td align="left"><p>fr MC︰ 法语 (180 c: 0000040 c)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>法语-瑞士</p></td>
<td align="left"><p>fr CH︰ 瑞士法语 (100 c: 0000100 c)</p></td>
<td align="left"><p>de CH︰ 瑞士德语 (0807:00000807)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>荷兰弗里斯兰语</p></td>
<td align="left"><p>fy-NL︰ 美国-国际 (0462:00020409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Fulah （拉丁语，塞内加尔）</p></td>
<td align="left"><p>ff-Latn SN︰ 沃洛夫语 (0867:00000488)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>加利西亚语-加利西亚语</p></td>
<td align="left"><p>gl-ES︰ 西班牙语 (0456:0000040a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>格鲁吉亚语-格鲁吉亚</p></td>
<td align="left"><p>ka-GE︰ 格鲁吉亚语 （标准键盘） (0437:00010437)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>德语-奥地利</p></td>
<td align="left"><p>de AT︰ 德语 (0c 07:00000407)</p></td>
<td align="left"><p>de AT: （德语)</p></td>
</tr>
<tr class="even">
<td align="left"><p>德语-德国</p></td>
<td align="left"><p>DE-DE︰ 德语 (0407:00000407)</p></td>
<td align="left"><p>DE-DE: （德语)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>德语-列支敦士登</p></td>
<td align="left"><p>de LI︰ 瑞士德语 (1407:00000807)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>德语-卢森堡</p></td>
<td align="left"><p>de LU︰ 德语 (1007:00000407)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>德语-瑞士</p></td>
<td align="left"><p>de CH︰ 瑞士德语 (0807:00000807)</p></td>
<td align="left"><p>fr CH︰ 瑞士法语 (100C: 0000100 C)</p></td>
</tr>
<tr class="even">
<td align="left"><p>希腊语-希腊</p></td>
<td align="left"><p>el-GR︰ 希腊文 (0408:00000408)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>格陵兰语-格陵兰</p></td>
<td align="left"><p>kl-GL︰ 丹麦语 (046f:00000406)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>瓜拉尼-巴拉圭</p></td>
<td align="left"><p>gn PY︰ 瓜拉尼 (0474:00000474)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>古吉拉特语-印度 （古吉拉特语字符集）</p></td>
<td align="left"><p>gu IN︰ 古吉拉特文 (0447:00000447)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>豪撒语 （拉丁语系）-尼日利亚</p></td>
<td align="left"><p>ha-Latn-NG︰ 豪撒语 (0468:00000468)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>夏威夷语-美国</p></td>
<td align="left"><p>haw 美国: (0475:00000475)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>希伯来语-以色列</p></td>
<td align="left"><p>他 IL: (040 d: 0002040 d)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>北印度语-印度</p></td>
<td align="left"><p>你在︰ 印度传统 (0439:00010439)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>匈牙利语-匈牙利</p></td>
<td align="left"><p>hu HU︰ 匈牙利语 (040e:0000040e)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>冰岛语-冰岛</p></td>
<td align="left"><p>是的是︰ 冰岛语 (040f:0000040f)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>伊博语-尼日利亚</p></td>
<td align="left"><p>ig NG︰ 伊博语 (0470:00000470)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>斯语萨米语-芬兰</p></td>
<td align="left"><p>smn FI︰ 芬兰萨米 (243b:0001083b)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>印度尼西亚语-印度尼西亚</p></td>
<td align="left"><p>标识符标识符︰ 美国-英语 (0421:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>因纽特语 （拉丁语系）-加拿大</p></td>
<td align="left"><p>iu-Latn CA︰ 因纽特语-拉丁语 (085 d: 0000085 d)</p></td>
<td align="left"><p>en-CA︰ 美国-英语 (1009:00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>因纽特语 （音节）-加拿大</p></td>
<td align="left"><p>iu 罐 CA︰ 因纽特语-Naqittaut (045 d: 0001045 d)</p></td>
<td align="left"><p>en-CA︰ 美国-英语 (1009:00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>爱尔兰的爱尔兰</p></td>
<td align="left"><p>ga IE︰ 爱尔兰 (083 c: 00001809)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>索萨语 / 南部非洲班图语</p></td>
<td align="left"><p>xh-ZA︰ 美国-英语 (0434:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>祖鲁语 / 祖鲁-南非</p></td>
<td align="left"><p>zu ZA︰ 美国-英语 (0435:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>意大利语-意大利</p></td>
<td align="left"><p>it IT︰ 意大利语 (0410:00000410)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>意大利语-瑞士</p></td>
<td align="left"><p>it 频道︰ 瑞士法语 (0810:0000100 c)</p></td>
<td align="left"><p>it 频道︰ 意大利语 (0810:00000410)</p></td>
</tr>
<tr class="even">
<td align="left"><p>日语-日本</p></td>
<td align="left"><p>JA-JP: Microsoft 输入法 (0411年: {03B5835F-F03C-411B-9CE2-AA23E1171E36}{A76C93D9-5523-4E90-AAFA-4DB112F9AC76})</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Javanese （拉丁）-印度尼西亚</p></td>
<td align="left"><p>jv Latn ID︰ 美国 (0c 00:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>卡纳达语-印度 （埃纳）</p></td>
<td align="left"><p>kn IN︰ 卡纳达文 (044b:0000044b)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>哈萨克语-哈萨克斯坦</p></td>
<td align="left"><p>kk KZ︰ 哈萨克语 (043f:0000043f)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>高棉语-柬埔寨</p></td>
<td align="left"><p>km KH︰ 高棉语 (0453:00000453)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>基切语-危地马拉</p></td>
<td align="left"><p>qut GT︰ 拉丁美洲 (0486:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>卢旺达语-Rwanda</p></td>
<td align="left"><p>rw-RW︰ 美国-英语 (0487:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>贡根语-印度</p></td>
<td align="left"><p>kok IN︰ 梵文 INSCRIPT (0457:00000439)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>朝鲜语 (扩展 Wansung)-韩国</p></td>
<td align="left"><p>KO-KR: Microsoft 输入法 (0412年: {A028AE76-01B1-46C2-99C4-ACD9858AE02F}{B5FE1F02-D5F2-4445-9C03-C568F23C99A1})</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>吉尔吉斯语-吉尔吉斯斯坦</p></td>
<td align="left"><p>肯塔基州公斤︰ 吉尔吉斯西里尔文 (0440:00000440)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>老挝语-老挝人民民主共和国</p></td>
<td align="left"><p>lo LA︰ 老挝语 (0454:00000454)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>拉脱维亚语-旧式</p></td>
<td align="left"><p>lv LV︰ 拉脱维亚语 （标准键盘） (0426:00010426)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>拉脱维亚语-标准</p></td>
<td align="left"><p>lv LV︰ 拉脱维亚语 （标准） (0426:00020426)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>立陶宛语-立陶宛</p></td>
<td align="left"><p>lt LT︰ 立陶宛语 (0427:00010427)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>下索布语-德国</p></td>
<td align="left"><p>dsb DE︰ 标准索布语 (082e:0002042e)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>律勒欧萨摩斯语-挪威</p></td>
<td align="left"><p>smj 否︰ 挪威萨米 (103b:0000043b)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>律勒欧萨摩斯语-瑞典</p></td>
<td align="left"><p>smj SE︰ 瑞典萨米 (143b:0000083b)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>卢森堡语-卢森堡</p></td>
<td align="left"><p>lb LU︰ 卢森堡语 (046e:0000046e)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>马其顿语-F.Y.R.O.M</p></td>
<td align="left"><p>mk MK︰ 马其顿共和国 （前南斯拉夫马其顿共和国） 的标准 (042f:0001042f)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>马来语-文莱</p></td>
<td align="left"><p>ms-BN︰ 美国-英语 (083e:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>马来语-马来西亚</p></td>
<td align="left"><p>我 ms︰ 美国-英语 (043e:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>马拉雅拉姆语-印度 （马拉雅拉姆语字符集）</p></td>
<td align="left"><p>ml IN︰ 马拉雅拉姆语 (044 c: 0000044 c)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>马耳他-马耳他</p></td>
<td align="left"><p>mt-MT︰ 马耳他 47-键 (043a:0000043a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>毛利语-新西兰</p></td>
<td align="left"><p>mi NZ︰ 毛利语 (0481:00000481)</p></td>
<td align="left"><p>en NZ︰ 美国-英语 (1409:00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Mapudungun-智利</p></td>
<td align="left"><p>arn CL︰ 拉丁美洲 (047a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>马拉地语-印度</p></td>
<td align="left"><p>mr IN︰ 马拉地语 (044e:0000044e)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>莫霍克语-莫霍克语</p></td>
<td align="left"><p>moh CA︰ 美国-英语 (047 c: 00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>蒙古语 （西里尔文）-蒙古</p></td>
<td align="left"><p>明尼苏达州明尼苏达州︰ 外蒙古西里尔文 (0450:00000450)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>蒙古语 （蒙古语）-蒙古</p></td>
<td align="left"><p>明尼苏达州明尼苏达州-旺: 传统蒙古语 （标准） (0c 50:00010850)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>蒙古语 （蒙古语 – 中国 – 传统）</p></td>
<td align="left"><p>明尼苏达州-旺-CN︰ 蒙古语 （蒙古语脚本） (0850:00000850)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>蒙古语 （蒙古语 – 中国 – 标准）</p></td>
<td align="left"><p>明尼苏达州-旺-CN︰ 蒙古语 （蒙古语脚本） (0850:00010850)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>N'ko-几内亚</p></td>
<td align="left"><p>nqo-GN: N'Ko (0c 00: 00090C 00)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>尼泊尔语-尼泊尔联邦民主共和国</p></td>
<td align="left"><p>内布拉斯加州-NP︰ 尼泊尔语 (0461:00000461)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>北萨米语-芬兰</p></td>
<td align="left"><p>se FI︰ 芬兰萨米 (0c3b:0001083b)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>北萨米语-挪威</p></td>
<td align="left"><p>se 否︰ 挪威萨米 (043b:0000043b)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>北萨米语-瑞典</p></td>
<td align="left"><p>se SE︰ 瑞典萨米 (083b:0000083b)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>挪威语-挪威 （博克马尔语）</p></td>
<td align="left"><p>nb 否︰ 挪威语 (0414:00000414)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>挪威语-挪威 （尼诺斯克语）</p></td>
<td align="left"><p>nn 否︰ 挪威语 (0814:00000414)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Occitan-法国</p></td>
<td align="left"><p>oc-FR︰ 法语 (0482:0000040 c)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Odia-印度 （Odia 脚本）</p></td>
<td align="left"><p>或在︰ Odia (0448:00000448)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>普什图语-阿富汗</p></td>
<td align="left"><p>ps AF︰ 普什图语 （阿富汗） (0463:00000463)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>波斯语</p></td>
<td align="left"><p>fa 红外线 （ir): 中央库尔德 (0429:00000429)</p></td>
<td align="left"><p>FA-IR︰ 波斯语 （标准） (0429:00050429)</p>
<p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>波兰语-波兰</p></td>
<td align="left"><p>pl PL︰ 波兰语 （程序员） (0415:00000415)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>葡萄牙-巴西</p></td>
<td align="left"><p>PT-BR︰ 葡萄牙语 (巴西语 ABNT) (0416:00000416)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>葡萄牙-葡萄牙</p></td>
<td align="left"><p>pt PT︰ 葡萄牙语 (0816:00000816)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>旁遮普语-印度 （果鲁穆）</p></td>
<td align="left"><p>pa IN︰ 旁遮普语 (0446:00000446)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>旁遮普语 （巴基斯坦伊斯兰共和国）</p></td>
<td align="left"><p>pa-阿拉伯的 PK︰ 乌尔都语 (0846:00000420)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>克丘亚语-玻利维亚</p></td>
<td align="left"><p>quz BO︰ 拉丁美洲 (046b:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>克丘亚语-厄瓜多尔</p></td>
<td align="left"><p>quz-EC︰ 拉丁美洲 (086b:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>克丘亚语-秘鲁</p></td>
<td align="left"><p>quz PE︰ 拉丁美洲 (0c6b:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>罗马尼亚语-罗马尼亚</p></td>
<td align="left"><p>ro RO︰ 罗马尼亚语 （标准） (0418:00010418)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>瑞士罗曼什语</p></td>
<td align="left"><p>rm-CH︰ 瑞士德语 (0417:00000807)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>俄语的俄罗斯</p></td>
<td align="left"><p>RU-RU︰ 俄语 (0419:00000419)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Sakha-俄罗斯</p></td>
<td align="left"><p>sah RU: Sakha (0485:00000485)</p></td>
<td align="left"><p>RU-RU 俄语 (0419:00000419)</p>
<p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>梵语-印度</p></td>
<td align="left"><p>sa IN︰ 梵文 INSCRIPT (044f:00000439)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>苏格兰盖尔语-英国</p></td>
<td align="left"><p>gd GB︰ 盖尔语 (0491:00011809)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>塞尔维亚语-波斯尼亚和黑塞哥维那 （西里尔文）</p></td>
<td align="left"><p>sr-符号-BA︰ 塞尔维亚语 （西里尔文） (1c1a:00000c1a)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>塞尔维亚语-波斯尼亚和黑塞哥维那 （拉丁语系）</p></td>
<td align="left"><p>sr-Latn BA︰ 塞尔维亚语 （拉丁） (181a:0000081a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>塞尔维亚语-黑山 （西里尔文）</p></td>
<td align="left"><p>sr-符号-ME︰ 塞尔维亚语 （西里尔文） (301a:00000c1a)</p></td>
<td align="left"><p>EN-US︰ 美国-国际 (0409:00020409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>塞尔维亚语-黑山 （拉丁语系）</p></td>
<td align="left"><p>sr-Latn ME︰ 塞尔维亚语 （拉丁） (2c1a:0000081a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>塞尔维亚语-塞尔维亚 （西里尔文）</p></td>
<td align="left"><p>sr-符号-RS︰ 塞尔维亚语 （西里尔文） (281a:00000c1a)</p></td>
<td align="left"><p>EN-US︰ 美国-国际 (0409:00020409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>塞尔维亚语-塞尔维亚 （拉丁语系）</p></td>
<td align="left"><p>sr-Latn RS︰ 塞尔维亚语 （拉丁） (241a:0000081a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>塞尔维亚语-塞尔维亚共和国和黑山共和国 （早期） （西里尔文）</p></td>
<td align="left"><p>sr-符号-CS︰ 塞尔维亚语 （西里尔文） (0c1a:00000c1a)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>塞尔维亚语-塞尔维亚共和国和黑山共和国 （早期） （拉丁语系）</p></td>
<td align="left"><p>sr-Latn CS︰ 塞尔维亚语 （拉丁） (081a:0000081a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>巴索托语 / 北梭托语-南非</p></td>
<td align="left"><p>nso ZA︰ 巴索托语 (046 c: 0000046 c)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>茨瓦纳语 / 茨瓦纳语-博茨瓦纳</p></td>
<td align="left"><p>tn BW︰ 茨瓦纳语 (0832:00000432)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>茨瓦纳语 / 南非茨瓦纳</p></td>
<td align="left"><p>tn-ZA︰ 茨瓦纳语 (0432:00000432)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Shona-津巴布韦</p></td>
<td align="left"><p>sn-Latn ZW︰ 美国 (0c 00:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>信德语 （巴基斯坦伊斯兰共和国）</p></td>
<td align="left"><p>sd-阿拉伯的 PK︰ 乌尔都语 (0859:00000420)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>僧伽罗语-斯里兰卡</p></td>
<td align="left"><p>si LK︰ 僧伽罗语 (045b:0000045b)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>斯科特萨米语-芬兰</p></td>
<td align="left"><p>sms FI︰ 芬兰萨米 (203b:0001083b)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>斯洛伐克语-斯洛伐克</p></td>
<td align="left"><p>sk-SK︰ 斯洛伐克语 (041b:0000041b)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>斯洛伐克语-斯洛伐克</p></td>
<td align="left"><p>sl SI︰ 斯洛文尼亚语 (0424:00000424)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>南萨米语-挪威</p></td>
<td align="left"><p>sma 否︰ 挪威萨米 (183b:0000043b)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>南萨米语-瑞典</p></td>
<td align="left"><p>sma SE︰ 瑞典萨米 (1c3b:0000083b)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>西班牙语-阿根廷</p></td>
<td align="left"><p>es AR︰ 拉丁美洲 (2c0a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>西班牙语-委内瑞拉玻利维亚共和国</p></td>
<td align="left"><p>es VE︰ 拉丁美洲 (200a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>西班牙语-玻利维亚</p></td>
<td align="left"><p>es BO︰ 拉丁美洲 (400a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>西班牙语-智利</p></td>
<td align="left"><p>es-CL︰ 拉丁美洲 (340a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>西班牙语-哥伦比亚</p></td>
<td align="left"><p>es CO︰ 拉丁美洲 (240a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>西班牙语-哥斯达黎加</p></td>
<td align="left"><p>es-CR︰ 拉丁美洲 (140a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>西班牙语-多米尼加共和国</p></td>
<td align="left"><p>es DO︰ 拉丁美洲 (1c0a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>西班牙语-厄瓜多尔</p></td>
<td align="left"><p>es EC︰ 拉丁美洲 (300a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>西班牙语-萨尔瓦多</p></td>
<td align="left"><p>es SV︰ 拉丁美洲 (440a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>西班牙语-危地马拉</p></td>
<td align="left"><p>es-GT︰ 拉丁美洲 (100a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>西班牙语-洪都拉斯</p></td>
<td align="left"><p>es HN︰ 拉丁美洲 (480a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>西班牙语-墨西哥</p></td>
<td align="left"><p>ES-MX︰ 拉丁美洲 (080a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>西班牙语-尼加拉瓜</p></td>
<td align="left"><p>es NI︰ 拉丁美洲 (4c0a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>西班牙语-巴拿马</p></td>
<td align="left"><p>es PA︰ 拉丁美洲 (180a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>西班牙语-巴拉圭</p></td>
<td align="left"><p>es PY︰ 拉丁美洲 (3c0a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>西班牙语-秘鲁</p></td>
<td align="left"><p>es PE︰ 拉丁美洲 (280a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>西班牙语-波多黎各自由联邦</p></td>
<td align="left"><p>es 公关︰ 拉丁美洲 (500a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>西班牙语-西班牙 （国际排序）</p></td>
<td align="left"><p>es-ES︰ 西班牙语 (0c0a:0000040a)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>西班牙语-西班牙 （传统风格）</p></td>
<td align="left"><p>es ES_tradnl︰ 西班牙语 (040a:0000040a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>西班牙语-美国</p></td>
<td align="left"><p>es 美国︰ 拉丁美洲 (540a:0000080a)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>西班牙语-乌拉圭</p></td>
<td align="left"><p>es UY︰ 拉丁美洲 (380a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>标准摩洛哥塔马赛特文-摩洛哥</p></td>
<td align="left"><p>zgh-Tfng-MA︰ 提夫纳语 （基本） (0c 00: 0000105F)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>斯瓦希里语-肯尼亚</p></td>
<td align="left"><p>sw KE︰ 美国-英语 (0441:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>瑞典语的芬兰</p></td>
<td align="left"><p>sv FI︰ 瑞典语 (081d: 0000041 d)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>瑞典语的瑞典</p></td>
<td align="left"><p>sv SE︰ 瑞典语 (041d: 0000041 d)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>叙利亚语-叙利亚</p></td>
<td align="left"><p>syr SY︰ 叙利亚文 (045a:0000045a)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>塔吉克语-塔吉克斯坦</p></td>
<td align="left"><p>tg-符号-TJ︰ 塔吉克语 (0428:00000428)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>泰米尔语-印度</p></td>
<td align="left"><p>选项卡中︰ 泰米尔语 (0449:00000449)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>泰米尔语-斯里兰卡</p></td>
<td align="left"><p>选项卡 LK︰ 泰米尔语 (0849:00000449)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>鞑靼语 – 俄罗斯 （传统）</p></td>
<td align="left"><p>tt RU︰ 鞑靼语 (0444:00000444)</p></td>
<td align="left"><p>RU-RU︰ 俄语 (0419:00000419)</p>
<p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>鞑靼语 – 俄罗斯 （标准）</p></td>
<td align="left"><p>tt RU︰ 鞑靼语 (0444:00010444)</p></td>
<td align="left"><p>RU-RU︰ 俄语 (0419:00000419)</p>
<p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>泰卢固语-印度 （泰卢固语字符集）</p></td>
<td align="left"><p>te IN︰ 泰卢固语 (044a:0000044a)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>泰国-泰国</p></td>
<td align="left"><p>TH-TH︰ 泰国 Kedmanee (041e:0000041e)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>西藏语-中国</p></td>
<td align="left"><p>bo CN︰ 藏语 （中国） (0451:00010451)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Tigrinya （厄立特里亚）</p></td>
<td align="left"><p>ti-ET: Tigrinya 输入法 (0473年: {E429B25A-E5D3-4D1F-9BE3-0C608477E3A1}{3CAB88B7-CC3E-46A6-9765-B772AD7761FF})</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Tigrinya （埃塞俄比亚）</p></td>
<td align="left"><p>ti-ET: Tigrinya 输入法 (0473年: {E429B25A-E5D3-4D1F-9BE3-0C608477E3A1}{3CAB88B7-CC3E-46A6-9765-B772AD7761FF})</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>土耳其语-土耳其</p></td>
<td align="left"><p>异︰ 土耳其语 Q (041f:0000041f)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>土库曼语-土库曼斯坦</p></td>
<td align="left"><p>tk TM︰ 土库曼语 (0442:00000442)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>乌克兰语乌克兰语</p></td>
<td align="left"><p>英国-UA︰ 乌克兰语 （增强型） (0422:00020422)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>上索布语-德国</p></td>
<td align="left"><p>hsb DE︰ 标准索布语 (042e:0002042e)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>乌尔都语-印度</p></td>
<td align="left"><p>您在︰ 乌尔都语 (0820:00000420)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>乌尔都语 （巴基斯坦伊斯兰共和国）</p></td>
<td align="left"><p>您 PK︰ 乌尔都语 (0420:00000420)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>维吾尔语-中国</p></td>
<td align="left"><p>ug-CN︰ 维吾尔语 (0480:00010480)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>乌兹别克语-乌兹别克斯坦 （西里尔文）</p></td>
<td align="left"><p>uz-符号-UZ︰ 乌兹别克西里尔文 (0843:00000843)</p></td>
<td align="left"><p>uz-Latn UZ︰ 美国-英语 (0443:00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>乌兹别克语-乌兹别克斯坦 （拉丁语系）</p></td>
<td align="left"><p>uz-Latn UZ︰ 美国-英语 (0443:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Valencian-Valencia</p></td>
<td align="left"><p>ca-ES valencia︰ 西班牙语 (0803:0000040a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>越南语-越南</p></td>
<td align="left"><p>vi-VN︰ 越南语 (042a:0000042a)</p></td>
<td align="left"><p>EN-US︰ 美国-英语 (0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>威尔士语-英国</p></td>
<td align="left"><p>cy GB︰ 英国扩展 (0452:00000452)</p></td>
<td align="left"><p>EN-GB︰ 英国 (0809:00000809)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>沃洛夫语-塞内加尔</p></td>
<td align="left"><p>wo-SN︰ 沃洛夫语 (0488:00000488)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>彝语-中国</p></td>
<td align="left"><p>ii-CN︰ 彝文输入 Method(0478:{E429B25A-E5D3-4D1F-9BE3-0C608477E3A1}{409C8376-007B-4357-AE8E-26316EE3FB0D})</p></td>
<td align="left"><p>ZH-CN︰ 微软拼音的快速简单 (0804年: {81D4E9C9-1D3B-41BC-9E6C-4B40BF79E35E}{FA550B04-5AD7-411f-A5AC-CA038EC515D7})</p></td>
</tr>
<tr class="odd">
<td align="left"><p>约鲁巴语-尼日利亚</p></td>
<td align="left"><p>yo NG︰ 约鲁巴语 (046a:0000046a)</p></td>
<td align="left"><p></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[默认时区](default-time-zones.md)

[将语言包添加到 Windows](add-language-packs-to-windows.md)

[可用语言包的 Windows](available-language-packs-for-windows.md)

[对于 Windows 键盘标识符](windows-language-pack-default-values.md)

[DISM 语言和国际服务命令行选项](dism-languages-and-international-servicing-command-line-options.md)

 

 






