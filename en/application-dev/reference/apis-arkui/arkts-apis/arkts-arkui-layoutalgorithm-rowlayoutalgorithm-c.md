# RowLayoutAlgorithm

```TypeScript
export class RowLayoutAlgorithm implements LayoutAlgorithm
```

A horizontal linear layout algorithm class, which is used to implement horizontal linear arrangement of child components. It is suitable for scenarios where child components need to be arranged horizontally, such as horizontal lists, toolbars, tab bars, and action button groups. It supports setting the spacing between child components, vertical alignment mode, horizontal alignment mode, and arrangement direction, which provides layout capabilities similar to the **Row** component.

> **NOTE:** 
> 
> The object of the **RowLayoutAlgorithm** class can be used as the input parameter of the
> [DynamicLayout](../arkts-components/arkts-arkui-dynamiclayout-comp-attribute.md#dynamiclayoutattribute) component to specify a layout algorithm.

**Inheritance/Implementation:** RowLayoutAlgorithm implements [LayoutAlgorithm](arkts-arkui-layoutalgorithm-i.md)

**Since:** 24

**Decorator:** @ObservedV2

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(option?: RowLayoutAlgorithmOptions)
```

Constructs the horizontal linear layout algorithm class.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**Widget capability:** This API can be used in ArkTS widgets since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| option | [RowLayoutAlgorithmOptions](arkts-arkui-layoutalgorithm-rowlayoutalgorithmoptions-i.md) | No | Input parameters for constructing the horizontal linear layout algorithm, which are used to set the spacing, main axis alignment mode, cross axis alignment mode, and main axis arrangement direction of the layout algorithm. If not passed, the default value of each attribute is used. |

**Examples**

For details, see [Example 2: Switching the Layout Algorithm](../arkui-ts/ts-container-dynamiclayout.md#example-2-switching-the-layout-algorithm).

## alignItems

```TypeScript
public alignItems?: VerticalAlign
```

Vertical alignment mode of all child components.

Default value: **VerticalAlign.Center**

Invalid values are treated as the default value.

Decorator: [@Trace](../../../ui/state-management/arkts-new-observedV2-and-trace.md)

**Type:** [VerticalAlign](arkts-arkui-verticalalign-e.md)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**Widget capability:** This API can be used in ArkTS widgets since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isReverse

```TypeScript
public isReverse?: boolean
```

Whether to reverse the horizontal arrangement of child components. **true** indicates to reverse the horizontal arrangement of child components. The horizontal direction is affected by the common attribute [direction](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#direction). If the [direction](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#direction) attribute takes effect, the child components are arranged based on **direction** and then are reversed based on **isReverse**. **false** indicates to arrange child components in the horizontal direction in normal order.

Default value: **false**

Invalid values are treated as the default value.

Decorator: [@Trace](../../../ui/state-management/arkts-new-observedV2-and-trace.md)

**Type:** boolean

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**Widget capability:** This API can be used in ArkTS widgets since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## justifyContent

```TypeScript
public justifyContent?: FlexAlign
```

Horizontal alignment mode of all child components.

Default value: **FlexAlign.Start**

Invalid values are treated as the default value.

Decorator: [@Trace](../../../ui/state-management/arkts-new-observedV2-and-trace.md)

**Type:** [FlexAlign](arkts-arkui-flexalign-e.md)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**Widget capability:** This API can be used in ArkTS widgets since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
public space?: LengthMetrics
```

Horizontal spacing between child components in a horizontal layout. Value range: a non-negative number.

Default value: **LengthMetrics.vp(0)**

Invalid values are treated as the default value.

Decorator: [@Trace](../../../ui/state-management/arkts-new-observedV2-and-trace.md)

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**Widget capability:** This API can be used in ArkTS widgets since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
