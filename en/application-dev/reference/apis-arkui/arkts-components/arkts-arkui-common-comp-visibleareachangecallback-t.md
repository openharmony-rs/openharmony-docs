# VisibleAreaChangeCallback

```TypeScript
declare type VisibleAreaChangeCallback = (isExpanding: boolean, currentRatio: number) => void
```

Represents a callback for visible area changes of the component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isExpanding | boolean | Yes | Whether the component's visible area has increased or decreased relative to its total area since the last callback. The value **true** indicates that the visible area has increased, and **false** indicates that the visible area has decreased. |
| currentRatio | number | Yes | Ratio of the component's visible area to its own area at the moment the callback is triggered. |
