# SegmentButtonOptions

```TypeScript
declare class SegmentButtonOptions
```


> **NOTE:** 
> 
> The component does not support custom font type settings.

Provides initial data and custom properties for the **SegmentButton** component.

> **NOTE:** 
> 
> Starting from API version 26.0.0, except for capsule-style multi-select buttons (where type is **"capsule"** and
> **multiply** is **true**), when **backgroundSystemMaterial** is set to a system material with automatic color
> inversion, **fontColor** and **selectedFontColor** use special system resources that support color inversion, and
> the colors automatically adapt to the inverted material background color.

**Since:** 11

**Decorator:** @Observed

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { SegmentButton, SegmentButtonOptions, SegmentButtonItemOptionsArray, TabSegmentButtonOptions, TabSegmentButtonConstructionOptions, CapsuleSegmentButtonOptions, CapsuleSegmentButtonConstructionOptions, SegmentButtonTextItem, SegmentButtonIconItem, SegmentButtonIconTextItem, DimensionNoPercentage, CommonSegmentButtonOptions, ItemRestriction, SegmentButtonItemTuple, SegmentButtonItemArray, SegmentButtonItemOptionsConstructorOptions, SegmentButtonItemOptions, BorderRadiusMode } from '@kit.ArkUI';
```

## capsule

```TypeScript
static capsule(options: CapsuleSegmentButtonConstructionOptions): SegmentButtonOptions
```

Creates a capsule-style **SegmentButtonOptions** instance, which is used to define capsule-style segment buttons.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [CapsuleSegmentButtonConstructionOptions](arkts-arkui-arkui-advanced-segmentbutton-capsulesegmentbuttonconstructionoptions-i.md) | Yes | Configuration options for capsule-style segment buttons. |

**Return value:**

| Type | Description |
| --- | --- |
| [SegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonoptions-c.md) | Segment button options for the capsule type. |

## constructor

```TypeScript
constructor(options: TabSegmentButtonOptions | CapsuleSegmentButtonOptions)
```

Constructor.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [TabSegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-tabsegmentbuttonoptions-i.md) &#124; [CapsuleSegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-capsulesegmentbuttonoptions-i.md) | Yes | Configuration options for tab-style or capsule-style segment buttons. |

## tab

```TypeScript
static tab(options: TabSegmentButtonConstructionOptions): SegmentButtonOptions
```

Creates a SegmentButtonOptions class to define tabs.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [TabSegmentButtonConstructionOptions](arkts-arkui-arkui-advanced-segmentbutton-tabsegmentbuttonconstructionoptions-i.md) | Yes | Configuration options for tab-style segment buttons. |

**Return value:**

| Type | Description |
| --- | --- |
| [SegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonoptions-c.md) | Options of the segment button, used to define a tab-type segment button. |

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle: BlurStyle
```

Background blur material of the segment button component.

Default value: **BlurStyle.NONE**

When the value is **undefined**, the default value is used.

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

This attribute takes effect only when **borderRadiusMode** is **BorderRadiusMode.CUSTOM**.

For capsule-type multi-selection segment buttons (**type** is **"capsule"** and **multiply** is **true**), this attribute does not take effect. Use **itemBorderRadius** to configure the corner radius instead.

The corner radius is limited by the component size. The maximum value is half of the component width or height. Percentage setting is not supported. When the value exceeds the maximum, it is automatically corrected to the maximum. When a percentage is used, the default value is used.

Default value: `$r('sys.float.segmentbutton_container_shape')`

When the value is **undefined**, the default value is used.

**Type:** LengthMetrics

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor: ResourceColor
```

Background color of the segment button component.

When the value is **undefined**, the background color is **$r('sys.color.ohos_id_color_button_normal')**.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundSystemMaterial

```TypeScript
backgroundSystemMaterial?: uiMaterial.Material
```

System material of the background of the segment button component. Different system materials have different properties and produce different effects. After a material is passed in, the animation effect of **SegmentButton** changes.

For capsule-type multi-selection segment buttons (**type** is **"capsule"** and **multiply** is **true**), this attribute does not take effect.

Default value: no material effect.

**Type:** [uiMaterial.Material](arkts-arkui-uimaterial-material-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderRadiusMode

```TypeScript
borderRadiusMode?: BorderRadiusMode
```

Border radius mode, which controls how the corner radius is calculated.

Default value: **BorderRadiusMode.DEFAULT**

When the value is **undefined**, the default value is used.

**Type:** [BorderRadiusMode](arkts-arkui-arkui-advanced-segmentbutton-borderradiusmode-e.md)

**Default:** BorderRadiusMode.Default

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## buttonPadding

```TypeScript
buttonPadding: Padding | Dimension
```

Button padding of the segment button component.

When the value is **undefined**, the padding for icon-only buttons and text-only buttons is: `{ top: 4, right: 8, bottom: 4, left: 8 }`

The padding for icon + text buttons is: `{ top: 6, right: 8, bottom: 6, left: 8 }`

Unit: vp

**Type:** Padding &#124; [Dimension](arkts-arkui-dimension-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## buttons

```TypeScript
buttons: SegmentButtonItemOptionsArray
```

Button information of the segment button component, including icon and text information.

**Type:** [SegmentButtonItemOptionsArray](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonitemoptionsarray-c.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: Direction
```

Layout direction of the segment button component.

Default value: **Direction.Auto**

When the value is **undefined**, the default value is used.

**Type:** [Direction](arkts-arkui-direction-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor: ResourceColor
```

Text color of the segment button component in the unselected state.

When the value is **undefined**, the color is **$r('sys.color.ohos_id_color_text_secondary')**.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize: DimensionNoPercentage
```

Font size of the segment button component in the unselected state. Percentage setting is not supported.

Unit: fp

When the value is **undefined**, the font size is **$r('sys.float.ohos_id_text_size_body2')**.

**Type:** [DimensionNoPercentage](arkts-arkui-dimensionnopercentage-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontWeight

```TypeScript
fontWeight: FontWeight
```

Font weight of the segment button component in the unselected state.

When the value is **undefined**, the font weight is **FontWeight.Regular**.

**Type:** [FontWeight](arkts-arkui-fontweight-e.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## imageSize

```TypeScript
imageSize: SizeOptions
```

Image size of the segment button component.

When the value is **undefined**, the image size is **{ width: 24, height: 24 }**.

Unit: vp

**NOTE:** 

The `imageSize` attribute takes effect only for icon-only buttons and icon + text buttons, and has no effect on text-only buttons.

**Type:** [SizeOptions](arkts-arkui-sizeoptions-i.md)

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

This attribute takes effect only when **borderRadiusMode** is **BorderRadiusMode.CUSTOM**.

For capsule-type multi-selection segment buttons (**type** is **"capsule"** and **multiply** is **true**), only the corner radius of the items at both ends can be controlled.

The corner radius is limited by the component size. The maximum value is half of the component width or height. Percentage setting is not supported. When the value exceeds the maximum, it is automatically corrected to the maximum. When a percentage is used, the default value is used.

Default value: `$r('sys.float.segmentbutton_selected_background_shape')`

When the value is **undefined**, the default value is used.

**Type:** LengthMetrics

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## localizedButtonPadding

```TypeScript
localizedButtonPadding?: LocalizedPadding
```

Button padding of the segment button component, which supports adaptation to the layout direction (LTR/RTL).

Default value:

For icon-only buttons and text-only buttons: `{ top: LengthMetrics.vp(4), end: LengthMetrics.vp(8), bottom: LengthMetrics.vp(4), start: LengthMetrics.vp(8) }`

For icon + text buttons: `{ top: LengthMetrics.vp(6), end: LengthMetrics.vp(8), bottom: LengthMetrics.vp(6), start: LengthMetrics.vp(8) }`

When the value is **undefined**, the default value is used.

**Type:** [LocalizedPadding](arkts-arkui-localizedpadding-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## localizedTextPadding

```TypeScript
localizedTextPadding?: LocalizedPadding
```

Text padding, which supports adaptation to the layout direction (LTR/RTL).

Default value: **0**

Unit: vp

When the value is **undefined**, the default value is used.

**Type:** [LocalizedPadding](arkts-arkui-localizedpadding-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## multiply

```TypeScript
multiply: boolean
```

Whether the segment button component supports multi-selection.

**true**: multi-selection is supported; **false**: multi-selection is not supported.

For tab-type segment buttons (type is **"tab"**), **multiply** is forcibly set to **false**, and setting it to **true** does not take effect.

Default value: **false**

When the value is **undefined**, the default value is used.

**Type:** boolean

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedBackgroundColor

```TypeScript
selectedBackgroundColor: ResourceColor
```

Background color of the segment button component in the selected state.

When the value is **undefined** and type is **"tab"**, the background color is `$r('sys.color.segment_button_checked_foreground_color')`.

When type is **"capsule"**, the background color is `$r('sys.color.ohos_id_color_emphasize')`.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedFontColor

```TypeScript
selectedFontColor: ResourceColor
```

Text color of the segment button component in the selected state.

When the value is **undefined** and **type** is **"tab"**, the color is `$r('sys.color.ohos_id_color_text_primary')`.

When **type** is **"capsule"**, the color is `$r('sys.color.ohos_id_color_foreground_contrary')`.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedFontSize

```TypeScript
selectedFontSize: DimensionNoPercentage
```

Font size of the segment button component in the selected state. Percentage setting is not supported.

Unit: fp

When the value is **undefined**, the font size is **$r('sys.float.ohos_id_text_size_body2')**.

**Type:** [DimensionNoPercentage](arkts-arkui-dimensionnopercentage-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedFontWeight

```TypeScript
selectedFontWeight: FontWeight
```

Font weight of the segment button component in the selected state.

When the value is **undefined**, the font weight is **FontWeight.Medium**.

**Type:** [FontWeight](arkts-arkui-fontweight-e.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textPadding

```TypeScript
textPadding: Padding | Dimension
```

Text padding of the segment button component.

When the value is **undefined**, the text padding is **0**.

Unit: vp

**Type:** Padding &#124; [Dimension](arkts-arkui-dimension-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: "tab" | "capsule"
```

Type of the segment button component.

**Note:** 

**"tab"**: tab-type segment button, suitable for switching between pages or content areas.

**"capsule"**: capsule-type segment button, suitable for single-selection or multi-selection scenarios.

**Type:** "tab" &#124; "capsule"

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
