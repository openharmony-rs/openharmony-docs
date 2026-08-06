# InputEventInterceptResult

Defines the input event intercept result.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare interface InputEventInterceptResult--><!--Device-unnamed-export declare interface InputEventInterceptResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## action

```TypeScript
action: InputEventInterceptAction
```

Event intercept decision. - CONTINUE: Allows the event to continue to be delivered to the UI framework. - BLOCK: Blocks the event from being delivered, the event will not enter the UI framework.

**类型：** InputEventInterceptAction

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InputEventInterceptResult-action: InputEventInterceptAction--><!--Device-InputEventInterceptResult-action: InputEventInterceptAction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

