---
title: IConfigServiceProvider2 ConfigManagerNotification
description: IConfigServiceProvider2 ConfigManagerNotification
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: b1f0fe0f-afbe-4b36-a75d-34239a86a75c
ms.openlocfilehash: deff995252c8779d08fcead630d4e3847d74f4bb
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="iconfigserviceprovider2configmanagernotification"></a>IConfigServiceProvider2::ConfigManagerNotification


此方法允许将事件通知发送到配置服务提供程序，如加载或卸载配置服务提供程序时，执行回滚时，和在节点上调用操作时的 ConfigManager2。

## <a name="syntax"></a>语法


``` syntax
HRESULT ConfigManagerNotification([in] CFGMGR_NOTIFICATION cmnfyState, 
                                  [in] LPARAM lpParam);
```

## <a name="parameters"></a>参数


<a href="" id="cmnfystate"></a>*cmnfyState*
<ul style="list-style-type:none">
<li>
所有配置服务提供程序都支持以下事件。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>事件</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CFGMGR_NOTIFICATION_LOAD</p></td>
<td><p>第一次配置服务提供程序加载/实例化。</p></td>
</tr>
<tr class="even">
<td><p>CFGMGR_NOTIFICATION_BEGINCOMMANDPROCESSING</p></td>
<td><p>要运行第一个命令的事务。</p></td>
</tr>
<tr class="odd">
<td><p>CFGMGR_NOTIFICATION_ENDCOMMANDPROCESSING</p></td>
<td><p>执行交易记录的最后一个命令。 如果始终引发此事件<code>BEGINCOMMANDPROCESSING</code>所引发，即使处理<code>BEGINCOMMANDPROCESSING</code>失败。</p></td>
</tr>
<tr class="even">
<td><p>CFGMGR_NOTIFICATION_BEGINCOMMIT</p></td>
<td><p>将要提交事务处理的第一个命令。</p></td>
</tr>
<tr class="odd">
<td><p>CFGMGR_NOTIFICATION_ENDCOMMIT</p></td>
<td><p>已提交事务的最后一个命令。 如果始终引发此事件<code>BEGINCOMMIT</code>所引发，即使处理<code>BEGINCOMMIT</code>失败。</p></td>
</tr>
<tr class="even">
<td><p>CFGMGR_NOTIFICATION_BEGINROLLBACK</p></td>
<td><p>要回滚的事务的第一个命令。</p></td>
</tr>
<tr class="odd">
<td><p>CFGMGR_NOTIFICATION_ENDROLLBACK</p></td>
<td><p>已回滚的事务的最后一个命令。 如果始终引发此事件<code>BEGINROLLBACK</code>所引发，即使处理<code>BEGINROLLBACK</code>失败。</p></td>
</tr>
<tr class="even">
<td><p>CFGMGR_NOTIFICATION_UNLOAD</p></td>
<td><p>配置服务提供程序将被卸载删除。</p></td>
</tr>
<tr class="odd">
<td><p>CFGMGR_NOTIFICATION_SETSESSIONOBJ</p></td>
<td><p>会话对象是可供使用;<em>lpParam</em>可以为 IConfigSession2 指针强制转换。</p></td>
</tr>
<tr class="even">
<td><p>CFGMGR_NOTIFICATION_BEGINTRANSACTIONING</p></td>
<td><p>主要用于与 v1 配置服务提供程序的兼容性。 用信号通知事务序列的开头。</p></td>
</tr>
<tr class="odd">
<td><p>CFGMGR_NOTIFICATION_ENDTRANSACTIONING</p></td>
<td><p>主要用于与 v1 配置服务提供程序的兼容性。 表示事务序列的结束。</p></td>
</tr>
</tbody>
</table>
</li>
</ul>
<br>


<a href="" id="lpparam"></a>*lpParam*
<ul style="list-style-type:none">
<li>
正常情况下为 NULL，但包含一个 IConfigSession2 实例的指针，如果*cmnfState* CFGMGR\_通知\_SETSESSIONOBJ。
</li>
</ul>
<br>

## <a name="return-value"></a>返回值

S 的值\_确定表示成功。

## <a name="remarks"></a>备注

ConfigManager2 保证如果引发该事件开始的事件之一

-   CFGMGR\_通知\_BEGINCOMMANDPROCESSING
-   CFGMGR\_通知\_BEGINCOMMIT
-   CFGMGR\_通知\_BEGINROLLBACK

然后相应的结束事件将引发，即使开始通知的处理失败。
对于每个交易记录，通知的顺序是︰

1.  BEGINCOMMANDPROCESSING

2.  BEGINTRANSACTIONING

3.  ENDTRANSACTIONING

4.  ENDCOMMANDPROCESSING

5.  BEGINCOMMIT 或 BEGINROLLBACK，具体取决于该交易记录是成功还是失败。

6.  ENDCOMMIT 或 ENDROLLBACK，具体取决于该交易记录是成功还是失败。

每个配置服务提供程序将接收相关 BEGIN/END 通知一次，每个 ConfigManager2 执行每个事务。

## <a name="requirements"></a>要求

**标头︰**无

 






