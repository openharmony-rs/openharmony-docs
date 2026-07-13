# UIStatesChangeHandler

```TypeScript
declare type UIStatesChangeHandler = (node: FrameNode, currentUIStates: number) => void
```

当UI状态发生变化时触发的回调。接收回调触发时的[UIState](arkts-arkui-uistate-e.md)状态，该参数的取值为UIState状态枚举值或其运算结果。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | FrameNode | 是 | 触发UI状态变化的节点。 |
| currentUIStates | number | 是 | 回调触发时当前的UI状态。<br>可以通过位与运算判断当前包含哪些[UIState](arkts-arkui-uistate-e.md)状态。<br>位与运算方法：if (currentState & UIState.PRESSED == UIState.PRESSED)。<br>一般的UIState状态检查可以直接判断：if (currentState == UIState.PRESSED)。 |

