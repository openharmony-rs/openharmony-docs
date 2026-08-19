# GestureGroupHandler

手势组处理器对象类型。

**继承/实现关系：** GestureGroupHandler extends [GestureHandler](arkts-arkui-gesture-gesturehandler-c.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class GestureGroupHandler--><!--Device-unnamed-export declare class GestureGroupHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: GestureGroupGestureHandlerOptions)
```

手势组处理器的构造函数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureGroupHandler-constructor(options?: GestureGroupGestureHandlerOptions)--><!--Device-GestureGroupHandler-constructor(options?: GestureGroupGestureHandlerOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [GestureGroupGestureHandlerOptions](arkts-arkui-gesture-gesturegroupgesturehandleroptions-i.md) | 否 | 手势组处理器配置参数。 |

## onCancel

```TypeScript
onCancel(event: VoidCallback): this
```

设置手势组处理器取消回调。顺序组合手势（[GestureMode](arkts-arkui-gesture-gesturemode-e.md).Sequence）取消后触发回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureGroupHandler-onCancel(event: VoidCallback): this--><!--Device-GestureGroupHandler-onCancel(event: VoidCallback): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [VoidCallback](arkts-arkui-voidcallback-t.md) | 是 | 手势组处理器取消回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前手势组处理器对象。 |

