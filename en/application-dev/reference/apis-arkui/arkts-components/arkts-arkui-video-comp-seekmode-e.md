# SeekMode

```TypeScript
declare enum SeekMode
```

Enumerates video seek modes.

**Since:** 8

<!--Device-unnamed-declare enum SeekMode--><!--Device-unnamed-declare enum SeekMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Accurate

```TypeScript
Accurate
```

Seeks precisely to the specified time point, regardless of whether it is a keyframe. This mode is highly accurate but may require decoding more frames.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SeekMode-Accurate--><!--Device-SeekMode-Accurate-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ClosestKeyframe

```TypeScript
ClosestKeyframe
```

Seeks to the keyframe closest to the current playback position.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SeekMode-ClosestKeyframe--><!--Device-SeekMode-ClosestKeyframe-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NextKeyframe

```TypeScript
NextKeyframe
```

Seeks to the nearest keyframe after the current playback position.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SeekMode-NextKeyframe--><!--Device-SeekMode-NextKeyframe-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## PreviousKeyframe

```TypeScript
PreviousKeyframe
```

Seeks to the nearest keyframe before the current playback position.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SeekMode-PreviousKeyframe--><!--Device-SeekMode-PreviousKeyframe-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
