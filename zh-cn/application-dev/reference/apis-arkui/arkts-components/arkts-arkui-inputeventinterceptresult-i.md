# InputEventInterceptResult

输入事件拦截结果接口，用于监听器回调[InputEventListener]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_返回是否拦截的决策。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

<!--Device-unnamed-declare interface InputEventInterceptResult--><!--Device-unnamed-declare interface InputEventInterceptResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## action

```TypeScript
action: InputEventInterceptAction
```

输入事件拦截动作。 CONTINUE：允许事件继续传递到UI框架。 BLOCK：阻止事件传递到UI框架。

**类型：** InputEventInterceptAction

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-InputEventInterceptResult-action: InputEventInterceptAction--><!--Device-InputEventInterceptResult-action: InputEventInterceptAction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

