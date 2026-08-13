# GridLayoutAlgorithm

网格布局算法类。 > **说明：** > > GridLayoutAlgorithm类对象可以作为 > [DynamicLayout](../../../reference/apis-arkui/arkui-ts/ts-container-dynamiclayout.md)组件的入参指定布局算法。

**继承/实现关系：** GridLayoutAlgorithm implements [LayoutAlgorithm](arkts-na-layoutalgorithm-i.md#LayoutAlgorithm)

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-unnamed-export declare class GridLayoutAlgorithm--><!--Device-unnamed-export declare class GridLayoutAlgorithm-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(option?: GridLayoutAlgorithmOptions)
```

网格布局算法类的构造函数。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-GridLayoutAlgorithm-constructor(option?: GridLayoutAlgorithmOptions)--><!--Device-GridLayoutAlgorithm-constructor(option?: GridLayoutAlgorithmOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| option | [GridLayoutAlgorithmOptions](arkts-na-layoutalgorithm-gridlayoutalgorithmoptions-i.md) | 否 | 网格布局算法的构造入参， 设置网格布局的列数、列间距、行间距。 |

## columnsGap

```TypeScript
public columnsGap?: LengthMetrics
```

列与列之间的间距。 非法值：按默认值处理。

**类型：** [LengthMetrics](arkts-na-graphics-lengthmetrics-c.md)

**默认值：** LengthMetrics.vp(0)

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-GridLayoutAlgorithm-public columnsGap?: LengthMetrics--><!--Device-GridLayoutAlgorithm-public columnsGap?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## columnsTemplate

```TypeScript
public columnsTemplate?: string | ItemFillPolicy
```

设置当前网格布局的列数。 非法值：按默认值处理。

**类型：** string \| [ItemFillPolicy](arkts-na-units-itemfillpolicy-i.md)

**默认值：** '1fr'

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-GridLayoutAlgorithm-public columnsTemplate?: string | ItemFillPolicy--><!--Device-GridLayoutAlgorithm-public columnsTemplate?: string | ItemFillPolicy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## rowsGap

```TypeScript
public rowsGap?: LengthMetrics
```

行与行之间的间距。 非法值：按默认值处理。

**类型：** [LengthMetrics](arkts-na-graphics-lengthmetrics-c.md)

**默认值：** LengthMetrics.vp(0)

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-GridLayoutAlgorithm-public rowsGap?: LengthMetrics--><!--Device-GridLayoutAlgorithm-public rowsGap?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

