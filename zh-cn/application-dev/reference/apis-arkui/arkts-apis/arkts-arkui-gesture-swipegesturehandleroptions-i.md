# SwipeGestureHandlerOptions

快滑手势处理器配置参数。继承自[BaseHandlerOptions](arkts-arkui-gesture-basehandleroptions-i.md#BaseHandlerOptions)。

**继承/实现关系：** SwipeGestureHandlerOptions extends [BaseHandlerOptions](arkts-arkui-gesture-basehandleroptions-i.md#BaseHandlerOptions)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface SwipeGestureHandlerOptions--><!--Device-unnamed-export interface SwipeGestureHandlerOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: SwipeDirection
```

触发快滑手势的滑动方向。 默认值：SwipeDirection.All

**类型：** [SwipeDirection](arkts-arkui-gesture-swipedirection-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwipeGestureHandlerOptions-direction?: SwipeDirection--><!--Device-SwipeGestureHandlerOptions-direction?: SwipeDirection-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fingers

```TypeScript
fingers?: int
```

触发快滑的最少手指数，默认为1，最小为1指，最大为10指。 默认值：1 取值范围：[1, 10]

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwipeGestureHandlerOptions-fingers?: int--><!--Device-SwipeGestureHandlerOptions-fingers?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## speed

```TypeScript
speed?: double
```

识别快滑的最小速度。 默认值：100VP/s **说明：** 当滑动速度的值小于等于0时，会被转化为默认值。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwipeGestureHandlerOptions-speed?: double--><!--Device-SwipeGestureHandlerOptions-speed?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

