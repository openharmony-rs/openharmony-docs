# OnPickerStateCallback

```TypeScript
export type OnPickerStateCallback = (state: AVCastPickerState) => void
```

Callback for picker state

@typedef { function } OnPickerStateCallback

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-unnamed-export type OnPickerStateCallback = (state: AVCastPickerState) => void--><!--Device-unnamed-export type OnPickerStateCallback = (state: AVCastPickerState) => void-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVInputCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| state | [AVCastPickerState](arkts-avsession-multimedia-avcastpickerparam-avcastpickerstate-e.md) | Yes | the picker state. |
