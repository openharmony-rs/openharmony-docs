# SwipeGestureHandler

快滑手势处理器对象类型。

**继承/实现关系：** SwipeGestureHandler extends [GestureHandler<SwipeGestureHandler>](GestureHandler<SwipeGestureHandler>)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: SwipeGestureHandlerOptions)
```

快滑手势处理器的构造函数。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | SwipeGestureHandlerOptions | 否 | 快滑手势处理器配置参数。 |

## onAction

```TypeScript
onAction(event: Callback<GestureEvent>): SwipeGestureHandler
```

设置快滑手势处理器识别成功回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | Callback&lt;GestureEvent&gt; | 是 | 快滑手势处理器识别成功回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SwipeGestureHandler | 返回当前快滑手势处理器对象。 |

