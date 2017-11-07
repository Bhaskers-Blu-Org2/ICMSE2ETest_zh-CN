# <a name="policy-resource-type"></a>策略资源类型

表示一个 Azure 的广告策略。 策略是可以在应用程序、 服务主体、 组或整个组织分配给他们的强制执行的自定义规则。 目前只有一种类型的策略可用︰
- 令牌的生存期策略︰ 指定的应用程序和服务主体所颁发的令牌的生存期

进一步下面将详细介绍这项策略。

### <a name="methods"></a>方法
| 方法       | 返回类型  |说明|
|:---------------|:--------|:----------|
| [获取策略](../api/policy_get.md) |策略|读取属性和用户对象的关系。|
|[创建策略](../api/policy_post.md)|策略|创建新的策略对象。|
|[更新策略](../api/policy_update.md)|无|更新策略对象。|
|[删除策略](../api/policy_delete.md)|无|删除策略对象。|
|[分配策略](../api/policy_assign.md)|无|将策略分配到应用程序，服务主体。|
|[列表策略](../api/policy_list.md)|策略集合|在组织中得到的所有策略对象。|
|[列表分配策略](../api/policy_list_assigned.md)|策略集合|获取分配给应用程序或服务主体的所有策略对象。|


### <a name="common-properties"></a>公共属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|定义|String|字符串版本的特定策略。 请参见下文。 必需。|
|显示名称|String|自定义策略的名称。 必需。|
|IsOrganizationDefault|Boolean|如果设置为 true 时，将激活此策略。 可以有多个策略相同的策略类型，但只有一个可以被激活为默认组织。 可选的默认值为 false。|
|类型|String|指定的策略的类型。 目前必须是"TokenLifetimePolicy"。 必需。|

#### <a name="common-relationships"></a>公共关系
|关系|类型|说明|
|:-------------|:-----------|:-----------|
|格值|[directoryObject](../resources/directoryObject.md)集合|应用程序、 服务主体、 组或组织应用该策略。|

## <a name="token-lifetime-policy"></a>令牌的生命周期策略
指定用于各种目的所颁发的令牌的生存期。 这种策略可以对应用程序和服务的原则[分配](../api/policy_assign.md)。 有四种类型的令牌可以配置其生存期。 而在通过浏览器身份验证期间获得 ID/会话令牌对在客户端通过身份验证过程都获得了访问/刷新令牌对。

- **访问令牌**包含有关标识和与客户端用于访问受保护的资源与应用程序相同的用户帐户关联的权限的信息。
- **刷新令牌**获取和访问令牌当通过客户端来访问受保护的资源的 Azure 广告对用户进行身份验证。 虽然它不是废除或留给未使用多个 MaxInactiveTime （见下文），可用于获取新的访问/刷新令牌对当前存取令牌过期时。
- **ID 标记**的行为方式类似的访问令牌，但通过浏览器获得。
- **会话令牌**的行为像一个刷新令牌，但获得通过浏览器。

#### <a name="properties"></a>属性
下列属性窗体表示令牌的生存期策略的 JSON 对象。 此 JSON 对象必须**转换为带引号转义字符串**插入到"定义"公共策略属性。 下面显示了一个示例。

>注意︰ 所有这些属性中的持续时间中"dd.hh:mm:ss"的格式指定。

>注意︰ 属性，以"天"的最大值是表示天数达到 1 秒。 例如，1 天的最大值被指定为"23: 59:59"。

| 属性     | 类型   |说明| 最小值 | 最大值 | 默认值|
|:---------------|:--------|:----------|:--------|:--------|:----|
|AccessTokenLifetime|String|控制多长时间**访问和 ID 标记**被视为有效。|10 分钟|1 天|1 小时|
|MaxInactiveTime|String|控制多久刷新令牌可以之前客户端不再可用来检索一个新的访问/刷新令牌对访问资源。|10 分钟|90 天|14 天|
|MaxAgeSingleFactor|String|控制用户可以继续使用刷新令牌来获取新的访问刷新令牌对上次他们通过身份验证之后成功单因子。 由于单因素被看作比多因素身份验证的安全性较低，建议该策略被设置为比 MultiFactorRefreshTokenMaxAge 相同或更低的值。|10 分钟|直到被吊销|365 天或直到吊销|
|MaxAgeMultiFactor|String|控制用户可以继续使用刷新令牌来获取新的访问刷新令牌对上次他们通过身份验证之后成功地与多因素。|10 分钟|直到被吊销|365 天或直到吊销|
|MaxAgeSessionSingleFactor|String|控制用户可以继续使用会话令牌来获取新的会话 ID/标记上次他们通过身份验证后成功单因子。 由于单因素被看作比多因素身份验证的安全性较低，建议该策略被设置为比 MultiFactorSessionTokenMaxAge 相同或更低的值|10 分钟|直到被吊销|365 或直至吊销|
|MaxAgeSessionMultiFactor|String|控制用户可以继续使用会话令牌之后最后一次成功的多因素验证获取新的会话 ID/标记。|10 分钟|直到被吊销|365 或直至吊销|
|版本|Integer|设置值为 1。 必需。|无|无|无|

### <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

```json
{
  "definition":["{\"TokenLifetimePolicy\":{\"Version\":1,\"AccessTokenLifetime\":\"8:00:00\",\"MaxInactiveTime\":\"20:00:00\",}}"],
  "displayName":"Test Policy",
  "isOrganizationDefault":false,
  "type":"TokenLifetimePolicy",
}
```
