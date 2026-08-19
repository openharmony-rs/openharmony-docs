# PanGestureHandlerOptions

滑动手势处理器配置参数。继承自[BaseHandlerOptions](arkts-arkui-gesture-basehandleroptions-i.md)。

**继承/实现关系：** PanGestureHandlerOptions extends [BaseHandlerOptions](arkts-arkui-gesture-basehandleroptions-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface PanGestureHandlerOptions--><!--Device-unnamed-export interface PanGestureHandlerOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: PanDirection
```

用于指定触发拖动的手势方向，此枚举值支持逻辑与(&)和逻辑或（|）运算。 默认值：PanDirection.All

**类型：** [PanDirection](arkts-arkui-gesture-pandirection-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PanGestureHandlerOptions-direction?: PanDirection--><!--Device-PanGestureHandlerOptions-direction?: PanDirection-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## distance

```TypeScript
distance?: double
```

用于指定触发滑动手势事件的最小拖动距离，单位为vp。 手写笔默认值：8，其余输入源默认值：5 **说明：** Tabs组件滑动与该滑动手势事件同时存在时，可将distance值设为1，使拖动更灵敏，避免造成事件错乱。 取值范围：[0, +∞)，当设定的值小于0时，按默认值处理。 从API version 19开始，手写笔默认值为8，单位为vp。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PanGestureHandlerOptions-distance?: double--><!--Device-PanGestureHandlerOptions-distance?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## distanceMap

```TypeScript
distanceMap?: Map<SourceTool, double>
```

用于指定不同输入源触发滑动手势事件的最小拖动距离，单位为vp。 手写笔默认值：8，其余输入源默认值：5 取值范围：[0, +∞)，当设定的值小于0时，按默认值处理。

**类型：** Map&lt;[SourceTool](../arkts-components/arkts-arkui-sourcetool-e.md), double&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PanGestureHandlerOptions-distanceMap?: Map<SourceTool, double>--><!--Device-PanGestureHandlerOptions-distanceMap?: Map<SourceTool, double>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fingers

```TypeScript
fingers?: int
```

用于指定触发拖动的最少手指数，最小为1指， 最大取值为10指。 默认值：1 取值范围：[1, 10] **说明：** 当设置的值小于1或不设置时，会被转化为默认值。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PanGestureHandlerOptions-fingers?: int--><!--Device-PanGestureHandlerOptions-fingers?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

