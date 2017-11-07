---
author: Justinha
Description: "导出或导入默认的应用程序关联"
ms.assetid: 87eb7510-df1a-4e3f-9cd4-5400fa6e1a07
MSHAttr: PreferredLib:/library/windows/hardware
title: "导出或导入默认的应用程序关联"
ms.openlocfilehash: 40b314583d33d7a3c07e62d71c0719d348c8d339
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="export-or-import-default-application-associations"></a>导出或导入默认的应用程序关联


可以使用部署映像服务和管理 (DISM) 工具来更改文件扩展名或协议 Windows® 图像中的相关联的默认程序。

## <a name="span-idgeneratedefaultapplicationassociationsxmlfilespanspan-idgeneratedefaultapplicationassociationsxmlfilespanspan-idgeneratedefaultapplicationassociationsxmlfilespangenerate-default-application-associations-xml-file"></a><span id="Generate_Default_Application_Associations_XML_File"></span><span id="generate_default_application_associations_xml_file"></span><span id="GENERATE_DEFAULT_APPLICATION_ASSOCIATIONS_XML_FILE"></span>生成默认应用程序关联的 XML 文件


将 Windows 映像部署到测试计算机和配置的程序添加到映像中。 您可以登录到 Windows 并使用控制面板来选择您默认的应用程序关联。 您可以导出配置到网络共享或可移动媒体上的 XML 文件，以便您可以将其导入到 WIM 或 VHD 文件之前将其部署到目标计算机的默认应用程序关联。

**设置默认的应用程序关联**

1.  将 Windows 映像安装到一台测试计算机。 有关如何应用 Windows 映像的详细信息，请参阅[使用 DISM 应用图像](apply-images-using-dism.md)。

2.  启动测试计算机并完成 Windows 安装程序。

3.  单击**搜索**，单击**设置**，然后键入**默认程序**。 单击**默认程序**。

4.  通过文件扩展名或应用程序，您可以配置默认程序。 例如，若要设置查看应用程序打开的所有文件类型和它支持的协议所都用的默认程序作为安装的照片，单击**设置默认程序**，单击在程序列表中，查看应用程序中的照片，然后单击**设置此程序为默认值**。

**导出应用程序关联的默认设置**

1.  您的测试计算机上具有管理凭据中打开命令提示符。 如果使用非 Windows 8 的 Windows 的版本，使用部署工具命令提示符下使用 ADK 安装或导航到您的本地计算机上的 DISM 目录。

2.  将默认应用程序关联设置在测试计算机中导出到一个网络共享或 USB 驱动器上的.xml 文件。 例如，在命令提示符处键入以下命令︰

    ``` syntax
    Dism /Online /Export-DefaultAppAssociations:\\Server\Share\AppAssoc.xml
    ```

    其中：

    -   服务器是包含您将导出的默认应用程序关联设置共享的计算机的服务器的名称。

    -   共享是导出的默认应用程序关联设置共享的名称。

## <a name="span-idaddorremovedefaultapplicationassociationsettingstoawindowsimagespanspan-idaddorremovedefaultapplicationassociationsettingstoawindowsimagespanspan-idaddorremovedefaultapplicationassociationsettingstoawindowsimagespanadd-or-remove-default-application-association-settings-to-a-windows-image"></a><span id="Add_or_Remove_Default_Application_Association_Settings_to_a_Windows_Image"></span><span id="add_or_remove_default_application_association_settings_to_a_windows_image"></span><span id="ADD_OR_REMOVE_DEFAULT_APPLICATION_ASSOCIATION_SETTINGS_TO_A_WINDOWS_IMAGE"></span>添加或删除默认应用程序关联设置应用于 Windows 映像


在将其部署到目标计算机之前，可以更改 WIM 或 VHD 文件中的默认应用程序关联设置。 您还可以添加和删除联机映像的应用程序关联的默认设置。

**导入应用程序关联的默认设置**

1.  技术人员计算机上具有管理凭据中打开命令提示符。 如果使用非 Windows 8 的 Windows 的版本，使用部署工具命令提示符下使用 ADK 安装或导航到您的本地计算机上的 DISM 目录。

2.  从 WIM 或 VHD 文件安装的 Windows 映像。 例如，在命令提示符下键入以下命令︰

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\install.wim /Name:"Windows" /MountDir:C:\test\offline
    ```

3.  导入包含默认应用程序关联设置应用于 Windows 映像的.xml 文件。 例如，在命令提示符下键入以下命令︰

    ``` syntax
    Dism.exe /Image:C:\test\offline /Import-DefaultAppAssociations:\\Server\Share\AppAssoc.xml
    ```

    其中：

    -   服务器是包含您将导出的默认应用程序关联设置共享的计算机的服务器的名称。

    -   共享是导出的默认应用程序关联设置共享的名称。

**查看图像中的默认应用程序关联设置**

1.  技术人员计算机上具有管理凭据中打开命令提示符。 如果使用非 Windows 8 的 Windows 的版本，使用部署工具命令提示符下使用 ADK 安装或导航到您的本地计算机上的 DISM 目录。

2.  列出已应用到已装载的映像的应用程序关联。 例如，在命令提示符下，键入以下命令︰

    ``` syntax
    Dism.exe /Image:C:\test\offline /Get-DefaultAppAssociations
    ```

**删除应用程序关联的默认设置**

1.  技术人员计算机上具有管理凭据中打开命令提示符。 如果使用非 Windows 8 的 Windows 的版本，使用部署工具命令提示符下使用 ADK 安装或导航到您的本地计算机上的 DISM 目录。

2.  移除已添加到已装载的映像的自定义默认应用程序关联。 例如，在命令提示符下键入以下命令︰

    ``` syntax
    Dism.exe /Image:C:\test\offline /Remove-DefaultAppAssociations
    ```

 

 





