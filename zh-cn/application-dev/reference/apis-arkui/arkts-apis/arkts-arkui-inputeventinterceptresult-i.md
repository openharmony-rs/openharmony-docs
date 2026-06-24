# InputEventInterceptResult

输入事件拦截结果接口，用于监听器回调[InputEventListener](arkts-arkui-common-inputeventlistener-t.md#InputEventListener)返回是否拦截的决策。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## action

```TypeScript
action: InputEventInterceptAction
```

输入事件拦截动作。

CONTINUE：允许事件继续传递到UI框架。

BLOCK：阻止事件传递到UI框架。

**类型：** InputEventInterceptAction

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

