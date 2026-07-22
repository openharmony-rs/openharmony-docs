# TapGestureHandler

点击手势处理器对象类型。

**继承/实现关系：** TapGestureHandler extends [GestureHandler<TapGestureHandler>](GestureHandler<TapGestureHandler>)

**起始版本：** 12

<!--Device-unnamed-declare class TapGestureHandler extends GestureHandler<TapGestureHandler>--><!--Device-unnamed-declare class TapGestureHandler extends GestureHandler<TapGestureHandler>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: TapGestureHandlerOptions)
```

点击手势处理器的构造函数。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TapGestureHandler-constructor(options?: TapGestureHandlerOptions)--><!--Device-TapGestureHandler-constructor(options?: TapGestureHandlerOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TapGestureHandlerOptions](arkts-arkui-tapgesturehandleroptions-i.md) | 否 | 点击手势处理器配置参数。 |

## onAction

```TypeScript
onAction(event: Callback<GestureEvent>): TapGestureHandler
```

设置点击手势处理器识别成功回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TapGestureHandler-onAction(event: Callback<GestureEvent>): TapGestureHandler--><!--Device-TapGestureHandler-onAction(event: Callback<GestureEvent>): TapGestureHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;GestureEvent&gt; | 是 | 点击手势处理器识别成功回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TapGestureHandler](arkts-arkui-tapgesturehandler-c.md) | 返回当前点击手势处理器对象。 |

