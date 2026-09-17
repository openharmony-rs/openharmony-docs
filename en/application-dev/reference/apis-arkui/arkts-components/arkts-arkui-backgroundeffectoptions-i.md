# BackgroundEffectOptions

Defines the options of BackgroundEffect

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## adaptiveColor

```TypeScript
adaptiveColor?: AdaptiveColor
```

Adaptive color mode used for the background blur effect. Default value: **DEFAULT** . When set to **AVERAGE**, the adaptive color mode takes effect only when the color has transparency.

**Type:** [AdaptiveColor](arkts-arkui-adaptivecolor-e.md)

**Default:** AdaptiveColor.DEFAULT

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## blurOptions

```TypeScript
blurOptions?: BlurOptions
```

Grayscale blur.

**Type:** [BlurOptions](arkts-arkui-bluroptions-i.md)

**Default:** 
- API version 11: { grayScale: [0,1] }
- API version 12+: { grayScale: [0,0] }

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## brightness

```TypeScript
brightness?: number
```

Brightness. <br>Value range: [0, +∞). <br>Default value: **1** Recommended value range: [0, 2].

**Type:** number

**Default:** 1

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ResourceColor
```

Color.

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Default:** Color.Transparent

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## inactiveColor

```TypeScript
inactiveColor?: ResourceColor
```

Background color when the blur effect does not take effect. This parameter must be used together with the **policy** parameter. When **policy** is set to a value that disables the blur effect, the blur effect on the components is removed. If **inactiveColor** is specified, it is applied as the component background color.

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Default:** Color.Transparent

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## policy

```TypeScript
policy?: BlurStyleActivePolicy
```

Blur activation policy.

**Type:** [BlurStyleActivePolicy](arkts-arkui-blurstyleactivepolicy-e.md)

**Default:** BlurStyleActivePolicy.ALWAYS_ACTIVE

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius: number
```

Blur radius. Value range: [0, +∞). Default value: **0**.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## saturation

```TypeScript
saturation?: number
```

Saturation. Value range: [0, +∞). Recommended value range: [0, 50].

**Type:** number

**Default:** 1

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
