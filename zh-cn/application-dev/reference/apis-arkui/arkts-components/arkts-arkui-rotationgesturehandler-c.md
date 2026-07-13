# RotationGestureHandler

旋转手势处理器对象类型。

**继承/实现关系：** RotationGestureHandler extends [GestureHandler<RotationGestureHandler>](GestureHandler<RotationGestureHandler>)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: RotationGestureHandlerOptions)
```

旋转手势处理器的构造函数。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | RotationGestureHandlerOptions | 否 | 旋转手势处理器配置参数。 |

## onActionCancel

```TypeScript
onActionCancel(event: Callback<void>): RotationGestureHandler
```

设置旋转手势处理器取消回调。旋转手势处理器识别成功后，接收到触摸取消事件时触发回调。不返回手势事件信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | Callback&lt;void&gt; | 是 | 旋转手势处理器取消回调。不返回手势事件信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RotationGestureHandler | 返回当前旋转手势处理器对象。 |

## onActionCancel

```TypeScript
onActionCancel(event: Callback<GestureEvent>): RotationGestureHandler
```

设置旋转手势处理器取消回调。旋转手势处理器识别成功后，接收到触摸取消事件时触发回调。与
[onActionCancel](arkts-arkui-rotationgesturehandler-c.md#onactioncancel-1)相比，此接口返回手势事件信息。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | Callback&lt;GestureEvent&gt; | 是 | 旋转手势处理器取消回调。返回手势事件信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RotationGestureHandler | 返回当前旋转手势处理器对象。 |

## onActionEnd

```TypeScript
onActionEnd(event: Callback<GestureEvent>): RotationGestureHandler
```

设置旋转手势处理器结束回调。旋转手势处理器识别成功后，手指抬起时触发回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | Callback&lt;GestureEvent&gt; | 是 | 旋转手势处理器结束回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RotationGestureHandler | 返回当前旋转手势处理器对象。 |

## onActionStart

```TypeScript
onActionStart(event: Callback<GestureEvent>): RotationGestureHandler
```

设置旋转手势处理器识别成功回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | Callback&lt;GestureEvent&gt; | 是 | 旋转手势处理器识别成功回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RotationGestureHandler | 返回当前旋转手势处理器对象。 |

## onActionUpdate

```TypeScript
onActionUpdate(event: Callback<GestureEvent>): RotationGestureHandler
```

设置旋转手势处理器更新回调。旋转手势处理器移动过程中触发回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | Callback&lt;GestureEvent&gt; | 是 | 旋转手势处理器更新回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RotationGestureHandler | 返回当前旋转手势处理器对象。 |

