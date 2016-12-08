---
author: Justinha
ms.assetid: 0fbb2a9b-d3ce-4d7f-b68a-af641ceec96d
MSHAttr: PreferredLib:/library/windows/hardware
title: "WIM 与 VHD 与 FFU︰ 比较图像文件格式"
ms.openlocfilehash: 6c3135aa2366fe3bf51f03837d8c432a1e0ca32e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wim-vs-vhd-vs-ffu-comparing-image-file-formats"></a>WIM 与 VHD 与 FFU︰ 比较图像文件格式


比较。WIM。VHD /。VHDX，和。FFU︰ 这些文件格式都用于将 Windows 部署到新设备。 下面是如何将它们进行比较︰

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"></td>
<td align="left">Windows 映像 (。WIM)</td>
<td align="left">虚拟硬盘 (。VHD/VHDX)</td>
<td align="left">全闪存更新 (。FFU)</td>
</tr>
<tr class="even">
<td align="left">常见用途</td>
<td align="left"><p>最快的测试和修改 Windows 映像。</p>
<p>快速装载和修改映像。</p></td>
<td align="left"><p>到虚拟 Pc 部署 Windows 的最简单。</p>
<p>您可以直接从单个 VHD/VHDX 文件引导新的设备。</p></td>
<td align="left"><p>用于捕获和部署 Windows 在工厂地板上的速度最快。</p>
<p>包括内置的安全机制来验证签名的图像。</p></td>
</tr>
<tr class="odd">
<td align="left">图像处理样式</td>
<td align="left">基于文件的</td>
<td align="left">基于扇区的</td>
<td align="left">基于扇区的</td>
</tr>
<tr class="even">
<td align="left">压缩</td>
<td align="left">支持多种类型的压缩</td>
<td align="left">无</td>
<td align="left">无</td>
</tr>
<tr class="odd">
<td align="left">它捕获什么？</td>
<td align="left"><p>一组文件，直到整个分区。</p></td>
<td align="left"><p>捕获完整的驱动器信息，包括分区集。</p></td>
<td align="left"><p>捕获完整的驱动器信息，包括分区集。</p></td>
</tr>
<tr class="even">
<td align="left">当应用图像时，会发生什么？</td>
<td align="left"><p>将文件和文件夹添加到分区中。</p>
<p>如果已存在相同名称的文件和文件夹，它们正在被替换。 否则，将保留现有的文件。</p></td>
<td align="left"><p>清除整个驱动器。</p></td>
<td align="left"><p>清除整个驱动器。</p></td>
</tr>
<tr class="odd">
<td align="left">可以为不同大小的硬盘进行部署</td>
<td align="left"><p>是。</p></td>
<td align="left"><p>是的尽管新的驱动器必须是相同的大小或大于原始。</p></td>
<td align="left"><p>是的尽管新的驱动器必须是相同的大小或大于原始。</p></td>
</tr>
<tr class="even">
<td align="left">是否可以修改图像？</td>
<td align="left"><p>是。 使用 DISM 之类的工具，您可以装载、 修改和卸载此映像。</p></td>
<td align="left"><p>是的您可以安装 VHD/VHDX，好像它是可移动媒体，和修改的文件。</p></td>
<td align="left"><p>是的但它仅限于添加软件包。</p></td>
</tr>
<tr class="odd">
<td align="left">安全性</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><p>包括安全标头和图像标题来标识受保护的图像。</p>
<p>包括目录和哈希表来验证签名提前前闪烁到设备。</p></td>
</tr>
</tbody>
</table>

 

若要了解详细信息，请参阅**/Apply-Image**在[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


**DISM**
[部署映像服务和管理 (DISM) 命令行选项](deployment-image-servicing-and-management--dism--command-line-options.md)

**VHD/VHDX**
[引导至 VHD （本机引导）︰ 将虚拟硬盘添加到引导菜单](boot-to-vhd--native-boot--add-a-virtual-hard-disk-to-the-boot-menu.md)

[部署 Windows 在 VHD （本机引导）](deploy-windows-on-a-vhd--native-boot.md)

**FFU**
[部署 Windows 使用全闪存更新 (FFU)](deploy-windows-using-full-flash-update--ffu.md)

[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)

[FFU 图像格式](../mobile/ffu-image-format.md)

 



