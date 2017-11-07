---
title: "DMProcessConfigXMLFiltered 函数"
description: "利用 OMA 客户端置备 XML 配置电话设置。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
Search.Refinement.TopicID: "184"
ms.assetid: 31D79901-6206-454C-AE78-9B85A3B3487F
keywords: "DMProcessConfigXMLFiltered 函数"
topic_type: apiref
api_name: DMProcessConfigXMLFiltered
api_location: dmprocessxmlfiltered.dll
api_type: DllExport
ms.openlocfilehash: fdb73fa49b41e4b1f49982906574370f118b7913
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="dmprocessconfigxmlfiltered-function"></a>DMProcessConfigXMLFiltered 函数

> **重要**  
此函数用于自动数据配置 (ADC) 已在 Windows Phone 8.1 中被否决。 请有关配置连接的新过程的详细信息，参见[连接配置](https://msdn.microsoft.com/en-us/library/windows/hardware/dn757424)。 仍为其他 OEM 支持此功能的但是，使用。


利用 OMA 客户端置备 XML 配置电话设置。 此函数的用法是局限于以下情况。

-   OMA 客户端配置中添加动态的凭据。

-   生产测试应用程序。 它们销售之前，必须从手机中删除的这些应用程序和支持的驱动程序。

Microsoft 建议，不使用此函数来配置下列设置类型。

-   使用配置的 CertificateStore、 SecurityPolicy 和 RemoteWipe，除非与 OMA DM 或 OMA 客户端设置安全策略的安全设置。

-   非蜂窝数据连接设置 （如热点设置）。

-   文件系统的文件和注册表设置，除非它们用于 OMA DM 帐户管理，移动运营商的数据连接设置或制造测试。

-   电子邮件设置。

> **请注意** **DMProcessConfigXMLFiltered**函数具有完整功能的 Windows 10 移动和 Windows Phone 8.1，但只读功能在 Windows 10 桌面。

 

<a name="syntax"></a>语法
------

```C++
HRESULT STDAPICALLTYPE DMProcessConfigXMLFiltered(
         LPCWSTR pszXmlIn,
   const WCHAR   **rgszAllowedCspNode,
   const DWORD   dwNumAllowedCspNodes,
         BSTR    *pbstrXmlOut
);
```

<a name="parameters"></a>参数
----------

*pszXmlIn*
<ul style="list-style-type:none">
<li>\[在\]的 null 终止 – 输入 XML 缓冲区包含配置数据。 参数包含的 XML，用于配置电话。 **DMProcessConfigXMLFiltered**接受仅 OMA 客户端置备 XML （也称为 WAP 资源调配）。 它不接受 OMA DM SyncML XML (也称为 SyncML)。</li>
</ul>
<br>

*rgszAllowedCspNode*
<ul style="list-style-type:none">
<li>\[在\]的**WCHAR\* ** ，指定允许哪些配置服务提供程序节点调用。</li>
</ul>
<br>

*dwNumAllowedCspNodes*
<ul style="list-style-type:none">
<li>\[在\]在*rgszAllowedCspNode*中传递的元素个数。</li>
</ul>
<br> 

*pbstrXmlOut*
<ul style="list-style-type:none">
<li>\[出\]生成 null – 结尾 XML 配置。 **DMProcessConfigXMLFiltered**的调用方负责清理*pbstrXmlOut*参数引用的输出缓冲区。 使用[**SysFreeString**](https://msdn.microsoft.com/library/windows/hardware/ms221481)来释放内存。</li>
</ul>
<br>

如果**DMProcessConfigXMLFiltered**检索文档， *pbstrXmlOut*包含资源调配操作的 XML 输出 （以字符串形式）。 如果**DMProcessConfigXMLFiltered**返回失败，XML 输出通常包含"错误节点"，指示哪些元素的原始 XML 失败。 如果输入的文档不包含查询和处理成功，输出文档应该与类似的输入的文档。 在某些错误情况下，则不返回任何输出。

<a name="return-value"></a>返回值
------------

返回标准的**HRESULT**值**S\_确定**来指示已成功。 下表显示了可能会返回额外的错误代码。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>返回代码</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top"><p><strong>CONFIG_E_OBJECTBUSY</strong></p></td>
<td style="vertical-align:top"><p>配置管理服务的其他实例当前正在运行。</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p><strong>CONFIG_E_ENTRYNOTFOUND</strong></p></td>
<td style="vertical-align:top"><p>找到没有配置数据库项。</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p><strong>CONFIG_E_CSPEXCEPTION</strong></p></td>
<td style="vertical-align:top"><p>配置服务提供程序之一中出现异常。</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p><strong>CONFIG_E_TRANSACTIONINGFAILURE</strong></p></td>
<td style="vertical-align:top"><p>配置服务提供程序未能正确回滚。 受影响的设置可能处于未知状态。</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p><strong>CONFIG_E_BAD_XML</strong></p></td>
<td style="vertical-align:top"><p>XML 输入是无效或格式不正确。</p></td>
</tr>
</tbody>
</table>

 

<a name="remarks"></a>备注
-------

XML 的处理是事务性的;整篇文档获取成功处理或处理的任何设置。 因此， **DMProcessConfigXMLFiltered**函数每次处理一个 XML 配置请求。

**DMProcessConfigXMLFiltered**的使用取决于所使用的配置服务提供程序。 例如，如果输入的.provxml 包含以下两个设置︰

``` XML
<wap-provisioningdoc>
    <characteristic type="NAPDEF">
        <characteristic type="Internet" mwid="1">
            <parm name="NAME" value="Contoso Internet APN"/>
            <parm name="BEARER" value="GSM-GPRS"/>
            <parm name="NAP-ADDRESS" value="wap.contoso"/>
            <parm name="NAP-ADDRTYPE" value="APN"/>
            <parm name="INTERNET" value="1"/>
        </characteristic>
    </characteristic>
    <characteristic type="BrowserFavorite">
        <characteristic type="Contoso">
            <parm name="URL" value="http://www.contoso.com"/>
        </characteristic>
    </characteristic>
</wap-provisioningdoc>
```

然后，对**DMProcessConfigXMLFiltered**的调用中的第二个参数必须具有下面的定义。

``` C++
LPCWSTR rgszAllowedCspNodes[] =
{
    L"NAPDEF",
    L"BrowserFavorite"
};
```

此配置服务提供程序名称的数组表示的.provxml 目录应存在。 如果 provxml 包含"电子邮件 2"资源调配，但*rgszAllowedCspNodes*不包含电子邮件 2，则**DMProcessConfigXMLFiltered**将失败，并**E\_ACCESSDENIED**错误代码。

下面的代码示例演示此数组中将传递的方式。 请注意， *szProvxmlContent*不显示为简洁起见的完整 XML 内容。 在实际的使用情况，"..."将包含如上所示的完整的 XML 字符串。

``` C++
WCHAR szProvxmlContent[] = L"<wap-provisioningdoc>...</wap-provisioningdoc>"; 
BSTR bstr = NULL;

HRESULT hr = DMProcessConfigXMLFiltered(
                szProvxmlContent,
                rgszAllowedCspNodes,
                _countof(rgszAllowedCspNodes),
                &bstr
                );

/* check error */

if ( bstr != NULL )
{
    SysFreeString( bstr );
    bstr = NULL;
}
```

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td style="vertical-align:top"><p>最低支持的客户端</p></td>
<td style="vertical-align:top"><p>无支持</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>最低支持的服务器</p></td>
<td style="vertical-align:top"><p>无支持</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>最小的支持的电话</p></td>
<td style="vertical-align:top"><p>Windows Phone 8.1</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>页眉</p></td>
<td style="vertical-align:top"><p>Dmprocessxmlfiltered.h</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>库</p></td>
<td style="vertical-align:top"><p>Dmprocessxmlfiltered.lib</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>DLL</p></td>
<td style="vertical-align:top"><p>Dmprocessxmlfiltered.dll</p></td>
</tr>
</tbody>
</table>

## <a name="see-also"></a>请参见

[**SysFreeString**](https://msdn.microsoft.com/library/windows/hardware/ms221481)

 






