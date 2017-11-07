---
title: IControlManager
description: IControlManager
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 4c6d4a0b-5a66-4fcc-ad8a-69c68a7e7fcc
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 6510c4d68929662bad4eec1965d147017b5175d4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="icontrolmanager"></a>IControlManager


表示 Windows 性能记录器管理器，用于控制跟踪 Windows 事件 (ETW) 会话。 客户端通过使用[IProfileCollection](iprofilecollection.md)接口的配置文件的集合和经理可以启动、 更新、 取消、 保存、 停止或查询 ETW 会话或提供程序的每个配置文件的描述。 客户端可以一个指针传递给[IControlProgressHandler](icontrolprogresshandler.md)处理程序来接收更新管理器执行的操作有关。

## <a name="syntax"></a>语法


``` syntax
{
  [propget, id(1), helpstring("property ControlProgressHandler")] HRESULT ControlProgressHandler
    ([out, retval] IControlProgressHandler** ppControlProgressHandler);
  [propput, id(1), helpstring("property ControlProgressHandler")] HRESULT ControlProgressHandler
    ([in] IControlProgressHandler* pControlProgressHandler);
  [id(2), helpstring("Start")] HRESULT Start
    ([in] IProfileCollection* pProfileCollection);
  [id(3), helpstring("Update")] HRESULT Update
    ([in] IProfileCollection* pProfileCollection);
  [id(4), helpstring("Cancel")] HRESULT Cancel
    ([in] IProfileCollection* pProfileCollection);
  [id(5), helpstring("Save")] HRESULT Save
    ([in] BSTR bstrFileName,
    [in] IProfileCollection* pProfileCollection,
    [in] ITraceMergeProperties* pTraceMergeProperties);
  [id(6), helpstring("Stop")] HRESULT Stop
    ([in] BSTR bstrFileName,
    [in] IProfileCollection* pProfileCollection,
    [in] ITraceMergeProperties* pTraceMergeProperties);
  [id(7), helpstring("QueryXML")] HRESULT QueryXML
    ([out] BSTR* pbstrResults,
    [in] VARIANT_BOOL fValidateRuntimeState);
  [id(8), helpstring("Query")] HRESULT Query
    ([out] IProfileCollection** ppProfileCollection,
    [in] VARIANT_BOOL fValidateRuntimeState);
  [propget, id(9), helpstring("property TraceMergeTextHandler")] HRESULT TraceMergeTextHandler
    ([out, retval] ITraceMergeTextHandler** ppTraceMergeTextHandler);
  [propput, id(9), helpstring("property TraceMergeTextHandler")] HRESULT TraceMergeTextHandler
    ([in] ITraceMergeTextHandler* pTraceMergeTextHandler);
  [propget, id(10), helpstring("property TemporaryTraceDirectory")] HRESULT TemporaryTraceDirectory
    ([out, retval] BSTR* pbstrTemporaryTraceDirectory);
  [propput, id(10), helpstring("property TemporaryTraceDirectory")] HRESULT TemporaryTraceDirectory
    ([in] BSTR bstrTemporaryTraceDirectory);
  [id(11), helpstring("GetProviderNameFromGuid")] HRESULT GetProviderNameFromGuid
    ([out] BSTR* bstrProviderIdStr,
    [in] REFGUID ProviderId);
  [id(12), helpstring("GetProviderGuidFromName")] HRESULT GetProviderGuidFromName
    ([out] GUID* ProviderId,
    [in] BSTR bstrProViderName);
};
```

## <a name="functions"></a>函数


下表描述了此接口提供的功能。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>函数</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[启动](start-icontrolmanager.md)</p></td>
<td><p>开始录制。</p></td>
</tr>
<tr class="even">
<td><p>[更新](update-icontrolmanager.md)</p></td>
<td><p>更新配置文件集合。</p></td>
</tr>
<tr class="odd">
<td><p>[取消](cancel.md)</p></td>
<td><p>停止录制，但不保存任何数据。</p></td>
</tr>
<tr class="even">
<td><p>[保存](save-icontrolmanager.md)</p></td>
<td><p>保存录制登录到指定的事件跟踪日志 (ETL) 文件到内存中的循环缓冲区。</p></td>
</tr>
<tr class="odd">
<td><p>[停止](stop-icontrolmanager.md)</p></td>
<td><p>停止录制，并将其保存到指定的事件跟踪日志 (ETL) 文件。</p></td>
</tr>
<tr class="even">
<td><p>[QueryXML](queryxml.md)</p></td>
<td><p>指示当前正在运行的配置文件和配置文件是否正确运行的 XML 格式。</p></td>
</tr>
<tr class="odd">
<td><p>[查询](query-icontrolmanager.md)</p></td>
<td><p>查询会话和所有配置文件中的提供程序的属性。</p></td>
</tr>
<tr class="even">
<td><p><strong>propget</strong></p></td>
<td><p>获取指定的属性。</p></td>
</tr>
<tr class="odd">
<td><p><strong>propput</strong></p></td>
<td><p>设置指定的属性。</p></td>
</tr>
<tr class="even">
<td><p>[GetProviderNameFromGuid](getprovidernamefromguid.md)</p></td>
<td><p>获取指定的提供程序名称。</p></td>
</tr>
<tr class="odd">
<td><p>[GetProviderGuidFromName](getproviderguidfromname.md)</p></td>
<td><p>获取提供程序的指定名称的 GUID。</p></td>
</tr>
</tbody>
</table>

 

## <a name="properties"></a>属性


下表描述了此接口可以获取或设置的属性的参数。

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>属性</th>
<th>参数</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>ControlProgressHandler</strong></p></td>
<td><p><em>ppControlProgressHandler</em> [out]</p></td>
<td><p>客户端实现[IControlProgressHandler](icontrolprogresshandler.md)接口的指针。</p></td>
</tr>
<tr class="even">
<td><p><strong>ControlProgressHandler</strong></p></td>
<td><p><em>pControlProgressHandler</em> [in]</p></td>
<td><p>客户端实现<strong>IControlProgressHandler</strong>接口的指针。 E_POINTER 表示无效的指针。</p></td>
</tr>
<tr class="odd">
<td><p><strong>TraceMergeTextHandler</strong></p></td>
<td><p><em>ppTraceMergeTextHandler</em> [out]</p></td>
<td><p>指针，指向文本和一些其他合并时间信息，通过[ITraceMergeTextHandler](itracemergetexthandler.md)接口插入跟踪中。</p></td>
</tr>
<tr class="even">
<td><p><strong>TraceMergeTextHandler</strong></p></td>
<td><p><em>pTraceMergeTextHandler</em> [in]</p></td>
<td><p>指针，指向文本和一些其他合并时间信息，通过<strong>ITraceMergeTextHandler</strong>接口插入跟踪中。 E_POINTER 表示无效的指针。</p></td>
</tr>
<tr class="odd">
<td><p><strong>TemporaryTraceDirectory</strong></p></td>
<td><p><em>pbstrTemporaryTraceDirectory</em> [out]</p></td>
<td><p>其中记录了预合并的跟踪文件的目录的路径的指针。 默认值为 %temp%文件夹。</p></td>
</tr>
<tr class="even">
<td><p><strong>TemporaryTraceDirectory</strong> [in]</p></td>
<td><p><em>bstrTemporaryTraceDirectory</em></p></td>
<td><p>其中记录了预合并的跟踪文件的目录的路径。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[接口](interfaces-wprcontrol.md)

 

 







