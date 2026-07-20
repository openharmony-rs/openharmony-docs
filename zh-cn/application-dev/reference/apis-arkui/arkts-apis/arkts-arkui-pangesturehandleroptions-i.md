# PanGestureHandlerOptions

滑动手势处理器配置参数。继承自[BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md)。

**继承/实现关系：** PanGestureHandlerOptions extends [BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md)

**起始版本：** 12

<!--Device-unnamed-interface PanGestureHandlerOptions extends BaseHandlerOptions--><!--Device-unnamed-interface PanGestureHandlerOptions extends BaseHandlerOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: PanDirection
```

用于指定触发拖动的手势方向，此枚举值支持逻辑与(&)和逻辑或（|）运算。

默认值：PanDirection.All

**类型：** PanDirection

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PanGestureHandlerOptions-direction?: PanDirection--><!--Device-PanGestureHandlerOptions-direction?: PanDirection-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## distance

```TypeScript
distance?: number
```

用于指定触发滑动手势事件的最小拖动距离，单位为vp。

手写笔默认值：8，其余输入源默认值：5

**说明：**

[Tabs组件](../arkts-components/arkts-arkui-tabs.md)滑动与该滑动手势事件同时存在时，可将distance值设为1，使拖动更灵敏，避免造成事件错乱。

取值范围：[0, +∞)，当设定的值小于0时，按默认值处理。

从API version 19开始，手写笔默认值为8，单位为vp。

使用[gestureModifier](../arkts-components/arkts-arkui-commonmethod-c.md#gesturemodifier-1)配置该字段时，单位为px。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PanGestureHandlerOptions-distance?: number--><!--Device-PanGestureHandlerOptions-distance?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## distanceMap

```TypeScript
distanceMap?: Map<SourceTool, number>
```

用于指定不同输入源触发滑动手势事件的最小拖动距离，单位为vp。

手写笔默认值：8，其余输入源默认值：5

取值范围：[0, +∞)，当设定的值小于0时，按默认值处理。

**类型：** Map&lt;SourceTool, number&gt;

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PanGestureHandlerOptions-distanceMap?: Map<SourceTool, number>--><!--Device-PanGestureHandlerOptions-distanceMap?: Map<SourceTool, number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fingers

```TypeScript
fingers?: number
```

用于指定触发拖动的最少手指数，最小为1指， 最大取值为10指。

默认值：1

取值范围：[1, 10]

**说明：**

当设置的值小于1或不设置时，会被转化为默认值。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PanGestureHandlerOptions-fingers?: number--><!--Device-PanGestureHandlerOptions-fingers?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

