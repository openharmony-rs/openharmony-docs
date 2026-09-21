# StackLayoutAlgorithm

```TypeScript
export class StackLayoutAlgorithm implements LayoutAlgorithm
```

A stack layout algorithm class, which is used to implement stacked arrangement of child components. It is suitable for scenarios where child components need to be displayed in a stacking manner, such as stacked layers, floating buttons, content areas with backgrounds, and card stack effects. It supports setting the alignment mode of child components within the stack container, which provides layout capabilities similar to the **Stack** component.

> **NOTE:** 
> 
> The object of the **StackLayoutAlgorithm** class can be used as the input parameter of the
> [DynamicLayout](../arkts-components/arkts-arkui-dynamiclayout-comp-attribute.md#dynamiclayoutattribute) component to specify a layout algorithm.

**Inheritance/Implementation:** StackLayoutAlgorithm implements [LayoutAlgorithm](arkts-arkui-layoutalgorithm-i.md)

**Since:** 24

**Decorator:** @ObservedV2

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(option?: StackLayoutAlgorithmOptions)
```

Constructs the stack layout algorithm class.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**Widget capability:** This API can be used in ArkTS widgets since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| option | [StackLayoutAlgorithmOptions](arkts-arkui-layoutalgorithm-stacklayoutalgorithmoptions-i.md) | No | Input parameters for constructing the stack layout algorithm, which are used to set the nine-box grid alignment mode. If not passed, the default value of each attribute is used. |

**Examples**

For details, see [Example 2: Switching the Layout Algorithm](../arkui-ts/ts-container-dynamiclayout.md#example-2-switching-the-layout-algorithm).

## alignContent

```TypeScript
public alignContent?: LocalizedAlignment
```

Alignment mode of child components in the stack layout algorithm.

Default value: **LocalizedAlignment.CENTER**

Invalid values are treated as the default value.

Decorator: [@Trace](../../../ui/state-management/arkts-new-observedV2-and-trace.md)

**Type:** [LocalizedAlignment](arkts-arkui-localizedalignment-e.md)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**Widget capability:** This API can be used in ArkTS widgets since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
