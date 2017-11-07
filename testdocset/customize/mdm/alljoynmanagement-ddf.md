---
title: AllJoynManagement DDF
description: AllJoynManagement DDF
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 540C2E60-A041-4749-A027-BBAF0BB046E4
ms.openlocfilehash: fd9635d976e069055f63725085d0c4c56235dbbb
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="alljoynmanagement-ddf"></a>AllJoynManagement DDF


本主题演示 OMA DM 设备描述框架 (DDF) **AllJoynManagement**配置服务提供程序。 Windows 10 1511年版本中添加了该 CSP。

``` syntax
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE MgmtTree PUBLIC " -//OMA//DTD-DM-DDF 1.2//EN"
    "http://www.openmobilealliance.org/tech/DTD/DM_DDF-V1_2.dtd"
    [<?oma-dm-ddf-ver supported-versions="1.2"?>]>
<MgmtTree xmlns:MSFT="http://schemas.microsoft.com/MobileDevice/DM">
    <VerDTD>1.2</VerDTD>
    <Node>
        <NodeName>AllJoynManagement</NodeName>
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
                <DDFName></DDFName>
            </DFType>
        </DFProperties>
        <Node>
            <NodeName>Services</NodeName>
            <DFProperties>
                <AccessType>
                    <Get />
                </AccessType>
                <Description>This is the list of AllJoyn Objects that are discovered on the AllJoyn bus.  Only AllJoyn Objects that expose the "com.microsoft.alljoynmanagement.config" will be shown here.</Description>
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
                <NodeName></NodeName>
                <DFProperties>
                    <AccessType>
                        <Get />
                    </AccessType>
                    <Description>The Unique AllJoyn About Device ID, a GUID, that Hosts one or more configurable objects
.
</Description>
                    <DFFormat>
                        <node />
                    </DFFormat>
                    <Occurrence>
                        <ZeroOrMore />
                    </Occurrence>
                    <Scope>
                        <Dynamic />
                    </Scope>
                    <DFTitle>ServiceID</DFTitle>
                    <DFType>
                        <DDFName></DDFName>
                    </DFType>
                </DFProperties>
                <Node>
                    <NodeName>Port</NodeName>
                    <DFProperties>
                        <AccessType>
                            <Get />
                        </AccessType>
                        <Description>The set of Ports that this AllJoyn Object uses to communicate configuration settings through.  

Typically, only one port is used for communication, but it is possible that additional ports may be specified.</Description>
                        <DFFormat>
                            <node />
                        </DFFormat>
                        <Occurrence>
                            <One />
                        </Occurrence>
                        <Scope>
                            <Dynamic />
                        </Scope>
                        <DFType>
                            <DDFName></DDFName>
                        </DFType>
                    </DFProperties>
                    <Node>
                        <NodeName></NodeName>
                        <DFProperties>
                            <AccessType>
                                <Get />
                            </AccessType>
                            <Description>The AllJoyn Port Number to communicate on.  This is specified by the Configurable AllJoyn Object and is reflected here.</Description>
                            <DFFormat>
                                <node />
                            </DFFormat>
                            <Occurrence>
                                <One />
                            </Occurrence>
                            <Scope>
                                <Dynamic />
                            </Scope>
                            <DFTitle>PortNum</DFTitle>
                            <DFType>
                                <DDFName></DDFName>
                            </DFType>
                        </DFProperties>
                        <Node>
                            <NodeName>CfgObject</NodeName>
                            <DFProperties>
                                <AccessType>
                                    <Get />
                                </AccessType>
                                <Description>The set of configurable interfaces that are available on the Port of the AllJoyn Object</Description>
                                <DFFormat>
                                    <node />
                                </DFFormat>
                                <Occurrence>
                                    <One />
                                </Occurrence>
                                <Scope>
                                    <Dynamic />
                                </Scope>
                                <DFType>
                                    <DDFName></DDFName>
                                </DFType>
                            </DFProperties>
                            <Node>
                                <NodeName></NodeName>
                                <DFProperties>
                                    <AccessType>
                                        <Get />
                                    </AccessType>
                                    <Description>The remainder of this URI is an escaped path to the Configurable AllJoyn Object Hosted by the parent ServiceID and Accessible by the parent PortNum.

For example an AllJoyn Bridge with the Microsoft specific AllJoyn Configuration Interface "\ASBService\BridgeConfig" would be specified in the URI as: %2FASBService%2FBridgeConfig
</Description>
                                    <DFFormat>
                                        <b64 />
                                    </DFFormat>
                                    <Occurrence>
                                        <OneOrMore />
                                    </Occurrence>
                                    <Scope>
                                        <Dynamic />
                                    </Scope>
                                    <DFTitle>CfgObjectPath</DFTitle>
                                    <DFType>
                                        <DDFName></DDFName>
                                    </DFType>
                                </DFProperties>
                            </Node>
                        </Node>
                    </Node>
                </Node>
            </Node>
        </Node>
        <Node>
            <NodeName>Credentials</NodeName>
            <DFProperties>
                <AccessType>
                    <Get />
                </AccessType>
                <Description>This is the Credential Store.  An Administrator can set credentials for each AllJoyn device that requires authentication at this node.  
If a SYNCML request arrives in the CSP to replace or query a configuration item on an AllJoyn Object that requires authentication, then the CSP will use the Credentials stored here during the authentication phase.

</Description>
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
                <NodeName></NodeName>
                <DFProperties>
                    <AccessType>
                        <Get />
                    </AccessType>
                    <Description>This is the same ServiceID as specified in the \AllJoynManagement\Services\ServiceID URI.

It is typically implemented as a GUID.</Description>
                    <DFFormat>
                        <node />
                    </DFFormat>
                    <Occurrence>
                        <ZeroOrMore />
                    </Occurrence>
                    <Scope>
                        <Dynamic />
                    </Scope>
                    <CaseSense>
                        <CIS />
                    </CaseSense>
                    <DFTitle>ServiceID</DFTitle>
                    <DFType>
                        <DDFName></DDFName>
                    </DFType>
                </DFProperties>
                <Node>
                    <NodeName>Key</NodeName>
                    <DFProperties>
                        <AccessType>
                            <Get />
                            <Replace />
                        </AccessType>
                        <Description>An Alphanumeric KEY value that conforms to the AllJoyn SRP KEYX Authentication Standard</Description>
                        <DFFormat>
                            <chr />
                        </DFFormat>
                        <Occurrence>
                            <One />
                        </Occurrence>
                        <Scope>
                            <Dynamic />
                        </Scope>
                        <CaseSense>
                            <CS />
                        </CaseSense>
                        <DFType>
                            <MIME>text/plain</MIME>
                        </DFType>
                    </DFProperties>
                </Node>
            </Node>
        </Node>
        <Node>
            <NodeName>Firewall</NodeName>
            <DFProperties>
                <AccessType>
                    <Get />
                </AccessType>
                <Description>Firewall setting for the AllJoyn service (AJRouter.dll).</Description>
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
                <NodeName>PublicProfile</NodeName>
                <DFProperties>
                    <AccessType>
                        <Get />
                        <Replace />
                    </AccessType>
                    <Description>Boolean value to enable or disable the AllJoyn router service (AJRouter.dll) for Public network profile.</Description>
                    <DFFormat>
                        <bool />
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
                <NodeName>PrivateProfile</NodeName>
                <DFProperties>
                    <AccessType>
                        <Get />
                    </AccessType>
                    <Description>Boolean value indicating whether AllJoyn router service (AJRouter.dll) is enabled for Private network profile.</Description>
                    <DFFormat>
                        <bool />
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

## <a name="related-topics"></a>相关的主题


[AllJoynManagement 配置服务提供程序](alljoynmanagement-csp.md)

 

 






