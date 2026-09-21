# PanListenerCallback

```TypeScript
declare type PanListenerCallback = (event: GestureEvent, current: GestureRecognizer, node?: FrameNode) => void
```

Defines a callback for pan gesture events.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [GestureEvent](../arkts-components/arkts-arkui-tapgesture-comp-gestureevent-i.md) | Yes | Information about the gesture event that triggers the callback. |
| current | [GestureRecognizer](../arkts-components/arkts-arkui-tapgesture-comp-gesturerecognizer-c.md) | Yes | Information about the gesture recognizer that detects the event. |
| node | [FrameNode](arkts-arkui-framenode-c.md) | No | Component bound to the gesture event. |
