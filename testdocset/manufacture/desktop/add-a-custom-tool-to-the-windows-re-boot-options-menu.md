---
author: Justinha
Description: "向 Windows 重新启动选项菜单中添加自定义工具"
ms.assetid: 474958cf-91bc-4c5c-8afd-22865e9bf4a5
MSHAttr: PreferredLib:/library/windows/hardware
title: "向 Windows 重新启动选项菜单中添加自定义工具"
ms.openlocfilehash: 2de8eadb2bff460a1bf69f7a6cbf55e5d2190b2d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add-a-custom-tool-to-the-windows-re-boot-options-menu"></a>向 Windows 重新启动选项菜单中添加自定义工具


可以向 Windows 恢复环境 (WinRE) 图像中添加的自定义诊断或诊断工具。 此工具将显示在启动选项菜单。

通过开发自定义工具在 WinRE 中运行，您可以利用触摸和屏幕键盘支持 WinRE 中可用。

新的 Windows 10︰ 您不能添加 WinRE 中不存在默认 WinRE 工具的可选组件。 例如，如果您有依赖于.NET 可选组件的 Windows 8 应用程序，您需要为 Windows 10 重写应用程序。

**若要添加自定义工具**

1.  提取并装载 Windows 映像 (install.wim) 和其相应的 WinRE 图像 (winre.wim):

    ``` syntax
    md c:\mount
    xcopy D:\sources\install.wim C:\mount 
    md C:\mount\windows
    Dism /mount-image /imagefile:C:\mount\install.wim /index:1 /mountdir:C:\mount\windows 
    md C:\mount\winre 
    Dism /mount-image /imagefile:c:\mount\windows\windows\system32\recovery\winre.wim /index:1 /mountdir:C:\mount\winre
    ```

    有关这些步骤的详细信息，请参阅主题︰[自定义 Windows RE](customize-windows-re.md)。

2.  在记事本中，创建一个配置文件，指定自定义工具的文件名和参数 （如果有）︰

    ``` syntax
    <?xml version="1.0" encoding="utf-8"?>
    <!-- WinREConfig.xml -->
    <Recovery>
       <RecoveryTools>
          <RelativeFilePath>OEMDiagnostics.exe</RelativeFilePath>
          <CommandLineParam>/param1 /param2</CommandLineParam>
       </RecoveryTools>
    </Recovery>
    ```

    其中*c:\\工具\\OEMDiagnostics.exe*的自定义诊断或诊断工具，并在*/param1*和*/param2*是可选的参数使用时运行此自定义工具。

    **请注意**  
    您只能向 WinRE 启动选项菜单添加一个自定义的工具。

    保存使用 utf-8 编码的文件。 不要使用 ANSI:

    单击**文件**，然后单击**另存为**。 在**编码**框中，选择**utf-8**，并保存该文件作为`C:\mount\WinREConfig.xml`。

3.  创建\\源\\恢复\\工具文件夹 WinRE 中的装入文件夹，然后将自定义工具和其配置文件复制到新文件夹中︰

    ``` syntax
    md C:\mount\winre\sources\recovery\tools
    copy C:\Tools\OEMDiagnostics.exe C:\mount\winre\sources\recovery\tools
    copy C:\mount\WinREConfig.xml C:\mount\winre\sources\recovery\tools
    ```

    自定义工具和任何相关联的文件夹，以便它能够继续在将来 WinRE 升级之后必须是在该文件夹中。

4.  提交您的自定义并卸载 WinRE 图像︰

    ``` syntax
    Dism /unmount-image /mountdir:C:\mount\winre /commit
    ```

5.  可选︰ 创建 WinRE 映像的备份副本。

    ``` syntax
    copy C:\mount\windows\windows\system32\recovery\winre.wim C:\mount\winre_amd64_backup.wim
    ```

    通常可以重用相同的自定义项在多个图像。

6.  卸下并保存更改，从基本的 Windows 映像︰

    ``` syntax
    Dism /unmount-image /mountdir:C:\mount\windows /commit
    ```

**部署映像**

1.  在记事本创建配置文件描述启动选项菜单中的自定义工具。 添加为您支持的每种语言的说明。 本示例指定工具的名称和说明的英语和法语语言版本︰

    ``` syntax
    <?xml version="1.0" encoding="utf-8"?>
    <!-- AddDiagnosticsToolToBootMenu.xml -->
    <BootShell>
       <WinRETool locale="en-us">
             <Name>Fabrikam Utility</Name>
             <Description>Troubleshoot your Fabrikam PC</Description>
       </WinRETool>
       <WinRETool locale="fr-fr">
          <Name>Utilité de Fabrikam</Name>
          <Description>Dépannez votre PC de Fabrikam</Description>
       </WinRETool>
    </BootShell>
    ```

    **警告**  
    限制`<Name>`和`<Description>`值为大约 30 个字符或更少，以确保其在正确显示在启动选项菜单中。

    保存使用 utf-8 编码的文件︰

    单击**文件**，然后单击**另存为**。 在**编码**框中，选择**utf-8**，并保存该文件作为`E:\Recovery\BootMenu\AddDiagnosticsToolToBootMenu.xml`。

    其中*e:\\*是可移动驱动器或网络位置的驱动器号。

2.  在目标计算机上，在映像部署过程，但在注册自定义的 WinRE 启动映像和 Windows 操作系统，您必须注册自定义工具的说明︰

    ``` syntax
    Reagentc /setbootshelllink /configfile E:\Recovery\BootMenu\AddDiagnosticsToolToBootMenu.xml
    ```

    如果已正确注册自定义工具，将会运行此命令的输出︰ `<OEM Tool =  1>`。

    **请注意**  
    有关部署 Windows 的详细信息，请参阅[部署 Windows RE](deploy-windows-re.md)主题。

**要验证的自定义工具将出现在 Windows 启动时的启动选项菜单中**

1.  重新启动目标计算机，然后完成 OOBE 为您的用户。

    **请注意**  
    如果系统提示您输入产品密钥，请单击**跳过**。   

2.  单击**开始** &gt; **PC 设置**，然后选择**常规**。

3.  在**高级启动**部分中，选择**立即重新启动**。

    将出现的 Windows**启动选项**菜单。

4.  在**启动选项**菜单中，选择**疑难解答**，然后单击**Fabrikam 实用程序**的链接。

    计算机 WinRE，并在中指定该工具以重新启动*&lt;RecoveryTools&gt;*部分的 WinREConfig.xml 文件，将出现。

5.  确认自定义工具可正常工作，然后关闭工具。

    如果未出现启动选项菜单上的自定义工具，您可以尝试以下︰

    -   请验证 WinREConfig.xml 和 AddDiagnosticsToolToBootMenu.xml 使用 utf-8 编码格式保存文件。

    -   禁用 WinRE 再次注册自定义工具，然后启用 WinRE。 例如︰

        ``` syntax
        Reagentc /disable 
        Reagentc /setbootshelllink /configfile E:\Recovery\BootMenu\AddDiagnosticsToolToBootMenu.xml
        Reagentc /enable
        ```
**若要验证的自定义工具将出现 WinRE 恢复菜单**

1.  在恢复菜单中，选择**疑难解答**，，然后单击**Fabrikam 实用程序**链接。

2.  确认自定义工具可正常工作，然后关闭工具。

3.  单击**继续**。

    计算机重新启动到操作系统。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Windows 恢复环境 (Windows RE) 技术参考](windows-recovery-environment--windows-re--technical-reference.md)

[自定义 Windows RE](customize-windows-re.md)

[部署 Windows RE](deploy-windows-re.md)

[Windows RE 疑难解答功能](windows-re-troubleshooting-features.md)

 

 






