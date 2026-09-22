# MotionBlurOptions

```TypeScript
declare interface MotionBlurOptions
```

运动模糊选项。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## anchor

```TypeScript
anchor: MotionBlurAnchor
```

运动模糊锚点坐标，需要与动画缩放[scale](arkts-arkui-common-comp-commonmethod-c.md#scale)属性的锚点（centerX/centerY）保持一致，否则会产生非预期效果。

**类型：** [MotionBlurAnchor](arkts-arkui-common-comp-motionbluranchor-i.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius: number
```

模糊半径，单位：vp，取值范围[0.0, +∞)，建议取值不超过1.0来实现较为美观的效果。传入负数时自动修正为0.0，超出建议值1.0时可能产生非预期效果。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
