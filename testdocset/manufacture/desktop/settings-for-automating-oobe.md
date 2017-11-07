---
author: Justinha
Description: "用于自动执行 OOBE 设置"
ms.assetid: b7d71c0e-6e91-4409-a184-d76d744b386b
MSHAttr: PreferredLib:/library/windows/hardware
title: "用于自动执行 OOBE 设置"
ms.openlocfilehash: 8cb684b15d627fc0f931d59b0d00a878689631b0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="settings-for-automating-oobe"></a>用于自动执行 OOBE 设置


您可以阻止用户界面 (UI) 页面的部分或全部出现在 Windows 的全新体验 (OOBE)。

## <a name="span-idautomatingoobespanspan-idautomatingoobespanspan-idautomatingoobespanautomating-oobe"></a><span id="Automating_OOBE"></span><span id="automating_oobe"></span><span id="AUTOMATING_OOBE"></span>自动执行 OOBE


要自动完成 OOBE，请到无人参与安装答案文件添加以下设置︰

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">设置</th>
<th align="left">配置阶段</th>
<th align="left">说明</th>
<th align="left">适用于</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Microsoft Windows 国际核设置︰ [InputLocale](http://go.microsoft.com/fwlink/?LinkId=224435)、 [SystemLocale](http://go.microsoft.com/fwlink/?LinkId=224436)、 [UILanguage](http://go.microsoft.com/fwlink/?LinkId=224437)和[UserLocale](http://go.microsoft.com/fwlink/?LinkId=224438)。</p></td>
<td align="left"><p><strong>oobeSystem</strong></p></td>
<td align="left"><p>指定 Windows 安装的特定于区域的默认设置。</p></td>
<td align="left"><p>桌面版本 （家庭、 Pro、 企业和教育） 和 Windows 服务器 2016年技术预览窗口 10 </p></td>
</tr>
<tr class="even">
<td align="left"><p>Microsoft Windows 外壳程序安装 |[计算机名](http://go.microsoft.com/fwlink/p/?linkid=224440)</p></td>
<td align="left"><p><strong>专门负责</strong></p></td>
<td align="left"><p>指定要应用于 Windows 安装的计算机的名称。</p>
<p>如果计算机名设置为一个星号 （*），或者为空字符串，则将生成随机的计算机名。</p></td>
<td align="left"><p>桌面版和 Windows 服务器 2016年技术预览窗口 10 </p></td>
</tr>
<tr class="odd">
<td align="left"><p>Microsoft Windows 外壳程序安装 |[用户帐户](http://go.microsoft.com/fwlink/?LinkId=224439)︰ 添加帐户和密码。</p></td>
<td align="left"><p><strong>oobeSystem</strong></p></td>
<td align="left"><p>指定的用户帐户创建的 Windows 安装上。</p>
<p>该帐户可以是用户帐户、 域帐户，或者默认的管理员帐户。</p>
<p>虽然您必须输入密码，密码可能为空。 若要输入一个空密码，Windows sim 卡中，右键单击<strong>值</strong>，然后选择<strong>写入空字符串</strong>。</p></td>
<td align="left"><p>桌面版和 Windows 服务器 2016年技术预览窗口 10 </p></td>
</tr>
<tr class="even">
<td align="left"><p>Microsoft Windows 外壳程序安装 |OOBE |（[HideEULAPage](http://go.microsoft.com/fwlink/?LinkId=224445)、 [HideOEMRegistrationScreen](http://go.microsoft.com/fwlink/?LinkId=252784)、 [HideOnlineAccountScreens](http://go.microsoft.com/fwlink/?LinkId=252785)，和[HideWirelessSetupInOOBE](http://go.microsoft.com/fwlink/?LinkId=252786)）</p></td>
<td align="left"><p><strong>oobeSystem</strong></p></td>
<td align="left"><p>指定某些 OOBE 屏幕的行为。</p></td>
<td align="left"><p>桌面版和 Windows 服务器 2016年技术预览窗口 10 </p></td>
</tr>
<tr class="odd">
<td align="left"><p>Microsoft Windows 外壳程序安装 |OOBE |[HideLocalAccountScreen](http://go.microsoft.com/fwlink/?LinkId=252787)</p></td>
<td align="left"><p><strong>oobeSystem</strong></p></td>
<td align="left"><p>指定最终用户是否必须设置管理员密码屏幕在 OOBE 期间出现。</p></td>
<td align="left"><p>Windows 服务器 2016年技术只可预览</p></td>
</tr>
<tr class="even">
<td align="left"><p>Microsoft Windows 外壳程序安装 |OOBE |[ProtectYourPC](http://go.microsoft.com/fwlink/?LinkId=224441)</p></td>
<td align="left"><p><strong>oobeSystem</strong></p></td>
<td align="left"><p>指定是否使用快速设置，如将数据发送到 Microsoft，让 Windows 和应用程序请求用户的本地化，并打开防范恶意 web 内容配置设备。</p></td>
<td align="left"><p>桌面版和 Windows 服务器 2016年技术预览窗口 10 </p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[自动执行 Windows 安装程序](automate-windows-setup.md)

 

 






