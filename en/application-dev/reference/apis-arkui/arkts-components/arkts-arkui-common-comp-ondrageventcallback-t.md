# OnDragEventCallback

```TypeScript
declare type OnDragEventCallback = (event: DragEvent, extraParams?: string) => void
```

Defines a callback for drag events.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [DragEvent](arkts-arkui-common-comp-dragevent-i.md) | Yes | **event**: drag event information, including the coordinates of the drag point. |
| extraParams | string | No | **extraParams**: additional information about the drag event. Its value must be parsed into JSON format. |
