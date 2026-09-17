# OnVisibleIndexesChangeCallback

```TypeScript
declare type OnVisibleIndexesChangeCallback = (start: number, end: number) => void
```

Defines the callback type used in OnVisibleIndexesChange.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | number | Yes | the first index in visible content. |
| end | number | Yes | the last index in visible content. |
