---
author: kpacquer
Description: "更新 IoT 核心设备上的时间服务器"
MSHAttr: PreferredLib:/library
title: "更新时间服务器"
ms.openlocfilehash: 14fae14755309b1fcc6b2c32619f40ddeea50f6f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="update-the-time-server"></a>更新时间服务器

IoT 核心设备和一台时间服务器的系统时间同步。 Windows 10 版本 1607年默认为在 http://time.windows.com 上使用 Windows 时间服务。 您可以更改时间服务器或添加多个时间服务器，当您的设备位于不同的网络环境。

##<a name="update-the-server-from-a-command-line-for-example-using-a-tool-like-putty"></a>更新服务器的命令行 （例如，使用类 PuTTY 工具）︰

1.   添加使用注册表项的时间服务器
     ``` syntax
     reg add HKLM\SYSTEM\CurrentControlSet\Services\w32time\Parameters /v NtpServer /t REG_SZ /d "time.windows.com,0x9 tick.usno.navy.mil,0x9 europe.pool.ntp.org,0x9 asia.pool.ntp.org,0x9" /f >nul 2>&1
     ```

2.  停止并重新启动网络服务
    
    ``` syntax
    net stop
    net start
    ```

##<a name="update-the-server-in-an-iot-core-image"></a>在 IoT 核心映像更新服务器

1.  创建程序包定义文件，并将其添加到图像。 若要了解详细信息，请参阅[实验室 1 c︰ 向图像中添加一个文件和注册表设置](add-a-registry-setting-to-an-image.md)。 示例脚本︰ 

    ``` syntax
    <OSComponent> 
      <RegKeys> 
         <RegKey KeyName="$(hklm.software)\CurrentControlSet\Services\w32time\Parameters">
            <RegValue Name="NtpServer" Value="time.windows.com,0x9 tick.usno.navy.mil,0x9 europe.pool.ntp.org,0x9 asia.pool.ntp.org,0x9" Type="REG_SZ"/>
        </RegKey>
      </RegKeys>
    </OSComponent>
    ```