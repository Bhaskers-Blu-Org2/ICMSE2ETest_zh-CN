---
title: "功能清单文件和定义使用 OEMInput 的图像"
description: "了解如何创建 OEMInput 和功能清单文件，以便充分定义的移动图像内容。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: A3E05C3B-450D-4AFD-8368-241EAB7F8036
ms.openlocfilehash: b62da13fb20718e47e5255110ec9b9fc359327dd
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="define-the-image-using-oeminput-and-feature-manifest-files"></a>功能清单文件和定义使用 OEMInput 的图像


了解如何创建 OEMInput 和功能清单文件，以便充分定义的移动图像内容。

## <a name="in-this-section"></a>在这一节


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>主题</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="oeminput-file-contents.md">OEMInput 文件的内容</a></p></td>
<td><p>OEMInput.xml 文件包含用于定义移动图像的必选和可选元素。 操作系统使用此文件来确定应用程序的处理器、 生成类型、 用户界面语言，默认区域格式、 分辨率和其他属性以在将生成的图像中包含。</p>
<p>本主题提供了有关该文件的 XML 架构的完整列表。</p></td>
</tr>
<tr class="even">
<td><p><a href="optional-features-for-building-images.md">可选功能，用于建立移动图像</a></p></td>
<td><p>它们包括在 OEMInput XML 文件中的<strong>功能</strong>元素，可以向图像添加可选功能。</p></td>
</tr>
<tr class="odd">
<td><p><a href="feature-manifest-file-contents.md">功能清单文件的内容</a></p></td>
<td><p><em>功能清单 (FM) 文件</em>用于定义特定类型的图像生成的包含不同的可选包。 本主题介绍了调频文件中的必需和可选元素。</p></td>
</tr>
<tr class="even">
<td><p><a href="create-a-feature-and-include-it-in-an-image.md">创建特征，并将其包括在映像中</a></p></td>
<td><p>本主题演示如何创建特征，并将其添加到图像。</p></td>
</tr>
<tr class="odd">
<td><p><a href="adding-a-driver-to-a-test-image.md">将驱动程序添加到测试映像</a></p></td>
<td><p>本主题演示如何创建特征，并将其添加到测试映像。</p></td>
</tr>
<tr class="even">
<td><p><a href="feature-groupings-and-constraints.md">分组功能和约束</a></p></td>
<td><p>功能组和功能约束允许额外的逻辑添加到生成系统支持 OEMInput 的 XML 的智能处理。</p></td>
</tr>
<tr class="odd">
<td><p><a href="set-device-platform-information.md">设置设备平台信息</a></p></td>
<td><p>了解如何构建图像，可以刷新到移动设备，在图像最终零售设备包括合作伙伴名称、 版本号和设备名称，例如附加的设备平台信息的先决条件。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[构建和闪烁移动图像](building-and-flashing-images.md)

 

 

[发送有关此主题的意见的评论](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_phFlashing\p_phFlashing%5D:%20Define%20the%20image%20using%20OEMInput%20and%20feature%20manifest%20files%20%20RELEASE:%20%2810/4/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "发送有关此主题的意见的评论")





