# <a name="chart-resource-type"></a>图表资源类型

表示工作簿中的图表对象。


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获取图表](../api/chart_get.md) | [图表](chart.md) |读取属性和关系的图表对象。|
|[创建 ChartSeries](../api/chart_post_series.md) |[ChartSeries](chartseries.md)| 由过账到系列集合中创建新的 ChartSeries。|
|[列表中系列](../api/chart_list_series.md) |[ChartSeries](chartseries.md)集合| 获得 ChartSeries 对象集合。|
|[更新](../api/chart_update.md) | [图表](chart.md)   |更新图表对象。 |
|[图像](../api/chart_image.md)|图像 base64 编码字符串|通过缩放图表以适合指定的尺寸为 base64 编码的图像呈现图表。|
|[删除](../api/chart_delete.md)|无|删除图表对象。|
|[Setdata](../api/chart_setdata.md)|无|重置该图表的源数据。|
|[Setposition](../api/chart_setposition.md)|无|相对于工作表上的单元格的位置的图表。|
|[列表](../api/chart_list.md) | [图表](chart.md)集合 |获取图表对象集合。 |
|[Itemat](../api/chartcollection_itemat.md)|[图表](chart.md)|获取图表根据其在集合中的位置。|
|[添加](../api/chartcollection_add.md)|[图表](chart.md)|创建新的图表。|

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|height|double|代表的高度，以磅为单位的图表对象。|
|id|string|获取图表根据其在集合中的位置。 只读的。|
|left|double|距离，以磅为单位，从工作表原点到图表的左侧。|
|name|string|表示图表对象的名称。|
|top|double|表示从顶部 （在工作表中） 的第 1 行或顶部的图表区域 （图表） 上对象的上边缘的距离，以磅为单位。|
|width|double|表示的宽度，以磅为单位的图表对象。|

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|axes|[ChartAxes](chartaxes.md)|表示图表轴。 只读的。|
|数据标签|[ChartDataLabels](chartdatalabels.md)|表示图表上的数据标签。 只读的。|
|格式|[ChartAreaFormat](chartareaformat.md)|封装的图表区域的格式属性。 只读的。|
|图例|[ChartLegend](chartlegend.md)|表示图表的图例。 只读的。|
|series|[ChartSeries](chartseries.md)集合|表示单个数据系列或图表中系列的集合。 只读的。|
|title|[ChartTitle](charttitle.md)|代表指定的图表，包括文本、 可见性、 位置和格式的标题的标题。 只读的。|
|worksheet|[工作表](worksheet.md)|包含当前图表的工作表。 只读的。|

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.chart"
}-->

```json
{
  "height": 1024,
  "id": "string",
  "left": 1024,
  "name": "string",
  "top": 1024,
  "width": 1024
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Chart resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->