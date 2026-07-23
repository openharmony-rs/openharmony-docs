# PanGestureHandler

滑动手势处理器对象类型。

**继承/实现关系：** PanGestureHandler extends [GestureHandler<PanGestureHandler>]

**起始版本：** 12

<!--Device-unnamed-declare class PanGestureHandler extends GestureHandler<PanGestureHandler>--><!--Device-unnamed-declare class PanGestureHandler extends GestureHandler<PanGestureHandler>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: PanGestureHandlerOptions)
```

滑动手势处理器的构造函数。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PanGestureHandler-constructor(options?: PanGestureHandlerOptions)--><!--Device-PanGestureHandler-constructor(options?: PanGestureHandlerOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [PanGestureHandlerOptions](arkts-arkui-gesture-pangesturehandleroptions-i.md) | 否 | 滑动手势处理器配置参数。 |

## onActionCancel

```TypeScript
onActionCancel(event: Callback<void>): PanGestureHandler
```

设置滑动手势处理器取消回调。滑动手势处理器识别成功后，接收到触摸取消事件时触发回调。不返回手势事件信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PanGestureHandler-onActionCancel(event: Callback<void>): PanGestureHandler--><!--Device-PanGestureHandler-onActionCancel(event: Callback<void>): PanGestureHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<void> | 是 | 滑动手势处理器取消回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PanGestureHandler](arkts-arkui-gesture-pangesturehandler-c.md) | 返回当前滑动手势处理器对象。 |

## onActionCancel

```TypeScript
onActionCancel(event: Callback<GestureEvent>): PanGestureHandler
```

设置滑动手势处理器取消回调。滑动手势处理器识别成功后，接收到触摸取消事件时触发回调。与[onActionCancel](arkts-arkui-gesture-pangesturehandler-c.md#onactioncancel-1)接口相比，此接口返回手势事件信息。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PanGestureHandler-onActionCancel(event: Callback<GestureEvent>): PanGestureHandler--><!--Device-PanGestureHandler-onActionCancel(event: Callback<GestureEvent>): PanGestureHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<GestureEvent> | 是 | 滑动手势处理器取消回调。返回手势事件信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PanGestureHandler](arkts-arkui-gesture-pangesturehandler-c.md) | 返回当前滑动手势处理器对象。 |

## onActionEnd

```TypeScript
onActionEnd(event: Callback<GestureEvent>): PanGestureHandler
```

设置滑动手势处理器结束回调。滑动手势处理器识别成功后，手指抬起时触发回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PanGestureHandler-onActionEnd(event: Callback<GestureEvent>): PanGestureHandler--><!--Device-PanGestureHandler-onActionEnd(event: Callback<GestureEvent>): PanGestureHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<GestureEvent> | 是 | 滑动手势处理器结束回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PanGestureHandler](arkts-arkui-gesture-pangesturehandler-c.md) | 返回当前滑动手势处理器对象。 |

## onActionStart

```TypeScript
onActionStart(event: Callback<GestureEvent>): PanGestureHandler
```

设置滑动手势处理器识别成功回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PanGestureHandler-onActionStart(event: Callback<GestureEvent>): PanGestureHandler--><!--Device-PanGestureHandler-onActionStart(event: Callback<GestureEvent>): PanGestureHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<GestureEvent> | 是 | 滑动手势处理器识别成功回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PanGestureHandler](arkts-arkui-gesture-pangesturehandler-c.md) | 返回当前滑动手势处理器对象。 |

## onActionUpdate

```TypeScript
onActionUpdate(event: Callback<GestureEvent>): PanGestureHandler
```

设置滑动手势处理器更新回调。滑动手势处理器移动过程中触发回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PanGestureHandler-onActionUpdate(event: Callback<GestureEvent>): PanGestureHandler--><!--Device-PanGestureHandler-onActionUpdate(event: Callback<GestureEvent>): PanGestureHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<GestureEvent> | 是 | 滑动手势处理器更新回调。<br/>fingerList为多根手指时，该回调监听每次只会更新一根手指的位置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PanGestureHandler](arkts-arkui-gesture-pangesturehandler-c.md) | 返回当前滑动手势处理器对象。 |

