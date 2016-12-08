---
title: "注册自定义的评估"
description: "注册自定义的评估"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: b86c6b47-08d0-441a-ba92-3a7be65ebe16
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 61074264ffadfd99ba25fce37cf3cda7a51da44a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="register-custom-assessments"></a>注册自定义的评估


他们在安装时自动注册安装与 Windows 评估 Toolkit 的评估。 但是，如果使用评估平台 Api 来开发自己的评估，则必须手动注册评估，以便它们出现在 Windows 评估控制台和 Windows 评估服务的客户端 (Windows ASC)。

**请注意**  
一组公共的 Api 可用于创建和扩展与评估平台兼容的评估。 有关详细信息，请参阅[MSDN︰ 评估执行引擎](http://go.microsoft.com/fwlink/?LinkId=236367)。

 

可以使用以下命令行选项来注册或注销定制评估。

若要注册评估︰

**Regasmt***&lt;路径\_的\_评估&gt;*

要注销的评估︰

**Regasmt/u***&lt;评估的路径&gt;*

**请注意**  
Windows 评估 Toolkit 安装时，默认安装**Regasmt.exe** 。 默认情况下， **Regasmt.exe**安装在 %PROGRAMFILES%\\窗口工具包\\10\\评估和部署工具包\\Windows 评估 Toolkit\\x86。 没有任何 x64 版本。

您必须具有管理员权限才能运行这些命令。

 

**若要注册评估**

1.  在提升的命令提示符下，键入︰

    ``` syntax
    regasmt C:\MyAssessments\example.asmtmanifest.asmtx
    ```

    其中 c:\\MyAssessments\\example.asmtmanifest 是评估的路径。 支持相对路径。

2.  若要注册多个评估，列出评估。 例如︰

    ``` syntax
    regasmt C:\MyAssessments\example.asmtmanifest.asmtx example2.asmtmanifest.asmtx
    ```

**要注销的评估**

-   在提升的命令提示符下，键入︰

    ``` syntax
    regasmt /u C:\MyAssessments\example.asmtmanifest.asmtx
    ```

    **请注意**  
    注销的评估不会卸载它。 您可以注销多个评估一次。

     

## <a name="related-topics"></a>相关的主题


[Windows 评估 Toolkit](windows-assessment-toolkit-technical-reference.md)

[评估 Windows 控制台的常见方案](windows-assessment-console-common-scenarios.md)

 

 







