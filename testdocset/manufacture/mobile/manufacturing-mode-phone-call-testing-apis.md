---
author: kpacquer
Description: "电话制造商使用这些 Api 时到制造模式引导设备测试电话功能。"
ms.assetid: 3a1bdf3e-e95d-4277-bad7-1063a138f473
MSHAttr: PreferredLib:/library/windows/hardware
title: "制造模式下测试 Api 的电话联络"
ms.openlocfilehash: 83dba8612cc51fb61cdfd1ac536b218319102613
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="manufacturing-mode-phone-call-testing-apis"></a>制造模式下测试 Api 的电话联络


\[某些信息与预发行产品，可能在商业上发布之前大幅度修改。 Microsoft 不做任何担保，明示或暗示的担保，此处提供的信息。\]

电话制造商使用这些 Api 时到制造模式引导设备测试电话功能。

## <a name="span-idinthissectionspanin-this-section"></a><span id="in_this_section"></span>在这一节


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">主题</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>[<strong>MfgPhoneDial</strong>](mfgphonedial.md)</p></td>
<td align="left"><p>导致电话才能拨打电话。</p></td>
</tr>
<tr class="even">
<td align="left"><p>[<strong>MfgPhoneEndCall</strong>](mfgphoneendcall.md)</p></td>
<td align="left"><p>结束电话呼叫。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[<strong>MfgPhoneGetSimLineCount</strong>](mfgphonegetsimlinecount.md)</p></td>
<td align="left"><p>获取当前检测到的 sim 卡插槽的数量。</p></td>
</tr>
<tr class="even">
<td align="left"><p>[<strong>MfgPhoneGetSimLineDetail</strong>](mfgphonegetsimlinedetail.md)</p></td>
<td align="left"><p>检索包含指定基于 sim 卡的电话线路的当前详细信息的结构。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[<strong>MfgPhoneGetSpeaker</strong>](mfgphonegetspeaker.md)</p></td>
<td align="left"><p>返回一个布尔值，该值指示是否使用电话扬声器，而不是电话听筒耳机。</p></td>
</tr>
<tr class="even">
<td align="left"><p>[<strong>MfgPhoneInitialize</strong>](mfgphoneinitialize.md)</p></td>
<td align="left"><p>初始化的电话系统和由 DLL 实现 API 的内部状态。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[<strong>MfgPhoneSetSimLineEventNotifyCallback</strong>](mfgphonesetsimlineeventnotifycallback.md)</p></td>
<td align="left"><p>基于回调的通知机制，用于接收基于 sim 卡的电话线路上的事件。</p></td>
</tr>
<tr class="even">
<td align="left"><p>[<strong>MfgPhoneSetSpeaker</strong>](mfgphonesetspeaker.md)</p></td>
<td align="left"><p>设置一个值，该值指示是否使用电话扬声器，而不是电话听筒耳机。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[<strong>MfgPhoneUninitialize</strong>](mfgphoneuninitialize.md)</p></td>
<td align="left"><p>取消初始化的电话系统和由 DLL 实现 API 的内部状态。</p></td>
</tr>
<tr class="even">
<td align="left"><p>[<strong>MFGPHONE_CALLSTATUS</strong>](mfgphone-callstatus.md)</p></td>
<td align="left"><p>提供调用的状态信息。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[<strong>MFGPHONE_LINESYSTEMTYPE</strong>](mfgphone-linesystemtype.md)</p></td>
<td align="left"><p>提供有关行系统的类型信息。</p></td>
</tr>
<tr class="even">
<td align="left"><p>[<strong>MFGPHONE_REGISTRATIONSTATE</strong>](mfgphone-registrationstate.md)</p></td>
<td align="left"><p>提供有关电话线路的状态信息。如何称呼？</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[<strong>MFGPHONE_SIMLINEDETAIL</strong>](mfgphone-simlinedetail.md)</p></td>
<td align="left"><p>提供有关特定基于 sim 卡的电话线路的信息。</p></td>
</tr>
<tr class="even">
<td align="left"><p>[<strong>MFGPHONE_SIMSTATE</strong>](mfgphone-simstate.md)</p></td>
<td align="left"><p>提供 sim 卡的状态信息。</p></td>
</tr>
</tbody>
</table>

 

 

 





