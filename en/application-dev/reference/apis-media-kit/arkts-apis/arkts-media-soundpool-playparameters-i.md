# PlayParameters

```TypeScript
export interface PlayParameters
```

Describes the playback parameters of the sound pool.

These parameters are used to control the playback volume, number of loops, and priority.

**Since:** 10

<!--Device-unnamed-export interface PlayParameters--><!--Device-unnamed-export interface PlayParameters-End-->

**System capability:** SystemCapability.Multimedia.Media.SoundPool

## leftVolume

```TypeScript
leftVolume?: number
```

Volume of the left channel. The value range is [0.0, 1.0], and the default value is **1.0**.

When the volume exceeds the boundary value, the boundary value is automatically used.

**Type:** number

**Since:** 10

<!--Device-PlayParameters-leftVolume?: double--><!--Device-PlayParameters-leftVolume?: double-End-->

**System capability:** SystemCapability.Multimedia.Media.SoundPool

## loop

```TypeScript
loop?: number
```

Number of loops.

If this parameter is set to a value greater than or equal to 0, the number of times the content is actually played is the value of **loop** plus 1.

If this parameter is set to a value less than 0, the content is played repeatedly.

The default value is **0**, indicating that the content is played only once.

If this parameter is set to a floating-point number, only the integer part is used.

**Type:** number

**Since:** 10

<!--Device-PlayParameters-loop?: int--><!--Device-PlayParameters-loop?: int-End-->

**System capability:** SystemCapability.Multimedia.Media.SoundPool

## pitch

```TypeScript
pitch?: number
```

Pitch for playing an audio stream. The value range is [0.25, 4.0]. The default value is **1.0**.<br>When the pitch exceeds the boundary value, the boundary value is automatically used.<br>**Since:** 26.0.0<br> **Model restriction**: This API can be used only in the stage model.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PlayParameters-pitch?: double--><!--Device-PlayParameters-pitch?: double-End-->

**System capability:** SystemCapability.Multimedia.Media.SoundPool

## priority

```TypeScript
priority?: number
```

Priority for playing an audio stream. The value **0** indicates the lowest priority. A larger value indicates a higher priority.

The playback priority is determined by comparing the values. The value must be an integer greater than or equal to
0. The default value is **0**.

If this parameter is set to a negative value, it is automatically set to 0. If this parameter is set to a floating point number, only the integer part is used.

**Type:** number

**Since:** 10

<!--Device-PlayParameters-priority?: int--><!--Device-PlayParameters-priority?: int-End-->

**System capability:** SystemCapability.Multimedia.Media.SoundPool

## rate

```TypeScript
rate?: number
```

Playback rate. For details, see [AudioRendererRate](../../apis-audio-kit/arkts-apis/arkts-audio-audio-audiorendererrate-e.md). The default value is **RENDER_RATE_NORMAL**, corresponding to the enumerated value **0**.

**Type:** number

**Since:** 10

<!--Device-PlayParameters-rate?: int--><!--Device-PlayParameters-rate?: int-End-->

**System capability:** SystemCapability.Multimedia.Media.SoundPool

## rightVolume

```TypeScript
rightVolume?: number
```

Volume of the right channel. (Currently, the volume cannot be set separately for the left and right channels. The volume set for the left channel is used.) The value range is [0.0, 1.0], and the default value is **1.0**.

When the volume exceeds the boundary value, the boundary value is automatically used.

**Type:** number

**Since:** 10

<!--Device-PlayParameters-rightVolume?: double--><!--Device-PlayParameters-rightVolume?: double-End-->

**System capability:** SystemCapability.Multimedia.Media.SoundPool
