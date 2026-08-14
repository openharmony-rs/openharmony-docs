# ColumnLayoutAlgorithm

垂直方向线性布局算法类。 > **说明：** > > ColumnLayoutAlgorithm类对象可以作为 > [DynamicLayout](../../../reference/apis-arkui/arkui-ts/ts-container-dynamiclayout.md)组件的入参指定布局算法。

**继承/实现关系：** ColumnLayoutAlgorithm implements [LayoutAlgorithm](arkts-na-layoutalgorithm-i.md#LayoutAlgorithm)

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-unnamed-export declare class ColumnLayoutAlgorithm--><!--Device-unnamed-export declare class ColumnLayoutAlgorithm-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(option?: ColumnLayoutAlgorithmOptions)
```

垂直方向线性布局算法类的构造函数。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-ColumnLayoutAlgorithm-constructor(option?: ColumnLayoutAlgorithmOptions)--><!--Device-ColumnLayoutAlgorithm-constructor(option?: ColumnLayoutAlgorithmOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| option | [ColumnLayoutAlgorithmOptions](arkts-na-layoutalgorithm-columnlayoutalgorithmoptions-i.md) | 否 | 垂直方向线性布局算法的构造入参， 设置布局算法的间距、主轴对齐方式、交叉轴对齐方式及主轴排列方向。 |

## alignItems

```TypeScript
@Trace public alignItems?: HorizontalAlign
```

所有子组件在水平方向上的对齐格式。 非法值：按默认值处理。

**类型：** [HorizontalAlign](arkts-na-enums-horizontalalign-e.md)

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-ColumnLayoutAlgorithm-@Trace public alignItems?: HorizontalAlign--><!--Device-ColumnLayoutAlgorithm-@Trace public alignItems?: HorizontalAlign-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isReverse

```TypeScript
@Trace public isReverse?: boolean
```

子组件在垂直方向上的排列是否反转。 取值为true表示子组件在垂直方向上反转排列。 取值为false表示子组件在垂直方向上正序排列。 非法值：按默认值处理。

**类型：** boolean

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-ColumnLayoutAlgorithm-@Trace public isReverse?: boolean--><!--Device-ColumnLayoutAlgorithm-@Trace public isReverse?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## justifyContent

```TypeScript
@Trace public justifyContent?: FlexAlign
```

所有子组件在垂直方向上的对齐格式。 非法值：按默认值处理。

**类型：** [FlexAlign](arkts-na-enums-flexalign-e.md)

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-ColumnLayoutAlgorithm-@Trace public justifyContent?: FlexAlign--><!--Device-ColumnLayoutAlgorithm-@Trace public justifyContent?: FlexAlign-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
@Trace public space?: LengthMetrics
```

纵向布局元素垂直方向间距。 非法值：按默认值处理。

**类型：** [LengthMetrics](arkts-na-graphics-lengthmetrics-c.md)

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-ColumnLayoutAlgorithm-@Trace public space?: LengthMetrics--><!--Device-ColumnLayoutAlgorithm-@Trace public space?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

