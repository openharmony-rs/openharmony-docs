# PinchGesture

用于触发捏合手势，最少需要2指，最多5指，最小识别距离为5vp。在支持鼠标和键盘输入的设备上，通过“Ctrl+鼠标滚轮”也可以触发捏合手势。 > **说明：** > > 捏合手势触发成功后，抬起手指直至不再满足触发条件。再次满足条件时，可重新触发捏合手势。

**继承/实现关系：** PinchGesture extends [Gesture](arkts-arkui-gesture-gesture-c.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class PinchGesture--><!--Device-unnamed-export declare class PinchGesture-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## $_instantiate

```TypeScript
static $_instantiate(factory: () => PinchGesture, value?: PinchGestureHandlerOptions): PinchGesture
```

设置捏合手势事件。继承自[Gesture](arkts-arkui-gesture-gesture-c.md)。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PinchGesture-static $_instantiate(factory: () => PinchGesture, value?: PinchGestureHandlerOptions): PinchGesture--><!--Device-PinchGesture-static $_instantiate(factory: () => PinchGesture, value?: PinchGestureHandlerOptions): PinchGesture-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| factory | () =&gt; PinchGesture | 是 |  |
| value | [PinchGestureHandlerOptions](arkts-arkui-gesture-pinchgesturehandleroptions-i.md) | 否 | 捏合手势处理器配置参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PinchGesture](arkts-arkui-gesture-pinchgesture-c.md) |  |

## onActionCancel

```TypeScript
onActionCancel(event: Callback<GestureEvent>): this
```

Pinch手势识别成功并接收到触摸取消事件的回调。与[onActionCancel](#onactioncancel)相比，该回调返回手势事件信息。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PinchGesture-onActionCancel(event: Callback<GestureEvent>): this--><!--Device-PinchGesture-onActionCancel(event: Callback<GestureEvent>): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gesture-gestureevent-i.md)&gt; | 是 | 手势事件回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onActionEnd

```TypeScript
onActionEnd(event: Callback<GestureEvent>): this
```

Pinch手势识别成功，当抬起最后一根满足手势触发条件的手指后，触发回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PinchGesture-onActionEnd(event: Callback<GestureEvent>): this--><!--Device-PinchGesture-onActionEnd(event: Callback<GestureEvent>): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gesture-gestureevent-i.md)&gt; | 是 | 手势事件回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onActionStart

```TypeScript
onActionStart(event: Callback<GestureEvent>): this
```

Pinch手势识别成功后触发回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PinchGesture-onActionStart(event: Callback<GestureEvent>): this--><!--Device-PinchGesture-onActionStart(event: Callback<GestureEvent>): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gesture-gestureevent-i.md)&gt; | 是 | 手势事件回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onActionUpdate

```TypeScript
onActionUpdate(event: Callback<GestureEvent>): this
```

Pinch手势移动过程中回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PinchGesture-onActionUpdate(event: Callback<GestureEvent>): this--><!--Device-PinchGesture-onActionUpdate(event: Callback<GestureEvent>): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gesture-gestureevent-i.md)&gt; | 是 | 手势事件回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

