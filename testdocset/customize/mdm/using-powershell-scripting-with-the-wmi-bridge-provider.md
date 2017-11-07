---
title: "使用 PowerShell 脚本使用 WMI 桥接器提供程序"
description: "本主题介绍如何使用 PowerShell Cmdlet 的脚本来配置每个用户和每台设备的策略设置，以及如何调用通过 WMI 桥提供程序的方法。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 238D45AD-3FD8-46F9-B7FB-6AEE42BE4C08
ms.openlocfilehash: be158e286d454e9958933ed4892568dafa0d6187
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="using-powershell-scripting-with-the-wmi-bridge-provider"></a>使用 PowerShell 脚本使用 WMI 桥接器提供程序

本主题介绍如何使用 PowerShell Cmdlet 的脚本来配置每个用户和每台设备的策略设置，以及如何调用通过[WMI 桥提供程序](https://msdn.microsoft.com/library/windows/desktop/dn905224.aspx)的方法。


## <a name="configuring-per-device-policy-settings"></a>每个设备策略设置的配置

本部分提供 PowerShell Cmdlet 来配置每台设备设置通过[WMI 桥提供程序](https://msdn.microsoft.com/library/windows/desktop/dn905224.aspx)的示例脚本。 如果一个类支持设备设置，必须为 InPartition("local-system") 定义的类级限定符。

对于所有设备设置，必须在本地系统用户下执行 WMI 桥客户端。 要做到这一点，从<https://technet.microsoft.com/sysinternals/bb897553.aspx>下载 psexec 工具并运行`psexec.exe -i -s cmd.exe`从管理提升的命令提示符。

此节中的脚本示例使用类[MDM\_策略\_Config01\_WiFi02](https://msdn.microsoft.com/library/windows/desktop/dn905246.aspx):

```ManagedCPlusPlus
[dynamic, provider("DMWmiBridgeProv"), InPartition("local-system")]
class MDM_Policy_Config01_WiFi02
{
  string InstanceID;
  string ParentID;
  sint32 AllowInternetSharing;
  sint32 AllowAutoConnectToWiFiSenseHotspots;
  sint32 WLANScanMode;
};
```

下面的脚本说明了如何创建、 枚举、 查询、 修改和删除实例。

```PowerShell
$namespaceName = "root\cimv2\mdm\dmmap"
$className = "MDM_Policy_Config01_WiFi02"

# Create a new instance for MDM_Policy_Config01_WiFi02 
New-CimInstance -Namespace $namespaceName -ClassName $className -Property @{ParentID="./Vendor/MSFT/Policy/Config";InstanceID="WiFi";AllowInternetSharing=1;AllowAutoConnectToWiFiSenseHotspots=0;WLANScanMode=100}

# Enumerate all instances available for MDM_Policy_Config01_WiFi02
Get-CimInstance -Namespace $namespaceName -ClassName $className

# Query instances with matching properties
Get-CimInstance -Namespace $namespaceName -ClassName $className -Filter "ParentID=&#39;./Vendor/MSFT/Policy/Config&#39; and InstanceID=&#39;WiFi&#39;"

# Modify existing instance
$obj = Get-CimInstance -Namespace $namespaceName -ClassName $className -Filter "ParentID=&#39;./Vendor/MSFT/Policy/Config&#39; and InstanceID=&#39;WiFi&#39;"
$obj.WLANScanMode=500
Set-CimInstance -CimInstance $obj

# Delete existing instance
try
{
    $obj = Get-CimInstance -Namespace $namespaceName -ClassName $className -Filter "ParentID=&#39;./Vendor/MSFT/Policy/Config&#39; and InstanceID=&#39;WiFi&#39;"
    Remove-CimInstance -CimInstance $obj
}
catch [Exception]
{
    write-host $_ | out-string
}
```

## <a name="configuring-per-user-settings"></a>配置每个用户设置

本部分提供 PowerShell Cmdlet 示例脚本来配置每个用户设置 WMI 桥通过。 如果一个类支持用户设置，必须为 InPartition("local-user") 定义的类级限定符。

此节中的脚本示例使用类[MDM\_策略\_用户\_Config01\_Authentication02](https://msdn.microsoft.com/library/windows/desktop/mt146854.aspx):

```ManagedCPlusPlus
[dynamic, provider("DMWmiBridgeProv"), InPartition("local-user")]
class MDM_Policy_User_Config01_Authentication02
{
  string InstanceID;
  string ParentID;
  sint32 AllowEAPCertSSO;
};
```

> **请注意** 如果当前登录的用户试图访问或修改自己的用户设置，则使用上一节的每个设备的设置脚本变得容易得多。 必须在提升的管理员命令提示符下执行所有 PowerShell cmdlet。

 

如果访问或修改其他用户的设置，然后 PowerShell 脚本会更复杂因为 WMI 桥需要用户 SID 设置在不支持本机 PowerShell cmdlet 的 MI 自定义上下文中。

> **请注意**  在本地系统下所必须执行的所有命令。

 

用户可以通过 Windows 命令获得 SID `wmic useraccount get name, sid`。 下面的脚本示例假定用户 SID 是 S-1-5-21-4017247134-4237859428-3008104844-1001。

```PowerShell
$namespaceName = "root\cimv2\mdm\dmmap"
$className = "MDM_Policy_User_Config01_Authentication02"

# Configure CIM operation options with target user info
$options = New-Object Microsoft.Management.Infrastructure.Options.CimOperationOptions
$options.SetCustomOption("PolicyPlatformContext_PrincipalContext_Type", "PolicyPlatform_UserContext", $false)
$options.SetCustomOption("PolicyPlatformContext_PrincipalContext_Id", "S-1-5-21-4017247134-4237859428-3008104844-1001", $false)

# Construct session used for all operations
$session = New-CimSession

##########################################################################
# Create a new instance for MDM_Policy_User_Config01_Authentication02
##########################################################################
$newInstance = New-Object Microsoft.Management.Infrastructure.CimInstance $className, $namespaceName
$property = [Microsoft.Management.Infrastructure.CimProperty]::Create("ParentID", &#39;./Vendor/MSFT/Policy/Config&#39;, "string", "Key")
$newInstance.CimInstanceProperties.Add($property)
$property = [Microsoft.Management.Infrastructure.CimProperty]::Create("InstanceID", &#39;Authentication&#39;, "String", "Key")
$newInstance.CimInstanceProperties.Add($property)
$property = [Microsoft.Management.Infrastructure.CimProperty]::Create("AllowEAPCertSSO", 1, "Sint32", "Property")
$newInstance.CimInstanceProperties.Add($property)
try
{
    $session.CreateInstance($namespaceName, $newInstance, $options)
}
catch [Exception]
{
    write-host $_ | out-string
}

##########################################################################
# Enumerate all instances for MDM_Policy_User_Config01_Authentication02
##########################################################################
$session.EnumerateInstances($namespaceName, $className, $options)

##########################################################################
# Query instance for MDM_Policy_User_Config01_Authentication02
# with matching properties
##########################################################################
$getInstance = New-Object Microsoft.Management.Infrastructure.CimInstance $className, $namespaceName
$property = [Microsoft.Management.Infrastructure.CimProperty]::Create("ParentID", &#39;./Vendor/MSFT/Policy/Config&#39;, "string", "Key")
$getInstance.CimInstanceProperties.Add($property)
$property = [Microsoft.Management.Infrastructure.CimProperty]::Create("InstanceID", &#39;Authentication&#39;, "String", "Key")
$getInstance.CimInstanceProperties.Add($property)
try
{
    $session.GetInstance($namespaceName, $getInstance, $options)
}
catch [Exception]
{
    write-host $_ | out-string
}

##########################################################################
# Modify existing instance for MDM_Policy_User_Config01_Authentication02
##########################################################################
$getInstance = New-Object Microsoft.Management.Infrastructure.CimInstance $className, $namespaceName
$property = [Microsoft.Management.Infrastructure.CimProperty]::Create("ParentID", &#39;./Vendor/MSFT/Policy/Config&#39;, "string", "Key")
$getInstance.CimInstanceProperties.Add($property)
$property = [Microsoft.Management.Infrastructure.CimProperty]::Create("InstanceID", &#39;Authentication&#39;, "String", "Key")
$getInstance.CimInstanceProperties.Add($property)
try
{
    $updateInstance = $session.GetInstance($namespaceName, $getInstance, $options)[0]
    $updateInstance.AllowEAPCertSSO = 0
    $session.ModifyInstance($namespaceName, $updateInstance, $options)
}
catch [Exception]
{
    write-host $_ | out-string
}

##########################################################################
# Delete existing instance for MDM_Policy_User_Config01_Authentication02
##########################################################################
$getInstance = New-Object Microsoft.Management.Infrastructure.CimInstance $className, $namespaceName
$property = [Microsoft.Management.Infrastructure.CimProperty]::Create("ParentID", &#39;./Vendor/MSFT/Policy/Config&#39;, "string", "Key")
$getInstance.CimInstanceProperties.Add($property)
$property = [Microsoft.Management.Infrastructure.CimProperty]::Create("InstanceID", &#39;Authentication&#39;, "String", "Key")
$getInstance.CimInstanceProperties.Add($property)
try
{
    $deleteInstance = $session.GetInstance($namespaceName, $getInstance, $options)[0]
    $session.DeleteInstance($namespaceName, $deleteInstance, $options)
}
catch [Exception]
{
    write-host $_ | out-string
}
```

## <a name="invoking-methods"></a>调用方法

本部分提供 PowerShell Cmdlet 来调用 WMI 网桥对象方法的示例脚本。 下面的脚本必须在本地系统用户执行。 要做到这一点，从<https://technet.microsoft.com/sysinternals/bb897553.aspx>下载 psexec 工具并运行`psexec.exe -i -s cmd.exe`从管理提升的命令提示符。

此节中的脚本示例使用[UpgradeEditionWithProductKeyMethod](https://msdn.microsoft.com/library/windows/desktop/mt599805.aspx)方法的[MDM\_WindowsLicensing](https://msdn.microsoft.com/library/windows/desktop/dn948453.aspx)类。

```PowerShell
$namespaceName = "root\cimv2\mdm\dmmap"
$className = "MDM_WindowsLicensing"
$methodName = "UpgradeEditionWithProductKeyMethod"
$fakeProductKey = "7f1a3659-3fa7-4c70-93ce-0d354e8e158e"

$session = New-CimSession

$params = New-Object Microsoft.Management.Infrastructure.CimMethodParametersCollection
$param = [Microsoft.Management.Infrastructure.CimMethodParameter]::Create("param", $fakeProductKey, "String", "In")
$params.Add($param)

try
{
    $instance = Get-CimInstance -Namespace $namespaceName -ClassName $className -Filter "ParentID=&#39;./Vendor/MSFT&#39; and InstanceID=&#39;WindowsLicensing&#39;"
    $session.InvokeMethod($namespaceName, $instance, $methodName, $params)
}
catch [Exception]
{
    write-host $_ | out-string
}
```

## <a name="related-topics"></a>相关的主题

[桥接 WMI 提供程序](https://msdn.microsoft.com/library/windows/desktop/dn905224.aspx)

 





