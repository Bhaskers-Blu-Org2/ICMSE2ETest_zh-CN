---
author: kpacquer
Description: "在闪烁的自定义工具中实现图像完整性验证"
ms.assetid: 0885d221-e9c6-4fe1-987b-34781546ba07
MSHAttr: PreferredLib:/library/windows/hardware
title: "在闪烁的自定义工具中实现图像完整性验证"
ms.openlocfilehash: 26468abb000faef1515759fe38463a6bd56ff170
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="implementing-image-integrity-validation-in-custom-flashing-tools"></a>在闪烁的自定义工具中实现图像完整性验证


FFU 图像包含签名的编录文件、 目录和对应于图像的每个块的哈希表中的哈希值。 使用 SHA256 安全哈希算法生成哈希表的内容。 必须执行三次检查，然后刷新图像是︰

-   **编录签名验证**的验证签名的编录文件的签名有助于验证图像来自受信任的来源。

-   **哈希值的哈希值验证表**-验证哈希值的哈希表中的表可以帮助验证图像未被篡改。

-   **数据分解使用哈希表项的验证**-FFU 应用程序必须在闪烁的图像的设备之前检查其对应的区块希对每个区块。

## <a name="span-idcheckingthesignatureonthecatalogandcheckingthehashofthetableofhashesspanspan-idcheckingthesignatureonthecatalogandcheckingthehashofthetableofhashesspanspan-idcheckingthesignatureonthecatalogandcheckingthehashofthetableofhashesspanchecking-the-signature-on-the-catalog-and-checking-the-hash-of-the-table-of-hashes"></a><span id="Checking_the_signature_on_the_catalog_and_checking_the_hash_of_the_table_of_hashes"></span><span id="checking_the_signature_on_the_catalog_and_checking_the_hash_of_the_table_of_hashes"></span><span id="CHECKING_THE_SIGNATURE_ON_THE_CATALOG_AND_CHECKING_THE_HASH_OF_THE_TABLE_OF_HASHES"></span>检查目录上的签名和检查哈希值的哈希表


签名验证的目标是确保在该目录中的签名与电话上的 PK 证书相匹配。 此方法允许检查而无完整图像闪烁之前设备上预先签名。 签名检查条件假设该目录中包含的 SHA1 哈希。

Microsoft 提供了一种 UEFI 协议，为此目的，EFI 公开函数\_检查\_SIG\_AND\_哈希。 有关详细信息，请参阅[UEFI 检查签名协议](https://msdn.microsoft.com/library/windows/hardware/dn772115)。 此函数还可验证哈希值的哈希表。

**示例代码流**

1.  建立目录和哈希表数据的指针。

2.  确定目录和哈希表数据中的字节大小。

3.  使用[UEFI 检查签名协议](https://msdn.microsoft.com/library/windows/hardware/dn772115)调用 EFI\_检查\_SIG\_AND\_传递指针和数据大小的哈希。

4.  基于 EFI 返回代码可以继续处理图像，或张贴安全消息如 EFI\_安全\_冲突。

**请注意**  
如果未在设备上启用安全引导，签名签入将不执行。

 

## <a name="span-idcheckingthedataagainstthehashtableentriesspanspan-idcheckingthedataagainstthehashtableentriesspanspan-idcheckingthedataagainstthehashtableentriesspanchecking-the-data-against-the-hash-table-entries"></a><span id="Checking_the_data_against_the_hash_table_entries"></span><span id="checking_the_data_against_the_hash_table_entries"></span><span id="CHECKING_THE_DATA_AGAINST_THE_HASH_TABLE_ENTRIES"></span>检查数据进行哈希表项


OEM 闪烁工具必须检查针对哈希表项的数据。 为闪烁工具，[开发自定义 OEM 闪烁工具](developing-custom-oem-flashing-tools.md)有关的信息。

**示例代码流**

可以使用多个有效的方法;此处提供示例作为参考的一个共同点。

1.  从哈希表的图像标题中获得新的哈希数据。

2.  设置一个循环来处理的图像中的数据块。

3.  获取指向当前文本块的数据的哈希。

4.  将当前文本块的使用函数**memcmp**例如哈希表数据与数据的哈希进行比较。

5.  如果两个哈希值匹配，则增加指针并准备签下一步的数据块。

6.  如果两个哈希值不匹配，停止所有图像的处理和发送一条安全消息如**EFI\_安全\_违反**。

7.  继续处理之前要处理的图像中没有更多的数据。

此处讨论的 FFU 元素的信息，请参阅[FFU 图像格式](ffu-image-format.md)。

## <a name="span-iderrorhandlingspanspan-iderrorhandlingspanspan-iderrorhandlingspanerror-handling"></a><span id="Error_handling"></span><span id="error_handling"></span><span id="ERROR_HANDLING"></span>错误处理


应使用标准错误处理代码的技术。 这里列出了一些常见的情况下，来处理︰

-   目录数据丢失

-   资源不足

-   空的图像

## <a name="span-idcleanupandexitspanspan-idcleanupandexitspanspan-idcleanupandexitspanclean-up-and-exit"></a><span id="Clean_up_and_exit"></span><span id="clean_up_and_exit"></span><span id="CLEAN_UP_AND_EXIT"></span>清理并退出


按照标准做法，清理任何数组或其他对象前创建退出闪烁代码。 退出进程应返回最终**EFI\_状态**值。 例如，如果图像是有效的您可以返回的值`EFI_SUCCESS`。

## <a name="span-idencryptionlibraryspanspan-idencryptionlibraryspanspan-idencryptionlibraryspanencryption-library"></a><span id="Encryption_library"></span><span id="encryption_library"></span><span id="ENCRYPTION_LIBRARY"></span>加密库


定位并支持哈希验证，如 EFI 的图像中包括适当的加密库\_希\_协议。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[开发自定义 OEM 闪烁工具](developing-custom-oem-flashing-tools.md)

 

 






