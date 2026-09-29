# OnDidStopDraggingCallback

```TypeScript
declare type OnDidStopDraggingCallback = (willFling: boolean) => void
```

Defines the callback invoked when the scrollable component stops being dragged.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**Widget capability:** This API can be used in ArkTS widgets since API version 21.

<!--Device-unnamed-declare type OnDidStopDraggingCallback = (willFling: boolean) => void--><!--Device-unnamed-declare type OnDidStopDraggingCallback = (willFling: boolean) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| willFling | boolean | Yes | Whether an inertial animation will follow. **true**: An inertial animation will follow. **false**: No inertial animation will follow. |
