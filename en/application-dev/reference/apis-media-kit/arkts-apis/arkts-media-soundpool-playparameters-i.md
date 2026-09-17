# PlayParameters

Describes the playback parameters of the sound pool.

These parameters are used to control the playback volume, number of loops, and priority.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Media.SoundPool

## leftVolume

```TypeScript
leftVolume?: number
```

Volume of the left channel. The value range is [0.0, 1.0], and the default value is **1.0**.

When the volume exceeds the boundary value, the boundary value is automatically used.

**Type:** number

**Since:** 10

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

**System capability:** SystemCapability.Multimedia.Media.SoundPool

## pitch

```TypeScript
pitch?: number
```

Pitch of the sound. The value ranges from 0.25 to 4.0 with a step size of 0.001. The default value is 1.0.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

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

**System capability:** SystemCapability.Multimedia.Media.SoundPool

## rate

```TypeScript
rate?: number
```

Playback rate. For details, see [AudioRendererRate](../../apis-audio-kit/arkts-apis/arkts-audio-audio-audiorendererrate-e.md). Default value: **0**

**Type:** number

**Since:** 10

**System capability:** SystemCapability.Multimedia.Media.SoundPool

## rightVolume

```TypeScript
rightVolume?: number
```

Volume of the right channel. (Currently, the volume cannot be set separately for the left and right channels. The volume set for the left channel is used.) The value range is [0.0, 1.0], and the default value is **1.0**.

When the volume exceeds the boundary value, the boundary value is automatically used.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.Multimedia.Media.SoundPool
