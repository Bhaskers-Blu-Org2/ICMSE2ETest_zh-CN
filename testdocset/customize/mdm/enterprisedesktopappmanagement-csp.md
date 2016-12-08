---
title: "EnterpriseDesktopAppManagement 的 CSP"
description: "EnterpriseDesktopAppManagement 配置服务提供程序用于处理企业桌面应用程序管理任务，例如查询已安装的企业应用程序，安装应用程序，或者删除应用程序。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 2BFF7491-BB01-41BA-9A22-AB209EE59FC5
ms.openlocfilehash: 2672eb2a8dd5344ab5a69fa6262e185f2cf8a1de
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="enterprisedesktopappmanagement-csp"></a>EnterpriseDesktopAppManagement 的 CSP


EnterpriseDesktopAppManagement 配置服务提供程序用于处理企业桌面应用程序管理任务，例如查询已安装的企业应用程序，安装应用程序，或者删除应用程序。

安装应用程序可能需要一些时间才能完成，因此它们是以异步方式完成。 Exec 命令完成后，客户端可以向一般警报管理服务器的状态，无论是失败还是成功。 SyncML 的示例，请参见[警报的示例](#alert-example)。

下面的关系图以树格式显示 EnterpriseDesktopAppManagement CSP。

![enterprisedesktopappmanagement 的 csp](images/provisioning-csp-enterprisedesktopappmanagement.png)

<a href="" id="--vendor-msft-enterprisedesktopappmanagement"></a>**./Vendor/MSFT/EnterpriseDesktopAppManagement**  
EnterpriseDesktopAppManagement 配置服务提供程序的根节点。

<a href="" id="msi"></a>**MSI**  
对于所有设置的节点。

<a href="" id="msi-productid"></a>**MSI / ***_产品 id_**  
应用程序的 MSI 产品代码。

<a href="" id="msi-productid-version"></a>* *MSI /*产品 id*/Version**  
版本编号。 值类型是字符串。 受支持的操作是获得。

<a href="" id="msi-productid-name"></a>* *MSI /*产品 id*/Name**  
应用程序的名称。 值类型是字符串。 受支持的操作是获得。

<a href="" id="msi-productid-publisher"></a>* *MSI /*产品 id*/Publisher**  
应用程序的发行者。 值类型是字符串。 受支持的操作是获得。

<a href="" id="msi-productid-installpath"></a>* *MSI /*产品 id*/InstallPath**  
应用程序安装路径。 值类型是字符串。 受支持的操作是获得。

<a href="" id="msi-productid-installdate"></a>* *MSI /*产品 id*/InstallDate**  
应用程序的安装日期。 值类型是字符串。 受支持的操作是获得。

<a href="" id="msi-productid-downloadinstall"></a>* *MSI /*产品 id*/DownloadInstall**  
执行下载和安装此应用程序。 值类型是字符串。 支持的操作的执行并获得。

<a href="" id="msi-productid-status"></a>* *MSI /*产品 id*/Status**  
该应用程序的状态。 值类型是字符串。 受支持的操作是获得。

| 。                    | 值 |
|---------------------------|-------|
| 初始化               | 10    |
| 正在下载      | 20    |
| 重试等待下载    | 25    |
| 下载失败           | 30    |
| 下载已完成        | 40    |
| 挂起用户会话      | 48    |
| 正在进行中的实施   | 50    |
| 挂起的强制重试 | 55    |
| 实施失败        | 60    |
| 已完成的实施     | 70    |

 

<a href="" id="msi-productid-lasterror"></a>* *MSI /*产品 id*/LastError**  
应用程序安装过程最后的错误代码。 这通常是作为 HRESULT 格式存储的。 这取决于什么发生在发生错误时，这可能是从一个失败的 API 执行 MSIExec.exe 或出现错误的结果。

值类型是字符串。 受支持的操作是获得。

<a href="" id="msi-productid-lasterrordesc"></a>* *MSI /*产品 id*/LastErrorDesc**  
包含上一次的错误代码说明。 LastErrorDesc 值查找匹配的 LastError 值。 有时没有返回任何 LastErrorDesc。

值类型是字符串。 受支持的操作是获得。

## <a name="examples"></a>示例


**SyncML 请求 CSP 版本信息**

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.1">
  <SyncBody>
    <Get>
      <CmdID>12345</CmdID>
      <Item>
        <Target>
          <LocURI>./Device/Vendor/MSFT/EnterpriseDesktopAppManagement?prop=Type</LocURI>
        </Target>
      </Item>
    </Get>
    <Final/>
  </SyncBody>
</SyncML>
```

下表描述了在上面示例中的字段︰

| 名称   | 说明                                                                                                                   |
|--------|-------------------------------------------------------------------------------------------------------------------------------|
| 获取    | 正在执行的操作。 获取操作是要返回的信息的请求。                                              |
| CmdID  | 用于引用请求的输入的值。 响应将包含此值可用于匹配请求和响应。 |
| LocURI | Win32 CSP 命令处理器的路径。                                                                                          |

 

**SyncML 执行卸载应用程序的 MSI 操作**

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.1">
  <SyncBody>
    <Delete>
      <CmdID>12345</CmdID>
      <Item>
        <Target>
          <LocURI>./Device/Vendor/MSFT/EnterpriseDesktopAppManagement/MSI/%7B1803A630-3C38-4D2B-9B9A-0CB37243539C%7D</LocURI>
        </Target>
      </Item>
    </Delete>
    <Final/>
  </SyncBody>
</SyncML>
```

下表描述了在上面示例中的字段︰

| 名称   | 说明                                                                                                                                                                                                         |
|--------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 删除 | 正在执行的操作。 删除操作是删除 CSP 节点，该值表示指定的 MSI 安装应用程序并进行执行和卸载过程中的应用程序的请求。 |
| CmdID  | 用于引用请求的输入的值。 响应将包含此值可用于匹配请求和响应。                                                                                       |
| LocURI | 为 Win32 CSP 命令处理器，包括产品 ID （在此示例中为 1803A630-3C38-4D2B-9B9A-0CB37243539C） 的路径转义以 XML 格式的属性。                                                          |

 

**SyncML 执行 MSI 操作的应用程序状态报告**

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.1">
  <SyncBody>
    <Get>
      <CmdID>12345</CmdID>
      <Item>
        <Target>
          <LocURI>./Device/Vendor/MSFT/EnterpriseDesktopAppManagement/MSI/%7B1803A630-3C38-4D2B-9B9A-0CB37243539C%7D</LocURI>
        </Target>
      </Item>
    </Get>
    <Final/>
  </SyncBody>
</SyncML>
```

下表描述了在上面示例中的字段︰

| 名称   | 说明                                                                                                                                                |
|--------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 获取    | 正在执行的操作。 获取操作是对报表的状态指定的 MSI 安装应用程序的请求。                                 |
| CmdID  | 用于引用请求的输入的值。 响应将包含此值可用于匹配请求和响应。                              |
| LocURI | 为 Win32 CSP 命令处理器，包括产品 ID （在此示例中为 1803A630-3C38-4D2B-9B9A-0CB37243539C） 的路径转义以 XML 格式的属性。 |

 

**SyncML 执行针对特定用户设备上的应用程序的 MSI 安装操作。添加命令，则需要低于 Exec 命令。**

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.1">
  <SyncBody>
    <Add>
      <CmdID>1</CmdID>
      <Item>
        <Target>
        <LocURI>./User/Vendor/MSFT/EnterpriseDesktopAppManagement/MSI/%7B1803A630-3C384D2B-9B9A-0CB37243539C%7D/DownloadInstall</LocURI>
        </Target>
      </Item>
    </Add>
    <Exec>
      <CmdID>6</CmdID>
      <Item>
        <Target>
          <LocURI>./User/Vendor/MSFT/EnterpriseDesktopAppManagement/MSI/%7B1803A630-3C38-4D2B-9B9A-0CB37243539C%7D/DownloadInstall</LocURI>
        </Target>
        <Meta>
          <Format xmlns="syncml:metinf">xml</Format>
          <Type xmlns="syncml:metinf">text/plain</Type>
        </Meta>
        <Data>
          <MsiInstallJob id="{9BD4F7CD-880A-40B5-B74C-1BEECB51E596}">
            <Product Version="1.0.0">
              <Download>
                <ContentURLList>
                  <ContentURL>
                    http://bcl-w2k12r2-vm/testapps/msi/reboot/reboot.msi
                  </ContentURL>
                  <ContentURL>https://dp2.com/packages/myApp.msi</ContentURL>
                </ContentURLList>
              </Download>
              <Validation>                
<FileHash>134D8F1F7C3C036DC3DCDA9F97515C8C7951DB154B73365C9C22962BD23E3EB3</FileHash>
              </Validation>
              <Enforcement>
                <CommandLine>/quiet</CommandLine>
                <TimeOut>5</TimeOut>
                <RetryCount>3</RetryCount>
                <RetryInterval>5</RetryInterval>
              </Enforcement>
            </Product>
          </MsiInstallJob>
        </Data>
      </Item>
    </Exec>
    <Final/>
  </SyncBody>
</SyncML>
```

下表描述了在上面示例中的字段︰

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>名称</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Add</td>
<td>这是前面 Exec 命令所必需的。
<ul>
<li>CmdID-用于引用请求的输入值。 Reponses 包含此值，可用于匹配请求和响应。</li>
<li>LocURI-指向 Win32 CSP 命令处理器，包括产品 ID （在此示例中为 1803A630-3C38-4D2B-9B9A-0CB37243539C） 的路径转义以 XML 格式的属性。</li>
</ul></td>
</tr>
<tr class="even">
<td>执行</td>
<td>执行节点包含的参数和属性需要查找、 下载、 验证和执行产品安装。
<ul>
<li>CmdID-用于引用请求的输入值。 响应将包含此值可用于匹配请求和响应。</li>
<li>LocURI-指向 Win32 CSP 命令处理器，包括产品 ID （在此示例中为 1803A630-3C38-4D2B-9B9A-0CB37243539C） 的路径转义以 XML 格式的属性。</li>
<li>数据的数据节点包含嵌入的 XML 中，"MsiInstallJob"类型的</li>
<li>MsiInstallJob-包含成功下载、 验证和执行 MSI 安装过程所需的所有信息 （请参见此嵌入的数据对象详细信息本文档的结尾处一节）。</li>
</ul></td>
</tr>
</tbody>
</table>

 

> **请注意** 将使用标准的 OMA DM 通知机制报告 MSI 在岗的信息状态。 状态报告表示在 Microsoft technet MSIEXEC 主题中定义标准 MSIEXEC 返回代码用作 HRESULT <https://technet.microsoft.com/library/cc759262(v=ws.10).aspx>.

 

**SyncML 执行目标设备 （每台设备安装） 上的所有用户的应用程序的 MSI 安装操作**

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.1">
  <SyncBody>
    <Add>
      <CmdID>1</CmdID>
      <Item>
        <Target>
          <LocURI>./Device /Vendor/MSFT/EnterpriseDesktopAppManagement/MSI/%7B6F7CB29F-1319-4816-B345-0856916EB801%7D/DownloadInstall
          </LocURI>
      </Target>
    </Item>
  </Add>
    <Exec>
      <CmdID>67890</CmdID>
      <Item>
        <Target>
          <LocURI>./Device /Vendor/MSFT/EnterpriseDesktopAppManagement/MSI/%7B6F7CB29F-1319-4816-B345-0856916EB801%7D/DownloadInstall</LocURI>
        </Target>
        <Meta>
          <Format xmlns="syncml:metinf">xml</Format>
          <Type xmlns="syncml:metinf">text/plain</Type>
        </Meta>
        <Data>
          <MsiInstallJob id="{9BD4F7CD-880A-40B5-B74C-1BEECB51E596}">
            <Product Version="1.0.0">
              <Download>
                <ContentURLList>
                  <ContentURL>http://bcl-w2k12r2-vm/testapps/msi/Orca/Orca.msi</ContentURL>
                  <ContentURL>https://dp2.com/packages/myApp.msi</ContentURL>
                </ContentURLList>
              </Download>
              <Validation>
                <FileHash>4525065777EF18B9444ABF71DD4B48E5F64F4F0E1E029995FB8DA441CDE4296E</FileHash>
              </Validation>
              <Enforcement>
                <CommandLine>/quiet</CommandLine>
                <TimeOut>5</TimeOut>
                <RetryCount>3</RetryCount>
                <RetryInterval>5</RetryInterval>
              </Enforcement>
            </Product>
          </MsiInstallJob>
        </Data>
      </Item>
    </Exec>
    <Final/>
  </SyncBody>
</SyncML>
```

下表 MsiInstallJob 中描述的架构元素。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>元素</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>MsiInstallJob</td>
<td>根元素
<p>&quot;特性︰ &quot;id-正在安装的应用程序的应用程序标识符</p></td>
</tr>
<tr class="even">
<td>Product</td>
<td>MsiInstallJob 的子元素
<p>属性:"版本"--应用程序版本的字符串表示形式</p></td>
</tr>
<tr class="odd">
<td>下载</td>
<td>产品的子元素。 下载配置信息的容器。</td>
</tr>
<tr class="even">
<td>ContentURLList</td>
<td>下载的子元素。 包含一个或多个内容下载 URL 定位器在窗体中的 ContentURL 元素的列表。</td>
</tr>
<tr class="odd">
<td>ContentURL</td>
<td>应从下载位置的内容。 必须为属性设置格式的 URL 指向。MSI 文件。</td>
</tr>
<tr class="even">
<td>验证</td>
<td>包含用于验证信息面临的真实性。 • FileHash – SHA256 散列值的文件内容</td>
</tr>
<tr class="odd">
<td>FileHash</td>
<td>SHA256 散列值的文件内容</td>
</tr>
<tr class="even">
<td>强制执行</td>
<td>用于安装此 MSI 的安装属性</td>
</tr>
<tr class="odd">
<td>在命令行</td>
<td>在调用 MSIEXEC.exe 时要使用的命令行选项</td>
</tr>
<tr class="even">
<td>Timeout</td>
<td>认为一段时间，以分钟为单位安装过程可以运行安装程序之前的安装可能会失败，并且不再监视安装操作。</td>
</tr>
<tr class="odd">
<td>RetryCount</td>
<td>下载和安装操作将重试之前安装将被标记为失败次数。</td>
</tr>
<tr class="even">
<td>RetryInterval</td>
<td>一段时间，在重试操作之间的分钟数。</td>
</tr>
</tbody>
</table>

 

下面是常见响应请求的示例

``` syntax
<?xml version="1.0" encoding="utf-16"?>
<SyncML>
  <SyncHdr />
  <SyncBody>
    <Status>
      <CmdID>12345</CmdID>
      <MsgRef>1</MsgRef>
      <CmdRef>0</CmdRef>
      <Cmd>SyncHdr</Cmd>
      <Data>200</Data>
    </Status>
    <Status>
      <CmdID>67890</CmdID>
      <MsgRef>1</MsgRef>
      <CmdRef>1</CmdRef>
      <Cmd>Add</Cmd>
      <Data>200</Data>
    </Status>
    <Final />
  </SyncBody>
</SyncML>
```

## <a name="how-to-determine-which-installation-context-to-use-for-an-msi-package"></a>如何确定要使用 MSI 程序包的安装上下文


下表显示了如何在客户端安装应用程序定位和 MSI 软件包类型 （每个用户，每个机器或双重模式）。

对于 Intune 独立环境，MSI 程序包将确定 MSI 执行上下文。

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Target</th>
<th>每个用户 MSI</th>
<th>每台机器 MSI</th>
<th>双模式 MSI</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>User</td>
<td>每个用户 MSI 安装
<p>LocURI 包含用户前缀，如。 / 用户</p></td>
<td>安装每个设备 MSI
<p>LocURI 包含设备的前缀，如。 / 设备</p></td>
<td>每个用户 MSI 安装
<p>LocURI 包含用户前缀，如。 / 用户</p></td>
</tr>
<tr class="even">
<td>System</td>
<td>每个用户 MSI 安装
<p>LocURI 包含用户前缀，如。 / 用户</p></td>
<td>安装每个设备 MSI
<p>LocURI 包含设备的前缀，如。 / 设备</p></td>
<td>每个用户 MSI 安装
<p>LocURI 包含用户前缀，如。 / 用户</p></td>
</tr>
</tbody>
</table>

 

下表适用于 SCCM 混合环境中。

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Target</th>
<th>每个用户 MSI</th>
<th>每台机器 MSI</th>
<th>双模式 MSI</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>User</td>
<td>每个用户 MSI 安装
<p>LocURI 包含用户前缀，如。 / 用户</p></td>
<td>安装每个设备 MSI
<p>LocURI 包含设备的前缀，如。 / 设备</p></td>
<td>每个用户 MSI 安装
<p>LocURI 包含用户前缀，如。 / 用户</p></td>
</tr>
<tr class="even">
<td>System</td>
<td>每个用户 MSI 安装
<p>LocURI 包含用户前缀，如。 / 用户</p></td>
<td>安装每个设备 MSI
<p>LocURI 包含设备的前缀，如。 / 设备</p></td>
<td>安装 MSI 每个系统上下文
<p>LocURI 包含设备的前缀，如。 / 设备</p></td>
</tr>
</tbody>
</table>

 

## <a name="how-to-determine-the-package-type-from-the-msi-package"></a>如何确定从 MSI 包的包类型


-   ALLUSERS =""的每个用户封装类型
-   ALLUSERS = 1-每台机器包类型
-   ALLUSERS = 2，MSIINSTALLPERUSER = 1-双模式程序包类型

属性可以包中指定、 通过命令行传递、 修改的转换，或通过用户界面对话框 （更常见） 选中。

下面是引用的列表︰

-   [使用 Windows 安装程序](https://technet.microsoft.com/library/cc782896.aspx)
-   [创作一个软件包，在 Windows 7 中的每个用户或每台计算机安装上下文](http://blogs.msdn.com/b/windows_installer_team/archive/2009/09/02/authoring-a-single-package-for-per-user-or-per-machine-installation-context-in-windows-7.aspx)
-   SyncML 表示协议，草稿版本 1.3 27 日 2009 年 (OMA-TS SyncML\_RepPro V1\_20090827 3 维)

## <a name="alert-example"></a>警报的示例


``` syntax
<Alert>
       <CmdID>4</CmdID>
       <Data>1224</Data>
       <Item>
          <Source>
             <LocURI>./Device/Vendor/MSFT/EnterpriseDesktopAppManagement/MSI/{AF9257BA-6BBD-4624-AA9B-0182D50292C3}/DownloadInstall</LocURI>
          </Source>
          <Meta>
             <Type xmlns="syncml:metinf">Reversed-Domain-Name:com.microsoft.mdm.win32csp_install</Type>
             <Format xmlns="syncml:metinf">int</Format>
             <Mark xmlns="syncml:metinf">informational</Mark>
          </Meta>
          <Data>0</Data>
       </Item>
</Alert>
```

 

 






