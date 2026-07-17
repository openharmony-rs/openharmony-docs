# GridLayoutAlgorithm

网格布局算法类。

> **说明：**  
>  
> GridLayoutAlgorithm类对象可以赋值给LayoutAlgorithm类型变量，作为[DynamicLayout](arkts-arkui-components-arkdynamiclayout.md)组件的入  
> 参指定布局算法。

**继承/实现关系：** GridLayoutAlgorithm implements [LayoutAlgorithm](arkts-arkui-layoutalgorithm-i.md)

**起始版本：** 24

<!--Device-unnamed-export class GridLayoutAlgorithm implements LayoutAlgorithm--><!--Device-unnamed-export class GridLayoutAlgorithm implements LayoutAlgorithm-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(option?: GridLayoutAlgorithmOptions)
```

网格布局算法类的构造函数。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-GridLayoutAlgorithm-constructor(option?: GridLayoutAlgorithmOptions)--><!--Device-GridLayoutAlgorithm-constructor(option?: GridLayoutAlgorithmOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| option | [GridLayoutAlgorithmOptions](arkts-arkui-layoutalgorithm-gridlayoutalgorithmoptions-i.md) | 否 | 网格布局算法的构造入参，设置网格布局的列数、列间距、行间距。 |

## columnsGap

```TypeScript
@Trace public columnsGap?: LengthMetrics
```

列与列之间的间距。

默认值：LengthMetrics.vp(0)

非法值：按默认值处理。

装饰器类型：@Trace

**类型：** LengthMetrics

**默认值：** LengthMetrics.vp(0)

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-GridLayoutAlgorithm-@Trace public columnsGap?: LengthMetrics--><!--Device-GridLayoutAlgorithm-@Trace public columnsGap?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## columnsTemplate

```TypeScript
@Trace public columnsTemplate?: string | ItemFillPolicy
```

设置当前网格布局的列数。

默认值：'1fr'

非法值：按默认值处理。

装饰器类型：@Trace

**类型：** string | ItemFillPolicy

**默认值：** '1fr'

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-GridLayoutAlgorithm-@Trace public columnsTemplate?: string | ItemFillPolicy--><!--Device-GridLayoutAlgorithm-@Trace public columnsTemplate?: string | ItemFillPolicy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## rowsGap

```TypeScript
@Trace public rowsGap?: LengthMetrics
```

行与行之间的间距。

默认值：LengthMetrics.vp(0)

非法值：按默认值处理。

装饰器类型：@Trace

**类型：** LengthMetrics

**默认值：** LengthMetrics.vp(0)

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-GridLayoutAlgorithm-@Trace public rowsGap?: LengthMetrics--><!--Device-GridLayoutAlgorithm-@Trace public rowsGap?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

