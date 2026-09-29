# UIStatesChangeHandler

```TypeScript
declare type UIStatesChangeHandler = (node: FrameNode, currentUIStates: number) => void
```

Defines the callback triggered when the UI state changes. It receives the current [UIState](arkts-arkui-framenode-uistate-e.md) value when triggered. The parameter represents **UIState** enumerated values or their bitwise combinations.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-unnamed-declare type UIStatesChangeHandler = (node: FrameNode, currentUIStates: number) => void--><!--Device-unnamed-declare type UIStatesChangeHandler = (node: FrameNode, currentUIStates: number) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Node triggering the UI state change. |
| currentUIStates | number | Yes | Current UI states when the callback is triggered. <br>You can use a bitwise AND operation to determine which [UI states](arkts-arkui-framenode-uistate-e.md) are currently included. <br>Bitwise AND operation: **if ((currentUIStates & UIState.PRESSED) == UIState.PRESSED)**. <br>If you only need to determine whether there is a single state, you can directly use **if (currentUIStates == UIState.PRESSED)**. Note: This method is valid only when a single state is active. To determine whether a specific state is included among multiple states, use a bitwise AND operation. |
