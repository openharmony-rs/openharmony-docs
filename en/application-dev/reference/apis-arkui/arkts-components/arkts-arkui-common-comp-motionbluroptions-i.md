# MotionBlurOptions

```TypeScript
declare interface MotionBlurOptions
```

Defines motion blur options.

**Since:** 12

<!--Device-unnamed-declare interface MotionBlurOptions--><!--Device-unnamed-declare interface MotionBlurOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## anchor

```TypeScript
anchor: MotionBlurAnchor
```

Coordinates of the motion blur anchor. They must be the same as those of the animation scaling anchor.

**Type:** [MotionBlurAnchor](arkts-arkui-common-comp-motionbluranchor-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MotionBlurOptions-anchor: MotionBlurAnchor--><!--Device-MotionBlurOptions-anchor: MotionBlurAnchor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius: number
```

Blur radius. The value range is [0.0, ∞). You are advised to set it to a value less than 1.0.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MotionBlurOptions-radius: number--><!--Device-MotionBlurOptions-radius: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
