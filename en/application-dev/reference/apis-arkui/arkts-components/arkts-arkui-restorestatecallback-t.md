# RestoreStateCallback

```TypeScript
declare type RestoreStateCallback = (savedState: Record<string, Object> | null) => void
```

Custom page state restore callback.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| savedState | Record&lt;string, Object&gt; &#124; null | Yes | Custom page state saved by onSaveState. |
