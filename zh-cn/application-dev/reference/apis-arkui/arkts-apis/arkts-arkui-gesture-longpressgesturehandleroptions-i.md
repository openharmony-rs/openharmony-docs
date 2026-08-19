# LongPressGestureHandlerOptions

长按手势处理器配置参数。继承自[BaseHandlerOptions](arkts-arkui-gesture-basehandleroptions-i.md)。

**继承/实现关系：** LongPressGestureHandlerOptions extends [BaseHandlerOptions](arkts-arkui-gesture-basehandleroptions-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface LongPressGestureHandlerOptions--><!--Device-unnamed-export interface LongPressGestureHandlerOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## allowableMovement

```TypeScript
allowableMovement?: double
```

长按手势识别器识别的手势的最大移动距离，单位为px。 默认值：15 取值范围：(0, +∞)，设置小于等于0时，按照默认值15处理。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LongPressGestureHandlerOptions-allowableMovement?: double--><!--Device-LongPressGestureHandlerOptions-allowableMovement?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration?: int
```

触发长按的最短时间，单位为毫秒（ms）。 默认值：500 **说明：** 取值范围：[0, +∞)，设置小于等于0时，按照默认值500处理。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LongPressGestureHandlerOptions-duration?: int--><!--Device-LongPressGestureHandlerOptions-duration?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fingers

```TypeScript
fingers?: int
```

触发长按的最少手指数，最小为1指， 最大取值为10指。 默认值：1 取值范围：[1, 10] **说明：** 手指按下后若发生超过15px的移动，则判定当前长按手势识别失败。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LongPressGestureHandlerOptions-fingers?: int--><!--Device-LongPressGestureHandlerOptions-fingers?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## repeat

```TypeScript
repeat?: boolean
```

是否连续触发事件回调。true表示为连续触发事件回调，false表示不连续触发事件回调。 默认值：false

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LongPressGestureHandlerOptions-repeat?: boolean--><!--Device-LongPressGestureHandlerOptions-repeat?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

