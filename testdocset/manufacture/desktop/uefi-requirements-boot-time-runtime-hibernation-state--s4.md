---
author: Justinha
Description: "（uefi） 要求︰ 启动时，运行时，休眠状态 (S4)"
ms.assetid: 8fad2f32-6ff5-49db-9d34-041485a34a4c
MSHAttr: PreferredLib:/library/windows/hardware
title: "（uefi） 要求︰ 启动时，运行时，休眠状态 (S4)"
ms.openlocfilehash: cb32653975fd2567f5642068703d453921c19d27
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="uefi-requirements-boot-time-runtime-hibernation-state-s4"></a>（uefi） 要求︰ 启动时，运行时，休眠状态 (S4)


本部分介绍 UEFI 和固件的要求，包括︰

-   引导时间要求

-   运行时要求

-   休眠状态 (S4) 要求

-   要求启用 UEFI 平台没有网吧点点通

## <a name="span-idboottimerequirementsspanspan-idboottimerequirementsspanspan-idboottimerequirementsspanboot-time-requirements"></a><span id="Boot_time_requirements"></span><span id="boot_time_requirements"></span><span id="BOOT_TIME_REQUIREMENTS"></span>引导时间要求


本部分介绍 UEFI 引导时间要求。

### <a name="span-iddisplayatboottimespanspan-iddisplayatboottimespanspan-iddisplayatboottimespandisplay-at-boot-time"></a><span id="Display_at_Boot_Time"></span><span id="display_at_boot_time"></span><span id="DISPLAY_AT_BOOT_TIME"></span>在启动时显示

控制台设备的平台，UEFI 2.0 规范要求的固件来实现简单的文本输出协议。 （可选） 固件还可以支持图形化的协议。 （uefi) 2.0 定义图形输出协议 (GOP) 和 EFI 1.1 定义通用图形适配器 (UGA) 协议。 Windows 支持所有三个协议，但每个协议与用户体验是不同的。 最佳的体验，如果固件实现了图形化的协议，Windows 建议并且倾向于 GOP。

Windows 需要用于呈现标志符号的非英语邮件资源的图形协议。 为此，固件必须支持︰

1.  一种图形化的协议 — — GOP 或 UGA。

2.  与 32 位像素颜色或使用 24 位像素颜色 800 x 600 显示器分辨率是 1024 x 768 显示分辨率。

如果固件不支持任何这些图形模式，Windows 仍然功能，但所有引导显示都恢复为文本模式和英语。

Windows 8.1、 Windows Server 2012 R2、 Windows 7，Windows Server 2008 R2 和 Windows Server 2008 要求 GOP 在启动期间显示的高分辨率、 动画图像。 如果 GOP 不可用，Windows 使用视频图形阵列 (VGA) 标准显示低分辨率的图像和简单的进度指示器。 为了这些 Windows 版本的最佳启动经验，无卡扩展槽密封的平台可以安全地使用图形模式下启用启动和消除过渡到文本模式。

只要固件启动管理器将传递到 Windows EFI 应用程序的执行，平台固件和固件启动管理器必须不使用帧缓存器出于何种目的。

### <a name="span-idinputatboottimespanspan-idinputatboottimespanspan-idinputatboottimespaninput-at-boot-time"></a><span id="Input_at_Boot_Time"></span><span id="input_at_boot_time"></span><span id="INPUT_AT_BOOT_TIME"></span>在启动时输入

控制台设备的平台，UEFI 2.0 规范要求的固件来实现简单的输入协议。 Windows 在启动过程中对本地键盘输入支持该协议。

### <a name="span-idnetworkbootspanspan-idnetworkbootspanspan-idnetworkbootspannetwork-boot"></a><span id="Network_Boot"></span><span id="network_boot"></span><span id="NETWORK_BOOT"></span>网络启动

Windows 实现对 EFI 预启动执行环境 (PXE) 基本代码协议的支持。 Windows 使用此协议通过网络引导和支持 Windows 部署服务 (WDS)。

### <a name="span-iddiskbootspanspan-iddiskbootspanspan-iddiskbootspandisk-boot"></a><span id="Disk_Boot"></span><span id="disk_boot"></span><span id="DISK_BOOT"></span>磁盘引导

Windows 需要包含 EFI 系统分区和 Windows 操作系统分区的磁盘块 I/O 协议和设备路径协议支持。

### <a name="span-idotherfirmwarebootrequirementsspanspan-idotherfirmwarebootrequirementsspanspan-idotherfirmwarebootrequirementsspanother-firmware-boot-requirements"></a><span id="Other_Firmware_Boot_Requirements"></span><span id="other_firmware_boot_requirements"></span><span id="OTHER_FIRMWARE_BOOT_REQUIREMENTS"></span>其他固件启动要求

为了确保正确操作，Windows 需要 EFI 固件，以遵守其指示的规范版本。 EFI 固件必须充分实现适当版本的 EFI 系统表、 EFI 引导服务和 EFI 运行时服务。 其他所需的特定协议和规格如下︰

-   **受信任的计算组 (TCG) EFI 规范**。 在 TCG EFI 平台和协议规范，必须实现所有 UEFI 平台具有受信任的平台模块 (TPM)。

-   **EFI\_PCI\_根\_BRIDGE\_IO\_协议**。 如果 Windows 引导配置数据 (BCD) 指定了 IEEE 1394 启动调试，Windows 将使用此协议。

## <a name="span-idruntimerequirementsspanspan-idruntimerequirementsspanspan-idruntimerequirementsspanruntime-requirements"></a><span id="Runtime_Requirements"></span><span id="runtime_requirements"></span><span id="RUNTIME_REQUIREMENTS"></span>运行时要求


Windows 在操作系统运行时将使用它 （uefi） 服务的减到最小，并在可能的情况下，依赖于运行库固件 ACPI 和 Windows 驱动程序等。 Windows 使用以下 UEFI 运行时服务之后调用 ExitBootServices() 管理 NVRAM 启动项目和硬件错误记录。

-   GetVariable

-   GetNextVariableName

-   SetVariable

-   QueryVariableInfo

## <a name="span-idhibernationstates4transitionrequirementsspanspan-idhibernationstates4transitionrequirementsspanspan-idhibernationstates4transitionrequirementsspanhibernation-state-s4-transition-requirements"></a><span id="Hibernation_State__S4__Transition_Requirements"></span><span id="hibernation_state__s4__transition_requirements"></span><span id="HIBERNATION_STATE__S4__TRANSITION_REQUIREMENTS"></span>休眠状态 (S4) 转换要求


本部分介绍了与过渡到休眠状态电源状态 (S4) 系统和固件内存要求。

### <a name="span-idsystemmemoryrequirementsspanspan-idsystemmemoryrequirementsspanspan-idsystemmemoryrequirementsspansystem-memory-requirements"></a><span id="System_Memory_Requirements"></span><span id="system_memory_requirements"></span><span id="SYSTEM_MEMORY_REQUIREMENTS"></span>系统内存要求

平台固件必须确保操作系统的物理内存在 S4 休眠状态转换，大小和位置是一致的。

操作系统的物理内存定义符合 ACPI 3.0 规范作为除**AddressRangeReserved**以外的内存类型的固件系统地址映射接口描述任何内存\[2\]， **AddressRangeUnusable** \[5\]，或**未定义**\[比 5 大的任何值\]。

### <a name="span-idfirmwarememoryrequirementsspanspan-idfirmwarememoryrequirementsspanspan-idfirmwarememoryrequirementsspanfirmware-memory-requirements"></a><span id="Firmware_Memory_Requirements"></span><span id="firmware_memory_requirements"></span><span id="FIRMWARE_MEMORY_REQUIREMENTS"></span>固件内存要求

在 UEFI 平台上，固件运行时内存必须一致 S4 休眠状态转换，大小和位置。 根据作为描述 GetMemoryMap() 引导服务，使用该属性的任何内存 （uefi） 规范定义了运行时内存**EFI\_内存\_运行时**。

## <a name="span-idrequirementstoenableuefiplatformswithoutcsmspanspan-idrequirementstoenableuefiplatformswithoutcsmspanspan-idrequirementstoenableuefiplatformswithoutcsmspanrequirements-to-enable-uefi-platforms-without-csm"></a><span id="Requirements_to_Enable_UEFI_Platforms_without_CSM"></span><span id="requirements_to_enable_uefi_platforms_without_csm"></span><span id="REQUIREMENTS_TO_ENABLE_UEFI_PLATFORMS_WITHOUT_CSM"></span>要求启用 UEFI 平台没有网吧点点通


第一代 64 位 UEFI 平台通常包含某种形式的有限的 BIOS 仿真，如网吧点点通，以保留运行 32 位的操作系统和操作系统不支持 （uefi） 的能力。 现有 Windows INT 10 视频 BIOS 函数依赖还要求网吧点点通。

要降低网吧点点通的需要并提高将来的启动时间，我们会与业界共同消除这种依赖关系，并鼓励对系统固件更改协作。

固件的要求︰

**GOP**。 Windows 使用 GOP 在操作系统运行时在启动时，用于获取帧缓冲区指针。 GOP 支持有必要替换支持 VGA 和避免在 Windows 的将来版本中网吧点点通的要求。

**EFI 封装服务**。 Windows 可以使用 EFI UpdateCapsule() 服务系统重新引导之后都会保留信息并将该信息传递到固件。 这将可能让系统报告和/或响应某些错误情况下，如果引导设备的操作系统已损坏或不可用。

### <a name="span-idfirmwarerecommendationsspanspan-idfirmwarerecommendationsspanspan-idfirmwarerecommendationsspanfirmware-recommendations"></a><span id="Firmware_recommendations"></span><span id="firmware_recommendations"></span><span id="FIRMWARE_RECOMMENDATIONS"></span>固件的建议

与固件制造商的注意︰ 我们建议，当禁用安全启动时，然后固件应触发为以前版本的 Windows 提供了更好的支持体验的以下操作︰

-   尽管不使用 BIOS 模式仿真启用 VGA 支持 CSM。

-   在开机自检过程中要显示哪些键打开启动菜单启用消息。

 

 





