# StackLayoutAlgorithm

堆叠布局算法类。
> **说明：**  
>  
> StackLayoutAlgorithm类对象可以赋值给LayoutAlgorithm类型变量，作为[DynamicLayout](arkts-arkui-components-arkdynamiclayout.md)组件的  
> 入参指定布局算法。

**继承/实现关系：** StackLayoutAlgorithm implements [LayoutAlgorithm](arkts-arkui-layoutalgorithm-i.md)

**起始版本：** 24

**装饰器类型：** @ObservedV2

<!--Device-unnamed-export class StackLayoutAlgorithm implements LayoutAlgorithm--><!--Device-unnamed-export class StackLayoutAlgorithm implements LayoutAlgorithm-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(option?: StackLayoutAlgorithmOptions)
```

堆叠布局算法类的构造函数。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本24开始，该接口支持在ArkTS卡片中使用。

<!--Device-StackLayoutAlgorithm-constructor(option?: StackLayoutAlgorithmOptions)--><!--Device-StackLayoutAlgorithm-constructor(option?: StackLayoutAlgorithmOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| option | [StackLayoutAlgorithmOptions](arkts-arkui-layoutalgorithm-stacklayoutalgorithmoptions-i.md) | 否 | 堆叠布局算法的构造入参，设置九宫格对齐格式。 |

## alignContent

```TypeScript
@Trace public alignContent?: LocalizedAlignment
```

设置子组件在堆叠布局算法中对齐格式。

默认值：LocalizedAlignment.CENTER

非法值：按默认值处理。

装饰器类型：@Trace

**类型：** LocalizedAlignment

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本24开始，该接口支持在ArkTS卡片中使用。

<!--Device-StackLayoutAlgorithm-@Trace public alignContent?: LocalizedAlignment--><!--Device-StackLayoutAlgorithm-@Trace public alignContent?: LocalizedAlignment-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

