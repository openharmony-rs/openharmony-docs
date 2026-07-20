# TapGestureHandlerOptions

点击手势处理器配置参数。继承自[BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md)。

**继承/实现关系：** TapGestureHandlerOptions extends [BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md)

**起始版本：** 12

<!--Device-unnamed-interface TapGestureHandlerOptions extends BaseHandlerOptions--><!--Device-unnamed-interface TapGestureHandlerOptions extends BaseHandlerOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## count

```TypeScript
count?: number
```

识别的连续点击次数。当设置的值小于1或不设置时，会被转化为默认值。

默认值：1

取值范围：[0, +∞)

**说明：**

1. 当配置多击时，上一次的最后一根手指抬起和下一次的第一根手指按下的超时时间为300毫秒。2. 当上次点击的位置与当前点击的位置距离超过60vp时，手势识别失败。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TapGestureHandlerOptions-count?: number--><!--Device-TapGestureHandlerOptions-count?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## distanceThreshold

```TypeScript
distanceThreshold?: number
```

点击手势移动阈值。当设置的值小于等于0或不设置时，会被转化为默认值。

默认值：2^31-1

单位：vp

**说明：**

当手指的移动距离超出开发者预设的移动阈值时，点击识别失败。如果初始化为默认阈值时，手指移动超过组件热区范围，点击识别失败。

**类型：** number

**默认值：** Infinity

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-TapGestureHandlerOptions-distanceThreshold?: number--><!--Device-TapGestureHandlerOptions-distanceThreshold?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fingers

```TypeScript
fingers?: number
```

触发点击的手指数，最小为1指， 最大为10指。当设置小于1的值或不设置时，会被转化为默认值。

默认值：1

**说明：**

1. 当配置多指时，第一根手指按下后300毫秒内未有足够的手指数按下，手势识别失败，第一根手指抬起后300毫秒内未有足够的手指抬起，手势识别失败。2. 实际点击手指数超过配置值，手势识别成功。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TapGestureHandlerOptions-fingers?: number--><!--Device-TapGestureHandlerOptions-fingers?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

