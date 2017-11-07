---
title: "更新包。FFU 图像文件"
description: "更新包。FFU 图像文件"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 39d965d5-880d-407f-9e16-ea6a1a8f42d0
ms.openlocfilehash: 18419ce2a38f6efcdaab049c966b02ac7c693869
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="update-packages-in-an-ffu-image-file"></a>更新包。FFU 图像文件


可以使用 ImageApp.exe 来将新的或更新的包添加到一个现有的。FFU 生产、 运行状况和测试图像的图像文件。

ImageApp 具有下列重要限制︰

-   ImageApp 只应将包添加到映像生产、 测试和运行状况。 不要使用 ImageApp 来修改零售的图像，因为它可能会产生负面影响更新的可靠性和安全性的设备。 ImageApp 不能用于更改现有的映像的分区布局。 如果需要一个不同的分区布局，则图像将需要重建。 有关详细信息，请参阅[构建使用 ImgGen.cmd 的设备图像](building-a-phone-image-using-imggencmd.md)。
-   ImageApp 不能用于从映像中删除程序包。
-   准备设备平台 CompactOS 上使用压缩的分区，则需要采用 Windows 10 的 DISM 版本的个人电脑。 如果您的技术人员计算机运行的以前版本的 Windows，您可以通过 Windows 10 为安装 Windows 评估和部署工具包 (ADK) 或复制和安装的 DISM 驱动程序获得这。 此过程是用来在 Windows PE 安装 DISM 相同。 若要了解详细信息，请参阅[使用早期版本的 Windows PE 安装 Windows 10︰ 将 DISM 添加到 Windows PE 映像](../desktop/copy-dism-to-another-computer.md)。

在更新现有的包时，一定要增加版本号。 有关详细信息，请参阅[更新的要求](../../service/mobile/update-requirements.md)。 当在图像中添加软件包，尚不存在，可以使用任意版本数量。

指定要添加类似于此处所示的一个输入 XML 文件中的程序包。

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<UpdateOSInput xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
      xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
      xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate">
   <Description>Add Debugger On package</Description>
   <PackageFiles>
      <PackageFile>C:\Program Files\Windows Kits\10\Packages\Microsoft.BCD.DebuggerOn.spkg</PackageFile>
   </PackageFiles>
</UpdateOSInput>
```

例如，如果`updateInput.xml`文件位于 c:\\temp 文件夹，请使用此命令来将指定的文件包添加到现有`flash.ffu`的图像文件。

``` syntax
ImageApp flash.ffu /UpdateInputXML:C:\temp\updateInput.xml
```

## <a name="command-line-syntax-for-imageappexe"></a>ImageApp.exe 的命令行语法


``` syntax
ImageApp.exe <imageFile.ffu> </UpdateInputXML:updateInputfile.xml> 
```

下表介绍的 ImageApp.exe 命令行参数。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>参数</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>imageFile</em>.ffu</p></td>
<td><p>要更新 FFU 文件的名称。</p></td>
</tr>
<tr class="even">
<td><p>/ UpdateInputXML:<em>updateInputfile</em>.xml</p></td>
<td><p>标识要添加到映像的包的 XML 文件的名称。 如果此文件不在当前目录中，则必须包括文件的路径。</p></td>
</tr>
</tbody>
</table>

 

## <a name="troubleshooting"></a>疑难解答


**"状态\_文件\_IS\_A\_目录"**︰ 未使用 DISM 的 Windows 10 版的电脑生成 CompactOS 的图像时，将出现此错误消息。 这下可以安装 Windows ADK 的 Windows 10，或只是安装 DISM 安装驱动程序从另一台计算机使用 Windows ADK 的 Windows 10。 若要了解详细信息，请参阅[安装 Windows 10 使用早期版本的 Windows PE](../desktop/copy-dism-to-another-computer.md)。

## <a name="related-topics"></a>相关的主题


[构建使用 ImgGen.cmd 的图像](building-a-phone-image-using-imggencmd.md)

 

 

[发送有关此主题的意见的评论](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_phFlashing\p_phFlashing%5D:%20Update%20packages%20in%20an%20.FFU%20image%20file%20%20RELEASE:%20%2810/4/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "发送有关此主题的意见的评论")





