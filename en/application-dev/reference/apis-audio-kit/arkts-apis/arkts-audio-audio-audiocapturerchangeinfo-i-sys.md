# AudioCapturerChangeInfo

```TypeScript
interface AudioCapturerChangeInfo
```

Describes the audio capturer change event.

**Since:** 9

<!--Device-audio-interface AudioCapturerChangeInfo--><!--Device-audio-interface AudioCapturerChangeInfo-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## capturerState

```TypeScript
readonly capturerState: AudioState
```

Audio state.

**Type:** [AudioState](arkts-audio-audio-audiostate-e.md)

**Since:** 9

<!--Device-AudioCapturerChangeInfo-readonly capturerState: AudioState--><!--Device-AudioCapturerChangeInfo-readonly capturerState: AudioState-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.

## clientUid

```TypeScript
readonly clientUid: number
```

Uid for audio capturer client application.

**Type:** number

**Since:** 9

<!--Device-AudioCapturerChangeInfo-readonly clientUid: int--><!--Device-AudioCapturerChangeInfo-readonly clientUid: int-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.
