# RowLayoutAlgorithm

水平方向线性布局算法类。

> **说明：**  
>  
> RowLayoutAlgorithm类对象可以赋值给LayoutAlgorithm类型变量，作为[DynamicLayout](arkts-arkui-components-arkdynamiclayout.md)组件的入参  
> 指定布局算法。

**继承/实现关系：** RowLayoutAlgorithm implements [LayoutAlgorithm](arkts-arkui-layoutalgorithm-i.md)

**起始版本：** 24

**装饰器类型：** @ObservedV2

<!--Device-unnamed-export class RowLayoutAlgorithm implements LayoutAlgorithm--><!--Device-unnamed-export class RowLayoutAlgorithm implements LayoutAlgorithm-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="constructor"></a>
## constructor

```TypeScript
constructor(option?: RowLayoutAlgorithmOptions)
```

水平方向线性布局算法类的构造函数。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本24开始，该接口支持在ArkTS卡片中使用。

<!--Device-RowLayoutAlgorithm-constructor(option?: RowLayoutAlgorithmOptions)--><!--Device-RowLayoutAlgorithm-constructor(option?: RowLayoutAlgorithmOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| option | [RowLayoutAlgorithmOptions](arkts-arkui-layoutalgorithm-rowlayoutalgorithmoptions-i.md) | 否 | 水平方向线性布局算法的构造入参，设置布局算法的间距、主轴对齐方式、交叉轴对齐方式及主轴排列方向。 |

## alignItems

```TypeScript
@Trace public alignItems?: VerticalAlign
```

所有子组件在垂直方向上的对齐格式。

默认值：VerticalAlign.Center

非法值：按默认值处理。

装饰器类型：@Trace

**类型：** VerticalAlign

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本24开始，该接口支持在ArkTS卡片中使用。

<!--Device-RowLayoutAlgorithm-@Trace public alignItems?: VerticalAlign--><!--Device-RowLayoutAlgorithm-@Trace public alignItems?: VerticalAlign-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isReverse

```TypeScript
@Trace public isReverse?: boolean
```

子组件在水平方向上的排列是否反转。取值为true表示子组件在水平方向上反转排列，由于水平方向受通用属性[direction](../arkts-components/arkts-arkui-commonmethod-c.md#direction-1)影响，如果[direction](../arkts-components/arkts-arkui-commonmethod-c.md#direction-1)属性生效，再做一次反转。取值为false表示子组件在水平方向上正序排列。

默认值：false

非法值：按默认值处理。

装饰器类型：@Trace

**类型：** boolean

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本24开始，该接口支持在ArkTS卡片中使用。

<!--Device-RowLayoutAlgorithm-@Trace public isReverse?: boolean--><!--Device-RowLayoutAlgorithm-@Trace public isReverse?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## justifyContent

```TypeScript
@Trace public justifyContent?: FlexAlign
```

所有子组件在水平方向上的对齐格式。

默认值：FlexAlign.Start

非法值：按默认值处理。

装饰器类型：@Trace

**类型：** FlexAlign

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本24开始，该接口支持在ArkTS卡片中使用。

<!--Device-RowLayoutAlgorithm-@Trace public justifyContent?: FlexAlign--><!--Device-RowLayoutAlgorithm-@Trace public justifyContent?: FlexAlign-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
@Trace public space?: LengthMetrics
```

横向布局元素水平方向间距。

默认值：LengthMetrics.vp(0)

非法值：按默认值处理。

装饰器类型：@Trace

**类型：** LengthMetrics

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本24开始，该接口支持在ArkTS卡片中使用。

<!--Device-RowLayoutAlgorithm-@Trace public space?: LengthMetrics--><!--Device-RowLayoutAlgorithm-@Trace public space?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

