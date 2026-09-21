# SeekMode

```TypeScript
declare enum SeekMode
```

Enumerates video seek modes.

| Name | Value | Description |  
| ---------------- |--| ---------------------------- |  
| [PreviousKeyframe](arkts-arkui-video-comp-seekmode-e.md) |0| Seeks to the nearest keyframe before the current playback position. |
| [NextKeyframe](arkts-arkui-video-comp-seekmode-e.md) |1| Seeks to the nearest keyframe after the current playback position. |
| [ClosestKeyframe](arkts-arkui-video-comp-seekmode-e.md) |2| Seeks to the keyframe closest to the current playback position. |
| [Accurate](arkts-arkui-video-comp-seekmode-e.md) |3| Seeks precisely to the specified time point, regardless of whether it is a keyframe. |
| | |This mode is highly accurate but may require decoding more frames. |

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## PreviousKeyframe

```TypeScript
PreviousKeyframe
```

Seek to the nearest previous keyframe.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NextKeyframe

```TypeScript
NextKeyframe
```

Seek to the nearest next keyframe.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ClosestKeyframe

```TypeScript
ClosestKeyframe
```

Seek to the nearest keyframe.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Accurate

```TypeScript
Accurate
```

Seek to a specific frame, regardless of whether the frame is a keyframe.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
