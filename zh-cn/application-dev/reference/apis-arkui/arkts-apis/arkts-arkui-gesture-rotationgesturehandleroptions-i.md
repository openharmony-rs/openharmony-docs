# RotationGestureHandlerOptions

旋转手势处理器配置参数。继承自[BaseHandlerOptions](arkts-arkui-gesture-basehandleroptions-i.md)。

**继承/实现关系：** RotationGestureHandlerOptions extends [BaseHandlerOptions](arkts-arkui-gesture-basehandleroptions-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface RotationGestureHandlerOptions--><!--Device-unnamed-export interface RotationGestureHandlerOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## angle

```TypeScript
angle?: double
```

触发旋转手势的最小改变度数，单位为deg。 默认值：1 **说明：** 当改变度数的值小于等于0或大于360时，会被转化为默认值。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RotationGestureHandlerOptions-angle?: double--><!--Device-RotationGestureHandlerOptions-angle?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fingers

```TypeScript
fingers?: int
```

触发旋转的最少手指数，最小为2指，最大为5指。 默认值：2 取值范围：[2, 5] 触发手势时手指数量可以多于fingers参数值，但仅最先落下的两指参与手势计算。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RotationGestureHandlerOptions-fingers?: int--><!--Device-RotationGestureHandlerOptions-fingers?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

