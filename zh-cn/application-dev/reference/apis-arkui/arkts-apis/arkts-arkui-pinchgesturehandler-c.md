# PinchGestureHandler

捏合手势处理器对象类型。

**继承/实现关系：** PinchGestureHandler extends [GestureHandler<PinchGestureHandler>](GestureHandler<PinchGestureHandler>)

**起始版本：** 12

<!--Device-unnamed-declare class PinchGestureHandler extends GestureHandler<PinchGestureHandler>--><!--Device-unnamed-declare class PinchGestureHandler extends GestureHandler<PinchGestureHandler>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="constructor"></a>
## constructor

```TypeScript
constructor(options?: PinchGestureHandlerOptions)
```

捏合手势处理器的构造函数。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PinchGestureHandler-constructor(options?: PinchGestureHandlerOptions)--><!--Device-PinchGestureHandler-constructor(options?: PinchGestureHandlerOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [PinchGestureHandlerOptions](arkts-arkui-pinchgesturehandleroptions-i.md) | 否 | 捏合手势处理器配置参数。 |

<a id="onactioncancel"></a>
## onActionCancel

```TypeScript
onActionCancel(event: Callback<void>): PinchGestureHandler
```

设置捏合手势处理器取消回调。捏合手势处理器识别成功后，接收到触摸取消事件时触发回调。不返回手势事件信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PinchGestureHandler-onActionCancel(event: Callback<void>): PinchGestureHandler--><!--Device-PinchGestureHandler-onActionCancel(event: Callback<void>): PinchGestureHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | 捏合手势处理器取消回调。不返回手势事件信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PinchGestureHandler](arkts-arkui-pinchgesturehandler-c.md) | 返回当前捏合手势处理器对象。 |

<a id="onactioncancel-1"></a>
## onActionCancel

```TypeScript
onActionCancel(event: Callback<GestureEvent>): PinchGestureHandler
```

设置捏合手势处理器取消回调。捏合手势处理器识别成功后，接收到触摸取消事件时触发回调。与[onActionCancel](arkts-arkui-pinchgesturehandler-c.md#onactioncancel-1)接口相比，此接口返回手势事件信息。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PinchGestureHandler-onActionCancel(event: Callback<GestureEvent>): PinchGestureHandler--><!--Device-PinchGestureHandler-onActionCancel(event: Callback<GestureEvent>): PinchGestureHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;GestureEvent&gt; | 是 | 捏合手势处理器取消回调。返回手势事件信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PinchGestureHandler](arkts-arkui-pinchgesturehandler-c.md) | 返回当前捏合手势处理器对象。 |

<a id="onactionend"></a>
## onActionEnd

```TypeScript
onActionEnd(event: Callback<GestureEvent>): PinchGestureHandler
```

设置捏合手势处理器结束回调。捏合手势处理器识别成功后，手指抬起时触发回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PinchGestureHandler-onActionEnd(event: Callback<GestureEvent>): PinchGestureHandler--><!--Device-PinchGestureHandler-onActionEnd(event: Callback<GestureEvent>): PinchGestureHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;GestureEvent&gt; | 是 | 捏合手势处理器结束回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PinchGestureHandler](arkts-arkui-pinchgesturehandler-c.md) | 返回当前捏合手势处理器对象。 |

<a id="onactionstart"></a>
## onActionStart

```TypeScript
onActionStart(event: Callback<GestureEvent>): PinchGestureHandler
```

设置捏合手势处理器识别成功回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PinchGestureHandler-onActionStart(event: Callback<GestureEvent>): PinchGestureHandler--><!--Device-PinchGestureHandler-onActionStart(event: Callback<GestureEvent>): PinchGestureHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;GestureEvent&gt; | 是 | 捏合手势处理器识别成功回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PinchGestureHandler](arkts-arkui-pinchgesturehandler-c.md) | 返回当前捏合手势处理器对象。 |

<a id="onactionupdate"></a>
## onActionUpdate

```TypeScript
onActionUpdate(event: Callback<GestureEvent>): PinchGestureHandler
```

设置捏合手势处理器更新回调。捏合手势处理器移动过程中触发回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PinchGestureHandler-onActionUpdate(event: Callback<GestureEvent>): PinchGestureHandler--><!--Device-PinchGestureHandler-onActionUpdate(event: Callback<GestureEvent>): PinchGestureHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;GestureEvent&gt; | 是 | 捏合手势处理器更新回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PinchGestureHandler](arkts-arkui-pinchgesturehandler-c.md) | 返回当前捏合手势处理器对象。 |

