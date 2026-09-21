# GridLayoutAlgorithm

```TypeScript
export class GridLayoutAlgorithm implements LayoutAlgorithm
```

A grid layout algorithm class, which is used to implement grid arrangement of child components. It is suitable for scenarios where child components need to be arranged in a grid format, such as grid menus, photo grids, app lists, and product displays. It supports setting the column count template, column spacing, and row spacing, which provides layout capabilities similar to the **Grid** component.

> **NOTE:** 
> 
> The object of the **GridLayoutAlgorithm** class can be used as the input parameter of the
> [DynamicLayout](../arkts-components/arkts-arkui-dynamiclayout-comp-attribute.md#dynamiclayoutattribute) component to specify a layout algorithm.

**Inheritance/Implementation:** GridLayoutAlgorithm implements [LayoutAlgorithm](arkts-arkui-layoutalgorithm-i.md)

**Since:** 24

**Decorator:** @ObservedV2

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(option?: GridLayoutAlgorithmOptions)
```

Constructs the grid layout algorithm class.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| option | [GridLayoutAlgorithmOptions](arkts-arkui-layoutalgorithm-gridlayoutalgorithmoptions-i.md) | No | Input parameters for constructing the grid layout algorithm, which are used to set the number of columns, column spacing, and row spacing of the grid layout. If not passed, the default value of each attribute is used. |

**Examples**

For details, see [Example 2: Switching the Layout Algorithm](../arkui-ts/ts-container-dynamiclayout.md#example-2-switching-the-layout-algorithm).

## columnsGap

```TypeScript
public columnsGap?: LengthMetrics
```

Spacing between columns. Value range: a non-negative number.

Default value: **LengthMetrics.vp(0)**

Invalid values are treated as the default value.

**Decorator:** [@Trace](../../../ui/state-management/arkts-new-observedV2-and-trace.md)

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Default:** LengthMetrics.vp(0)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## columnsTemplate

```TypeScript
public columnsTemplate?: string | ItemFillPolicy
```

Column template of the current grid layout, defining the width and number of columns. The string type must conform to the template format, for example, **'1fr'** indicates a single-column layout, **'1fr 1fr 1fr'** indicates a three-column equal-width layout, and **'1fr 2fr'** indicates a two-column layout where the second column is twice as wide as the first. When **ItemFillPolicy** is used, adaptive column count can be implemented.

Default value: **'1fr'**

Invalid values are treated as the default value.

**Decorator:** [@Trace](../../../ui/state-management/arkts-new-observedV2-and-trace.md)

**Type:** string &#124; [ItemFillPolicy](arkts-arkui-itemfillpolicy-i.md)

**Default:** '1fr'

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## rowsGap

```TypeScript
public rowsGap?: LengthMetrics
```

Spacing between rows. Value range: a non-negative number.

Default value: **LengthMetrics.vp(0)**

Invalid values are treated as the default value.

**Decorator:** [@Trace](../../../ui/state-management/arkts-new-observedV2-and-trace.md)

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Default:** LengthMetrics.vp(0)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
