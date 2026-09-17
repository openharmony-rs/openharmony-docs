# SegmentButtonOptions


> **NOTE:** 
> 
> The component does not support custom font type settings.

Provides initial data and custom properties for the **SegmentButton** component.

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

Creates a **SegmentButtonOptions** object specifically for capsule-style segmented buttons.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [CapsuleSegmentButtonConstructionOptions](arkts-arkui-arkui-advanced-segmentbutton-capsulesegmentbuttonconstructionoptions-i.md) | Yes | Configuration options for capsule-style segmented buttons. |

**Return value:**

| Type | Description |
| --- | --- |
| [SegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonoptions-c.md) | Options of the **SegmentButton** component. |

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
| options | [TabSegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-tabsegmentbuttonoptions-i.md) &#124; [CapsuleSegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-capsulesegmentbuttonoptions-i.md) | Yes | Configuration options for tab-style or capsule-style segmented buttons. |

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
| options | [TabSegmentButtonConstructionOptions](arkts-arkui-arkui-advanced-segmentbutton-tabsegmentbuttonconstructionoptions-i.md) | Yes | Configuration options for tab-style segmented buttons. |

**Return value:**

| Type | Description |
| --- | --- |
| [SegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonoptions-c.md) | Options of the **SegmentButton** component. |

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle: BlurStyle
```

Background blur style of the component.

If the value is **undefined**, it defaults to **BlurStyle.NONE**.

**Type:** [BlurStyle](../arkts-components/arkts-arkui-blurstyle-e.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundBorderRadius

```TypeScript
backgroundBorderRadius?: LengthMetrics
```

Container border radius.

**NOTE:** 

This attribute takes effect only when **borderRadiusMode** is set to **BorderRadiusMode.CUSTOM**.

For capsule-style multi-selection segmented buttons (with **type** being **"capsule"** and **multiply** being **true**), this attribute does not take effect and **itemBorderRadius** must be used to set the border radius.

The maximum value for the border radius is half of the component's width or height, and percentage values are not supported.

Default value: **&#36;r('sys.float.segmentbutton_container_shape')**

If the value is **undefined**, the default value is used.

**Type:** LengthMetrics

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor: ResourceColor
```

Background color of the component.

If the value is **undefined**, the background color is &#36;r('sys.color.ohos_id_color_button_normal').

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundSystemMaterial

```TypeScript
backgroundSystemMaterial?: uiMaterial.Material
```

Set system-styled materials for the component. Different materials have different effects, which can influence the backgroundColor, border, shadow, and other visual attributes of the component.

**Type:** [uiMaterial.Material](arkts-arkui-uimaterial-material-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderRadiusMode

```TypeScript
borderRadiusMode?: BorderRadiusMode
```

Border radius mode, used to control the border radius calculation method.

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
buttonPadding: Padding | Dimension
```

Button padding of the component.

When the value is **undefined**, the button padding settings are as follows:

Icon button and text button: **{ top: 4, right: 8, bottom: 4, left: 8 }**.

Icon + text button: **{ top: 6, right: 8, bottom: 6, left: 8 }**.

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

Button information of the component, including the icon and text.

**Type:** [SegmentButtonItemOptionsArray](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonitemoptionsarray-c.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: Direction
```

Layout direction of the component.

Default value: **Direction.Auto**

If the value is **undefined**, the default value is used.

**Type:** [Direction](arkts-arkui-direction-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor: ResourceColor
```

Text color of the unselected button.

If the value is **undefined**, the color is &#36;r('sys.color.ohos_id_color_text_secondary').

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize: DimensionNoPercentage
```

Font size of the unselected button. The value cannot be set in percentage.

If the value is **undefined**, the font size is &#36;r('sys.float.ohos_id_text_size_body2').

**Type:** [DimensionNoPercentage](arkts-arkui-dimensionnopercentage-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontWeight

```TypeScript
fontWeight: FontWeight
```

Font weight of the unselected button.

If the value is **undefined**, the font weight is **FontWeight.Regular**.

**Type:** [FontWeight](arkts-arkui-fontweight-e.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## imageSize

```TypeScript
imageSize: SizeOptions
```

Image size of the component.

When the value is **undefined**, the image size is { width: 24, height: 24 }.

Unit: vp

**NOTE:** 

The **imageSize** property takes effect only for icon-only and icon-with-text buttons.

**Type:** [SizeOptions](arkts-arkui-sizeoptions-i.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemBorderRadius

```TypeScript
itemBorderRadius?: LengthMetrics
```

Individual button border radius.

**NOTE:** 

This attribute takes effect only when **borderRadiusMode** is set to **BorderRadiusMode.CUSTOM**.

For capsule-style multi-selection segmented buttons (with **type** being **"capsule"** and **multiply** being **true**), this attribute only affects end items.

The maximum value for the border radius is half of the component's width or height, and percentage values are not supported.

Default value: **&#36;r('sys.float.segmentbutton_selected_background_shape')**

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

Button padding of the component.

Default value:

Icon button and text button: **{ top: LengthMetrics.vp(4), end: LengthMetrics.vp(8), bottom: LengthMetrics.vp(4), start: LengthMetrics.vp(8) }**.

Icon + text button: **{ top: LengthMetrics.vp(6), end: LengthMetrics.vp(8), bottom: LengthMetrics.vp(6), start: LengthMetrics.vp(8) **}.

If the value is **undefined**, the default value is used.

**Type:** [LocalizedPadding](arkts-arkui-localizedpadding-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## localizedTextPadding

```TypeScript
localizedTextPadding?: LocalizedPadding
```

Text padding.

Default value: **0**

If the value is **undefined**, the default value is used.

**Type:** [LocalizedPadding](arkts-arkui-localizedpadding-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## multiply

```TypeScript
multiply: boolean
```

Whether multiple items can be selected.

**true**: Multiple items can be selected.

**false**: Multiple items cannot be selected. For the **SegmentButton** component consisting of tab-style buttons, only one item can be selected. In this case, setting **multiply** to **true** does not take effect.

If the value is **undefined**, the component does not support selection of multiple items.

**Type:** boolean

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedBackgroundColor

```TypeScript
selectedBackgroundColor: ResourceColor
```

Background color of the selected button.

When the value is **undefined** and **type** is **"tab"**, the background color is **&#36;r('sys.color.segment_button_checked_foreground_color')**.

When **type** is **"capsule"**, the background color is **&#36;r('sys.color.ohos_id_color_emphasize')**.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedFontColor

```TypeScript
selectedFontColor: ResourceColor
```

Text color of the selected button.

If the value is **undefined**, the color is &#36;r('sys.color.ohos_id_color_text_primary') when type is set to **"tab"**.

When type is set to **"capsule"**, the color is &#36;r('sys.color.ohos_id_color_foreground_contrary').

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedFontSize

```TypeScript
selectedFontSize: DimensionNoPercentage
```

Font size of the selected button. The value cannot be set in percentage.

If the value is **undefined**, the font size is &#36;r('sys.float.ohos_id_text_size_body2').

**Type:** [DimensionNoPercentage](arkts-arkui-dimensionnopercentage-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedFontWeight

```TypeScript
selectedFontWeight: FontWeight
```

Font weight of the selected button.

If the value is **undefined**, the font weight is **FontWeight.Medium**.

**Type:** [FontWeight](arkts-arkui-fontweight-e.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textPadding

```TypeScript
textPadding: Padding | Dimension
```

Text padding of the component.

When the value is **undefined**, the text padding is 0.

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

Type of the **SegmentButton** component.

**NOTE:** 

**"tab"**: tab-style segmented buttons, designed for page or content section switching.

**"capsule"**: capsule-style segmented buttons, suitable for single or multiple selection scenarios.

**Type:** "tab" &#124; "capsule"

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
