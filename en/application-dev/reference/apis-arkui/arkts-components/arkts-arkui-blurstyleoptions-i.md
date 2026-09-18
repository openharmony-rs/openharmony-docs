# BlurStyleOptions

Defines the options of blurStyle

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## adaptiveColor

```TypeScript
adaptiveColor?: AdaptiveColor
```

Adaptive color mode.

Default value: **AdaptiveColor.DEFAULT**

**Type:** [AdaptiveColor](arkts-arkui-adaptivecolor-e.md)

**Default:** AdaptiveColor.DEFAULT

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## blurOptions

```TypeScript
blurOptions?: BlurOptions
```

Grayscale blur parameters.

Default value: **grayscale: [0,0]**

**Type:** [BlurOptions](arkts-arkui-bluroptions-i.md)

**Default:** { grayScale: [0,0] }

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## colorMode

```TypeScript
colorMode?: ThemeColorMode
```

Color mode used for the foreground blur.

Default value: **ThemeColorMode.SYSTEM**

**Type:** [ThemeColorMode](arkts-arkui-themecolormode-e.md)

**Default:** ThemeColorMode.SYSTEM

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scale

```TypeScript
scale?: number
```

Foreground blur scale.

Default value: **1.0**

Value range: [0.0, 1.0]

**1.0** indicates the highest blur degree.

**0.0** indicates the lowest blur degree.

**Type:** number

**Default:** 1.0

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
