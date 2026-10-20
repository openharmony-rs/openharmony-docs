# LayoutChild

```TypeScript
declare interface LayoutChild
```

Provides the child component layout information.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** Measurable/Layoutable

<!--Device-unnamed-declare interface LayoutChild--><!--Device-unnamed-declare interface LayoutChild-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## layout

```TypeScript
layout(childLayoutInfo: LayoutInfo)
```

Applies the specified layout constraints to the child component.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** Measurable/Layoutable

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-LayoutChild-layout(childLayoutInfo: LayoutInfo)--><!--Device-LayoutChild-layout(childLayoutInfo: LayoutInfo)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| childLayoutInfo | [LayoutInfo](arkts-arkui-common-comp-layoutinfo-i.md) | Yes | Layout information of the child component, including **position** (position coordinates) and **constraint** (constraint size). The position is used to set the **position** of the child component, and the constraint is used to pass **constraint** information to the child component. |

## measure

```TypeScript
measure(childConstraint: ConstraintSizeOptions)
```

Applies specified size constraints to child components.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** Measurable/Layoutable

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-LayoutChild-measure(childConstraint: ConstraintSizeOptions)--><!--Device-LayoutChild-measure(childConstraint: ConstraintSizeOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| childConstraint | [ConstraintSizeOptions](../arkts-apis/arkts-arkui-constraintsizeoptions-i.md) | Yes | Constraint information about the size range of the child component, including constraint conditions such as **minWidth**, **maxWidth**, **minHeight**, and **maxHeight**. Unit: vp. |

## borderInfo

```TypeScript
borderInfo: LayoutBorderInfo
```

Provides the border information of the child component.

**Type:** [LayoutBorderInfo](arkts-arkui-common-comp-layoutborderinfo-i.md)

**Since:** 9

**Deprecated since:** 10

**Substitutes:** Measurable/Layoutable

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-LayoutChild-borderInfo: LayoutBorderInfo--><!--Device-LayoutChild-borderInfo: LayoutBorderInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constraint

```TypeScript
constraint: ConstraintSizeOptions
```

Constraint size of the child component. Value principle: **minWidth** ≤ **maxWidth**, **minHeight** ≤ **maxHeight**. Unit: vp.

**Type:** [ConstraintSizeOptions](../arkts-apis/arkts-arkui-constraintsizeoptions-i.md)

**Since:** 9

**Deprecated since:** 10

**Substitutes:** Measurable/Layoutable

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-LayoutChild-constraint: ConstraintSizeOptions--><!--Device-LayoutChild-constraint: ConstraintSizeOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id: string
```

ID of the child component.

**Type:** string

**Since:** 9

**Deprecated since:** 10

**Substitutes:** Measurable/Layoutable

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-LayoutChild-id: string--><!--Device-LayoutChild-id: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## name

```TypeScript
name: string
```

Name of the child component.

**Type:** string

**Since:** 9

**Deprecated since:** 10

**Substitutes:** Measurable/Layoutable

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-LayoutChild-name: string--><!--Device-LayoutChild-name: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## position

```TypeScript
position: Position
```

Position coordinates of the child component. Unit: vp.

**Type:** Position

**Since:** 9

**Deprecated since:** 10

**Substitutes:** Measurable/Layoutable

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-LayoutChild-position: Position--><!--Device-LayoutChild-position: Position-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
