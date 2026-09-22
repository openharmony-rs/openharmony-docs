# GestureEventListenerCallback

```TypeScript
declare type GestureEventListenerCallback = (event: GestureEvent, node?: FrameNode) => void
```

Defines the callback type for gesture event listeners in **UIObserver**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [GestureEvent](../arkts-components/arkts-arkui-tapgesture-comp-gestureevent-i.md) | Yes | Information about the gesture event that triggers the callback. |
| node | [FrameNode](arkts-arkui-framenode-c.md) | No | Component bound to the gesture event. |
