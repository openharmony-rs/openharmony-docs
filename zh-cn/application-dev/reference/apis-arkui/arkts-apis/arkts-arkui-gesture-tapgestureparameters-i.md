# TapGestureParameters

> **说明：** > > 点击手势参数。继承自[BaseHandlerOptions](arkts-arkui-gesture-basehandleroptions-i.md)。

**继承/实现关系：** TapGestureParameters extends [BaseHandlerOptions](arkts-arkui-gesture-basehandleroptions-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface TapGestureParameters--><!--Device-unnamed-export declare interface TapGestureParameters-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## count

```TypeScript
count?: int
```

识别的连续点击次数。当设置的值小于1或不设置时，会被转化为默认值。 默认值：1 取值范围：[0, +∞) **说明：** 1. 当配置多击时，上一次的最后一根手指抬起和下一次的第一根手指按下的超时时间为300毫秒。 2. 当上次点击的位置与当前点击的位置距离超过60vp时，手势识别失败。在多指情况下，点击的位置为所有参与手势响应手指的平均位置。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TapGestureParameters-count?: int--><!--Device-TapGestureParameters-count?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## distanceThreshold

```TypeScript
distanceThreshold?: double
```

点击手势移动阈值。当设置的值小于等于0或不设置时，会被转化为默认值。 默认值：2³¹-1 单位：vp **说明：** 当手指的移动距离超出开发者预设的移动阈值时，点击识别失败。如果初始化为默认阈值时，手指移动超过组件热区范围，点击识别失败。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TapGestureParameters-distanceThreshold?: double--><!--Device-TapGestureParameters-distanceThreshold?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fingers

```TypeScript
fingers?: int
```

触发点击的手指数，最小为1指， 最大为10指。当设置小于1的值或不设置时，会被转化为默认值。 默认值：1 **说明：** 1. 当配置多指时，第一根手指按下后300毫秒内未有足够的手指数按下，手势识别失败；手指抬起时，抬起后剩余的手指数小于阈值时开始计时，如300ms内未全部抬起则手势识别失败。 2. 实际点击手指数超过配置值，手势识别成功。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TapGestureParameters-fingers?: int--><!--Device-TapGestureParameters-fingers?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

