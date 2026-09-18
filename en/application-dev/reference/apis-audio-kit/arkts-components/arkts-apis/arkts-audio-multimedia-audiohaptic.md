# @ohos.multimedia.audioHaptic(Audio Haptic)

Audio-haptic enables users to get rhythmic auditory and haptic feedback while having incoming calls or messages.

**Device behavior difference**: For a device without a vibration component, no vibration effect is generated.

**Since:** 11

**System capability:** SystemCapability.Multimedia.AudioHaptic.Core

## Modules to Import

```TypeScript
import { audioHaptic } from '@kit.AudioKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getAudioHapticManager](arkts-audio-audiohaptic-getaudiohapticmanager-f.md) | Obtains an [AudioHapticManager](arkts-audio-audiohaptic-audiohapticmanager-i.md) instance. This object is singleton in one process. |

### Interfaces

| Name | Description |
| --- | --- |
| [AudioHapticFileDescriptor](arkts-audio-audiohaptic-audiohapticfiledescriptor-i.md) | Describes the audio-haptic file descriptor. |
| [AudioHapticManager](arkts-audio-audiohaptic-audiohapticmanager-i.md) | Manages the audio-haptic feature. Before calling any API in AudioHapticManager, you must use [getAudioHapticManager](arkts-audio-audiohaptic-getaudiohapticmanager-f.md) to create an AudioHapticManager instance. |
| [AudioHapticPlayer](arkts-audio-audiohaptic-audiohapticplayer-i.md) | Implements audio-haptic playback. Before calling any API in AudioHapticPlayer, you must use [createPlayer](arkts-audio-audiohaptic-audiohapticmanager-i.md#createplayer) to create an AudioHapticPlayer instance. |
| [AudioHapticPlayerOptions](arkts-audio-audiohaptic-audiohapticplayeroptions-i.md) | Describes the options for the audio-haptic player. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [AudioHapticPlayer](arkts-audio-audiohaptic-audiohapticplayer-i-sys.md) | Implements audio-haptic playback. Before calling any API in AudioHapticPlayer, you must use [createPlayer](arkts-audio-audiohaptic-audiohapticmanager-i.md#createplayer) to create an AudioHapticPlayer instance. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [AudioHapticType](arkts-audio-audiohaptic-audiohaptictype-e.md) | Enumerates the audio haptic types. |
| [AudioLatencyMode](arkts-audio-audiohaptic-audiolatencymode-e.md) | Enumerates the audio latency modes. |
