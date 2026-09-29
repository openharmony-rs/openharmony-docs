# SoundInterruptMode

```TypeScript
enum SoundInterruptMode
```

Enumerates the interruption modes of the audio files with the same ID in SoundPool.

**Since:** 23

<!--Device-media-enum SoundInterruptMode--><!--Device-media-enum SoundInterruptMode-End-->

**System capability:** SystemCapability.Multimedia.Media.SoundPool

## NO_INTERRUPT

```TypeScript
NO_INTERRUPT = 0
```

If the former audio file is not completely played, the latter audio file with the same ID does not interrupt the former audio file. Two audio files are played concurrently.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-SoundInterruptMode-NO_INTERRUPT = 0--><!--Device-SoundInterruptMode-NO_INTERRUPT = 0-End-->

**System capability:** SystemCapability.Multimedia.Media.SoundPool

## SAME_SOUND_INTERRUPT

```TypeScript
SAME_SOUND_INTERRUPT = 1
```

If the former audio file is not completely played, the latter audio file with the same ID interrupts the former audio file.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-SoundInterruptMode-SAME_SOUND_INTERRUPT = 1--><!--Device-SoundInterruptMode-SAME_SOUND_INTERRUPT = 1-End-->

**System capability:** SystemCapability.Multimedia.Media.SoundPool
