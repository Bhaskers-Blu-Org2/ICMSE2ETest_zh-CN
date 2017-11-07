---
author: kpacquer
Description: "对设备的闪存 MMO"
ms.assetid: 23b741e6-ba15-4a81-a78e-9545ff62c3af
MSHAttr: PreferredLib:/library/windows/hardware
title: "对设备的闪存 MMO"
ms.openlocfilehash: 6c98346635cef770ea338ca673e4db45153d4349
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="flash-mmos-to-the-device"></a>对设备的闪存 MMO


MMO 图像定义完毕后，可以将图像刷新到设备

1.  在主机端上的闪烁被通过使用 WinUSB，Microsoft 通用 USB 设备驱动程序建立连接。 默认情况下，Windows 8 和 Windows 10 中包括必要的驱动程序。 在 Windows 7 中，可以从 Windows Update 安装必要的驱动程序。 若要配置的 Windows 7 计算机来安装必要的驱动程序，请单击**开始**，键入"设备安装设置"，选择**是，这样做会自动 （推荐）**，然后单击 [**保存更改**。

2.  将设备置于打开设备电源时按住按钮向上卷闪烁模式。 设备处于闪烁模式后，连接到计算机的 USB 数据线。

3.  验证在设备管理器中为*WinUsb 设备*检测设备。

4.  若要能够使用 ffutool、 符号和 ImageSigner 工具，添加 %WPDKCONTENTROOT%\\工具\\bin\\i386 到**Path**环境变量。

5.  前闪烁 FFU 文件到该设备，您必须在命令提示符处使用以下语法 FFU 文件进行签名。 使用 ImgGen 工具时，猫文件将生成带有 FFU。

    ``` syntax
    c:\>sign <path to cat file>
    c:\>ImageSigner SIGN <path to ffu> <path to cat file>
    ```

    例如︰

    ``` syntax
    c:\>sign MMOS.cat
    c:\>ImageSigner SIGN MMOS.ffu MMOS.cat
    ```

6.  在命令提示符下运行 ffutool 命令，使用以下语法︰

    ``` syntax
    c:\>ffutool -flash <path to ffu image file>
    ```

    例如︰

    ``` syntax
    c:\>ffutool -flash C:\MMOS\MMOS.ffu
    ```

7.  您应该看到类似于下面的输出。

    ``` syntax
    Logging to ETL file: C:\Users\Nancy\AppData\Local\Temp\ffutool8276.etl 
    Found device: 
    Name: Contoso.DCD6000 Phone.DCD6000 
    ID: 00000045-14ca-3016-8fbe-120000000000 
    Flashing: MMOS.ffu 
    [==================================================] 100.00% 
    Transferred 157.88 MB in 50.56 seconds, overall rate 3.12 MB/s.
    ```

8.  在 MMO，设备将重新启动。 在设备上的显示将显示小的旋转图形。

 

 





