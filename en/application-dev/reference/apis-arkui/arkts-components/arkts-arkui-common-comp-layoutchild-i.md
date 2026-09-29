# LayoutChild

```TypeScript
declare interface LayoutChild
```

Provides the child component layout information.

@interface LayoutChild

**Since:** 9

**Deprecated since:** 10

**Substitutes:** Measurable/Layoutable

<!--Device-unnamed-declare interface LayoutChild--><!--Device-unnamed-declare interface LayoutChild-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## layout

```TypeScript
layout(childLayoutInfo: LayoutInfo)
```

Call this layout method in onLayout callback to assign layout info to sub component.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** Measurable/Layoutable

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-LayoutChild-layout(childLayoutInfo: LayoutInfo)--><!--Device-LayoutChild-layout(childLayoutInfo: LayoutInfo)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| childLayoutInfo | [LayoutInfo](arkts-arkui-common-comp-layoutinfo-i.md) | Yes |  |

## measure

```TypeScript
measure(childConstraint: ConstraintSizeOptions)
```

Call this measure method in onMeasure callback to supply sub component size.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** Measurable/Layoutable

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-LayoutChild-measure(childConstraint: ConstraintSizeOptions)--><!--Device-LayoutChild-measure(childConstraint: ConstraintSizeOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| childConstraint | [ConstraintSizeOptions](../arkts-apis/arkts-arkui-constraintsizeoptions-i.md) | Yes |  |

## borderInfo

```TypeScript
borderInfo: LayoutBorderInfo
```

Sub component border info.

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

Sub component constraint.

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

Sub component id.

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

Sub component name.

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

Sub component position.

**Type:** Position

**Since:** 9

**Deprecated since:** 10

**Substitutes:** Measurable/Layoutable

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-LayoutChild-position: Position--><!--Device-LayoutChild-position: Position-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
