---
title: DeviceManageability DDF
description: "本主题演示 OMA DM 设备描述框架 (DDF) DeviceManageability 配置服务提供程序。 Windows 10，1607年版本中添加了该 CSP。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: D7FA8D51-95ED-40D2-AA84-DCC4BBC393AB
ms.openlocfilehash: 7e7588722115fa7d019ff37da46daf9a384ad09f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="devicemanageability-ddf"></a>DeviceManageability DDF


本主题演示 OMA DM 设备描述框架 (DDF) DeviceManageability 配置服务提供程序。 Windows 10，1607年版本中添加了该 CSP。

``` syntax
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE MgmtTree PUBLIC " -//OMA//DTD-DM-DDF 1.2//EN"
  "http://www.openmobilealliance.org/tech/DTD/DM_DDF-V1_2.dtd"
  [<?oma-dm-ddf-ver supported-versions="1.2"?>]>
<MgmtTree xmlns:MSFT="http://schemas.microsoft.com/MobileDevice/DM">
  <VerDTD>1.2</VerDTD>
      <Node>
        <NodeName>Root</NodeName>
        <Path>./User/Vendor/MSFT</Path>
        <DFProperties>
          <AccessType>
            <Get />
          </AccessType>
          <DFFormat>
            <node />
          </DFFormat>
          <Occurrence>
            <One />
          </Occurrence>
          <Scope>
            <Permanent />
          </Scope>
          <DFType>
            <DDFName></DDFName>
          </DFType>
        </DFProperties>
      </Node>
      <Node>
        <NodeName>DeviceManageability</NodeName>
        <Path>./Device/Vendor/MSFT</Path>
        <DFProperties>
          <AccessType>
            <Get />
          </AccessType>
          <DFFormat>
            <node />
          </DFFormat>
          <Occurrence>
            <One />
          </Occurrence>
          <Scope>
            <Permanent />
          </Scope>
          <DFType>
            <MIME>com.microsoft/1.0/MDM/DeviceManageability</MIME>
          </DFType>
        </DFProperties>
        <Node>
          <NodeName>Capabilities</NodeName>
          <DFProperties>
            <AccessType>
              <Get />
            </AccessType>
            <DFFormat>
              <node />
            </DFFormat>
            <Occurrence>
              <One />
            </Occurrence>
            <Scope>
              <Permanent />
            </Scope>
            <DFType>
              <DDFName></DDFName>
            </DFType>
          </DFProperties>
          <Node>
            <NodeName>CSPVersions</NodeName>
            <DFProperties>
              <AccessType>
                <Get />
              </AccessType>
              <Description>Returns the versions of all configuration service providers (CSP) for MDM. </Description>
              <DFFormat>
                <xml />
              </DFFormat>
              <Occurrence>
                <One />
              </Occurrence>
              <Scope>
                <Permanent />
              </Scope>
              <DFType>
                <MIME>text/plain</MIME>
              </DFType>
            </DFProperties>
          </Node>
        </Node>
      </Node>
</MgmtTree>
```

 

 






