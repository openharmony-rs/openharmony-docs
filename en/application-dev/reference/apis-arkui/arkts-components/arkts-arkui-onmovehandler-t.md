# OnMoveHandler

```TypeScript
declare type OnMoveHandler = (from: number, to: number) => void
```

Defines the onMove callback.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| from | number | Yes | Index number for moving elements. |
| to | number | Yes | Target index number for moving elements. |
