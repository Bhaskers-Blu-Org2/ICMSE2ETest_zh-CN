---
title: "Win32AppInventory DDF 文件"
description: "Win32AppInventory DDF 文件"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: F6BCC10B-BFE4-40AB-AEEE-34679A4E15B0
ms.openlocfilehash: b5c4fa95f7c27daa5255dc238b704a767781e3e9
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="win32appinventory-ddf-file"></a>Win32AppInventory DDF 文件


本主题演示 OMA DM 设备描述框架 (DDF) **Win32AppInventory**配置服务提供程序。 DDF 文件只能用于提供 XML 的 OMA DM。

``` syntax
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE MgmtTree PUBLIC " -//OMA//DTD-DM-DDF 1.2//EN"
  "http://www.openmobilealliance.org/tech/DTD/DM_DDF-V1_2.dtd"
  [<?oma-dm-ddf-ver supported-versions="1.2"?>]>
<MgmtTree xmlns:MSFT="http://schemas.microsoft.com/MobileDevice/DM">
  <VerDTD>1.2</VerDTD>
      <Node>
        <NodeName>Win32AppInventory</NodeName>
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
          <NodeName>Win32InstalledProgram</NodeName>
          <DFProperties>
            <AccessType>
              <Get />
            </AccessType>
            <Description>The Win32InstalledProgram class represents installed applications.</Description>
            <DFFormat>
              <node />
            </DFFormat>
            <Occurrence>
              <One />
            </Occurrence>
            <Scope>
              <Permanent />
            </Scope>
            <DFTitle>Win32InstalledProgram</DFTitle>
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
              <Description>The InstalledProgram class represents an installed application.</Description>
              <DFFormat>
                <node />
              </DFFormat>
              <Occurrence>
                <ZeroOrMore />
              </Occurrence>
              <Scope>
                <Dynamic />
              </Scope>
              <DFTitle>InstalledProgram</DFTitle>
              <DFType>
                <DDFName></DDFName>
              </DFType>
            </DFProperties>
            <Node>
              <NodeName>Name</NodeName>
              <DFProperties>
                <AccessType>
                  <Get />
                </AccessType>
                <Description>Application name</Description>
                <DFFormat>
                  <chr />
                </DFFormat>
                <Occurrence>
                  <One />
                </Occurrence>
                <Scope>
                  <Dynamic />
                </Scope>
                <DFTitle>Name</DFTitle>
                <DFType>
                  <MIME>text/plain</MIME>
                </DFType>
              </DFProperties>
            </Node>
            <Node>
              <NodeName>Publisher</NodeName>
              <DFProperties>
                <AccessType>
                  <Get />
                </AccessType>
                <Description>Application publisher</Description>
                <DFFormat>
                  <chr />
                </DFFormat>
                <Occurrence>
                  <One />
                </Occurrence>
                <Scope>
                  <Dynamic />
                </Scope>
                <DFTitle>Publisher</DFTitle>
                <DFType>
                  <MIME>text/plain</MIME>
                </DFType>
              </DFProperties>
            </Node>
            <Node>
              <NodeName>Version</NodeName>
              <DFProperties>
                <AccessType>
                  <Get />
                </AccessType>
                <Description>Application version</Description>
                <DFFormat>
                  <chr />
                </DFFormat>
                <Occurrence>
                  <One />
                </Occurrence>
                <Scope>
                  <Dynamic />
                </Scope>
                <DFTitle>Version</DFTitle>
                <DFType>
                  <MIME>text/plain</MIME>
                </DFType>
              </DFProperties>
            </Node>
            <Node>
              <NodeName>Language</NodeName>
              <DFProperties>
                <AccessType>
                  <Get />
                </AccessType>
                <Description>Application language</Description>
                <DFFormat>
                  <chr />
                </DFFormat>
                <Occurrence>
                  <One />
                </Occurrence>
                <Scope>
                  <Dynamic />
                </Scope>
                <DFTitle>Language</DFTitle>
                <DFType>
                  <MIME>text/plain</MIME>
                </DFType>
              </DFProperties>
            </Node>
            <Node>
              <NodeName>RegKey</NodeName>
              <DFProperties>
                <AccessType>
                  <Get />
                </AccessType>
                <Description>For MSI this is the product code. For ARP this is the registry subkey.</Description>
                <DFFormat>
                  <chr />
                </DFFormat>
                <Occurrence>
                  <One />
                </Occurrence>
                <Scope>
                  <Dynamic />
                </Scope>
                <DFTitle>RegKey</DFTitle>
                <DFType>
                  <MIME>text/plain</MIME>
                </DFType>
              </DFProperties>
            </Node>
            <Node>
              <NodeName>Source</NodeName>
              <DFProperties>
                <AccessType>
                  <Get />
                </AccessType>
                <Description>The source of the installation info</Description>
                <DFFormat>
                  <chr />
                </DFFormat>
                <Occurrence>
                  <One />
                </Occurrence>
                <Scope>
                  <Dynamic />
                </Scope>
                <DFTitle>Source</DFTitle>
                <DFType>
                  <MIME>text/plain</MIME>
                </DFType>
              </DFProperties>
            </Node>
            <Node>
              <NodeName>MsiProductCode</NodeName>
              <DFProperties>
                <AccessType>
                  <Get />
                </AccessType>
                <Description>GUID that uniquely identifies a particular product.</Description>
                <DFFormat>
                  <chr />
                </DFFormat>
                <Occurrence>
                  <One />
                </Occurrence>
                <Scope>
                  <Dynamic />
                </Scope>
                <DFTitle>MsiProductCode</DFTitle>
                <DFType>
                  <MIME>text/plain</MIME>
                </DFType>
              </DFProperties>
            </Node>
            <Node>
              <NodeName>MsiPackageCode</NodeName>
              <DFProperties>
                <AccessType>
                  <Get />
                </AccessType>
                <Description>GUID that identifies a Windows Installer package.</Description>
                <DFFormat>
                  <chr />
                </DFFormat>
                <Occurrence>
                  <One />
                </Occurrence>
                <Scope>
                  <Dynamic />
                </Scope>
                <DFTitle>MsiPackageCode</DFTitle>
                <DFType>
                  <MIME>text/plain</MIME>
                </DFType>
              </DFProperties>
            </Node>
          </Node>
        </Node>
      </Node>
</MgmtTree>
```

## <a name="related-topics"></a>相关的主题


[Win32AppInventory 配置服务提供程序](win32appinventory-csp.md)

 

 






