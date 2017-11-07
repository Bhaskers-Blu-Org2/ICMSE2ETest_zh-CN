---
title: "报告 CSP"
description: "报告配置服务提供程序用于检索 Windows （以前称为企业数据保护） 的信息保护和安全审核日志。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 148441A6-D9E1-43D8-ADEE-FB62E85A39F7
ms.openlocfilehash: c27a119b35b3dfffc18efe147dfda81449120068
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="reporting-csp"></a>报告 CSP


报告配置服务提供程序用于检索 Windows （以前称为企业数据保护） 的信息保护和安全审核日志。 Windows 10 1511年版本中添加了该 CSP。 桌面窗口 10，1607年版本中添加了对桌面安全审核的支持。

下面的关系图以树格式显示报告配置服务提供程序。

![csp 的报告图表](images/provisioning-csp-reporting.png)

<a href="" id="reporting"></a>**报告**  
根节点。

<a href="" id="reporting-enterprisedataprotection"></a>**报告 EnterpriseDataProtection**  
用于检索 Windows 信息保护 （以前称为企业数据保护） 的内部节点记录。

<a href="" id="reporting-securityauditing--for-mobile-only-"></a>**安全审计报告 /**（对于手机仅）  
用于检索安全审核日志的内部节点。 此节点是仅用于移动设备。

<a href="" id="retrievebytimerange"></a>**RetrieveByTimeRange**  
返回日志中的开始时间和停止时间存在。 以 ISO 8601 格式表示的开始时间和停止时间。 如果不指定开始时间和停止时间，然后这些值被解释为先现有或最后一个现有的时间。

以下是其他可能的方案︰

-   如果不指定开始时间和停止时间，然后它返回所有现有的日志。
-   如果指定的停止时间，但不是指定开始时间，然后返回在停止时间之前存在的所有日志。
-   如果指定开始时间，但未指定停止时间，从开始时间存在的所有记录，则会返回。

<a href="" id="retrievebycount"></a>**RetrieveByCount**  
从开始时间检索指定的数目的日志的内部节点。 以 ISO 8601 格式表示的开始时间。 您可以设置日志设置 LogCount 和开始时间所需的数量。 它返回指定的数目的日志或更少，如果总编号日志小于 LogCount。

<a href="" id="logs"></a>**日志**  
包含报表的日志。

值类型是 XML。

支持的操作是获得。

<a href="" id="starttime"></a>**开始时间**  
指定用于检索日志的开始时间。

值类型是字符串。 使用 ISO 8601 格式。

支持的操作包括获取和替换。

<a href="" id="stoptime"></a>**停止时间**  
指定用于检索日志的结束时间。

值类型是字符串。 使用 ISO 8601 格式。

支持的操作包括获取和替换。

<a href="" id="logcount"></a>**LogCount**  
指定要检索从开始时间的日志数目。

值类型是 int。

支持的操作包括获取和替换。

## <a name="examples"></a>示例


检索所有可用的 Windows （以前称为企业数据保护） 的信息保护日志从指定的开始时间开始。

``` syntax
<SyncML>
    <SyncBody>
        <Replace>
            <CmdID>3</CmdID>
            <Item>
                <Target><LocURI>./Vendor/MSFT/PolicyManager/My/DataProtection/EnterpriseProtectedDomainNames</LocURI></Target>
                <Data>microsoft.com|office.com|xbox.com</Data>
            </Item>
        </Replace>
        <Replace>
            <CmdID>2</CmdID>
            <Item>
                <Target><LocURI>./Vendor/MSFT/Reporting/EnterpriseDataProtection/RetrieveByTimeRange/StartTime</LocURI></Target>
                <Data>2012-11-30T01:48:14.233Z</Data>
            </Item>
        </Replace>
        <Get>
            <CmdID>4</CmdID>
            <Item>
                <Target><LocURI>./Vendor/MSFT/Reporting/EnterpriseDataProtection/RetrieveByTimeRange/Logs</LocURI></Target>
            </Item>
        </Get>
        <Final/>
    </SyncBody>
</SyncML>
```

检索指定的数目的安全审核日志从指定的开始时间开始。

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.2">
  <SyncBody>
    <Replace>
      <CmdID>1</CmdID>
      <Item>
        <Target>
          <LocURI>
            ./Vendor/MSFT/Reporting/SecurityAuditing/RetrieveByCount/LogCount
          </LocURI>
        </Target>
        <Meta>
          <Format xmlns="syncml:metinf">int</Format>
          <Type>text/plain</Type>
        </Meta>
        <Data>10</Data>
      </Item>
    </Replace>
    <Replace>
      <CmdID>2</CmdID>
      <Item>
        <Target>
          <LocURI>
            ./Vendor/MSFT/Reporting/SecurityAuditing/RetrieveByCount/StartTime
          </LocURI>
        </Target>
        <Meta>
          <Format xmlns="syncml:metinf">chr</Format>
          <Type>text/plain</Type>
        </Meta>
        <Data>2015-08-12T08:15:30:27</Data>
      </Item>
    </Replace>
    <Get>
      <CmdID>3</CmdID>
      <Item>
        <Target>
          <LocURI>
            ./Vendor/MSFT/Reporting/SecurityAuditing/RetrieveByCount/Logs
          </LocURI>
        </Target>
      </Item>
    </Get>
    <Final/> 
  </SyncBody>
</SyncML>
```

 

 






