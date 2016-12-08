---
title: "DDF 注册表文件"
description: "DDF 注册表文件"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 29b5cc07-f349-4567-8a77-387d816a9d15
ms.openlocfilehash: b17050e38d38ac4534886d08d4a72c6dc02df5fe
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="registry-ddf-file"></a>DDF 注册表文件


本主题演示 OMA DM 设备描述框架 (DDF)**注册表**配置服务提供程序。 DDF 文件只能用于提供 XML 的 OMA DM。

``` syntax
<MgmtTree xmlns:MSFT="http://schemas.microsoft.com/MobileDevice/DM">
    <VerDTD>1.2</VerDTD>
    <Node>
        <NodeName>Registry</NodeName>
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
            <Description>The root node of registry</Description>
        </DFProperties>
        <Node>
            <NodeName>HKCR</NodeName>
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
                <Description>HK_CLASSES_ROOT portion of device registry.</Description>
            </DFProperties>
        </Node>
        <Node>
            <NodeName>HKCU</NodeName>
            <DFProperties>
                <AccessType>
                    <Get />
                </AccessType>
                <DFFormat>
                    <node />
                </DFFormat>
                <Occurrence>
                    <ZeroOrMore />
                </Occurrence>
                <Scope>
                    <Permanent />
                </Scope>
                <Description>HK_CURRENT_USER portion of device registry.</Description>
             </DFProperties>
        </Node>
        <Node>
            <NodeName>HKLM</NodeName>
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
                <Description>HK_LOCAL_MACHINE portion of device registry.</Description>
            </DFProperties>
        </Node>
        <Node>
            <NodeName>HKU</NodeName>
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
                <Description>HK_USERS portion of device registry.</Description>
            </DFProperties>
        </Node>
    </Node>
</MgmtTree>
```

## <a name="related-topics"></a>相关的主题


[注册表配置服务提供程序](registry-csp.md)

 

 






