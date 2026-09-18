# OnHomeShowOnTopCallback

```TypeScript
declare type OnHomeShowOnTopCallback = (name: string) => void
```

Represents the callback invoked when the home page is displayed at the top of the stack.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | ID of the page displayed at the top of the stack. |
