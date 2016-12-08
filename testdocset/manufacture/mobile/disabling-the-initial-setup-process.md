---
author: kpacquer
Description: "初始安装进程，则禁用"
ms.assetid: e0aa36a7-5524-42de-855d-1a9b7e03e250
MSHAttr: PreferredLib:/library/windows/hardware
title: "初始安装进程，则禁用"
ms.openlocfilehash: b94974de01d6072b3aaa5d1039f531f7373c9176
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="disabling-the-initial-setup-process"></a>初始安装进程，则禁用


要禁用该设备的初始安装过程 （有时也称为*现成的经验*或*OOBE*） 测试、 运行状况或生产在制造过程中使用的图像中，包括用于生成图像的 OEMnput.xml 文件中的 SKIPOOBE 图像处理功能。

SKIPOOBE 功能设置**OobeHeadless**注册表值 (REG\_DWORD 值下 HKEY\_本地\_机\\软件\\Microsoft\\外壳\\OOBE 条目) 到 1。 或者，您可以直接在自己的包之一来配置此注册表值。 下面的示例演示如何设置此注册表值的包 XML 文件。

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<Package xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  Owner="Contoso"
  Component="Shell"
  SubComponent="DisableOOBE"
  OwnerType="OEM"
  ReleaseType="Production" xmlns="urn:Microsoft.WindowsPhone/PackageSchema.v8.00">

  <Macros>
    <Macro Id="hklm.shell" Value="$(hklm.microsoft)\Shell"/>
  </Macros>

  <Components>
    <OSComponent>
      <RegKeys>
        <RegKey KeyName="$(hklm.shell)\OOBE">
          <RegValue Name="OobeHeadless" Type="REG_DWORD" Value="00000001" />
        </RegKey>
      </RegKeys>
    </OSComponent>
  </Components>
</Package>
```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[在包项目文件中指定的文件和注册表项](https://msdn.microsoft.com/library/dn789219)

 

 






