# RowLayoutAlgorithm

水平方向线性布局算法类。 > **说明：** > > RowLayoutAlgorithm类对象可以作为 > [DynamicLayout](../../../reference/apis-arkui/arkui-ts/ts-container-dynamiclayout.md)组件的入参指定布局算法。

**继承/实现关系：** RowLayoutAlgorithm implements [LayoutAlgorithm](arkts-na-layoutalgorithm-i.md#LayoutAlgorithm)

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-unnamed-export declare class RowLayoutAlgorithm--><!--Device-unnamed-export declare class RowLayoutAlgorithm-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(option?: RowLayoutAlgorithmOptions)
```

水平方向线性布局算法类的构造函数。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-RowLayoutAlgorithm-constructor(option?: RowLayoutAlgorithmOptions)--><!--Device-RowLayoutAlgorithm-constructor(option?: RowLayoutAlgorithmOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| option | [RowLayoutAlgorithmOptions](arkts-na-layoutalgorithm-rowlayoutalgorithmoptions-i.md) | 否 | 水平方向线性布局算法的构造入参， 设置布局算法的间距、主轴对齐方式、交叉轴对齐方式及主轴排列方向。 |

## alignItems

```TypeScript
@Trace public alignItems?: VerticalAlign
```

所有子组件在垂直方向上的对齐格式。 非法值：按默认值处理。

**类型：** [VerticalAlign](arkts-na-enums-verticalalign-e.md)

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-RowLayoutAlgorithm-@Trace public alignItems?: VerticalAlign--><!--Device-RowLayoutAlgorithm-@Trace public alignItems?: VerticalAlign-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isReverse

```TypeScript
@Trace public isReverse?: boolean
```

子组件在水平方向上的排列是否反转。 取值为true表示子组件在水平方向上反转排列， 由于水平方向受通用属性 [direction](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-location.md#direction)影响， 如果[direction](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-location.md#direction)属性生效， 再做一次反转。 取值为false表示子组件在水平方向上正序排列。 非法值：按默认值处理。

**类型：** boolean

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-RowLayoutAlgorithm-@Trace public isReverse?: boolean--><!--Device-RowLayoutAlgorithm-@Trace public isReverse?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## justifyContent

```TypeScript
@Trace public justifyContent?: FlexAlign
```

所有子组件在水平方向上的对齐格式。 非法值：按默认值处理。

**类型：** [FlexAlign](arkts-na-enums-flexalign-e.md)

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-RowLayoutAlgorithm-@Trace public justifyContent?: FlexAlign--><!--Device-RowLayoutAlgorithm-@Trace public justifyContent?: FlexAlign-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
@Trace public space?: LengthMetrics
```

横向布局元素水平方向间距。 非法值：按默认值处理。

**类型：** [LengthMetrics](arkts-na-graphics-lengthmetrics-c.md)

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-RowLayoutAlgorithm-@Trace public space?: LengthMetrics--><!--Device-RowLayoutAlgorithm-@Trace public space?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

