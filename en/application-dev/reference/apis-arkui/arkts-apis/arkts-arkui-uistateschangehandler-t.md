# UIStatesChangeHandler

```TypeScript
declare type UIStatesChangeHandler = (node: FrameNode, currentUIStates: number) => void
```

Defines the callback triggered when the UI state changes. Defines the callback triggered on UI state changes. It receives the current [UIState](arkts-arkui-framenode-uistate-e.md) value when triggered. The parameter represents **UIState** enumerated values or their bitwise combinations.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Node triggering the UI state change. |
| currentUIStates | number | Yes | Current UI states when the callback is triggered. <br>You can use the bitwise AND operation to check the [UI states](arkts-arkui-framenode-uistate-e.md) that are currently included. <br>Example: **if (currentState & UIState.PRESSED == UIState.PRESSED)**. <br>Direct comparison: **if (currentState == UIState.PRESSED)**. |
