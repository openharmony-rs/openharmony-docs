# Measurable

```TypeScript
declare interface Measurable
```

Provides measurement information of a child component. The **Measurable** object is created and passed in by the ArkUI framework when **onMeasureSize** is called, and is used in the measurement phase. Unlike **Layoutable** (used in the layout phase), Measurable is mainly used to measure the size of a child component. Developers set constraint conditions and obtain measurement results through the **measure** method. **Measurable** and **Layoutable** are two representations of the same child component in different layout phases.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getBorderWidth

```TypeScript
getBorderWidth() : DirectionalEdgesT<number>
```

Obtains the **borderWidth** information of the child component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [DirectionalEdgesT](../arkts-apis/arkts-arkui-directionaledgest-i.md)&lt;number&gt; | Border width object of the child component, containing the border width values in four directions. Unit: vp. |

## getMargin

```TypeScript
getMargin() : DirectionalEdgesT<number>
```

Obtains the margin information of the child component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [DirectionalEdgesT](../arkts-apis/arkts-arkui-directionaledgest-i.md)&lt;number&gt; | Margin object of the child component, containing the margin values in four directions. Unit: vp. |

## getPadding

```TypeScript
getPadding() : DirectionalEdgesT<number>
```

Obtains the padding information of the child component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [DirectionalEdgesT](../arkts-apis/arkts-arkui-directionaledgest-i.md)&lt;number&gt; | Padding object of the child component, containing the padding values in four directions. Unit: vp. |

## measure

```TypeScript
measure(constraint: ConstraintSizeOptions) : MeasureResult
```

Imposes size constraints on the child component and returns the measured layout information of the component.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| constraint | [ConstraintSizeOptions](../arkts-apis/arkts-arkui-constraintsizeoptions-i.md) | Yes | Constraint size, including constraint conditions such as **minWidth**, **maxWidth**, **minHeight**, and **maxHeight**, used to limit the size range of the child component. Value principle: **minWidth** ≤ **maxWidth**, **minHeight** ≤ **maxHeight**; unit: vp. |

**Return value:**

| Type | Description |
| --- | --- |
| [MeasureResult](arkts-arkui-common-comp-measureresult-i.md) | Layout information of the component after measurement, including the measured width and height. |

## uniqueId

```TypeScript
uniqueId?: number
```

Unique ID assigned by the system to the child component. It uniquely identifies the child component for subsequent operations (for example, obtaining the **FrameNode** through **getFrameNodeByUniqueId**). The value range is [0, +∞). The system automatically assigns a UniqueID to each child component. Developers can read it as needed and do not need to set it proactively.

**Type:** number

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
