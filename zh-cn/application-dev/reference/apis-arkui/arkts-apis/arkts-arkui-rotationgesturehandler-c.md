# RotationGestureHandler

旋转手势处理器对象类型。

**继承/实现关系：** RotationGestureHandler extends [GestureHandler<RotationGestureHandler>]

**起始版本：** 12

<!--Device-unnamed-declare class RotationGestureHandler extends GestureHandler<RotationGestureHandler>--><!--Device-unnamed-declare class RotationGestureHandler extends GestureHandler<RotationGestureHandler>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: RotationGestureHandlerOptions)
```

旋转手势处理器的构造函数。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RotationGestureHandler-constructor(options?: RotationGestureHandlerOptions)--><!--Device-RotationGestureHandler-constructor(options?: RotationGestureHandlerOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RotationGestureHandlerOptions](arkts-arkui-rotationgesturehandleroptions-i.md) | 否 | 旋转手势处理器配置参数。 |

## onActionCancel

```TypeScript
onActionCancel(event: Callback<void>): RotationGestureHandler
```

设置旋转手势处理器取消回调。旋转手势处理器识别成功后，接收到触摸取消事件时触发回调。不返回手势事件信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RotationGestureHandler-onActionCancel(event: Callback<void>): RotationGestureHandler--><!--Device-RotationGestureHandler-onActionCancel(event: Callback<void>): RotationGestureHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | 旋转手势处理器取消回调。不返回手势事件信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RotationGestureHandler](arkts-arkui-rotationgesturehandler-c.md) | 返回当前旋转手势处理器对象。 |

## onActionCancel

```TypeScript
onActionCancel(event: Callback<GestureEvent>): RotationGestureHandler
```

设置旋转手势处理器取消回调。旋转手势处理器识别成功后，接收到触摸取消事件时触发回调。与[onActionCancel](arkts-arkui-rotationgesturehandler-c.md#onactioncancel)相比，此接口返回手势事件信息。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-RotationGestureHandler-onActionCancel(event: Callback<GestureEvent>): RotationGestureHandler--><!--Device-RotationGestureHandler-onActionCancel(event: Callback<GestureEvent>): RotationGestureHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;GestureEvent&gt; | 是 | 旋转手势处理器取消回调。返回手势事件信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RotationGestureHandler](arkts-arkui-rotationgesturehandler-c.md) | 返回当前旋转手势处理器对象。 |

## onActionEnd

```TypeScript
onActionEnd(event: Callback<GestureEvent>): RotationGestureHandler
```

设置旋转手势处理器结束回调。旋转手势处理器识别成功后，手指抬起时触发回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RotationGestureHandler-onActionEnd(event: Callback<GestureEvent>): RotationGestureHandler--><!--Device-RotationGestureHandler-onActionEnd(event: Callback<GestureEvent>): RotationGestureHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;GestureEvent&gt; | 是 | 旋转手势处理器结束回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RotationGestureHandler](arkts-arkui-rotationgesturehandler-c.md) | 返回当前旋转手势处理器对象。 |

## onActionStart

```TypeScript
onActionStart(event: Callback<GestureEvent>): RotationGestureHandler
```

设置旋转手势处理器识别成功回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RotationGestureHandler-onActionStart(event: Callback<GestureEvent>): RotationGestureHandler--><!--Device-RotationGestureHandler-onActionStart(event: Callback<GestureEvent>): RotationGestureHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;GestureEvent&gt; | 是 | 旋转手势处理器识别成功回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RotationGestureHandler](arkts-arkui-rotationgesturehandler-c.md) | 返回当前旋转手势处理器对象。 |

## onActionUpdate

```TypeScript
onActionUpdate(event: Callback<GestureEvent>): RotationGestureHandler
```

设置旋转手势处理器更新回调。旋转手势处理器移动过程中触发回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RotationGestureHandler-onActionUpdate(event: Callback<GestureEvent>): RotationGestureHandler--><!--Device-RotationGestureHandler-onActionUpdate(event: Callback<GestureEvent>): RotationGestureHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;GestureEvent&gt; | 是 | 旋转手势处理器更新回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RotationGestureHandler](arkts-arkui-rotationgesturehandler-c.md) | 返回当前旋转手势处理器对象。 |

