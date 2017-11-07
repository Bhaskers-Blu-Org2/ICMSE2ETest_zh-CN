---
title: "DDF VPN 文件"
description: "DDF VPN 文件"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 728FCD9C-0B8E-413B-B54A-CD72C9F2B9EE
ms.openlocfilehash: 3ff09bf5e8aadaafb7747ebd512f30028b917ded
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="vpn-ddf-file"></a>DDF VPN 文件


本主题演示 OMA DM 设备描述框架 (DDF) **VPN**配置服务提供程序。 DDF 文件只能用于提供 XML 的 OMA DM。

``` syntax
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE MgmtTree PUBLIC "-//OMA//DTD-DM-DDF 1.2//EN"
    "http://www.openmobilealliance.org/tech/DTD/DM_DDF-V1_2.dtd"
    [
  <?oma-dm-ddf-ver supported-versions="1.2"?>
]>
<MgmtTree xmlns:MSFT="http://schemas.microsoft.com/MobileDevice/DM">
  <VerDTD>1.2</VerDTD>
  <Node>
    <NodeName>MSFT</NodeName>
    <Path>./Vendor</Path>
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
        <Dynamic />
      </Scope>
      <DFType>
        <DDFName></DDFName>
      </DFType>
    </DFProperties>
    <Node>
      <NodeName>VPN</NodeName>
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
          <Dynamic />
        </Scope>
        <CaseSense>
          <CS />
        </CaseSense>
        <DFTitle>Root</DFTitle>
        <DFType>
          <DDFName></DDFName>
        </DFType>
      </DFProperties>
      <Node>
        <NodeName></NodeName>
        <DFProperties>
          <AccessType>
            <Add />
            <Get />
            <Delete />
            <Replace />
          </AccessType>
          <DFFormat>
            <node />
          </DFFormat>
          <Occurrence>
            <One />
          </Occurrence>
          <Scope>
            <Dynamic />
          </Scope>
          <CaseSense>
            <CIS />
          </CaseSense>
          <DFTitle>Profile Name</DFTitle>
          <DFType>
            <DDFName></DDFName>
          </DFType>
        </DFProperties>
        <Node>
          <NodeName>Server</NodeName>
          <DFProperties>
            <AccessType>
              <Add />
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
            <CaseSense>
              <CIS />
            </CaseSense>
            <DFTitle>VPN Gateway Server</DFTitle>
            <DFType>
              <MIME>text/plain</MIME>
            </DFType>
          </DFProperties>
        </Node>
        <Node>
          <NodeName>TunnelType</NodeName>
          <DFProperties>
            <AccessType>
              <Add />
              <Get />
              <Delete />
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
            <CaseSense>
              <CIS />
            </CaseSense>
            <DFTitle>TunnelType</DFTitle>
            <DFType>
              <MIME>text/plain</MIME>
            </DFType>
          </DFProperties>
        </Node>
        <Node>
          <NodeName>ThirdParty</NodeName>
          <DFProperties>
            <AccessType>
              <Add />
              <Get />
              <Delete />
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
            <DFTitle>Third Party</DFTitle>
            <DFType>
              <DDFName></DDFName>
            </DFType>
          </DFProperties>
          <Node>
            <NodeName>Name</NodeName>
            <DFProperties>
              <AccessType>
                <Add />
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
              <CaseSense>
                <CIS />
              </CaseSense>
              <DFTitle>Third Party Name</DFTitle>
              <DFType>
                <MIME>text/plain</MIME>
              </DFType>
            </DFProperties>
          </Node>
          <Node>
            <NodeName>AppID</NodeName>
            <DFProperties>
              <AccessType>
                <Add />
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
              <DFTitle>APPID</DFTitle>
              <DFType>
                <MIME>text/plain</MIME>
              </DFType>
            </DFProperties>
          </Node>
          <Node>
            <NodeName>CustomStoreURL</NodeName>
            <DFProperties>
              <AccessType>
                <Add />
                <Get />
                <Delete />
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
              <CaseSense>
                <CIS />
              </CaseSense>
              <DFTitle>Custom Store URL</DFTitle>
              <DFType>
                <MIME>text/plain</MIME>
              </DFType>
            </DFProperties>
          </Node>
          <Node>
            <NodeName>CustomConfiguration</NodeName>
            <DFProperties>
              <AccessType>
                <Add />
                <Get />
                <Delete />
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
              <CaseSense>
                <CIS />
              </CaseSense>
              <DFTitle>Custom Configuration</DFTitle>
              <DFType>
                <MIME>text/plain</MIME>
              </DFType>
            </DFProperties>
          </Node>
        </Node>
        <Node>
          <NodeName>RoleOrGroup</NodeName>
          <DFProperties>
            <AccessType>
              <Add />
              <Get />
              <Delete />
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
            <CaseSense>
              <CIS />
            </CaseSense>
            <DFTitle>RoleOrGroup</DFTitle>
            <DFType>
              <MIME>text/plain</MIME>
            </DFType>
          </DFProperties>
        </Node>
        <Node>
          <NodeName>Authentication</NodeName>
          <DFProperties>
            <AccessType>
              <Add />
              <Get />
              <Replace />
            </AccessType>
            <DFFormat>
              <node />
            </DFFormat>
            <Occurrence>
              <One />
            </Occurrence>
            <Scope>
              <Dynamic />
            </Scope>
            <CaseSense>
              <CIS />
            </CaseSense>
            <DFTitle>Authentication</DFTitle>
            <DFType>
              <DDFName></DDFName>
            </DFType>
          </DFProperties>
          <Node>
            <NodeName>Method</NodeName>
            <DFProperties>
              <AccessType>
                <Add />
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
              <CaseSense>
                <CIS />
              </CaseSense>
              <DFTitle>Method</DFTitle>
              <DFType>
                <MIME>text/plain</MIME>
              </DFType>
            </DFProperties>
          </Node>
          <Node>
            <NodeName>Certificate</NodeName>
            <DFProperties>
              <AccessType>
                <Add />
                <Get />
                <Delete />
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
              <CaseSense>
                <CIS />
              </CaseSense>
              <DFTitle>Certificate</DFTitle>
              <DFType>
                <DDFName></DDFName>
              </DFType>
            </DFProperties>
            <Node>
              <NodeName>Issuer</NodeName>
              <DFProperties>
                <AccessType>
                  <Add />
                  <Get />
                  <Delete />
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
                <CaseSense>
                  <CIS />
                </CaseSense>
                <DFTitle>Issuer</DFTitle>
                <DFType>
                  <MIME>text/plain</MIME>
                </DFType>
              </DFProperties>
            </Node>
            <Node>
              <NodeName>EKU</NodeName>
              <DFProperties>
                <AccessType>
                  <Add />
                  <Get />
                  <Delete />
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
                <CaseSense>
                  <CIS />
                </CaseSense>
                <DFTitle>EKU</DFTitle>
                <DFType>
                  <MIME>text/plain</MIME>
                </DFType>
              </DFProperties>
            </Node>
            <Node>
              <NodeName>ChacheLifeTimeForProtectedCert</NodeName>
              <DFProperties>
                <AccessType>
                  <Add />
                  <Get />
                  <Delete />
                  <Replace />
                </AccessType>
                <DFFormat>
                  <int />
                </DFFormat>
                <Occurrence>
                  <One />
                </Occurrence>
                <Scope>
                  <Dynamic />
                </Scope>
                <CaseSense>
                  <CIS />
                </CaseSense>
                <DFTitle>ChacheLifeTimeForProtectedCert</DFTitle>
                <DFType>
                  <MIME>text/plain</MIME>
                </DFType>
              </DFProperties>
            </Node>
          </Node>
          <Node>
            <NodeName>MultiAuth</NodeName>
            <DFProperties>
              <AccessType>
                <Add />
                <Get />
                <Delete />
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
              <CaseSense>
                <CIS />
              </CaseSense>
              <DFTitle>MultiAuth</DFTitle>
              <DFType>
                <DDFName></DDFName>
              </DFType>
            </DFProperties>
            <Node>
              <NodeName>StartURL</NodeName>
              <DFProperties>
                <AccessType>
                  <Add />
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
                <CaseSense>
                  <CIS />
                </CaseSense>
                <DFTitle>StartURL</DFTitle>
                <DFType>
                  <MIME>text/plain</MIME>
                </DFType>
              </DFProperties>
            </Node>
            <Node>
              <NodeName>EndURL</NodeName>
              <DFProperties>
                <AccessType>
                  <Add />
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
                <CaseSense>
                  <CIS />
                </CaseSense>
                <DFTitle>EndURL</DFTitle>
                <DFType>
                  <MIME>text/plain</MIME>
                </DFType>
              </DFProperties>
            </Node>
          </Node>
          <Node>
            <NodeName>EAP</NodeName>
            <DFProperties>
              <AccessType>
                <Add />
                <Get />
                <Delete />
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
              <CaseSense>
                <CIS />
              </CaseSense>
              <DFTitle>EAP</DFTitle>
              <DFType>
                <MIME>text/plain</MIME>
              </DFType>
            </DFProperties>
          </Node>
        </Node>
        <Node>
          <NodeName>Proxy</NodeName>
          <DFProperties>
            <AccessType>
              <Add />
              <Get />
              <Replace />
            </AccessType>
            <DFFormat>
              <node />
            </DFFormat>
            <Occurrence>
              <One />
            </Occurrence>
            <Scope>
              <Dynamic />
            </Scope>
            <CaseSense>
              <CIS />
            </CaseSense>
            <DFTitle>Proxy</DFTitle>
            <DFType>
              <DDFName></DDFName>
            </DFType>
          </DFProperties>
          <Node>
            <NodeName>Automatic</NodeName>
            <DFProperties>
              <AccessType>
                <Add />
                <Get />
                <Delete />
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
              <CaseSense>
                <CIS />
              </CaseSense>
              <DFTitle>Automatic</DFTitle>
              <DFType>
                <MIME>text/plain</MIME>
              </DFType>
            </DFProperties>
          </Node>
          <Node>
            <NodeName>Manual</NodeName>
            <DFProperties>
              <AccessType>
                <Add />
                <Get />
                <Delete />
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
              <CaseSense>
                <CIS />
              </CaseSense>
              <DFTitle>Manual</DFTitle>
              <DFType>
                <DDFName></DDFName>
              </DFType>
            </DFProperties>
            <Node>
              <NodeName>Server</NodeName>
              <DFProperties>
                <AccessType>
                  <Add />
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
                <CaseSense>
                  <CIS />
                </CaseSense>
                <DFTitle>Server</DFTitle>
                <DFType>
                  <MIME>text/plain</MIME>
                </DFType>
              </DFProperties>
            </Node>
            <Node>
              <NodeName>Port</NodeName>
              <DFProperties>
                <AccessType>
                  <Add />
                  <Get />
                  <Replace />
                </AccessType>
                <DFFormat>
                  <int />
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
                <DFTitle>Port</DFTitle>
                <DFType>
                  <MIME>text/plain</MIME>
                </DFType>
              </DFProperties>
            </Node>
          </Node>
          <Node>
            <NodeName>BypassProxyForLocal</NodeName>
            <DFProperties>
              <AccessType>
                <Add />
                <Get />
                <Delete />
                <Replace />
              </AccessType>
              <DefaultValue>false</DefaultValue>
              <DFFormat>
                <bool />
              </DFFormat>
              <Occurrence>
                <ZeroOrOne />
              </Occurrence>
              <Scope>
                <Dynamic />
              </Scope>
              <CaseSense>
                <CIS />
              </CaseSense>
              <DFTitle>BypassProxyForLocal</DFTitle>
              <DFType>
                <MIME>text/plain</MIME>
              </DFType>
            </DFProperties>
          </Node>
        </Node>
        <Node>
          <NodeName>SecuredResources</NodeName>
          <DFProperties>
            <AccessType>
              <Add />
              <Get />
              <Delete />
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
            <CaseSense>
              <CIS />
            </CaseSense>
            <DFTitle>SecuredResources</DFTitle>
            <DFType>
              <DDFName></DDFName>
            </DFType>
          </DFProperties>
          <Node>
            <NodeName>AppPublisherNameList</NodeName>
            <DFProperties>
              <AccessType>
                <Add />
                <Get />
                <Delete />
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
              <CaseSense>
                <CIS />
              </CaseSense>
              <DFTitle>AppPublisherNameList</DFTitle>
              <DFType>
                <DDFName></DDFName>
              </DFType>
            </DFProperties>
            <Node>
              <NodeName></NodeName>
              <DFProperties>
                <AccessType>
                  <Add />
                  <Get />
                  <Delete />
                  <Replace />
                </AccessType>
                <DFFormat>
                  <chr />
                </DFFormat>
                <Occurrence>
                  <OneOrMore />
                </Occurrence>
                <Scope>
                  <Dynamic />
                </Scope>
                <CaseSense>
                  <CIS />
                </CaseSense>
                <DFTitle>AppPublisherName*</DFTitle>
                <DFType>
                  <MIME>text/plain</MIME>
                </DFType>
              </DFProperties>
            </Node>
          </Node>
          <Node>
            <NodeName>AppAllowedList</NodeName>
            <DFProperties>
              <AccessType>
                <Add />
                <Get />
                <Delete />
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
              <CaseSense>
                <CIS />
              </CaseSense>
              <DFTitle>AppAllowedList</DFTitle>
              <DFType>
                <DDFName></DDFName>
              </DFType>
            </DFProperties>
            <Node>
              <NodeName></NodeName>
              <DFProperties>
                <AccessType>
                  <Add />
                  <Get />
                  <Delete />
                </AccessType>
                <DFFormat>
                  <chr />
                </DFFormat>
                <Occurrence>
                  <OneOrMore />
                </Occurrence>
                <Scope>
                  <Dynamic />
                </Scope>
                <CaseSense>
                  <CIS />
                </CaseSense>
                <DFTitle>Apps*</DFTitle>
                <DFType>
                  <MIME>text/plain</MIME>
                </DFType>
              </DFProperties>
            </Node>
          </Node>
          <Node>
            <NodeName>NetworkAllowedList</NodeName>
            <DFProperties>
              <AccessType>
                <Add />
                <Get />
                <Delete />
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
              <CaseSense>
                <CIS />
              </CaseSense>
              <DFTitle>NetworkAllowedList</DFTitle>
              <DFType>
                <DDFName></DDFName>
              </DFType>
            </DFProperties>
            <Node>
              <NodeName></NodeName>
              <DFProperties>
                <AccessType>
                  <Add />
                  <Get />
                  <Delete />
                  <Replace />
                </AccessType>
                <DFFormat>
                  <chr />
                </DFFormat>
                <Occurrence>
                  <OneOrMore />
                </Occurrence>
                <Scope>
                  <Dynamic />
                </Scope>
                <CaseSense>
                  <CIS />
                </CaseSense>
                <DFTitle>Networks*</DFTitle>
                <DFType>
                  <MIME>text/plain</MIME>
                </DFType>
              </DFProperties>
            </Node>
          </Node>
          <Node>
            <NodeName>NameSpaceAllowedList</NodeName>
            <DFProperties>
              <AccessType>
                <Add />
                <Get />
                <Delete />
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
              <CaseSense>
                <CIS />
              </CaseSense>
              <DFTitle>NameSpaceAllowedList</DFTitle>
              <DFType>
                <DDFName></DDFName>
              </DFType>
            </DFProperties>
            <Node>
              <NodeName></NodeName>
              <DFProperties>
                <AccessType>
                  <Add />
                  <Get />
                  <Delete />
                  <Replace />
                </AccessType>
                <DFFormat>
                  <chr />
                </DFFormat>
                <Occurrence>
                  <OneOrMore />
                </Occurrence>
                <Scope>
                  <Dynamic />
                </Scope>
                <DFTitle>NameSpace*</DFTitle>
                <DFType>
                  <MIME>text/plain</MIME>
                </DFType>
              </DFProperties>
            </Node>
          </Node>
          <Node>
            <NodeName>ExcludedAppList</NodeName>
            <DFProperties>
              <AccessType>
                <Add />
                <Get />
                <Delete />
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
              <CaseSense>
                <CIS />
              </CaseSense>
              <DFTitle>ExcludedAppList</DFTitle>
              <DFType>
                <DDFName></DDFName>
              </DFType>
            </DFProperties>
            <Node>
              <NodeName></NodeName>
              <DFProperties>
                <AccessType>
                  <Add />
                  <Get />
                  <Delete />
                  <Replace />
                </AccessType>
                <DFFormat>
                  <chr />
                </DFFormat>
                <Occurrence>
                  <OneOrMore />
                </Occurrence>
                <Scope>
                  <Dynamic />
                </Scope>
                <CaseSense>
                  <CIS />
                </CaseSense>
                <DFTitle>ExcludedAppList*</DFTitle>
                <DFType>
                  <MIME>text/plain</MIME>
                </DFType>
              </DFProperties>
            </Node>
          </Node>
          <Node>
            <NodeName>ExcludedNetworkList</NodeName>
            <DFProperties>
              <AccessType>
                <Add />
                <Get />
                <Delete />
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
              <CaseSense>
                <CIS />
              </CaseSense>
              <DFTitle>ExcludedNetworkList</DFTitle>
              <DFType>
                <DDFName></DDFName>
              </DFType>
            </DFProperties>
            <Node>
              <NodeName></NodeName>
              <DFProperties>
                <AccessType>
                  <Add />
                  <Get />
                  <Delete />
                  <Replace />
                </AccessType>
                <DFFormat>
                  <chr />
                </DFFormat>
                <Occurrence>
                  <OneOrMore />
                </Occurrence>
                <Scope>
                  <Dynamic />
                </Scope>
                <CaseSense>
                  <CIS />
                </CaseSense>
                <DFTitle>ExcludedNetworkList*</DFTitle>
                <DFType>
                  <MIME>text/plain</MIME>
                </DFType>
              </DFProperties>
            </Node>
          </Node>
          <Node>
            <NodeName>ExcludedNameSpaceList</NodeName>
            <DFProperties>
              <AccessType>
                <Add />
                <Get />
                <Delete />
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
              <CaseSense>
                <CIS />
              </CaseSense>
              <DFTitle>ExcludedNameSpaceList</DFTitle>
              <DFType>
                <DDFName></DDFName>
              </DFType>
            </DFProperties>
            <Node>
              <NodeName></NodeName>
              <DFProperties>
                <AccessType>
                  <Add />
                  <Get />
                  <Delete />
                  <Replace />
                </AccessType>
                <DFFormat>
                  <chr />
                </DFFormat>
                <Occurrence>
                  <OneOrMore />
                </Occurrence>
                <Scope>
                  <Dynamic />
                </Scope>
                <CaseSense>
                  <CIS />
                </CaseSense>
                <DFTitle>ExcludedNamespaceList*</DFTitle>
                <DFType>
                  <MIME>text/plain</MIME>
                </DFType>
              </DFProperties>
            </Node>
          </Node>
          <Node>
            <NodeName>DNSSuffixSearchList</NodeName>
            <DFProperties>
              <AccessType>
                <Add />
                <Get />
                <Delete />
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
              <CaseSense>
                <CIS />
              </CaseSense>
              <DFTitle>DNSSuffixSearchList</DFTitle>
              <DFType>
                <DDFName></DDFName>
              </DFType>
            </DFProperties>
            <Node>
              <NodeName></NodeName>
              <DFProperties>
                <AccessType>
                  <Add />
                  <Get />
                  <Delete />
                  <Replace />
                </AccessType>
                <DFFormat>
                  <chr />
                </DFFormat>
                <Occurrence>
                  <OneOrMore />
                </Occurrence>
                <Scope>
                  <Dynamic />
                </Scope>
                <CaseSense>
                  <CIS />
                </CaseSense>
                <DFTitle>DNSSuffixSearchList*</DFTitle>
                <DFType>
                  <MIME>text/plain</MIME>
                </DFType>
              </DFProperties>
            </Node>
          </Node>
        </Node>
        <Node>
          <NodeName>Policies</NodeName>
          <DFProperties>
            <AccessType>
              <Add />
              <Get />
              <Delete />
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
            <CaseSense>
              <CIS />
            </CaseSense>
            <DFTitle>Policies</DFTitle>
            <DFType>
              <DDFName></DDFName>
            </DFType>
          </DFProperties>
          <Node>
            <NodeName>RememberCredentials</NodeName>
            <DFProperties>
              <AccessType>
                <Add />
                <Get />
                <Delete />
                <Replace />
              </AccessType>
              <DefaultValue>true</DefaultValue>
              <DFFormat>
                <bool />
              </DFFormat>
              <Occurrence>
                <ZeroOrOne />
              </Occurrence>
              <Scope>
                <Dynamic />
              </Scope>
              <CaseSense>
                <CIS />
              </CaseSense>
              <DFTitle>RememberCredentials</DFTitle>
              <DFType>
                <MIME>text/plain</MIME>
              </DFType>
            </DFProperties>
          </Node>
          <Node>
            <NodeName>SplitTunnel</NodeName>
            <DFProperties>
              <AccessType>
                <Add />
                <Get />
                <Delete />
                <Replace />
              </AccessType>
              <DefaultValue>true</DefaultValue>
              <DFFormat>
                <bool />
              </DFFormat>
              <Occurrence>
                <ZeroOrOne />
              </Occurrence>
              <Scope>
                <Dynamic />
              </Scope>
              <CaseSense>
                <CS />
              </CaseSense>
              <DFTitle>SplitTunnel</DFTitle>
              <DFType>
                <MIME>text/plain</MIME>
              </DFType>
            </DFProperties>
          </Node>
          <Node>
            <NodeName>BypassForLocal</NodeName>
            <DFProperties>
              <AccessType>
                <Add />
                <Get />
                <Delete />
                <Replace />
              </AccessType>
              <DefaultValue>true</DefaultValue>
              <DFFormat>
                <bool />
              </DFFormat>
              <Occurrence>
                <ZeroOrOne />
              </Occurrence>
              <Scope>
                <Dynamic />
              </Scope>
              <CaseSense>
                <CS />
              </CaseSense>
              <DFTitle>BypassForLocal</DFTitle>
              <DFType>
                <MIME>text/plain</MIME>
              </DFType>
            </DFProperties>
          </Node>
          <Node>
            <NodeName>TrustedNetworkDetection</NodeName>
            <DFProperties>
              <AccessType>
                <Add />
                <Get />
                <Delete />
                <Replace />
              </AccessType>
              <DefaultValue>true</DefaultValue>
              <DFFormat>
                <bool />
              </DFFormat>
              <Occurrence>
                <ZeroOrOne />
              </Occurrence>
              <Scope>
                <Dynamic />
              </Scope>
              <CaseSense>
                <CIS />
              </CaseSense>
              <DFTitle>TrustedNetworkDetection</DFTitle>
              <DFType>
                <MIME>text/plain</MIME>
              </DFType>
            </DFProperties>
          </Node>
          <Node>
            <NodeName>ConnectionType</NodeName>
            <DFProperties>
              <AccessType>
                <Add />
                <Get />
                <Delete />
                <Replace />
              </AccessType>
              <DefaultValue>Triggering</DefaultValue>
              <DFFormat>
                <chr />
              </DFFormat>
              <Occurrence>
                <ZeroOrOne />
              </Occurrence>
              <Scope>
                <Dynamic />
              </Scope>
              <CaseSense>
                <CIS />
              </CaseSense>
              <DFTitle>ConnectionType</DFTitle>
              <DFType>
                <MIME>text/plain</MIME>
              </DFType>
            </DFProperties>
          </Node>
        </Node>
        <Node>
          <NodeName>DNSSuffix</NodeName>
          <DFProperties>
            <AccessType>
              <Add />
              <Get />
              <Delete />
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
            <CaseSense>
              <CIS />
            </CaseSense>
            <DFTitle>DNSSuffix</DFTitle>
            <DFType>
              <DDFName></DDFName>
            </DFType>
          </DFProperties>
        </Node>
      </Node>
    </Node>
  </Node>
</MgmtTree>
```

## <a name="related-topics"></a>相关的主题


[VPN 的 configurtion 服务提供商](vpn-csp.md)

 

 






