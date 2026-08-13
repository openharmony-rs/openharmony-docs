# TapGestureHandler

点击手势处理器对象类型。

**继承/实现关系：** TapGestureHandler extends [GestureHandler](arkts-arkui-gesture-gesturehandler-c.md#GestureHandler)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class TapGestureHandler--><!--Device-unnamed-export declare class TapGestureHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: TapGestureHandlerOptions)
```

点击手势处理器的构造函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TapGestureHandler-constructor(options?: TapGestureHandlerOptions)--><!--Device-TapGestureHandler-constructor(options?: TapGestureHandlerOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TapGestureHandlerOptions](arkts-arkui-gesture-tapgesturehandleroptions-i.md) | 否 | 点击手势处理器配置参数。 |

## onAction

```TypeScript
onAction(event: Callback<GestureEvent>): this
```

设置点击手势处理器识别成功回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TapGestureHandler-onAction(event: Callback<GestureEvent>): this--><!--Device-TapGestureHandler-onAction(event: Callback<GestureEvent>): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gesture-gestureevent-i.md)&gt; | 是 | 点击手势处理器识别成功回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前点击手势处理器对象。 |

