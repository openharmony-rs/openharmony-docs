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

Anchor point coordinates of the motion blur. They must be consistent with the anchor point (centerX/centerY) of the animation [scale](arkts-arkui-common-comp-commonmethod-c.md#scale1) attribute; otherwise, unexpected effects may occur.

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

Blur radius, in vp. The value range is [0.0, +∞). A value not greater than 1.0 is recommended for a better visual effect. A negative value is automatically corrected to 0.0, and a value greater than the recommended 1.0 may cause unexpected effects.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MotionBlurOptions-radius: number--><!--Device-MotionBlurOptions-radius: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
