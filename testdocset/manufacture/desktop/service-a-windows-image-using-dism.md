---
author: Justinha
Description: "使用 DISM Windows 映像提供服务"
ms.assetid: 7578765f-15ca-4cdd-9327-cfe42a36add2
MSHAttr: PreferredLib:/library/windows/hardware
title: "使用 DISM Windows 映像提供服务"
ms.openlocfilehash: 1175dde3fe059f60f301888d46662b75c4fd63d1
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="service-a-windows-image-using-dism"></a>使用 DISM Windows 映像提供服务


部署映像服务和管理 (DISM) 工具允许用户枚举驱动程序和程序包、 修改配置设置、 添加和删除驱动程序，而无需使用无人参与的答案文件，等等。 您可以使用 DISM WIM 或 VHD 文件时，在脱机或联机上运行的操作系统。

脱机服务允许您修改或处理的 Windows® 图像完全脱机，而不首先将其启动。 因为操作系统部署到计算机之前，您可以自定义程度的图像，这样可以减少部署成本。 此外，如果您有存储的主映像，您要确保始终是最新的则可以将它保存而不启动图像。

您还可以使用 DISM 若要联机处理映像。 如果您需要启动的操作系统来安装应用程序或测试和验证安装，您可以启动审核模式并添加驱动程序和程序包，或启用功能和国际设置。

## <a name="span-idinthissectionspanspan-idinthissectionspanspan-idinthissectionspanin-this-section"></a><span id="In_This_Section"></span><span id="in_this_section"></span><span id="IN_THIS_SECTION"></span>在这一节


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>[添加和移除脱机 Windows 映像的驱动程序](add-and-remove-drivers-to-an-offline-windows-image.md)</p></td>
<td align="left"><p>添加或删除使用 DISM 或无人参与的答案文件脱机映像中的驱动程序。</p></td>
</tr>
<tr class="even">
<td align="left"><p>[启用或禁用使用 DISM 的 Windows 功能](enable-or-disable-windows-features-using-dism.md)</p></td>
<td align="left"><p>启用或禁用 Windows 映像使用 DISM 中的功能。 此外可以删除的功能，安装要求，并恢复以前删除的功能。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[添加或删除程序包使用 DISM 脱机](add-or-remove-packages-offline-using-dism.md)</p></td>
<td align="left"><p>添加或使用 DISM 或无人参与的答案文件脱机映像中删除程序包。</p></td>
</tr>
<tr class="even">
<td align="left"><p>[添加和删除语言包使用 DISM 脱机](add-and-remove-language-packs-offline-using-dism.md)</p></td>
<td align="left"><p>添加或删除语言包并配置国际设置使用 DISM 脱机映像中。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[使用 DISM 的 sideload 应用程序](sideload-apps-with-dism-s14.md)</p></td>
<td align="left"><p>使用 Windows PowerShell® 或部署映像服务和管理 (DISM) 平台，业务线 (LOB) Windows 应用商店应用程序安装到 Windows 映像。</p></td>
</tr>
<tr class="even">
<td align="left"><p>[使用 DISM 的预安装应用程序](preinstall-apps-using-dism.md)</p></td>
<td align="left"><p>在 Windows 映像中的预安装应用程序。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[自定义开始屏幕](customize-the-start-screen.md)</p></td>
<td align="left"><p>自定义开始屏幕包含 Windows 应用商店应用程序和桌面应用程序在您的业务中使用。</p></td>
</tr>
<tr class="even">
<td align="left"><p>[将 Windows 映像更改为较高版本使用 DISM](change-the-windows-image-to-a-higher-edition-using-dism.md)</p></td>
<td align="left"><p>查询以确定哪种版本的 Windows 映像，以及如何将映像更改为较高版本的 Windows 映像。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[导出或导入默认的应用程序关联](export-or-import-default-application-associations.md)</p></td>
<td align="left"><p>更改与文件扩展名或 Windows 映像中的协议关联的默认程序。</p></td>
</tr>
<tr class="even">
<td align="left"><p>[已安装的 Windows 映像提供服务](service-a-mounted-windows-image.md)</p></td>
<td align="left"><p>使用 DISM 装载映像并对其进行修改。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[应用的 Windows 映像提供服务](service-an-applied-windows-image.md)</p></td>
<td align="left"><p>使用 DISM 应用映像，然后再修改它。</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[了解处理策略](understanding-servicing-strategies.md)

[获取映像或组件使用 DISM 的清单](take-inventory-of-an-image-or-component-using-dism.md)

 

 






