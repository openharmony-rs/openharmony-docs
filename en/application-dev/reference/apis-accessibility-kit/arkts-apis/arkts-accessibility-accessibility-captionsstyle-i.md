# CaptionsStyle

```TypeScript
interface CaptionsStyle
```

Describes the style of captions.

**Since:** 8

<!--Device-accessibility-interface CaptionsStyle--><!--Device-accessibility-interface CaptionsStyle-End-->

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

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

**Widget capability (ArkTS-Dyn only) :** This API can be used in ArkTS widgets since version 23.

<!--Device-CaptionsStyle-backgroundColor: int | string--><!--Device-CaptionsStyle-backgroundColor: int | string-End-->

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

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

**Widget capability (ArkTS-Dyn only) :** This API can be used in ArkTS widgets since version 23.

<!--Device-CaptionsStyle-fontColor: int | string--><!--Device-CaptionsStyle-fontColor: int | string-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Hearing

## fontEdgeType

```TypeScript
fontEdgeType: CaptionsFontEdgeType
```

Font edge type of captions.

**Type:** [CaptionsFontEdgeType](arkts-accessibility-accessibility-captionsfontedgetype-t.md)

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

**Widget capability (ArkTS-Dyn only) :** This API can be used in ArkTS widgets since version 23.

<!--Device-CaptionsStyle-fontEdgeType: CaptionsFontEdgeType--><!--Device-CaptionsStyle-fontEdgeType: CaptionsFontEdgeType-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Hearing

## fontFamily

```TypeScript
fontFamily: CaptionsFontFamily
```

Font family of captions.

**Type:** [CaptionsFontFamily](arkts-accessibility-accessibility-captionsfontfamily-t.md)

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

**Widget capability (ArkTS-Dyn only) :** This API can be used in ArkTS widgets since version 23.

<!--Device-CaptionsStyle-fontFamily: CaptionsFontFamily--><!--Device-CaptionsStyle-fontFamily: CaptionsFontFamily-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Hearing

## fontScale

```TypeScript
fontScale: number
```

Font scale factor of captions, in percentage. The value ranges from 1 to 200.

**Type:** number

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

**Widget capability (ArkTS-Dyn only) :** This API can be used in ArkTS widgets since version 23.

<!--Device-CaptionsStyle-fontScale: int--><!--Device-CaptionsStyle-fontScale: int-End-->

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

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

**Widget capability (ArkTS-Dyn only) :** This API can be used in ArkTS widgets since version 23.

<!--Device-CaptionsStyle-windowColor: int | string--><!--Device-CaptionsStyle-windowColor: int | string-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Hearing
