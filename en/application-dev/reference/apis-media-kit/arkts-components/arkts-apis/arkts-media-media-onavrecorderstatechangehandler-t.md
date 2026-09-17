# OnAVRecorderStateChangeHandler

```TypeScript
type OnAVRecorderStateChangeHandler = (state: AVRecorderState, reason: StateChangeReason) => void
```

Describes the callback invoked for the AVRecorder state change event.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| state | [AVRecorderState](arkts-media-media-avrecorderstate-t.md) | Yes | AVRecorder state. |
| reason | [StateChangeReason](arkts-media-media-statechangereason-e.md) | Yes | Reason for the state change. |
