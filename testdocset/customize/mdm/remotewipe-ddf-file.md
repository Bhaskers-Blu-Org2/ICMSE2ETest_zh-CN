---
title: "RemoteWipe DDF 文件"
description: "RemoteWipe DDF 文件"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 10ec4fb7-f911-4d0c-9a8f-e96bf5faea0c
ms.openlocfilehash: 742c89f07634acc2c4237673edfa7be49e7b10c4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="remotewipe-ddf-file"></a>RemoteWipe DDF 文件


本主题演示 OMA DM 设备描述框架 (DDF) **RemoteWipe**配置服务提供程序。 DDF 文件只能用于提供 XML 的 OMA DM。

``` syntax
<?xml version="1.0" encoding="UTF-8"?>  
<!--  
Copyright (c) Microsoft Corporation.  All rights reserved.  
-->  
<!--  
Use of this source code is subject to the terms of the Microsoft  
premium shared source license agreement under which you licensed  
this source code. If you did not accept the terms of the license  
agreement, you are not authorized to use this source code.  
For the terms of the license, please see the license agreement  
signed by you and Microsoft.  
THE SOURCE CODE IS PROVIDED "AS IS", WITH NO WARRANTIES OR INDEMNITIES.  
-->  
<!DOCTYPE MgmtTree PUBLIC " -//OMA//DTD-DM-DDF 1.2//EN" "http://www.openmobilealliance.org/tech/DTD/DM_DDF-V1_2.dtd" [<?oma-dm-ddf-ver supported-versions="1.2"?>]>  
<MgmtTree xmlns:MSFT="http://schemas.microsoft.com/MobileDevice/DM">  
    <VerDTD>1.2</VerDTD>  
    <Node>  
        <NodeName>RemoteWipe</NodeName>  
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
                <MIME>com.microsoft/1.0/MDM/RemoteWipe</MIME>  
            </DFType>  
        </DFProperties>  
        <Node>  
            <NodeName>doWipe</NodeName>  
            <DFProperties>  
                <AccessType>  
                    <Exec />  
                </AccessType>  
                <Description>Exec on this node will perform a remote wipe on the device. The return status code shows whether the device accepted the Exec command.</Description>  
                <DFFormat>  
                    <chr />  
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
        <Node>  
            <NodeName>doWipePersistProvisionedData</NodeName>  
            <DFProperties>  
                <AccessType>  
                    <Exec />  
                </AccessType>  
                <Description>Exec on this node will back up provisioning data to a persistent location and perform a remote wipe on the device. The information that was backed up will be restored and applied to the device when it resumes. The return status code shows whether the device accepted the Exec command.</Description>  
                <DFFormat>  
                    <chr />  
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
</MgmtTree>
```

## <a name="related-topics"></a>相关的主题


[RemoteWipe 配置服务提供程序](remotewipe-csp.md)

 

 






