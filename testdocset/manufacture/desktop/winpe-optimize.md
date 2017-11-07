---
作者︰ KPacquer 描述: WinPE︰ 优化并缩小图像 ms.assetid: 5d5c13e8-8754-4fff-afd1-dcc3fb757bb9 MSHAttr: PreferredLib: / 库/windows/硬件标题: WinPE︰ 优化并缩小图像
---

# <a name="winpe-optimize-and-shrink-the-image"></a>WinPE︰ 优化并缩小图像

通过添加驱动程序、 语言、 或包后清理图像加速 Windows 预安装环境 (WinPE) 启动时间。

## <a name="span-idmountthewindowspebootimagespanmount-the-windows-pe-boot-image"></a><span id="Mount_the_Windows_PE_boot_image"></span>装载 Windows PE 启动映像

``` syntax
Dism /Mount-Image /ImageFile:"C:\WinPE_amd64\media\sources\boot.wim" /index:1 /MountDir:"C:\WinPE_amd64\mount"
```

## <a name="span-idaddcustomizationsspanspan-idaddcustomizationsspanspan-idaddcustomizationsspanadd-customizations"></a><span id="Add_customizations"></span><span id="add_customizations"></span><span id="ADD_CUSTOMIZATIONS"></span>添加自定义项

添加[驱动程序](winpe-add-drivers.md)、[程序包 （可选的组件参考）](winpe-add-packages--optional-components-reference.md)，和/或[任何其他自定义设置](winpe-mount-and-customize.md)。

但是，不要卸载映像还为时尚早。

## <a name="span-idpreparetocleantheimagespanprepare-to-clean-the-image"></a><span id="Prepare_to_clean_the_image"></span>准备以清理图像

此过程将标记可以在导出过程中删除的文件。 

``` syntax
DISM /Cleanup-Image /Image="C:\WinPE_amd64\mount" /StartComponentCleanup /ResetBase 
```

## <a name="span-idunmounttheimagespanunmount-the-image"></a><span id="Unmount_the_image"></span>卸载映像
    
提交更改并卸载 WinPE 映像︰
``` syntax
Dism /Unmount-Image /MountDir:"C:\WinPE_amd64\mount" /Commit
```

## <a name="span-idexportandthenreplacetheimagespanexport-and-then-replace-the-image"></a><span id="Export_and_then_replace_the_image"></span>导出，然后将替换图像

导出的图像应小于旧映像。 新替换原始图像。 

``` syntax
Dism /Export-Image /SourceImageFile:"c:\winpe_amd64\media\sources\boot.wim" /SourceIndex:1 /DestinationImageFile:"c:\winpe_amd64\mount\boot2.wim"
Del "C:\WinPE_amd64\media\sources\boot.wim"
Copy "C:\WinPE_amd64\mount\boot2.wim" "c:\winpe_amd64\media\sources\boot.wim"
```

## <a name="span-idtryitoutspantry-it-out"></a><span id="Try_it_out"></span>试一下

1.  创建可引导介质，如 USB 闪存驱动器。

    ``` syntax
    MakeWinPEMedia /UFD C:\WinPE_amd64 F:
    ```

2.  引导介质。 自动启动 WinPE。 WinPE 窗口出现后，wpeinit 命令将自动运行。 这可能需要几分钟的时间。 请验证您的自定义。


## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题

[WinPE︰ 添加软件包 （可选的组件参考）](winpe-add-packages--optional-components-reference.md)

 

 






