# UIStatesChangeHandler

```TypeScript
declare type UIStatesChangeHandler = (node: FrameNode, currentUIStates: int) => void
```

UI状态变化处理函数，返回当前UI状态，值为结果 的所有当前状态枚举值或计算，并且可以确定状态 通过执行&操作，如下。 如果(currentStates & UIState.PRESSED == UIState.PRESSED) 但是，请注意，对于正常的状态检查，应该直接使用equal。 如果(currentStates == UIState.NORMAL)。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare type UIStatesChangeHandler = (node: FrameNode, currentUIStates: int) => void--><!--Device-unnamed-declare type UIStatesChangeHandler = (node: FrameNode, currentUIStates: int) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 触发UI状态变化的节点。  |
| currentUIStates | int | 是 | 回调触发时当前的UI状态。可以通过位与运算判断当前包含哪些[UIState]\_\_\_JSDOC\_LINK\_USD\_0\_\_\_状态。位与运算方法：if (currentState & UIState.PRESSED == UIState.PRESSED)。一般的UIState状态检查可以直接判断：if (currentState == UIState.PRESSED)。 \_\_\_HTML\_TAG\_USD\_1\_\_\_取值限定为整数。  |

