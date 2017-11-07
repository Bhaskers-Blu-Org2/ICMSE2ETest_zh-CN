---
author: kpacquer
Description: To update your devices, you'll submit an update to Microsoft.
ms.assetid: 529f841c-abd2-4b33-93c6-509e3dfcbff7
MSHAttr: PreferredLib:/library/windows/hardware
title: "移动的更新"
ms.openlocfilehash: 4f7c688443f88801616586790a8a7684e9d13b2b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mobile-update"></a>移动的更新

##<a name="updating-a-device"></a>更新设备
若要更新您的设备，将提交给 Microsoft 更新。 移动运营商 (MO) 可以帮助更新测试。 审核时，该更新将转到生产更新服务器，在客户手机可以下载并接收通过移动电话或 Wi-fi 连接更新。 与用户同意的情况下，设备更新，自动的大部分工作在后台更新过程。

### <a name="span-idbeforeyoubeginspanspan-idbeforeyoubeginspanspan-idbeforeyoubeginspanbefore-you-begin"></a><span id="Before_you_begin"></span><span id="before_you_begin"></span><span id="BEFORE_YOU_BEGIN"></span>在开始之前


之前提交的更新，请完成以下任务︰

1.  注册以便提交固件提交和更新请求。 有关详细信息，请参阅[接收客户端](ingestion-client-for-windows-phone.md)的"零售包进行签名和更新提交注册"一节。

2.  查看[更新方案](update-scenarios.md)中适用于您的更新方案。

3.  检查[更新要求](update-requirements.md)在适用于您的更新要求。

4.  获取固件成功签名的提交票证 Id 将从更新设备的固件和设备将更新的固件。 有关如何执行此任务的信息，查看[签名提交二进制文件是零售](https://msdn.microsoft.com/library/windows/hardware/dn789223)。

### <a name="span-idtypesofupdatesspanspan-idtypesofupdatesspanspan-idtypesofupdatesspantypes-of-updates"></a><span id="Types_of_updates"></span><span id="types_of_updates"></span><span id="TYPES_OF_UPDATES"></span>更新类型


-   **Microsoft 更新**。 这些更新目标在图像中，包括在 ESP （EFI 系统分区） 和主操作系统分区中，Microsoft 程序包和系统加载程序的 Microsoft 程序包的 Microsoft 代码。

-   **OEM 的更新**。 这些也被称为主板支持包 (BSP) 的更新。 Oem 可以开发包中保留区域及其组件和它们提供货物，包括主操作系统和 MMO 分区的分区。 无法更新用户数据和 SD 卡。 当应用这些更新，必须保留所有用户数据和设置。

这些类型的更新只分别提交。

 

##<a name="refurbishing-a-device"></a>翻新过的设备
使用本节中的主题以了解更多关于翻新移动设备运行 Windows 10 移动过。


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
<td align="left"><p>[重置移动设备](resetting-the-phone.md)</p></td>
<td align="left"><p>重置设备解决了大量关键的方案︰</p>
<ul>
<li>用户可能需要重置的设备来将它转移到另一个所有者。</li>
<li>设备已丢失或被盗以及所有者想要远程重新启动设备</li>
<li>该设备属于一个单位，并组织想要远程重新启动设备。 例如，当雇员离开公司。</li>
<li>该设备出现故障，用户想要将设备重置。</li>
<li>OEM 出厂测试已完成，并且想要重置该设备 （还可以选择保留预加载的站点地图数据）。</li>
</ul></td>
</tr>
</tbody>
</table>

 

 


 





