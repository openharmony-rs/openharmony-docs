# PlayParameters

表示音频池播放参数设置。

通过设置播放相关参数，来控制播放的音量，循环次数，播放优先级等参数。

**起始版本：** 10

<!--Device-unnamed-export interface PlayParameters--><!--Device-unnamed-export interface PlayParameters-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

## leftVolume

```TypeScript
leftVolume?: number
```

设置左声道音量。设置范围为[0.0, 1.0]，默认值为1.0。

当音量超过边界值时自动设置为边界值。

**类型：** number

**起始版本：** 10

<!--Device-PlayParameters-leftVolume?: double--><!--Device-PlayParameters-leftVolume?: double-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

## loop

```TypeScript
loop?: number
```

设置循环次数。

当loop≥0时，实际播放次数为loop+1。

当loop＜0时，表示一直循环。

默认值：0，表示仅播放一次。

当loop为浮点数时只截取整数部分。

**类型：** number

**起始版本：** 10

<!--Device-PlayParameters-loop?: int--><!--Device-PlayParameters-loop?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

## pitch

```TypeScript
pitch?: number
```

Pitch of the sound. The value ranges from 0.25 to 4.0 with a step size of 0.001. The Deault pitch is 1.0.

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PlayParameters-pitch?: double--><!--Device-PlayParameters-pitch?: double-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

## priority

```TypeScript
priority?: number
```

音频流播放的优先级。0为最低优先级，数值越大优先级越高。

通过相互比较数值大小确定播放优先级，设置范围为大于等于0的整数。默认值为0。

当优先级为负数时自动设置为0，为浮点数时只截取整数部分。

**类型：** number

**起始版本：** 10

<!--Device-PlayParameters-priority?: int--><!--Device-PlayParameters-priority?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

## rate

```TypeScript
rate?: number
```

设置音频播放的倍速，具体倍速范围参照[AudioRendererRate](../../../../reference/apis-audio-kit/arkts-apis-audio-e.md)。默认值：0。

**类型：** number

**起始版本：** 10

<!--Device-PlayParameters-rate?: int--><!--Device-PlayParameters-rate?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

## rightVolume

```TypeScript
rightVolume?: number
```

设置右声道音量（当前不支持左右分别设置，将以左声道音量为准）。设置范围为[0.0, 1.0]，默认值为1.0。

当音量超过边界值时自动设置为边界值。

**类型：** number

**起始版本：** 10

<!--Device-PlayParameters-rightVolume?: double--><!--Device-PlayParameters-rightVolume?: double-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

