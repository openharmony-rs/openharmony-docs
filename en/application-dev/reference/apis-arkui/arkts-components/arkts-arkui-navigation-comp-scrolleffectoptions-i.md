# ScrollEffectOptions

```TypeScript
declare interface ScrollEffectOptions
```

Provides the scroll blur effect options of the title bar.

> **NOTE:** 
> 
> - If **backgroundColor** in [NavigationTitleOptions](arkts-arkui-navigation-comp-navigationtitleoptions-i.md) is also set, the scroll blur effect will be overridden by the background color of the title bar.

**Since:** 26.0.0

<!--Device-unnamed-declare interface ScrollEffectOptions--><!--Device-unnamed-declare interface ScrollEffectOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## blurEffectiveEndOffset

```TypeScript
blurEffectiveEndOffset?: LengthMetrics
```

Maximum sliding distance for the title bar to reach the final blur style. When the sliding distance reaches this value, the blur effect reaches the final state.

The maximum sliding distance cannot be set using [LengthMetrics.percent](../arkts-apis/arkts-arkui-graphics-lengthmetrics-c.md#percent).

Default value: **8vp**

**Type:** LengthMetrics

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ScrollEffectOptions-blurEffectiveEndOffset?: LengthMetrics--><!--Device-ScrollEffectOptions-blurEffectiveEndOffset?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## blurEffectiveStartOffset

```TypeScript
blurEffectiveStartOffset?: LengthMetrics
```

Minimum sliding distance for enabling the scroll blur effect of the title bar. When the sliding distance exceeds this value, the blur effect starts to be applied.

The minimum sliding distance cannot be set using [LengthMetrics.percent](../arkts-apis/arkts-arkui-graphics-lengthmetrics-c.md#percent).

Default value: **0vp**

**Type:** LengthMetrics

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ScrollEffectOptions-blurEffectiveStartOffset?: LengthMetrics--><!--Device-ScrollEffectOptions-blurEffectiveStartOffset?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scrollEffectType

```TypeScript
scrollEffectType?: ScrollEffectType
```

Scroll blur effect type of the title bar.

Default value: **ScrollEffectType.COMMON_BLUR**.

**Type:** [ScrollEffectType](arkts-arkui-navigation-comp-scrolleffecttype-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ScrollEffectOptions-scrollEffectType?: ScrollEffectType--><!--Device-ScrollEffectOptions-scrollEffectType?: ScrollEffectType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
