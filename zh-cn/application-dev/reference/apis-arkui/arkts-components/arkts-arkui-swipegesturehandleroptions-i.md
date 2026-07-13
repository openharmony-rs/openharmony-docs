# SwipeGestureHandlerOptions

快滑手势处理器配置参数。继承自[BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md)。

**继承/实现关系：** SwipeGestureHandlerOptions extends [BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: SwipeDirection
```

触发快滑手势的滑动方向。

默认值：SwipeDirection.All

**类型：** SwipeDirection

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fingers

```TypeScript
fingers?: number
```

触发快滑的最少手指数，默认为1，最小为1指，最大为10指。

默认值：1

取值范围：[1, 10]

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## speed

```TypeScript
speed?: number
```

识别快滑的最小速度。

默认值：100VP/s

**说明：**

当滑动速度的值小于等于0时，会被转化为默认值。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

