---
title: "AppLocker DDF 文件"
description: "AppLocker DDF 文件"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 79E199E0-5454-413A-A57A-B536BDA22496
ms.openlocfilehash: cae6843597fe38e111eaffa1802e0c969a34d909
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="applocker-ddf-file"></a>AppLocker DDF 文件


本主题演示 OMA DM 设备描述框架 (DDF) **AppLocker**配置服务提供程序。 DDF 文件只能用于提供 XML 的 OMA DM。

``` syntax
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE MgmtTree PUBLIC " -//OMA//DTD-DM-DDF 1.2//EN"
    "http://www.openmobilealliance.org/tech/DTD/DM_DDF-V1_2.dtd"
    [<?oma-dm-ddf-ver supported-versions="1.2"?>]>
<MgmtTree xmlns:MSFT="http://schemas.microsoft.com/MobileDevice/DM">
    <VerDTD>1.2</VerDTD>
    <Node>
        <NodeName>AppLocker</NodeName>
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
            <NodeName>ApplicationLaunchRestrictions</NodeName>
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
                <CaseSense>
                    <CIS />
                </CaseSense>
                <DFType>
                    <DDFName></DDFName>
                </DFType>
            </DFProperties>
            <Node>
                <NodeName></NodeName>
                <DFProperties>
                    <AccessType>
                        <Add />
                        <Delete />
                        <Get />
                        <Replace />
                    </AccessType>
                    <DFFormat>
                        <node />
                    </DFFormat>
                    <Occurrence>
                        <ZeroOrMore />
                    </Occurrence>
                    <Scope>
                        <Dynamic />
                    </Scope>
                    <DFTitle>Grouping</DFTitle>
                    <DFType>
                        <DDFName></DDFName>
                    </DFType>
                </DFProperties>
                <Node>
                    <NodeName>EXE</NodeName>
                    <DFProperties>
                        <AccessType>
                            <Add />
                            <Delete />
                            <Get />
                            <Replace />
                        </AccessType>
                        <DFFormat>
                            <node />
                        </DFFormat>
                        <Occurrence>
                            <ZeroOrOne />
                        </Occurrence>
                        <Scope>
                            <Dynamic />
                        </Scope>
                        <DFType>
                            <DDFName></DDFName>
                        </DFType>
                    </DFProperties>
                    <Node>
                        <NodeName>Policy</NodeName>
                        <DFProperties>
                            <AccessType>
                                <Add />
                                <Delete />
                                <Get />
                                <Replace />
                            </AccessType>
                            <DFFormat>
                                <chr />
                            </DFFormat>
                            <Occurrence>
                                <ZeroOrOne />
                            </Occurrence>
                            <Scope>
                                <Dynamic />
                            </Scope>
                            <DFType>
                                <MIME>text/plain</MIME>
                            </DFType>
                        </DFProperties>
                    </Node>
                    <Node>
                        <NodeName>EnforcementMode</NodeName>
                        <DFProperties>
                            <AccessType>
                                <Add />
                                <Delete />
                                <Get />
                                <Replace />
                            </AccessType>
                            <DFFormat>
                                <chr />
                            </DFFormat>
                            <Occurrence>
                                <ZeroOrOne />
                            </Occurrence>
                            <Scope>
                                <Dynamic />
                            </Scope>
                            <DFType>
                                <MIME>text/plain</MIME>
                            </DFType>
                        </DFProperties>
                    </Node>
                    <Node>
                        <NodeName>NonInteractiveProcessEnforcement</NodeName>
                        <DFProperties>
                            <AccessType>
                                <Add />
                                <Delete />
                                <Get />
                                <Replace />
                            </AccessType>
                            <DFFormat>
                                <chr />
                            </DFFormat>
                            <Occurrence>
                                <ZeroOrOne />
                            </Occurrence>
                            <Scope>
                                <Dynamic />
                            </Scope>
                            <DFType>
                                <MIME>text/plain</MIME>
                            </DFType>
                        </DFProperties>
                    </Node>
                </Node>
                <Node>
                    <NodeName>MSI</NodeName>
                    <DFProperties>
                        <AccessType>
                            <Add />
                            <Delete />
                            <Get />
                            <Replace />
                        </AccessType>
                        <DFFormat>
                            <node />
                        </DFFormat>
                        <Occurrence>
                            <ZeroOrOne />
                        </Occurrence>
                        <Scope>
                            <Dynamic />
                        </Scope>
                        <DFType>
                            <DDFName></DDFName>
                        </DFType>
                    </DFProperties>
                    <Node>
                        <NodeName>Policy</NodeName>
                        <DFProperties>
                            <AccessType>
                                <Add />
                                <Delete />
                                <Get />
                                <Replace />
                            </AccessType>
                            <DFFormat>
                                <chr />
                            </DFFormat>
                            <Occurrence>
                                <ZeroOrOne />
                            </Occurrence>
                            <Scope>
                                <Dynamic />
                            </Scope>
                            <DFType>
                                <MIME>text/plain</MIME>
                            </DFType>
                        </DFProperties>
                    </Node>
                    <Node>
                        <NodeName>EnforcementMode</NodeName>
                        <DFProperties>
                            <AccessType>
                                <Add />
                                <Delete />
                                <Get />
                                <Replace />
                            </AccessType>
                            <DFFormat>
                                <chr />
                            </DFFormat>
                            <Occurrence>
                                <ZeroOrOne />
                            </Occurrence>
                            <Scope>
                                <Dynamic />
                            </Scope>
                            <DFType>
                                <MIME>text/plain</MIME>
                            </DFType>
                        </DFProperties>
                    </Node>
                </Node>
                <Node>
                    <NodeName>Script</NodeName>
                    <DFProperties>
                        <AccessType>
                            <Add />
                            <Delete />
                            <Get />
                            <Replace />
                        </AccessType>
                        <DFFormat>
                            <node />
                        </DFFormat>
                        <Occurrence>
                            <ZeroOrOne />
                        </Occurrence>
                        <Scope>
                            <Dynamic />
                        </Scope>
                        <DFType>
                            <DDFName></DDFName>
                        </DFType>
                    </DFProperties>
                    <Node>
                        <NodeName>Policy</NodeName>
                        <DFProperties>
                            <AccessType>
                                <Add />
                                <Delete />
                                <Get />
                                <Replace />
                            </AccessType>
                            <DFFormat>
                                <chr />
                            </DFFormat>
                            <Occurrence>
                                <ZeroOrOne />
                            </Occurrence>
                            <Scope>
                                <Dynamic />
                            </Scope>
                            <DFType>
                                <MIME>text/plain</MIME>
                            </DFType>
                        </DFProperties>
                    </Node>
                    <Node>
                        <NodeName>EnforcementMode</NodeName>
                        <DFProperties>
                            <AccessType>
                                <Add />
                                <Delete />
                                <Get />
                                <Replace />
                            </AccessType>
                            <DFFormat>
                                <chr />
                            </DFFormat>
                            <Occurrence>
                                <ZeroOrOne />
                            </Occurrence>
                            <Scope>
                                <Dynamic />
                            </Scope>
                            <DFType>
                                <MIME>text/plain</MIME>
                            </DFType>
                        </DFProperties>
                    </Node>
                </Node>
                <Node>
                    <NodeName>StoreApps</NodeName>
                    <DFProperties>
                        <AccessType>
                            <Add />
                            <Delete />
                            <Get />
                            <Replace />
                        </AccessType>
                        <DFFormat>
                            <node />
                        </DFFormat>
                        <Occurrence>
                            <ZeroOrOne />
                        </Occurrence>
                        <Scope>
                            <Dynamic />
                        </Scope>
                        <DFType>
                            <DDFName></DDFName>
                        </DFType>
                    </DFProperties>
                    <Node>
                        <NodeName>Policy</NodeName>
                        <DFProperties>
                            <AccessType>
                                <Add />
                                <Delete />
                                <Get />
                                <Replace />
                            </AccessType>
                            <DFFormat>
                                <chr />
                            </DFFormat>
                            <Occurrence>
                                <ZeroOrOne />
                            </Occurrence>
                            <Scope>
                                <Dynamic />
                            </Scope>
                            <DFType>
                                <MIME>text/plain</MIME>
                            </DFType>
                        </DFProperties>
                    </Node>
                    <Node>
                        <NodeName>EnforcementMode</NodeName>
                        <DFProperties>
                            <AccessType>
                                <Add />
                                <Delete />
                                <Get />
                                <Replace />
                            </AccessType>
                            <DFFormat>
                                <chr />
                            </DFFormat>
                            <Occurrence>
                                <ZeroOrOne />
                            </Occurrence>
                            <Scope>
                                <Dynamic />
                            </Scope>
                            <DFType>
                                <MIME>text/plain</MIME>
                            </DFType>
                        </DFProperties>
                    </Node>
                </Node>
                <Node>
                    <NodeName>DLL</NodeName>
                    <DFProperties>
                        <AccessType>
                            <Add />
                            <Delete />
                            <Get />
                            <Replace />
                        </AccessType>
                        <DFFormat>
                            <node />
                        </DFFormat>
                        <Occurrence>
                            <ZeroOrOne />
                        </Occurrence>
                        <Scope>
                            <Dynamic />
                        </Scope>
                        <DFType>
                            <DDFName></DDFName>
                        </DFType>
                    </DFProperties>
                    <Node>
                        <NodeName>Policy</NodeName>
                        <DFProperties>
                            <AccessType>
                                <Add />
                                <Delete />
                                <Get />
                                <Replace />
                            </AccessType>
                            <DFFormat>
                                <chr />
                            </DFFormat>
                            <Occurrence>
                                <ZeroOrOne />
                            </Occurrence>
                            <Scope>
                                <Dynamic />
                            </Scope>
                            <DFType>
                                <MIME>text/plain</MIME>
                            </DFType>
                        </DFProperties>
                    </Node>
                    <Node>
                        <NodeName>EnforcementMode</NodeName>
                        <DFProperties>
                            <AccessType>
                                <Add />
                                <Delete />
                                <Get />
                                <Replace />
                            </AccessType>
                            <DFFormat>
                                <chr />
                            </DFFormat>
                            <Occurrence>
                                <ZeroOrOne />
                            </Occurrence>
                            <Scope>
                                <Dynamic />
                            </Scope>
                            <DFType>
                                <MIME>text/plain</MIME>
                            </DFType>
                        </DFProperties>
                    </Node>
                    <Node>
                        <NodeName>NonInteractiveProcessEnforcement</NodeName>
                        <DFProperties>
                            <AccessType>
                                <Add />
                                <Delete />
                                <Get />
                                <Replace />
                            </AccessType>
                            <DFFormat>
                                <chr />
                            </DFFormat>
                            <Occurrence>
                                <One />
                            </Occurrence>
                            <Scope>
                                <Dynamic />
                            </Scope>
                            <DFType>
                                <MIME>text/plain</MIME>
                            </DFType>
                        </DFProperties>
                    </Node>
                </Node>
                <Node>
                    <NodeName>CodeIntegrity</NodeName>
                    <DFProperties>
                        <AccessType>
                            <Add />
                            <Delete />
                            <Get />
                            <Replace />
                        </AccessType>
                        <DFFormat>
                            <node />
                        </DFFormat>
                        <Occurrence>
                            <ZeroOrOne />
                        </Occurrence>
                        <Scope>
                            <Dynamic />
                        </Scope>
                        <DFType>
                            <DDFName></DDFName>
                        </DFType>
                    </DFProperties>
                    <Node>
                        <NodeName>Policy</NodeName>
                        <DFProperties>
                            <AccessType>
                                <Add />
                                <Delete />
                                <Get />
                                <Replace />
                            </AccessType>
                            <DFFormat>
                                <b64 />
                            </DFFormat>
                            <Occurrence>
                                <ZeroOrOne />
                            </Occurrence>
                            <Scope>
                                <Dynamic />
                            </Scope>
                            <DFType>
                                <MIME>text/plain</MIME>
                            </DFType>
                        </DFProperties>
                    </Node>
                </Node>
            </Node>
        </Node>
        <Node>
            <NodeName>EnterpriseDataProtection</NodeName>
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
                <NodeName></NodeName>
                <DFProperties>
                    <AccessType>
                        <Add />
                        <Delete />
                        <Get />
                        <Replace />
                    </AccessType>
                    <DFFormat>
                        <node />
                    </DFFormat>
                    <Occurrence>
                        <ZeroOrMore />
                    </Occurrence>
                    <Scope>
                        <Dynamic />
                    </Scope>
                    <DFTitle>Grouping</DFTitle>
                    <DFType>
                        <DDFName></DDFName>
                    </DFType>
                </DFProperties>
                <Node>
                    <NodeName>EXE</NodeName>
                    <DFProperties>
                        <AccessType>
                            <Add />
                            <Delete />
                            <Get />
                            <Replace />
                        </AccessType>
                        <DFFormat>
                            <node />
                        </DFFormat>
                        <Occurrence>
                            <ZeroOrOne />
                        </Occurrence>
                        <Scope>
                            <Dynamic />
                        </Scope>
                        <DFType>
                            <DDFName></DDFName>
                        </DFType>
                    </DFProperties>
                    <Node>
                        <NodeName>Policy</NodeName>
                        <DFProperties>
                            <AccessType>
                                <Add />
                                <Delete />
                                <Get />
                                <Replace />
                            </AccessType>
                            <DFFormat>
                                <chr />
                            </DFFormat>
                            <Occurrence>
                                <ZeroOrOne />
                            </Occurrence>
                            <Scope>
                                <Dynamic />
                            </Scope>
                            <DFType>
                                <MIME>text/plain</MIME>
                            </DFType>
                        </DFProperties>
                    </Node>
                </Node>
                <Node>
                    <NodeName>StoreApps</NodeName>
                    <DFProperties>
                        <AccessType>
                            <Add />
                            <Delete />
                            <Get />
                            <Replace />
                        </AccessType>
                        <DFFormat>
                            <node />
                        </DFFormat>
                        <Occurrence>
                            <ZeroOrOne />
                        </Occurrence>
                        <Scope>
                            <Dynamic />
                        </Scope>
                        <DFType>
                            <DDFName></DDFName>
                        </DFType>
                    </DFProperties>
                    <Node>
                        <NodeName>Policy</NodeName>
                        <DFProperties>
                            <AccessType>
                                <Add />
                                <Delete />
                                <Get />
                                <Replace />
                            </AccessType>
                            <DFFormat>
                                <chr />
                            </DFFormat>
                            <Occurrence>
                                <ZeroOrOne />
                            </Occurrence>
                            <Scope>
                                <Dynamic />
                            </Scope>
                            <DFType>
                                <MIME>text/plain</MIME>
                            </DFType>
                        </DFProperties>
                    </Node>
                </Node>
            </Node>
        </Node>
    </Node>
</MgmtTree>
```

## <a name="related-topics"></a>相关的主题


[AppLocker 配置服务提供程序](applocker-csp.md)

 

 






