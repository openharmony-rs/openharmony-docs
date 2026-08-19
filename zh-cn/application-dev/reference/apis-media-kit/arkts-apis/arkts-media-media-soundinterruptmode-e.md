# SoundInterruptMode

表示在SoundPool中，同一ID的音频在播放时的打断模式的枚举。

**起始版本：** 23

<!--Device-media-enum SoundInterruptMode--><!--Device-media-enum SoundInterruptMode-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

## NO_INTERRUPT

```TypeScript
NO_INTERRUPT = 0
```

表示同一ID的音频，如果前者尚未播放完成，后者不会打断前者的播放，二者并行播放。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SoundInterruptMode-NO_INTERRUPT = 0--><!--Device-SoundInterruptMode-NO_INTERRUPT = 0-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

## SAME_SOUND_INTERRUPT

```TypeScript
SAME_SOUND_INTERRUPT = 1
```

表示同一ID的音频，如果前者尚未播放完成，后者在播放前会先打断前者的播放。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SoundInterruptMode-SAME_SOUND_INTERRUPT = 1--><!--Device-SoundInterruptMode-SAME_SOUND_INTERRUPT = 1-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

