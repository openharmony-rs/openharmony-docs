# SectionOptions

FlowItem分组配置信息。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## onGetItemMainSizeByIndex

```TypeScript
onGetItemMainSizeByIndex?: GetItemMainSizeByIndex
```

瀑布流组件布局过程中获取指定index的FlowItem的主轴大小，纵向瀑布流时为高度，横向瀑布流时为宽度，单位vp。不设置时，瀑布流按FlowItem的常规测量结果确定主轴大小。  
**说明：**
1. 同时使用onGetItemMainSizeByIndex和FlowItem的宽高属性时，主轴大小以onGetItemMainSizeByIndex返回结果为准，onGetItemMainSizeByIndex会覆盖FlowItem的主轴长度。
2. 使用onGetItemMainSizeByIndex可以提高瀑布流跳转到指定位置或index时的效率，避免混用设置onGetItemMainSizeByIndex和未设置的分组，否则会导致布局异常。
3. onGetItemMainSizeByIndex返回负数时，FlowItem主轴大小为0。
4. 如果FlowItem主轴大小会随数据动态变化，应保证onGetItemMainSizeByIndex返回值与数据源保持一致。使用[LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)时，数据变化后应调用onDataChange、[onDataReloaded](arkts-arkui-datachangelistener-i.md#ondatareloaded)或[onDatasetChange](arkts-arkui-datachangelistener-i.md#ondatasetchange)等方法通知框架数据已变化；使用[Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)时，应按Repeat的数据更新规则修改状态数组。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## columnsGap

```TypeScript
columnsGap?: Dimension
```

该分组的列间距，不设置该参数时默认使用瀑布流的[columnsGap](arkts-arkui-waterflow-attribute.md#columnsgap)，设置非法值时使用0vp。

**类型：** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## crossCount

```TypeScript
crossCount?: number
```

纵向布局时为列数，横向布局时为行数，默认值：1。小于1的按默认值处理。

**类型：** number

**默认值：** 1 one column in vertical layout, or one row in horizontal layout

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemsCount

```TypeScript
itemsCount: number
```

分组中FlowItem数量，必须是非负数。若splice、push、update方法收到的分组中有分组的itemsCount小于0，则该方法不会生效（返回false）。避免使用itemsCount为0的分组，否则可能导致布局计算异 常。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## margin

```TypeScript
margin?: Margin | Dimension
```

该分组的外边距参数为Length类型时，四个方向外边距同时生效。默认值：0单位：vp margin设置百分比时，上下左右外边距均以瀑布流的width作为基础值。

**类型：** [Margin](../arkts-apis/arkts-arkui-margin-t.md) \| [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**默认值：** {top: 0, right: 0, bottom: 0, left: 0}

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## rowsGap

```TypeScript
rowsGap?: Dimension
```

该分组的行间距，不设置该参数时默认使用瀑布流的[rowsGap](arkts-arkui-waterflow-attribute.md#rowsgap)，设置非法值时使用0vp。

**类型：** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
