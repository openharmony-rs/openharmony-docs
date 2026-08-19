# LongPressGestureHandler

长按手势处理器对象类型。

**继承/实现关系：** LongPressGestureHandler extends [GestureHandler](arkts-arkui-gesture-gesturehandler-c.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class LongPressGestureHandler--><!--Device-unnamed-export declare class LongPressGestureHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: LongPressGestureHandlerOptions)
```

长按手势处理器的构造函数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LongPressGestureHandler-constructor(options?: LongPressGestureHandlerOptions)--><!--Device-LongPressGestureHandler-constructor(options?: LongPressGestureHandlerOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [LongPressGestureHandlerOptions](arkts-arkui-gesture-longpressgesturehandleroptions-i.md) | 否 | 长按手势处理器配置参数。 |

## onAction

```TypeScript
onAction(event: Callback<GestureEvent>): this
```

设置长按手势处理器识别成功回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LongPressGestureHandler-onAction(event: Callback<GestureEvent>): this--><!--Device-LongPressGestureHandler-onAction(event: Callback<GestureEvent>): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gesture-gestureevent-i.md)&gt; | 是 | 长按手势处理器识别成功回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前长按手势处理器对象。 |

## onActionCancel

```TypeScript
onActionCancel(event: Callback<GestureEvent>): this
```

设置长按手势处理器取消回调。长按手势处理器识别成功后，接收到触摸取消事件时触发回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LongPressGestureHandler-onActionCancel(event: Callback<GestureEvent>): this--><!--Device-LongPressGestureHandler-onActionCancel(event: Callback<GestureEvent>): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gesture-gestureevent-i.md)&gt; | 是 | 长按手势处理器取消回调。该回调会返回手势事件信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前长按手势处理器对象。 |

## onActionEnd

```TypeScript
onActionEnd(event: Callback<GestureEvent>): this
```

设置长按手势处理器结束回调。长按手势处理器识别成功后，最后一根手指抬起时触发回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LongPressGestureHandler-onActionEnd(event: Callback<GestureEvent>): this--><!--Device-LongPressGestureHandler-onActionEnd(event: Callback<GestureEvent>): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gesture-gestureevent-i.md)&gt; | 是 | 长按手势处理器结束回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前长按手势处理器对象。 |

