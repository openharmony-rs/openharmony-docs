# UIStatesChangeHandler

```TypeScript
declare type UIStatesChangeHandler = (node: FrameNode, currentUIStates: number) => void
```

当UI状态发生变化时触发的回调。接收回调触发时的[UIState](../../apis-na/arkts-apis/arkts-na-framenode-uistate-e.md#UIState)状态，该参数的取值为UIState状态枚举值或其运算结果。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type UIStatesChangeHandler = (node: FrameNode, currentUIStates: number) => void--><!--Device-unnamed-declare type UIStatesChangeHandler = (node: FrameNode, currentUIStates: number) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](../../apis-na/arkts-apis/arkts-na-framenode-c.md) | 是 | 触发UI状态变化的节点。 |
| currentUIStates | number | 是 | 回调触发时当前的UI状态。 <br>可以通过位与运算判断当前包含哪些[UIState](../../apis-na/arkts-apis/arkts-na-framenode-uistate-e.md#UIState)状态。 <br>位与运算方法：if ((currentUIStates & UIState.PRESSED) == UIState.PRESSED)。 <br>当仅需判断当前是否仅处于单个状态时，可以直接判断：if (currentUIStates == UIState.PRESSED)。注意，此方式仅在当前仅有一个状态激活时有效，若需判断多个状态中是否包含某个状态，请使用位 与运算。 |

