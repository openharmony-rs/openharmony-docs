# StackLayoutAlgorithm

Stack layout algorithm class.

> **NOTE:** 
> 
> The object of the **StackLayoutAlgorithm** class can be assigned to a variable of the **LayoutAlgorithm** type as
> the input parameter of the
> [DynamicLayout](../../../reference/apis-arkui/arkui-ts/ts-container-dynamiclayout.md) component to specify the
> layout algorithm.

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
| option | [StackLayoutAlgorithmOptions](arkts-arkui-layoutalgorithm-stacklayoutalgorithmoptions-i.md) | No | Input parameters for constructing the stack layout algorithm, which are used to set the nine-box grid alignment mode. |

**Examples**

```TypeScript
For details, see [Example 2: Switching the Layout Algorithm](../arkui-ts/ts-container-dynamiclayout.md#example-2-switching-the-layout-algorithm).
```

## alignContent

```TypeScript
public alignContent?: LocalizedAlignment
```

Alignment mode of child components in the stack layout algorithm.

Default value: **LocalizedAlignment.CENTER**

Invalid values are treated as the default value.

**Type:** [LocalizedAlignment](arkts-arkui-localizedalignment-e.md)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**Widget capability:** This API can be used in ArkTS widgets since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
