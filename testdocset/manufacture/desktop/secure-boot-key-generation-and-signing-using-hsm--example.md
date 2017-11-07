---
author: Justinha
Description: "安全启动密钥生成和签名使用 HSM （示例）"
ms.assetid: b776b30c-28b5-4300-932a-a35a2e489074
MSHAttr: PreferredLib:/library/windows/hardware
title: "安全启动密钥生成和签名使用 HSM （示例）"
ms.openlocfilehash: 7fd83bfa955a5f4f8cb135a6c4b0fcf84cba2156
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="secure-boot-key-generation-and-signing-using-hsm-example"></a>安全启动密钥生成和签名使用 HSM （示例）


1.3 版

通过使用硬件安全模块 (HSM)，下面是举例说明如何生成安全启动密钥 （PK 和其他人）。

您将需要知道安全引导公钥基础结构 (PKI)。 有关更多信息，请参阅[Windows 8.1 安全启动密钥创建和管理指导](windows-secure-boot-key-creation-and-management-guidance.md)。

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>要求


### <a name="span-idtoolsneededspanspan-idtoolsneededspanspan-idtoolsneededspantools-needed"></a><span id="Tools_Needed"></span><span id="tools_needed"></span><span id="TOOLS_NEEDED"></span>所需工具

-   certreq.exe — 可收件箱

-   certutil.exe – 可用的收件箱

-   Signtool.exe – 最新 Windows SDK 中的可用

### <a name="span-idhardwaresecuritymodulehsmspanspan-idhardwaresecuritymodulehsmspanspan-idhardwaresecuritymodulehsmspanhardware-security-module-hsm"></a><span id="Hardware_Security_Module__HSM_"></span><span id="hardware_security_module__hsm_"></span><span id="HARDWARE_SECURITY_MODULE__HSM_"></span>硬件安全模块 (HSM)

白皮书演示如何使用从 nCipher (现在 Thales) PCI HSM 模型 nC1003P/nC3023P/nC3033P 和 SafeNet Luna Hsm 示例生成密钥。 大多数概念应用到其他 HSM 供应商。

对于其他 Hsm，联系其他有关如何定制您的方法使用 HSM 加密服务提供程序 (CSP) 制造商。

## <a name="span-idapproachspanspan-idapproachspanspan-idapproachspanapproach"></a><span id="Approach"></span><span id="approach"></span><span id="APPROACH"></span>方法


我们使用 Microsoft 证书创建工具︰ **certreq.exe**生成安全引导的平台键 (PK) 和其它所需的安全启动键。

Certreq 中的工具可以调整以使用 HSM 提供加密服务提供程序 (CSP) 为 HSM。

### <a name="span-idfindthecryptographicserviceprovidercspspanspan-idfindthecryptographicserviceprovidercspspanspan-idfindthecryptographicserviceprovidercspspanfind-the-cryptographic-service-provider-csp"></a><span id="Find_the_Cryptographic_Service_Provider__CSP_"></span><span id="find_the_cryptographic_service_provider__csp_"></span><span id="FIND_THE_CRYPTOGRAPHIC_SERVICE_PROVIDER__CSP_"></span>查找加密服务提供程序 (CSP)

您可以使用 certutil.exe 工具或 HSM 用于列出 Csp 的工具。

-   **此示例使用 certutil 工具显示 Csp Thales/nCipher HSM 上︰**

    ``` syntax
    C:\secureboot_training\certreq> certutil -csplist
    Provider Name: Microsoft Base Cryptographic Provider v1.0
    Provider Type: 1 - PROV_RSA_FULL

    Provider Name: Microsoft Base DSS and Diffie-Hellman Cryptographic Provider
    Provider Type: 13 - PROV_DSS_DH

    Provider Name: Microsoft Base DSS Cryptographic Provider
    Provider Type: 3 - PROV_DSS

    Provider Name: Microsoft Base Smart Card Crypto Provider
    Provider Type: 1 - PROV_RSA_FULL

    Provider Name: Microsoft DH SChannel Cryptographic Provider
    Provider Type: 18 - PROV_DH_SCHANNEL

    Provider Name: Microsoft Enhanced Cryptographic Provider v1.0
    Provider Type: 1 - PROV_RSA_FULL

    Provider Name: Microsoft Enhanced DSS and Diffie-Hellman Cryptographic Provider
    Provider Type: 13 - PROV_DSS_DH

    Provider Name: Microsoft Enhanced RSA and AES Cryptographic Provider
    Provider Type: 24 - PROV_RSA_AES

    Provider Name: Microsoft RSA SChannel Cryptographic Provider
    Provider Type: 12 - PROV_RSA_SCHANNEL

    Provider Name: Microsoft Strong Cryptographic Provider
    Provider Type: 1 - PROV_RSA_FULL

    Provider Name: Microsoft Software Key Storage Provider

    Provider Name: nCipher Security World Key Storage Provider

    Provider Name: Microsoft Smart Card Key Storage Provider
    CertUtil: -csplist command completed successfully.
    ```

    对于 sha-256 算法，digesting 使用的**CNG**提供︰ `"nCipher Security World Key Storage Provider"`。 旧式的提供程序不支持 sha-256 并不适用于安全启动。

-   **此示例使用内置的 Thales/nCipher 工具 CSP 列表︰**

    ``` syntax
    C:\Program Files\nCipher\nfast\bin> cnglist --list-providers
    Microsoft Primitive Provider
    Microsoft Smart Card Key Storage Provider
    Microsoft Software Key Storage Provider
    Microsoft SSL Protocol Provider
    nCipher Primitive Provider
    nCipher Security World Key Storage Provider
    ```

    对于 sha-256 算法，digesting 使用的**CNG**提供︰ `"nCipher Security World Key Storage Provider"`。 旧式的提供程序不支持 sha-256 并不适用于安全启动。

-   **此示例使用 SafeNet Luna Hsm 工具 CSP 列表︰**

    ``` syntax
    C:\>certutil -csplist
    ------------------------------------------------------------------------------------------
    Provider Name: Luna Cryptographic Services for Microsoft Windows
    Provider Type: 1 - PROV_RSA_FULL

    Provider Name: Luna enhanced RSA and AES provider for Microsoft Windows
    Provider Type: 24 - PROV_RSA_AES

    Provider Name: Luna SChannel Cryptographic Services for Microsoft Windows
    Provider Type: 12 - PROV_RSA_SCHANNEL

    Provider Name: Microsoft Base Cryptographic Provider v1.0
    Provider Type: 1 - PROV_RSA_FULL

    Provider Name: Microsoft Base DSS and Diffie-Hellman Cryptographic Provider
    Provider Type: 13 - PROV_DSS_DH

    Provider Name: Microsoft Base DSS Cryptographic Provider
    Provider Type: 3 - PROV_DSS

    Provider Name: Microsoft Base Smart Card Crypto Provider
    Provider Type: 1 - PROV_RSA_FULL

    Provider Name: Microsoft DH SChannel Cryptographic Provider
    Provider Type: 18 - PROV_DH_SCHANNEL

    Provider Name: Microsoft Enhanced Cryptographic Provider v1.0
    Provider Type: 1 - PROV_RSA_FULL

    Provider Name: Microsoft Enhanced DSS and Diffie-Hellman Cryptographic Provider
    Provider Type: 13 - PROV_DSS_DH

    Provider Name: Microsoft Enhanced RSA and AES Cryptographic Provider
    Provider Type: 24 - PROV_RSA_AES

    Provider Name: Microsoft RSA SChannel Cryptographic Provider
    Provider Type: 12 - PROV_RSA_SCHANNEL

    Provider Name: Microsoft Strong Cryptographic Provider
    Provider Type: 1 - PROV_RSA_FULL

    Provider Name: Microsoft Software Key Storage Provider

    Provider Name: Microsoft Smart Card Key Storage Provider

    Provider Name: SafeNet Key Storage Provider
    CertUtil: -csplist command completed successfully.
    ------------------------------------------------------------------------------------------
    ```

    对于 sha-256 摘要算法需要使用 CNG 提供程序 –"SafeNet 密钥存储提供程序"。 旧式的提供程序不支持 sha-256 并不适用于安全启动。

生成密钥︰

``` syntax
certreq.exe -new request.inf PK.cer
```

Request.inf 文件的示例︰

``` syntax
[Version]
Signature= "$Windows NT$"
[NewRequest]
ValidityPeriod = Years
ValidityPeriodUnits = 6
Subject = "CN=Corporation TODO Platform Key,O=TODO Corporation,L=TODO_City,S=TODO_State,C=TODO_Country"
MachineKeySet = true
RequestType=Cert
Exportable =  FALSE 
HashAlgorithm = SHA256
KeyAlgorithm = RSA
KeyLength = 2048
KeyContainer = "PKContainer"
ProviderName = "nCipher Security World Key Storage Provider"
KeyUsage = 0xf0
```

更新以下值︰

-   **主题︰**使用真实数据替换 TODO 的`"CN=Corporation TODO Platform Key,O=TODO Corporation,L=TODO_City,S=TODO_State,C=TODO_Country"`。

-   **ValidityPeriod，ValidityPeriodUnits:**使用有效期为 6 年。 而仅 2 年的时间里都是有效的 PK，6 年的时间内允许潜在的未来服务。

-   **KeyContainer:**输入用来使用 HSM 创建密钥容器 id。 您可能需要提供有用于创建安全领域 Thales HSM 的标记。

### <a name="span-idvalidatingcertificateself-signedspanspan-idvalidatingcertificateself-signedspanspan-idvalidatingcertificateself-signedspanvalidating-certificate-self-signed"></a><span id="Validating_certificate__self-signed_"></span><span id="validating_certificate__self-signed_"></span><span id="VALIDATING_CERTIFICATE__SELF-SIGNED_"></span>验证证书 （自签名）

验证证书已正确生成︰

``` syntax
certutil -store -v my  "<Certificate_serial_number_or_thumbprint>"
```

例如︰`certutil -store -v my  "7569d364a2e77b814274c81ae6360ffe"`

输出示例︰

``` syntax
my
================ Certificate 16 ================
X509 Certificate:
Version: 3
Serial Number: 7569d364a2e77b814274c81ae6360ffe
Signature Algorithm:
    Algorithm ObjectId: 1.2.840.113549.1.1.11 sha256RSA
    Algorithm Parameters:
    05 00
Issuer:
    CN=test self-signed

 NotBefore: 1/21/2013 7:25 PM
 NotAfter: 1/21/2015 7:35 PM

Subject:
    CN=test self-signed

Public Key Algorithm:
    Algorithm ObjectId: 1.2.840.113549.1.1.1 RSA (RSA_SIGN)
    Algorithm Parameters:
    05 00
Public Key Length: 2048 bits
Public Key: UnusedBits = 0
    0000  30 82 01 0a 02 82 01 01  00 cf e3 83 c7 a4 05 dd
    0010  be 05 76 b6 26 16 ae ba  0f a1 c6 3f 4f 58 11 2a
    0020  4c fe fc 44 f5 d2 11 36  75 c8 c9 90 15 d3 06 94
    0030  18 ea 10 d8 4c 77 60 1f  45 75 25 6f 21 08 84 d3
    0040  8f 6f 70 07 1b 3e eb 26  94 b8 aa 0d fd 0c 13 f1
    0050  7f 76 0c 33 a4 ad b4 7a  f3 c1 f1 d8 c9 a0 ba d2
    0060  c5 9e 2b ce 36 7e 34 9b  81 26 74 0b 32 47 48 48
    0070  08 ab c0 e7 c3 a2 8e e4  1f b8 6f 38 a2 31 84 65
    0080  75 67 db 01 fc 41 a8 98  83 ad ba 2f 4e 59 c3 6b
    0090  93 84 e0 ab de bd 6f 8f  61 9b b3 42 b3 fb 19 f7
    00a0  46 3a ad d7 e9 d1 fa 2b  a7 72 8d 76 ac 9f 6d c3
    00b0  79 ba 37 e4 6d 72 b1 6f  22 82 80 77 a7 92 3f b7
    00c0  e2 1f e0 c6 90 9a 82 ef  40 47 29 fb c3 83 7e 38
    00d0  01 35 1f 66 6c 1b 93 0d  c2 fc 5c e2 4e bd e1 85
    00e0  c3 7e a9 51 6f 57 82 86  37 79 92 63 b2 e0 42 4f
    00f0  25 5c 1b 03 50 29 2d ee  40 31 c3 a1 c3 cf 62 31
    0100  e0 8c 60 2f d4 34 56 f1  bf 02 03 01 00 01
Certificate Extensions: 2
    2.5.29.15: Flags = 1(Critical), Length = 4
    Key Usage
        Digital Signature, Non-Repudiation, Key Encipherment, Data Encipherment (f0)

    2.5.29.14: Flags = 0, Length = 16
    Subject Key Identifier
        5b 3b 53 ed e3 0f a9 48 90 e0 93 09 0f f9 7b 32 3a 8d 89 4f

Signature Algorithm:
    Algorithm ObjectId: 1.2.840.113549.1.1.11 sha256RSA
    Algorithm Parameters:
    05 00
Signature: UnusedBits=0
    0000  3c 08 5f e0 a7 42 2a bc  58 61 64 43 b6 f4 23 99
    0010  ca 58 b1 8c a3 6b eb 9c  31 a0 ce 25 3a d5 b4 74
    0020  c2 0c 9c 00 1e c8 0f d2  05 3d fc 5d 6f 17 cd ac
    0030  4d 14 9e d4 2b 45 1e ad  5f 5b ee 23 a8 29 65 b3
    0040  cd c4 fd 5c e6 6a bd 95  ce f0 f9 be 31 19 87 90
    0050  f8 86 c4 31 a8 b3 d5 b3  14 24 5b de f8 c0 f9 9c
    0060  96 a2 b5 89 39 41 bd 4b  5f 04 16 10 c0 5c b8 fb
    0070  1d 8d 64 b2 87 00 72 46  b9 5e d0 3a 75 8d ea 5a
    0080  f6 5d 9c c5 03 cd c8 54  b7 7a ef c8 3e 3f 4b f6
    0090  d2 c7 70 67 29 92 70 44  fc c6 2e c9 42 dd 6e 01
    00a0  c5 71 27 20 51 ed 34 3c  98 c2 bc 1f 57 16 71 86
    00b0  24 e3 0e 41 57 82 ba 41  df b5 6d f9 4d e4 72 80
    00c0  6f 8d ab 10 06 cd 69 6b  d0 82 ac db 04 da 6b a5
    00d0  83 14 1a a0 6d 90 c4 01  5d 24 68 ac 10 ca db 96
    00e0  44 8b ef f1 13 7f 22 15  32 93 4e 2d 23 ce 7f fb
    00f0  18 9f d0 1c c1 45 2c e6  bb 23 7f 9e 22 ea fc 88
Signature matches Public Key
Root Certificate: Subject matches Issuer
Key Id Hash(rfc-sha1): 5b 3b 53 ed e3 0f a9 48 90 e0 93 09 0f f9 7b 32 3a 8d 89 4f
Key Id Hash(sha1): 1e 07 bb 05 ce d2 db 9c 9f ab d1 46 b8 32 20 e3 41 dc 4c 08
Cert Hash(md5): 45 ab 9b e4 6e 91 53 b5 96 81 10 8e 01 45 6c 54
Cert Hash(sha1): 37 ed 7c 3e ee 76 a2 d0 42 3a e3 1a 16 9f 74 d0 3c 7f 34 2c

  CERT_REQUEST_ORIGINATOR_PROP_ID(71):
    VM-DESKTEST.ntdev.corp.microsoft.com

  CERT_KEY_PROV_INFO_PROP_ID(2):
    Key Container = PKContainer
    Provider = nCipher Security World Key Storage Provider
    ProviderType = 0
    Flags = 20
    KeySpec = 0

  CERT_SHA1_HASH_PROP_ID(3):
    37 ed 7c 3e ee 76 a2 d0 42 3a e3 1a 16 9f 74 d0 3c 7f 34 2c

  CERT_SUBJECT_PUBLIC_KEY_MD5_HASH_PROP_ID(25):
    12 eb 13 79 64 61 08 e9 a6 75 f2 9a 5c 49 b4 f9

  CERT_KEY_IDENTIFIER_PROP_ID(20):
    5b 3b 53 ed e3 0f a9 48 90 e0 93 09 0f f9 7b 32 3a 8d 89 4f

  CERT_SIGNATURE_HASH_PROP_ID(15):
       0000  38 c4 1b 14 d8 74 95 42  1b fb 7d 72 d2 0b 03 ad
    0010  bd e8 aa 19 14 9e a2 41  30 fe b4 d4 93 b6 9f 3b

  CERT_MD5_HASH_PROP_ID(4):
    45 ab 9b e4 6e 91 53 b5 96 81 10 8e 01 45 6c 54
  UI Policy = 0
    Version: 0

PKContainer

  Export Policy = 0
  Key Usage = 3
    NCRYPT_ALLOW_DECRYPT_FLAG -- 1
    NCRYPT_ALLOW_SIGNING_FLAG -- 2

  D:AI(A;ID;FA;;;SY)(A;ID;FA;;;BA)(A;ID;0x1200a9;;;BU)

    Allow WriteNT AUTHORITY\SYSTEM
    Allow WriteBUILTIN\Administrators
    Allow WriteBUILTIN\Users

Private key is NOT exportable
Signature test passed
CertUtil: -store command completed successfully.
```

### <a name="span-idbackingupthecertificatespanspan-idbackingupthecertificatespanspan-idbackingupthecertificatespanbacking-up-the-certificate"></a><span id="Backing_up_the_certificate"></span><span id="backing_up_the_certificate"></span><span id="BACKING_UP_THE_CERTIFICATE"></span>备份证书

建议您备份您的证书。 这样一来，如果证书存储或服务器出现故障，您可以添加证书回存储区。 对于 certreq.exe 的详细信息，请参阅[高级证书注册和管理︰ 附录 3: Certreq.exe 语法](http://go.microsoft.com/fwlink/?LinkId=317912)

注意，PK 是自签名的证书，并还可用于签名 KEK。

有 2 部分对 PK 签名 / 初始资源调配。 请与您的 Microsoft 联系人获取这些脚本︰

-   `subcreate_set_PK_example_initial_provisioning_example.ps1`. 由 signtool 号 PK 以后进入服务的情况。

-   `subcreate_set_PK_service_example.ps1`. 因为我们正在处理的 HSM 情况，脚本中适用以下行适用。

## <a name="span-idsigningwithpkcertificateservicingscenariospanspan-idsigningwithpkcertificateservicingscenariospanspan-idsigningwithpkcertificateservicingscenariospansigning-with-pk-certificate-servicing-scenario"></a><span id="Signing_with_PK_certificate__servicing_scenario_"></span><span id="signing_with_pk_certificate__servicing_scenario_"></span><span id="SIGNING_WITH_PK_CERTIFICATE__SERVICING_SCENARIO_"></span>用 PK （维修方案） 的证书签名


本部分适用于用 PK 证书签名，可能并不适用于系统的初始设置。 但是，可以使用下面的方法来测试您的服务方案。

### <a name="span-iddeterminethecertificatehashsha1spanspan-iddeterminethecertificatehashsha1spanspan-iddeterminethecertificatehashsha1spandetermine-the-certificate-hash-sha1"></a><span id="Determine_the_certificate_hash__sha1_"></span><span id="determine_the_certificate_hash__sha1_"></span><span id="DETERMINE_THE_CERTIFICATE_HASH__SHA1_"></span>确定证书哈希 (sha1)

确定证书的 SHA1 哈希。 可以使用以下方法之一来获取的 SHA1 哈希︰

-   在 Windows 中，打开**证书**文件，选择**详细信息**选项卡，以及检查**指纹**值。

-   或者，使用下面的命令︰

    ``` syntax
    C:\>certutil -store My PKContainer
    ```

    输出示例︰

    ``` syntax
    My
    ================ Certificate 5 ================
    Serial Number: 58efcfd8f929c5bd41152a8ec413051e
    Issuer: CN=test self-signed
     NotBefore: 1/30/2013 3:24 PM
     NotAfter: 1/30/2019 3:34 PM
    Subject: CN=test self-signed
    Signature matches Public Key
    Root Certificate: Subject matches Issuer
    Template:
    Cert Hash(sha1): db 31 4d a0 d0 ef 87 d4 2b 42 f7 4b 9c 38 a1 f9 17 3e f7 a2
      Key Container = PKContainer
      Provider = nCipher Security World Key Storage Provider
    Private key is NOT exportable
    Signature test passed
    CertUtil: -store command completed successfully.
    ```

### <a name="span-idsignwithsigntoolwiththecertificatestorespecifiedasareferencespanspan-idsignwithsigntoolwiththecertificatestorespecifiedasareferencespanspan-idsignwithsigntoolwiththecertificatestorespecifiedasareferencespansign-with-signtool-with-the-certificate-store-specified-as-a-reference"></a><span id="Sign_with_signtool_with_the_certificate_store_specified_as_a_reference"></span><span id="sign_with_signtool_with_the_certificate_store_specified_as_a_reference"></span><span id="SIGN_WITH_SIGNTOOL_WITH_THE_CERTIFICATE_STORE_SPECIFIED_AS_A_REFERENCE"></span>使用 signtool 签名与指定为引用的证书存储区

使用 SHA1 哈希 KEK 证书进行签名︰

``` syntax
C:\> signtool.exe  sign /v /fd sha256 /sha1 "db314da0d0ef87d42b42f74b9c38a1f9173ef7a2" /sm /p7  .\ /p7co 1.2.840.113549.1.7.1 /p7ce  DetachedSignedData KEK.bin
```

其中，KEK.bin 是证书的二进制要签名的文件名。

输出示例︰

``` syntax
The following certificate was selected:
    Issued to: test self-signed
    Issued by: test self-signed
    Expires:   Fri Jan 30 15:34:32 2019
    SHA1 hash: DB314DA0D0EF87D42B42F74B9C38A1F9173EF7A2

Done Adding Additional Store
Successfully signed: KEK.bin

Number of files successfully Signed: 1
Number of warnings: 0
Number of errors: 0
```

更多的信息，请参阅[签名工具 (SignTool.exe)](http://go.microsoft.com/fwlink/?LinkId=317911)和[Windows 8.1 安全启动密钥创建和管理指导](windows-secure-boot-key-creation-and-management-guidance.md)。

## <a name="span-idappendixausingthaleskeysafeforviewingkeysspanspan-idappendixausingthaleskeysafeforviewingkeysspanspan-idappendixausingthaleskeysafeforviewingkeysspanappendix-a-using-thales-keysafe-for-viewing-keys"></a><span id="Appendix_A___Using_Thales_KeySafe_for_viewing_keys"></span><span id="appendix_a___using_thales_keysafe_for_viewing_keys"></span><span id="APPENDIX_A___USING_THALES_KEYSAFE_FOR_VIEWING_KEYS"></span>附录 A – 查看密钥使用 Thales KeySafe


Thales KeySafe 基于 GUI。

若要使用 KeySafe，您必须已安装 JRE/JDK 1.4.2、 1.5 或 1.6。 安装 nCipher 软件之前，请安装 Java。

配置下的 hardserver 配置文件`%NFAST_KMDATA%\config\`文件夹︰

在中编辑设置`server_startup`部分中︰

**nonpriv\_端口**。 此字段指定 hardserver 侦听本地非特权 TCP 连接的端口。

-   默认为连接到端口 9000。

-   如果`NFAST_SERVER_PORT`环境变量已设置，该设置将替代任何值 nonpriv\_端口

**专用\_端口。** 此字段指定 hardserver 侦听本地特权的 TCP 连接的端口。

-   默认为连接到端口 9001。

-   如果`NFAST_SERVER_PRIVPORT`环境变量已设置，该设置将替代任何值专用\_端口

以下是 Thales KeySafe GUI 中的屏幕快照︰

![thales keysafe 键操作菜单的屏幕抓图](images/dep-8-secureboot-hsm-operations.png)

下面的图像是由启动 KeySafe 实用程序，然后导航到 KeyList 菜单生成的。

![thales keysafe keylist 菜单的屏幕抓图](images/dep-8-secureboot-hsm-keylisting.png)

有关详细信息，请参阅 nCipher/Thales 用户指南。

## <a name="span-idappendixbusingsafenetcmuutilitytoviewkeysspanspan-idappendixbusingsafenetcmuutilitytoviewkeysspanspan-idappendixbusingsafenetcmuutilitytoviewkeysspanappendix-b-using-safenet-cmu-utility-to-view-keys"></a><span id="Appendix_B__Using_SafeNet_CMU_Utility_to_view_keys"></span><span id="appendix_b__using_safenet_cmu_utility_to_view_keys"></span><span id="APPENDIX_B__USING_SAFENET_CMU_UTILITY_TO_VIEW_KEYS"></span>附录 b︰ 使用 SafeNet CMU 实用程序来查看密钥


有关详细信息，请参阅 SafeNet Luna HSM 文档。

``` syntax
C:\Program Files\SafeNet\LunaClient>cmu list
Please enter password for token in slot 1: ********
handle=72       label=PKContainer
handle=43       label=PKContainer

C:\Program Files\SafeNet\LunaClient>cmu getattribute
Please enter password for token in slot 1: ********
Select object to query
Handler Label
72      PKContainer
43      PKContainer
Enter handler (or 0 for exit): 72
class=privateKey
token=true
private=true
label=PKContainer
keytype=RSA
subject=
id=3081cd300d02050080000010020401000000300c02050080000011020346494d3053020500800
00014024a660064006400340064006400330061002d0064003900610064002d00340066006200630
02d0062003000320031002d006300660034006100650064006100650035006400350033000000301
d0205008000001302140100000000000000000000000000000000000000300d02050080000015020
400000000300d02050080000016020400000000300d02050080000017020400000000300d0205008
0000018020400000000
sensitive=true
decrypt=true
unwrap=true
sign=true
derive=false
startdate=
enddate=
modulus=b56a518c2744a3341dd1ed27cfe5dc6cabac7d4b820c00d60cb2a4b713f28b3e1836b619
b61b79be76d1870e09961972c83cc338a2065880ec4f6fb00c48f1f953c7fff132be9df36f13bcda
f0f873bcfaa81734290f85ff123072b258fb16b0833722af72f90fd29c533153b0ba52d502ab11c4
81cd6e60733cfa39a811c7ff381ba57081c818881a6bbeeb60091ab9f26f6cd177dcff884d7d9edb
e69e61b316ef12785f5957a1e6bb0b21497b328e475f82e7efac71815d2c153b5991ebfacf4bb75c
72afff513a55f68f260f09aa9d687639a24e1ce35fd5588d27c2ff69b7e6c9b5fcb4ec7d55674e85
45f051d4945ae5d46d958056aaf7e01943eda91d
modulusbits=2048
publicexponent=010001
extractable=true
local=true
neverextractable=false
alwayssensitive=true
modifiable=true
```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Windows 8.1 安全启动密钥创建和管理指南](windows-secure-boot-key-creation-and-management-guidance.md)

[安全引导概述](secure-boot-overview.md)

 

 






