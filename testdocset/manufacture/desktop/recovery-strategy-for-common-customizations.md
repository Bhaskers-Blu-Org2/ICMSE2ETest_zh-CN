---
author: Justinha
Description: "默认按钮重置功能还原驱动 （通过 INF 软件包安装） 的程序和预装 Windows 应用程序。"
ms.assetid: 909227f2-8969-4ab3-b296-c54977a38977
MSHAttr: PreferredLib:/library/windows/hardware
title: "恢复组件"
ms.openlocfilehash: 454c842408cf7fb03a23ed1de32d44eb6e548172
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="recovery-components"></a>恢复组件


默认按钮重置功能还原驱动 （通过 INF 软件包安装） 的程序和预装 Windows 应用程序。 要配置还原其他自定义设置，如设置和 Windows 桌面应用程序的功能，将需要准备一个或多个包含自定义项的自定义软件包。 这些自定义程序包是资源调配包 (.ppkg) 的形式。

依靠以点击方式重置功能查找并自动恢复设置软件包位于 c: 文件夹中的\\恢复\\的自定义设置。

保护从软件包篡改或意外删除、 写/更改权限的 c:\\恢复\\自定义应限制为本地管理员用户组。

一些设置和自定义项不包含在资源调配的包。 相反，可以恢复其使用使用点击式应用无人参与文件重置扩展性脚本。 受这两个设置包和无人参与的设置，建议您指定它们使用的机制，不能两个之一。 若要了解详细信息，请参阅[如何按钮重置功能的工作](how-push-button-reset-features-work.md)。

## <a name="span-idcapturingclassicwindowsapplicationsusingwindowsuserstatemigrationtoolusmtsscanstatetoolspanspan-idcapturingwindowsdesktopapplicationsusingwindowsuserstatemigrationtoolusmtsscanstatetoolspanspan-idcapturingwindowsdesktopapplicationsusingwindowsuserstatemigrationtoolusmtsscanstatetoolspancapturing-windows-desktop-applications-using-windows-user-state-migration-tool-usmts-scanstate-tool"></a><span id="Capturing_Classic_Windows_applications_using_Windows_User_State_Migration_Tool__USMT__s_ScanState_tool"></span><span id="capturing_windows_desktop_applications_using_windows_user_state_migration_tool__usmt__s_scanstate_tool"></span><span id="CAPTURING_WINDOWS_DESKTOP_APPLICATIONS_USING_WINDOWS_USER_STATE_MIGRATION_TOOL__USMT__S_SCANSTATE_TOOL"></span>捕获 Windows 桌面应用程序，使用 Windows 用户状态迁移工具 (USMT) 的扫描状态工具


Windows 用户状态迁移工具 (USMT) ScanState.exe 已更新 Windows 10 支持捕获 Windows 桌面应用程序的应用程序中。 此功能可通过指定激活`/apps`选项。

当`/apps`扫描状态使用一套应用程序发现规则来确定什么应捕获，并将输出存储为参考设备数据映像供应包内的指定。 一般情况下，引用设备数据包含下列内容︰

-   使用 Microsoft Windows Installer 或其他安装程序安装 Windows 桌面应用程序
-   所有文件和文件夹在 Windows 命名空间外的 (之外的换而言之，\\窗口，\\程序文件\\程序文件 (x86)， \\ProgramData，和\\的用户)。 这仅适用于 Windows 安装的卷。
-   不捕获︰ Windows 应用程序。
-   不捕获︰ 用户的状态数据。

您还可以指定要包含或排除特定的文件、 文件夹和注册表设置的其他规则。 例如，如果您正在工厂在部署期间使用扫描状态，可能需要排除制造特定工具，以便它们不会还原时最终用户使用点击式重置功能。 若要指定其他规则，您需要迁移 XML 创作并指定`/i`选项时使用 ScanState.exe。

扫描状态的 /apps 选项还支持下列可选参数︰

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">参数</th>
<th align="left">使用</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><code>+/-sysdrive</code></td>
<td align="left">指定是否应捕获应用程序、 文件和文件夹在 Windows 命名空间外。
<p>如果<code>+sysdrive</code>指定，则在系统驱动器上的所有内容都是检查和资格要捕获发现规则。</p>
<p>如果<code>-sysdrive</code>指定，则只会将 Windows 命名空间中的内容检查和资格要捕获发现规则。</p>
<p><code>+sysdrive</code> 是默认值。</p></td>
</tr>
<tr class="even">
<td align="left"><code>+/-oeminfo</code></td>
<td align="left">指定是否特定于 OEM 的帮助和支持应捕获信息。
<p>如果<code>+oeminfo</code>指定，捕获 OEM 和支持信息。</p>
<p>如果<code>-oeminfo</code>指定，则不会捕获 OEM 和支持信息。</p>
<p><code>+oeminfo</code> 是默认值。</p></td>
</tr>
</tbody>
</table>

 

**重要**  
-   尽管按钮重置功能可以恢复多个资源调配的包，包中的只有一个可以包含参考设备数据映像捕获使用扫描状态。
-   只有在所有自定义设置已经应用于 PC 之后，应使用扫描状态。 它不支持将其他更改追加到现有的参考设备数据映像。
-   只能使用点击式重置功能和部署介质创建使用 Windows 图像处理和配置设计器 (ICD) 应用提供包捕获使用 ScanState.exe。 无法应用使用 DISM 或 USMT 的 LoadState.exe 这样的工具。
-   当您准备扫描状态捕获自定义项时，应排除 Windows Defender 设置，以防止可能会导致文件冲突的恢复过程中的可能的故障。 有关详细信息，请参阅步骤 1 中[部署按钮重置功能](deploy-push-button-reset-features.md)。

 

## <a name="span-idcreatingcustomizationpackagesusingwindowsicdspanspan-idcreatingcustomizationpackagesusingwindowsicdspanspan-idcreatingcustomizationpackagesusingwindowsicdspancreating-customization-packages-using-windows-icd"></a><span id="Creating_customization_packages_using__Windows_ICD"></span><span id="creating_customization_packages_using__windows_icd"></span><span id="CREATING_CUSTOMIZATION_PACKAGES_USING__WINDOWS_ICD"></span>创建自定义软件包使用 Windows ICD


对于自定义涉及设置适用于所有版本的 Windows 10 （包括 Windows 10 移动），您可以创建使用 Windows ICD 的供应包。

在生成的库存 (BTS) 情况下，如果已经捕捉了参考 PC 使用扫描状态工具，从 Windows 桌面应用程序可以导入到 Windows ICD 调配包的输出并指定应在恢复过程中恢复的其他设置。

## <a name="span-idrestoringsettingsusingunattendxmlandextensibilityscriptsspanspan-idrestoringsettingsusingunattendxmlandextensibilityscriptsspanrestoring-settings-using-unattendxml-and-extensibility-scripts"></a><span id="restoring_settings_using_unattend.xml_and_extensibility_scripts"></span><span id="RESTORING_SETTINGS_USING_UNATTEND.XML_AND_EXTENSIBILITY_SCRIPTS"></span>还原设置使用 unattend.xml 和可扩展性的脚本


不能使用资源调配包还原大多数设置配置为使用 unattend.xml 和其他配置文件 (例如 oobe.xml，LayoutModification.xml)。 相反，您需要使用点击式重新设置扩展点来恢复过程中恢复它们。 这些扩展性点允许您运行脚本，它可以︰

-   已恢复操作系统中注入 unattend.xml
-   复制到恢复操作系统的其他配置文件和资源

**重要**  
-   不应使用 unattend.xml （或其他机制） 启动到审核模式恢复的操作系统。 已恢复的操作系统必须保留已配置为启动到 OOBE。
-   配置文件和资源的需要恢复的副本必须放在 c:\\恢复\\OEM。 此文件夹中的内容不被修改的按钮重置功能和自动备份到使用**恢复驱动器创建**实用程序创建恢复媒体。 为了保护 unattend.xml 和配置文件/资产从篡改或意外删除、 写/更改权限的 c:\\恢复\\OEM 应限制为本地管理员用户组。

 

若要了解如何创建要使用的扩展点运行的脚本，请参阅[添加脚本的按钮重置功能](add-a-script-to-push-button-reset-features.md)。

若要了解如何使用扫描状态捕获并存储在 c︰ 下的得到 PPKG\\恢复\\自定义项，则自动恢复期间 PBR，请参阅[部署按钮重置功能使用扫描状态](deploy-push-button-reset-features.md)。

## <a name="span-idrecoverystrategiesforcommoncustomizationsspanspan-idrecoverystrategiesforcommoncustomizationsspanspan-idrecoverystrategiesforcommoncustomizationsspanrecovery-strategies-for-common-customizations"></a><span id="Recovery_strategies_for_common_customizations"></span><span id="recovery_strategies_for_common_customizations"></span><span id="RECOVERY_STRATEGIES_FOR_COMMON_CUSTOMIZATIONS"></span>常见的自定义的恢复战略


下表列出了常见的自定义的用户体验 Windows 工程指南 (UX WEG) 以及那些覆盖 OEM 策略文档 (OPD) 中所述的恢复策略。 有关这些自定义项的最新详细信息，请参阅最新版本的用户体验 WEG 和 OPD。

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">自定义项</th>
<th align="left">如何配置</th>
<th align="left">在 PBR 可以如何还原</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">OOBE – HID 配对</td>
<td align="left">在设置<code>&lt;hidSetup&gt;</code>OOBE.xml 和图像 （如.png 文件） 部分</td>
<td align="left">使用 PBR 扩展性脚本来从 C:\Recovery\OEM 还原 OOBE.xml 和图像</td>
</tr>
<tr class="even">
<td align="left">OOBE – OEM 最终用户许可协议</td>
<td align="left"><code>&lt;Eulafilename&gt;</code> 设置在 OOBE.xml 和许可术语存储在 %WINDIR%\System32\Oobe\Info 下的.rtf 文件</td>
<td align="left">使用 PBR 扩展性脚本来从 C:\Recovery\OEM 还原 OOBE.xml 和.rtf 文件</td>
</tr>
<tr class="odd">
<td align="left">OOBE – Preconfigured 语言和时区</td>
<td align="left">设置在<code>&lt;defaults&gt;</code>的 OOBE.xml 部分</td>
<td align="left">使用 PBR 扩展性脚本来从 C:\Recovery\OEM 还原 OOBE.xml</td>
</tr>
<tr class="even">
<td align="left">OOBE – 隐藏移动宽带页</td>
<td align="left">Microsoft 的 Windows WwanUI |在 unattend.xml NotInOOBE 设置</td>
<td align="left">使用 PBR 扩展性脚本来从 C:\Recovery\OEM 还原 unattend.xml</td>
</tr>
<tr class="odd">
<td align="left">OOBE – OEM 注册页</td>
<td align="left">在设置&lt;注册&gt;的 OOBE.xml 和 HTML 文件中进行链接的部分</td>
<td align="left">使用 PBR 扩展性脚本来从 C:\Recovery\OEM 还原 OOBE.xml 和 HTML 文件</td>
</tr>
<tr class="even">
<td align="left">开始-固定拼贴和组</td>
<td align="left">存储在 %SYSTEMDRIVE%\Users\Default\AppData\Local\Microsoft\Windows\Shell 或 Microsoft Windows 外壳程序设置下的设置 LayoutModification.xml |在 unattend.xml StartTiles</td>
<td align="left">使用 PBR 扩展性脚本来从 C:\Recovery\OEM 还原 LayoutModification.xml 或 unattend.xml</td>
</tr>
<tr class="odd">
<td align="left">开始-Prepopulated 常用程序列表</td>
<td align="left">存储在 %SYSTEMDRIVE%\Users\Default\AppData\Local\Microsoft\Windows\Shell 下的 LayoutModification.xml</td>
<td align="left">使用 PBR 扩展性脚本来还原从 C:\Recovery\OEM LayoutModification.xml</td>
</tr>
<tr class="even">
<td align="left">统一体 – 板型</td>
<td align="left">在 unattend.xml 设置︰
<p>• Microsoft Windows 部署 |DeviceForm</p>
<p>• Microsoft Windows GPIOButtons |ConvertibleSlateMode</p></td>
<td align="left">使用 PBR 扩展性脚本来从 C:\Recovery\OEM 还原 unattend.xml</td>
</tr>
<tr class="odd">
<td align="left">统一体 – 默认模式</td>
<td align="left">Microsoft Windows 外壳程序安装 |在 unattend.xml SignInMode 设置</td>
<td align="left">使用 PBR 扩展性脚本来从 C:\Recovery\OEM 还原 unattend.xml</td>
</tr>
<tr class="even">
<td align="left">台式机主板 – 默认值和其他强调文字颜色</td>
<td align="left">RunSynchronous 命令中 unattend.xml 这会增加注册表 HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Themes\Accents AGRB 十六进制颜色值</td>
<td align="left">使用 PBR 扩展性脚本来从 C:\Recovery\OEM 还原 unattend.xml</td>
</tr>
<tr class="odd">
<td align="left">桌面背景图像</td>
<td align="left">Microsoft Windows 外壳程序安装 |主题 |DesktopBackground unattend.xml 和图像 （例如.jpg/.png/.bmp 文件） 中的设置</td>
<td align="left">使用 PBR 扩展性脚本来从 C:\Recovery\OEM 还原 unattend.xml 和背景图像文件</td>
</tr>
<tr class="even">
<td align="left">台式机主板 – 固定任务栏项</td>
<td align="left">在 Microsoft Windows 外壳程序安装设置 |在 unattend.xml 和快捷方式 (.lnk) TaskbarLinks %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs\ 下的某个文件夹中存储的文件</td>
<td align="left">使用 PBR 扩展性脚本来从 C:\Recovery\OEM 还原 unattend.xml 和.lnk 文件</td>
</tr>
<tr class="odd">
<td align="left">台式机主板-系统托盘图标</td>
<td align="left">在 Microsoft Windows 外壳程序安装设置 |在 unattend.xml NotificationArea</td>
<td align="left">使用 PBR 扩展性脚本来从 C:\Recovery\OEM 还原 unattend.xml</td>
</tr>
<tr class="even">
<td align="left">移动宽带-重命名"WiFi"到"WLAN"在网络列表</td>
<td align="left">Microsoft 的 Windows SystemSettings |在 unattend.xml WiFiToWlan 设置</td>
<td align="left">使用 PBR 扩展性脚本来从 C:\Recovery\OEM 还原 unattend.xml</td>
</tr>
<tr class="odd">
<td align="left">移动宽带--在设置中启用网络选择控件</td>
<td align="left">Microsoft 的 Windows SystemSettings |在 unattend.xml DisplayNetworkSelection 设置</td>
<td align="left">使用 PBR 扩展性脚本来从 C:\Recovery\OEM 还原 unattend.xml</td>
</tr>
<tr class="even">
<td align="left">PC 设置 – 设置预安装应用程序</td>
<td align="left">设置应用程序预安装的方式与任何其他应用程序中，相同和设置中会自动显示。 在应用程序清单中声明的能力确定其是否为设置应用程序。</td>
<td align="left">与其他预安装的应用程序一起自动恢复</td>
</tr>
<tr class="odd">
<td align="left">默认的浏览器和协议处理程序</td>
<td align="left">默认应用程序关联设置 XML 文件导入使用 DISM 中的 /Import-DefaultAppAssociations 命令</td>
<td align="left">使用 PBR 扩展性脚本来重新导入的 XML 的使用 DISM C:\Recovery\OEM</td>
</tr>
<tr class="even">
<td align="left">在联系技术支持应用程序的支持信息</td>
<td align="left">在 Microsoft Windows 外壳程序安装设置 |Unattend.xml 和 logo.bmp 文件中的 OEMInformation</td>
<td align="left">使用 PBR 扩展性脚本来从 C:\Recovery\OEM 还原 unattend.xml 和.bmp 文件</td>
</tr>
<tr class="odd">
<td align="left">存储内容修饰符</td>
<td align="left">Microsoft 的 Windows-存储-客户端的 UI |在 unattend.xml StoreContentModifier 设置</td>
<td align="left">使用 PBR 扩展性脚本来从 C:\Recovery\OEM 还原 unattend.xml</td>
</tr>
<tr class="even">
<td align="left">Windows 桌面应用程序 （包括通过 setup.exe 安装的驱动程序小程序）</td>
<td align="left">MSI 或自定义安装程序</td>
<td align="left">扫描状态用于捕获和存储 C:\Recovery\Customizations，自动恢复期间 PBR 下的生成 PPKG。</td>
</tr>
<tr class="odd">
<td align="left">RDX 内容</td>
<td align="left">有关详细信息，请参见用户体验 WEG</td>
<td align="left">不应在 PBR 恢复</td>
</tr>
</tbody>
</table>

 

 

 





