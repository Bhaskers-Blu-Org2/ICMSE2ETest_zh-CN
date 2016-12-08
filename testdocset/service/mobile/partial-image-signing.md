---
author: kpacquer
Description: "部分图像签名"
ms.assetid: dac19053-5243-45f2-9041-b9de9ea0bd80
MSHAttr: PreferredLib:/library/windows/hardware
title: "部分图像签名"
ms.openlocfilehash: ec80d4f41b1d35e1e9a6feed31f8927a40ba8aed
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="partial-image-signing"></a>部分图像签名


接收客户端的旧版支持签名只完整 FFU 图像。 但是，有几种有效方案，您可以提交一个分部 FFU 图像签名而不是一个完整的图像，如︰

-   签名的包[零售映像的 Windows 标准包装配置 (WSPC) 要求](https://msdn.microsoft.com/library/dn756781)所述缓存了 Windows 标准软件包配置 (WSPC) 方案中详细说明的功能。

-   签名验证的 MMO 包和在制造过程中的故障排除。

-   修复的 bug 进行测试图像清单本身的快速测试。 例如，以前可能有一周的延迟或更的这段时间您修复内容签入到实际生成的二进制文件包含此修复程序。 为了减少这种延迟，您可以现在生成的二进制文件的本地副本，创建包、 提交部分包要签名，零售，然后检索零售签名部分包之前重新集成和闪烁它使用 IUTool 的移动电话。

-   安装测试和调试工具零售映像调试仅零售映像显现的问题上。

接收客户端的最新版本现在实现了支持部分图像签名的功能，降低对您手动创建您自己的需要"制造"包和 UpdateHistory.xml 文件提交到接收客户端要签名的软件包时。 注意您的帐户必须有权对部分图像签名为利用这种新功能，否则任何此类提交会失败。

## <a name="span-idcontextualindividualpackagesigningspanspan-idcontextualindividualpackagesigningspanspan-idcontextualindividualpackagesigningspancontextual-individual-package-signing"></a><span id="Contextual_Individual_Package_Signing"></span><span id="contextual_individual_package_signing"></span><span id="CONTEXTUAL_INDIVIDUAL_PACKAGE_SIGNING"></span>上下文的单个包签名


Oem 可能利用高速缓存机制来优化其生成过程的包。 在这过程，在零售已签名的软件包都会被缓存，以便可以重新使用，跨多个图像。 因此任何新代码都必须签名，然后才能重新使用它跨多个图像放入包缓存的零售。 为此，应创建新包，其中包含二进制文件和图像。 但是，而不是提交从零售签名图像的所有程序包，您现在可以提交程序包包含的修补程序。 若要执行此操作，使用接收客户端的`Initialize-FirmwareSubmission`使用的 cmdlet `-TypeOfSubmission PartialImage`，以及到目录中的图像生成过程中创建的 UpdateHistory.xml 文件指定的目录，包含新的软件包，为零售签名。 接收客户端将检索包和 UpdateHistory.xml 文件。 Microsoft 将再验证基于 UpdateHistory.xml 文件的提交和零售对包进行签名。 然后，您可以使用`Get-SignedFirmwareSubmission`cmdlet 获得零售已签名的软件包并将其放置在包缓存中。 注意您的帐户必须有权签署单个软件包以这种方式为利用这种新功能，否则任何此类提交会失败。

## <a name="span-idcontextfreeindividualpackagesigningspanspan-idcontextfreeindividualpackagesigningspanspan-idcontextfreeindividualpackagesigningspancontext-free-individual-package-signing"></a><span id="Context_Free_Individual_Package_Signing"></span><span id="context_free_individual_package_signing"></span><span id="CONTEXT_FREE_INDIVIDUAL_PACKAGE_SIGNING"></span>上下文可用的单个包签名


Oem 可以现在还用于接收客户端创建"上下文可用"提交。 例如，如果您需要创建一个新的 MMO 包，根据产品系列最近所做的更改，然后就可以 MMO 包在目录中，在提交使用接收客户端时指定目录，以及指定提交"免费上下文"。 这种包提交签名仅根据 EKU 组合。

## <a name="span-idpartialimagepackagesigningexamplespanspan-idpartialimagepackagesigningexamplespanspan-idpartialimagepackagesigningexamplespanpartial-image-package-signing-example"></a><span id="Partial_Image_Package_Signing_Example"></span><span id="partial_image_package_signing_example"></span><span id="PARTIAL_IMAGE_PACKAGE_SIGNING_EXAMPLE"></span>部分图像包签名示例


准备要签名部分 FFU:

``` syntax
PS> Initialize-FirmwareSubmission -TypeOfProduct WindowsPhoneBlue -TypeOfSubmission PartialImage -UpdateHistoryPath c:\input\UpdateHistory.xml -OemInputPath c:\input -OutputFilePath c:\output -PartialImageDirectory c:\input\spkg
```

 

 





