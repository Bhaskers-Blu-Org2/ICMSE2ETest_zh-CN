---
author: kpacquer
Description: "Microsoft 制造操作系统"
ms.assetid: 8a46f749-6405-40e8-b3a5-32955e1c0070
MSHAttr: PreferredLib:/library/windows/hardware
title: "Microsoft 制造操作系统"
ms.openlocfilehash: 979ac8e44d3e5fc29fb14c4a69b91a4dc6bf359b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="microsoft-manufacturing-os"></a>Microsoft 制造操作系统


Microsoft 制造 OS (MMO)，操作系统，优化配置方便高效的制造。 MMO 旨在提供以下功能︰

-   快速启动时产生较小的图像包含支持制造所需的代码的测试执行。 快，加快了制造工艺，均可刷新较小的 OS 映像。

-   能够创建包含唯一的驱动程序的 OEM 自定义 MMO 图像和测试应用程序。

-   对 OEM 开发组件级测试，以及全功能质量和校准测试的支持。

-   对直接测试电话硬件组件的低级本机 Api 访问。

-   能够创建一种机制来远程控制测试应用程序和检索测试记录通过 USB 通信通道。

-   不依赖显示或触摸硬件，以便无外设的操作。

-   能够直接引导至 MMO 在制造环境中。

-   启动 MMO 时，OEM 测试应用程序的自动的启动。

-   能够编写到 DPP 分区来存储唯一的每个电话的数据。

-   在 UEFI 和 MMO 支持电池充电。 设置使用功能设置，使合作伙伴可以根据需要将其打开和关闭。 有关更多信息，请参见[MMO 图像定义](mmos-image-definition.md)。

## <a name="span-idworkingwithmmosspanspan-idworkingwithmmosspanspan-idworkingwithmmosspanworking-with-mmos"></a><span id="Working_with_MMOS"></span><span id="working_with_mmos"></span><span id="WORKING_WITH_MMOS"></span>使用 MMO


本部分介绍如何生成和闪存的 MMO 图像。

若要使用 MMO，请完成以下任务︰

1.  创建测试应用程序或其他制造工具的软件包形式。 更多的信息，请参阅[创建程序包](https://msdn.microsoft.com/library/dn756642)。

2.  创建闪烁协议并添加文件包，以支持该功能的 MMO。 有关更多信息，请参见[闪烁工具](flashing-tools.md)。

3.  创建 MMO 图像。 有关更多信息，请参见[MMO 图像定义](mmos-image-definition.md)。

4.  闪存设备的 MMO 图像。 更多的信息，请参阅[与设备闪存 MMO](flash-mmos-to-the-phone.md)。

5.  部署生产应用程序。 有关更多信息，请参阅[部署和测试 MMO 在用户模式下测试应用程序](deploy-and-test-a-user-mode-test-application-in-mmos.md)。

6.  如果您想要创建能够在内存中运行 MMO WIM，计算。 有关更多信息，请参见[使用 WIM MMO 图像](working-with-wim-mmos-images.md)。

## <a name="span-iddevelopingusermodetestapplicationsspanspan-iddevelopingusermodetestapplicationsspanspan-iddevelopingusermodetestapplicationsspandeveloping-user-mode-test-applications"></a><span id="Developing_user_mode_test_applications"></span><span id="developing_user_mode_test_applications"></span><span id="DEVELOPING_USER_MODE_TEST_APPLICATIONS"></span>开发用户模式下测试应用程序


若要创建用户模式下测试应用程序在生产测试设备，请完成以下任务︰

1.  开发使用 MMO 库的用户模式下测试应用程序。 更多的信息，请参阅[Api 支持的生产测试环境](manufacturing-test-environment-supported-apis.md)和[开发 MMO 测试应用程序](develop-mmos-test-applications.md)。

2.  服务可以用于启动用户模式下测试应用程序。 如果需要，可以与 PC 控制测试过程和结果记录上的测试控制器通信测试应用程序。

    配置服务在操作系统启动时自动启动，请服务包的配置文件中设置**启动**属性设置为"自动"。  

    ``` syntax
      <Components>
        <Service
          Name="SampleMMOSSvc"
          Start="Auto"
          …
    ```

    此功能才可用在 MMO。

3.  应只允许某些应用程序运行在 MMO。 API 可用于确定 MMO 是否或不运行。 有关更多信息，请参阅[确定是否运行 MMO](determine-if-mmos-is-running.md)。

4.  若要使设备进入连接备用电源状态，调用 SetScreenOff 函数。 更多的信息，请参见[调用 SetScreenOff 进入连接待机状态](calling-setscreenoff-to-enter-connected-standby.md)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[开发 MMO 测试应用程序](develop-mmos-test-applications.md)

 

 






