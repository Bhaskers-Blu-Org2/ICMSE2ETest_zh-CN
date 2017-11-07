---
title: "WindowsAdvancedThreatProtection 的 CSP"
description: "WindowsAdvancedThreatProtection 的 CSP"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 6C3054CA-9890-4C08-9DB6-FBEEB74699A8
ms.openlocfilehash: a69f7277913d31fe44b1977425548ffc7f8ec99f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windowsadvancedthreatprotection-csp"></a>WindowsAdvancedThreatProtection 的 CSP


Windows Defender 高级威胁保护 (WDATP) 配置服务提供程序 (CSP) 板载，允许 IT 管理员确定 WDATP 的配置和运行状况，以及离职的终结点。

下图显示了使用开放移动联盟 (OMA) 设备管理 (DM) 的树格式 WDATP 配置服务提供程序。

![windowsadvancedthreatprotection 的 csp 图](images/provisioning-csp-watp.png)

下面的列表描述特征和参数。

<a href="" id="--device-vendor-msft-windowsadvancedthreatprotection"></a>**./Device/Vendor/MSFT/WindowsAdvancedThreatProtection**  
Windows Defender 高级威胁防护配置服务提供程序的根节点。

受支持的操作是获得。

<a href="" id="onboarding"></a>**板载**  
设置 Windows Defender 高级威胁保护板载 blob 和启动到 Windows Defender 高级威胁保护服务。

数据类型是一个字符串。

支持的操作包括获取和替换。

<a href="" id="healthstate"></a>**HealthState**  
表示 Windows Defender 高级威胁保护健康状态的节点。

<a href="" id="healthstate-lastconnected"></a>**HealthState/LastConnected**  
包含上一次成功的连接的时间戳。

受支持的操作是获得。

<a href="" id="healthstate-senseisrunning"></a>**HealthState/SenseIsRunning**  
布尔值，该值标识 Windows Defender 高级威胁保护意义上运行状态。

默认值为 false。

受支持的操作是获得。

<a href="" id="healthstate-onboardingstate"></a>**HealthState/OnboardingState**  
表示服务状态。

受支持的操作是获得。

下面的列表显示了受支持的值︰

-   0 （默认）-不 onboarded。
-   1-Onboarded

<a href="" id="healthstate-orgid"></a>**HealthState/OrgId**  
字符串，表示 OrgID。

受支持的操作是获得。

<a href="" id="configuration"></a>**配置**  
表示 Windows Defender 高级威胁保护配置。

<a href="" id="configuration-samplesharing"></a>**配置/SampleSharing**  
返回或设置 Windows Defender 高级威胁保护示例共享配置参数︰ 0-无、 1-全部

下面的列表显示了受支持的值︰

-   0-无
-   1 （缺省值）-所有

支持的操作包括获取和替换。

<a href="" id="offboarding"></a>**Offboarding**  
设置 Windows Defender 高级威胁保护 Offboarding 斑点并启动 Windows Defender 高级威胁保护到 offboarding。

数据类型是一个字符串。

支持的操作包括获取和替换。

## <a name="examples"></a>示例


``` syntax
<SyncML xmlns="SYNCML:SYNCML1.2">
  <SyncBody>
    <Get>
      <CmdID>11</CmdID>
      <Item>
        <Target>
          <LocURI>
            ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/Onboarding
          </LocURI>
        </Target>
      </Item>
    </Get>
    <Get>
      <CmdID>1</CmdID>
      <Item>
        <Target>
          <LocURI>
            ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/HealthState/LastConnected
          </LocURI>
        </Target>
      </Item>
    </Get>
        <Get>
      <CmdID>2</CmdID>
      <Item>
        <Target>
          <LocURI>
            ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/HealthState/OnBoardingState
          </LocURI>
        </Target>
      </Item>
    </Get>
            <Get>
      <CmdID>3</CmdID>
      <Item>
        <Target>
          <LocURI>
            ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/HealthState/SenseIsRunning
          </LocURI>
        </Target>
      </Item>
    </Get>
            <Get>
      <CmdID>4</CmdID>
      <Item>
        <Target>
          <LocURI>
            ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/HealthState/OrgId
          </LocURI>
        </Target>
      </Item>
    </Get>

            <Get>
      <CmdID>5</CmdID>
      <Item>
        <Target>
          <LocURI>
            ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/Configuration/SampleSharing
          </LocURI>
        </Target>
      </Item>
    </Get>
    <Get>
      <CmdID>99</CmdID>
      <Item>
        <Target>
          <LocURI>
            ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/Offboarding
          </LocURI>
        </Target>
      </Item>
    </Get>
    <Final/> 
  </SyncBody>
</SyncML>
```

## <a name="related-topics"></a>相关的主题


[配置服务提供程序的引用](configuration-service-provider-reference.md)

 

 






