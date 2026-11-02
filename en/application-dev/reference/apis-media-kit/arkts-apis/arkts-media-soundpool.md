# soundPool(SoundPool)

The module provides APIs for loading, unloading, playing, and stopping playing sounds, setting the volume,
 and setting the number of loops. The module is applicable to scenarios that require quick response and
 low-latency playback, such as game sound effects, UI interaction sound effects, and notification sounds.

Before using these APIs, you must call
 [media.createSoundPool](arkts-media-media-createsoundpool-f.md)
 to create a **SoundPool** instance.



## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [ErrorInfo](arkts-media-soundpool-errorinfo-i.md) | Describes the error information. |
| [PlayParameters](arkts-media-soundpool-playparameters-i.md) | Describes the playback parameters of the sound pool. |
| [SoundPool](arkts-media-soundpool-i.md) | Implements a sound pool that provides APIs for loading, unloading, playing, and stopping playing system sounds, setting the volume, and setting the number of loops. Before using these APIs, you must call [media.createSoundPool](arkts-media-media-createsoundpool-f.md) to create a SoundPool instance. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [PlayParameters](arkts-media-soundpool-playparameters-i-sys.md) | Describes the playback parameters of the sound pool. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [ErrorType](arkts-media-soundpool-errortype-e.md) | Enumerates the error types (used to distinguish error stages). |
