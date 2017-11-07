---
author: Justinha
Description: "创建数据映像使用 DISM"
ms.assetid: e182335f-fe0e-4e85-8c2b-807d22af6d4b
MSHAttr: PreferredLib:/library/windows/hardware
title: "创建数据映像使用 DISM"
ms.openlocfilehash: cf499f4ff64b46fbd5d3f63bef3ec96329e2970e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="create-a-data-image-using-dism"></a>创建数据映像使用 DISM


要在安装过程中向 Windows® 添加应用程序、 文件和其他资源，您可以创建数据映像。 通过使用部署映像服务和管理 (DISM) 工具，您可以创建其他 Windows 映像 (.wim) 文件只包含文件和您想要复制到 Windows 安装的应用程序。

数据映像，您可以添加︰

-   应用程序、 文件、 脚本和 windows 安装过程中的其他资源。

-   文件、 资源和其他数据添加到操作系统分区以外的分区。

**请注意**  
必须使用数据映像，只是为了将新文件添加到 Windows 安装。 不要使用数据映像替换现有的 Windows 文件。 覆盖操作系统数据不受支持。

 

以前的方法，将数据传输到 Windows 安装所需 $OEM$ 文件夹的使用。 仍然支持这些文件夹结构，但数据映像提供了将其他数据传输到 Windows 的更方便且更高效的方法。

在无人参与安装中，指定要安装的 Windows 映像`OSImage`在 Microsoft Windows 安装程序组件中设置。 您可以添加一个或多个`DataImage`Microsoft Windows 安装程序组件表示向系统中添加的额外数据图像的设置。 有关详细信息，请参阅 Windows® 无人参与安装参考。

**若要创建数据映像**

1.  找到您将创建数据映像的数据。

2.  打开命令提示符，作为管理员，或计算机启动到 Windows PE 打开 Windows PE 命令提示符窗口。

3.  使用 DISM 压缩数据文件到一个.wim 文件。 例如︰

    ``` syntax
    Dism /Capture-Image /ImageFile:c:\data\myData.wim /CaptureDir:C:\data\dataFiles /Name:MyData
    ```

    在此示例中，在 c︰ 驱动器下的一切\\数据\\数据文件的目录添加到.wim 文件和.wim 文件给出"MyData"的标签。 所有文件和文件夹在 c︰ 下的\\数据\\数据文件将解压缩到答案文件中指定的驱动器的根目录。

    有关如何使用 DISM 的详细信息，请参阅[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)。

4.  在 Windows 安装过程中，数据映像复制到可用的位置，如另一个分区或网络共享中。

**数据映像路径添加到答案文件**

1.  使用 Windows 系统映像管理器 (Windows SIM) 来创建一个应答文件，其中包含要安装的数据映像和安装位置的路径。

2.  Microsoft Windows 安装中添加\\`DataImage`设置为适当的配置将为您的环境。 例如︰ `windowsPE`。

3.  保存答案文件并关闭 Windows sim 卡。

    答案文件必须类似于以下示例︰

    ``` syntax
       <settings pass="windowsPE">
          <component name="Microsoft-Windows-Setup" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
             <ImageInstall>
                <DataImage wcm:action="add">
                   <InstallTo>
                      <DiskID>0</DiskID>
                      <PartitionID>1</PartitionID>
                   </InstallTo>
                   <InstallFrom>
                      <Credentials>
                         <Domain>Fabrikam</Domain>
                         <Username>MyUsername</Username>
                         <Password>MyPassword</Password>
                      </Credentials>
                   <Path>\\networkshare\share\MyData.wim</Path>
                   </InstallFrom>
                      <Order>1</Order>
                </DataImage>
             </ImageInstall>
          </component>
       </settings>
    ```

4.  运行 Setup.exe，指定答案文件的位置。 例如︰

    ``` syntax
    setup /unattend:C:\unattend.xml
    ```

所有文件和数据映像中指定的文件夹都解压缩到驱动器的根目录安装过程。 可执行文件和脚本不运行时将应用的数据图像;他们只被复制到该驱动器。 您可以使用`FirstLogonCommands`若要指定命令运行一个用户登录到计算机的第一次。 有关详细信息`FirstLogonCommands`，请参阅 Windows® 无人参与安装参考。

 

 





