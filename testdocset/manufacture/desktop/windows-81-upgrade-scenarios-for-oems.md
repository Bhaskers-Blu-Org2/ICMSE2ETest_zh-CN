---
author: Justinha
Description: "Oem 的 Windows 8.1 升级方案"
ms.assetid: 92f0ef1c-06e0-4f9b-8009-9567ae1bfaac
MSHAttr: PreferredLib:/library/windows/hardware
title: "Oem 的 Windows 8.1 升级方案"
ms.openlocfilehash: 05721f74166e679270f4e214bedde551be701714
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-81-upgrade-scenarios-for-oems"></a>Oem 的 Windows 8.1 升级方案


Windows 8.1 升级会保留大多数的 OEM 的自定义设置，包括 OEM 品牌、 应用程序、 帮助和支持信息，驱动程序，以及 OEM 存储区列表。 一些 OEM 解决方案，包括自定义的帮助和支持过或自定义恢复解决方案可能不会保留完成升级。 若要为您的客户减少任何潜在的问题，测试端到端升级体验。

可以安装 Windows 8.1，从 Windows 应用商店或媒体。

Windows 8.1 的升级选项包括︰

-   **完全升级**会保留应用程序、 用户数据、 用户帐户和计算机设置。

-   **数据只**会保留用户帐户和数据，但不能保留安装桌面应用程序或操作系统设置。 驱动程序安装 （存储和网络设备驱动程序） 的关键迁移到新安装中。

-   **全新安装**不会保存任何数据或 Windows 配置。

所有的个人文件，以及 Windows 文件和目录，移动到 Windows.old 文件夹，并在 Windows 安装完成后可以访问。 个人文件将保留在 Windows.old。 后一段时间，从以前的安装的 Windows 文件已删除。

支持升级的选项是︰

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">以前的操作系统</th>
<th align="left">全面升级</th>
<th align="left">仅数据</th>
<th align="left">干净安装</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Windows 8 （从 Windows 应用商店）</p></td>
<td align="left"><p>是</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>否</p></td>
</tr>
<tr class="even">
<td align="left"><p>Windows RT （从 Windows 应用商店）</p></td>
<td align="left"><p>是</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>否</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Windows 8 （从介质）</p></td>
<td align="left"><p>是</p></td>
<td align="left"><p>是</p></td>
<td align="left"><p>是</p></td>
</tr>
<tr class="even">
<td align="left"><p>Windows 7 （从介质）</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>是</p></td>
<td align="left"><p>是</p></td>
</tr>
</tbody>
</table>

 

Windows Vista 和 Windows XP 从 Windows 8.1 升级安装不受支持。

## <a name="span-idrollbackspanspan-idrollbackspansystem-rollback-log-files"></a><span id="ROLLBACK"></span><span id="rollback"></span>系统回滚日志文件


当 Windows 升级失败，则回滚到先前的安装时发生。 通过查看日志文件解决问题 (*&lt;驱动器&gt;*$Windows。 ~ BT\\源\\黑豹和源\\回滚，其中*&lt;驱动器&gt;*已安装了 Windows 的驱动器的根目录)。

**警告**  
如果发生系统回滚，Push-Button 重设图像不再将 Windows RT 设备上可用。

 

## <a name="span-idlowdiskspanspan-idlowdiskspanlow-disk-space"></a><span id="LOWDISK"></span><span id="lowdisk"></span>磁盘空间不足


具有有限的磁盘空间，可以在 Pc 上安装 Windows 8.1。 升级过程将压缩以前的 Windows 安装并删除大型 Windows 缓存文件。

## <a name="span-idwinrespanspan-idwinrespanspan-idwinrespanwindows-re"></a><span id="WinRE"></span><span id="winre"></span><span id="WINRE"></span>Windows RE


这样可以修复操作系统安装 Windows RE 的 Windows 8.1 版本。 升级期间，引导关键和输入设备驱动程序添加到新的 Windows RE 映像。

通过以下方式安装 Windows RE:

1.  在 Windows 直角上使用现有的 Windows RE 分区

2.  Windows RE 分区保留在原位置上 Windows 8 的 Pc OEM 配置 Windows RE 分区。 收缩 Windows 分区中创建新的 Windows RE 分区。

3.  与一般的 Windows RE 分区在 Windows 8 台 Pc 上使用现有的 Windows RE 分区。

**警告︰**  
任何 OEM 自定义现有的 Windows RE 映像不会迁移到新的 Windows RE 映像。

 

## <a name="span-idrecpbrspanspan-idrecpbrspanrecovery-image-for-push-button-reset"></a><span id="RECPBR"></span><span id="recpbr"></span>下压按钮重置的恢复映像


下压按钮重置的图像将更新基于下列实现︰

升级平台**映像的本地恢复可用性**之后升级前

**升级方法**

**恢复映像**

**恢复映像分区**

x64、 x86

本地恢复映像时可用

媒体或 Windows 应用商店

现有 Windows 8 的恢复映像

现有的分区未被修改

x64、 x86

本地恢复的图像不可用

媒体或 Windows 应用商店

无

无

Windows RT

本地恢复映像时可用

Windows 应用商店

新的 Windows 8.1 恢复映像

重用现有的分区

Windows RT

本地恢复的图像不可用

Windows 应用商店

无

无

 

在与现有的恢复映像的 Windows RT Pc，图像将被 Windows 8.1 恢复映像。 以下自定义项迁移到 Windows 8.1 恢复映像，包括︰

-   存储自定义项和预装 Windows 应用商店应用程序许可证

-   与 Windows 8.1 兼容的驱动程序

-   OEM 支持信息

恢复图像仍在 Windows 8 台 Pc 上与现有的恢复映像。

如果没有现有的以前的操作系统创建恢复图像分区、 没有恢复映像或分区。

## <a name="span-iddriversspanspan-iddriversspandrivers"></a><span id="DRIVERS"></span><span id="drivers"></span>驱动程序


在全面升级方案、 迁移类型的以下驱动程序︰

-   兼容的驱动程序

-   由 OEM 或最终用户安装第三方驱动程序

-   存储驱动程序是安装的关键被迁移到 Windows PE，以及所有的升级方案中的操作系统。

将不迁移下列驱动程序︰

-   第三方机箱中的驱动程序，例如打印机驱动程序不会迁移，因为新的操作系统通常包含更多最新的驱动程序。

-   不迁移软件筛选器驱动程序，但防病毒筛选驱动程序安装或驱动程序.inf 文件。

在全新安装和升级方案仅数据迁移的网络和 Wi-fi 驱动程序。

迁移的所有驱动程序放置在驱动程序存储库中，Windows 自动安装驱动程序期间即插即用基于[如何 Windows 通道驱动程序](http://go.microsoft.com/fwlink/?LinkId=294347)中定义的条件。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Windows 安装程序技术参考](windows-setup-technical-reference.md)

[Windows 安装程序日志文件和事件日志](windows-setup-log-files-and-event-logs.md)

 

 






