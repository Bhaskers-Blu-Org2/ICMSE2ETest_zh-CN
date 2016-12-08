---
author: Justinha
Description: "捕获硬盘分区使用 DISM 的图像"
ms.assetid: 164b9185-402f-4afb-bcf5-ef2f37077ed6
MSHAttr: PreferredLib:/library/windows/hardware
title: "捕获硬盘分区使用 DISM 的图像"
ms.openlocfilehash: de61537a6793328daa2dddc0a68e005db6aa8aa9
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="capture-images-of-hard-disk-partitions-using-dism"></a>捕获硬盘分区使用 DISM 的图像


可以使用部署映像服务和管理 (DISM) 工具来捕获映像部署到硬盘并将其保存为 Windows® 映像 (.wim) 文件。 若要查看此信息如何应用于 Windows、 系统和恢复分区，请参阅[捕获和应用 Windows、 系统和恢复分区](capture-and-apply-windows-system-and-recovery-partitions.md)。

## <a name="span-idprerequisitesspanspan-idprerequisitesspanspan-idprerequisitesspanprerequisites"></a><span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>系统必备组件


1.  Windows PE。 请参阅[WinPE︰ 创建可引导 USB 驱动器](winpe-create-usb-bootable-drive.md)。

2.  参考计算机。 您可以通过部署 Windows，然后从系统中删除特定于计算机的信息来创建参考计算机。 有关详细信息，请参阅[Sysprep （通用化） 的 Windows 安装](sysprep--generalize--a-windows-installation.md)。

## <a name="span-idstep1determiningwhichpartitionstocapturespanspan-idstep1determiningwhichpartitionstocapturespanspan-idstep1determiningwhichpartitionstocapturespanstep-1-determining-which-partitions-to-capture"></a><span id="Step_1__Determining_Which_Partitions_to_Capture"></span><span id="step_1__determining_which_partitions_to_capture"></span><span id="STEP_1__DETERMINING_WHICH_PARTITIONS_TO_CAPTURE"></span>步骤 1︰ 确定到捕获的分区


此表显示分区，您必须捕获和自动管理的那些的类型。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">分区类型</th>
<th align="left">您应捕获此分区？</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>系统分区</strong>（系统分区 BIOS 或 EFI 系统分区）</p></td>
<td align="left"><p>可选项。</p>
<p>如果只需要一组简单的分区文件，则您不需要捕获此分区。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>Microsoft 保留分区 (MSR)</strong></p></td>
<td align="left"><p>No.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>主分区</strong>（Windows 分区的实用程序分区）</p></td>
<td align="left"><p>是。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>扩展的分区</strong></p></td>
<td align="left"><p>No.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>逻辑分区</strong>（Windows 分区的实用程序分区）</p></td>
<td align="left"><p>是。</p></td>
</tr>
</tbody>
</table>

 

可以捕获和应用映像之间基于 BIOS 以及基于 UEFI 的计算机上的分区，因为 Windows 映像不受固件。 有关详细信息，请参阅[捕获和应用 Windows、 系统和恢复分区](capture-and-apply-windows-system-and-recovery-partitions.md)。

## <a name="span-idstep2assigndriveletterstopartitionsspanspan-idstep2assigndriveletterstopartitionsspanspan-idstep2assigndriveletterstopartitionsspanstep-2-assign-drive-letters-to-partitions"></a><span id="Step_2__Assign_Drive_Letters_to_Partitions"></span><span id="step_2__assign_drive_letters_to_partitions"></span><span id="STEP_2__ASSIGN_DRIVE_LETTERS_TO_PARTITIONS"></span>步骤 2︰ 给分区分配驱动器号


如果任何您想要捕获的分区没有分配一个驱动器号，则将使用**DiskPart**工具号分配。

1.  使用 Windows PE 启动计算机的引用。

2.  在 Windows PE 命令提示符下键入`diskpart`打开 DiskPart 工具。

    ``` syntax
    X:> diskpart
    DISKPART>
    ```

3.  选择与硬盘`select disk`命令。 例如，

    ``` syntax
    DISKPART> select disk 0
    ```

4.  查看与分区`list partition`命令。 例如，

    ``` syntax
    DISKPART> list partition

    DISKPART> list partition

      Partition ###  Type              Size     Offset
      -------------  ----------------  -------  -------
      Partition 1    Primary            300 MB  1024 KB
      Partition 2    Primary            200 GB   301 MB
    ```

5.  选择与该分区`select partition`命令。 例如，

    ``` syntax
    DISKPART> select partition=1
    ```

6.  将字母分配给与该分区`assign letter`命令。 例如，

    ``` syntax
    DISKPART> assign letter=S
    ```

7.  类型`exit`返回到 Windows PE 命令提示符。

    ``` syntax
    DISKPART> exit
    X:\>
    ```

有关详细信息，请参阅从命令行的 DiskPart 帮助或[Diskpart 命令行语法](http://go.microsoft.com/fwlink/?LinkId=128458)。

## <a name="span-idstep3capturepartitionimagesusingdismspanspan-idstep3capturepartitionimagesusingdismspanspan-idstep3capturepartitionimagesusingdismspanstep-3-capture-partition-images-using-dism"></a><span id="Step_3__Capture_Partition_Images_using_DISM"></span><span id="step_3__capture_partition_images_using_dism"></span><span id="STEP_3__CAPTURE_PARTITION_IMAGES_USING_DISM"></span>第 3 步︰ 捕获使用 DISM 的分区映像


捕获图像的每个自定义分区。

-   在 Windows PE 命令提示符下，捕获通过使用**DISM**命令和**/captureImage**选项的图像。 例如，

    ``` syntax
    Dism /Capture-Image /ImageFile:c:\my-windows-partition.wim /CaptureDir:C:\ /Name:"My Windows partition"
    Dism /Capture-Image /ImageFile:s:\my-system-partition.wim /CaptureDir:S:\ /Name:"My system partition"
    ```

    有关使用 DISM 工具来捕获映像的详细信息，请参阅[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)。

## <a name="span-idstep4saveimagestothenetworkspanspan-idstep4saveimagestothenetworkspanspan-idstep4saveimagestothenetworkspanstep-4-save-images-to-the-network"></a><span id="Step_4__Save_Images_to_the_Network"></span><span id="step_4__save_images_to_the_network"></span><span id="STEP_4__SAVE_IMAGES_TO_THE_NETWORK"></span>步骤 4︰ 将图像保存到网络


将.wim 文件保存到您的网络或其他安全的地方。

1.  使用**net use**命令连接到分布共享。 例如，

    ``` syntax
    net use n: \\Server\Share
    ```

    如果出现提示，请提供网络凭据。

2.  将分区复制到网络共享。 例如，

    ``` syntax
    md N:\Images\
    copy C:\my-windows-partition.wim N:\Images\
    copy c:\my-system-partition.wim N:\Images\
    ```

## <a name="span-idnextstepsspanspan-idnextstepsspanspan-idnextstepsspannext-steps"></a><span id="Next_Steps"></span><span id="next_steps"></span><span id="NEXT_STEPS"></span>下一步行动


捕获和存储映像之后，您可以︰

-   将其装载到参考计算机以进行修改。 有关详细信息，请参阅[安装和修改 Windows 映像使用 DISM](mount-and-modify-a-windows-image-using-dism.md)。

-   将文件拆分成更小的文件。 有关详细信息，请参阅[拆分到范围跨多个 Dvd 的 Windows 映像 (WIM) 文件](split-a-windows-image--wim--file-to-span-across-multiple-dvds.md)。

-   将映像应用到目标计算机。 有关详细信息，请参阅[使用 DISM 应用图像](apply-images-using-dism.md)。

-   映像提供服务。 有关详细信息，请参阅[Windows 映像使用 DISM 服务](service-a-windows-image-using-dism.md)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[部署映像服务和管理 (DISM) 命令行选项](deployment-image-servicing-and-management--dism--command-line-options.md)

[BCDboot 命令行选项](bcdboot-command-line-options-techref-di.md)

[捕获和应用 Windows、 系统和恢复分区](capture-and-apply-windows-system-and-recovery-partitions.md)

[引导至 VHD （本机引导）︰ 将虚拟硬盘添加到引导菜单](boot-to-vhd--native-boot--add-a-virtual-hard-disk-to-the-boot-menu.md)

 

 






