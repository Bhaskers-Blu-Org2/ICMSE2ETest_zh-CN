---
author: kpacquer
Description: "开发 MMO 测试应用程序"
ms.assetid: 1149e3d6-79d9-443e-9561-c030069eb79a
MSHAttr: PreferredLib:/library/windows/hardware
title: "开发 MMO 测试应用程序"
ms.openlocfilehash: 616b2aa552d9a018b529626d8e97f1301a3da5dc
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="develop-mmos-test-applications"></a>开发 MMO 测试应用程序


开发中 MMO 的用户模式测试是开发用户模式应用程序非常相似。

## <a name="span-idtestdevelopmentinmmosspanspan-idtestdevelopmentinmmosspanspan-idtestdevelopmentinmmosspantest-development-in-mmos"></a><span id="Test_development_in_MMOS"></span><span id="test_development_in_mmos"></span><span id="TEST_DEVELOPMENT_IN_MMOS"></span>在 MMO 的测试开发


使用以下步骤来创建、 部署和测试一个 MMO 测试应用程序。

1.  创建一个应用程序。

2.  添加代码以测试所需的组件，并显示或根据需要发送这些结果。 例如，此示例代码可以用于在 MMO 显示控制台消息。

    ``` syntax
#include <stdio.h>
#include <Windows.h>

    int main()
    {
        int i = 0;
        for(;;)
        {    
            wprintf(L"Test");
            Sleep(500);
            if (i == 12)
            {
                wprintf(L"Done");
                break;
            }
            i++;
        }
        return 0;
    }
    ```

3.  生成在 Visual Studio 中的测试应用程序。

4.  找到您生成应用程序时生成的二进制文件。 通常他们会在项目文件夹的子目录中如*\\MyProject\\arm\\调试\\*。

5.  通过使用中的 sign.cmd 脚本签名的可执行文件"%WPDKCONTENTROOT%\\工具\\bin\\i386"文件夹中，如下面的示例中所示。

    ``` syntax
    sign.cmd ApplicationForDrivers.exe
    ```

6.  若要测试您的应用程序，请将其复制到 c︰ 驱动器中的设备\\数据\\测试通过使用 FTP 目录，并通过 Telnet 运行它。 有关更多信息，请参阅[部署和测试 MMO 在用户模式下测试应用程序](deploy-and-test-a-user-mode-test-application-in-mmos.md)。

## <a name="span-idlibrariesinmmosspanspan-idlibrariesinmmosspanspan-idlibrariesinmmosspanlibraries-in-mmos"></a><span id="Libraries_in_MMOS"></span><span id="libraries_in_mmos"></span><span id="LIBRARIES_IN_MMOS"></span>在 MMO 库


在 MMO 中添加 lib 是类似于生产操作系统中添加 lib。 目前，在 Visual Studio 中配置此默认库位置的工具包。

``` syntax
$(WPDKInstallDir)lib\$(KitOs)\wp_um\$(Platform)
$(WPDKInstallDir)Tools\WPE\CRT\lib\$(Platform)
```

若要在 Visual Studio 中添加 lib，选择**项目** &gt; **属性** &gt; **配置属性** &gt; **VC + + 目录** &gt; **包含目录**。 若要使用 MMO 库，附加以下目录路径。

``` syntax
$(WPDKContentRoot)include\mmos
```

将手臂目录添加。 在 Visual Studio 中，选择**项目** &gt; **属性** &gt; **配置属性** &gt; **链接器** &gt; **常规** &gt; **附加库目录**。 若要使用 MMO 库，附加以下目录路径。

``` syntax
$(WPDKContentRoot)lib\win8\mmos\arm
```

## <a name="span-idsecurityinmmosspanspan-idsecurityinmmosspanspan-idsecurityinmmosspansecurity-in-mmos"></a><span id="Security_in_MMOS"></span><span id="security_in_mmos"></span><span id="SECURITY_IN_MMOS"></span>在 MMO 的安全


在开发环境中，用户模式测试二进制文件可以测试签名 （未签名的生产）。 使用[符号二进制文件和包](https://msdn.microsoft.com/library/windows/hardware/dn789217)中所述的过程来测试二进制文件的符号。

如果代码完整性检查处于活动状态，因为它通常是测试二进制文件未签名，将在调试窗口中收到与以下内容类似的错误信息。

``` syntax
* This is not a failure in CI, but a problem with the failing binary.
* Please contact the binary owner for getting the binary correctly signed.
```

 

 





