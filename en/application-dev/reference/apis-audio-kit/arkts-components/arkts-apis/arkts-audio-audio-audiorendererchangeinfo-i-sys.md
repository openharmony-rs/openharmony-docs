# AudioRendererChangeInfo

```TypeScript
interface AudioRendererChangeInfo
```

Describes the audio renderer change event.

**Since:** 9

<!--Device-audio-interface AudioRendererChangeInfo--><!--Device-audio-interface AudioRendererChangeInfo-End-->

**System capability:** SystemCapability.Multimedia.Audio.Renderer

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## clientUid

```TypeScript
readonly clientUid: number
```

Uid for audio renderer client application.

**Type:** number

**Since:** 9

<!--Device-AudioRendererChangeInfo-readonly clientUid: int--><!--Device-AudioRendererChangeInfo-readonly clientUid: int-End-->

**System capability:** SystemCapability.Multimedia.Audio.Renderer

**System API:** This is a system API.

## rendererState

```TypeScript
readonly rendererState: AudioState
```

Audio state.

**Type:** [AudioState](arkts-audio-audio-audiostate-e.md)

**Since:** 9

<!--Device-AudioRendererChangeInfo-readonly rendererState: AudioState--><!--Device-AudioRendererChangeInfo-readonly rendererState: AudioState-End-->

**System capability:** SystemCapability.Multimedia.Audio.Renderer

**System API:** This is a system API.
