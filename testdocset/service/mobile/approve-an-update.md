---
author: kpacquer
Description: "批准更新"
ms.assetid: 766c5961-4291-4547-a3a4-8ce98d3525e5
MSHAttr: PreferredLib:/library/windows/hardware
title: "批准更新"
ms.openlocfilehash: e32f78ce6ca1236c7a9ab29915c5eea27a761740
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="approve-an-update"></a>批准更新


提交更新后，OEM 和移动操作员 (MO) 批准它，或取消它。

## <a name="span-idprerequisitestoapproveanupdatespanspan-idprerequisitestoapproveanupdatespanspan-idprerequisitestoapproveanupdatespanprerequisites-to-approve-an-update"></a><span id="Prerequisites_to_approve_an_update"></span><span id="prerequisites_to_approve_an_update"></span><span id="PREREQUISITES_TO_APPROVE_AN_UPDATE"></span>批准的更新的先决条件


请参阅[提交更新](submit-an-update.md)。

## <a name="span-idapprovingrfusspanspan-idapprovingrfusspanspan-idapprovingrfusspanapproving-rfus"></a><span id="Approving_RFUs"></span><span id="approving_rfus"></span><span id="APPROVING_RFUS"></span>批准的 RFUs


打开一个 Team Foundation Server (TFS) 更新请求。

打开单独 TFS 的更新请求更新从 Windows Phone 8.0 到 Windows Phone 8.1 和 Windows Phone 8.1 到 Windows Phone 8.1。

1.  添加标题，使用格式:"RFU 批准&lt;MOID 或多个&gt;&lt;设备名称或多个&gt;&lt;阿波罗蓝色或蓝色蓝色&gt;"。

2.  完成其他相应的 TFS 字段。

3.  将 Excel 电子表格 (.xls) 附加的设备，包括以下信息的列表︰

    1.  RFU\#

    2.  RFU 证号 （不进行代码签名 TKT）

    3.  PhoneManufacturerModelName （不友好或代码名称）

    4.  电话移动操作员姓名 (MOId)

    5.  源的固件修订版本

    6.  目标的固件修订版

    示例：

    <table>
    <colgroup>
    <col width="12%" />
    <col width="12%" />
    <col width="12%" />
    <col width="12%" />
    <col width="12%" />
    <col width="12%" />
    <col width="12%" />
    <col width="12%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left">RFU#</th>
    <th align="left">RFU 票据编号</th>
    <th align="left">PhoneManufacturerModelName</th>
    <th align="left">MOId</th>
    <th align="left">固件源</th>
    <th align="left">目标固件</th>
    <th align="left">在更新之前的操作系统版本</th>
    <th align="left">更新后的操作系统版本</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><p>12345</p></td>
    <td align="left"><p>TKT-RFU-生产-ABC3DEF-2</p></td>
    <td align="left"><p>OEMDeviceName</p></td>
    <td align="left"><p>000-33</p></td>
    <td align="left"><p>1.2.3.4</p></td>
    <td align="left"><p>1.2.3.5</p></td>
    <td align="left"><p>10521</p></td>
    <td align="left"><p>12397</p></td>
    </tr>
    </tbody>
    </table>

     

## <a name="span-idapprovingadaptationkitakreleasesnofirmwareupdatespanspan-idapprovingadaptationkitakreleasesnofirmwareupdatespanspan-idapprovingadaptationkitakreleasesnofirmwareupdatespanapproving-adaptation-kit-ak-releases-no-firmware-update"></a><span id="Approving_Adaptation_Kit__AK__Releases__no_firmware_update_"></span><span id="approving_adaptation_kit__ak__releases__no_firmware_update_"></span><span id="APPROVING_ADAPTATION_KIT__AK__RELEASES__NO_FIRMWARE_UPDATE_"></span>批准的适配套件 (AK) 版本 （无固件更新）


OEM 和 MO 可以提交和批准发行的适配套件 (AK) 而无需附带 RFU。 只 AK 包准备预览和发布 OEM 提交通过摄取工具只 AK 请求时。 一旦获得批准，该更新可发放到生产中。 这些更新程序应针对零售服务预览，如果想要进入生产。

打开 TFS 更新请求︰

1.  输入格式的标题:"批准只 AK 发行&lt;MOID 或多个&gt;&lt;设备名称或多个&gt;&lt;发行版中，例如 GDR2QFE1&gt;"。

2.  完成其他相应的 TFS 字段。

3.  将 Excel 电子表格 (.xls) 附加的设备，包括以下信息的列表。 提供请求取消手动更新的说明。

    1.  RFU\#。 请注意，会有 TFS ID 与只 AK 捆绑包。

        只用一个 TFS 请求中的普通 RFU 批准不混合使用 AK，单独管理。

    2.  PhoneManufacturerModelName

    3.  电话移动操作员姓名 (MOId)

    4.  在更新之前的操作系统版本

    5.  更新后的操作系统版本

    示例：

    <table>
    <colgroup>
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left">RFU#</th>
    <th align="left">PhoneManufacturerModelName</th>
    <th align="left">MOId</th>
    <th align="left">在更新之前的操作系统版本</th>
    <th align="left">更新后的操作系统版本</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><p>12345</p></td>
    <td align="left"><p>OEMDeviceName</p></td>
    <td align="left"><p>000-33</p></td>
    <td align="left"><p>10327</p></td>
    <td align="left"><p>10501</p></td>
    </tr>
    </tbody>
    </table>

     

## <a name="span-idcancellingrfusspanspan-idcancellingrfusspanspan-idcancellingrfusspancancelling-rfus"></a><span id="Cancelling_RFUs"></span><span id="cancelling_rfus"></span><span id="CANCELLING_RFUS"></span>正在取消 RFUs


RFUs 在预览中的不需要手动取消时用同一个基准来替换。 当最新的固件更新进入实时预览自动摄取将取消替换 RFU 最佳的基础上。 对于取消 RFUs 的实时预览中，使用[请求 UpdateCancellation cmdlet](request-updatecancellation.md)。 取消已有的 RFUs 实时在生产环境中︰

打开 TFS 更新请求︰

1.  输入格式的标题:"&lt;OEM&gt;请求取消︰&lt;设备名称&gt;&lt;MOId&gt; &lt;解释&gt;"。

2.  完成其他相应的 TFS 字段。

3.  将 Excel 电子表格 (.xls) 附加的设备，包括以下信息的列表。 提供请求取消手动更新的说明。

    1.  RFU\#

    2.  PhoneManufacturerModelName

    3.  电话移动操作员姓名 (MOId)

    4.  在更新之前的操作系统版本

    5.  更新后的操作系统版本

    示例：

    <table>
    <colgroup>
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left">RFU#</th>
    <th align="left">PhoneManufacturerModelName</th>
    <th align="left">MOId</th>
    <th align="left">在更新之前的操作系统版本</th>
    <th align="left">更新后的操作系统版本</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><p>765432</p></td>
    <td align="left"><p>OEMDeviceName</p></td>
    <td align="left"><p>000-33</p></td>
    <td align="left"><p>12345</p></td>
    <td align="left"><p>12346</p></td>
    </tr>
    </tbody>
    </table>

     

## <a name="span-idaftertheupdatespanspan-idaftertheupdatespanspan-idaftertheupdatespanafter-the-update"></a><span id="After_the_update"></span><span id="after_the_update"></span><span id="AFTER_THE_UPDATE"></span>更新后


更新发布到 Microsoft 的生产更新服务器，在其中您的客户的电话将下载更新并将其安装得到他们同意。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[更新](index.md)

[提交更新](submit-an-update.md)

 

 
