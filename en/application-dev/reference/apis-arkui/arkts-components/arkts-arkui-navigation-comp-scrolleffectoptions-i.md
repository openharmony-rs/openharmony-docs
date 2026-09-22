# ScrollEffectOptions

```TypeScript
declare interface ScrollEffectOptions
```

Defines the scroll effect options for the title bar.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## blurEffectiveEndOffset

```TypeScript
blurEffectiveEndOffset?: LengthMetrics
```

The maximum sliding distance of the content area to enable the final blur style of the title bar. Default value: 8vp.

**Type:** LengthMetrics

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## blurEffectiveStartOffset

```TypeScript
blurEffectiveStartOffset?: LengthMetrics
```

The minimum sliding distance of the content area to enable the title bar sliding blur effect. Default value: 0vp.

**Type:** LengthMetrics

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scrollEffectType

```TypeScript
scrollEffectType?: ScrollEffectType
```

Title bar scroll blur style. Default value: ScrollEffectType.COMMON_BLUR.

**Type:** [ScrollEffectType](arkts-arkui-navigation-comp-scrolleffecttype-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
