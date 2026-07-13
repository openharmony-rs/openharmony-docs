# LongPressGestureHandler

长按手势处理器对象类型。

**继承/实现关系：** LongPressGestureHandler extends [GestureHandler<LongPressGestureHandler>](GestureHandler<LongPressGestureHandler>)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: LongPressGestureHandlerOptions)
```

长按手势处理器的构造函数。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | LongPressGestureHandlerOptions | 否 | 长按手势处理器配置参数。 |

## onAction

```TypeScript
onAction(event: Callback<GestureEvent>): LongPressGestureHandler
```

设置长按手势处理器识别成功回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | Callback&lt;GestureEvent&gt; | 是 | 长按手势处理器识别成功回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| LongPressGestureHandler | 返回当前长按手势处理器对象。 |

## onActionCancel

```TypeScript
onActionCancel(event: Callback<void>): LongPressGestureHandler
```

设置长按手势处理器取消回调。长按手势处理器识别成功后，接收到触摸取消事件时触发回调。不返回手势事件信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | Callback&lt;void&gt; | 是 | 长按手势处理器取消回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| LongPressGestureHandler | 返回当前长按手势处理器对象。 |

## onActionCancel

```TypeScript
onActionCancel(event: Callback<GestureEvent>): LongPressGestureHandler
```

设置长按手势处理器取消回调。长按手势处理器识别成功后，接收到触摸取消事件时触发回调。与
[onActionCancel](arkts-arkui-longpressgesturehandler-c.md#onactioncancel-1)接口相比，此接口返回手势事件信息。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | Callback&lt;GestureEvent&gt; | 是 | 长按手势处理器取消回调。该回调会返回手势事件信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| LongPressGestureHandler | 返回当前长按手势处理器对象。 |

## onActionEnd

```TypeScript
onActionEnd(event: Callback<GestureEvent>): LongPressGestureHandler
```

设置长按手势处理器结束回调。长按手势处理器识别成功后，最后一根手指抬起时触发回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | Callback&lt;GestureEvent&gt; | 是 | 长按手势处理器结束回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| LongPressGestureHandler | 返回当前长按手势处理器对象。 |

