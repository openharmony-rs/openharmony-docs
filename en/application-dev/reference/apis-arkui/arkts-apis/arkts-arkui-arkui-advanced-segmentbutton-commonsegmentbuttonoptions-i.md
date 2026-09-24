# CommonSegmentButtonOptions

```TypeScript
interface CommonSegmentButtonOptions
```

Defines the customizable attributes of a segment button component.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { SegmentButton, SegmentButtonOptions, SegmentButtonItemOptionsArray, TabSegmentButtonOptions, TabSegmentButtonConstructionOptions, CapsuleSegmentButtonOptions, CapsuleSegmentButtonConstructionOptions, SegmentButtonTextItem, SegmentButtonIconItem, SegmentButtonIconTextItem, DimensionNoPercentage, CommonSegmentButtonOptions, ItemRestriction, SegmentButtonItemTuple, SegmentButtonItemArray, SegmentButtonItemOptionsConstructorOptions, SegmentButtonItemOptions, BorderRadiusMode } from '@kit.ArkUI';
```

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

Background blur material.

Default value: **BlurStyle.NONE**

If the value is **undefined**, the default value is used.

**Type:** [BlurStyle](../arkts-components/arkts-arkui-common-comp-blurstyle-e.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundBorderRadius

```TypeScript
backgroundBorderRadius?: LengthMetrics
```

Border radius of the overall container of the segment button.

**NOTE:** 

This attribute takes effect only when **borderRadiusMode** is set to **BorderRadiusMode.CUSTOM**.

For capsule-type multi-select segment buttons (**type** is **"capsule"** and **multiply** is **true**), this attribute does not take effect. Use **itemBorderRadius** to configure the radius instead.

The radius size is limited by the component size. The maximum value is half of the component width or height. Percentage setting is not supported. If the value exceeds the maximum, it is automatically corrected to the maximum. If a percentage is used, the default value is used.

Default value: `$r('sys.float.segmentbutton_container_shape')`

If the value is **undefined**, the default value is used.

**Type:** LengthMetrics

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

Color of the background.

Default value: **$r('sys.color.ohos_id_color_button_normal')**

If the value is **undefined**, the default value is used.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Default:** $r('sys.color.ohos_id_color_button_normal')

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundSystemMaterial

```TypeScript
backgroundSystemMaterial?: uiMaterial.Material
```

System material of the background of the segment button component. Different system materials have different properties and produce different effects. After a material is passed in, the animation effects of the **SegmentButton** change.

For capsule-type multi-select segment buttons (type is **"capsule"** and **multiply** is **true**), this attribute does not take effect.

Default value: no material effect.

Since API version 26.0.0, except for capsule-type multi-select segment buttons (**type** is **"capsule"** and **multiply** is **true**), when **backgroundSystemMaterial** is set to a system material with automatic inverted color, **fontColor** and **selectedFontColor** use special system resources that support inverted color, and the colors automatically adapt to the inverted color of the material background color.

**Type:** [uiMaterial.Material](arkts-arkui-uimaterial-material-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderRadiusMode

```TypeScript
borderRadiusMode?: BorderRadiusMode
```

Border radius mode, which controls the radius calculation method.

Default value: **BorderRadiusMode.DEFAULT**

If the value is **undefined**, the default value is used.

**Type:** [BorderRadiusMode](arkts-arkui-arkui-advanced-segmentbutton-borderradiusmode-e.md)

**Default:** BorderRadiusMode.Default

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## buttonPadding

```TypeScript
buttonPadding?: Padding | Dimension
```

Button padding.

Default value:

For icon-only buttons and text-only buttons: `{ top: 4, right: 8, bottom: 4, left: 8 }`

For icon+text buttons: `{ top: 6, right: 8, bottom: 6, left: 8 }`

Unit: vp

If the value is **undefined**, the default value is used.

**Type:** Padding &#124; [Dimension](arkts-arkui-dimension-t.md)

**Default:** For text only / icon only buttons Padding { top: 4, right: 8, bottom: 4, left: 8 }. For text & icon buttons Padding { top: 6, right: 8, bottom: 6, left: 8 }.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: Direction
```

Layout direction.

Default value: **Direction.Auto**

If the value is **undefined**, the default value is used.

**Type:** [Direction](arkts-arkui-direction-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor?: ResourceColor
```

Text color of the button in unselected state.

Default value: **$r('sys.color.ohos_id_color_text_secondary')**

If the value is **undefined**, the default value is used.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: DimensionNoPercentage
```

Font size of the button in unselected state (percentage setting is not supported).

Default value: **$r('sys.float.ohos_id_text_size_body2')**

Unit: fp

If the value is **undefined**, the default value is used.

**Type:** [DimensionNoPercentage](arkts-arkui-dimensionnopercentage-t.md)

**Default:** $r('sys.float.ohos_id_text_size_body2')

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontWeight

```TypeScript
fontWeight?: FontWeight
```

Font weight of the button in unselected state.

Default value: **FontWeight.Regular**

If the value is **undefined**, the default value is used.

**Type:** [FontWeight](arkts-arkui-fontweight-e.md)

**Default:** FontWeight.Regular

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## imageSize

```TypeScript
imageSize?: SizeOptions
```

Image size.

Default value: **{ width: 24, height: 24 }**

Unit: vp

If the value is **undefined**, the default value is used.

**NOTE:** 

The `imageSize` attribute takes effect only for icon buttons and icon + text buttons, and does not respond on text- only buttons.

**Type:** [SizeOptions](arkts-arkui-sizeoptions-i.md)

**Default:** SizeOptions { width: 24, height: 24 }

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemBorderRadius

```TypeScript
itemBorderRadius?: LengthMetrics
```

Border radius of the button items in the segment button.

**NOTE:** 

This attribute takes effect only when **borderRadiusMode** is set to **BorderRadiusMode.CUSTOM**.

For capsule-type multi-select segment buttons (**type** is **"capsule"** and **multiply** is **true**), only the radius of the options at both ends can be controlled.

The radius size is limited by the component size. The maximum value is half of the component width or height. Percentage setting is not supported. If the value exceeds the maximum, it is automatically corrected to the maximum. If a percentage is used, the default value is used.

Default value: `$r('sys.float.segmentbutton_selected_background_shape')`

If the value is **undefined**, the default value is used.

**Type:** LengthMetrics

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## localizedButtonPadding

```TypeScript
localizedButtonPadding?: LocalizedPadding
```

Button padding, which supports adaptive adjustment based on the layout direction (LTR/RTL).

Default value:

For icon-only buttons and text-only buttons: `{ top: LengthMetrics.vp(4), end: LengthMetrics.vp(8), bottom: LengthMetrics.vp(4), start: LengthMetrics.vp(8) }`

For icon + text buttons: `{ top: LengthMetrics.vp(6), end: LengthMetrics.vp(8), bottom: LengthMetrics.vp(6), start: LengthMetrics.vp(8) }`

If the value is **undefined**, the default value is used.

**Type:** [LocalizedPadding](arkts-arkui-localizedpadding-i.md)

**Default:** For text only / icon only buttons LocalizedPadding { top: LengthMetrics.vp(4), end: LengthMetrics.vp(8), bottom: LengthMetrics.vp(4), start: LengthMetrics.vp(8) }. For text & icon buttons LocalizedPadding {{ top: LengthMetrics.vp(6), end: LengthMetrics.vp(8), bottom: LengthMetrics.vp(6), start: LengthMetrics.vp(8)}.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## localizedTextPadding

```TypeScript
localizedTextPadding?: LocalizedPadding
```

Text padding, which supports adaptive adjustment based on the layout direction (LTR/RTL).

Default value: **0**

Unit: vp

If the value is **undefined**, the default value is used.

**Type:** [LocalizedPadding](arkts-arkui-localizedpadding-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedBackgroundColor

```TypeScript
selectedBackgroundColor?: ResourceColor
```

Color of the background for the button in selected state.

Default value:

When **type** is **"tab"**, the default value is `$r('sys.color.segment_button_checked_foreground_color')`.

When **type** is **"capsule"**, the default value is `$r('sys.color.ohos_id_color_emphasize')`.

If the value is **undefined**, the default value is used.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedFontColor

```TypeScript
selectedFontColor?: ResourceColor
```

Text color of the button in selected state.

Default value:

When type is **"tab"**, the default value is `$r('sys.color.ohos_id_color_text_primary')`.

When type is **"capsule"**, the default value is `$r('sys.color.ohos_id_color_foreground_contrary')`.

If the value is **undefined**, the default value is used.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedFontSize

```TypeScript
selectedFontSize?: DimensionNoPercentage
```

Font size of the button in selected state (percentage setting is not supported).

Default value: **$r('sys.float.ohos_id_text_size_body2')**

Unit: fp

If the value is **undefined**, the default value is used.

**Type:** [DimensionNoPercentage](arkts-arkui-dimensionnopercentage-t.md)

**Default:** $r('sys.float.ohos_id_text_size_body2')

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedFontWeight

```TypeScript
selectedFontWeight?: FontWeight
```

Font weight of the button in selected state.

Default value: **FontWeight.Medium**

If the value is **undefined**, the default value is used.

**Type:** [FontWeight](arkts-arkui-fontweight-e.md)

**Default:** FontWeight.Medium

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textPadding

```TypeScript
textPadding?: Padding | Dimension
```

Text padding.

Default value: **0**

Unit: vp

If the value is **undefined**, the default value is used.

**Type:** Padding &#124; [Dimension](arkts-arkui-dimension-t.md)

**Default:** 0

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
