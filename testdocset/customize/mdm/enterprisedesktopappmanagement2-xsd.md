---
title: EnterpriseDesktopAppManagement XSD
description: "本主题包含 EnterpriseDesktopAppManagement 配置服务提供程序的 DownloadInstall 参数的 XSD 架构文件。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 60980257-4F48-4A68-8E8E-1EF0A3F090E2
ms.openlocfilehash: 3a1dfad4437d61f3a73dfe0dcd3e272c6fefa822
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="enterprisedesktopappmanagement-xsd"></a>EnterpriseDesktopAppManagement XSD


本主题包含 EnterpriseDesktopAppManagement 配置服务提供程序的 DownloadInstall 参数的 XSD 架构文件。

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="Data">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="MsiInstallJob">
          <xs:complexType>
            <xs:sequence>
              <xs:element name="Product">
                <xs:complexType>
                  <xs:sequence>
                    <xs:element name="Download">
                      <xs:complexType>
                        <xs:sequence>
                          <xs:element name="ContentURLList">
                            <xs:complexType>
                              <xs:sequence>
                                <xs:element maxOccurs="unbounded" name="ContentURL" type="xs:string" />
                              </xs:sequence>
                            </xs:complexType>
                          </xs:element>
                        </xs:sequence>
                      </xs:complexType>
                    </xs:element>
                    <xs:element name="Validation">
                      <xs:complexType>
                        <xs:sequence>
                          <xs:element name="FileHash" type="xs:string" />
                        </xs:sequence>
                      </xs:complexType>
                    </xs:element>
                    <xs:element name="Enforcement">
                      <xs:complexType>
                        <xs:sequence>
                          <xs:element name="CommandLine" type="xs:string" />
                          <xs:element name="TimeOut" type="xs:unsignedByte" />
                          <xs:element name="RetryCount" type="xs:unsignedByte" />
                          <xs:element name="RetryInterval" type="xs:unsignedByte" />
                        </xs:sequence>
                      </xs:complexType>
                    </xs:element>
                  </xs:sequence>
                  <xs:attribute name="Version" type="xs:string" use="required" />
                </xs:complexType>
              </xs:element>
            </xs:sequence>
            <xs:attribute name="id" type="xs:string" use="required" />
          </xs:complexType>
        </xs:element>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```

下表描述了各种元素和属性的 XSD 文件︰

 

| 名称           | 说明                                                                                                                                                                        |
|----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| MsiInstallJob  | 根元素                                                                                                                                                                       |
| id             | 正在安装的应用程序的应用程序标识符。                                                                                                                    |
| Product        | MsiInstallJob 的子元素                                                                                                                                                     |
| 版本        | 应用程序的版本的字符串表示形式                                                                                                                                   |
| 下载       | 产品的子元素。 下载配置信息的容器。                                                                                                        |
| ContentURLList | 下载的子元素。 包含一个或多个内容下载 URL 定位器在窗体中的 ContentURL 元素的列表。                                                          |
| ContentURL     | 应从下载内容的位置。 必须是属性格式指向 MSI 文件的 URL。                                                                     |
| 验证     | 包含用于验证内容真实性的信息。                                                                                                                        |
| FileHash       | SHA256 散列值的文件内容。                                                                                                                                                 |
| 强制执行    | 用于安装此 MSI 的安装属性                                                                                                                        |
| 在命令行    | 在调用 MSIEXEC.exe 时要使用的命令行选项                                                                                                                           |
| Timeout        | 一段时间，以分钟为单位安装过程可以运行安装程序之前考虑安装可能会失败，并且不再监视安装操作。 |
| RetryCount     | 在安装之前将重试下载和安装操作次数将被标记为失败。                                                          |
| RetryInterval  | 在几分钟内重试操作之间的时间量。                                                                                                                                |

 

 

 






