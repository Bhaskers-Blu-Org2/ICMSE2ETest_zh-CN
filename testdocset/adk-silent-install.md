# <a name="windows-adk-silent-install"></a>Windows ADK 静默式安装

如果您有需要以无提示方式安装 Windows ADK 的方案，您可以安装使用命令行。

请确保您的 PC 在 ADK 安装程序运行时将保持与 Internet 的连接。 运行时 ADK 安装程序从 Internet 上下载的安装包。 

## <a name="install-the-windows-adk-by-using-the-command-line"></a>通过使用命令行来安装 Windows ADK
1. 从[Microsoft 网站](https://developer.microsoft.com/en-us/windows/hardware/windows-assessment-deployment-kit)adksetup.exe 下载到您的 PC 上。
2. 以管理员身份打开命令提示符。
3. 在命令提示符窗口中，更改为包含 adksetup.exe 的目录。

        
```
    cd %userprofile%\downloads
```

4. 安装在 ADK。 使用 /quiet 进行静默安装。 使用 /features 指定的功能。 例如，部署工具和 Windows PE 以静默模式安装︰


```
    adksetup.exe /quiet /features OptionId.DeploymentTools OptionId.WindowsPreinstallationEnvironment
```

[ADKSetup 命令行语法](https://technet.microsoft.com/en-us/library/dn621910.aspx)。