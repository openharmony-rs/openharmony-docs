# OnDidStopDraggingCallback

```TypeScript
declare type OnDidStopDraggingCallback = (willFling: boolean) => void
```

On scroll callback using in scrollable onDidStopDragging.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**Widget capability:** This API can be used in ArkTS widgets since API version 21.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| willFling | boolean | Yes | whether start fling animation. |
