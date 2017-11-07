# <a name="install-the-windows-adk-offline"></a>安装 Windows ADK 脱机

若要在不能访问 Internet 的 PC 上安装 Windows ADK，首先下载可以访问互联网的电脑上的安装程序文件。 接下来，将安装程序文件复制到脱机的计算机可以访问的位置。 然后，运行 ADKSetup.exe 使用 GUI 或命令行。

## <a name="to-install-the-windows-adk-on-an-offline-computer-using-the-gui"></a>若要在脱机使用图形用户界面的计算机上安装 Windows ADK
1. 在 PC 上访问 Internet， [Microsoft 网站](https://developer.microsoft.com/en-us/windows/hardware/windows-assessment-deployment-kit)从运行 Windows ADK 安装程序。
2. 选择**为单独的计算机上安装下载的评估和部署工具包。**
3. 在**下载路径**框中，指定想要下载的文件的位置，然后单击**下一步**。
4. 选择是否要参与在客户体验改善计划 (CEIP)，然后单击**下载**。 
5. 下载完成后，单击**关闭**。
6. 将下载的文件复制到脱机的计算机可以访问的位置。
    例如，将文件复制到可移动媒体或计算机可以访问的文件服务器。

7. 在脱机的计算机中，将目录更改到所复制的文件的位置。
8. 运行 ADKSetup.exe，，然后选择您想要安装的 Windows ADK 功能。

## <a name="to-install-the-windows-adk-on-an-offline-computer-using-the-command-line"></a>在使用命令行脱机的计算机上安装 Windows ADK
1. 在 PC 上访问 Internet，保存一份 Adksetup.exe。
2. 以管理员身份打开命令提示符窗口。
3. 转到存储的 Adksetup.exe 文件的目录。
        
    ```
    cd %userprofile%\downloads
    ```

4. 运行 adksetup.exe。 使用 /quiet 以静默方式运行安装程序。 使用 /layout，以指定在其中脱机安装文件将被复制到。

    ```
    adksetup /quiet /layout c:\temp\ADKoffline
    ```

5. 将下载的文件复制到脱机的计算机可以访问的位置。
    例如，将文件复制到可移动媒体或脱机的计算机可以访问的文件服务器。
6. 在脱机的计算机上以管理员身份打开命令提示符窗口。
7. 转到包含 adksetup.exe 的目录。
8. 运行 adksetup.exe。 使用 /quiet 进行静默安装，/installpath 指定 ADK，并 /features 指定的安装位置。 例如，部署工具和 Windows PE 对 c:\ADK 进行静默安装︰ 

    ```
    adksetup.exe /quiet /installpath c:\ADK /features OptionId.DeploymentTools OptionId.WindowsPreinstallationEnvironment
    ```
    
[ADKSetup 命令行语法](https://technet.microsoft.com/en-us/library/dn621910.aspx)。