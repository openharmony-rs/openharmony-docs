# PinchGestureHandlerOptions

捏合手势处理器配置参数。继承自[BaseHandlerOptions](arkts-arkui-gesture-basehandleroptions-i.md)。

**继承/实现关系：** PinchGestureHandlerOptions extends [BaseHandlerOptions](arkts-arkui-gesture-basehandleroptions-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface PinchGestureHandlerOptions--><!--Device-unnamed-export interface PinchGestureHandlerOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## distance

```TypeScript
distance?: double
```

最小识别距离，单位为vp。 默认值：5 **说明：** 当识别距离的值小于等于0时，会被转化为默认值。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PinchGestureHandlerOptions-distance?: double--><!--Device-PinchGestureHandlerOptions-distance?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fingers

```TypeScript
fingers?: int
```

触发捏合的最少手指数，最小为2指，最大为5指。 默认值：2 取值范围：[2, 5] 触发手势手指可以多于fingers数目，但只有先落下的与fingers相同数目的手指参与手势计算。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PinchGestureHandlerOptions-fingers?: int--><!--Device-PinchGestureHandlerOptions-fingers?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

