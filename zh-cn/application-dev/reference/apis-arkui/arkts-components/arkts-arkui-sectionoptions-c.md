# SectionOptions

FlowItem分组配置信息。

**起始版本：** 12

<!--Device-unnamed-declare class SectionOptions--><!--Device-unnamed-declare class SectionOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## columnsGap

```TypeScript
columnsGap?: Dimension
```

该分组的列间距，不设置该参数时默认使用瀑布流的columnsGap，设置非法值时使用0vp。

**类型：** Dimension

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SectionOptions-columnsGap?: Dimension--><!--Device-SectionOptions-columnsGap?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## crossCount

```TypeScript
crossCount?: number
```

纵向布局时为列数，横向布局时为行数。

默认值：**1**

小于1的按默认值处理。

**类型：** number

**默认值：** 1 one column in vertical layout, or one row in horizontal layout

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SectionOptions-crossCount?: number--><!--Device-SectionOptions-crossCount?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemsCount

```TypeScript
itemsCount: number
```

分组中FlowItem数量，必须是非负数。若splice、push、update方法收到的分组中有分组的itemsCount小于0，则不会执行该方法。避免使用itemsCount为0的分组，这可能导致布局计算异常。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SectionOptions-itemsCount: number--><!--Device-SectionOptions-itemsCount: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## margin

```TypeScript
margin?: Margin | Dimension
```

该分组的外边距参数为Length类型时，四个方向外边距同时生效。

默认值：**0**

单位：vp

margin设置百分比时，上下左右外边距均以瀑布流的width作为基础值。

**类型：** Margin \| Dimension

**默认值：** {top: 0, right: 0, bottom: 0, left: 0}

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SectionOptions-margin?: Margin | Dimension--><!--Device-SectionOptions-margin?: Margin | Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onGetItemMainSizeByIndex

```TypeScript
onGetItemMainSizeByIndex?: GetItemMainSizeByIndex
```

瀑布流组件布局过程中获取指定index的FlowItem的主轴大小，纵向瀑布流时为高度，横向瀑布流时为宽度，单位vp。

<p><strong>说明</strong><br>1. 同时使用onGetItemMainSizeByIndex和FlowItem的宽高属性时，主轴大小以onGetItemMainSizeByIndex返回结果为准，onGetItemMainSizeByIndex会覆盖FlowItem的主轴长度。<br>2. 使用onGetItemMainSizeByIndex可以提高瀑布流跳转到指定位置或index时的效率，避免混用设置onGetItemMainSizeByIndex和未设置的分组，会导致布局异常。<br>3. onGetItemMainSizeByIndex返回负数时FlowItem高度为0。</p>

**类型：** GetItemMainSizeByIndex

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SectionOptions-onGetItemMainSizeByIndex?: GetItemMainSizeByIndex--><!--Device-SectionOptions-onGetItemMainSizeByIndex?: GetItemMainSizeByIndex-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## rowsGap

```TypeScript
rowsGap?: Dimension
```

该分组的行间距，不设置该参数时默认使用瀑布流的rowsGap，设置非法值时使用0vp。

**类型：** Dimension

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SectionOptions-rowsGap?: Dimension--><!--Device-SectionOptions-rowsGap?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

