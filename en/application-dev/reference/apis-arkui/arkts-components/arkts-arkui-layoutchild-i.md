# LayoutChild

Sub component info passed from framework when layout and measure happens.

@interface LayoutChild

**Since:** 9

**Deprecated since:** 10

**Substitutes:** Measurable/Layoutable

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| childLayoutInfo | [LayoutInfo](arkts-arkui-layoutinfo-i.md) | Yes |  |

## measure

```TypeScript
measure(childConstraint: ConstraintSizeOptions)
```

Call this measure method in onMeasure callback to supply sub component size.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** Measurable/Layoutable

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

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

**Type:** [LayoutBorderInfo](arkts-arkui-layoutborderinfo-i.md)

**Since:** 9

**Deprecated since:** 10

**Substitutes:** Measurable/Layoutable

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full
