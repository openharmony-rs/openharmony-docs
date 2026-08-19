# MotionBlurOptions

Define motion blur options.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface MotionBlurOptions--><!--Device-unnamed-export declare interface MotionBlurOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## anchor

```TypeScript
anchor: MotionBlurAnchor | undefined
```

Define motion blur anchor coordinates. Undefined value means default MotionBlurAnchor.

**类型：** [MotionBlurAnchor](arkts-na-common-motionbluranchor-i.md) \| undefined

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MotionBlurOptions-anchor: MotionBlurAnchor | undefined--><!--Device-MotionBlurOptions-anchor: MotionBlurAnchor | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius: double | undefined
```

Define the size of motion blur radius.The range of this value is [0.0, ∞). Undefined value means 0.0.

**类型：** double \| undefined

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MotionBlurOptions-radius: double | undefined--><!--Device-MotionBlurOptions-radius: double | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

