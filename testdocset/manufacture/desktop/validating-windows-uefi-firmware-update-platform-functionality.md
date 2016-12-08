---
author: Justinha
Description: "本文档列出了需经过签名的关闭 Windows UEFI 固件更新平台功能的基本验证方案。 可以在此处下载规范。"
ms.assetid: 42e7c93e-3af3-496a-8fdf-ac97b4e85970
MSHAttr: PreferredLib:/library/windows/hardware
title: "验证 Windows UEFI 固件更新平台功能"
ms.openlocfilehash: a75a98cd9436b5b69904c86fbcb8d0b49d0765fb
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="validating-windows-uefi-firmware-update-platform-functionality"></a>验证 Windows UEFI 固件更新平台功能


本文档列出了需经过签名的关闭 Windows UEFI 固件更新平台功能的基本验证方案。 技术指标可从[此处](http://go.microsoft.com/fwlink/p/?linkid=523808)下载。

## <a name="span-idprerequisitesspanspan-idprerequisitesspanspan-idprerequisitesspan-prerequisites"></a><span id="_Prerequisites"></span><span id="_prerequisites"></span><span id="_PREREQUISITES"></span>系统必备组件


-   EFI 系统资源表 (ESRT) 的每个条目，您需要最新的固件版本为胶囊。 方案将为 X 引用最新版本。每个 ESRT 条目使用一个唯一的 GUID 标识。
-   为每个公开的 ESRT 条目，创建一个马蹄形包，其版本递增上面的步骤 1 中创建的包。 这些马蹄形称为 X + 1。
-   在模拟故障条件，如为其负载是没有签名或签名具有无效的 PK.胶囊帮助的马蹄形
-   请确保所有要使用的马蹄形进行了签名正确地从操作系统的角度来看、 编录签名和签名的固件，PK 签名。 除非您专门测试签名的情况下负 PK。 有关如何对胶囊或固件驱动程序包进行签名的详细信息的规范中的"签名固件驱动程序软件包"，请参阅。

## <a name="span-idhowtospanspan-idhowtospanspan-idhowtospanhow-to"></a><span id="How_To"></span><span id="how_to"></span><span id="HOW_TO"></span>如何


**安装新胶囊或重新安装以前安装的胶囊**

1.  打开设备管理器。
2.  找到表示固件的设备节点，它通常位于"固件"设备。
3.  右键单击您想要更新的固件设备。
4.  选择**更新驱动程序软件**。 将获取弹出菜单，提示"更新驱动程序软件-&lt;固件&gt;"。
5.  选择**浏览计算机以查找驱动程序软件**。
6.  在下一个窗口中，选择**让我从我的计算机上的设备驱动程序的列表中选择**。
7.  如果之前已安装了驱动程序，请从**显示兼容的硬件**框选择它。 如果不存在，选择**磁盘**并继续。 否则为选择**确定**并重新启动系统。
8.  如果选择**从磁盘安装**，则会弹出菜单标记为**从磁盘安装**。
9.  使用**浏览**转到包含您想要安装的固件胶囊的目录。
10. 在该目录中选择该 INF 文件并点击**确定**以安装。
11. 在安装期间，如果获取弹出窗口说︰ 未签名驱动程序，请继续操作并接受此驱动程序。
12. 系统将要求您重新启动。
13. 安装的固件胶囊后，您需要重新启动。 如果您想要安装多个胶囊的包，然后等待直到所有马蹄形安装，然后重新启动最终胶囊上重新启动。

**查询的版本和状态的详细信息︰**

-   运行 QueryVersionAndStatus.ps1 PowerShell (PS) 脚本来查询当前的固件版本，最后一次尝试固件版本和最后一次尝试的状态。

    **若要运行该脚本︰**

    1.  以管理员身份运行 PowerShell。
    2.  `Set-ExecutionPolicy -ExecutionPolicy Unrestricted -Force`（这仅有一次做。）
    3.  显示给定 GUID 的版本和状态的详细信息。 例如︰`.\QueryVersionAndStatus.ps1 6bd2efb9-23ab-4b4c-bc37-016517413e9a`
    4.  检查固件更新是否成功︰ 请参阅一节"验证固件更新的状态"规范文档中。 确保最后一次尝试状态和当前的版本与预期的版本匹配。
    5.  建议︰ 检查以确保您要更新的设备仍然会正常工作。
    6.  设置回退策略︰ 在某些情形下可能需要回滚固件。 回滚不生产方案。 为了能够回滚，必须创建注册表策略。 创建 REG\_HKEY 节点下的名称"策略"的 DWORD 项\_本地\_机\\系统\\开目前控制设置\\控件\\FirmwareResources\\{&lt;GUID&gt;} 并将策略注册表项的值设置为 1。 请注意 GUID 应替换从 ESRT 实际 GUID。

## <a name="span-idscenariosspanspan-idscenariosspanspan-idscenariosspanscenarios"></a><span id="Scenarios"></span><span id="scenarios"></span><span id="SCENARIOS"></span>方案


### <a name="span-ids1eachesrtentryissuccessfullyupdatablethroughcapsulespanspan-ids1eachesrtentryissuccessfullyupdatablethroughcapsulespanspan-ids1eachesrtentryissuccessfullyupdatablethroughcapsulespans1-each-esrt-entry-is-successfully-updatable-through-capsule"></a><span id="S1__Each_ESRT_entry_is_successfully_updatable_through_capsule"></span><span id="s1__each_esrt_entry_is_successfully_updatable_through_capsule"></span><span id="S1__EACH_ESRT_ENTRY_IS_SUCCESSFULLY_UPDATABLE_THROUGH_CAPSULE"></span>S1: ESRT 的每个条目是胶囊通过成功更新

为每个平台所支持的 ESRT 条目应完成以下步骤。 或换言之，系统固件和每个设备固件支持通过 UpdateCapsule 的更新固件。

**步骤**

1.  输入每个 ESRT 安装固件版本 X 胶囊。
2.  请确保安装了所有上述的马蹄形，则在重新启动之前。

**预期的结果**

固件更新应为每个已更新的 ESRT 项成功。 所有的 ESRT 条目，其试图更新，则请检查确认︰

-   当前固件版本 = X
-   上次尝试版本 = X
-   上次尝试状态 = 0 (状态\_成功)

### <a name="span-ids2thelatestfirmwareversionxisalsoupdatabletox1spanspan-ids2thelatestfirmwareversionxisalsoupdatabletox1spanspan-ids2thelatestfirmwareversionxisalsoupdatabletox1spans2-the-latest-firmware-version-x-is-also-updatable-to-x1"></a><span id="S2__The_latest_firmware_version_X_is_also_updatable_to_X_1_"></span><span id="s2__the_latest_firmware_version_x_is_also_updatable_to_x_1_"></span><span id="S2__THE_LATEST_FIRMWARE_VERSION_X_IS_ALSO_UPDATABLE_TO_X_1_"></span>S2︰ 最新的固件版本 X 也是可更新 X + 1

为每个平台所支持的 ESRT 条目应完成以下步骤。 或换言之，系统固件和每个设备固件支持通过 UpdateCapsule 的更新固件。

**步骤**

1.  完成上面的 S1 的方案。
2.  输入每个 ESRT 安装固件版本 X + 1 胶囊。

**预期的结果**

固件更新应为每个已更新的 ESRT 项成功。 所有的 ESRT 条目，其试图更新，则请检查确认︰

-   当前固件版本 = X + 1
-   上次尝试版本 = X + 1
-   上次尝试状态 = 0 (状态\_成功)

### <a name="span-ids3onfailurefirmwareupdatereturnstherightstatuscodeasdefinedinthespecificationspanspan-ids3onfailurefirmwareupdatereturnstherightstatuscodeasdefinedinthespecificationspanspan-ids3onfailurefirmwareupdatereturnstherightstatuscodeasdefinedinthespecificationspans3-on-failure-firmware-update-returns-the-right-status-code-as-defined-in-the-specification"></a><span id="S3__On_failure__firmware_update_returns_the_right_status_code_as_defined_in_the_specification_"></span><span id="s3__on_failure__firmware_update_returns_the_right_status_code_as_defined_in_the_specification_"></span><span id="S3__ON_FAILURE__FIRMWARE_UPDATE_RETURNS_THE_RIGHT_STATUS_CODE_AS_DEFINED_IN_THE_SPECIFICATION_"></span>S3︰ 失败时，固件更新返回适当的状态代码规范中定义

命名"UEFI 系统资源表定义"，表中包含标题"ESRT 上次尝试状态字段值"一节中定义的状态代码。

### <a name="span-ids31insufficientbatteryanduefisystemfirmwareupdatespanspan-ids31insufficientbatteryanduefisystemfirmwareupdatespanspan-ids31insufficientbatteryanduefisystemfirmwareupdatespans31-insufficient-battery-and-uefi-system-firmware-update"></a><span id="S3.1_Insufficient_Battery_and_UEFI_System_Firmware_update"></span><span id="s3.1_insufficient_battery_and_uefi_system_firmware_update"></span><span id="S3.1_INSUFFICIENT_BATTERY_AND_UEFI_SYSTEM_FIRMWARE_UPDATE"></span>S3.1 没有足够的电池和 UEFI 系统固件更新

**步骤**

1.  交流电源耗尽电池充电不超过 25%，然后插件。
2.  安装 UEFI 系统固件版本 X + 1 胶囊。 让我们假定当前的版本是 X。
3.  在重新引导之前请确保电池电量低于 25%

**预期的结果**

固件更新失败。 对应于系统固件的 ESRT 条目，则请检查确认︰

-   当前固件版本 = X
-   上次尝试版本 = X + 1
-   上次尝试状态 = 0xc00002de (状态\_INSUFFICIENT\_电源)

### <a name="span-ids32insufficientbatteryanddevicefirmwareupdatespanspan-ids32insufficientbatteryanddevicefirmwareupdatespanspan-ids32insufficientbatteryanddevicefirmwareupdatespans32-insufficient-battery-and-device-firmware-update"></a><span id="S3.2_Insufficient_Battery_and_Device_Firmware_update_"></span><span id="s3.2_insufficient_battery_and_device_firmware_update_"></span><span id="S3.2_INSUFFICIENT_BATTERY_AND_DEVICE_FIRMWARE_UPDATE_"></span>S3.2 没有足够的电池和设备固件更新

**步骤**

1.  交流电源耗尽电池充电不超过 25%，然后插件。
2.  X + 1 的固件版本的系统中安装所有受支持设备的马蹄的形。 我们假设给定设备的当前固件版本是 X。
3.  在重新引导之前确保电池电量是少于 25%。

**预期的结果**

固件更新失败。 所有的 ESRT 条目，其试图更新，则请检查确认︰

-   当前固件版本 = X
-   上次尝试版本 = X + 1
-   上次尝试状态 = 0xc00002de (状态\_INSUFFICIENT\_电源)

### <a name="span-ids33insufficientbatteryuefisystemanddevicefirmwareupdateatthesametimespanspan-ids33insufficientbatteryuefisystemanddevicefirmwareupdateatthesametimespanspan-ids33insufficientbatteryuefisystemanddevicefirmwareupdateatthesametimespans33-insufficient-battery-uefi-system-and-device-firmware-update-at-the-same-time"></a><span id="S3.3_Insufficient_Battery__UEFI_System_and_Device_Firmware_update_at_the_same_time"></span><span id="s3.3_insufficient_battery__uefi_system_and_device_firmware_update_at_the_same_time"></span><span id="S3.3_INSUFFICIENT_BATTERY__UEFI_SYSTEM_AND_DEVICE_FIRMWARE_UPDATE_AT_THE_SAME_TIME"></span>同时 S3.3 不足电池、 UEFI 系统和设备固件更新

**步骤**

1.  交流电源耗尽电池充电不超过 25%，然后插件。
2.  安装马蹄形 UEFI 系统固件和所有设备固件版本 X + 1。
3.  在重新引导之前确保电池电量是少于 25%。

**预期的结果**

系统固件和试图为其更新的所有设备固件，固件更新应该会失败。 所有的 ESRT 条目，其试图更新，则请检查确认︰

-   当前固件版本 = X
-   上次尝试版本 = X + 1
-   上次尝试状态 = 0xc00002de (状态\_INSUFFICIENT\_电源)

### <a name="span-ids34firmwareupdateshouldfailwhenthecapsuleisnotpksignedspanspan-ids34firmwareupdateshouldfailwhenthecapsuleisnotpksignedspanspan-ids34firmwareupdateshouldfailwhenthecapsuleisnotpksignedspans34-firmware-update-should-fail-when-the-capsule-is-not-pk-signed"></a><span id="S3.4_Firmware_update_should_fail_when_the_capsule_is_not_PK_signed"></span><span id="s3.4_firmware_update_should_fail_when_the_capsule_is_not_pk_signed"></span><span id="S3.4_FIRMWARE_UPDATE_SHOULD_FAIL_WHEN_THE_CAPSULE_IS_NOT_PK_SIGNED"></span>S3.4 固件更新胶囊不签名的 PK 时出现故障

为每个平台所支持的 ESRT 条目应完成以下步骤。 或换言之，系统固件和每个设备固件支持通过 UpdateCapsule 的更新固件。

**步骤**

1.  每个 ESRT 条目，创建的胶囊 X + 2 中，未签名的有效负载。
2.  安装马蹄形 X + 2。 让我们假定当前的版本是 X。

**预期的结果**

固件更新应该试图为其更新的 ESRT 条目失败。 所有的 ESRT 条目，其试图更新，则请检查确认︰

-   当前固件版本 = X
-   上次尝试版本 = X + 2
-   上次尝试状态 = 0xC0000022 (状态\_访问\_被拒绝)

### <a name="span-ids35firmwareupdateshouldfailwhenthecapsuleissignedwiththewrongpkcertificatespanspan-ids35firmwareupdateshouldfailwhenthecapsuleissignedwiththewrongpkcertificatespanspan-ids35firmwareupdateshouldfailwhenthecapsuleissignedwiththewrongpkcertificatespans35-firmware-update-should-fail-when-the-capsule-is-signed-with-the-wrong-pk-certificate"></a><span id="S3.5_Firmware_update_should_fail_when_the_capsule_is_signed_with_the_wrong_PK_certificate"></span><span id="s3.5_firmware_update_should_fail_when_the_capsule_is_signed_with_the_wrong_pk_certificate"></span><span id="S3.5_FIRMWARE_UPDATE_SHOULD_FAIL_WHEN_THE_CAPSULE_IS_SIGNED_WITH_THE_WRONG_PK_CERTIFICATE"></span>S3.5 固件更新发生故障时使用错误的 PK 证书进行了签名胶囊

为每个平台所支持的 ESRT 条目应完成以下步骤。 或换言之，系统固件和每个设备固件支持通过 UpdateCapsule 的更新固件。

**步骤**

1.  每个 ESRT 条目，创建 X + 2 胶囊、 签名密钥不正确或证书 （例如使用调试签名胶囊生产设备上的） 的有效负载。
2.  安装马蹄形 X + 2。 让我们假定当前的版本是 X。

**预期的结果**

固件更新应该试图为其更新的 ESRT 条目失败。 所有的 ESRT 条目，其试图更新，则请检查确认︰

-   当前固件版本 = X
-   上次尝试版本 = X + 2
-   上次尝试状态 = 0xC0000022 (状态\_访问\_被拒绝)

### <a name="span-ids36firmwareupdateshouldfailwhenthecapsulepayloadistamperedwithspanspan-ids36firmwareupdateshouldfailwhenthecapsulepayloadistamperedwithspanspan-ids36firmwareupdateshouldfailwhenthecapsulepayloadistamperedwithspans36-firmware-update-should-fail-when-the-capsule-payload-is-tampered-with"></a><span id="S3.6_Firmware_update_should_fail_when_the_capsule_payload_is_tampered_with"></span><span id="s3.6_firmware_update_should_fail_when_the_capsule_payload_is_tampered_with"></span><span id="S3.6_FIRMWARE_UPDATE_SHOULD_FAIL_WHEN_THE_CAPSULE_PAYLOAD_IS_TAMPERED_WITH"></span>S3.6 固件更新失败时马蹄形负载被篡改

为每个平台所支持的 ESRT 条目应完成以下步骤。 或换言之，系统固件和每个设备固件支持通过 UpdateCapsule 的更新固件。

**步骤**

1.  输入每个 ESRT 创建 X + 2 胶囊、 签名具有正确密钥或证书的有效负载。 然后打开固件的二进制文件和文件中翻转 1 或更多位数并保存此文件。
2.  重新生成 bin 文件并将 INF 文件的目录。
3.  安装马蹄形 X + 2。 让我们假定当前的版本是 X。

**预期的结果**

固件更新应该试图为其更新的 ESRT 条目失败。 所有的 ESRT 条目，其试图更新，则请检查确认︰

-   当前固件版本 = X
-   上次尝试版本 = X + 2
-   上次尝试状态 = 0xC0000022 (状态\_访问\_被拒绝) 或 0xC000007B (状态\_无效\_图像\_格式)

### <a name="span-ids37firmwaredoesnotallowrollbackbeyondthelowestsupportedfirmwareversionspanspan-ids37firmwaredoesnotallowrollbackbeyondthelowestsupportedfirmwareversionspanspan-ids37firmwaredoesnotallowrollbackbeyondthelowestsupportedfirmwareversionspans37-firmware-does-not-allow-rollback-beyond-the-lowestsupportedfirmwareversion"></a><span id="S3.7__Firmware_does_not_allow_rollback_beyond_the_LowestSupportedFirmwareVersion_"></span><span id="s3.7__firmware_does_not_allow_rollback_beyond_the_lowestsupportedfirmwareversion_"></span><span id="S3.7__FIRMWARE_DOES_NOT_ALLOW_ROLLBACK_BEYOND_THE_LOWESTSUPPORTEDFIRMWAREVERSION_"></span>S3.7︰ 固件不允许超过 LowestSupportedFirmwareVersion 的回滚

以下步骤也应为其他设备固件 （低优先级） 执行。

**步骤**

1.  对于 UEFI 系统固件，创建 X + 1 胶囊，使"LowestSupportedFirmwareVersion"中的系统固件的 ESRT 条目设置为 X + 1。
2.  安装 X + 1 胶囊，并确保更新成功。
3.  创建 UEFI 系统固件更新马蹄形，这样在 INF 中的版本为 X + 2 但实际固件二进制文件 X 版本。
4.  安装马蹄形 X + 2，然后重新启动系统。

**预期的结果**

固件更新失败。 对应于系统固件的 ESRT 条目，则请检查确认︰

-   当前固件版本 = X + 1
-   上次尝试版本 = X + 2
-   上次尝试状态 = 0xC0000059 (状态\_修订版\_不匹配)

### <a name="span-ids4seamlessrecoveryandfirmwareupdateifimplementedspanspan-ids4seamlessrecoveryandfirmwareupdateifimplementedspanspan-ids4seamlessrecoveryandfirmwareupdateifimplementedspans4-seamless-recovery-and-firmware-update-if-implemented"></a><span id="S4__Seamless_recovery_and_firmware_update__if_implemented__"></span><span id="s4__seamless_recovery_and_firmware_update__if_implemented__"></span><span id="S4__SEAMLESS_RECOVERY_AND_FIRMWARE_UPDATE__IF_IMPLEMENTED__"></span>S4︰ 无缝恢复和固件更新 （如果实现）

这种情况下因无缝恢复的实现从一个平台到另一个平台。 根据实现，验证可能需要创建坏马蹄形来强制系统进入恢复或切断电源更新过程当中或通过任何其他途径的 【 恢复流。

**预期的结果**

系统将启动至操作系统和固件更新应标记为失败。 UEFI 固件资源设备报告的版本不应该有变化。

### <a name="span-ids5firmwareupdateadherestotheuserexperienceuxrequirementspanspan-ids5firmwareupdateadherestotheuserexperienceuxrequirementspanspan-ids5firmwareupdateadherestotheuserexperienceuxrequirementspans5-firmware-update-adheres-to-the-user-experience-ux-requirement"></a><span id="S5__Firmware_Update_adheres_to_the_User_Experience__UX__requirement"></span><span id="s5__firmware_update_adheres_to_the_user_experience__ux__requirement"></span><span id="S5__FIRMWARE_UPDATE_ADHERES_TO_THE_USER_EXPERIENCE__UX__REQUIREMENT"></span>S5︰ 符合用户体验 (UX) 要求的固件更新

**步骤**

-   这种情况下可以执行任何上述情形导致一个成功的固件更新时进行验证。

**预期的结果**

用户体验是按照规范，请参阅"用户体验"一节。

-   仅有的文本在屏幕上显示的是"我们安装系统的更新，请等待"。 规范中提出，位于右坐标在屏幕上显示文本。
-   如规范中所述，将显示 OEM 徽标。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Windows UEFI 固件更新平台](http://go.microsoft.com/fwlink/p/?linkid=523808)

[（uefi） 验证选项 ROM 验证指南](uefi-validation-option-rom-validation-guidance.md)

 

 






