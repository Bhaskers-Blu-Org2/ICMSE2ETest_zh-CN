---
author: Justinha
Description: "自动执行 Windows 安装程序"
ms.assetid: 882a3774-d0c3-405f-af31-2b9a5d1458d5
MSHAttr: PreferredLib:/library/windows/hardware
title: "自动执行 Windows 安装程序"
ms.openlocfilehash: 0811a566f920a01fbeb30302f37b4b34de552042
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="automate-windows-setup"></a>自动执行 Windows 安装程序


您可以防止来自 Windows® 安装程序的用户界面 (UI) 页面的部分或全部显示在安装过程中。 Windows 安装程序的默认行为是显示安装程序的用户界面，如果有任何必需的设置不正确或为空。

## <a name="span-iduseananswerfilewhileinstallingwindowsspanspan-iduseananswerfilewhileinstallingwindowsspanspan-iduseananswerfilewhileinstallingwindowsspanuse-an-answer-file-while-installing-windows"></a><span id="Use_an_answer_file_while_installing_Windows"></span><span id="use_an_answer_file_while_installing_windows"></span><span id="USE_AN_ANSWER_FILE_WHILE_INSTALLING_WINDOWS"></span>在安装 Windows 时使用的应答文件


可以使用答案文件自动完成 Windows 安装︰

**使用 USB 闪存驱动器**

1.  使用示例答案文件或创建您自己与 Windows 系统映像管理器 （Windows sim 卡）。

2.  将文件保存为**Autounattend.xml** USB 闪存驱动器的根目录。

3.  在新 PC 上，放在 Windows 产品 DVD 和 USB 闪存驱动器，然后启动计算机。 选择任何其他答案文件时，Windows 安装程序搜索此文件。

**选择答案文件**

-   您可以在安装过程中选择特定的应答文件通过引导至 Windows 预安装环境中，并使用**setup.exe**命令及**/unattend:***文件名*选项。

对于示例答案文件和用于自动化安装设置的列表，请参阅设置自动执行 Windows 安装程序。

## <a name="span-idsampleanswerfilesspanspan-idsampleanswerfilesspanspan-idsampleanswerfilesspansample-answer-files"></a><span id="Sample_answer_files"></span><span id="sample_answer_files"></span><span id="SAMPLE_ANSWER_FILES"></span>示例答案文件


下面的示例文件包含 Windows 评估和部署工具包 (Windows ADK) 中的以下文件夹中︰

C:\\程序文件 (x86)\\窗口工具包\\8.0\\评估和部署工具包\\部署工具\\样本\\无人参与的。

## <a name="span-idlistofsettingsspanspan-idlistofsettingsspanspan-idlistofsettingsspanlist-of-settings"></a><span id="List_of_settings"></span><span id="list_of_settings"></span><span id="LIST_OF_SETTINGS"></span>设置列表


以下是使用这些答案文件中的设置列表︰

-   Windows 安装程序语言设置︰ Microsoft 的 Windows-国际的核心-WinPE\\[UILanguage](http://go.microsoft.com/fwlink/?LinkId=224328)和 Microsoft 的 Windows-国际的核心-WinPE\\SetupUILanguage\\[UILanguage](http://go.microsoft.com/fwlink/?LinkId=224329)。

-   产品密钥︰ Microsoft Windows 安装程序\\UserData\\的产品密钥\\[键](http://go.microsoft.com/fwlink/?LinkId=224330)。

## <a name="span-idautomatingwindowssetupspanspan-idautomatingwindowssetupspanspan-idautomatingwindowssetupspanautomating-windows-setup"></a><span id="Automating_Windows_Setup"></span><span id="automating_windows_setup"></span><span id="AUTOMATING_WINDOWS_SETUP"></span>自动执行 Windows 安装程序


要自动完成 Windows 安装程序，添加到无人参与安装答案文件每个下面的 Windows 安装程序页设置。 当配置 Windows 安装程序页的设置时，Windows 安装程序将跳过该页。

### <a name="span-idlanguageregionandinputmethodselectionpagespanspan-idlanguageregionandinputmethodselectionpagespanspan-idlanguageregionandinputmethodselectionpagespanlanguage-region-and-input-method-selection-page"></a><span id="Language__Region__and_Input_Method_Selection_Page_"></span><span id="language__region__and_input_method_selection_page_"></span><span id="LANGUAGE__REGION__AND_INPUT_METHOD_SELECTION_PAGE_"></span>语言、 区域和输入的法选择页

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">设置</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Microsoft 的 Windows-国际的核心-WinPE |[UILanguage](http://go.microsoft.com/fwlink/?LinkId=224328)</p></td>
<td align="left"><p>指定要安装的 Windows 操作系统上使用的默认语言。</p></td>
</tr>
<tr class="even">
<td align="left"><p>Microsoft 的 Windows-国际的核心-WinPE |SetupUILanguage |[UILanguage](http://go.microsoft.com/fwlink/?LinkId=224329)</p></td>
<td align="left"><p>指定要 Windows 安装过程中使用的默认语言。 安装过程中，Windows 安装程序在选定的语言显示安装进度。</p></td>
</tr>
</tbody>
</table>

 

**请注意**  
当您的 Windows 安装程序使用 Autounattend.xml 文件并依赖于隐式应答文件搜索时，在安装程序中的语言选择页不显示，即使明确不配置语言设置应答文件中。 关于模糊答案文件的详细信息，请参阅[Windows 安装程序自动化概述](windows-setup-automation-overview.md)。

 

### <a name="span-idtypeyourproductkeyforactivationpagespanspan-idtypeyourproductkeyforactivationpagespanspan-idtypeyourproductkeyforactivationpagespantype-your-product-key-for-activation-page"></a><span id="Type_your_Product_Key_for_Activation_Page"></span><span id="type_your_product_key_for_activation_page"></span><span id="TYPE_YOUR_PRODUCT_KEY_FOR_ACTIVATION_PAGE"></span>键入产品密钥进行激活页上

产品密钥必须与要安装的 Windows 版本相匹配。 有关详细信息，请参阅[使用产品密钥和激活](work-with-product-keys-and-activation-auth-phases.md)。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">设置</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Microsoft Windows 安装程序 |UserData |产品密钥 |[密钥](http://go.microsoft.com/fwlink/?LinkId=224330)</p></td>
<td align="left"><p>指定用于将 Windows 安装的产品密钥。</p></td>
</tr>
<tr class="even">
<td align="left"><p>Microsoft Windows 安装程序 |ImageInstall |OSImage |InstallFrom |元数据 |（[键](http://go.microsoft.com/fwlink/?LinkId=252771)和[值](http://go.microsoft.com/fwlink/?LinkId=252772)）。</p></td>
<td align="left"><p>键和值一起使用来选择要安装的特定 Windows 映像。 所需的某些 Windows Server® 2012年版本。</p>
<p>可以通过使用 DISM /Get-ImageInfo 命令来获取图像信息。 有关详细信息，请参阅[图像管理命令行选项](http://go.microsoft.com/fwlink/?LinkId=208186)。</p></td>
</tr>
</tbody>
</table>

 

### <a name="span-idacceptmicrosoftsoftwarelicensetermspagespanspan-idacceptmicrosoftsoftwarelicensetermspagespanspan-idacceptmicrosoftsoftwarelicensetermspagespanaccept-microsoft-software-license-terms-page"></a><span id="Accept_Microsoft_Software_License_Terms_Page"></span><span id="accept_microsoft_software_license_terms_page"></span><span id="ACCEPT_MICROSOFT_SOFTWARE_LICENSE_TERMS_PAGE"></span>接受 Microsoft 软件许可条款页

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">设置</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Microsoft Windows 安装程序 |UserData |[AcceptEula](http://go.microsoft.com/fwlink/?LinkId=224331)</p></td>
<td align="left"><p>指定是否在 Windows 安装过程中接受 Microsoft 许可软件条款。</p></td>
</tr>
</tbody>
</table>

 

### <a name="span-idselectupgradeorcustominstallationpagespanspan-idselectupgradeorcustominstallationpagespanspan-idselectupgradeorcustominstallationpagespanselect-upgrade-or-custom-installation-page"></a><span id="Select_Upgrade_or_Custom_Installation_Page"></span><span id="select_upgrade_or_custom_installation_page"></span><span id="SELECT_UPGRADE_OR_CUSTOM_INSTALLATION_PAGE"></span>选择升级或自定义安装页

默认情况下，使用答案文件时，不显示此页，并且 Windows 配置为新的安装。 若要将 Windows 配置为升级，添加以下设置︰

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">设置</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Microsoft Windows 安装程序 |UpgradeData |[升级](http://go.microsoft.com/fwlink/?LinkId=224332)</p></td>
<td align="left"><p>指定出现的安装是从以前版本的 Windows 升级而来。</p></td>
</tr>
</tbody>
</table>

 

### <a name="span-idspecifywheretoinstallwindowspagespanspan-idspecifywheretoinstallwindowspagespanspan-idspecifywheretoinstallwindowspagespanspecify-where-to-install-windows-page"></a><span id="Specify_Where_to_Install_Windows_Page"></span><span id="specify_where_to_install_windows_page"></span><span id="SPECIFY_WHERE_TO_INSTALL_WINDOWS_PAGE"></span>指定要安装 Windows 页面的位置

您可以指定准确的磁盘 ID 和分区 ID，也可以将 Windows 安装到第一个可用的分区。 要预配置分区，可能还需要配置的驱动器分区。 有关完整的 XML 示例建议的分区配置，请参阅[如何 Configure UEFI/GPT-Based 硬盘分区](http://go.microsoft.com/fwlink/?LinkId=214261)或[如何 Configure BIOS/MBR-Based 硬盘分区](http://go.microsoft.com/fwlink/?LinkId=214260)。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">设置</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Microsoft Windows 安装程序 |ImageInstall |OSImage |InstallTo |[DiskID](http://go.microsoft.com/fwlink/?LinkId=224334)</p></td>
<td align="left"><p>指定将在其中安装 Windows 的磁盘。</p></td>
</tr>
<tr class="even">
<td align="left"><p>Microsoft Windows 安装程序 |ImageInstall |OSImage |InstallTo |[PartitionID](http://go.microsoft.com/fwlink/?LinkId=224335)</p></td>
<td align="left"><p>指定将在其中安装 Windows 的分区。</p></td>
</tr>
</tbody>
</table>

 

-或者-

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">设置</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Microsoft Windows 安装程序 |ImageInstall |OSImage |[InstallToAvailablePartition](http://go.microsoft.com/fwlink/?LinkId=224335)</p></td>
<td align="left"><p>指定第一个可用的分区上安装 Windows。</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idsettingstousewithunattendedwindowsdeploymentservicesspanspan-idsettingstousewithunattendedwindowsdeploymentservicesspanspan-idsettingstousewithunattendedwindowsdeploymentservicesspansettings-to-use-with-unattended-windows-deployment-services"></a><span id="Settings_to_Use_with_Unattended_Windows_Deployment_Services"></span><span id="settings_to_use_with_unattended_windows_deployment_services"></span><span id="SETTINGS_TO_USE_WITH_UNATTENDED_WINDOWS_DEPLOYMENT_SERVICES"></span>设置应用于使用无人参与的 Windows 部署服务


在部署时使用 Windows 部署服务窗口，每个设置中添加以下各节到无人参与安装答案文件。 这些都是无人参与的安装所需的唯一设置。

### <a name="span-idselectalanguageandlocalepagespanspan-idselectalanguageandlocalepagespanspan-idselectalanguageandlocalepagespanselect-a-language-and-locale-page"></a><span id="Select_a_Language_and_Locale_Page"></span><span id="select_a_language_and_locale_page"></span><span id="SELECT_A_LANGUAGE_AND_LOCALE_PAGE"></span>选择语言和区域设置页

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">设置</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Microsoft 的 Windows-国际的核心-WinPE |SetupUILanguage |[UILanguage](http://go.microsoft.com/fwlink/?LinkId=224337)</p></td>
<td align="left"><p>指定要 Windows 安装过程中使用的默认语言。</p></td>
</tr>
</tbody>
</table>

 

### <a name="span-idprovidewindowsdeploymentservicescredentialspagespanspan-idprovidewindowsdeploymentservicescredentialspagespanspan-idprovidewindowsdeploymentservicescredentialspagespanprovide-windows-deployment-services-credentials-page"></a><span id="Provide_Windows_Deployment_Services_Credentials_Page"></span><span id="provide_windows_deployment_services_credentials_page"></span><span id="PROVIDE_WINDOWS_DEPLOYMENT_SERVICES_CREDENTIALS_PAGE"></span>提供 Windows 部署服务凭据页

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">设置</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Microsoft Windows 安装程序 |WindowsDeploymentServices |[登录](http://go.microsoft.com/fwlink/?LinkId=224338)</p></td>
<td align="left"><p>指定用于 Windows 部署服务登录凭据并指定在何种情况下显示的用户界面进行登录。</p></td>
</tr>
</tbody>
</table>

 

### <a name="span-idselectanimagetoinstallpagespanspan-idselectanimagetoinstallpagespanspan-idselectanimagetoinstallpagespanselect-an-image-to-install-page"></a><span id="Select_an_Image_to_Install_Page"></span><span id="select_an_image_to_install_page"></span><span id="SELECT_AN_IMAGE_TO_INSTALL_PAGE"></span>选择要安装页上的图像

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">设置</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Microsoft Windows 安装程序 |WindowsDeploymentServices |[ImageSelection](http://go.microsoft.com/fwlink/?LinkId=224339)</p></td>
<td align="left"><p>指定要安装的映像和位置，安装位置，以及是否显示用户界面。</p></td>
</tr>
</tbody>
</table>

 

### <a name="span-idspecifywheretoinstallwindowspagespanspan-idspecifywheretoinstallwindowspagespanspan-idspecifywheretoinstallwindowspagespanspecify-where-to-install-windows-page"></a><span id="Specify_Where_to_Install_Windows_Page"></span><span id="specify_where_to_install_windows_page"></span><span id="SPECIFY_WHERE_TO_INSTALL_WINDOWS_PAGE"></span>指定要安装 Windows 页面的位置

这些设置假定您正在安装到的分区的磁盘驱动器。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">设置</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Microsoft Windows 安装程序 |WindowsDeploymentServices |ImageSelection |InstallTo |[DiskID](http://go.microsoft.com/fwlink/?LinkId=224340)</p></td>
<td align="left"><p>指定该图像是要安装的磁盘的磁盘 ID。</p></td>
</tr>
<tr class="even">
<td align="left"><p>Microsoft Windows 安装程序 |WindowsDeploymentServices |ImageSelection |InstallTo |[PartitionID](http://go.microsoft.com/fwlink/?LinkId=224342)</p></td>
<td align="left"><p>指定图像将被安装到的分区的分区 ID。</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[用于自动执行 OOBE 设置](settings-for-automating-oobe.md)

[Windows 安装程序技术参考](windows-setup-technical-reference.md)

 

 






