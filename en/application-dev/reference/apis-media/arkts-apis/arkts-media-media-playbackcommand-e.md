# PlaybackCommand

```TypeScript
enum PlaybackCommand
```

Enumeration definition of executable playback control instructions, This interface is used by the application to query whether the corresponding playback control operation can be performed on the media asset after Prepare() is complete.

**Since:** 26.1.0

<!--Device-media-enum PlaybackCommand--><!--Device-media-enum PlaybackCommand-End-->

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

## PLAYBACK_COMMAND_RATE

```TypeScript
PLAYBACK_COMMAND_RATE = 1
```

Operation value for adjusting the playback rate

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-PlaybackCommand-PLAYBACK_COMMAND_RATE = 1--><!--Device-PlaybackCommand-PLAYBACK_COMMAND_RATE = 1-End-->

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

## PLAYBACK_COMMAND_SEEK

```TypeScript
PLAYBACK_COMMAND_SEEK = 0
```

Definition of Enumerated Values of the Seek Operation

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-PlaybackCommand-PLAYBACK_COMMAND_SEEK = 0--><!--Device-PlaybackCommand-PLAYBACK_COMMAND_SEEK = 0-End-->

**System capability:** SystemCapability.Multimedia.Media.AVPlayer
