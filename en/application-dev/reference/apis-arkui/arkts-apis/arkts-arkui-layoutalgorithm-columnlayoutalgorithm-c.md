# ColumnLayoutAlgorithm

```TypeScript
export class ColumnLayoutAlgorithm implements LayoutAlgorithm
```

A vertical linear layout algorithm class, which is used to implement vertical linear arrangement of child components. It is suitable for scenarios where child components need to be arranged vertically, such as vertical lists, vertically stacked form items, and vertical menus. It supports setting the spacing between child components, horizontal alignment mode, vertical alignment mode, and arrangement direction, which provides layout capabilities similar to the **Column** component.

> **NOTE:** 
> 
> The object of the **ColumnLayoutAlgorithm** class can be used as the input parameter of the
> [DynamicLayout](../arkts-components/arkts-arkui-dynamiclayout-comp-attribute.md#dynamiclayoutattribute) component to specify a layout algorithm.

**Inheritance/Implementation:** ColumnLayoutAlgorithm implements [LayoutAlgorithm](arkts-arkui-layoutalgorithm-i.md)

**Since:** 24

**Decorator:** @ObservedV2

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(option?: ColumnLayoutAlgorithmOptions)
```

Constructs the vertical linear layout algorithm class.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**Widget capability:** This API can be used in ArkTS widgets since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| option | [ColumnLayoutAlgorithmOptions](arkts-arkui-layoutalgorithm-columnlayoutalgorithmoptions-i.md) | No | Input parameters for constructing the vertical linear layout algorithm, which are used to set the spacing, main axis alignment method, cross axis alignment method, and main axis arrangement direction of the layout algorithm. If not passed, the default value of each attribute is used. |

**Examples**

For details, see [Example 2: Switching the Layout Algorithm](../arkui-ts/ts-container-dynamiclayout.md#example-2-switching-the-layout-algorithm).

## alignItems

```TypeScript
public alignItems?: HorizontalAlign
```

Horizontal alignment mode of all child components.

Default value: **HorizontalAlign.Center**

Invalid values are treated as the default value.

Decorator: [@Trace](../../../ui/state-management/arkts-new-observedV2-and-trace.md)

**Type:** [HorizontalAlign](arkts-arkui-horizontalalign-e.md)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**Widget capability:** This API can be used in ArkTS widgets since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isReverse

```TypeScript
public isReverse?: boolean
```

Whether to reverse the vertical arrangement of child components. **true** indicates to reverse the vertical arrangement of child components. The vertical direction is not affected by the common attribute **direction**. **false** indicates to arrange child components in the vertical direction in normal order.

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

Vertical alignment mode of all child components.

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

Vertical spacing between child components in a vertical layout.

Value range: a non-negative number.

Default value: **LengthMetrics.vp(0)**

Invalid values are treated as the default value.

Decorator: [@Trace](../../../ui/state-management/arkts-new-observedV2-and-trace.md)

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**Widget capability:** This API can be used in ArkTS widgets since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
