---
author: Justinha
Description: "添加和移除脱机 Windows 映像的驱动程序"
ms.assetid: 71651630-2e26-4174-8161-8f83b8ae4bc3
MSHAttr: PreferredLib:/library/windows/hardware
title: "添加和移除脱机 Windows 映像的驱动程序"
ms.openlocfilehash: 8bc27dda494a405404dee0bf8cb7272e5363bc7e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add-and-remove-drivers-to-an-offline-windows-image"></a>添加和移除脱机 Windows 映像的驱动程序


您可以使用部署映像服务和管理 (DISM) 工具来安装或删除脱机 Windows 映像中的驱动程序 (.inf) 文件。 您可以将无人参与的答案文件应用到已装载的.wim、.vhd 或.vhdx 文件中，或者可以添加，也可以直接通过使用命令提示符删除驱动程序。

当您使用 DISM 脱机映像中安装的设备驱动程序时，设备驱动程序添加到脱机映像中的驱动程序存储区。 启动映像时，插即用 (PnP) 运行，并且将在存储到计算机上相应的设备驱动程序相关联。

**请注意**  将驱动程序添加到 Windows 10 映像脱机，您必须使用运行 Windows 10、 Windows 服务器 2016年技术预览或 Windows 预安装环境 (WinPE) 的技术人员计算机 Windows 10。 从技术人员计算机运行任何其他操作系统的驱动程序添加到脱机 Windows 10 图像时，驱动程序签名验证可能会失败。


## <a name="to-add-drivers-to-an-offline-image-by-using-dism"></a>若要通过使用 DISM 将驱动程序添加到脱机映像

1.  在提升的命令提示符下，检索名称或要修改的映像的索引号。 例如，键入︰

    ``` syntax
    Dism /Get-ImageInfo /ImageFile:C:\test\images\install.wim
    ```

    对于指定 WIM 文件的大多数操作，需要索引或名称值为 对于 VHD 文件，您必须指定`/Index:1`。

2.  装入脱机 Windows 映像。 例如，键入︰

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\install.wim /Name:"Windows Drive" /MountDir:C:\test\offline
    ```

3.  将驱动程序添加到映像中。

    ``` syntax
    Dism /Image:C:\test\offline /Add-Driver /Driver:C:\drivers\mydriver.inf
    ```

    要安装所有的驱动程序从某个文件夹及其所有子文件夹，请指向该文件夹并使用**/recurse**选项。

    ``` syntax
    Dism /Image:C:\test\offline /Add-Driver /Driver:c:\drivers /Recurse
    ```

    **警告** 尽管 /Recurse 可能很方便，很容易膨胀与图像。 某些驱动程序包包括多个.inf 驱动程序包，通常有效负载从共享文件所在的文件夹。 安装过程中，每个.inf 驱动程序包扩展到一个单独的文件夹，每个都有有效载荷文件的副本。 我们看到其中有 900 MB 文件夹中的常见驱动程序将添加到图像时使用 /Recurse 选项添加 10 GB 的情况。

    要安装未签名驱动程序，请使用**/ForceUnsigned**替代基于 X64 的计算机上安装的驱动程序必须具有数字签名的要求。

    ``` syntax
    Dism /Image:C:\test\offline /Add-Driver /Driver:C:\drivers\mydriver.inf /ForceUnsigned
    ```

4.  查看 Windows 映像中的第三方驱动程序 (.inf) 文件的列表。 添加到 Windows 映像的驱动程序称为 Oem\*。 inf。 这是为了确保添加到计算机的新驱动程序命名的唯一。 例如，MyDriver1.inf 和 MyDriver2.inf 的文件被重命名为 Oem0.inf 和 Oem1.inf。

    ``` syntax
    Dism /Image:C:\test\offline /Get-Drivers 
    ```

5.  提交更改并卸载映像。

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\test\offline /Commit
    ```

## <a name="to-remove-drivers-from-an-offline-image-by-using-dism"></a>通过使用 DISM 脱机映像中删除驱动程序

1.  在提升的命令提示符下，检索名称或要修改的映像的索引号。

    ``` syntax
    Dism /Get-ImageInfo /ImageFile:C:\test\images\install.wim
    ```

    对于指定 WIM 文件的大多数操作，需要索引或名称值为 对于 VHD 文件，您必须指定`/Index:1`。

2.  装入脱机 Windows 映像。 例如︰

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\install.wim /Name:"Windows 10 Home" /MountDir:C:\test\offline
    ```

3.  从映像中删除特定的驱动程序。 可以在一个命令行删除多个驱动程序。

    ``` syntax
    Dism /Image:C:\test\offline /Remove-Driver /Driver:OEM1.inf /Driver:OEM2.inf
    ```

    **警告**  
    删除启动关键驱动程序程序包可以使脱机 Windows 映像无法启动。 有关详细信息，请参阅[DISM 驱动程序服务命令行选项](dism-driver-servicing-command-line-options-s14.md)。
     

4.  提交更改并卸载映像。

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\test\offline /Commit
    ```

## <a name="to-add-drivers-to-an-offline-windows-image-by-using-an-unattended-answer-file"></a>若要向脱机 Windows 映像中添加驱动程序，通过使用无人参与的答案文件

1.  找到要在 Windows 映像上安装设备驱动程序.inf 文件。

    **请注意**  
    在目录和子目录中的答案文件中引用的所有驱动程序添加到映像中。 您应管理答案文件和这些目录，以解决有关增加不必要的驱动程序包的图像的大小问题仔细。

2.  使用 Windows 系统映像管理器 (Windows SIM) 来创建一个应答文件，其中包含您想要安装的设备驱动程序的路径。

3.  Microsoft 的 Windows PnpCustomizationsNonWinPE 组件添加到答案文件中的**offlineServicing**配置阶段。

4.  **Microsoft 的 Windows PnpCustomizationsNonWinPE**在展开节点应答文件。 **DevicePaths**，用鼠标右键单击，然后选择**插入新 PathAndCredentials**。

    新的**PathAndCredentials**列表项出现。

5.  为每个您想要访问，请添加一个单独的**PathAndCredentials**列表项的位置。

6.  Microsoft 的 Windows PnpCustomizationsNonWinPE 组件中指定的路径的设备驱动程序和用于访问该文件，如果文件位于网络共享的凭据。

    **请注意**  
    您可以通过添加多个**PathAndCredentials**列表项包含多个设备驱动程序路径。 如果添加多个列表项，则必须增加每个路径的值的**键**。 例如，可以添加两个单独的驱动程序路径第一个路径**项**的值等于**1** ，第二条路径为**键**的值等于**2**。

7.  保存答案文件并退出 Windows sim 卡。 答案文件必须类似于以下示例。

    ``` syntax
    <?xml version="1.0" ?><unattend xmlns="urn:schemas-microsoft-com:asm.v3" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State">
       <settings pass="offlineServicing">
          <component name="Microsoft-Windows-PnpCustomizationsNonWinPE" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS">
             <DriverPaths>
                <PathAndCredentials wcm:keyValue="1">
                   <Path>\\networkshare\share\drivers</Path>
                   <Credentials>
                      <Domain>Fabrikam</Domain>
                      <Username>MyUserName</Username>
                      <Password>MyPassword</Password>
                   </Credentials>
                </PathAndCredentials>
             </DriverPaths>
          </component>
       </settings>
    </unattend>
    ```

8.  您想要安装的驱动程序为使用 DISM 将 Windows 映像装载。 例如，键入︰

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\install.wim /Index:1 /MountDir:C:\test\offline
    ```

    对于指定 WIM 文件的大多数操作，需要索引或名称值为 对于 VHD 文件，您必须指定`/Index:1`。

9.  使用 DISM 将答案文件应用到安装的 Windows 映像。 例如，键入︰

    ``` syntax
    DISM /Image:C:\test\offline /Apply-Unattend:C:\test\answerfiles\myunattend.xml
    ```

    有关如何应用答案文件的详细信息，请参阅[无人参与服务 DISM 命令行选项](dism-unattended-servicing-command-line-options.md)。

    在应答文件中的路径中引用的.inf 文件将添加到 Windows 映像。

10. 查看 Windows 映像中的第三方驱动程序 (.inf) 文件的列表。 添加到 Windows 映像的驱动程序称为 Oem\*。 inf。 这是为了确保所有新的驱动程序添加到计算机有唯一的名称。 例如，MyDriver1.inf 和 MyDriver2.inf 的文件被重命名为 Oem0.inf 和 Oem1.inf。

    例如，键入︰

    ``` syntax
    Dism /Image:C:\test\offline /Get-Drivers 
    ```

11. 卸载.wim 文件并提交所做的更改。 例如，键入︰

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\test\offline /Commit
    ```

如果您需要的 WinPE 查看本地硬盘驱动器或网络驱动程序，必须使用答案文件在**windowsPE**配置阶段，到 WinPE 驱动程序存储区中添加驱动程序，以反映所需的 WinPE 的启动关键驱动程序。 有关详细信息，请参阅[添加设备驱动程序与 Windows 安装过程中 Windows](add-device-drivers-to-windows-during-windows-setup.md)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[设备驱动程序和部署概述](device-drivers-and-deployment-overview.md)

[在 Windows 安装期间添加到 Windows 的设备驱动程序](add-device-drivers-to-windows-during-windows-setup.md)

[DISM 的部署 windows 映像服务和管理技术参考](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md)

 

 






