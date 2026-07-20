# SwipeGestureHandler

快滑手势处理器对象类型。

**继承/实现关系：** SwipeGestureHandler extends [GestureHandler<SwipeGestureHandler>](GestureHandler<SwipeGestureHandler>)

**起始版本：** 12

<!--Device-unnamed-declare class SwipeGestureHandler extends GestureHandler<SwipeGestureHandler>--><!--Device-unnamed-declare class SwipeGestureHandler extends GestureHandler<SwipeGestureHandler>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="constructor"></a>
## constructor

```TypeScript
constructor(options?: SwipeGestureHandlerOptions)
```

快滑手势处理器的构造函数。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SwipeGestureHandler-constructor(options?: SwipeGestureHandlerOptions)--><!--Device-SwipeGestureHandler-constructor(options?: SwipeGestureHandlerOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SwipeGestureHandlerOptions](arkts-arkui-swipegesturehandleroptions-i.md) | 否 | 快滑手势处理器配置参数。 |

<a id="onaction"></a>
## onAction

```TypeScript
onAction(event: Callback<GestureEvent>): SwipeGestureHandler
```

设置快滑手势处理器识别成功回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SwipeGestureHandler-onAction(event: Callback<GestureEvent>): SwipeGestureHandler--><!--Device-SwipeGestureHandler-onAction(event: Callback<GestureEvent>): SwipeGestureHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;GestureEvent&gt; | 是 | 快滑手势处理器识别成功回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SwipeGestureHandler](arkts-arkui-swipegesturehandler-c.md) | 返回当前快滑手势处理器对象。 |

