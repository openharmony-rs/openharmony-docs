# CustomLayoutAlgorithm

Custom layout algorithm class.

> **NOTE:** 
> 
> The object of the **CustomLayoutAlgorithm** class can be assigned to a variable of the **LayoutAlgorithm** type as
> the input parameter of the
> [DynamicLayout](../../../reference/apis-arkui/arkui-ts/ts-container-dynamiclayout.md) component to specify the
> layout algorithm.

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
> In this callback, you can call
> [getChild()](../../../reference/apis-arkui/js-apis-arkui-frameNode.md#getchild12) of
> [FrameNode](../../../reference/apis-arkui/js-apis-arkui-frameNode.md#framenode-1) to obtain the child
> component **FrameNode** and call
> [layout()](../../../reference/apis-arkui/js-apis-arkui-frameNode.md#layout12) of
> [FrameNode](../../../reference/apis-arkui/js-apis-arkui-frameNode.md#framenode-1) to set the position of the
> child component. For details, see
> [Example 1](../../../reference/apis-arkui/arkui-ts/ts-container-dynamiclayout.md#example-1-implementing-waterfall-layout-using-a-custom-layout-algorithm).

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**Widget capability:** This API can be used in ArkTS widgets since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| self | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Entity node of the dynamic layout component in the component tree. |
| position | [Position](arkts-arkui-position-t.md) | Yes | Position information used in layout of the dynamic layout component. |

**Examples**

```TypeScript
For details, see [Example 1: Implementing Waterfall Layout Using a Custom Layout Algorithm](../arkui-ts/ts-container-dynamiclayout.md#example-1-implementing-waterfall-layout-using-a-custom-layout-algorithm).
```

## onMeasure

```TypeScript
onMeasure(self: FrameNode, constraint: LayoutConstraint): void
```

Customizes the size of the child component to be measured. When the size of the dynamic layout component is determined, the ArkUI framework will transfer the FrameNode and layout constraint of the component to you through **onMeasure**. State variables should not be changed in this callback.

> **NOTE:** 
> 
> In this callback, you can call
> [getChild()](../../../reference/apis-arkui/js-apis-arkui-frameNode.md#getchild12) of
> [FrameNode](../../../reference/apis-arkui/js-apis-arkui-frameNode.md#framenode-1) to obtain the child
> component **FrameNode** and call
> [measure()](../../../reference/apis-arkui/js-apis-arkui-frameNode.md#measure12) of
> [FrameNode](../../../reference/apis-arkui/js-apis-arkui-frameNode.md#framenode-1) to measure the size of the
> child component. For details, see
> [Example 1](../../../reference/apis-arkui/arkui-ts/ts-container-dynamiclayout.md#example-1-implementing-waterfall-layout-using-a-custom-layout-algorithm).

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**Widget capability:** This API can be used in ArkTS widgets since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| self | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Entity node of the dynamic layout component in the component tree. |
| constraint | [LayoutConstraint](arkts-arkui-framenode-layoutconstraint-i.md) | Yes | Layout constraint used by the dynamic layout component for measurement. |
