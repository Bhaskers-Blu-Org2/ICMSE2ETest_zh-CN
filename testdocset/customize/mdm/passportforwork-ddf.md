---
title: PassportForWork DDF
description: "本主题演示 OMA DM 设备描述框架 (DDF) PassportForWork 配置服务提供程序。 DDF 文件只能用于提供 XML 的 OMA DM。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: A2182898-1577-4675-BAE5-2A3A9C2AAC9B
ms.openlocfilehash: 2407924dec4acb1c766fa3eca7cb49d86eb63626
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="passportforwork-ddf"></a>PassportForWork DDF


本主题演示 OMA DM 设备描述框架 (DDF) **PassportForWork**配置服务提供程序。 DDF 文件只能用于提供 XML 的 OMA DM。

``` syntax
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE MgmtTree PUBLIC " -//OMA//DTD-DM-DDF 1.2//EN"
  "http://www.openmobilealliance.org/tech/DTD/DM_DDF-V1_2.dtd"
  [<?oma-dm-ddf-ver supported-versions="1.2"?>]>
<MgmtTree xmlns:MSFT="http://schemas.microsoft.com/MobileDevice/DM">
  <VerDTD>1.2</VerDTD>
      <Node>
        <NodeName>PassportForWork</NodeName>
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
            <MIME>com.microsoft/1.2/MDM/PassportForWork</MIME>
          </DFType>
        </DFProperties>
        <Node>
          <NodeName></NodeName>
          <DFProperties>
            <AccessType>
              <Add />
              <Delete />
              <Get />
            </AccessType>
            <Description>This policy specifies the Tenant ID in the format of a Globally Unique Identifier (GUID) without curly braces ( { , } ), which will be used as part of Microsoft Passport for work provisioning and management.</Description>
            <DFFormat>
              <node />
            </DFFormat>
            <Occurrence>
              <ZeroOrMore />
            </Occurrence>
            <Scope>
              <Dynamic />
            </Scope>
            <DFTitle>TenantId</DFTitle>
            <DFType>
              <DDFName></DDFName>
            </DFType>
          </DFProperties>
          <Node>
            <NodeName>Policies</NodeName>
            <DFProperties>
              <AccessType>
                <Get />
              </AccessType>
              <Description>Root node for policies.</Description>
              <DFFormat>
                <node />
              </DFFormat>
              <Occurrence>
                <One />
              </Occurrence>
              <Scope>
                <Permanent />
              </Scope>
              <DFTitle>Policies</DFTitle>
              <DFType>
                <DDFName></DDFName>
              </DFType>
            </DFProperties>
            <Node>
              <NodeName>UsePassportForWork</NodeName>
              <DFProperties>
                <AccessType>
                  <Add />
                  <Delete />
                  <Get />
                  <Replace />
                </AccessType>
                <DefaultValue>True</DefaultValue>
                <Description>Microsoft Passport for Work is an alternative method for signing into Windows using your Active Directory or Azure Active Directory account that can replace passwords, Smart Cards, and Virtual Smart Cards.

If you enable or do not configure this policy setting, the device provisions Microsoft Passport for Work for all users.

If you disable this policy setting, the device does not provision Microsoft Passport for Work for any user.</Description>
                <DFFormat>
                  <bool />
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
              <NodeName>RequireSecurityDevice</NodeName>
              <DFProperties>
                <AccessType>
                  <Add />
                  <Delete />
                  <Get />
                  <Replace />
                </AccessType>
                <DefaultValue>False</DefaultValue>
                <Description>A Trusted Platform Module (TPM) provides additional security benefits over software because data stored within it cannot be used on other devices.

If you enable this policy setting, only devices with a usable TPM provision Microsoft Passport for Work.

If you disable or do not configure this policy setting, the TPM is still preferred, but all devices provision Microsoft Passport for Work using software if the TPM is non-functional or unavailable.</Description>
                <DFFormat>
                  <bool />
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
              <NodeName>PINComplexity</NodeName>
              <DFProperties>
                <AccessType>
                  <Get />
                </AccessType>
                <Description>Root node for PIN policies</Description>
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
                <NodeName>MinimumPINLength</NodeName>
                <DFProperties>
                  <AccessType>
                    <Add />
                    <Delete />
                    <Get />
                    <Replace />
                  </AccessType>
                  <DefaultValue>4</DefaultValue>
                  <Description>Minimum PIN length configures the minimum number of characters required for the work PIN.  The lowest number you can configure for this policy setting is 4.  The largest number you can configure must be less than the number configured in the Maximum PIN length policy setting or the number 127, whichever is the lowest.

If you configure this policy setting, the work PIN length must be greater than or equal to this number.

If you do not configure this policy setting, the work PIN length must be greater than or equal to 4.

NOTE: If the above specified conditions for the minimum PIN length are not met, default values will be used for both the maximum and minimum PIN lengths.</Description>
                  <DFFormat>
                    <int />
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
                <NodeName>MaximumPINLength</NodeName>
                <DFProperties>
                  <AccessType>
                    <Add />
                    <Delete />
                    <Get />
                    <Replace />
                  </AccessType>
                  <DefaultValue>127</DefaultValue>
                  <Description>Maximum PIN length configures the maximum number of characters allowed for the work PIN.  The largest number you can configure for this policy setting is 127. The lowest number you can configure must be larger than the number configured in the Minimum PIN length policy setting or the number 4, whichever is greater.

If you configure this policy setting, the work PIN length must be less than or equal to this number.

If you do not configure this policy setting, the work PIN length must be less than or equal to 127.

NOTE: If the above specified conditions for the maximum PIN length are not met, default values will be used for both the maximum and minimum PIN lengths.</Description>
                  <DFFormat>
                    <int />
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
                <NodeName>UppercaseLetters</NodeName>
                <DFProperties>
                  <AccessType>
                    <Add />
                    <Delete />
                    <Get />
                    <Replace />
                  </AccessType>
                  <DefaultValue>0</DefaultValue>
                  <Description>Use this policy setting to configure the use of uppercase letters in the Microsoft Passport for work PIN.

A value of 1 corresponds to “Required.” If you configure this policy setting to 1, Microsoft Passport for Work requires users to include at least one uppercase letter in their work PIN.

A value of 2 corresponds to “Disallow.” If you configure this policy setting to 2, Microsoft Passport for Work prevents users from using uppercase letters in their work PIN.

If you do not configure this policy setting, Microsoft Passport for Work does not allow users to use uppercase letters in their work PIN.</Description>
                  <DFFormat>
                    <int />
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
                <NodeName>LowercaseLetters</NodeName>
                <DFProperties>
                  <AccessType>
                    <Add />
                    <Delete />
                    <Get />
                    <Replace />
                  </AccessType>
                  <DefaultValue>0</DefaultValue>
                  <Description>Use this policy setting to configure the use of lowercase letters in the Microsoft Passport for work PIN.

A value of 1 corresponds to “Required.” If you configure this policy setting to 1, Microsoft Passport for Work requires users to include at least one lowercase letter in their work PIN.

A value of 2 corresponds to “Disallow.” If you configure this policy setting to 2, Microsoft Passport for Work prevents users from using lowercase letters in their work PIN.

If you do not configure this policy setting, Microsoft Passport for Work does not allow users to use lowercase letters in their work PIN.</Description>
                  <DFFormat>
                    <int />
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
                <NodeName>SpecialCharacters</NodeName>
                <DFProperties>
                  <AccessType>
                    <Add />
                    <Delete />
                    <Get />
                    <Replace />
                  </AccessType>
                  <DefaultValue>0</DefaultValue>
                  <Description><![CDATA[Use this policy setting to configure the use of special characters in the Microsoft Passport for work PIN gesture.  Valid special characters for Microsoft Passport for work PIN gestures include: ! " # $ % & ' ( ) * + , - . / : ; < = > ? @ [ \ ] ^ _ ` { | } ~ .

A value of 1 corresponds to “Required.” If you configure this policy setting to 1, Microsoft Passport for Work requires users to include at least one special character in their work PIN.

A value of 2 corresponds to “Disallow.” If you configure this policy setting to 2, Microsoft Passport for Work prevents users from using special characters in their work PIN.

If you do not configure this policy setting, Microsoft Passport for Work does not allow users to use special characters in their work PIN.]]></Description>
                  <DFFormat>
                    <int />
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
                <NodeName>Digits</NodeName>
                <DFProperties>
                  <AccessType>
                    <Add />
                    <Delete />
                    <Get />
                    <Replace />
                  </AccessType>
                  <DefaultValue>0</DefaultValue>
                  <Description>Use this policy setting to configure the use of digits in the Microsoft Passport for work PIN.

A value of 1 corresponds to “Required.” If you configure this policy setting to 1, Microsoft Passport for Work requires users to include at least one digit in their work PIN.

A value of 2 corresponds to “Disallow.” If you configure this policy setting to 2, Microsoft Passport for Work prevents users from using digits in their work PIN.

If you do not configure this policy setting, Microsoft Passport for Work requires users to use digits in their work PIN.</Description>
                  <DFFormat>
                    <int />
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
                <NodeName>History</NodeName>
                <DFProperties>
                  <AccessType>
                    <Add />
                    <Delete />
                    <Get />
                    <Replace />
                  </AccessType>
                  <DefaultValue>0</DefaultValue>
                  <Description>This policy specifies the number of past PINs that can be stored in the history that can’t be used. Valid values are 0 to 50 inclusive. If this policy is set to 0, then storage of previous PINs is not required. PIN history is not preserved through PIN reset.</Description>
                  <DFFormat>
                    <int />
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
                <NodeName>Expiration</NodeName>
                <DFProperties>
                  <AccessType>
                    <Add />
                    <Delete />
                    <Get />
                    <Replace />
                  </AccessType>
                  <DefaultValue>0</DefaultValue>
                  <Description>This policy specifies when the PIN expires (in days). Valid values are 0 to 730 inclusive. If this policy is set to 0, then PINs do not expire.</Description>
                  <DFFormat>
                    <int />
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
      <Node>
        <NodeName>PassportForWork</NodeName>
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
            </AccessType>
            <Description>This policy specifies the Tenant ID in the format of a Globally Unique Identifier (GUID) without curly braces ( { , } ), which will be used as part of Microsoft Passport for work provisioning and management.</Description>
            <DFFormat>
              <node />
            </DFFormat>
            <Occurrence>
              <ZeroOrMore />
            </Occurrence>
            <Scope>
              <Dynamic />
            </Scope>
            <DFTitle>TenantId</DFTitle>
            <DFType>
              <DDFName></DDFName>
            </DFType>
          </DFProperties>
          <Node>
            <NodeName>Policies</NodeName>
            <DFProperties>
              <AccessType>
                <Get />
              </AccessType>
              <Description>Root node for policies.</Description>
              <DFFormat>
                <node />
              </DFFormat>
              <Occurrence>
                <One />
              </Occurrence>
              <Scope>
                <Permanent />
              </Scope>
              <DFTitle>Policies</DFTitle>
              <DFType>
                <DDFName></DDFName>
              </DFType>
            </DFProperties>
            <Node>
              <NodeName>UsePassportForWork</NodeName>
              <DFProperties>
                <AccessType>
                  <Add />
                  <Delete />
                  <Get />
                  <Replace />
                </AccessType>
                <DefaultValue>True</DefaultValue>
                <Description>Microsoft Passport for Work is an alternative method for signing into Windows using your Active Directory or Azure Active Directory account that can replace passwords, Smart Cards, and Virtual Smart Cards.

If you enable or do not configure this policy setting, the device provisions Microsoft Passport for Work for all users.

If you disable this policy setting, the device does not provision Microsoft Passport for Work for any user.</Description>
                <DFFormat>
                  <bool />
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
              <NodeName>RequireSecurityDevice</NodeName>
              <DFProperties>
                <AccessType>
                  <Add />
                  <Delete />
                  <Get />
                  <Replace />
                </AccessType>
                <DefaultValue>False</DefaultValue>
                <Description>A Trusted Platform Module (TPM) provides additional security benefits over software because data stored within it cannot be used on other devices.

If you enable this policy setting, only devices with a usable TPM provision Microsoft Passport for Work.

If you disable or do not configure this policy setting, the TPM is still preferred, but all devices provision Microsoft Passport for Work using software if the TPM is non-functional or unavailable.</Description>
                <DFFormat>
                  <bool />
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
              <NodeName>UseCertificateForOnPremAuth</NodeName>
              <DFProperties>
                <AccessType>
                  <Add />
                  <Delete />
                  <Get />
                  <Replace />
                </AccessType>
                <DefaultValue>False</DefaultValue>
                <Description>Microsoft Passport for Work can use certificates to authenticate to on-premise resources. 

If you enable this policy setting, Microsoft Passport for Work will wait until the device has received a certificate payload from the enterprise Certificate Authority before provisioning a PIN.

If you disable or do not configure this policy setting, the PIN will be provisioned when the user logs in, without waiting for a certificate payload.</Description>
                <DFFormat>
                  <bool />
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
              <NodeName>PINComplexity</NodeName>
              <DFProperties>
                <AccessType>
                  <Get />
                </AccessType>
                <Description>Root node for PIN policies</Description>
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
                <NodeName>MinimumPINLength</NodeName>
                <DFProperties>
                  <AccessType>
                    <Add />
                    <Delete />
                    <Get />
                    <Replace />
                  </AccessType>
                  <DefaultValue>4</DefaultValue>
                  <Description>Minimum PIN length configures the minimum number of characters required for the work PIN.  The lowest number you can configure for this policy setting is 4.  The largest number you can configure must be less than the number configured in the Maximum PIN length policy setting or the number 127, whichever is the lowest.

If you configure this policy setting, the work PIN length must be greater than or equal to this number.

If you do not configure this policy setting, the work PIN length must be greater than or equal to 4.

NOTE: If the above specified conditions for the minimum PIN length are not met, default values will be used for both the maximum and minimum PIN lengths.</Description>
                  <DFFormat>
                    <int />
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
                <NodeName>MaximumPINLength</NodeName>
                <DFProperties>
                  <AccessType>
                    <Add />
                    <Delete />
                    <Get />
                    <Replace />
                  </AccessType>
                  <DefaultValue>127</DefaultValue>
                  <Description>Maximum PIN length configures the maximum number of characters allowed for the work PIN.  The largest number you can configure for this policy setting is 127. The lowest number you can configure must be larger than the number configured in the Minimum PIN length policy setting or the number 4, whichever is greater.

If you configure this policy setting, the work PIN length must be less than or equal to this number.

If you do not configure this policy setting, the work PIN length must be less than or equal to 127.

NOTE: If the above specified conditions for the maximum PIN length are not met, default values will be used for both the maximum and minimum PIN lengths.</Description>
                  <DFFormat>
                    <int />
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
                <NodeName>UppercaseLetters</NodeName>
                <DFProperties>
                  <AccessType>
                    <Add />
                    <Delete />
                    <Get />
                    <Replace />
                  </AccessType>
                  <DefaultValue>0</DefaultValue>
                  <Description>Use this policy setting to configure the use of uppercase letters in the Microsoft Passport for work PIN.

A value of 1 corresponds to “Required.” If you configure this policy setting to 1, Microsoft Passport for Work requires users to include at least one uppercase letter in their work PIN.

A value of 2 corresponds to “Disallow.” If you configure this policy setting to 2, Microsoft Passport for Work prevents users from using uppercase letters in their work PIN.

If you do not configure this policy setting, Microsoft Passport for Work does not allow users to use uppercase letters in their work PIN.</Description>
                  <DFFormat>
                    <int />
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
                <NodeName>LowercaseLetters</NodeName>
                <DFProperties>
                  <AccessType>
                    <Add />
                    <Delete />
                    <Get />
                    <Replace />
                  </AccessType>
                  <DefaultValue>0</DefaultValue>
                  <Description>Use this policy setting to configure the use of lowercase letters in the Microsoft Passport for work PIN.

A value of 1 corresponds to “Required.” If you configure this policy setting to 1, Microsoft Passport for Work requires users to include at least one lowercase letter in their work PIN.

A value of 2 corresponds to “Disallow.” If you configure this policy setting to 2, Microsoft Passport for Work prevents users from using lowercase letters in their work PIN.

If you do not configure this policy setting, Microsoft Passport for Work does not allow users to use lowercase letters in their work PIN.</Description>
                  <DFFormat>
                    <int />
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
                <NodeName>SpecialCharacters</NodeName>
                <DFProperties>
                  <AccessType>
                    <Add />
                    <Delete />
                    <Get />
                    <Replace />
                  </AccessType>
                  <DefaultValue>0</DefaultValue>
                  <Description><![CDATA[Use this policy setting to configure the use of special characters in the Microsoft Passport for work PIN gesture.  Valid special characters for Microsoft Passport for work PIN gestures include: ! " # $ % & ' ( ) * + , - . / : ; < = > ? @ [ \ ] ^ _ ` { | } ~ .

A value of 1 corresponds to “Required.” If you configure this policy setting to 1, Microsoft Passport for Work requires users to include at least one special character in their work PIN.

A value of 2 corresponds to “Disallow.” If you configure this policy setting to 2, Microsoft Passport for Work prevents users from using special characters in their work PIN.

If you do not configure this policy setting, Microsoft Passport for Work does not allow users to use special characters in their work PIN.]]></Description>
                  <DFFormat>
                    <int />
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
                <NodeName>Digits</NodeName>
                <DFProperties>
                  <AccessType>
                    <Add />
                    <Delete />
                    <Get />
                    <Replace />
                  </AccessType>
                  <DefaultValue>0</DefaultValue>
                  <Description>Use this policy setting to configure the use of digits in the Microsoft Passport for work PIN.

A value of 1 corresponds to “Required.” If you configure this policy setting to 1, Microsoft Passport for Work requires users to include at least one digit in their work PIN.

A value of 2 corresponds to “Disallow.” If you configure this policy setting to 2, Microsoft Passport for Work prevents users from using digits in their work PIN.

If you do not configure this policy setting, Microsoft Passport for Work requires users to use digits in their work PIN.</Description>
                  <DFFormat>
                    <int />
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
                <NodeName>History</NodeName>
                <DFProperties>
                  <AccessType>
                    <Add />
                    <Delete />
                    <Get />
                    <Replace />
                  </AccessType>
                  <DefaultValue>0</DefaultValue>
                  <Description>This policy specifies the number of past PINs that can be stored in the history that can’t be used. Valid values are 0 to 50 inclusive. If this policy is set to 0, then storage of previous PINs is not required. PIN history is not preserved through PIN reset.</Description>
                  <DFFormat>
                    <int />
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
                <NodeName>Expiration</NodeName>
                <DFProperties>
                  <AccessType>
                    <Add />
                    <Delete />
                    <Get />
                    <Replace />
                  </AccessType>
                  <DefaultValue>0</DefaultValue>
                  <Description>This policy specifies when the PIN expires (in days). Valid values are 0 to 730 inclusive. If this policy is set to 0, then PINs do not expire.</Description>
                  <DFFormat>
                    <int />
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
              <NodeName>Remote</NodeName>
              <DFProperties>
                <AccessType>
                  <Get />
                </AccessType>
                <Description>Root node for Remote Passport policies</Description>
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
                <NodeName>UseRemotePassport</NodeName>
                <DFProperties>
                  <AccessType>
                    <Add />
                    <Delete />
                    <Get />
                    <Replace />
                  </AccessType>
                  <DefaultValue>False</DefaultValue>
                  <Description>Boolean that specifies if Remote Passport can be used with a device. Remote Passport provides the ability for a portable, registered device to be usable as a companion device for desktop authentication.

Default value is false. If you enable this setting, a desktop device will allow a registered, companion device to be used as an authentication factor. If you disable this setting, a companion device cannot be used in desktop authentication scenarios.</Description>
                  <DFFormat>
                    <bool />
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
          <NodeName>UseBiometrics</NodeName>
          <DFProperties>
            <AccessType>
              <Add />
              <Delete />
              <Get />
              <Replace />
            </AccessType>
            <DefaultValue>False</DefaultValue>
            <Description>THIS NODE IS DEPRECATED AND WILL BE REMOVED IN A FUTURE VERSION. PLEASE USE Biometrics/UseBiometrics NODE INSTEAD.

Microsoft Passport for Work enables users to use biometric gestures, such as face and fingerprints, as an alternative to the PIN gesture. However users must still configure a work PIN to use in case of failures.

If you enable this policy setting, Microsoft Passport for Work allows the use biometric gestures on.

If you disable this policy setting, Microsoft Passport for Work prevents the use of biometric gestures.

If you do not configure this policy setting, Microsoft Passport for Work allows the use of biometric gestures.

NOTE: Disabling this policy prevents the user of biometric gestures on the device for all account types.</Description>
            <DFFormat>
              <bool />
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
          <NodeName>Biometrics</NodeName>
          <DFProperties>
            <AccessType>
              <Get />
            </AccessType>
            <Description>Root node for biometrics policies</Description>
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
            <NodeName>UseBiometrics</NodeName>
            <DFProperties>
              <AccessType>
                <Add />
                <Delete />
                <Get />
                <Replace />
              </AccessType>
              <DefaultValue>False</DefaultValue>
              <Description>Microsoft Passport for Work enables users to use biometric gestures, such as face and fingerprints, as an alternative to the PIN gesture. However users must still configure a work PIN to use in case of failures.

If you enable this policy setting, Microsoft Passport for Work allows the use biometric gestures on.

If you disable this policy setting, Microsoft Passport for Work prevents the use of biometric gestures.

If you do not configure this policy setting, Microsoft Passport for Work allows the use of biometric gestures.

NOTE: Disabling this policy prevents the user of biometric gestures on the device for all account types.</Description>
              <DFFormat>
                <bool />
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
            <NodeName>FacialFeaturesUseEnhancedAntiSpoofing</NodeName>
            <DFProperties>
              <AccessType>
                <Add />
                <Delete />
                <Get />
                <Replace />
              </AccessType>
              <DefaultValue>False</DefaultValue>
              <Description>This policy setting determines whether enhanced anti-spoofing is configured for facial features, on devices which support it.

If you do not configure this policy setting, users will be able to choose whether or not to use enhanced anti-spoofing for facial features.

If you enable this policy setting, Windows will require all users on the device to use enhanced anti-spoofing for facial features, on devices which support it.

If you disable this policy setting, enhanced anti-spoofing for facial features is turned off for all users on the device and they will be unable to turn it on.
              </Description>
              <DFFormat>
                <bool />
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
</MgmtTree>
```

 

 






