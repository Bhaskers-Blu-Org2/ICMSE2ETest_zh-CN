# <a name="datetimetimezone-resource-type"></a>dateTimeTimeZone 资源类型

介绍在时间的日期、 时间和时区的一个点。

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|DateTime|String|时间组合的日期和时间表示形式的单一 (`<date>T<time>`)。|
|时区|String|以下时区名称之一。|


_时区_属性可以设置为任何支持的窗口，以及以下时区名称的时区。

等/GMT + 12

等/GMT + 11

太平洋/Honolulu

美国 Anchorage /

美国/Santa_Isabel

美国/Los_Angeles

美国/菲尼克斯

美国/Chihuahua

美国/丹佛

美国/危地马拉

美国/芝加哥

美国/标准

美国/里贾纳

美国/波哥大

美国/New_York

美国/印地安那州/Indianapolis

美国/加拉加斯

美国/亚松

美国/哈利法克斯

美国/Cuiaba

美国/La_Paz

美国/圣地亚哥

美国/St_Johns

美国/Sao_Paulo

美国/阿根廷/Buenos_Aires

美国/卡宴

美国/戈特霍布

美国/蒙得维的亚

美国/巴伊亚

等/格林威治标准时间 + 2

大西洋/亚速尔群岛

大西洋/Cape_Verde

非洲/卡萨布兰卡

格林威治标准时间等 /

欧洲/伦敦

大西洋/雷克雅未克

欧洲/柏林

欧洲/布达佩斯

欧洲/巴黎

欧洲/华沙

非洲/Lagos

非洲/Windhoek

欧洲/布加勒斯特

亚洲/贝鲁特

非洲/开罗

亚洲/大马士革

非洲/约翰内斯堡

欧洲/基辅

欧洲/伊斯坦布尔

亚洲/耶路撒冷

亚洲/Amman

亚洲/巴格达

欧洲/加里宁格勒

亚洲/利雅得

非洲/内罗毕

亚洲/德黑兰

亚洲/迪拜

亚洲/巴库

欧洲/莫斯科

毛里求斯印度洋 /

亚洲/第比利斯

亚洲/埃里温

亚洲/喀布尔

亚洲/卡拉奇

亚洲/塔什干

亚洲/Kolkata

亚洲/科伦坡

亚洲/加德满都

亚洲/阿拉木图

亚洲/达卡

亚洲/Yekaterinburg

亚洲/Rangoon

亚洲/曼谷

亚洲/新西伯利亚

亚洲/上海

亚洲/Krasnoyarsk

亚洲/新加坡

佩思澳大利亚 /

亚洲/台北

亚洲/乌兰巴托

亚洲/伊尔库茨克

亚洲/东京

亚洲/首尔

阿德莱德澳大利亚 /

达尔文澳大利亚 /

澳大利亚布里斯班 /

澳大利亚/悉尼

莫尔斯比港太平洋 /

澳大利亚霍巴特 /

亚洲/雅库茨克

太平洋/瓜达康纳尔岛

亚洲/符拉迪沃斯托克 （海参崴)

太平洋/奥克兰

等格林尼治标准时间-12

斐济太平洋 /

马加丹亚 /

太平洋/汤加塔布

太平洋/阿皮亚

太平洋/Kiritimati

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.dateTimeTimeZone"
}-->

```json
{
  "dateTime": "string",
  "timeZone": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "dateTimeTimeZone resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
