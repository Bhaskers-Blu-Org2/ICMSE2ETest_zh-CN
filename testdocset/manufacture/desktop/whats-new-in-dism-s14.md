---
author: Justinha
Description: What's New in DISM
ms.assetid: f1b463c0-96b5-4ad2-afac-53f9baf475a3
MSHAttr: PreferredLib:/library/windows/hardware
title: What's New in DISM
ms.openlocfilehash: 8b6db528d19ed4cae44ee6f62f3538bcd526a63c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="whats-new-in-dism"></a>DISM 中的新增功能


DISM Windows 10 中的支持新功能︰

-   [Windows 图像处理和配置设计器](https://msdn.microsoft.com/library/windows/hardware/dn916113)和相关的工具。

-   **全闪存更新 (。FFU)**: DISM 支持完整的闪存更新 (。FFU) 格式，它捕获应用整个驱动器，包括分区信息。 这样可使部署更快、 更方便。

    若要了解详细信息，请参阅[WIM vs FFU 图像文件格式](wim-vs-ffu-image-file-formats.md)和**/Apply-FFU**和**/Split-FFU**在[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)。

-   **功能**︰ 这个新的 Windows 程序包类型允许您无需指定版本请求.NET 或语言等服务。 使用 DISM 搜索类似 Windows Update 或您公司的服务器来查找并安装最新版本的多个源。 有关详细信息，请参阅[DISM 功能程序包服务命令行选项](dism-capabilities-package-servicing-command-line-options.md)。

    若要了解详细信息，请参阅新主题︰ [DISM 功能程序包服务命令行选项](dism-capabilities-package-servicing-command-line-options.md)。

-   **操作系统和配置包压缩**︰ 通过运行操作系统和其他系统文件的压缩文件在 Windows 映像上节省空间。 这将替换 Windows 8.1 中的 WIMBoot 功能。

    若要了解详细信息，请参阅**/Apply-Image***/ 压缩*和**/Apply-CustomDataImage**在[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)。

有关 DISM 的概述，请参阅[DISM 是什么？](what-is-dism.md)。

 

 





