---
author: Justinha
Description: "创建和管理 Windows 映像使用 DISM"
ms.assetid: ef3d32c6-54f4-4347-9cbb-593c7ae7bf5e
MSHAttr: PreferredLib:/library/windows/hardware
title: "创建和管理 Windows 映像使用 DISM"
ms.openlocfilehash: aa064445ac66d6943ed2f19925ddc1ab618c6b0a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="create-and-manage-a-windows-image-using-dism"></a>创建和管理 Windows 映像使用 DISM


部署映像服务和管理 (DISM.exe) 装载 Windows 映像 (.wim) 文件或虚拟硬盘 （.vhd 或.vhdx） 来处理。 图像索引号或验证您要装载的映像的体系结构，您还可以使用 DISM 图像管理命令。 更新映像后，您必须卸载它，要么提交或放弃所做的更改。

您可以使用 DISM 服务命令来安装、 卸载、 配置和更新的功能和离线的 Windows® 图像和脱机 Windows 预安装环境 (Windows PE) 映像中的程序包。 有关 DISM 的常见方案的详细信息，请参阅[DISM 是什么？](what-is-dism.md)。 有关 DISM 服务命令的详细信息，请参阅[部署映像服务和管理 (DISM) 命令行选项](deployment-image-servicing-and-management--dism--command-line-options.md)。

## <a name="span-idinthissectionspanspan-idinthissectionspanspan-idinthissectionspanin-this-section"></a><span id="In_This_Section"></span><span id="in_this_section"></span><span id="IN_THIS_SECTION"></span>在这一节


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>[捕获硬盘分区使用 DISM 的图像](capture-images-of-hard-disk-partitions-using-dism.md)</p></td>
<td align="left"><p>使用 Diskpart 工具和部署映像服务和管理 (DISM) 工具来捕获映像并将其保存为.wim 文件。</p></td>
</tr>
<tr class="even">
<td align="left"><p>[装载和修改 Windows 映像使用 DISM](mount-and-modify-a-windows-image-using-dism.md)</p></td>
<td align="left"><p>将 Windows 映像 (.wim) 文件的内容映射到映像提供服务或执行常见的文件操作，例如添加和删除文件的目录。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[应用使用 DISM 的映像](apply-images-using-dism.md)</p></td>
<td align="left"><p>使用 Diskpart 工具和 DISM 工具将 Windows 映像应用到部署的计算机上的一个或多个分区。</p></td>
</tr>
<tr class="even">
<td align="left"><p>[分割成多个 Dvd 的跨度的 Windows 映像 (WIM) 文件](split-a-windows-image--wim--file-to-span-across-multiple-dvds.md)</p></td>
<td align="left"><p>将大型.wim 文件拆分为几个较小的文件符合您选定的介质。 副本为.iso 文件拆分.wim 文件到您选定的介质上。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[使用 DISM 的多种体系结构类型创建 WIM](create-a-wim-for-multiple-architecture-types-using-dism.md)</p></td>
<td align="left"><p>创建单个.wim 文件，其中包括 32 位和 64 位的 Windows 图像。</p></td>
</tr>
<tr class="even">
<td align="left"><p>[将卷映像附加到现有图像使用 DISM](append-a-volume-image-to-an-existing-image-using-dism--s14.md)</p></td>
<td align="left"><p>将第二个映像添加到现有.wim 文件。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[创建数据映像使用 DISM](create-a-data-image-using-dism.md)</p></td>
<td align="left"><p>创建一个只包含文件和应用程序要使用无人参与的答案文件将复制到 Windows 安装的.wim 文件。</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)

 

 






