---
title: "WindowsSecurityAuditing DDF 文件"
description: "本主题演示 OMA DM 设备描述框架 (DDF) WindowsSecurityAuditing 配置服务提供程序。 Windows 10 1511年版本中添加了该 CSP。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: B1F9A5FA-185B-48C6-A7F4-0F0F23B971F0
ms.openlocfilehash: 326afd0e2f24f4d95a942f003f8f22fe9c6491ad
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windowssecurityauditing-ddf-file"></a>WindowsSecurityAuditing DDF 文件


本主题演示 OMA DM 设备描述框架 (DDF) WindowsSecurityAuditing 配置服务提供程序。 Windows 10 1511年版本中添加了该 CSP。

``` syntax
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE MgmtTree PUBLIC " -//OMA//DTD-DM-DDF 1.2//EN"
    "http://www.openmobilealliance.org/tech/DTD/DM_DDF-V1_2.dtd"
    [<?oma-dm-ddf-ver supported-versions="1.2"?>]>
<MgmtTree xmlns:MSFT="http://schemas.microsoft.com/MobileDevice/DM">
    <VerDTD>1.2</VerDTD>
    <Node>
        <NodeName>WindowsSecurityAuditing</NodeName>
        <Path>./Vendor/MSFT</Path>
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
                <MIME>com.microsoft/1.0/MDM/WindowsSecurityAuditing</MIME>
            </DFType>
        </DFProperties>
        <Node>
            <NodeName>ConfigurationSettings</NodeName>
            <DFProperties>
                <AccessType>
                    <Get />
                </AccessType>
                <Description>This branch handles all the audit configuration settings for the device. This node should not be used for a get/set but is simply a grouping interior node for all configuration functionality.</Description>
                <DFFormat>
                    <node />
                </DFFormat>
                <Occurrence>
                    <One />
                </Occurrence>
                <Scope>
                    <Permanent />
                </Scope>
                <DFTitle>Configuration Settings</DFTitle>
                <DFType>
                    <DDFName></DDFName>
                </DFType>
            </DFProperties>
            <Node>
                <NodeName>EnableSecurityAuditing</NodeName>
                <DFProperties>
                    <AccessType>
                        <Get />
                        <Replace />
                    </AccessType>
                    <DefaultValue>false</DefaultValue>
                    <Description>Specifies whether to enable or disable auditing for the device. If the value is true, a default set of audit events will be captured to a log file for upload. If the value is false, auditing will be disabled and events will no longer be logged. </Description>
                    <DFFormat>
                        <bool />
                    </DFFormat>
                    <Occurrence>
                        <One />
                    </Occurrence>
                    <Scope>
                        <Permanent />
                    </Scope>
                    <DFTitle>Enable Security Auditing</DFTitle>
                    <DFType>
                        <MIME>text/plain</MIME>
                    </DFType>
                </DFProperties>
            </Node>
        </Node>
    </Node>
</MgmtTree>
```

 

 






