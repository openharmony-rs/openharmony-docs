# CustomLayoutAlgorithm

```TypeScript
export class CustomLayoutAlgorithm implements LayoutAlgorithm
```

A custom layout algorithm class, which allows you to implement custom measurement and layout logic. It is suitable for complex layout scenarios that require fine-grained control over child component sizes and positions, such as waterfall flow layout, irregular grid layout, and dynamic flow layout. By overriding **onMeasure** and **onLayout**, you can implement layout strategies that are not covered by the built-in layout algorithms.

> **NOTE:** 
> 
> The object of the **CustomLayoutAlgorithm** class can be used as the input parameter of the
> [DynamicLayout](../arkts-components/arkts-arkui-dynamiclayout-comp-attribute.md#dynamiclayoutattribute) component to specify a layout algorithm.

**Inheritance/Implementation:** CustomLayoutAlgorithm implements [LayoutAlgorithm](arkts-arkui-layoutalgorithm-i.md)

**Since:** 24

**Decorator:** @ObservedV2

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onLayout

```TypeScript
onLayout(self: FrameNode, position: Position): void
```

Customizes the position of the child component to be arranged. When the position of the dynamic layout component is determined, the ArkUI framework will transfer the FrameNode and layout position of the component to you through **onLayout**. State variables should not be changed in this callback.

> **NOTE:** 
> 
> - **onLayout** and [onMeasure](#onmeasure) usually need to be used together to complete the full custom layout process. The framework first calls **onMeasure** to measure the child component size, and then calls **onLayout** to set the child component position.
> 
> - In this API, you can call [getChild()](arkts-arkui-framenode-c.md#getchild) of [FrameNode](arkts-arkui-framenode-c.md) to obtain the child component FrameNode, call [layout()](arkts-arkui-framenode-c.md#layout) of [FrameNode](arkts-arkui-framenode-c.md) to set the child component position. For details, see [Example 1: Implementing Waterfall Layout Using a Custom Layout Algorithm](../../../reference/apis-arkui/arkui-ts/ts-container-dynamiclayout.md#example-1-implementing-waterfall-layout-using-a-custom-layout-algorithm).

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**Widget capability:** This API can be used in ArkTS widgets since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| self | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Entity node of the dynamic layout component in the component tree, which is used to obtain the child component FrameNode and set the child component position. |
| position | [Position](arkts-arkui-position-t.md) | Yes | Position information used in layout of the dynamic layout component. |

**Examples**

For details, see [Example 1: Implementing Waterfall Layout Using a Custom Layout Algorithm](../arkui-ts/ts-container-dynamiclayout.md#example-1-implementing-waterfall-layout-using-a-custom-layout-algorithm).

## onMeasure

```TypeScript
onMeasure(self: FrameNode, constraint: LayoutConstraint): void
```

Customizes the size of the child component to be measured. When the size of the dynamic layout component is determined, the ArkUI framework will transfer the FrameNode and layout constraint of the component to you through **onMeasure**. State variables should not be changed in this callback.

> **NOTE:** 
> 
> - **onMeasure** and [onLayout](#onlayout) usually need to be used together to complete the full custom layout process. The framework first calls **onMeasure** to measure the child component size, and then calls **onLayout** to set the child component position.
> 
> - In this API, you can call [getChild()](arkts-arkui-framenode-c.md#getchild) of [FrameNode](arkts-arkui-framenode-c.md) to obtain the child component FrameNode, call [measure()](arkts-arkui-framenode-c.md#measure) of [FrameNode](arkts-arkui-framenode-c.md) to measure the child component size. For details, see [Example 1: Implementing Waterfall Layout Using a Custom Layout Algorithm](../../../reference/apis-arkui/arkui-ts/ts-container-dynamiclayout.md#example-1-implementing-waterfall-layout-using-a-custom-layout-algorithm).

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**Widget capability:** This API can be used in ArkTS widgets since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| self | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Entity node of the dynamic layout component in the component tree, which is used to obtain the child component FrameNode and measure the child component size. |
| constraint | [LayoutConstraint](arkts-arkui-framenode-layoutconstraint-i.md) | Yes | Layout constraint used by the dynamic layout component for measurement. |
