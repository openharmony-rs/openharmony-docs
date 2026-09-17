# CaptionsStyle

Describes the style of captions.

**Since:** 8

**System capability:** SystemCapability.BarrierFree.Accessibility.Hearing

## Modules to Import

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { AccessibilityEventType, AccessibilityAction, FocusMoveResultCode, InjectActionType, AccessibilityFocusScene, FocusRuleType, OperateVirtualNodeResult, AccessibilitySourceType } from '@kit.AccessibilityKit';
```

## backgroundColor

```TypeScript
backgroundColor: number | string
```

Describes the caption background color.

number: HEX format color, supporting RGB or ARGB.

string: supports '#rrggbb', '#rrggbbaa', '#rgb', and '#rgba' formats.

Example: opaque red, number: 0xffff0000, string: '#ff0000', '#ff0000ff', '#f00', '#f00f'.

**Type:** number &#124; string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Hearing

## fontColor

```TypeScript
fontColor: number | string
```

Describes the caption font color.

number: HEX format color, supporting RGB or ARGB.

string: supports '#rrggbb', '#rrggbbaa', '#rgb', and '#rgba' formats.

Example: opaque red, number: 0xffff0000, string: '#ff0000', '#ff0000ff', '#f00', '#f00f'.

**Type:** number &#124; string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Hearing

## fontEdgeType

```TypeScript
fontEdgeType: CaptionsFontEdgeType
```

Font edge type of captions.

**Type:** [CaptionsFontEdgeType](arkts-accessibility-accessibility-captionsfontedgetype-t.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Hearing

## fontFamily

```TypeScript
fontFamily: CaptionsFontFamily
```

Font family of captions.

**Type:** [CaptionsFontFamily](arkts-accessibility-accessibility-captionsfontfamily-t.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Hearing

## fontScale

```TypeScript
fontScale: number
```

Font scale factor of captions, in percentage. The value ranges from 1 to 200.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Hearing

## windowColor

```TypeScript
windowColor: number | string
```

Describes the caption window color.

number: HEX format color, supporting RGB or ARGB.

string: supports '#rrggbb', '#rrggbbaa', '#rgb', and '#rgba' formats.

Example: opaque red, number: 0xffff0000, string: '#ff0000', '#ff0000ff', '#f00', '#f00f'.

**Type:** number &#124; string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Hearing
