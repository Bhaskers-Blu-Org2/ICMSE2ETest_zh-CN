---
title: "RootCATrustedCertificates 的 CSP"
description: "RootCATrustedCertificates 的 CSP"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: F2F25DEB-9DB3-40FB-BC3C-B816CE470D61
ms.openlocfilehash: 61d104d67a9fea301288edd20ab5154760c7aaeb
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="rootcatrustedcertificates-csp"></a>RootCATrustedCertificates 的 CSP


RootCATrustedCertificates 配置服务提供程序，使得企业能够设置根证书颁发机构 (CA) 证书。

> **请注意** **。 /User/**配置不受支持的**RootCATrustedCertificates/根/**。

 

下面的图像以树格式显示 RootCATrustedCertificates 配置服务提供程序。

![roocacertificate](images/provisioning-csp-rootcacertificate.png)

<a href="" id="device-or-user"></a>**设备或用户**  
对于设备的证书，使用**./Device/Vendor/MSFT**路径并为用户证书使用**./User/Vendor/MSFT**路径。

<a href="" id="rootcatrustedcertificates"></a>**RootCATrustedCertificates**  
RootCATrustedCertificates 配置服务提供程序的根节点。

<a href="" id="rootcatrustedcertificates-root-"></a>**RootCATrustedCertificates/根 /**  
定义的证书存储区包含根元素或自签名的证书，在此情况下，计算机存储区。

> **请注意** **。 /User/**配置不受支持的**RootCATrustedCertificates/根/**。

 

<a href="" id="rootcatrustedcertificates-ca"></a>**RootCATrustedCertificates/CA**  
CA 证书的节点。

<a href="" id="rootcatrustedcertificates-trustedpublisher"></a>**RootCATrustedCertificates/TrustedPublisher**  
受信任的发行者的证书的节点。

<a href="" id="rootcatrustedcertificates-trustedpeople"></a>**RootCATrustedCertificates/TrustedPeople**  
受信任的人员证书的节点。

<a href="" id="certhash"></a>**_CertHash_**  
定义证书的 SHA1 哈希。 20 个字节的值的 SHA1 证书哈希值被指定为一个十六进制的字符串值。

支持的操作是添加，删除，并替换。

<a href="" id="-encodedcertificate"></a>**/ EncodedCertificate**  
指定以 Base64 编码字符串形式的 X.509 证书。 Base 64 字符串值不能包括额外格式的字符，如嵌入式的换行符等。

支持的操作是添加 Get，删除和替换。

<a href="" id="-issuedby"></a>**/ IssuedBy**  
返回证书颁发者的名称。 这相当于在证书中的**颁发者**成员\_信息数据结构。

唯一受支持的操作是获得。

<a href="" id="-issuedto"></a>**/ IssuedTo**  
返回证书使用者的名称。 这相当于在证书中的**主题**成员\_信息数据结构。

唯一受支持的操作是获得。

<a href="" id="-validfrom"></a>**/ ValidFrom**  
返回该证书的有效期的起始日期。 这相当于在证书中的**NotBefore**成员\_信息数据结构。

唯一受支持的操作是获得。

<a href="" id="-validto"></a>**/ ValidTo**  
返回证书的到期日期。 这相当于在证书中的**NotAfter**成员\_信息数据结构。

唯一受支持的操作是获得。

<a href="" id="-templatename"></a>**/ 模板名称**  
返回的证书模板名称。

唯一受支持的操作是获得。

## <a name="related-topics"></a>相关的主题


[配置服务提供程序的引用](configuration-service-provider-reference.md)

 

 






