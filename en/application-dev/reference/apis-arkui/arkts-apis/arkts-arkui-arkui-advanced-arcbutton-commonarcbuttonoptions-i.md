# CommonArcButtonOptions

Defines the default or custom style parameters for the **ArcButton** component.

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## Modules to Import

```TypeScript
import { ArcButton, ArcButtonOptions, ArcButtonProgressConfig, ArcButtonPosition, ArcButtonStyleMode, ArcButtonStatus } from '@kit.ArkUI';
```

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

Background blur style of the arc button.

Default value: **BlurStyle.NONE**

**Type:** [BlurStyle](../arkts-components/arkts-arkui-blurstyle-e.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## backgroundColor

```TypeScript
backgroundColor?: ColorMetrics
```

Background color of the arc button.

This property takes effect only when **ArcButtonStyleMode** is set to **CUSTOM**.

Default value: **Color.Black**

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## fontColor

```TypeScript
fontColor?: ColorMetrics
```

Font color of the arc button.

This property takes effect only when **ArcButtonStyleMode** is set to **CUSTOM**.

Default value: **Color.White**

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## fontFamily

```TypeScript
fontFamily?: string | Resource
```

Font family of the arc button.

**Type:** string &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## fontMargin

```TypeScript
fontMargin?: LocalizedMargin
```

Margin of the arc button text.

Default value: **{start:24vp, top: 10vp,end: 24vp, bottom:16vp }**

**Type:** [LocalizedMargin](arkts-arkui-localizedmargin-t.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## fontSize

```TypeScript
fontSize?: LengthMetrics
```

Font size of the arc button.

Default value: **19fp**

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## fontStyle

```TypeScript
fontStyle?: FontStyle
```

Font style of the arc button.

Default value: **FontStyle.Normal**

**Type:** [FontStyle](arkts-arkui-fontstyle-e.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## label

```TypeScript
label?: ResourceStr
```

Text displayed on the arc button.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## onClick

```TypeScript
onClick?: Callback<ClickEvent>
```

Callback triggered by click actions on the arc button.

**Type:** Callback&lt;[ClickEvent](../arkts-components/arkts-arkui-clickevent-i.md)&gt;

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## onTouch

```TypeScript
onTouch?: Callback<TouchEvent>
```

Callback triggered by touch actions on the arc button.

**Type:** Callback&lt;[TouchEvent](../arkts-components/arkts-arkui-touchevent-i.md)&gt;

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## position

```TypeScript
position?: ArcButtonPosition
```

Type of the arc button.

Default value: **ArcButtonPosition.BOTTOM_EDGE**

**Type:** [ArcButtonPosition](arkts-arkui-arkui-advanced-arcbutton-arcbuttonposition-e.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## pressedFontColor

```TypeScript
pressedFontColor?: ColorMetrics
```

Font color of the arc button when pressed.

This property takes effect only when **ArcButtonStyleMode** is set to **CUSTOM**.

Default value: **Color.White**

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## progressConfig

```TypeScript
progressConfig?: ArcButtonProgressConfig
```

Parameters for the progress indicator of the **ArcButton** component. If this property is not set, the **ArcButton** component is displayed as a button (see [Example 1](../../../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-ArcButton.md#example-1-setting-an-arc-button)). If this property is set, the component is displayed as a progress indicator (see [Example 2](../../../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-ArcButton.md#example-2-setting-a-device-progress-indicator-button)). The progress indicator style is not affected by the settings of the [ArcButtonStyleMode](arkts-arkui-arkui-advanced-arcbutton-arcbuttonstylemode-e.md) attribute.

Default value: default values of all properties of [ArcButtonProgressConfig](arkts-arkui-arkui-advanced-arcbutton-arcbuttonprogressconfig-c.md)

**Type:** [ArcButtonProgressConfig](arkts-arkui-arkui-advanced-arcbutton-arcbuttonprogressconfig-c.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## shadowColor

```TypeScript
shadowColor?: ColorMetrics
```

Shadow color of the arc button.

Default value: **Color.Black**

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## shadowEnabled

```TypeScript
shadowEnabled?: boolean
```

Whether to enable the shadow for the arc button.

Default value: **false**

The value **true** means to enable the shadow, and **false** means the opposite.

**Type:** boolean

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## status

```TypeScript
status?: ArcButtonStatus
```

Status of the arc button.

Default value: **ArcButtonStatus.NORMAL**

**Type:** [ArcButtonStatus](arkts-arkui-arkui-advanced-arcbutton-arcbuttonstatus-e.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## styleMode

```TypeScript
styleMode?: ArcButtonStyleMode
```

Style mode for the arc button. This style cannot be used together with the [ArcButtonProgressConfig](arkts-arkui-arkui-advanced-arcbutton-arcbuttonprogressconfig-c.md) style.

Default value: **ArcButtonStyleMode.EMPHASIZED_LIGHT**

**Type:** [ArcButtonStyleMode](arkts-arkui-arkui-advanced-arcbutton-arcbuttonstylemode-e.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle
