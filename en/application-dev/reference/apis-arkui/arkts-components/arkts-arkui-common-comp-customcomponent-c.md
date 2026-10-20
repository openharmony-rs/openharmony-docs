# CustomComponent

```TypeScript
declare class CustomComponent extends BaseCustomComponent
```

Custom Component

**Inheritance/Implementation:** CustomComponent extends [BaseCustomComponent](arkts-arkui-common-comp-basecustomcomponent-c.md)

**Since:** 7

<!--Device-unnamed-declare class CustomComponent extends BaseCustomComponent--><!--Device-unnamed-declare class CustomComponent extends BaseCustomComponent-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## aboutToReuse

```TypeScript
aboutToReuse?(params: Record<string, Object | undefined | null>): void
```

When a reusable custom component is re-added to the node tree from the reuse cache, the **aboutToReuse** lifecycle callback is triggered, and the construction parameters of the component are passed to this callback.

> **NOTE:** 
> 
> * Avoid repeatedly assigning values to state variables that are automatically updated, such as **@Link**\/
> **@ObjectLink**\/**@Prop**, in **aboutToReuse()**.
> 
> * In sliding scenarios, component reuse usually requires this callback function to update the state variables of the component. Therefore, avoid time-consuming operations in this callback function, otherwise frame loss and lag may occur. For best practices, see [Optimizing Time-Consuming Operations in the Main Thread - Component Reuse Callback](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-time-optimization-of-the-main-thread#section20815336174316).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CustomComponent-aboutToReuse?(params: Record<string, Object | undefined | null>): void--><!--Device-CustomComponent-aboutToReuse?(params: Record<string, Object | undefined | null>): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| params | Record&lt;string, Object &#124; undefined &#124; null&gt; | Yes | Construction parameters of the custom component. The key is the name of the component member variable passed in from outside during reuse, and the value is the corresponding parameter value passed in from outside during reuse.<br>**Since:** 20 |

## onLayout

```TypeScript
onLayout?(children: Array<LayoutChild>, constraint: ConstraintSizeOptions): void
```

When the custom component determines the positions of its child components, the ArkUI framework passes the child node information of the custom component and its own size range to the custom component through **onLayout**. Developers can lay out child components in this method. State variables are not allowed to be changed in the **onLayout** function.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [onPlaceChildren](arkts-arkui-common-comp-basecustomcomponent-c.md#onplacechildren)

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-CustomComponent-onLayout?(children: Array<LayoutChild>, constraint: ConstraintSizeOptions): void--><!--Device-CustomComponent-onLayout?(children: Array<LayoutChild>, constraint: ConstraintSizeOptions): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| children | Array&lt;[LayoutChild](arkts-arkui-common-comp-layoutchild-i.md)&gt; | Yes | Child component layout information. |
| constraint | [ConstraintSizeOptions](../arkts-apis/arkts-arkui-constraintsizeoptions-i.md) | Yes | Constraint information of the parent component, including constraint conditions such as **minWidth**, **maxWidth**, **minHeight**, and **maxHeight**. Value principle: **minWidth** ≤ **maxWidth**, **minHeight** ≤ **maxHeight**. Unit: vp. |

## onMeasure

```TypeScript
onMeasure?(children: Array<LayoutChild>, constraint: ConstraintSizeOptions): void
```

When the custom component determines its size, the ArkUI framework passes the child node information of the custom component and its own size range to the custom component through **onMeasure**. Developers can measure child components in this method. State variables are not allowed to be changed in the **onMeasure** function.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [onMeasureSize](arkts-arkui-common-comp-basecustomcomponent-c.md#onmeasuresize)

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-CustomComponent-onMeasure?(children: Array<LayoutChild>, constraint: ConstraintSizeOptions): void--><!--Device-CustomComponent-onMeasure?(children: Array<LayoutChild>, constraint: ConstraintSizeOptions): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| children | Array&lt;[LayoutChild](arkts-arkui-common-comp-layoutchild-i.md)&gt; | Yes | Child component layout information. |
| constraint | [ConstraintSizeOptions](../arkts-apis/arkts-arkui-constraintsizeoptions-i.md) | Yes | Constraint information of the parent component, including constraint conditions such as **minWidth**, **maxWidth**, **minHeight**, and **maxHeight**. Value principle: **minWidth** ≤ **maxWidth** and **minHeight** ≤ **maxHeight**. Unit: vp. |
