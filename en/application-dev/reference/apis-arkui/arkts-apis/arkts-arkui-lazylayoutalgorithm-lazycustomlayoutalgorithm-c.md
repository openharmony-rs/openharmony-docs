# LazyCustomLayoutAlgorithm

```TypeScript
export class LazyCustomLayoutAlgorithm implements LazyLayoutAlgorithm
```

A custom lazy loading layout algorithm class. It supports custom measurement and arrangement of child components by overriding [onMeasure](#onmeasure) and [onLayout](#onlayout).

> **NOTE:** 
> 
> The object of the **LazyCustomLayoutAlgorithm** class can be used as the input parameter of the
> [LazyDynamicLayout](../../../reference/apis-arkui/arkui-ts/ts-container-lazydynamiclayout.md) component to specify
> a layout algorithm.

**Inheritance/Implementation:** LazyCustomLayoutAlgorithm implements [LazyLayoutAlgorithm](arkts-arkui-lazylayoutalgorithm-i.md)

**Since:** 26.0.0

<!--Device-unnamed-export class LazyCustomLayoutAlgorithm implements LazyLayoutAlgorithm--><!--Device-unnamed-export class LazyCustomLayoutAlgorithm implements LazyLayoutAlgorithm-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(option?: LazyCustomLayoutAlgorithmOptions)
```

Constructor of the custom lazy loading layout algorithm class.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LazyCustomLayoutAlgorithm-constructor(option?: LazyCustomLayoutAlgorithmOptions)--><!--Device-LazyCustomLayoutAlgorithm-constructor(option?: LazyCustomLayoutAlgorithmOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| option | [LazyCustomLayoutAlgorithmOptions](arkts-arkui-lazylayoutalgorithm-lazycustomlayoutalgorithmoptions-i.md) | No | Input parameters for constructing the custom lazy loading layout algorithm, which are used to set the axis direction of the layout algorithm. This parameter needs to be passed when the main axis direction needs to be specified. If not passed, the main axis direction is **Axis.Vertical**. |

## onLayout

```TypeScript
onLayout(self: FrameNode, position: Position): void
```

Customizes the position of the child component to be arranged. When the position of the lazy loading dynamic layout component is determined, the ArkUI framework will transfer the FrameNode and layout position of the component to you through **onLayout**. State variables should not be changed in this callback.

> **NOTE:** 
> 
> - In this callback, you can call the [getChild()](arkts-arkui-framenode-c.md#getchild) API of [FrameNode](arkts-arkui-framenode-c.md) to obtain the child component FrameNode and call the [layout()](arkts-arkui-framenode-c.md#layout) API of [FrameNode](arkts-arkui-framenode-c.md) to set the position of the child component. For details, see [Example 1: Implementing Custom Lazy Loading Layout](arkts-arkui-lazylayoutalgorithm-i.md)of the **LazyDynamicLayout** component.
> 
> - When calling [getChild()](arkts-arkui-framenode-c.md#getchild) in this callback to obtain a child component, you must pass [ExpandMode.LAZY_NOT_EXPAND](arkts-arkui-framenode-expandmode-e.md) to prevent lazy loading from becoming invalid due to full loading of child components. When calling [getChildrenCount()](arkts-arkui-framenode-c.md#getchildrencount) to obtain the total number of child components, you must pass [ChildrenCountMode.ALL_NOT_EXPAND](arkts-arkui-framenode-childrencountmode-e.md) to prevent lazy loading from becoming invalid due to full loading of child components.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LazyCustomLayoutAlgorithm-onLayout(self: FrameNode, position: Position): void--><!--Device-LazyCustomLayoutAlgorithm-onLayout(self: FrameNode, position: Position): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| self | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Entity node of the lazy loading dynamic layout component in the component tree. |
| position | [Position](arkts-arkui-position-t.md) | Yes | Position information used when the lazy loading dynamic layout component is laid out. |

## onMeasure

```TypeScript
onMeasure(self: FrameNode, constraint: LayoutConstraint, helper?: LazyLayoutHelper): void
```

Customizes the size of the child component to be measured. When the size of the lazy loading dynamic layout component is determined, the ArkUI framework will transfer the FrameNode, layout constraint, and lazy loading auxiliary object corresponding to the component to you through **onMeasure**. State variables should not be changed in this callback.

> **NOTE:** 
> 
> - In this callback, you can call the [getChild()](arkts-arkui-framenode-c.md#getchild) API of [FrameNode](arkts-arkui-framenode-c.md) to obtain the child component FrameNode and call the [measure()](arkts-arkui-framenode-c.md#measure) API of [FrameNode](arkts-arkui-framenode-c.md) to measure the size of the child component. For details, see [Example 1: Implementing Custom Lazy Loading Layout](arkts-arkui-lazylayoutalgorithm-i.md)of the **LazyDynamicLayout** component.
> 
> - When calling [getChild()](arkts-arkui-framenode-c.md#getchild) in this callback to obtain a child component, you must pass [ExpandMode.LAZY_NOT_EXPAND](arkts-arkui-framenode-expandmode-e.md) to prevent lazy loading from becoming invalid due to full loading of child components. When calling [getChildrenCount()](arkts-arkui-framenode-c.md#getchildrencount) to obtain the total number of child components, you must pass [ChildrenCountMode.ALL_NOT_EXPAND](arkts-arkui-framenode-childrencountmode-e.md) to prevent lazy loading from becoming invalid due to full loading of child components.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LazyCustomLayoutAlgorithm-onMeasure(self: FrameNode, constraint: LayoutConstraint, helper?: LazyLayoutHelper): void--><!--Device-LazyCustomLayoutAlgorithm-onMeasure(self: FrameNode, constraint: LayoutConstraint, helper?: LazyLayoutHelper): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| self | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Entity node of the lazy loading dynamic layout component in the component tree. |
| constraint | [LayoutConstraint](arkts-arkui-framenode-layoutconstraint-i.md) | Yes | Layout constraint used when the lazy loading dynamic layout component is measured. |
| helper | [LazyLayoutHelper](arkts-arkui-lazylayoutalgorithm-lazylayouthelper-c.md) | No | Lazy loading layout auxiliary object, which provides the layout direction and visible area position information. If the value is **undefined**, lazy loading is not supported. The value of **helper** is **undefined** in the following scenarios: <br>1. Lazy loading is not supported when the [WaterFlow](../arkts-components/arkts-arkui-waterflow-comp.md) component uses the multi-column mode or uses the section mode with any section being in multi-column format. <br>2. Lazy loading is not supported when any of [lanes](../arkts-components/arkts-arkui-list-comp-attribute.md#lanes), [chainAnimation](../arkts-components/arkts-arkui-list-comp-attribute.md#chainanimation), and [scrollSnapAlign](../arkts-components/arkts-arkui-list-comp-attribute.md#scrollsnapalign) is set for the [List](../arkts-components/arkts-arkui-list-comp.md) component. |
